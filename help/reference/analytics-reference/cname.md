---
description: Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).
keywords: ordem de operações, serviço de ID
title: Visão geral da implementação CNAME
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: d2586fc722be25df1b82caaf2cc6de6a2a6c31bf
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 100%

---

# Visão geral da implementação CNAME {#cname-implementation-overview}

Implementações CNAME permitem personalizar o domínio de coleção usado pelo Adobe para que corresponda ao seu próprio domínio. Esses domínios também são chamados de domínios de coleção próprios. Essas implementações permitem que a Adobe defina cookies próprios no lado do servidor, em vez de no lado do cliente, usando JavaScript. Anteriormente, esses cookies primários do lado do servidor não estavam sujeitos aos limites impostos pela política de Prevenção de Rastreamento Inteligente (ITP) da Apple. No entanto, em novembro de 2020, a [!DNL Apple] atualizou suas políticas para que essas limitações também fossem aplicadas aos cookies definidos por CNAME. Atualmente, os cookies definidos no lado do servidor por meio do CNAME e os definidos no lado do cliente por meio do JavaScript são limitados a um prazo de sete dias ou 24 horas em ITP. Para obter mais informações sobre a política ITP, consulte este [!DNL Apple] documento [sobre prevenção de rastreamento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Embora uma implementação CNAME não forneça benefícios em termos de duração do cookie, ela pode oferecer outros benefícios. Esses benefícios incluem bloqueadores de anúncios e navegadores menos comuns que impedem o envio de dados para domínios que eles classificam como rastreadores. Nesses casos, o uso de um CNAME pode impedir que a coleção de dados seja interrompida para usuários que utilizam essas ferramentas.

Além disso, as implementações de CNAME permitem [escolher um tipo de RDC personalizado](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=pt-BR), que controla para onde as ocorrências dos usuários são encaminhadas inicialmente. A maioria dos clientes não usa tipos personalizados de RDC.
