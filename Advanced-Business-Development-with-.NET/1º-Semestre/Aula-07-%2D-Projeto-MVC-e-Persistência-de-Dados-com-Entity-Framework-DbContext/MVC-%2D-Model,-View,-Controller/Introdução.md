# Introdução ao MVC (Model-View-Controller)      
O MVC é um padrão de design usado para desacoplar a interface do usuário (a exibição), os dados (o modelo) e a lógica do aplicativo (o controlador). Esse padrão ajuda a obter uma separação das preocupações [1].
O padrão de arquitetura MVC (Model-View-Controller) separa um aplicativo em três grupos de componentes principais: Modelos, Exibições e Componentes. Esse padrão ajuda a obter a separação de interesses. Usando esse padrão, as solicitações de usuário são encaminhadas para um Controlador, que é responsável por trabalhar com o Modelo para executar as ações do usuário e/ou recuperar os resultados de consultas. O Controlador escolhe a Exibição a ser exibida para o usuário e fornece-a com os dados do Modelo solicitados [2].
O seguinte diagrama mostra os três componentes principais e quais deles referenciam os outros:

::: mermaid
 graph TD; 
 View-->Model; Controller-->Model; Controller-->View;
:::
