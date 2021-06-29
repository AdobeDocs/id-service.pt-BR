---
description: Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).
keywords: ordem de operações, serviço de ID
title: Visão geral da implementação CNAME
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '221'
ht-degree: 100%

---


# Visão geral da implementação CNAME {#cname-implementation-overview}

Implementações CNAME permitem personalizar o domínio de coleção usado pelo Adobe para que corresponda ao seu próprio domínio. Isso permite que o Adobe defina cookies primários no lado do servidor, em vez de no lado do cliente, usando JavaScript. Anteriormente, esses cookies primários do lado do servidor não estavam sujeitos aos limites impostos pela política de Prevenção de Rastreamento Inteligente (ITP) da Apple. No entanto, em novembro de 2020, a [!DNL Apple] atualizou suas políticas para que essas limitações também fossem aplicadas aos cookies definidos por CNAME. Atualmente, os cookies definidos no lado do servidor por meio do CNAME e os definidos no lado do cliente por meio do JavaScript são limitados a um prazo de sete dias ou 24 horas em ITP. Para obter mais informações sobre a política ITP, consulte este [!DNL Apple] documento [sobre prevenção de rastreamento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Embora a implementação CNAME não forneça benefícios em termos de tempo de vida do cookie, pode haver outros benefícios, como bloqueadores de anúncios e navegadores menos comuns, impedindo que dados sejam enviados para domínios classificados por eles como rastreadores. Nesses casos, o uso de um CNAME pode impedir que a coleção de dados seja interrompida para usuários que utilizam essas ferramentas.