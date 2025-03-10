[[_TOC_]]

# Introdução

Agora que temos um repositório público disponível através do GitHub, o próximo passo está em criar os projetos no VS Code. Para isso, entre no Visual Studio Code e abra a pasta do repositório ou siga o procedimento abaixo:

# Abrir o repositório do GitHub no VS Code

![animacao.gif](/.attachments/animacao-b52fbd7d-c3d0-4383-8232-2ddccee63a17.gif)

# Criar e desenvolver a library para Struct

1. Dentro do Visual Studio Code, no Terminal (Ctrl + aspas simples), digite a linha abaixo para criar um novo projeto do tipo library:
   ```csharp
   dotnet new classlib -n StructProject --force
   ```
   ![animacao.gif](/.attachments/animacao-267eeec8-25d2-49ff-9ca3-6884b3e51423.gif)
2. Crie um arquivo chamado ``PontoStruct.cs`` e escreva o código abaixo:
   ```csharp
   namespace StructProject;

   public struct PontoStruct
   {
      public int X { get; }
      public int Y { get; }

       public PontoStruct(int x, int y)
       {
          X = x;
          Y = y;
       }

       public double Distancia(PontoStruct outro)
       {
          int deltaX = X - outro.X;
          int deltaY = Y - outro.Y;
          return Math.Sqrt(deltaX * deltaX + deltaY * deltaY);
       }
   }
   ```
   ![animacao.gif](/.attachments/animacao-801055fe-3424-4b22-abef-6cdf5b9c6533.gif)
3. Agora vamos buildar o projeto, para ver se está tudo certo
   ```csharp
   dotnet build
   ```
   ![animacao.gif](/.attachments/animacao-cd4be883-ddc1-4ec8-af7d-e77a72c59d6e.gif)

# Criar e desenvolver a library para Class

4. Vamos repetir o procedimento acima, porém dessa vez criando um projeto para Class
   ```csharp
   dotnet new classlib -n ClassProject --force
   ```
   ```csharp
   namespace ClassProject;

   public class PontoClass
   {
       public int X { get; }
       public int Y { get; }

       public PontoClass(int x, int y)
       {
           X = x;
           Y = y;
       }

       public double Distancia(PontoClass outro)
       {
           int deltaX = X - outro.X;
           int deltaY = Y - outro.Y;
           return Math.Sqrt(deltaX * deltaX + deltaY * deltaY);
       }
   }
   ```
   ![animacao.gif](/.attachments/animacao-69b36369-a209-4fb8-be2a-cad28fc4dc3c.gif)
   
# Criar e desenvolver o projeto Console

Já temos o projeto ClassProject e StructProject criados. O próximo passo está em criar o projeto responsável por chamar as libraries e fazer o nosso teste simples de performance

```csharp
dotnet new console -n PerformanceTest --force
```