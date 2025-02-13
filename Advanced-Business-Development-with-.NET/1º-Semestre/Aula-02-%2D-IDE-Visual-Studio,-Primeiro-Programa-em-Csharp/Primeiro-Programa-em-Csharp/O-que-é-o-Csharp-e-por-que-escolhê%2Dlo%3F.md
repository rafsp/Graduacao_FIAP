# Sobre o C#

C# é uma linguagem de programação de código aberto, moderna e inovadora, que faz parte da plataforma .NET [[7]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

É uma das linguagens que compõem a “família” .NET de linguagens [[7]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências). Existem outras linguagens como o Visual Basic e F# que também participam dessa família, porém para as aulas vamos considerar o desenvolvimento em C#.

Com C# é possível criar diversos tipos de aplicativos para diferentes plataformas, como Windows, Linux, Android, iOS e web [[8]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

C# é uma linguagem de programação **orientada a objetos** e **orientada a componentes**. C# fornece construções de linguagem para dar suporte diretamente a esses conceitos, tornando C# uma linguagem natural para criação e uso de componentes de software. Desde sua origem, o C# adicionou recursos para dar suporte a novas cargas de trabalho e práticas emergentes de design de software. Em sua essência, o C# é uma linguagem orientada a objeto. Você define os tipos e o comportamento deles [[9]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

Quando falamos que o C# é uma linguagem orientada a objetos, pode-se considerar o exemplo de código abaixo:

```csharp
// Definindo uma classe Pessoa com atributos e métodos
class Pessoa
{
    // Atributos privados da classe
    private string nome;
    private int idade;
    private double altura;

    // Construtor da classe que recebe os valores dos atributos como parâmetros
    public Pessoa(string nome, int idade, double altura)
    {
        this.nome = nome;
        this.idade = idade;
        this.altura = altura;
    }

    // Método público que retorna o nome da pessoa
    public string GetNome()
    {
        return this.nome;
      
    }

    // Método público que retorna a idade da pessoa
    public int GetIdade()
    {
        return this.idade;
    }

    // Método público que retorna a altura da pessoa
    public double GetAltura()
    {
        return this.altura;
    }

    // Método público que imprime as informações da pessoa
    public void Imprimir()
    {
        Console.WriteLine("Nome: " + this.nome);
        Console.WriteLine("Idade: " + this.idade);
        Console.WriteLine("Altura: " + this.altura);
    }
}

// Criando um objeto da classe Pessoa usando o operador new
Pessoa pessoa = new Pessoa("João", 25, 1.75);

// Acessando os métodos do objeto
Console.WriteLine("O nome da pessoa é " + pessoa.GetNome());
Console.WriteLine("A idade da pessoa é " + pessoa.GetIdade());
Console.WriteLine("A altura da pessoa é " + pessoa.GetAltura());

// Invocando o método Imprimir do objeto
pessoa.Imprimir();
```
      
Esse código demonstra como definir uma classe com atributos e métodos, como criar um objeto a partir de uma classe e como acessar os membros do objeto. Esse é um conceito básico da programação orientada a objetos em C#. Exemplos assim também podem ser encontrados na referência [[10]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

Agora para compreender a orientação de componentes, seria interessante considerarmos como exemplo o código a seguir:

```csharp
// Definindo uma interface IComponente que define um método Comunicar
interface IComponente
{
    void Comunicar();
}

// Definindo uma classe ComponenteA que implementa a interface IComponente
class ComponenteA : IComponente
{
    // Implementando o método Comunicar da interface
    public void Comunicar()
    {
        Console.WriteLine("Olá, eu sou o Componente A");
    }
}

// Definindo uma classe ComponenteB que implementa a interface IComponente
class ComponenteB : IComponente
{
    // Implementando o método Comunicar da interface
    public void Comunicar()
    {
        Console.WriteLine("Olá, eu sou o Componente B");
    }
}

// Definindo uma classe Sistema que usa os componentes A e B
class Sistema
{
    // Criando uma lista de componentes
    private List<IComponente> componentes;

    // Construtor da classe que recebe os componentes como parâmetros
    public Sistema(params IComponente[] componentes)
    {
        // Inicializando a lista de componentes
        this.componentes = new List<IComponente>();

        // Adicionando os componentes à lista
        foreach (IComponente componente in componentes)
        {
            this.componentes.Add(componente);
        }
    }

    // Método que invoca o método Comunicar de cada componente da lista
    public void Executar()
    {
        foreach (IComponente componente in componentes)
        {
            componente.Comunicar();
        }
    }
}

// Criando objetos dos componentes A e B
ComponenteA a = new ComponenteA();
ComponenteB b = new ComponenteB();

// Criando um objeto do sistema passando os componentes A e B como parâmetros
Sistema s = new Sistema(a, b);

// Invocando o método Executar do sistema
s.Executar();
```
      
# Por que escolher o C#?

Considero essa pergunta inviesada, pois depende do perfil de cada pessoa. Contudo, vou abordar algumas questões que eu acredito importantes para aventurarmos com C#.

- **Salário**
  Considerando uma pesquisa feita nos dados da Indeed [[13]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências) no dia 13 de fevereiro de 2024, a faixa salarial média para o cargo de desenvolvedor C# era de R$ 5.573 por mês para o Brasil. Esse valor pode variar de acordo com o nível de experiência, a localização, a empresa e outros fatores.

Utilizando outra referência [[14]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências), um desenvolvedor C# sênior pode ganhar até R$ 18.000 por mês, enquanto um desenvolvedor C# júnior pode ganhar até R$ 8.000 por mês.