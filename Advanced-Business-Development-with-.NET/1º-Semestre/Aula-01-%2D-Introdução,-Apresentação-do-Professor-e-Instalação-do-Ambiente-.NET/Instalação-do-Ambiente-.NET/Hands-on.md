[[_TOC_]]


Não há maneira melhor de verificar se a instalação foi bem-sucedida do que criando sua primeira solução, certo?

**Então vamos lá !!!!**

# Criando o seu console

1. Crie uma pasta chamada “HelloWorld”, em algum local de sua preferência (no meu caso vou criar no “C:”)

   ![animacao.gif](/.attachments/animacao-495a5163-bd8b-4fd7-beaf-3c767ddd6c6c.gif)

2. Agora abra o Prompt de Comando e digite “cd” junto com o caminho que você acabou de criar

   ![animacao.gif](/.attachments/animacao-d71bba04-6134-4bb8-bed7-4c2d6762961f.gif)

3. O próximo passo está em criar um novo projeto, do tipo console. Para isso vamos digitar o comando abaixo:

   ```bash
   dotnet new console
   ```
   ![animacao.gif](/.attachments/animacao-0d0fe03c-db64-4c64-a934-252d84da6267.gif)

4. Depois entre na pasta que você criou, para verificar os arquivos que foram criados:

   ![image.png](/.attachments/image-2f5849ef-f22a-495d-bf5b-d14851971a93.png)

# Significado das pastas e dos arquivos

## Pasta obj
A pasta “obj” é usada pelo compilador para armazenar objetos temporários usados na compilação do seu projeto [[11]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências). Esses objetos incluem arquivos intermediários, arquivos de dependência e arquivos de configuração [[12]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências). Você não precisa se preocupar com o conteúdo dessa pasta, pois ela é gerada automaticamente pelo SDK do .NET. Você pode excluir essa pasta sem afetar o seu código-fonte, mas ela será recriada na próxima vez que você compilar o seu projeto.

![image.png](/.attachments/image-d525d6a1-73d4-432b-8e72-9c1cd40b93dd.png)

## Arquivo HelloWorld.csproj
O arquivo “HelloWorld.csproj” é um arquivo de projeto do MSBuild, que é o mecanismo usado pelo .NET para compilar e implantar seus projetos [[13]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências). Esse arquivo contém informações como o tipo de projeto (console, web, desktop, etc.), a plataforma alvo, as dependências de outros projetos ou bibliotecas de terceiros, e as tarefas que devem ser executadas durante o processo de construção [[14]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências). O arquivo csproj é um documento XML que segue o esquema do MSBuild, e você pode editá-lo manualmente para personalizar o comportamento do seu projeto [[15]](/Advanced-Business-Development-with-.NET/1º-Semestre/Aula-01-%2D-Introdução,-Apresentação-do-Professor-e-Instalação-do-Ambiente-.NET/Instalação-do-Ambiente-.NET/Referências).
![image.png](/.attachments/image-e1df5618-ce2a-424d-959b-ed388b03fd0c.png)

## Arquivo Program.cs
O arquivo “Program.cs” é o arquivo que contém o código principal do seu programa em C#. Ele é o ponto de entrada da sua aplicação, onde você pode definir as instruções que serão executadas quando o programa for iniciado.
![image.png](/.attachments/image-6b01f600-4e48-401e-bbe1-7142573dd8c7.png)

# Compilando o projeto

O próximo passo está em compilar esse projeto. Para isso, no Prompt de Comando, utilize o comando abaixo:
   ```bash
   dotnet new console
   ```