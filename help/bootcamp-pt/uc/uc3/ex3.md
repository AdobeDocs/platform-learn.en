---
title: Bootcamp - Blending physical and digital - Journey Optimizer Create your journey and push  - Brazilnotification
description: Bootcamp - Blending physical and digital - Journey Optimizer Create your journey and push  - Brazilnotification
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
---
# 3.3 Crie sua jornada e notificação push

Neste exercício, você irá configurar a jornada e a mensagem que precisa ser acionada quando alguém inserir uma sinalização (beacon) usando o aplicativo móvel. 

Faça login no Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Clique em **Journey Optimizer**. 

![ACOP](./images/acophome.png)

Você será redirecionado para a visualização da **Home** no Journey Optimizer. Primeiro, verifique se você está usando o sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternar de um sandbox para outro, clique em **Prod** e selecione o sandbox na lista. Neste exemplo, o nome do sandbox é **Bootcamp**. Você estará na visualização da **Home**  do seu sandbox `Bootcamp`. 

![ACOP](./images/acoptriglp.png)

## 3.3.1 Crie a sua jornada

No menu à esquerda, clique em **Journeys**. Em seguida, clique em **Create Journey** para criar uma nova jornada. 

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No exercício anterior, você criou um novo **Event**. Você nomeou o evento `yourLastNameBeaconEntryEvent` e substituiu `yourLastName` pelo seu sobrenome. Este foi o resultado da criação do Evento: 

![ACOP](./images/eventdone.png)

Agora você deve considerar este evento como o início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de jornada. Sua jornada agora deve ser semelhante ao seguinte. Clique em **Ok** para salvar suas alterações. 

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma ação **Push**. Vá para o lado esquerdo da tela para **Actions**, selecione a ação **Push** e arraste e solte a ação no segundo nó da sua jornada. 

![ACOP](./images/journeyactions.png)

No lado direito da tela, agora você deve criar sua notificação push. 

Defina a **Category** como **Marketing** e selecione uma superfície push que permite enviar notificações push. Nesse caso, a superfície push a ser selecionada é **mmeeewis-app-mobile-bootcamp**. 

![ACOP](./images/journeyactions1.png)

## 3.3.2 Crie a sua mensagem

Clique em **Edit Content**.

![ACOP](./images/emptymsg.png)

Em seguida, a tela abaixo será exibida:

![ACOP](./images/emailmsglist.png)

Vamos definir o conteúdo da notificação push. 

Clique no campo de texto **Title**. 

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**. Clique no ícone de personalização.

![Journey Optimizer](./images/msg6.png)

Agora você precisa trazer o token de personalização para o campo **First name** que está armazenado em `profile.person.name.firstName`. No menu à esquerda, selecione **Profile Attributes**, role para baixo/navegue para encontrar o elemento **Person** e clique na seta para avançar um nível até chegar ao campo `profile.person.name.firstName`. Clique no ícone **+** para adicionar o campo à tela. Clique em **Save**. 

![Journey Optimizer](./images/msg7.png)

Então, você irá retornar para esta tela. Clique no ícone de personalização ao lado do campo **Body**. 

![Journey Optimizer](./images/msg11.png)

Na área de texto, escreva `Bem-vindo(a)`. 

![Journey Optimizer](./images/msg12.png)

Em seguida, clique em  **Contextual Attributes** and then **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Clique em **Events**.

![ACOP](./images/jomsg4.png)

Clique no nome do seu evento, que deve ser semelhante ao seguinte: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Clique em **Place context**.

![ACOP](./images/jomsg6.png)

Clique em **POI Interaction**.

![ACOP](./images/jomsg7.png)

Clique em **POI Detail**.

![ACOP](./images/jomsg8.png)

Clique no **+** icon no **POI Name**.
Em seguida, o seguinte será exibido. Clique em **Save**.

![ACOP](./images/jomsg9.png)

Sua mensagem agora está pronta. Clique na seta no canto superior esquerdo para retornar à sua jornada. 

![ACOP](./images/jomsg11.png)

Clique em **Ok**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Envie uma mensagem para uma tela

Como terceira etapa da jornada, você deve adicionar uma ação  **sendMessageToScreen** action. Vá para o lado esquerdo da tela para **Actions**, selecione a ação **sendMessageToScreen** e arraste e solte a ação no terceiro nó da sua jornada. Em seguida, você verá a tela abaixo.

![ACOP](./images/jomsg15.png)

**sendMessageToScreen** é uma ação personalizada que irá publicar uma mensagem no ponto de extremidade usado pela exibição na loja. A ação **sendMessageToScreen** espera que múltiplas variáveis sejam definidas. Você pode visualizar essas variáveis rolando para baixo até ver **Action Parameters**.

![ACOP](./images/jomsg16.png)

Agora você precisa definir os valores para cada parâmetro de ação. Siga esta tabela para entender quais valores são necessários e onde.

| Parameter     | value       |
|:-------------:| :---------------:|
|DELIVERY|`'image'`|
|ECID|`@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}`|
|FIRST NAME |`#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}`|
|EVENTSUBJECT|`#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}`|
| EVENTSUBJECTURL |`#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}`|
| SANDBOX         |`'bootcamp'` |
| CONTAINERID         | `''` |
| ACTIVITYID         |`''` |
| PLACEMENTID         | `''` |

{style="table-layout:auto"}

Para definir esses valores, clique no ícone **Edit**.

![ACOP](./images/jomsg17.png)

Em seguida, selecione **Advanced Mode**.

![ACOP](./images/jomsg18.png)

Em seguida, cole o valor com base na tabela acima. Clique em **Ok**.

![ACOP](./images/jomsg19.png)

Repita esse processo para adicionar valores para cada campo.

>[!IMPORTANTE]
>
>Para o campo ECID, há uma referência ao evento`yourLastNameBeaconEntryEvent`. Lembre-se de substituir  `yourLastName` pelo seu sobrenome. 

O resultado final deve ser semelhante ao seguinte:

![ACOP](./images/jomsg20.png)

Role para cima e clique em **Ok**.

![ACOP](./images/jomsg21.png)

You still need to give your journey a Name. You can do that by clicking the **Properties** icon in the top right side of your screen.

![ACOP](./images/journeyname.png)

Você pode inserir o nome da jornada aqui. Use `yourLastName - Beacon Entry Journey`. Clique em **OK** para salvar suas alterações. 

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Publish**.

![ACOP](./images/publishjourney.png)

Clique em **Publish** novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de confirmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

Sua jornada agora está ativa e pode ser acionada.

Você terminou este exercício.

Próxima etapa: [3.4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)
