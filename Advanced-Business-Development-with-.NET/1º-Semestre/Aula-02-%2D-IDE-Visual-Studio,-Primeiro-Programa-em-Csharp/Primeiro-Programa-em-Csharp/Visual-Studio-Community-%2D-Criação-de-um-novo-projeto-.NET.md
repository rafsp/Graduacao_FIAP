# Clonando um repositório

Agora que estamos mais familiarizados com C#, o próximo passo é compreender uma de suas principais IDEs, o Visual Studio. Na aula anterior, conduzimos todo o processo de instalação da IDE. Ao iniciar o Visual Studio, a primeira tela que surge é a seguinte:

![image.png](/.attachments/image-53435c8e-b4f4-4606-986d-e8828b56befe.png)

Nessa primeira tela do Visual Studio nós temos algumas opções, como:

## Clone a Repository

Serve para copiar um repositório git existente de um provedor remoto, como o GitHub ou o Azure DevOps, para o seu computador local. Dessa forma, você pode trabalhar com o código do repositório no Visual Studio, fazer alterações, sincronizar e enviar suas contribuições.

Vamos ver melhor como funciona através dos passos abaixo:
  
1. Entrar no Visual Studio, depois clicar em “Clone a repository”;

   ![image.png](/.attachments/image-8c862d96-bfd6-45d1-85e5-d5ab4fe71319.png)

2. Em "Repository Location", copie e cole o link abaixo:

   ```git
   https://nagibsabbag.visualstudio.com/2tdspx-2025/_git/hello-world
   ```

   ![image.png](/.attachments/image-7c20b1dd-f81c-47f2-ba44-c5fb3c564203.png)
   
3. Clique em “Clone”;

4. Caso encontre algum problema de segurança ao clonar um repositório, escreva o código abaixo para retirar a validação de ssl

   ```git
   git config --global http.sslverify "false"
   ```

5. Pronto! Perceba que você acabou de “baixar” o projeto que criamos na primeira aula

   ![image.png](/.attachments/image-f99d34d7-081a-4439-b017-9cab66ebe4fe.png)

