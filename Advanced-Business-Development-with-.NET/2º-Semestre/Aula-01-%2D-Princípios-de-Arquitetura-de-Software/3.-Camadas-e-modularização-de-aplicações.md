[[_TOC_]]

## Camadas e Modularização de Aplicações

A modularização é um princípio fundamental na arquitetura de software, que pode ser implementado através de camadas. Em um sistema arquitetado em camadas, cada camada tem uma responsabilidade específica, promovendo separação de preocupações.

### Exemplo de Estrutura em Camadas

*   **Camada de Apresentação:** Responsável pela interface do usuário. Em uma aplicação .NET, isso pode ser implementado por exemplo com ASP.NET MVC ou Blazor.
*   **Camada de Negócios:** Contém a lógica de negócio da aplicação. Essa camada orquestra as operações e validações.
*   **Camada de Acesso a Dados:** Interage com o banco de dados. Em .NET, isso pode ser feito com Entity Framework Core.
*   **Camada de Serviços:** Pode incluir serviços externos ou microservices que a aplicação consome.

Considerando uma aplicação de e-commerce, os casos de uso para essa aplicação podem incluir:

*   Registro de Usuário
*   Login do Usuário
*   Adicionar Produtos ao Carrinho
*   Checkout
*   Visualização de Pedidos

A modularização permite que cada um desses casos de uso seja tratado em uma camada específica, facilitando a manutenção e a evolução do software. A estrutura típica em camadas pode ser dividida em:

*   **Camada de Apresentação:** Responsável pela interface do usuário e interação.
*   **Camada de Lógica de Negócio:** Contém as regras de negócio e a lógica da aplicação.
*   **Camada de Acesso a Dados:** Responsável pela interação com o banco de dados.
*   **Camada de Banco de Dados:** Onde os dados são fisicamente armazenados.

### Vantagens da Modularização

*   Facilidade de manutenção: Mudanças em uma camada não impactam diretamente as outras.
*   Testabilidade: Cada módulo pode ser testado de forma independente.
*   Reusabilidade: Módulos podem ser reutilizados em diferentes partes da aplicação ou em outras aplicações.

### Exemplos Práticos em CSharp

#### Camada de Apresentação (ASP.NET MVC)

No ASP.NET MVC, a camada de apresentação pode ser implementada com controladores e views:

```csharp

public class HomeController : Controller
{
    private readonly IProductService _productService;

    public HomeController(IProductService productService)
    {
        _productService = productService;
    }

    public IActionResult Index()
    {
        var products = _productService.GetAllProducts();
        return View(products);
    }
}
```

#### Camada de Negócios

A camada de negócios contém a lógica de negócio da aplicação:

```csharp

public class ProductService : IProductService
{
    private readonly IProductRepository _productRepository;

    public ProductService(IProductRepository productRepository)
    {
        _productRepository = productRepository;
    }

    public IEnumerable GetAllProducts()
    {
        return _productRepository.GetAll();
    }
}
```

#### Camada de Acesso a Dados (Entity Framework Core)

A camada de acesso a dados pode ser implementada usando o Entity Framework Core:

```csharp

public class ApplicationDbContext : DbContext
{
    public DbSet Products { get; set; }

    public ApplicationDbContext(DbContextOptions options) : base(options)
    {
    }
}

public class ProductRepository : IProductRepository
{
    private readonly ApplicationDbContext _context;

    public ProductRepository(ApplicationDbContext context)
    {
        _context = context;
    }

    public IEnumerable GetAll()
    {
        return _context.Products.ToList();
    }
}
```

#### Camada de Serviços

A camada de serviços pode consumir APIs externas ou microservices:

```csharp

public class ExternalApiService : IExternalApiService
{
    private readonly HttpClient _httpClient;

    public ExternalApiService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<WeatherForecast> GetWeatherForecastAsync(string city)
    {
        var response = await _httpClient.
GetAsync($"https://api.weather.com/v3/wx/forecast/daily/5day?city={city}");
        response.EnsureSuccessStatusCode();

        var content = await response.Content.ReadAsStringAsync();
        return JsonConvert.DeserializeObject<WeatherForecast>(content);
    }
}
```