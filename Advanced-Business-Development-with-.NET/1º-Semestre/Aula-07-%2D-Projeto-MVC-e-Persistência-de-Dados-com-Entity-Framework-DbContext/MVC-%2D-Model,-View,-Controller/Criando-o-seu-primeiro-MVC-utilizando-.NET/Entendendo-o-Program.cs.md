[[_TOC_]]

# Introdução
      
Quando o projeto foi criado, alguns arquivos “default” foram automaticamente configurados. Entre eles, o arquivo Program.cs .  
O arquivo Program.cs em um projeto C# MVC serve como ponto de entrada para a aplicação. Ele é responsável por inicializar e configurar o host da aplicação web, que inclui:

- Configurar o servidor web e os serviços necessários;
- Definir o pipeline de solicitações HTTP;
- Iniciar a aplicação.

Em versões mais recentes do .NET, como o .NET 6, o arquivo Program.cs também assumiu responsabilidades que anteriormente estavam no arquivo Startup.cs, como a configuração de serviços e middlewares. 

Isso faz parte de uma simplificação geral para tornar o código mais conciso e fácil de entender [4].

Abaixo um exemplo de um código no Program.cs :

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddControllersWithViews();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Home/Error");
    // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();

app.UseRouting();

app.UseAuthorization();

app.MapControllerRoute(
    name: "default",
    pattern: "{controller=Home}/{action=Index}/{id?}");

app.Run();
```

Explicando o código, linha por linha...

```csharp      
var builder = WebApplication.CreateBuilder(args);
```
Cria um novo construtor de aplicação web com os argumentos fornecidos, que geralmente são os argumentos da linha de comando.  

```csharp
builder.Services.AddControllersWithViews();
```
Registra os controladores e as views no contêiner de serviços, permitindo que o MVC seja usado na aplicação.

```csharp
var app = builder.Build();
```
Constrói a aplicação web a partir do construtor.

```csharp      
// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Home/Error");
    // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
    app.UseHsts();
}
```
Configura o pipeline de solicitações HTTP. Se o ambiente não estiver em modo de desenvolvimento, ele usa um manipulador de exceções para as rotas /Home/Error.

```csharp
var app = builder.Build();
```