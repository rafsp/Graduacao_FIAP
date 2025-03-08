[[_TOC_]]      

# Introdução

O .NET usa namespaces para organizar suas muitas classes [[12]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências).
## Namespace
Por exemplo, a classe **Console** está no namespace **System**. Portanto, podemos usar **System.Console.WriteLine("Hello World!")** para exibir uma mensagem no console.

```csharp
namespace MeuProjeto
{
    class Program
    {
        static void Main()
        {
            System.Console.WriteLine("Hello World!");
        }
    }
}
```

## Using
Também podemos utilizar a diretiva **using** para considerar a chamada do **Console.WriteLine** dentro da **Main()**:
```csharp
using System;

namespace MeuProjeto
{
    class Program
    {
        static void Main()
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```