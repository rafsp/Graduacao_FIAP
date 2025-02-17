[[_TOC_]]

# Clonando uma Web API

Neste tópico vamos utilizar como exemplo um template de projeto de webapi usando .NET. Para isso, siga os passos de clonar um repositório (clone a repository) do link abaixo.

```git
git clone https://nagibsabbag.visualstudio.com/2tdspx-2025/_git/first-webapi
```

Para compreender os arquivos e diretórios, vamos passar pelos principais arquivos e diretórios.

# Connect Services

![image.png](/.attachments/image-0bcc30df-34a7-432f-84c6-2ffa46a3c140.png)

Este diretório é usado para armazenar referências a serviços conectados, como APIs externas, bancos de dados, serviços em nuvem, entre outros. Essas referências são frequentemente gerenciadas e configuradas usando o Visual Studio.

![image.png](/.attachments/image-955fc851-f2c5-4ae1-b94e-4e28316c239b.png)

# Dependencies

![image.png](/.attachments/image-75b12fad-1db8-4c9b-b208-e2604a1b1ba8.png)

Este diretório armazena as dependências do projeto, como bibliotecas de terceiros (pacotes NuGet) necessárias para compilar e executar a aplicação. O gerenciamento de dependências é essencial para garantir que o projeto tenha acesso às bibliotecas e recursos necessários.

# Properties

![image.png](/.attachments/image-1ef159cf-6bdb-4567-94fc-6e3d00bdb439.png)
      
O diretório Properties geralmente contém arquivos de configuração e metadados relacionados ao projeto, como arquivos de configuração de compilação e informações sobre o assembly.

# Controllers

![image.png](/.attachments/image-e4b9550b-98c8-4d52-bfed-d77634143088.png)

Este diretório geralmente contém os controladores da Web API. Os controladores são responsáveis por receber as solicitações HTTP, processá-las e retornar as respostas apropriadas. Eles são uma parte fundamental de uma Web API em C#.

# Appsettings.json

![image.png](/.attachments/image-b3f5bc98-cffc-4a7f-85d5-686cd7e4626b.png)

Este arquivo contém configurações de aplicativo, como cadeias de conexão de banco de dados, configurações de log, chaves de API, entre outras. Ele é usado para configurar o comportamento da aplicação e pode ser acessado durante a execução.

# First-webapi.http

![image.png](/.attachments/image-043157ae-7d1f-4d4f-bb21-e42d50878a5b.png)
      
Este arquivo contém solicitações HTTP de teste ou exemplos de solicitações que podem ser feitas para a Web API. Ele pode ser usado para testar e depurar a API diretamente do ambiente de desenvolvimento.

