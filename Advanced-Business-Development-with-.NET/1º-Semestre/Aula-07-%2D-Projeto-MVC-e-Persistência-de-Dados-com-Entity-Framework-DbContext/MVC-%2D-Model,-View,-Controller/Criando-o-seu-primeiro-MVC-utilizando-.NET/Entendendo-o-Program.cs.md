[[_TOC_]]

# Introdução
      
Quando o projeto foi criado, alguns arquivos “default” foram automaticamente configurados. Entre eles, o arquivo Program.cs .  
O arquivo Program.cs em um projeto C# MVC serve como ponto de entrada para a aplicação. Ele é responsável por inicializar e configurar o host da aplicação web, que inclui:

- Configurar o servidor web e os serviços necessários;
- Definir o pipeline de solicitações HTTP;
- Iniciar a aplicação.

Em versões mais recentes do .NET, como o .NET 6, o arquivo Program.cs também assumiu responsabilidades que anteriormente estavam no arquivo Startup.cs, como a configuração de serviços e middlewares. 

Isso faz parte de uma simplificação geral para tornar o código mais conciso e fácil de entender [4].

Abaixo um exemplo de um código no Program.cs :

