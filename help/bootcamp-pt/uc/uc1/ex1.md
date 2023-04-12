---
title: Bootcamp -  Real-time Customer Profile - From unknown to known on the website - Brazil
description: Bootcamp - Real-time Customer Profile - From unknown to known on the website - Brazil
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 853a69d2-5dac-413d-bb40-ef29604a26ae
---
# 1.1 Do desconhecido ao conhecido em nosso site

## Contexto

A Adobe Experience Platform desempenha um papel importante nessa jornada. A plataforma é o cérebro da comunicação, o **experience system of record**. 

Plataforma é um ambiente em que a palavra cliente engloba mais do que clientes conhecidos. Um visitante desconhecido no site também é um cliente do ponto de vista da Plataforma e, como tal, todo o comportamento de um visitante desconhecido também é enviado à Plataforma. Graças a essa abordagem, quando esse visitante eventualmente se torna um cliente conhecido, uma marca também pode visualizar o que aconteceu antes daquele momento. Isso ajuda a partir de uma perspectiva de otimização de atribuição e experiência. 

## Fluxo da jornada do cliente

Acesse [https://bootcamp.aepdemo.net](https://bootcamp.aepdemo.net). Clique em **Allow All**.

![DSN](./images/web8.png)

Clique no ícone do logotipo da Adobe no canto superior esquerdo da tela para abrir o Visualizador de perfil.
  
![Demo](./images/pv1.png)

Verifique o painel do Visualizador de perfil e no Perfil do cliente em tempo real com o **Experience Cloud ID** como o identificador primário para este cliente que ainda é desconhecido. 
      
![Demo](./images/pv2.png)

Você também pode ver todos os Eventos de Experiência coletados com base no comportamento do cliente. A lista está vazia no momento, mas isso mudará em breve.

![Demo](./images/pv3.png)

Acesse a opção de menu **Application Services** e clique no produto **Real-Time CDP**. 

![Demo](./images/pv4.png)

Você verá a página de detalhes do produto. Um Evento de experiência do tipo **Product View** agora foi enviado para a Adobe Experience Platform usando a implementação do Web SDK que você revisou no Módulo 1. Abra o painel Visualizador de perfil e verifique seus **Experience Events**. 
  
![Demo](./images/pv5.png)

Acesse a opção de menu **Application Services** e clique no produto **Adobe Journey Optimizer**. Mais um Evento de experiência foi enviado para a Adobe Experience Platform. 
  
![Demo](./images/pv7.png)

Abra o painel Visualizador de perfil. Agora você verá 2 Eventos de experiência do tipo **Product View**. Embora o comportamento seja anônimo, cada clique é rastreado e armazenado na Adobe Experience Platform. Depois que o cliente anônimo se tornar conhecido, poderemos mesclar todo o comportamento anônimo automaticamente ao perfil conhecido. 
  
![Demo](./images/pv8.png)

Agora vamos analisar seu perfil de cliente e usar seu comportamento para personalizar sua experiência do cliente no site.

Próxima etapa: [1.2 Visualize seu próprio perfil de cliente em tempo real - UI](./ex2.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
