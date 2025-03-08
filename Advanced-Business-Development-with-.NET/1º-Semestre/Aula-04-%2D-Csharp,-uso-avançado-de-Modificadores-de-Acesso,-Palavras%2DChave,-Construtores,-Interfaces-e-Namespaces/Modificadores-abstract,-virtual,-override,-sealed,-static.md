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

Propriedades virtuais funcionam de maneira semelhante a métodos virtuais, mas são usadas para acessar campos de dados.
Exemplo de uma propriedade virtual chamada **Name**:

```csharp      
class MyBaseClass
{
    // Propriedade virtual com implementação automática.
    public virtual string Name { get; set; }

    // Propriedade virtual com campo de suporte.
    private int _num;
    public virtual int Number
    {
        get { return _num; }
        set { _num = value; }
    }
}

class MyDerivedClass : MyBaseClass
{
    private string _name;

    // Substituição da propriedade para fornecer comportamento especializado.
    public override string Name
    {
        get
        {
            return _name;
        }
        set
        {
            if (!string.IsNullOrEmpty(value))
            {
                _name = value;
            }
            else
            {
                _name = "Unknown";
            }
        }
    }
}
```

Perceba que no exemplo acima, a propriedade virtual foi declarada mesmo dentro de uma classe que não é abstrata. Isso é possível.

A diferença é que, quando um método ou propriedade é declarado como **virtual** em uma classe **abstrata**, estamos dando ênfase a sua **implementação**. O conceito de classe abstrata enfatiza contratos e obrigações, enquanto outros tipos de classes oferecem flexibilidade sem obrigações rígidas.

Isso transparece de uma forma para que todas as classes derivadas tenham uma versão do método ou propriedade, mesmo que essa versão seja diferente para cada classe.

## Override

      
O modificador **override** fornece uma **nova implementação** de um membro herdado de uma classe base [[5]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Ele permite que os membros sejam substituídos em classes derivadas. À seguir um exemplo de método com o modificador **override**:

```csharp
abstract class Shape
{
    public abstract int GetArea();
}

class Square : Shape
{
    private int _side;

    public Square(int n) => _side = n;

    // O método GetArea é necessário para evitar um erro de compilação.
    public override int GetArea() => _side * _side;

    static void Main()
    {
        var sq = new Square(12);
        Console.WriteLine($"Área do quadrado = {sq.GetArea()}");
    }
}
// Saída: Área do quadrado = 144
```

Neste exemplo:
- A classe **Square** herda de **Shape**;
- O método **GetArea()** na classe **Square** substitui o método abstrato **GetArea()** da classe base **Shape**.
- O uso do modificador **override** indica que estamos fornecendo uma nova implementação para o método herdado.
  
Além disso, aqui estão algumas informações importantes sobre o uso do override:
- O método base substituído deve ser **virtual**, **abstract** ou **override**;
- Uma declaração override **não** pode alterar a acessibilidade do método **virtual**.

## Sealed

O modificador sealed em C# é usado para restringir a herança de classes, métodos ou propriedades.

Também é possível usar o modificador **sealed** em um método ou propriedade que substitui um método ou propriedade virtual em uma classe base. Com isso, é possível permitir que classes sejam derivadas de sua classe e impedir que substituam métodos ou propriedades virtuais [[6]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Abaixo um exemplo:

```csharp
class X
{
    protected virtual void F() { Console.WriteLine("X.F"); }
    protected virtual void F2() { Console.WriteLine("X.F2"); }
}

class Y : X
{
    sealed protected override void F() { Console.WriteLine("Y.F"); }
    protected override void F2() { Console.WriteLine("Y.F2"); }
}

class Z : Y
{
    // Tentar substituir F causa erro de compilação CS0239.
    // protected override void F() { Console.WriteLine("Z.F"); }
    // Substituir F2 é permitido.
    protected override void F2() { Console.WriteLine("Z.F2"); }
}
```