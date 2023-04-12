---
title: Bootcamp - Real-time Customer Profile - Create a segment - UI - Brazil
description: Bootcamp - Real-time Customer Profile - Create a segment - UI - Brazil
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 9b8d93b5-5bed-4600-8602-b438a0893612
---
# 1.3 Crie um segmento - UI

Neste exercício, você irá criar um segmento usando o Construtor de Segmentos da Adobe Experience Platform.

## História

Acesse [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Data Ingestion](./images/home.png)

Antes de continuar, você precisa selecionar um **sandbox**. O nome do sandbox a ser selecionado é ``Bootcamp``. É possível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] dedicado. 

![Data Ingestion](./images/sb1.png)

No menu à esquerda, acesse **Segments**. Nesta página, você tem uma visão geral de todos os segmentos existentes. Clique no botão + Criar segmento para começar a criar um novo segmento. 

![Segmentation](./images/menuseg.png)

Quando estiver no novo construtor de segmentos, você irá perceber imediatamente a opção de menu **Attributes** e a referência do **XDM Individual Profile**. 

![Segmentation](./images/segmentationui.png)

Como o XDM é a linguagem que alimenta o setor de experiência, o XDM também é a base para o construtor de segmentos. Todos os dados ingeridos na plataforma devem ser mapeados em relação ao XDM e, portanto, todos os dados se tornam parte do mesmo modelo de dados, independentemente da origem desses dados. Isso oferece uma grande vantagem ao criar segmentos, pois a partir dessa interface do usuário do construtor de segmento, é possível combinar dados de qualquer origem no mesmo fluxo de trabalho. Os segmentos criados no Construtor de segmentos podem ser enviados para soluções como Adobe Target, Adobe Campaign e Adobe Audience Manager para ativação.

Agora você precisa criar um segmento de todos os clientes que visualizaram o produto **Real-Time CDP**.

Para construir este segmento, você precisa adicionar um Evento de experiência. Você pode encontrar todos os Eventos de experiência clicando no ícone **Events** na barra de menu **Fields**. 

![Segmentation](./images/findee.png)

Em seguida, você verá o nó **XDM ExperienceEvents** do nível superior. Clique em **XDM ExperienceEvent**. 

![Segmentation](./images/see.png)

Acesse **Product List Items**.

![Segmentation](./images/plitems.png)

Selecione **Name** e arraste e solte o objeto **Name** do menu à esquerda na tela do construtor de segmentos na seção **Events**. Em seguida, o seguinte será exibido: 

![Segmentation](./images/eewebpdtlname.png)

O parâmetro de comparação deve ser **equals** e, no campo de entrada, insira **Real-time CDP**.

![Segmentation](./images/pv.png)

Sempre que adicionar um elemento ao construtor de segmentos, você pode clicar no botão **Refresh Estimate** para obter uma nova estimativa da população em seu segmento. 

![Segmentation](./images/refreshest.png)

Para **Evaluation Method**, selecione **Edge**.

![Segmentation](./images/evedge.png)

Por fim, vamos dar um nome ao seu segmento e salvá-lo. 

Como modelo de nomenclatura, use:

- `seuSobrenome - Interest in Real-Time CDP`

Em seguida, clique no botão **Save and Close** para salvar seu segmento. 

![Segmentation](./images/segmentname.png)

Agora você irá retornar à página de visão geral do segmento, onde verá uma visualização de amostra dos perfis de clientes que se qualificam para o seu segmento.

![Segmentation](./images/savedsegment.png)

Agora você pode continuar no próximo exercício e usar seu segmento com o Adobe Target.

Próxima etapa: [1.4 Ação: envie seu segmento para o Adobe Target](./ex4.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
