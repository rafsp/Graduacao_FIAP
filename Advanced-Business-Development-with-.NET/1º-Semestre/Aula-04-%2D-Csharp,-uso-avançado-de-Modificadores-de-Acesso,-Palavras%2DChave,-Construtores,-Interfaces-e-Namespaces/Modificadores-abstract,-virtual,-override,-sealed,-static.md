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

Um método abstrato não possui uma implementação real (corpo). Ele é declarado apenas na classe abstrata e deve ser implementado pelas classes derivadas.
Exemplo de uma classe abstrata **Animal** com um método abstrato **makeSound()**.

```csharp
abstract class Animal
{
    public abstract void makeSound();
}

class Dog : Animal
{
    public override void makeSound()
    {
        Console.WriteLine("Au Au");
    }
}

static void Main()
{
    var dog = new Dog();
    dog.makeSound();
}
// Saída: Au Au
```

Aqui, a classe **Dog** herda de **Animal** e fornece a implementação do método abstrato **makeSound()**.
Caso o método makeSound() não seja implementado pela classe Dog, então teremos o erro à seguir:

![image.png](/.attachments/image-c99c0f53-733a-467a-a03a-d90933392258.png)

# Virtual

## Métodos Virtuais

O modificador **virtual** é usado para modificar implementações em C# [[4]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Ele permite que os membros sejam substituídos em classes derivadas. À seguir um exemplo de método com o modificador **virtual**:

```csharp
public virtual double Area()
{
    return x * y;
}
```

## Propriedades Virtuais
