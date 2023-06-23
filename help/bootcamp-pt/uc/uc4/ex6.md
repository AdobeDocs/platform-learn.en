---
title: Bootcamp - Customer Journey Analytics - From insights to action - Brazil
description: Bootcamp - Customer Journey Analytics - From insights to action - Brazil
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 28b87e21-3168-447e-9a93-a6ae7e969657
---
# 4.6 Dos insights à ação

## Objetivos

- Entenda como criar um público com base em uma visão coletada no Customer Journey Analytics
- Use esse público no CDP em tempo real e no Adobe Journey Optimizer

## 4.6.1 Crie uma audiência e publique-a

Em seu projeto, você criou um filtro chamado **Call Feelings** e conseguiu visualizar a quantidade de usuários que tiveram suas ligações ao call center classificadas como **positivas**. Agora, você poderá criar um segmento com esses usuários e ativação-los em jornadas ou em canais de comunicação.

O primeiro passo é: No painel criado no último exercício, selecione a linha **1. Call Feeling - Positive**, clique com o botão direito de seu mouse e selecione a opção **Create audience from selection**:

![demo](./images/aud1.png)

Em seguida, dê um nome para a sua audiência seguindo o modelo **yourLastName - cia audience call feeling positive**:

![demo](./images/aud2.png)

Note que é possível ter um preview da audiência que está sendo criada:

![demo](./images/aud3.png)

Para finalizar, clique em **Publicar**:

![demo](./images/aud4.png)

## 4.6.2 Use sua audiência como parte de um segmento

Voltando para a Adobe Experience Platform, vá em **Segments > Browse** e você conseguirá visualizar o seu segmento criado no CJA pronto e disponível para ser usado nas suas ativações e jornadas!

![demo](./images/aud5.png)

Vamos agora usar esse segmento em uma ativação no Facebook e em uma jornada do cliente!

## 4.6.3 Use seu segmento na Real-Time CDP em tempo real

Na Adobe Experience Platform, vá em **Segments > Browse** e encontre a audiência que você criou no CJA:

![demo](./images/aud6.png)

Clique no seu segmento e, em seguida, clique em **Activate to Destination**:

![demo](./images/aud7.png)

Selecione a destination chamada bootcamp-facebook e, em seguida, clique em Next:

![demo](./images/aud8.png)

Em seguida, clique em Next novamente:

![demo](./images/aud9.png)

Selecione a opção **Origin of your audience** e defina como **Directly from customers** e clique em Next:

![demo](./images/aud10.png)

Por fim, na página **Review** clique em Finish!

![demo](./images/aud11.png)

Pronto! Agora o seu segmento está vinculado aos públicos personalizados do Facebook.
Agora, vamos utilizar esse segmento no AJO!

## 4.6.4 Use seu segmento no Adobe Journey Optimizer

Na interface da Adobe Experience Platform clique em Journey Optimizer e, em seguida, no menu lateral esquerdo, clique em **Journeys** e comece a criar uma jornada clicando em **Create Journey**:

![demo](./images/aud20.png)

![demo](./images/aud21.png)

![demo](./images/aud22.png)

Em seguida, no menu lateral esquerdo, em Eventos, selecione **Segment Qualification** e arraste-o até a jornada:

![demo](./images/aud23.png)

Em seguida, em **Segment** clique em **Edit** para selecionar um segmento:

![demo](./images/aud24.png)

Selecione a audiência que você criou no CJA e clique em **Save**:

![demo](./images/aud25.png)

Pronto! A partir daí você pode criar uma jornada para clientes que se qualificam para esse segmento!

[Go Back to User Flow 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)
