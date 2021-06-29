---
description: O cookie AMCV contém a Experience Cloud ID (MID) e uma ID de região para os visitantes do site. Essas IDs são armazenadas como pares de valores chave. A ID mid user contém a Experience Cloud ID do visitante. A ID aamlh region contém a ID de região dos visitantes do site. É possível recuperar essas informações ao analisar o cookie AMCV.
keywords: Serviço de ID
title: Obter as IDs de região e usuário do cookie AMCV ou do serviço de ID
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '224'
ht-degree: 100%

---

# Obter as IDs de região e usuário do cookie AMCV ou do serviço de ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

O cookie AMCV contém a Experience Cloud ID (MID) e uma ID de região para os visitantes do site. Essas IDs são armazenadas como pares de valores chave. A ID mid:user contém a Experience Cloud ID do visitante. A ID aamlh:region contém a ID de região dos visitantes do site. É possível recuperar essas informações ao analisar o cookie AMCV.

Para obter mais informações, consulte [Obter IDs de usuário e regiões por meio do serviço de identidade da Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=pt-BR).

Se você for um [!DNL Audience Manager] cliente do, é possível obter a ID da região da resposta enviada pelo Servidor de coleta de dados (DCS). Consulte [Obter IDs de usuário e regiões de uma resposta de DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=pt-BR).

Também é possível obter a ID da região com um `GET` método fornecido pelo serviço de ID. Consulte [Obter IDs de região (Dica de localização)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
