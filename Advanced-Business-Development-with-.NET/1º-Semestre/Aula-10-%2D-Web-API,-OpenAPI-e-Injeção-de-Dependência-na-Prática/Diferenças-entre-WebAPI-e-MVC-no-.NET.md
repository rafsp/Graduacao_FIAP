[[_TOC_]]

# Introdução

No ecossistema do .NET, tanto **.NET MVC** quanto **.NET WebAPI** são frameworks para construção de aplicações web, mas eles têm **propósitos** e **focos** diferentes.

## .NET MVC

- **Foco**: Construção de aplicações **web tradicionais**, baseadas em **páginas HTML**.
    
- **Objetivo principal**: Gerar **HTML** que é renderizado nos navegadores.
    
- **Fluxo típico**
  - O navegador faz uma requisição (HTTP GET ou POST);    
  - O servidor responde com **Views** (HTML) renderizadas no lado do servidor.
        
- **Estrutura típica**
  - **Model**: Lida com a lógica de dados (banco de dados, regras de negócio);
  - **View**: Define como a interface é apresentada (HTML/CSS);
  - **Controller**: Gerencia a interação entre Model e View.
        
- **Exemplo**
   ```csharp
   public class HomeController : Controller
   {
      public IActionResult Index()
      {
         return View();
      }
   }
   ```
- **Resposta esperada**: Um arquivo HTML renderizado.

## .NET WebAPI

- **Foco**: Construção de **serviços HTTP** que expõem **dados** (geralmente no formato **JSON**);
    
- **Objetivo principal**: Criar **APIs RESTful** para serem consumidas por clientes como:
  - Aplicações web SPA (ex: Angular, React);
  - Aplicações móveis;
  - Outros sistemas.
        
- **Fluxo típico**
  - O cliente faz uma requisição HTTP (GET, POST, PUT, DELETE);
  - O servidor responde com **dados** (JSON, XML, etc.), sem gerar HTML.
        
- **Estrutura típica**
  - **Controller**: Focado em manipular dados e retornar respostas padronizadas para APIs.
        
- **Exemplo**
   ```csharp    
    [ApiController]
    [Route("api/[controller]")]
    public class ProductsController : ControllerBase
    {
        [HttpGet]
        public IEnumerable<Product> Get()
        {
            return _productService.GetAll();
        }
    }
   ```

- **Resposta esperada**: Um objeto JSON:
   ```json    
    [
      { "id": 1, "name": "Produto A" },
      { "id": 2, "name": "Produto B" }
    ]
   ```

# Principais Diferenças

| Característica | MVC | WebAPI |
| --- | --- | --- |
| Resposta principal | HTML | JSON/XML |
| Público-alvo | Navegadores | Aplicações clientes (web, mobile) |
| Base controller | `Controller` | `ControllerBase` + `[ApiController]` |
| Retorno de métodos | Views ou Resultados de Ação | Dados serializados (JSON/XML) |
| Tipos de requisição comum | GET, POST | GET, POST, PUT, DELETE |

# Observação Importante

No **.NET**, os dois frameworks foram **unificados** em uma estrutura única, permitindo que você misture **MVC** e **API Controllers** dentro do mesmo projeto, dependendo da necessidade.