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

O acesso é limitado à classe que o contém **ou** a tipos derivados da classe que o contém no assembly atual [[1]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-04-%2D-Csharp,-uso-avançado-de-Modificadores-de-Acesso,-Palavras%2DChave,-Construtores,-Interfaces-e-Namespaces/Referências). Isso significa que o membro é acessível dentro da classe em que foi definido e em classes derivadas (subclasses), porém apenas dentro do mesmo **assembly**:

```csharp      
public class ClasseBase
{
    private protected int ValorPrivadoProtegido;
}

public class SubClasseNoMesmoAssembly : ClasseBase
{
    public void Exemplo()
    {
        // Acesso permitido, pois SubClasse é uma subclasse de ClasseBase e estão no mesmo assembly.
        ValorPrivadoProtegido = 10;
    }
}

public class SubClasseEmAssemblyDiferente : ClasseBase
{
    public void Exemplo()
    {
        // Acesso não permitido, pois OutraSubClasse é uma subclasse de ClasseBase, mas estão em assemblies diferentes.
        ValorPrivadoProtegido = 10;
    }
}
```