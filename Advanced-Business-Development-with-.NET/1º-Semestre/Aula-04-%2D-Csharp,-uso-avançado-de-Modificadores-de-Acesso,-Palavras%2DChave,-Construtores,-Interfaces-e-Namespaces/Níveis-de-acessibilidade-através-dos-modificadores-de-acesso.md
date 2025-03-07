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
