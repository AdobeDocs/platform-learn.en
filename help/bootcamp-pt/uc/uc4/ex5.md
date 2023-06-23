---
title: Bootcamp - Customer Journey Analytics - Visualization using Customer Journey Analytics - Brazil
description: Bootcamp - Customer Journey Analytics - Visualization using Customer Journey Analytics - Brazil
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: eb5eac54-22d8-428b-acac-16570f75085e
---
# 4.5 Visualização usando o Customer Journey Analytics

## Objetivos

- Entenda a UI do Analysis Workspace 
- Conheça alguns recursos que tornam o Analysis Workspace tão diferente. 
- Aprenda a analisar no CJA usando o Analysis Workspace 

## Contexto

Neste exercício, você usará o Analysis Workspace no CJA para analisar visualizações de produtos, funis de produtos, rotatividade, etc. 

Vamos usar o projeto que você criou em  [4.4 Preparação de dados no Analysis Workspace](./ex4.md), então acesse [https://analytics.adobe.com](https://analytics.adobe.com).

![demo](./images/prohome.png)

Abra seu projeto `yourLastName - Omnichannel Analysis`.

Com seu projeto aberto e Visualização de dados `yourLastName - Omnichannel Analysis` selecionado, você está pronto para começar a construir suas primeiras visualizações. 

![demo](./images/prodataView1.png)

## Quantas visualizações de produtos temos diariamente?

Em primeiro lugar, precisamos selecionar as datas certas para analisar os dados. Acesse o menu suspenso do calendário no lado direito da tela. Clique nele e selecione o intervalo de datas aplicável. 

>[!IMPORTANT]
>
>Selecione um intervalo de datas como **This Week** ou **This Month**. Os dados disponíveis mais recentes foram absorvidos em 19 de setembro de 2022. 

![demo](./images/pro1.png)
No menu do lado esquerdo (área de componentes), encontre as métricas calculadas **Product Views**. Selecione-as e arraste e solte na tela, no canto superior direito da tabela de forma livre.

![demo](./images/pro2.png)

Automaticamente a dimensão **Day** será adicionada para criar sua primeira tabela. Agora você pode ver sua pergunta respondida imediatamente. 

![demo](./images/pro3.png)

Em seguida, clique com o botão direito do mouse no resumo da métrica.

![demo](./images/pro4.png)

Clique em **Visualize** e selecione **Line** como visualização. 

![demo](./images/pro5.png)

Você verá as suas visualizações de produto por dia.

![demo](./images/pro6.png)

Você pode alterar o escopo de tempo para o dia clicando em **Settings** na visualização.

![demo](./images/pro7.png)

Clique no ponto ao lado de **Line** e **Manage the Data Source**.

![demo](./images/pro7a.png)

Em seguida, clique em **Lock Selection** e selecione **Selected Items** para bloquear esta visualização para que ela sempre exiba uma linha do tempo de Visualizações de produtos.

![demo](./images/pro7b.png)

## 5 produtos mais vistos

Quais são os 5 produtos mais vistos? 

Lembre-se de salvar o projeto de tempos em tempos.

|  OS        | Short cut   | 
| ----------------- |-------------| 
| Windows | Control + S          | 
| Mac | Command + S          |

Vamos começar a encontrar os 5 produtos mais vistos. No menu do lado esquerdo, encontre o Nome do produto - Dimensão.

![demo](./images/pro8.png)

Agora arraste e solte **Product Name** para substituir a dimensão **Day**:

Este será o resultado.

![demo](./images/pro10a.png)

Em seguida, tente dividir um dos produtos por Nome da marca. Pesquise **brandName** e arraste para baixo do primeiro nome do produto.

![demo](./images/pro13.png)

Em seguida, faça um detalhamento usando o Agente de usuário. Pesquise **User Agent** e arraste-o para baixo do nome da marca.

![demo](./images/pro15.png)

Em seguida, será exibida a tela abaixo: 

![demo](./images/pro15a.png)

Por fim, você pode adicionar mais visualizações. No lado esquerdo, em visualizações, pesquise `Donut`. Pegue `Donut`, arraste e solte na tela sob a visualização **Line** 

![demo](./images/pro18.png)

Next, in the Table, select the first 5 **User Agent**  rows from the breakdown we did under **Google Pixel XL 32GB Black Smartphone** > **Citi Signal**. While selecting the 5 rows, hold the **CTRL** button (on Windows) or the **Command** button (on Mac).

Em seguida, na Tabela, selecione as primeiras 5 linhas de **User Agent** do detalhamento que fizemos em **Google Pixel XL 32GB Black Smartphone** > **Citi Signal**. Ao selecionar as 5 linhas, segure o botão **CTRL** (no Windows) ou o botão **Command** (no Mac). 

![demo](./images/pro20.png)

Você verá o gráfico de donut alterado:

![demo](./images/pro21.png)

Você pode até adaptar o design para ser mais legível, tornando o gráfico de **Line** e o gráfico de **Donut** um pouco menor para que sejam exibidos lado a lado: 

![demo](./images/pro22.png)

Clique no ponto ao lado de *Donut** para **Manage the Data Source**. Em seguida, clique em **Lock Selection** para bloquear essa visualização para que ela sempre exiba uma linha do tempo de Visualizações de produto. 

![demo](./images/pro22b.png)

Saiba mais sobre visualizações usando o Analysis Workspace em: 

- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html)
- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html)

