[[_TOC_]]

Agora que tivemos um entendimento base sobre como que funciona uma aplicação dentro do visual studio, o próximo passo está em criarmos mais um Hello World (Olá Mundo), dessa vez utilizando a IDE e na versão Web 😊

# Criando o projeto
      
1. Primeiro, será necessário criar um novo projeto entrando em “File > New > Project”:
   ![image.png](/.attachments/image-eb0a6df8-a62c-4c39-bd75-40ad980284ea.png)
      
2. Depois, selecionar “ASP.NET Core Empty”, conforme ilustração:
   ![image.png](/.attachments/image-22af6e73-594a-4b0d-b2f8-ac68d0814d36.png)
   
3. Seguir os passos abaixo:
   ![image.png](/.attachments/image-96fb50d7-57bf-424f-b21e-fdadd272431e.png)

   ![image.png](/.attachments/image-bd9a33f5-8b01-4839-ab51-45627b27b412.png)

4. O projeto deverá ficar conforme abaixo
   
   ![image.png](/.attachments/image-ee6cb582-68dd-44d5-ae0f-8d5164ccf249.png)

5. Agora, em Program.cs, escreva, além de "Hello World", "Olá Mundo FIAP":

   ```csharp
   var builder = WebApplication.CreateBuilder(args);
   var app = builder.Build();

   app.MapGet("/", () => "Olá Mundo FIAP!");

   app.Run();
   ```

# Explicando o projeto

Agora que temos o nosso projeto em mãos, podemos verificar cada parte do código, como por ex os namespaces, classes e métodos.

## launchSettings.json

![image.png](/.attachments/image-65e40fcc-7d04-459b-8bc2-a4806fe0d0fc.png)

Possui as configurações de iniciação e disponibilização da solução.

```json
{
  "$schema": "https://json.schemastore.org/launchsettings.json",
  "profiles": {
    "http": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "applicationUrl": "http://localhost:5078",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

## Program.cs

```csharp
var builder = WebApplication.CreateBuilder(args);
```
      
Serve para criar uma instância da classe WebApplicationBuilder, que é usada para configurar e construir uma aplicação web usando o ASP.NET Core. O parâmetro args é um array de strings que contém os argumentos da linha de comando passados para o programa [[26]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências). O WebApplicationBuilder permite adicionar serviços, configurar o ambiente, definir pontos finais de roteamento e outras opções para a aplicação web.
   
```csharp
var app = builder.Build();
```