# Abstract

O modificador abstract em C# indica que o item que está sendo modificado tem uma implementação ausente ou incompleta [[3]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências).

## Classes Abstratas
      
Uma classe abstrata não pode ser instanciada diretamente. Ela serve como uma classe **base** para outras classes.
Exemplo de uma classe abstrata chamada **Shape** com um método abstrato **GetArea()**:

```csharp
abstract class Shape
{
    public abstract int GetArea();
}

class Square : Shape
{
    private int _side;

    public Square(int n) => _side = n;

    public override int GetArea() => _side * _side;
}

static void Main()
{
    var sq = new Square(12);
    Console.WriteLine($"Área do quadrado = {sq.GetArea()}");
}
// Saída: Área do quadrado = 144
```

Note que a classe **Square** herda da classe abstrata **Shape** e implementa o método abstrato **GetArea()**.

## Métodos Abstratos

