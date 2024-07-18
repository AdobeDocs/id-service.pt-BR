---
title: Usar o Opt-in para controlar atividades da Experience Cloud com base no consentimento do usuário
description: O Adobe Opt-in Object é uma extensão do serviço de identidade da Adobe Experience Platform, projetada para ajudá-lo a controlar se e quais soluções da Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 100%

---

# Controlar atividades da Experience Cloud com base no consentimento do usuário

O Adobe [!UICONTROL Opt-in] Object é uma extensão do [!UICONTROL serviço de identidade da Adobe Experience Platform], projetada para ajudá-lo a controlar se e quais soluções da Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.

## Noções básicas do [!UICONTROL Opt-in]

Um aspecto importante das regras de privacidade é a aquisição e a transmissão do consentimento dos utilizadores sobre a forma como os seus dados pessoais podem ser utilizados e por quem. A versão mais recente do [!UICONTROL serviço de identidade] inclui uma funcionalidade que fornece um disparo condicional (como pré e pós-consentimento) das tags da solução da Experience Cloud, com base no consentimento do usuário final. Esse processo é mostrado na imagem a seguir:

![Diagrama de como o [!UICONTROL Opt-in] funciona](assets/opt-in.png)

O [!UICONTROL Opt-in] funciona da seguinte forma:

**Se o [!UICONTROL Opt-in] estiver ativado no serviço de identidade (por meio de uma variável Booleana), ele faz com que as bibliotecas de soluções da Experience Cloud atrasem o disparo de tags ou a definição de cookies até que seja dado consentimento para essa solução.**

O [!UICONTROL Opt-in] também permite decidir se as tags são disparadas antes do consentimento do usuário. Depois, essas informações de consentimento (junto com o consentimento dado pelo usuário final) são armazenadas para que possam ser usadas em ocorrências subsequentes. O armazenamento do consentimento está disponível nas opções do [!UICONTROL Opt-in], ou você pode se integrar a um CMP e fazer com que ele armazene seleções de consentimento.

## Ativar e configurar o [!UICONTROL Opt-in]

O [!UICONTROL Opt-in] é configurado mais facilmente com a Adobe Experience Platform (antigo Launch). Assista ao vídeo a seguir para saber como.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se você não estiver usando tags da Experience Platform, poderá definir a configuração do [!UICONTROL Opt-in] na inicialização do objeto de Visitante global, como mostrado na [documentação](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=pt-BR).

## Implementação do [!UICONTROL Opt-in] na página

Toda essa configuração e material de backend estão sendo preparados para fornecer uma interface para que os visitantes do site tenham opções de consentimento. Essa interface pode ser criada por você ou você pode usar um parceiro CMP (Plataforma de gerenciamento de consentimento) para criar a interface.

Ao configurar uma interface para usar o [!UICONTROL Opt-in] para coletar o consentimento, ela deve ser configurada para chamar APIs que entrarão no [!UICONTROL Opt-in] e informá-la para dar consentimento a algumas ou todas as soluções da Adobe Experience Cloud. Informações detalhadas sobre essas APIs podem ser encontradas na [documentação de Referência do Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=pt-BR). Informações adicionais sobre o Opt-in também podem ser encontradas nas páginas de documentação adjacentes.

## Demonstração do [!UICONTROL Opt-in]

No vídeo a seguir, assista uma rápida demonstração do funcionamento do [!UICONTROL Opt-in] na página e como ele pode influenciar se as soluções da Experience Cloud podem ou não definir cookies, iniciar beacons, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**OBSERVAÇÃO:** é importante observar que, no momento da redação deste artigo, o [!UICONTROL Opt-in] não havia sido integrado nas bibliotecas de todos os aplicativos da Experience Cloud. As bibliotecas atualmente compatíveis com o [!UICONTROL Opt-in] são:

* Serviço de identidade
* Analytics
* Audience Manager
* [!DNL Target]
