---
title: Usar o Opt-in para controlar atividades da Experience Cloud com base no consentimento do usuário
description: O Adobe Opt-in Object é uma extensão do serviço de identidade da Adobe Experience Platform, projetada para ajudá-lo a controlar se e quais soluções da Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 36%

---

# Controlar atividades da Experience Cloud com base no consentimento do usuário

O Adobe [!UICONTROL Opt-in] Object é uma extensão do Adobe [!UICONTROL Experience Platform Identity Service], projetada para ajudá-lo a controlar se e quais soluções da Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.

## Noções básicas do [!UICONTROL Opt-In]

Um aspecto importante das regras de privacidade é a aquisição e a transmissão do consentimento dos utilizadores sobre a forma como os seus dados pessoais podem ser utilizados e por quem. A versão mais recente do [!UICONTROL Identity Service] inclui uma funcionalidade que fornece um disparo condicional (como pré e pós-consentimento) das marcas de solução da Experience Cloud, com base no consentimento do usuário final. Esse processo é mostrado na imagem a seguir:

![Diagrama de como [!UICONTROL Opt-in] funciona](assets/opt-in.png)

[!UICONTROL Opt-in] funciona da seguinte maneira:

**Se [!UICONTROL Opt-in] estiver habilitado no Identity Service (por meio de uma variável Booliana), ele faz com que as bibliotecas de soluções da Experience Cloud atrasem o disparo de marcas ou a definição de cookies até que seja dado consentimento para essa solução.**

[!UICONTROL Opt-in] também permite decidir se as tags são acionadas antes do consentimento do usuário. Depois, essas informações de consentimento (junto com o consentimento dado pelo usuário final) são armazenadas para que possam ser usadas em ocorrências subsequentes. O armazenamento do consentimento está disponível nas opções [!UICONTROL Opt-in], ou você pode se integrar a um CMP e fazer com que ele armazene seleções de consentimento.

## Habilitando e configurando [!UICONTROL Opt-In]

O [!UICONTROL Opt-in] pode ser configurado mais facilmente com as marcas do Adobe Experience Platform (antigo Launch). Assista ao vídeo a seguir para saber como.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se você não estiver usando marcas Experience Platform, poderá definir a configuração de [!UICONTROL Opt-in] na inicialização do objeto de Visitante global, como mostrado na [documentação](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=pt-BR).

## Implementando [!UICONTROL Opt-In] na página

Toda essa configuração e material de backend estão sendo preparados para fornecer uma interface para que os visitantes do site tenham opções de consentimento. Essa interface pode ser criada por você ou você pode usar um parceiro CMP (Plataforma de gerenciamento de consentimento) para criar a interface.

Ao configurar uma interface para usar o [!UICONTROL Opt-in] para coletar o consentimento, ela deve ser configurada para chamar APIs que se conectarão ao [!UICONTROL Opt-in] e informá-la para dar consentimento a algumas ou todas as soluções da Adobe Experience Cloud. Informações detalhadas sobre essas APIs podem ser encontradas na [documentação de Referência do Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=pt-BR). Informações adicionais sobre o Opt-in também podem ser encontradas nas páginas de documentação adjacentes.

## Demonstração do [!UICONTROL Opt-In]

No vídeo a seguir, assista uma rápida demonstração do trabalho de [!UICONTROL Opt-in] na página e como isso pode influenciar se as soluções da Experience Cloud podem ou não definir cookies, iniciar beacons, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**OBSERVAÇÃO:** é importante observar que, no momento da redação deste artigo, o [!UICONTROL Opt-in] não foi integrado nas bibliotecas de todos os aplicativos da Experience Cloud. As bibliotecas atualmente com suporte para [!UICONTROL Opt-in] são:

* Serviço de identidade
* Analytics
* Audience Manager
* [!DNL Target]

