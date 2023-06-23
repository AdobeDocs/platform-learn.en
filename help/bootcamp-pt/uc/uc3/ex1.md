---
title: Bootcamp - Blending physical and digital - Use the mobile app and trigger a beacon entry - Brazil
description: Bootcamp - Blending physical and digital - Use the mobile app and trigger a beacon entry - Brazil
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 14bfbebe-6df3-4a0e-875c-b4c0d016f8da
---
# 3.1 Use o aplicativo móvel e acione um beacon

## Instale o aplicativo móvel

Antes de instalar o aplicativo, é necessário habilitar o **Rastreamento** no seu dispositivo iOS. Para isso, acesse **Configurações** > **Privacidade e segurança** > **Rastreamento** e verifique a opção **Permitir que os aplicativos solicitem o rastreamento**. 

![DSN](./../uc3/images/app4.png)

Acesse a App Store da Apple e pesquise `aepmobile-bootcamp`. Clique em **Instalar** ou **Download**. 

![DSN](./../uc3/images/app1.png)

Depois que o aplicativo estiver instalado, clique em **Abrir**. 

![DSN](./../uc3/images/app2.png)

Clique em **OK**.

![DSN](./../uc3/images/app9.png)

Clique em **Permitir**.

![DSN](./../uc3/images/app3.png)

Click **I agree**.

![DSN](./../uc3/images/app7.png)

Clique em **Permitir enquanto usa o aplicativo**.

![DSN](./../uc3/images/app8.png)

Clique em **Permitir**.

![DSN](./../uc3/images/app5.png)

Agora você está no aplicativo, na página inicial, pronto(a) para verificar toda a jornada do cliente.

![DSN](./../uc3/images/app12.png)

## Fluxo da jornada do cliente

Primeiramente, é necessário fazer o login. Clique em **Login**.

![DSN](./images/app13.png)

Depois de criar sua conta nos exercícios anteriores, isso é exibido no site. Agora é necessário reutilizar o endereço de e-mail da conta que você criou no aplicativo para fazer o login.
  
![Demo](./images/pv1.png)

Digite o endereço de e-mail que você usou no site e clique em **Login**.

![DSN](./images/app14.png)

Você receberá uma confirmação de que está conectado e receberá uma notificação push.

![DSN](./images/app15.png)

Retorne para a página inicial do aplicativo e os recursos adicionais irão aparecer.

![DSN](./images/app17.png)

Primeiro, acesse **Products**. Clique em qualquer produto, neste exemplo: **Coffee to go**. 

![DSN](./images/app19.png)

Você verá a página do produto **Coffee to go** no aplicativo. 

![DSN](./images/app20.png)

Agora você irá simular um evento de entrada de sinalização (beacon) em uma loja offline. O objetivo da simulação é personalizar a experiência do cliente nas telas da loja. Para visualizar a experiência na loja, foi criada uma página que mostrará de forma dinâmica as informações relevantes para o cliente ao entrar na loja. 

Antes de continuar, abra esta página da Web em seu computador: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/screen.html)

Em seguida, a tela abaixo será exibida:

![DSN](./images/screen1.png)

Em seguida, retorne para a página inicial. Clique no ícone do **beacon**.

![DSN](./images/app23.png)

Após essa etapa, o seguinte será exibido. Primeiro, selecione **Bootcamp Screen Beacon** e clique no botão de **entrada**. Isso permitirá que você simule uma entrada de sinalização com beacon. 

![DSN](./images/app21.png)

Agora confira a tela da loja. Você verá o último produto visualizado aparecer nessa tela em 5 segundos.

![DSN](./images/screen2.png)

Em seguida, retorne para **Products**. Clique em qualquer produto, neste exemplo: **Beach blanket Tan**. 

![DSN](./images/app22.png)

Em seguida, retorne para a página inicial. Clique no ícone do **beacon**.

![DSN](./images/app23.png)

Em seguida, selecione **Bootcamp Screen Beacon** e clique no botão de **Entrada** novamente. Isso permitirá que você simule uma entrada de sinalização (beacon). 

![DSN](./images/app21.png)

Agora, confira a tela da loja novamente. Você verá o último produto visualizado aparecer nessa tela em 5 segundos.

![DSN](./images/screen3.png)

Agora, vamos verificar também o seu Visualizador de Perfil no site. Você verá muitos eventos que foram adicionados, para mostrar que qualquer interação com um cliente é coletada e armazenada na Adobe Experience Platform.

![DSN](./images/screen4.png)

Nos próximos exercícios, você irá configurar e testar sua própria jornada de entrada do beacon. 

Próxima etapa: [3.2 Crie seu evento](./ex2.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)
