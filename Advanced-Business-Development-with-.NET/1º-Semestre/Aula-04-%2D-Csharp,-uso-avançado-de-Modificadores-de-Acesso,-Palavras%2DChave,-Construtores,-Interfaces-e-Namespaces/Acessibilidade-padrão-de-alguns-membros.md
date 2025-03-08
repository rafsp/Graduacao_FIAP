[[_TOC_]]

# Introdução

Tipos aninhados, que são membros de outros tipos, podem ter acessibilidades declaradas, conforme a tabela à seguir [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências):


| Membro pai | Padrão de acessibilidade para o membro filho | Acessibilidade permitida para o membro filho |
|--|--|--|
| enum | public | Nenhum |
| class | private | public, protected, internal, private, protected internal, private protected |
| interface | public | public, protected, internal, private, protected internal, private protected |
| struct | private | public, internal, private |

# enum

Em C#, **enum** é uma abreviação de "enumeration" (enumeração), e é um tipo de dados que permite definir um conjunto nomeado de constantes relacionadas. Em outras palavras, um enum é uma **lista de valores** constantes que podem ser usados ​​como valores válidos para uma variável:

```csharp
public enum DiasDaSemana
{
    Segunda,
    Terca,
    Quarta,
    Quinta,
    Sexta,
    Sabado,
    Domingo
}
```

Membros do tipo **enum** tem uma acessibilidade padrão de **public**. Isso significa que todos os membros de um enum são, por padrão, **public**.

Da mesma forma, não é possível definir explicitamente a acessibilidade de "membros filhos" de um **enum**.

Isso não significa que o nível de acessibilidade do próprio **enum** não pode ser alterado. Por exemplo:


```csharp
enum DiasDaSemana
{
    ...
}
```
Tem o **mesmo nível de acessibilidade** de:
```csharp
public enum DiasDaSemana
{
    ...
}
```
Considerando o exemplo acima, segue um exemplo sobre o que **é possível** de ser feito:
```csharp
internal enum DiasDaSemana
{
    ...
}
```
Abaixo, um exemplo sobre o que **não é possível** de ser feito:
```csharp
internal enum DiasDaSemana
{
    internal Segunda,
    internal Terca
    ...
}
```

# class

      
A acessibilidade padrão para membros de uma classe é **private**.
      
Os membros de uma classe podem ser explicitamente declarados como **private**, **public**, **protected**, **internal**, **protected internal** ou **private protected**.

Exemplo:
```csharp
using System;

public class Exemplo
{
    // Acessibilidade padrão (private)
    int valorPadrao = 10; // Equivalente a "private int valorPadrao = 10;"

    // private - Acessível apenas dentro da própria classe
    private int valorPrivado = 20;

    // public - Acessível de qualquer lugar
    public int valorPublico = 30;

    // protected - Acessível dentro da classe e em classes derivadas
    protected int valorProtegido = 40;

    // internal - Acessível dentro do mesmo assembly
    internal int valorInterno = 50;

    // protected internal - Acessível dentro do mesmo assembly e em classes derivadas em qualquer assembly
    protected internal int valorProtegidoInterno = 60;

    // private protected - Acessível apenas dentro da classe e em classes derivadas dentro do mesmo assembly
    private protected int valorPrivadoProtegido = 70;

    public void MostrarValores()
    {
        Console.WriteLine($"Valor Padrão (private implícito): {valorPadrao}");
        Console.WriteLine($"Private: {valorPrivado}");
        Console.WriteLine($"Public: {valorPublico}");
        Console.WriteLine($"Protected: {valorProtegido}");
        Console.WriteLine($"Internal: {valorInterno}");
        Console.WriteLine($"Protected Internal: {valorProtegidoInterno}");
        Console.WriteLine($"Private Protected: {valorPrivadoProtegido}");
    }
}

// Classe derivada para testar os modificadores de acesso
public class Subclasse : Exemplo
{
    public void TestarAcesso()
    {
        // Console.WriteLine(valorPrivado); // Erro: private não é acessível aqui
        Console.WriteLine(valorPublico); // Ok: public é acessível
        Console.WriteLine(valorProtegido); // Ok: protected é acessível em classes derivadas
        Console.WriteLine(valorInterno); // Ok: internal é acessível dentro do mesmo assembly
        Console.WriteLine(valorProtegidoInterno); // Ok: protected internal é acessível em classes derivadas
        Console.WriteLine(valorPrivadoProtegido); // Ok: private protected é acessível, pois está no mesmo assembly
    }
}

class Program
{
    static void Main()
    {
        Exemplo exemplo = new Exemplo();
        exemplo.MostrarValores();
        
        Subclasse sub = new Subclasse();
        sub.TestarAcesso();
    }
}
```

# Interface
  
Interfaces tem uma acessibilidade padrão de **public**. Isso significa que todas as interfaces e seus membros são automaticamente **public**.

Os membros de uma interface podem ser explicitamente declarados como **private**, **public**, **protected**, **internal**, **protected internal** ou **private protected**.

No caso de um membro declarado como **private** dentro de uma **interface**, o mesmo precisará ter uma implementação padrão (sim, existe essa possibilidade, a partir do C# 8):

```csharp
using System;

public interface IExemplo
{
    // Método privado com implementação padrão (permitido a partir do C# 8.0)
    private void MetodoPrivado()
    {
        Console.WriteLine("Este é um método privado com implementação padrão na interface.");
    }

    // Método com implementação padrão que chama o método privado
    void MetodoPublico()
    {
        MetodoPrivado();
    }
}

public class Exemplo : IExemplo
{
    // Nenhuma implementação necessária, pois a interface já fornece uma implementação padrão
}

class Program
{
    static void Main()
    {
        IExemplo exemplo = new Exemplo();
        exemplo.MetodoPublico(); // Saída esperada: "Este é um método privado com implementação padrão na interface."
    }
}
```