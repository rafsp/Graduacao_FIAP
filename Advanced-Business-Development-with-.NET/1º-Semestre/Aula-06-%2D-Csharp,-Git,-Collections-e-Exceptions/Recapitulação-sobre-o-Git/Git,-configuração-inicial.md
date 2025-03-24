[[_TOC_]]

# Verificação da versão
No primeiro passo, uma forma de validar se o git está instalado é digitar o código abaixo no terminal
```bash
git --version
```

![image.png](/.attachments/image-491ec262-b5d0-489b-be47-56978a60902a.png)

# Git Bash

Outra forma de poder utilizar o git é através do Git Bash. O Git Bash é um emulador de terminal que vem junto com a instalação do Git para sistemas Windows. Ele fornece um ambiente de linha de comando, permitindo que os usuários executem comandos do Git e outros comandos do shell em um ambiente familiar.

![image.png](/.attachments/image-120cd8df-8993-4fd6-8d45-0ff336e75f51.png)
![image.png](/.attachments/image-cf85324c-5348-41d3-88f8-c5ffd4c54488.png)

# Configurações de nome de usuário e endereço de e-mail
      
As configurações de nome de usuário e e-mail no Git são importantes porque ajudam a identificar quem fez quais alterações em um repositório Git. Quando você faz um commit em um repositório Git, o Git registra o nome de usuário e o endereço de e-mail associados a essa ação.
    
- **Nome de usuário:** Identifica quem fez as alterações no repositório. Geralmente é seu nome real ou um identificador único.

- **Endereço de e-mail:** Serve como um ponto de contato para os colaboradores do projeto. Além disso, é usado pelo Git para atribuir as alterações a uma pessoa específica.

Para listarmos o usuário e endereço de e-mail globais associados ao git, utilize os comandos abaixo:

- Listar o Usuário
  ```bash
  git config user.name
  ```
- Listar o E-mail
  ```bash
  git config user.email
  ```

Para removermos o usuário e endereço de e-mail globais associados ao git, utilize os comandos abaixo:

```bash
git config --global --unset user.name
git config --global --unset user.email
```


