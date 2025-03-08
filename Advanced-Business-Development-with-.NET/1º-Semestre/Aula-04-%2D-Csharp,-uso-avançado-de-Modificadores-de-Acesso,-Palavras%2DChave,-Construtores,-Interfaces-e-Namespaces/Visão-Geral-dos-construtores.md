# O que são construtores?
Um construtor em C# é chamado quando uma classe (class) ou estrutura (struct) é criada [10].
Utilizamos construtores para:
- Definir valores padrão;
- Limitar a instanciação;
- Escrever código flexível e fácil de ler.

# Sintaxe do Construtor
Um construtor é um método cujo nome é igual ao nome de seu tipo. A assinatura do método inclui:
- Modificador de acesso (opcional);
- Nome do método;
- Lista de parâmetros (não inclui tipo de retorno).
```csharp
public class Person
{
    private string last;
    private string first;

    public Person(string lastName, string firstName)
    {
        last = lastName;
        first = firstName;
    }

    // Restante da implementação da classe Person.
}
```
  
Se um construtor puder ser implementado como uma única instrução, podemos usar uma definição de **corpo da expressão**.
```csharp
public class Location
{
    private string locationName;

    public Location(string name) => Name = name;

    public string Name
    {
        get => locationName;
        set => locationName = value;
    }
}
```

Ademais, um construtor estático em C# é usado para inicializar dados estáticos ou executar uma ação específica que precisa ocorrer apenas uma vez. Ele é chamado automaticamente antes que a primeira instância da classe seja criada ou antes que quaisquer membros estáticos sejam referenciados. Aqui está um exemplo:
```csharp
class MinhaClasse
{
    // Variável estática que deve ser inicializada em tempo de execução.
    static readonly long baseline;

    // Construtor estático é chamado no máximo uma vez, antes que qualquer
    // construtor de instância seja invocado ou membro seja acessado.
    static MinhaClasse()
    {
        baseline = DateTime.Now.Ticks;
    }
}

class Program
{
    static void Main()
    {
        // Criando uma instância da classe MinhaClasse.
        MinhaClasse instancia1 = new MinhaClasse();

        // Verificando o valor da variável estática baseline.
        Console.WriteLine($"Valor da baseline: {MinhaClasse.baseline}");
    }
}
```

# Considerações
  
Se não especificarmos um modificador de acesso para um construtor, ele será considerado **private** por padrão.  
Um construtor privado é útil quando queremos restringir a criação de instâncias da classe fora dela mesma.
  
No caso abaixo por exemplo está sendo restringido a criação de uma instância da classe por outros membros:
```csharp
public class Counter
{
    // Construtor privado
    private Counter()
    {
        // Este construtor não pode ser chamado externamente.
    }

    // Propriedade estática para contar
    public static int CurrentCount { get; private set; }

    // Método estático para incrementar o contador
    public static int IncrementCount()
    {
        return ++CurrentCount;
    }
}
```
  
Nesta classe:
- O construtor **Counter** é privado, o que significa que não pode ser chamado fora da própria classe;
- A propriedade **CurrentCount** é pública e estática, permitindo que seja acessada de qualquer lugar;
- O método **IncrementCount()** também é público e estático, permitindo que outros códigos incrementem o contador.

Agora, vamos criar um exemplo na classe **TestCounter** para demonstrar um exemplo de uso da classe **Counter**:
```csharp
class TestCounter
{
    static void Main()
    {
        // Se descomentarmos a seguinte linha, ocorrerá um erro,
        // pois o construtor é inacessível:
        // Counter aCounter = new Counter();

        // Incrementamos o contador
        Counter.IncrementCount();

        // Exibimos o novo valor do contador
        Console.WriteLine($"Novo contador: {Counter.CurrentCount}");

        // Mantemos a janela do console aberta no modo de depuração
        Console.WriteLine("Pressione qualquer tecla para sair.");
        Console.ReadKey();
    }
}
```