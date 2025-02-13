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

## Salário
Considerando uma pesquisa feita nos dados da Indeed [[13]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências) no dia 30 de janeiro de 2025, a faixa salarial média para o cargo de desenvolvedor C# era de R$ 5.398 por mês para o Brasil. Esse valor pode variar de acordo com o nível de experiência, a localização, a empresa e outros fatores.

Utilizando outra referência, do Programathor [[14]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências), um desenvolvedor C# sênior pode ganhar até R$ 18.000 por mês, enquanto um desenvolvedor C# júnior pode ganhar até R$ 8.000 por mês.

![image.png](/.attachments/image-637c6efa-edc8-4022-9125-0232312afbab.png)

Além disso, algumas cidades como Blumenau, São Paulo e Belo Horizonte oferecem salários mais altos do que outras como Porto Alegre, Ribeirão Preto e Curitiba [[13]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-02-%2D-IDE-Visual-Studio,-Primeiro-Programa-em-Csharp/Referências).

Lembrando que essas informações não são uma regra, pois a mesma pode variar de acordo com a localização, expertise técnica em outras linguagens, tamanho da corporação e experiência profissional.

## Abrangência

C# é uma linguagem de programação muito popular e versátil, que pode ser usada para desenvolver diversos tipos de aplicações, como jogos, aplicativos móveis, sites, serviços web, sistemas operacionais, etc. Muitas grandes empresas utilizam C# nos seus sistemas, tanto para criar produtos internos quanto para oferecer soluções para seus clientes. Aqui estão alguns exemplos de empresas que usam C#:

o   **Delivery Hero:** é um serviço multinacional de entrega de comida online que opera em mais de 50 países, em parceria com mais de 500.000 restaurantes. Delivery Hero usa C# para desenvolver sua plataforma de q-commerce, que permite entregar itens essenciais em menos de uma hora [9].  
  

o   **Stack Overflow:** é um site de perguntas e respostas sobre programação, que conta com mais de 14 milhões de usuários registrados. Stack Overflow usa C# para construir sua interface web, sua API e sua infraestrutura de banco de dados [9].  
  

o   **Trustpilot:** é uma plataforma online de avaliação de empresas, que permite aos consumidores compartilhar suas experiências e opiniões sobre produtos e serviços. Trustpilot usa C# para desenvolver seu sistema de coleta e análise de dados, que processa mais de 4 bilhões de solicitações por mês [9].  
  

o   **Venmo:** é um aplicativo de pagamento móvel, que permite aos usuários enviar e receber dinheiro de forma rápida e fácil. Venmo usa C# para desenvolver seu aplicativo para Windows Phone, que oferece as mesmas funcionalidades que as versões para iOS e Android [9].  
  

o   **PedidosYa:** é uma empresa latino-americana de delivery de comida, que opera em mais de 400 cidades em 12 países. PedidosYa usa C# para desenvolver seu aplicativo móvel, que permite aos usuários fazer pedidos, acompanhar o status da entrega e avaliar os restaurantes [9].

Esses são apenas alguns exemplos de grandes empresas que utilizam C# nos seus sistemas. Há muitas outras, como Microsoft, Amazon, Google, Intel, Oracle, NASA, Dropbox, VMware, LinkedIn, Siemens, etc [10]. C# é uma linguagem que oferece muitas vantagens, como simplicidade, produtividade, desempenho, portabilidade, interoperabilidade, etc. Por isso, ela é uma das linguagens mais requisitadas no mercado de trabalho em 2023 [11].
