---
title: Usar o Opt-in para controlar atividades da Experience Cloud com base no consentimento do usuário
description: O Adobe Opt-in Object é uma extensão do Adobe Experience Platform Identity Service, projetada para ajudá-lo a controlar se e quais soluções do Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# Controlar atividades da Experience Cloud com base no consentimento do usuário

O Adobe [!UICONTROL Opt-in] O objeto é uma extensão do Adobe [!UICONTROL Serviço de identidade do Experience Platform], projetado para ajudá-lo a controlar se e quais soluções do Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.

## Noções básicas do [!UICONTROL Opt-in]

Um aspecto importante das regras de privacidade é a aquisição e a transmissão do consentimento dos utilizadores sobre a forma como os seus dados pessoais podem ser utilizados e por quem. A versão mais recente do [!UICONTROL Serviço de identidade] O inclui uma funcionalidade que fornece o acionamento condicional (como pré e pós consentimento) das tags de solução do Experience Cloud, com base no consentimento do usuário final. Esse processo é mostrado na seguinte imagem:

![ Diagrama de como o [!UICONTROL  Opt-in] funciona](assets/opt-in.png)

[!UICONTROL Opt-in] funciona da seguinte forma:

**Se o [!UICONTROL Opt-in] estiver ativado no Identity Service (por meio de uma variável Booliana), ele faz com que as bibliotecas de soluções da Experience Cloud atrasem o disparo de tags ou a definição de cookies até que o consentimento seja dado para essa solução.**

[!UICONTROL Opt-in] O também permite decidir se as tags são acionadas antes do consentimento do usuário, e então essas informações de consentimento (junto com o consentimento dado pelo usuário final) são armazenadas para que possam ser usadas em ocorrências subsequentes. O armazenamento do consentimento está disponível nas opções do [!UICONTROL Opt-in], ou você pode se integrar a um CMP e fazer com que ele armazene seleções de consentimento.

## Ativar e configurar o [!UICONTROL Opt-in]

[!UICONTROL Opt-in] O é configurado mais facilmente com tags Adobe Experience Platform (anteriormente, Launch). Assista ao vídeo a seguir para saber como.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se você não estiver usando tags Experience Platform, é possível definir [!UICONTROL Opt-in]Configuração do na inicialização do objeto de Visitante global, como mostrado no [documentação](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## Implementação do [!UICONTROL Opt-in] na página

Toda essa configuração e material de backend estão sendo preparados para fornecer uma interface para que os visitantes do site tenham opções de consentimento. Essa interface pode ser criada por você ou você pode usar um parceiro CMP (Plataforma de gerenciamento de consentimento) para criar a interface.

Ao configurar uma interface para usar o [!UICONTROL Opt-in] para coletar o consentimento, ela deve ser configurada para chamar APIs que entrarão no [!UICONTROL Opt-in] e informá-la para dar consentimento a algumas ou todas as soluções da Adobe Experience Cloud. Informações detalhadas sobre essas APIs podem ser encontradas na [documentação de Referência do Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en). Informações adicionais sobre o Opt-in também podem ser encontradas nas páginas de documentação adjacentes.

## Demonstração do [!UICONTROL Opt-in]

No vídeo a seguir, assista uma rápida demonstração de [!UICONTROL Opt-in] trabalhar na página e como isso pode afetar se as soluções do Experience Cloud podem definir cookies, iniciar beacons e assim por diante.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**OBSERVAÇÃO:** É importante observar que, no momento da redação do presente artigo, [!UICONTROL Opt-in] O não foi integrado às bibliotecas para todos os aplicativos do Experience Cloud. As bibliotecas atualmente compatíveis com o [!UICONTROL Opt-in] são:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
