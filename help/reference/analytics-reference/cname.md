---
description: Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).
keywords: ordem de operações, serviço de ID
seo-description: Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).
seo-title: Visão geral da implementação CNAME
title: Visão geral da implementação CNAME
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# Visão geral da implementação CNAME{#cname-implementation-overview}

As implementações CNAME permitem personalizar o domínio de coleta usado pelo Adobe para que correspondam ao seu próprio domínio. Isso permite que o Adobe defina cookies primários no lado do servidor, em vez de no lado do cliente usando JavaScript. Anteriormente, esses cookies primários do lado do servidor não estavam sujeitos aos limites impostos pela política de Prevenção de Rastreamento Inteligente (ITP) da Apple. No entanto, em novembro de 2020, [!DNL Apple] atualizou suas políticas para que essas limitações também fossem aplicadas aos cookies definidos por CNAME. Atualmente, ambos os cookies definidos no lado do servidor por meio do CNAME e os cookies definidos no lado do cliente por meio do Javascript são limitados a um prazo de sete dias ou 24 horas em ITP. Para obter mais informações sobre a política ITP, consulte este [!DNL Apple] documento [sobre prevenção de rastreamento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Embora a implementação CNAME não forneça benefícios em termos de duração do cookie, pode haver outros benefícios, como bloqueadores de anúncios e navegadores menos comuns, impedindo que os dados sejam enviados para domínios que classificam como rastreadores. Nesses casos, o uso de um CNAME pode impedir que sua coleta de dados seja interrompida para usuários que utilizam essas ferramentas.