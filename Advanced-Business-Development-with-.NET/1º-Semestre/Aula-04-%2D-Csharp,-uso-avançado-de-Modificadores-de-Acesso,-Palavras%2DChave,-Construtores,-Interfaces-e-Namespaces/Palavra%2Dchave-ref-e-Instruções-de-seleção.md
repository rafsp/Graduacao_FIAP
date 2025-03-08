[[_TOC_]]

# Ref
  
A palavra-chave **ref** é usada para passar ou retornar referências de valores ou de métodos. Basicamente, isso significa que qualquer alteração feita em um valor que é passado por referência será refletida, pois está sendo modificado o valor no endereço de memória e não apenas o valor em si [[8]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências).
Dessa forma, temos 2 possibilidades:

## Passagem de Argumentos por Referência

Em uma assinatura de método e em uma chamada de método, é possível usar **ref** para passar um argumento para um método por referência. Isso permite que o método modifique o valor original do argumento [[8]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências) :
```csharp
void AlterarValor(ref int numero)
{
  numero += 10;
}

int valor = 5;
AlterarValor(ref valor);
// Agora, valor é 15.
```

## Retorno de Valores por Referência

Também é possível usar **ref** em uma assinatura de método para retornar um valor para o chamador por referência. Isso permite que o método altere o valor original da variável que o chamou [[8]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências).
```csharp
ref int ObterReferencia(ref int[] array)
{
  return ref array[0];
}

int[] meuArray = { 1, 2, 3 };
ref int primeiraPosicao = ref ObterReferencia(ref meuArray);
primeiraPosicao = 10;
// Agora, meuArray[0] é 10.
```

Uma consideração importante é procurar evitar o uso de **ref** desnecessariamente, pois pode tornar o código mais complexo e difícil de entender.

# Instruções de Seleção

As instruções de seleção no C# permitem que seja possível escolher diferentes caminhos de código com base em condições específicas [[9]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências):

## Instrução if

A instrução if executa um bloco de código somente se uma expressão booleana fornecida for avaliada como verdadeira.
```csharp
void DisplayWeatherReport(double tempInCelsius)
{
    if (tempInCelsius < 20.0)
    {
        Console.WriteLine("Frio.");
    }
    else
    {
        Console.WriteLine("Perfeito!");
    }
}
```
  
Neste exemplo, a função **DisplayWeatherReport** exibe **“Frio”** se a temperatura for inferior a 20°C e **“Perfeito!”** caso contrário.

Também é possível aninhar várias instruções **if** para verificar várias condições:
```csharp
void DisplayCharacter(char ch)
{
    if (char.IsUpper(ch))
    {
        Console.WriteLine($"Uma letra maiúscula: {ch}");
    }
    else if (char.IsLower(ch))
    {
        Console.WriteLine($"Uma letra minúscula: {ch}");
    }
    else if (char.IsDigit(ch))
    {
        Console.WriteLine($"Um dígito: {ch}");
    }
    else
    {
        Console.WriteLine($"Caractere não alfanumérico: {ch}");
    }
}
```

## Instrução switch

A instrução **switch** seleciona um conjunto de instruções a serem executadas com base em uma correspondência de padrão com uma expressão.
```csharp
void DisplayMeasurement(double value)
{
    switch (value)
    {
        case < 0:
        case > 100:
            Console.Write("Aviso: valor não aceitável! ");
            break;
        default:
            Console.WriteLine($"O valor da medição é {value}");
            break;
    }
}
```
  
Aqui, a função **DisplayMeasurement** exibe mensagens diferentes com base no valor da medição.