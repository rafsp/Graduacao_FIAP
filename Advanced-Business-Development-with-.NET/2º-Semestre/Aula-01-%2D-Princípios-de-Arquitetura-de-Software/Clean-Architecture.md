[[_TOC_]]
    
# Introdução à Clean Architecture
    
A Clean Architecture, proposta por Robert C. Martin (também conhecido como Uncle Bob), é uma abordagem arquitetural que visa a separação clara de responsabilidades em um sistema de software. Seu objetivo é permitir que a lógica de negócio seja completamente independente de frameworks, bancos de dados, interfaces de usuário ou qualquer outro detalhe externo. Isso facilita a manutenção, os testes e a evolução do sistema ao longo do tempo.
    
# Visão Geral da Arquitetura
    
A Clean Architecture propõe a divisão da aplicação em quatro camadas concêntricas:
    
1. **Entidades (Entities)** – Regras de negócio mais fundamentais e independentes.
2. **Casos de Uso (Use Cases)** – Regras específicas de aplicação que orquestram o comportamento do sistema.
3. **Interfaces de Entrada (Interface Adapters)** – Controladores, Gateways e Presenters que adaptam dados entre as camadas internas e externas.
4. **Frameworks e Drivers** – Detalhes externos como bancos de dados, bibliotecas, interfaces gráficas e frameworks web.
    
A **dependência** entre as camadas deve sempre apontar **do externo para o interno**, respeitando o princípio da **inversão de dependência**.
        
# Entidades
    
As Entidades representam conceitos centrais e atemporais do domínio de negócio. Elas encapsulam as regras que são verdadeiras independentemente da aplicação, da interface ou da persistência de dados. Por isso, devem ser projetadas para não depender de nenhuma tecnologia.
    
## Exemplo em .NET
    
```csharp
public class Usuario         
{
    public string Nome { get; }
    public string Email { get; }
    public string Senha { get; }
    
    public Usuario(string nome, string email, string senha)             
    {
            Nome = nome ?? throw new ArgumentNullException(nameof(nome));                 
            Email = email ?? throw new ArgumentNullException(nameof(email));                 
            Senha = senha ?? throw new ArgumentNullException(nameof(senha));             
    }              
}
```

# Casos de Uso

Os Casos de Uso encapsulam regras de negócio específicas da aplicação. Eles coordenam as Entidades e interagem com as portas de entrada e saída (interfaces), garantindo que as regras do sistema sejam executadas corretamente.

### Exemplo em .NET

```csharp
public interface IRegistrarUsuario
{
    void Executar(string nome, string email, string senha);
}
    
public class RegistrarUsuario : IRegistrarUsuario
{
    private readonly IUsuarioRepository _usuarioRepository;
    
    public RegistrarUsuario(IUsuarioRepository usuarioRepository)             
    {
        _usuarioRepository = usuarioRepository;             
    }              
    
    public void Executar(string nome, string email, string senha)             
    {
        if (!email.Contains("@"))
            throw new ArgumentException("Email inválido.");
    
        var usuario = new Usuario(nome, email, senha);        
        _usuarioRepository.Adicionar(usuario);
    }         
}
```

# Interface de Entrada

A Interface de Entrada adapta requisições externas (como APIs HTTP) para chamadas aos casos de uso. Essa camada não contém lógica de negócio, apenas transforma dados de entrada em comandos que os casos de uso podem executar.

## Exemplo em ASP.NET Core
```csharp
[ApiController]
[Route("api/[controller]")]
public class UsuarioController : ControllerBase
{
    private readonly IRegistrarUsuario _registrarUsuario;
    
    public UsuarioController(IRegistrarUsuario registrarUsuario)
    {
        _registrarUsuario = registrarUsuario;
    }
    
    [HttpPost]
    public IActionResult Post([FromBody] UsuarioDto usuarioDto)
    {
        try
        {
            _registrarUsuario.Executar(
                usuarioDto.Nome,
                usuarioDto.Email,
                usuarioDto.Senha
            );
            return Ok("Usuário registrado com sucesso.");
        }
        catch (Exception ex)
        {
            return BadRequest(ex.Message);
        }
    }
}
    
public class UsuarioDto
{
    public string Nome { get; set; }
    public string Email { get; set; }
    public string Senha { get; set; }
}
```

# Interface de Saída

A Interface de Saída representa as dependências externas do sistema, como bancos de dados, sistemas de arquivos, serviços de terceiros, etc. Na Clean Architecture, essas dependências são acessadas através de **interfaces**, que são injetadas nos casos de uso.

## Interface de Repositório
```csharp
public interface IUsuarioRepository
{
    void Adicionar(Usuario usuario);
    Usuario ObterPorEmail(string email);
}
```

### Implementação no projeto de infraestrutura
```csharp
public class UsuarioRepository : IUsuarioRepository
{
    private readonly DatabaseContext _context;
    
    public UsuarioRepository(DatabaseContext context)
    {
        _context = context;
    }
    
    public void Adicionar(Usuario usuario)
    {
        _context.Usuarios.Add(usuario);
        _context.SaveChanges();
    }
    
    public Usuario ObterPorEmail(string email)
    {
        return _context.Usuarios.FirstOrDefault(u => u.Email == email);
    }
}
```    

# Considerações Finais

Ao adotar a Clean Architecture, você obtém um sistema mais desacoplado, testável e flexível a mudanças tecnológicas. Em ambientes .NET, esse padrão é particularmente poderoso quando combinado com injeção de dependência, testes automatizados e separação clara entre domínios.