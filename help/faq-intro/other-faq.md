---
description: Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso de outras soluções da Experience Cloud com o serviço de ID.
keywords: Serviço de ID
title: Perguntas frequentes de outras soluções da Experience Cloud
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: e171c94ccfa1f4fe9b8d909d0204adb94f20cbb6
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 100%

---

# Perguntas frequentes de outras soluções da Experience Cloud {#faqs-for-other-experience-cloud-solutions}

Perguntas frequentes sobre recursos, funcionalidades e problemas relacionados ao uso de outras soluções da Experience Cloud com o serviço de ID.

## Analytics e Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**O histórico de visitas de um usuário poderá ser exportado do [!DNL Adobe Analytics] para o [!DNL Audience Manager] depois que eu implementar o serviço de identidade da Experience Cloud?**

Existem duas opções aqui:

* Se um usuário tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico serão incluídos na exportação de dados para o [!DNL Audience Manager].
* Se um usuário não tiver uma atividade de visitação após a implementação do Serviço de ID, o visitante e seu histórico não serão incluídos na exportação de dados para o Audience Manager. Como a nova atividade não está presente, não temos como associar a ID do Analytics à Experience Cloud ID.
