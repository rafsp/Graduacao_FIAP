[[_TOC_]]

# Introdução

O Git é uma ferramenta poderosa não apenas para controle de versão local, mas também para colaboração em projetos distribuídos. Aqui está uma explicação prática de como usar os comandos git remote, git push e git pull para gerenciar repositórios remotos:

# Vincular Repositórios Remotos

Para adicionar um repositório remoto ao seu projeto local, você usa o comando git remote add <nome_remoto> <url_do_repositório>. Isso cria uma conexão entre o repositório local e o repositório remoto.

```bash
git remote add
```
      
Para adicionar um repositório remoto ao seu projeto local, você usa o comando git remote add <nome_remoto> <url_do_repositório>. Isso cria uma conexão entre o repositório local e o repositório remoto.

![image.png](/.attachments/image-ddf6ed0b-aca3-4aa4-a1a1-fd8b9c0fc774.png)

# Listar Repositórios Remotos
      
Para ver uma lista dos repositórios remotos associados ao seu projeto, você pode usar o comando git remote -v. Isso mostra os URLs dos repositórios remotos e seus respectivos apelidos.

```bash   
git remote -v
```
![image.png](/.attachments/image-bb787081-9e31-414d-a118-9d328091372b.png)

# Atualizar o Repositório Local
      
Utilize o comando git reset –hard para atualizar os arquivos do branch remoto para o branch local.

```bash
git reset --hard
```

![image.png](/.attachments/image-e76c9c79-97ae-4e2b-ad10-a545f1bb9fdc.png)

```bash
git clone
```