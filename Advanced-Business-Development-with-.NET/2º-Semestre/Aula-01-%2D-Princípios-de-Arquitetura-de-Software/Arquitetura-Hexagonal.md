[[_TOC_]]

A Arquitetura Hexagonal, também conhecida como **Ports and Adapters**, é um padrão arquitetural proposto por Alistair Cockburn. Seu principal objetivo é **isolar o núcleo da aplicação de suas dependências externas**, como UI, banco de dados e frameworks, garantindo maior **manutenibilidade, testabilidade e flexibilidade**.
Esse modelo se encaixa perfeitamente no ecossistema .NET, permitindo a construção de aplicações mais **modulares e resilientes a mudanças tecnológicas**.

# Domínio

O **domínio** é o núcleo da aplicação. É onde estão as **entidades** e **regras de negócio puras**, sem qualquer dependência de infraestrutura, framework ou camada externa. Essa independência garante **testabilidade unitária** e estabilidade frente a mudanças externas.
Exemplo de entidade `Produto` em uma aplicação de e-commerce:

```csharp
public class Produto
{
    public int Id { get; private set; }
    public string Nome { get; private set; }
    public decimal Preco { get; private set; }
        
    public Produto(int id, string nome, decimal preco)
    {
        Id = id;
        Nome = nome;
        Preco = preco < 0 ? throw new ArgumentException("Preço não pode ser negativo") : preco;
    }
        
    public void AplicarDesconto(decimal percentual)
    {
        Preco -= Preco * percentual / 100;
    }
}
```

# Portas (Ports)

As **portas** são interfaces que definem como o domínio se comunica com o mundo externo. Elas são divididas em:
*   **Portas de Entrada (Input Ports)**: definem as operações que podem ser executadas no sistema — normalmente representadas pelos casos de uso.
    
*   **Portas de Saída (Output Ports)**: definem os contratos para dependências externas — como acesso a bancos, filas ou APIs externas.
    
Essas portas são **interfaces puras** que não dependem de implementação.
Exemplo de uma porta de entrada:

```csharp
public interface ICriaPedido
{
    void Executar(CriaPedidoRequest request);
}
    
public class CriaPedidoRequest
{
    public int ClienteId { get; set; }
    public List<int> ProdutosIds { get; set; }
}
```

# Casos de Uso

Os **casos de uso** implementam as **portas de entrada**. Eles orquestram as regras de negócio contidas nas entidades do domínio, coordenando os fluxos da aplicação. Embora conheçam o domínio, eles **não sabem nada sobre UI, banco de dados ou qualquer tecnologia externa**.

# Adaptadores (Adapters)

Os adaptadores conectam o sistema com o mundo externo. Eles **implementam ou consomem as portas**, traduzindo dados e chamadas entre a aplicação e as interfaces externas.
*   **Adaptadores de Entrada**: como controladores REST, interfaces gráficas, CLI, consumidores Kafka, etc. Chamam as portas de entrada.
    
*   **Adaptadores de Saída**: como repositórios, clients HTTP, serviços externos. Implementam as portas de saída.
    
Exemplo de adaptador de entrada (`PedidosController`):

```csharp
[ApiController]
[Route("[controller]")]
public class PedidosController : ControllerBase
{
    private readonly ICriaPedido _criaPedido;
    
    public PedidosController(ICriaPedido criaPedido)
    {
        _criaPedido = criaPedido;
    }
    
    [HttpPost]
    public IActionResult CriarPedido([FromBody] CriaPedidoRequest request)
    {
        _criaPedido.Executar(request);
        return CreatedAtAction(nameof(CriarPedido), new { id = request.ClienteId });
    }
}
```

# Diagrama Ilustrativo
```plaintext
+-----------------------------+
|     Adaptadores de Entrada  |
|-----------------------------|
|  - Controllers REST         |
|  - CLI / UI / Kafka         |
|                             |
|  Chamam as portas de entrada|
+-------------▼---------------+
              |
+-------------▼---------------+
|        Portas de Entrada    |
|(Interfaces: ex. ICriaPedido)|
+-------------▼---------------+
              |
+-------------▼---------------+
|         Casos de Uso        |
|-----------------------------|
| - Orquestram o domínio      |
| - Independentes de UI/DB    |
+-------------▼---------------+
              |
+-------------▼---------------+
|           Domínio           |
|-----------------------------|
| - Entidades e Regras        |
| - Independente de tudo      |
+-------------▲---------------+
              |
+-------------▲---------------+
|       Portas de Saída       |
|    (Interfaces: ex. IRepo)  |
+-------------▲---------------+
              |
+-------------▲---------------+
|     Adaptadores de Saída    |
|-----------------------------|
| - EF Core / Dapper          |
| - APIs externas             |
| - Repositórios concretos    |
+-----------------------------+
```

# Conclusão

A Arquitetura Hexagonal promove um design **orientado ao domínio**, facilitando a **evolução do sistema** e a **substituição de tecnologias externas** sem impactar a lógica de negócio. No .NET, essa abordagem se alinha naturalmente com recursos como **injeção de dependência, interfaces e testes unitários**.
Adotar este padrão em suas aplicações melhora não apenas a **organização do código**, mas também sua **manutenibilidade e longevidade**.