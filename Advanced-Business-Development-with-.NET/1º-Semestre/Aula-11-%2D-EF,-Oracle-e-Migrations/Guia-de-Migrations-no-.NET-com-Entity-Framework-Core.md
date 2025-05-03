[[_TOC_]]

# O que é Migration?

**Migration** (ou migração) é um recurso do **Entity Framework Core (EF Core)** que permite controlar a evolução do esquema do banco de dados (tabelas, colunas, relações) a partir do código C#. Ele mantém sincronizado o modelo de dados da aplicação com o banco de dados real, de forma automatizada.

## Pré-requisitos

Antes de usar migrations, é necessário:
*   Ter um projeto .NET com **Entity Framework Core** instalado;    
*   Definir um **DbContext** e classes de entidades (models);
*   Ter configurado a **string de conexão** no `appsettings.json`.

# Como aplicar Migrations — Passo a Passo

## Instalar os pacotes necessários

Executar no terminal do projeto (caso ainda não tenha instalado):
```csharp
dotnet add package Microsoft.EntityFrameworkCore
dotnet add package Oracle.EntityFrameworkCore
dotnet add package Microsoft.EntityFrameworkCore.Tools
```

## Configurar o `DbContext`
Exemplo:
```csharp
public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options)
        : base(options) { }

    public DbSet<Cliente> Clientes { get; set; }
}
``` 

# Configurar o `Program.cs`:
`Program.cs`:
```csharp
    builder.Services.AddDbContext<AppDbContext>(options =>
        options.UseOracle(builder.Configuration.GetConnectionString("DefaultConnection")));
``` 

`appsettings.json`:
```csharp
    "ConnectionStrings": {
      "DefaultConnection": "Server=localhost;Database=MinhaBase;Trusted_Connection=True;"
    } 
```

### 3. Crie a primeira Migration

Comando no terminal (na raiz do projeto):

    dotnet ef migrations add Inicial
    

> 💡 Substitua "Inicial" pelo nome que quiser dar à sua migração.

Esse comando:
*   Cria uma pasta chamada `Migrations`.
    
*   Gera arquivos com instruções C# para criar o banco de dados conforme o modelo atual.
    

* * *

### 4. Aplique a migration ao banco de dados

    dotnet ef database update
    

Esse comando:
*   Cria o banco de dados (caso ainda não exista).
    
*   Aplica a migração no banco.
    

* * *

### 5. Adicionando novas alterações

Se você alterar ou adicionar propriedades nas classes de modelo, siga os passos abaixo:

    dotnet ef migrations add NovaAlteracao
    dotnet ef database update
    

* * *

📁 Organização
--------------

*   A pasta `Migrations` contém:
    *   Arquivos `.cs` com código gerado para criar/modificar tabelas.
        
    *   Um snapshot (`ModelSnapshot`) da estrutura atual do banco.
        

* * *

🧹 Comandos úteis
-----------------

| Comando | Descrição |
| --- | --- |
| `dotnet ef migrations remove` | Remove a última migração ainda não aplicada |
| `dotnet ef migrations list` | Lista todas as migrations |
| `dotnet ef database update` | Aplica todas as migrations pendentes |
| `dotnet ef database update NomeDaMig` | Aplica até uma migration específica |
| `dotnet ef migrations script` | Gera um script SQL da migration |

* * *

❗ Dicas Importantes
-------------------

*   Sempre **comite suas migrations** no controle de versão (ex: Git).
    
*   Evite editar arquivos de migration manualmente.
    
*   Para ambientes de produção, revise e teste bem antes de aplicar migrations automáticas.