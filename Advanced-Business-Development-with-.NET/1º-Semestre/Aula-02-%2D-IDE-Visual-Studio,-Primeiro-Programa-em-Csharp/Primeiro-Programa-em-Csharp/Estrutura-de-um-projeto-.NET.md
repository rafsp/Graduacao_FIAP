Um projeto .NET é uma coleção de arquivos que contém código-fonte, recursos, configurações e referências a bibliotecas que são usadas para compilar e executar um aplicativo ou uma biblioteca. Um projeto .NET, em conjunto com o C#, pode ter uma das seguintes estruturas:

## SDK-style

Um projeto **SDK-style**, que usa um formato simplificado de arquivo de projeto baseado em **XML** e pode ser direcionado a **múltiplas plataformas** e versões do .NET. Esse tipo de projeto é recomendado para projetos novos ou migrados que usam o .NET Core, o .NET Standard ou o .NET 5 ou superior [[21]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="13.0.1" />
  </ItemGroup>
</Project>
```

## 