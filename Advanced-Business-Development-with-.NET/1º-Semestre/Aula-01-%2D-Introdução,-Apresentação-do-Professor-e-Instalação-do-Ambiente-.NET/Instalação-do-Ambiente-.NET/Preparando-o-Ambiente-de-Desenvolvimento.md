O próximo passo agora está em verificar o ambiente para podermos desenvolver as aplicações. Para isso vamos precisar instalar o SDK e o Runtime.

O SDK (Software Development Kit) é o conjunto de ferramentas, bibliotecas e compiladores que permitem a experiência básica do desenvolvedor. Você precisa do SDK para criar bibliotecas e aplicações .NET. 

Já o Runtime é o conjunto de "runtimes" e bibliotecas que permitem executar aplicativos .NET, ou seja, você precisa do Runtime para rodar um aplicativo .NET no seu computador ou servidor. O Runtime do .NET sempre é instalado com o SDK. 

Em outras palavras, o **SDK é para construir o aplicativo** e o **Runtime é para rodar o aplicativo**.

Normalmente, por conta de rodar alguns aplicativos na nossa máquina, já existe algum Runtime instalado no nosso computador. Para verificar se já temos alguma versão instalada, basta seguir os passos abaixo. 

Windows (Prompt de Comando), Linux (bash) ou MAC (Terminal):

```bash
dotnet --list-sdks
```
![animacao.gif](/.attachments/animacao-9ee63a6f-eb46-491a-bd82-3ceb77b19f10.gif)

O código acima lista todos os SDKs do .NET instalados.