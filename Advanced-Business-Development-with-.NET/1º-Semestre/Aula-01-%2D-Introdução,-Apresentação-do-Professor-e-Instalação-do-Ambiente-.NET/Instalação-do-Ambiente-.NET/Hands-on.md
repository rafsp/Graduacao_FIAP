Não há maneira melhor de verificar se a instalação foi bem-sucedida do que criando sua primeira solução, certo?

**Então vamos lá !!!!**

1. Crie uma pasta chamada “HelloWorld”, em algum local de sua preferência (no meu caso vou criar no “C:”)

   ![animacao.gif](/.attachments/animacao-e26c07c5-59d4-4de4-b6f9-bba3071872be.gif)

2. Agora abra o Prompt de Comando e digite “cd” junto com o caminho que você acabou de criar

   ![animacao.gif](/.attachments/animacao-d71bba04-6134-4bb8-bed7-4c2d6762961f.gif)

3. O próximo passo está em criar um novo projeto, do tipo console. Para isso vamos digitar o comando abaixo:

   ```bash
   dotnet new console
   ```
   ![animacao.gif](/.attachments/animacao-0d0fe03c-db64-4c64-a934-252d84da6267.gif)

4. Depois entre na pasta que você criou, para verificar os arquivos que foram criados:

   ![image.png](/.attachments/image-2f5849ef-f22a-495d-bf5b-d14851971a93.png)

A pasta “obj” é usada pelo compilador para armazenar objetos temporários usados na compilação do seu projeto [11] . Esses objetos incluem arquivos intermediários, arquivos de dependência e arquivos de configuração [12]. Você não precisa se preocupar com o conteúdo dessa pasta, pois ela é gerada automaticamente pelo SDK do .NET. Você pode excluir essa pasta sem afetar o seu código-fonte, mas ela será recriada na próxima vez que você compilar o seu projeto.

![image.png](/.attachments/image-d525d6a1-73d4-432b-8e72-9c1cd40b93dd.png)