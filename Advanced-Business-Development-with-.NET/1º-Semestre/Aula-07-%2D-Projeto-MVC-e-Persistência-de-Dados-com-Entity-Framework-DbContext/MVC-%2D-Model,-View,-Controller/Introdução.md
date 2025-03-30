[[_TOC_]]

# Introdução ao MVC (Model-View-Controller)      
O MVC é um padrão de design usado para desacoplar a interface do usuário (a exibição), os dados (o modelo) e a lógica do aplicativo (o controlador). Esse padrão ajuda a obter uma separação das preocupações [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

O padrão de arquitetura MVC (Model-View-Controller) separa um aplicativo em três grupos de componentes principais: Modelos, Exibições e Componentes. Esse padrão ajuda a obter a separação de interesses. Usando esse padrão, as solicitações de usuário são encaminhadas para um Controlador, que é responsável por trabalhar com o Modelo para executar as ações do usuário e/ou recuperar os resultados de consultas. O Controlador escolhe a Exibição a ser exibida para o usuário e fornece-a com os dados do Modelo solicitados [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

O seguinte diagrama mostra os três componentes principais e quais deles referenciam os outros:

::: mermaid
 graph TD; 
 View-->|Referencia|Model; Controller-->|Referencia|Model; Controller-->|Renderiza|View;
:::

# Models
O Modelo em um aplicativo MVC representa o estado da aplicação e qualquer lógica de negócios ou operação que deve ser executada por ele. A lógica de negócios deve ser encapsulada no modelo, juntamente com qualquer lógica de implementação, para persistir o estado. As exibições fortemente tipadas normalmente usam tipos ViewModel criados para conter os dados a serem exibidos nessa exibição. O controlador cria e popula essas instâncias de ViewModel com base no modelo [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

Através dos models é possível definir regras de validação declarativamente, usando atributos C#, que são aplicados no cliente e no servidor [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

Exemplo de Model:
```csharp
public class Person
{
    public int PersonId { get; set; }

    [Required]
    [MinLength(2)]
    public string Name { get; set; }

    [Phone]
    public string PhoneNumber { get; set; }

    [EmailAddress]
    public string Email { get; set; }
}
```

#Views

As exibições são responsáveis por apresentar o conteúdo por meio da interface do usuário. Elas usam o mecanismo de exibição do Razor para inserir o código .NET em uma marcação HTML. Deve haver uma lógica mínima nas exibições e qualquer lógica contida nelas deve se relacionar à apresentação do conteúdo. Se você precisar executar uma grande quantidade de lógica em arquivos de exibição para exibir dados de um modelo complexo, considere o uso de um Componente de Exibição, ViewModel ou um modelo de exibição para simplificar a exibição [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

Através do Razor é possível desenvolver, de uma maneira simples, clara e leve, a renderização de um conteúdo HTML com base em sua exibição. O Razor permite renderizar uma página usando C#, produzindo páginas da Web totalmente compatíveis com HTML5 [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

A abordagem mais robusta é especificar um tipo de modelo na exibição. Esse modelo é conhecido como viewmodel. Você passa uma instância do tipo viewmodel para a exibição da ação [[3]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

Usar um viewmodel para passar dados para uma exibição permite que a exibição tire proveito da verificação de tipo forte. Tipagem forte (ou fortemente tipado) significa que cada variável e constante têm um tipo definido explicitamente (por exemplo, string, int ou DateTime). A validade dos tipos usados em uma exibição é verificada em tempo de compilação [[3]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

Exemplo de View:
```html
@model WebApplication1.ViewModels.Address

<h2>Contact</h2>
<address>
    @Model.Street<br>
    @Model.City, @Model.State @Model.PostalCode<br>
    <abbr title="Phone">P:</abbr> 425.555.0100
</address>
```

# Controllers
      
Os controladores são os componentes que cuidam da interação do usuário, trabalham com o modelo e, em última análise, selecionam uma exibição a ser renderizada. Em um aplicativo MVC, a exibição mostra apenas informações; o controlador manipula e responde à entrada e à interação do usuário. No padrão MVC, o controlador é o ponto de entrada inicial e é responsável por selecionar quais tipos de modelo serão usados para o trabalho e qual exibição será renderizada (daí seu nome – ele controla como o aplicativo responde a determinada solicitação) [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-07-%2D-Projeto-MVC-e-Persistência-de-Dados-com-Entity-Framework-DbContext/Referências).

Abaixo um exemplo de Controller:
```csharp
[Route("api/[controller]")]
public class ProductsController : Controller
{
    [HttpGet("{id}")]
    public IActionResult GetProduct(int id)
    {
      ...
    }
}
```

Abaixo um exemplo de validação de uma ViewModel dentro de uma Action:
```csharp
public async Task<IActionResult> Login(LoginViewModel model)
{
    if (ModelState.IsValid)
    {
      // work with the model
    }
    // At this point, something failed, redisplay form
    return View(model);
}
```