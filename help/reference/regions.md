---
description: O cookie AMCV contém a ECID e uma ID de região para os visitantes do site. Essas IDs são armazenadas como pares de valores chave. A ID mid user contém a ECID do visitante. A ID aamlh region contém a ID de região dos visitantes do site. É possível recuperar essas informações ao analisar o cookie AMCV.
keywords: Serviço de ID de visitante
title: Obter as IDs de região e usuário do cookie AMCV ou do serviço de ID de visitante
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 235
ht-degree: 42%

---

# Obter as IDs de região e usuário do cookie AMCV ou do serviço de ID de visitante {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

O cookie AMCV contém a ECID e uma ID de região para os visitantes do site. Essas IDs são armazenadas como pares de valores chave. A ID mid:user contém a ECID do visitante. A ID aamlh:region contém a ID de região dos visitantes do site. É possível recuperar essas informações ao analisar o cookie AMCV.

Para obter mais informações, consulte [Obter IDs de usuário e regiões por meio do Serviço de ID de visitante](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=pt-BR).

Se você for um cliente do Audience Manager, é possível obter a ID da região da resposta enviada pelo Servidor de coleta de dados (DCS). Consulte [Obter IDs de usuário e regiões de uma resposta de DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=pt-BR).

Você também pode obter a ID da região com um método `GET` fornecido pelo Serviço de ID do visitante. Consulte [Obter IDs de região (Dica de localização)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

