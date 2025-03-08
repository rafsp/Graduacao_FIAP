As interfaces em C# são uma parte importante da linguagem e permitem definir contratos que as classes devem seguir [11]. Vamos explorar os conceitos relacionados a interfaces:

# O que é uma Interface?
- Uma interface define um contrato;
- Qualquer classe/struct que implemente esse contrato deve fornecer uma implementação dos membros definidos na interface;  
- As interfaces permitem uma separação clara entre a definição da interface e a implementação nas classes.
**Sintaxe de uma Interface**
- Uma interface é como uma classe base abstrata que contém apenas **membros abstratos**.
- Os membros de uma interface podem ser:

## Métodos
```csharp
public interface IDisplayable
{
    void Display();
}
```

## Propriedades
```csharp
public interface ISampleInterface
{
    // Declaração de propriedade:
    string Name { get; set; }
}
```

## Eventos
```csharp
public interface IDrawingObject
{
    // Declare an event in the interface
    event EventHandler ShapeChanged;
}
```

## Indexadores
```csharp
public interface IIndexInterface
{
    // Declaração do indexador:
    int this[int index] { get; set; }
}
```

## Implementações Padrão
```csharp
public interface IControl
{
    // Método com implementação padrão
    void Paint() => Console.WriteLine("Método Paint padrão");
}
```

**Exemplo de implementação dos membros da Interface em C#**
```csharp
interface ISampleInterface
{
    void SampleMethod();
}

class ImplementationClass : ISampleInterface
{
    // Implementação explícita do método da interface:
    void ISampleInterface.SampleMethod()
    {
        // Implementação do método.
    }

    static void Main()
    {
        // Criando uma instância da interface.
        ISampleInterface obj = new ImplementationClass();
        // Chamando o método da interface.
        obj.SampleMethod();
    }
}
```