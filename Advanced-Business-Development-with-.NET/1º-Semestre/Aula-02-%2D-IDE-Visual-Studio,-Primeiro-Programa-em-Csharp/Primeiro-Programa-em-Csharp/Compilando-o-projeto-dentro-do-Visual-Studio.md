[[_TOC_]]

# Introdução

Existem várias formas para realizar um Build e publicar no nosso host local (localhost) o nosso Hello World.  

# Build

## Através do projeto

Para Buildar, pode-se considerar clicar com o botão direito no projeto do Visual Studio e depois em “Build”.

![image.png](/.attachments/image-e1b1f875-6229-40f6-bfe8-96b8f8f42e67.png)

## Através da solução

Você também pode realizar esse procedimento para a solução inteira, ou seja, realizar o “build” em todos os projetos que configuram aquela solução.

![image.png](/.attachments/image-8568b520-2ab5-45d2-8d4a-9f83d9e625eb.png)

## Utilizando atalhos
      
Caso prefira utilizar atalhos, basta usar o “Ctrl + Shift + B”.

A opção Build no Visual Studio realiza uma compilação incremental, ou seja, somente os arquivos que foram alterados serão recriados e os arquivos que não foram modificados não serão compilados.

## Resultado final
O resultado do Build fica dentro da pasta “bin”.

![image.png](/.attachments/image-72eb0b72-b811-4b33-bcd7-1b0800ace0fb.png)

# Debug

Outro ponto importante foi que a compilação foi gerada no modo “Debug”.

      
Quando compilamos o nosso projeto no modo “Debug”, o Visual Studio gera um arquivo executável ou uma biblioteca com informações de depuração simbólicas e sem otimização [21]. Essas informações permitem que o depurador seja usado para acompanhar e analisar a execução do seu código, encontrar e corrigir erros, inspecionar variáveis, definir pontos de interrupção e etc.

      
O modo Debug também define a variável de compilação DEBUG, que pode ser usada para ativar ou desativar partes do código dependendo da configuração de build [22]. O modo Debug é recomendado para testar e depurar seu projeto, mas **não para distribuir a versão final**, pois ele pode **afetar o desempenho e o tamanho do arquivo** [21].