---
description: Se você possuir um site de entrada principal em que os clientes possam ser identificados antes que visitem outros domínios, um CNAME poderá ativar o rastreamento entre domínios nos navegadores que não aceitam cookies de terceiros (como o Safari).
keywords: ordem de operações, serviço de ID
title: Visão geral da implementação CNAME
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 45%

---

# Visão geral da implementação CNAME{#cname-implementation-overview}

Implementações CNAME permitem personalizar o domínio de coleção usado pelo Adobe para que corresponda ao seu próprio domínio. Esses domínios também são chamados de domínios de coleção próprios. Essas implementações permitem que o Adobe defina cookies primários no lado do servidor, em vez de no lado do cliente usando JavaScript. Anteriormente, esses cookies primários do lado do servidor não estavam sujeitos aos limites impostos pela política de Prevenção de Rastreamento Inteligente (ITP) da Apple. No entanto, em novembro de 2020, a [!DNL Apple] atualizou suas políticas para que essas limitações também fossem aplicadas aos cookies definidos por CNAME. Atualmente, os cookies definidos no lado do servidor por meio do CNAME e os cookies definidos no lado do cliente por meio do Javascript são limitados a um prazo de sete dias ou 24 horas em ITP. Para obter mais informações sobre a política ITP, consulte este [!DNL Apple] documento [sobre prevenção de rastreamento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Embora uma implementação CNAME não forneça benefícios em termos de duração do cookie, pode haver outros benefícios. Esses benefícios incluem bloqueadores de anúncios e navegadores menos comuns que impedem o envio de dados para domínios que classificam como rastreadores. Nesses casos, o uso de um CNAME pode impedir que sua coleta de dados seja interrompida para usuários que utilizam essas ferramentas.

Além disso, as implementações CNAME permitem especificar **[!UICONTROL Escolher tipo de RDC personalizado]** que controla onde as ocorrências dos usuários são encaminhadas inicialmente. A maioria dos clientes não usa tipos de RDC personalizados.