## Funil de interação do produto, da visualização à compra 

Existem muitas formas de resolver esta questão. Uma delas é usar o Tipo de Interação de Produto e usá-lo em uma tabela de formato livre. Outra forma é usar uma **Fallout Visualization**. Vamos usar o último, pois queremos visualizar e analisar ao mesmo tempo. 

Feche o painel atual clicando aqui: 

![demo](./images/pro23.png)

Agora adicione um novo painel em branco clicando em **+ Add Blank Panel**.

![demo](./images/pro24.png)

Clique na visualização de **Fallout**.

![demo](./images/pro25.png)

Selecione o mesmo intervalo de datas do exercício anterior.

![demo](./images/prodatef.png)

Em seguida, você verá:

![demo](./images/prodatefa.png)

Encontre a dimensão **Event Type** nos componentes no lado esquerdo:

![demo](./images/pro26.png)

Clique na seta para abrir a dimensão:

![demo](./images/pro27.png)

Você verá todos os Tipos de eventos disponíveis. 

![demo](./images/pro28.png)

Selecione o item **commerce.productViews** e arraste e solte-o no campo **Add Touchpoint** dentro da **Fallout Visualization**.

![demo](./images/pro29.png)

Faça o mesmo com **commerce.productListAdds** and **commerce.purchases** e solte-os no campo **Add Touchpoint** dentro da  **Fallout Visualization**. Sua visualização agora deve ser semelhante ao seguinte:

![demo](./images/props1.png)

Você pode fazer muitas coisas aqui. Alguns exemplos: comparar ao longo do tempo, comparar cada passo por dispositivo ou comparar por fidelidade. No entanto, se quisermos analisar coisas interessantes como porque os clientes não compram depois de adicionar um item ao carrinho, podemos usar a melhor ferramenta do CJA: clicar com o botão direito. 

Clique com o botão direito do mouse no touchpoint **commerce.productListAdds**. Em seguida, clique em **Breakdown fallout at this touchpoint**.

![demo](./images/pro32.png)

Uma nova tabela de formato livre será criada para analisar o que as pessoas fizeram se não compraram.

![demo](./images/pro33.png)

Altere o **Event Type** by **Page Name**, na nova tabela de formato livre, para ver em quais páginas eles estão indo, em vez da Página de confirmação de compra.

![demo](./images/pro34.png)

## O que as pessoas fazem no site antes de acessar a página Cancelar serviço?

Novamente, há muitas formas de realizar essa análise. Vamos usar a análise de fluxo para iniciar parte da descoberta. 

Feche o painel atual clicando aqui: 

![demo](./images/pro0.png)

Agora adicione um novo painel em branco clicando em **+ Add Blank Panel**.

![demo](./images/pro0a.png)

Clique na visualização **Flow**.

![demo](./images/pro35.png)

Em seguida, será exibido:

![demo](./images/pro351.png)

Selecione o mesmo intervalo de datas do exercício anterior.

![demo](./images/pro0b.png)

Encontre a dimensão **Page Name** nos componentes no lado esquerdo:

