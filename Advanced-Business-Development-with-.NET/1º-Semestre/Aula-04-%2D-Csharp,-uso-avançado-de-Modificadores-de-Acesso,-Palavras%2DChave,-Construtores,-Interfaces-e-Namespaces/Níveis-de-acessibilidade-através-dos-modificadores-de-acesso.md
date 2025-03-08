[[_TOC_]]

Os modificadores de acesso são palavras-chave usadas para especificar a acessibilidade declarada de um membro ou de um tipo [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências).

A seguir é apresentado 7 níveis de acessibilidade que podem ser especificados utilizando os modificadores de acesso do C#:

# public

Com public, o acesso não é restrito [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Isso significa que ele é visível em qualquer lugar, dentro ou fora da classe que o contém:

```csharp     
public class Exemplo
{
    public int MeuMetodo()
    {
        // Código aqui
    }
}
```

# protected

O acesso é limitado à classe que os contém ou aos tipos derivados da classe que os contém [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Isso significa que ele é visível apenas dentro da hierarquia de herança:

```csharp
public class Base
{
    protected int MeuMetodoProtegido()
    {
        // Código aqui
    }
}

public class Derivada : Base
{
    public void OutroMetodo()
    {
        int resultado = MeuMetodoProtegido(); // Acesso permitido
    }
}
```

# internal

      
O acesso é limitado ao assembly atual [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Isso significa que o membro é visível apenas dentro do mesmo assembly (DLL ou executável):

```csharp     
internal class Interna
{
    // Código aqui
}
```

# protected internal

O acesso é limitado ao assembly atual **ou** aos tipos derivados da classe que os contém [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Isso significa que o modificador protected internal combina as características do protected e do internal. Ele permite acesso dentro do assembly atual e também por classes derivadas:

```csharp
public class Base
{
    protected internal int MeuMetodoProtegidoInterno()
    {
        // Código aqui
    }
}
```

# private

O acesso é limitado ao tipo recipiente [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Isso significa que o membro é visível apenas dentro da própria classe:

```csharp      
public class Exemplo
{
    private int MeuMetodoPrivado()
    {
        // Código aqui
    }
}
```

# private protected

O acesso é limitado à classe que o contém **ou** a tipos derivados da classe que o contém **no assembly atual** [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Isso significa que o membro é acessível dentro da classe em que foi definido e em classes derivadas (subclasses), porém apenas dentro do mesmo **assembly**:

```csharp      
//[ PROJETO 01]
public class ClasseBase
{
    private protected int ValorPrivadoProtegido;
}

//[ PROJETO 01]
public class SubClasseNoMesmoAssembly : ClasseBase
{
    public void Exemplo()
    {
        // Acesso permitido, pois SubClasse é uma subclasse de ClasseBase e estão no mesmo assembly.
        ValorPrivadoProtegido = 10;
    }
}

//[ PROJETO 02]
public class SubClasseEmAssemblyDiferente : ClasseBase
{
    public void Exemplo()
    {
        // Acesso não permitido, pois OutraSubClasse é uma subclasse de ClasseBase, mas estão em assemblies diferentes.
        ValorPrivadoProtegido = 10;
    }
}
```

# file
      
O tipo declarado apenas é visível no arquivo de origem atual [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Geralmente, é usado para geradores de código-fonte:

```csharp      
// In Arquivo.cs:
file interface IWidget
{
    int ProvideAnswer();
}

file class HiddenWidget
{
    public int Work() => 42;
}

public class Widget : IWidget
{
    public int ProvideAnswer()
    {
        var worker = new HiddenWidget();
        return worker.Work();
    }
}
```

# Considerações
    
- Apenas um modificador de acesso é permitido para um membro ou tipo, com exceção para **protected internal** e **private protected** [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências).

- Dependendo do contexto no qual ocorre uma declaração de membro, apenas algumas acessibilidades declaradas são permitidas [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Se não for especificado nenhum modificador de acesso em uma declaração de membro, uma acessibilidade padrão será usada [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências).

# Padrão de acessibilidade

Tipos aninhados, que são membros de outros tipos, podem ter acessibilidades declaradas, conforme a tabela à seguir [[2]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências):


| Membro pai | Padrão de acessibilidade para o membro filho | Acessibilidade permitida para o membro filho |
|--|--|--|
| enum | public | Nenhum |
| class | private | public, protected, internal, private, protected internal, private protected |
| interface | public | public, protected, internal, private, protected internal, private protected |
| struct | private | public, internal, private |

## enum

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
Ainda considerando o exemplo acima. Segue um exemplo sobre o que **é possível** de ser feito:
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