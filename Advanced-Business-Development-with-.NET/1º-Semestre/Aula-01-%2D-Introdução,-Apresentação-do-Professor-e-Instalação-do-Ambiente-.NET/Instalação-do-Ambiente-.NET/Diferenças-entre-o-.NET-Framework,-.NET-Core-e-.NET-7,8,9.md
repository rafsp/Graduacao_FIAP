[[_TOC_]]

O .NET possui várias versões e distribuições, cada uma com suas características e vantagens. Neste texto, vamos apresentar as principais diferenças entre o .NET Framework, o .NET Core e o .NET 7/8/9. 

# Sobre o .NET Framework

- .NET Framework é uma estrutura de desenvolvimento de software para criar e executar aplicativos no Windows [[4]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências);

- O .NET Framework também é a implementação original do .NET. Ele oferece suporte à execução de sites, serviços, aplicativos da área de trabalho e muito mais no Windows [[4]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências);

- Suporta várias linguagens e compiladores, conforme ilustração a seguir.

![swimlane-architecture-framework.svg](/.attachments/swimlane-architecture-framework-1e2755da-0c90-4551-be99-fa93db2a17e8.svg)
_Imagem retirada da referência [[4]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências)._

# Sobre o .NET Core

- O .NET Core é uma plataforma de desenvolvimento gratuita e de código aberto para a criação de vários tipos de aplicativos, como aplicativos web, móveis, de desktop, de nuvem e de jogos [[5]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências);

- O .NET Core, diferente do .NET Framework, pode ser executado em Windows, Linux, macOS e Docker [[6]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências);

- O CLR do .NET Core é uma versão otimizada e modular do CLR do .NET Framework, que permite o desenvolvimento e a implantação de aplicativos multiplataforma [[7]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências).

# Sobre o .NET 7/8/9

Antes de entrar no contexto do .NET 7 e 8, é importante entendermos sobre a “mudança de chave” entre o .NET Core e .NET 5.

Após o .NET Core, o próximo lançamento foi o .NET 5, que foi lançado em novembro de 2020 [[8]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências). 

Em resumo, o objetivo do .NET 5 foi em expandir as funcionalidades .NET Core, .NET Framework, Xamarin e Mono [[9]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências).

Posteriormente, houveram novas versões, como o .NET 6, .NET 7, .NET 8 e .NET 9. 

Entre as características deles estão:

- **.NET 6** é uma versão de suporte de longo prazo (LTS) que melhora o desempenho e o tempo de execução do .NET, e suporta novas linguagens, tecnologias e plataformas;

- **.NET 7** é uma versão de suporte de curto prazo (STS) que introduz novos recursos e melhorias para o desenvolvimento de aplicativos nativos híbridos, inteligência artificial, aprendizado de máquina, realidade aumentada e realidade virtual;

- **.NET 8** é uma versão de suporte de longo prazo (LTS) que enfatiza melhorias na linguagem e na experiência do desenvolvedor, e suportará novos cenários de computação, como a computação quântica e a computação em borda.

- **.NET 9** é uma versão de suporte de prazo padrão (STS) com foco especial em aplicativos nativos de nuvem e desempenho. Entre suas principais características estão:
    
  - Aprimoramentos no runtime: introdução de um novo modelo de atributos para alternância de funcionalidades com suporte a trimming, otimizações no coletor de lixo com adaptação dinâmica ao tamanho do aplicativo e diversas melhorias de desempenho, incluindo otimizações de loop, inlining e vetorização para Arm64;
    
  - Melhorias nas bibliotecas: o `System.Text.Json` agora oferece suporte a anotações de tipos de referência nulos e exportação de esquemas JSON a partir de tipos. No LINQ, foram adicionados os métodos `CountBy` e `AggregateBy`, permitindo agregações por chave sem a necessidade de alocar agrupamentos intermediários via `GroupBy`. Além disso, o tipo `System.Collections.Generic.PriorityQueue<TElement, TPriority>` inclui um novo método `Remove` para atualização da prioridade de itens na fila;
    
  - Avanços no SDK: introdução de conjuntos de carga de trabalho, onde todas as cargas de trabalho permanecem em uma única versão específica até serem atualizadas explicitamente. Para ferramentas, uma nova opção para `dotnet tool install` permite que os usuários decidam se uma ferramenta tem permissão para ser executada em uma versão de runtime do .NET mais recente do que a versão que a ferramenta tem como alvo. Além disso, o teste de unidade possui melhor integração com o MSBuild, permitindo a execução de testes em paralelo;
    
  - Blocos de construção de IA: o .NET 9 inclui novos recursos que facilitam a integração de inteligência artificial em aplicativos, como o `TensorPrimitives` e o `Tensor`, além de atualizações no ML .NET para a versão 4.0, oferecendo suporte aprimorado para modelos de aprendizado de máquina.