![demo](./images/pro36.png)

Clique na seta para abrir a dimensão: 

![demo](./images/pro37.png)

Você encontrará todas as páginas vistas. Encontre o nome da página: **Cancel Service**.
Arraste e solte **Cancel Service** na Visualização de fluxo no campo do meio:

![demo](./images/pro38.png)

Em seguida, será exibido:

![demo](./images/pro40.png)

Vamos agora analisar se os clientes que visitaram a página C**Cancel Service** no site também ligaram para o call center e qual foi o resultado. 

Nas dimensões, retorne e encontre Tipo de interação de chamada. Arraste e solte **Call Interaction Type** para substituir a primeira interação à direita em **Flow Visualization**. 

![demo](./images/pro43.png)

Agora você visualiza o ticket de suporte dos clientes que ligaram para a central de atendimento depois de visitar a página **Cancel Service**.

![demo](./images/pro44.png)

Em seguida, nas dimensões, procure **Call Feeling**. Arraste e solte para substituir a primeira interação à direita na visualização de fluxo.

![demo](./images/pro46.png)

Em seguida, será exibido:

![demo](./images/flow.png)

Como pode ver, executamos uma análise omnichannel usando a visualização de fluxo. Graças a isso, descobrimos que alguns clientes que estavam pensando em cancelar o serviço tiveram uma avaliação positiva depois de ligar para o call center. Talvez tenhamos mudado de ideia com uma promoção? 

## Qual é o desempenho dos clientes com um contato de Call center Positivo em relação aos principais KPIs?

Primeiramente, vamos segmentar os dados para obter apenas usuários com chamadas **positive**. No CJA, os Segmentos são chamados de Filtros. Acesse para filtros na área de componentes (no lado esquerdo) e clique em **+**. 

![demo](./images/pro58.png)

Dentro do Construtor de filtro, dê um nome ao filtro

|  Name        | Description    | 
| ----------------- |-------------| 
| Call Feeling - Positive | Call Feeling - Positive          | 

![demo](./images/pro47.png)

Nos componentes (dentro do Construtor de filtro), encontre **Call Feeling** e arraste e solte na Definição do construtor de filtro. 

![demo](./images/pro48.png)

Agora selecione **positive** como valor para o filtro. 

![demo](./images/pro49.png)

Altere o escopo para o nível **Person**.

![demo](./images/pro50.png)

Para finalizar, basta clicar em **Save**.

![demo](./images/pro51.png)

Então, você irá retornar para esta tela. Se ainda não retornou, feche o painel anterior.

![demo](./images/pro0c.png)

Agora adicione um novo painel em branco clicando em **+ Add Blank Panel**.

![demo](./images/pro24c.png)

Selecione o mesmo intervalo de datas do exercício anterior.

![demo](./images/pro24d.png)

Clique em **Freeform table**.

![demo](./images/pro52.png)

Agora arraste e solte o filtro que você acabou de criar.

![demo](./images/pro53.png)

Hora de adicionar algumas métricas. Comece com **Product Views**. Arraste e solte na tabela de forma livre. Você também pode excluir a métrica **Events**. 

![demo](./images/pro54.png)

Faça o mesmo com **People**, **Add to Cart** e **Purchases**. Você vai acabar com uma tabela como a seguinte. 

![demo](./images/pro55.png)

Graças à primeira análise de fluxo, uma nova pergunta surgiu. Então decidimos criar esta tabela e verificar alguns KPIs em um segmento para responder a essa pergunta. Como você pode ver, o tempo de insight é muito mais rápido do que usar SQL ou usar outras soluções de BI.

## Recapitulação do Analysis Workspace e do Customer Journey Analytics

O Analysis Workspace remove todas as limitações típicas de um relatório do Analytics. Ele fornece uma tela robusta e flexível para criar projetos de analytics personalizados. Arraste e solte qualquer número de tabelas de dados, visualizações e componentes (dimensões, métricas, segmentos e granularidades de tempo) para um projeto. Você pode criar de forma instantânea filtros e analises, gráficos de coorte, alertas, segmentos, análises de fluxo e relatórios de curadoria e agendamento para compartilhar com qualquer pessoa em seu negócio.

Próxima etapa: [4.6 De insights a ação](./ex6.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)
