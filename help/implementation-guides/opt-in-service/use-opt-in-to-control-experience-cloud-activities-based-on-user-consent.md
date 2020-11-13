---
title: Usar a aceitação para controlar Atividades Experience Cloud com base no consentimento do usuário
description: O Adobe Opt-in Object é uma extensão do Adobe Experience Platform Identity Service, projetado para ajudá-lo a controlar se e quais soluções de Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Controlar Atividades Experience Cloud com base no consentimento do usuário

O Adobe [!UICONTROL Opt-in] Object é uma extensão do Adobe [!UICONTROL Experience Platform Identity Service], projetada para ajudá-lo a controlar se e quais soluções de Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.

## Noções básicas da [!UICONTROL aceitação]

Um aspecto importante das regras de privacidade é a aquisição e a transmissão do consentimento dos utilizadores sobre a forma como os seus dados pessoais podem ser utilizados e por quem. A versão mais recente do Serviço [!UICONTROL de] identidade inclui funcionalidade, que se situa entre o usuário (a interface do usuário) e as soluções de Adobe e fornece o acionamento condicional (por exemplo, consentimento prévio e posterior) das tags de solução Adobe Experience Cloud com base no consentimento do usuário final. Isso é mostrado na seguinte imagem:

![Diagrama de como a [!UICONTROL aceitação] funciona](assets/opt-in.png)

[!UICONTROL A aceitação] é basicamente o porteiro... ou é o mestre-chave? Você decide.

Resume-se a isto:

**Se a opção [!UICONTROL Aceitação] estiver ativada no Serviço de identidade (por meio de uma variável Booliana), ela atrasará as bibliotecas da solução Experience Cloud de disparar tags ou definir cookies até que o consentimento seja dado para essa solução.**

[!UICONTROL A aceitação] também permite decidir se as tags são acionadas *antes* do consentimento do usuário, e então essas informações de consentimento (junto com o consentimento dado pelo usuário final) são armazenadas, para que possam ser usadas em ocorrências subsequentes. A armazenamento do consentimento está disponível nas opções de [!UICONTROL aceitação] , ou você pode se integrar com um CMP e fazer com que ele armazene seleções de consentimento.

## Ativar e configurar a [!UICONTROL aceitação]

[!UICONTROL A aceitação] também é mais facilmente configurável com o Adobe Experience Platform Launch. Visualização o vídeo curto a seguir para ver como.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se você não estiver usando o Experience Platform Launch, poderá definir a configuração da [!UICONTROL opção]na inicialização do objeto de Visitante global, como mostrado na [documentação](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html).

## Implementação da [!UICONTROL aceitação] na página

Toda esta configuração e material de backend está apenas em preparação para fornecer uma interface para que os visitantes do site sejam apresentados com opções de consentimento. Essa interface pode ser criada por você ou você pode usar um parceiro CMP (Plataforma de gerenciamento de consentimento) para criar a interface.

Ao configurar uma interface para usar o [!UICONTROL Opt-in] para coletar consentimento, ele deve ser configurado para chamar APIs que entrarão em [!UICONTROL Opt-in] e informá-la para dar consentimento a algumas ou todas as soluções da Adobe Experience Cloud. Informações detalhadas sobre essas APIs podem ser encontradas na documentação [de Referência de](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html)aceitação. Informações adicionais sobre a aceitação também estão nas páginas de documentação adjacentes.

## [!UICONTROL Demonstração de aceitação]

No vídeo a seguir, assista uma rápida demonstração do [!UICONTROL Opt-in] trabalhando na página e como isso pode afetar se as soluções do Experience Cloud podem ou não definir cookies, iniciar beacons etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**NOTA:** É importante observar que, no momento da redação deste artigo, a [!UICONTROL opção] Opt-in não foi integrada nas bibliotecas para todas as soluções de Experience Cloud. As bibliotecas atualmente compatíveis com o [!UICONTROL Opt-in] são:

* Serviço de identidade
* Analytics
* Audience Manager
* [!DNL Target]
