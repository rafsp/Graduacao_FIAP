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
 