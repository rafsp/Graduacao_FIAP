[[_TOC_]]


# Introdução

Um projeto .NET é uma coleção de arquivos que contém código-fonte, recursos, configurações e referências a bibliotecas que são usadas para compilar e executar um aplicativo ou uma biblioteca. Um projeto .NET, em conjunto com o C#, pode ter uma das seguintes estruturas:

# Tipos de Projetos

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

## Não SDK-style

Um projeto **não SDK-style**, que usa um formato mais detalhado de arquivo de projeto baseado em XML e é direcionado ao .NET Framework. Esse tipo de projeto é mais comum em projetos existentes que usam o .NET Framework 4.8 ou inferior [[22]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
    <ProductVersion>10.0.30319</ProductVersion>
    <SchemaVersion>2.0</SchemaVersion>
    <ProjectGuid>{INSERT-GUID-HERE}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <AppDesignerFolder>Properties</AppDesignerFolder>
    <RootNamespace>MyProject</RootNamespace>
    <AssemblyName>MyProject</AssemblyName>
    <TargetFrameworkVersion>v4.8</TargetFrameworkVersion>
    <FileAlignment>512</FileAlignment>
    <Deterministic>true</Deterministic>
  </PropertyGroup>

  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    <LangVersion>8.0</LangVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugType>pdbonly</DebugType>
    <Optimize>true</Optimize>
    <OutputPath>bin\Release\</OutputPath>
    <DefineConstants>TRACE</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    <LangVersion>8.0</LangVersion>
  </PropertyGroup>
  <ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Core" />
    <Reference Include="System.Xml.Linq" />
    <Reference Include="System.Data.DataSetExtensions" />
    <Reference Include="Microsoft.CSharp" />
    <Reference Include="System.Data" />
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Xml" />
  </ItemGroup>
  <ItemGroup>
    <Compile Include="Program.cs" />
    <!-- Outros arquivos de código -->
  </ItemGroup>
  <ItemGroup>
    <None Include="App.config" />
  </ItemGroup>
</Project>
```

# Extensões de Arquivos
      
As extensões de projetos e solução no Visual Studio .NET são os arquivos que armazenam as informações sobre os componentes da solução, como os projetos, as configurações, as referências e as propriedades. As extensões mais comuns são:

## .sln

É o arquivo da solução, que contém os metadados sobre os projetos e as configurações da solução. Ele também define a ordem de compilação dos projetos e as dependências entre eles [[23]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

## .csproj, .vbproj, .fsproj

