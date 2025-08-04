[[_TOC_]]

### Clean Architecture

Clean Architecture é um conceito introduzido por Robert C. Martin (também conhecido como Uncle Bob) que tem como objetivo criar sistemas de software que são independentes de frameworks, bancos de dados, interfaces de usuário e qualquer outra preocupação externa. O foco está em manter uma estrutura clara e bem definida, onde as regras de negócio são isoladas das implementações técnicas. Neste artigo, exploraremos os principais componentes da Clean Architecture, especialmente em um contexto .NET.

#### Entidades

As Entidades são objetos que representam as regras de negócio fundamentais do sistema. Elas são o núcleo da aplicação e devem ser projetadas para serem independentes de qualquer tecnologia específica. Na Clean Architecture, as Entidades devem ser mantidas em um nível mais interno, longe de detalhes como bancos de dados ou interfaces de usuário.

Um exemplo em .NET pode ser uma classe que representa um Usuário, que contém propriedades como Nome, Email e Senha, além de métodos que implementam regras de validação. Veja um exemplo:

```csharp
public class Usuario         
{             
    public string Nome { get; private set; }
    public string Email { get; private set; }
    public string Senha { get; private set; }

    public Usuario(string nome, string email, string senha)             
    {                 
        // Validações podem ser feitas aqui                 
        Nome = nome;                 
        Email = email;                 
        Senha = senha;             
    }              

    public bool ValidarEmail()             
    {                 
        // Implementação de validação de email                 
        return Email.Contains("@");             
    }         
}
```                

#### Casos de Uso

Os Casos de Uso representam as operações que a aplicação pode realizar. Eles orquestram as Entidades e interagem com as interfaces de entrada e saída, definindo a lógica de aplicação. Os Casos de Uso são responsáveis por garantir que a aplicação atue de acordo com as regras de negócio.

Um exemplo de Caso de Uso em .NET poderia ser um serviço que registra um novo usuário. Este serviço usaria a Entidade Usuario e poderia se parecer com o seguinte código:

```csharp
public class RegistrarUsuario         
{             
    private readonly IUsuarioRepository _usuarioRepository;

    public RegistrarUsuario(IUsuarioRepository usuarioRepository)             
    {                 
        _usuarioRepository = usuarioRepository;             
    }              

    public void Executar(string nome, string email, string senha)             
    {                 
        var usuario = new Usuario(nome, email, senha);

        if (!usuario.ValidarEmail()) 
        {                     
            throw new Exception("Email inválido.");
        }

            _usuarioRepository.Adicionar(usuario);
    }         
}
```
        
        

#### Interface de Entrada

A Interface de Entrada é a camada que interage com o usuário ou com outros sistemas. Essa interface pode ser uma API REST, uma interface gráfica de usuário ou até mesmo uma interface de linha de comando. O importante é que a lógica de apresentação não deve estar misturada com as regras de negócio.

Em um projeto .NET, você pode usar o ASP.NET Core para criar uma API que receba solicitações para registrar um usuário. Aqui está um exemplo de um Controller que utiliza o Caso de Uso:

```csharp
[ApiController]
[Route("api/[controller]")]
public class UsuarioController : ControllerBase
{
    private readonly RegistrarUsuario _registrarUsuario;

    public UsuarioController(RegistrarUsuario registrarUsuario)
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
```     

#### Interface de Saída

A Interface de Saída é responsável por interagir com sistemas externos, como bancos de dados, serviços de terceiros ou qualquer outra dependência externa. Em Clean Architecture, essa interface deve ser abstraída para que a lógica de negócio não dependa diretamente de implementações específicas.

No caso do registro de usuário, você pode ter uma interface de repositório para persistir os dados do usuário. Um exemplo em .NET pode ser:

```csharp
public interface IUsuarioRepository
{
    void Adicionar(Usuario usuario);
    Usuario ObterPorEmail(string email);
}

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