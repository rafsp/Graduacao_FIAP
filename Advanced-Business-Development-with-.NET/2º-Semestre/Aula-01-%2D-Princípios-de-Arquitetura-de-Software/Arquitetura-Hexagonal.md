[[_TOC_]]

A Arquitetura Hexagonal, também conhecida como Arquitetura de Portos e Adaptadores, é um padrão de arquitetura de software que visa criar sistemas que sejam independentes de suas interfaces externas, facilitando a testabilidade e a manutenção do código. Este conceito é especialmente relevante no contexto da plataforma .NET, onde a construção de aplicações robustas e escaláveis é fundamental.

# Domain

O domínio, ou a camada de domínio, é o núcleo da aplicação, onde reside a lógica de negócio. Na arquitetura hexagonal, o domínio não deve ter dependências diretas de frameworks, bibliotecas externas ou de qualquer interface de usuário. Isso permite que a lógica de negócio permaneça pura e facilmente testável.

Por exemplo, em uma aplicação de e-commerce desenvolvida em .NET, o domínio poderia incluir entidades como `Produto`, `Pedido` e `Cliente`. Cada uma dessas entidades conteria suas regras de negócio específicas. Aqui está um exemplo simplificado de uma entidade `Produto`:

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
        Preco = preco < 0 ? throw new ArgumentException(
"Preço não pode ser negativo") : preco;
    }
    
    public void AplicarDesconto(decimal percentual)
    {
        Preco -= Preco * percentual / 100;
    }
}
    
```

# Ports

Os "ports" (portas) são as interfaces que definem a forma como o domínio interage com o mundo exterior. Elas são contratos que descrevem as operações que o domínio pode realizar, sem se preocupar com a implementação específica. Os ports podem ser divididos em dois tipos: **input ports** e **output ports**.

Os **input ports** definem as operações que podem ser solicitadas a partir de interfaces externas, enquanto os **output ports** definem como o domínio se comunica com serviços externos, como bancos de dados ou APIs. Um exemplo de um input port em .NET poderia ser um serviço de aplicação que permite a criação de um novo pedido:

```csharp

public interface ICriaPedido
{
    void Executar(CriaPedidoRequest request);
}

public class CriaPedidoRequest
{
    public int ClienteId { get; set; }
    public List ProdutosIds { get; set; }
}
    
```

# Adapters

Os "adapters" (adaptadores) são as implementações concretas das portas. Eles conectam o mundo externo ao domínio da aplicação. Por exemplo, um adaptador pode ser um controlador de API em uma aplicação ASP.NET Core que manipula requisições HTTP e chama o input port correspondente. Aqui está um exemplo de como um adaptador poderia ser implementado:

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
        return CreatedAtAction(
nameof(CriarPedido), new { id = request.ClienteId });
    }
}
    
```

# Design Exemplo
```plaintext
                         +-----------------------------+
                         |  Adaptadores de Entrada     |
                         |-----------------------------|
                         |  - Controllers REST         |
                         |  - CLI / UI / Kafka Consumer|
                         |                             |
                         |  Chamam as portas           |
                         +-------------┬---------------+
                                       |
                      +----------------▼----------------+
                      |       Portas de Entrada         |
                      |      (Interfaces públicas)      |
                      |  ex: IRegistrarUsuario          |
                      +----------------┬----------------+
                                       | Implementado por
                          +------------▼-------------+
                          |       Casos de Uso       |
                          |--------------------------|
                          |  - Orquestram o domínio  |
                          |  - Não conhecem UI/DB    |
                          +------------┬-------------+
                                       | Usa
                          +------------▼-------------+
                          |         Domínio          |
                          |--------------------------|
                          | - Entidades e regras     |
                          | - Independente de tudo   |
                          +------------▲-------------+
                                       | Define
                      +----------------▼----------------+
                      |       Portas de Saída           |
                      |  (Interfaces: ex. IRepository)  |
                      +----------------▲----------------+
                                       | Implementado por
                          +------------▼--------------+
                          |  Adaptadores de Saída     |
                          |---------------------------|
                          |  - EF Core / Dapper       |
                          |  - APIs externas          |
                          |  - Repositórios concretos |
                          +---------------------------+
```


Neste exemplo, o `PedidosController` atua como um adaptador que transforma requisições HTTP em chamadas para o input port `ICriaPedido`, permitindo que a lógica de criação de pedidos no domínio seja invocada sem que o domínio conheça detalhes sobre a origem da chamada.