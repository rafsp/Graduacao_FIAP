[[_TOC_]]

Agora vamos conhecer alguns comandos básicos do Git.

# Git Clone
```bash
git clone
```
O comando git clone é utilizado para clonar um repositório Git existente para um novo diretório. Isso significa que você está fazendo uma cópia exata do repositório remoto em seu computador local. Isso é útil quando você deseja colaborar em um projeto existente ou deseja obter uma cópia local de um repositório remoto.

# Git Init
```bash
git init
```
O comando git init é usado para inicializar um novo repositório Git em um diretório específico. Quando você executa este comando em um diretório, o Git cria uma estrutura inicial de repositório, incluindo um diretório oculto chamado ".git", que contém todos os metadados e objetos necessários para o controle de versão do Git.

![image.png](/.attachments/image-cde375a9-d53b-4e3d-a335-ab95de6c78a0.png)

# Git Status
```bash
git status
```
      
O comando git status é uma ferramenta útil para verificar o estado atual do seu repositório Git. Ele mostra quais arquivos foram modificados, quais arquivos estão no índice e prontos para serem commitados, e se há alguma alteração que ainda não foi rastreada pelo Git. O git status é uma maneira rápida de entender o que está acontecendo em seu repositório e quais ações você pode precisar tomar.

![image.png](/.attachments/image-d6f1f0a3-91cb-4407-92ee-fb9a884f8f9a.png)

# Git Add
```bash
git add
```
O comando git add é usado para adicionar arquivos ao índice do Git, também conhecido como área de preparação. Quando você faz alterações em seus arquivos, o Git não as rastreia automaticamente. Você precisa usar o git add para informar ao Git quais alterações você deseja incluir no próximo commit.

![image.png](/.attachments/image-2ab57a32-7b50-4889-81a1-5d120c38c78b.png)

# Git rm cached
```bash
git rm --cached
```
O comando git rm é utilizado no Git para remover arquivos do seu repositório Git e também do seu sistema de arquivos local. Ele é usado principalmente para instruir o Git a parar de rastrear um arquivo que já está sob controle de versão ou para remover um arquivo que foi adicionado ao índice (git add), mas ainda não foi commitado.
      
- **git rm <arquivo>:** Remove o arquivo do diretório de trabalho e também o remove do índice, ou seja, prepara o arquivo para ser removido no próximo commit;
- **git rm --cached <arquivo>:** Remove o arquivo do índice, mas mantém o arquivo no sistema de arquivos local. Isso significa que o arquivo ainda existirá em seu diretório de trabalho, mas não será mais rastreado pelo Git.

![image.png](/.attachments/image-e03ba2ce-f769-479c-8248-04a676a78507.png)

# Git commit

O comando git commit é usado para criar um novo commit no repositório Git, que registra as alterações feitas desde o último commit. Para criar um commit, você precisa incluir uma mensagem que descreva as alterações que estão sendo feitas. Isso ajuda a manter um histórico claro e compreensível das mudanças em seu projeto.

![image.png](/.attachments/image-6aa1f235-b675-440e-a29a-54d91bb56ad2.png)