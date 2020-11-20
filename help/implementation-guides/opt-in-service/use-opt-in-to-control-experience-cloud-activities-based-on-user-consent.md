---
title: Usar o Opt-in para controlar atividades da Experience Cloud com base no consentimento do usuário
description: O Adobe Opt-in Object é uma extensão do Adobe Experience Platform Identity Service, projetado para ajudá-lo a controlar se e quais soluções da Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.
translation-type: ht
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: ht
source-wordcount: '554'
ht-degree: 100%

---


# Controlar atividades da Experience Cloud com base no consentimento do usuário

O Adobe [!UICONTROL Opt-in] Object é uma extensão do Adobe [!UICONTROL Experience Platform Identity Service], projetada para ajudá-lo a controlar se e quais soluções da Experience Cloud podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.

## Noções básicas do [!UICONTROL Opt-in]

Um aspecto importante das regras de privacidade é a aquisição e a transmissão do consentimento dos utilizadores sobre a forma como os seus dados pessoais podem ser utilizados e por quem. A versão mais recente do [!UICONTROL Identitiy Service] inclui uma funcionalidade, que se situa entre o usuário (a interface do usuário) e as soluções da Adobe e fornece o acionamento condicional (por exemplo, consentimento prévio e posterior) das tags de solução da Adobe Experience Cloud com base no consentimento do usuário final. Isso é mostrado na imagem a seguir:

![Diagrama de como o [!UICONTROL Opt-in] funciona](assets/opt-in.png)

O [!UICONTROL Opt-in] é basicamente o porteiro... ou é o guardião das chaves? Você decide.

Ela se resume em:

**Se o [!UICONTROL Opt-in] estiver ativado no Identity Service (por meio de uma variável Booliana), ele faz com que as bibliotecas de soluções da Experience Cloud atrasem o disparo de tags ou a definição de cookies até que o consentimento seja dado para essa solução.**

O [!UICONTROL Opt-in] também permite decidir se as tags são acionadas *antes* do consentimento do usuário. Depois, essas informações de consentimento (junto com o consentimento dado pelo usuário final) são armazenadas para que possam ser usadas em ocorrências subsequentes. O armazenamento do consentimento está disponível nas opções do [!UICONTROL Opt-in], ou você pode se integrar a um CMP e fazer com que ele armazene seleções de consentimento.

## Ativar e configurar o [!UICONTROL Opt-in]

O [!UICONTROL Opt-in] também é configurado mais facilmente com o Adobe Experience Platform Launch. Assista ao vídeo a seguir para saber como.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12&captions=por_br)

Se você não estiver usando o Experience Platform Launch, poderá definir a configuração do [!UICONTROL Opt-in] na inicialização do objeto de Visitante global, como mostrado na [documentação](https://marketing.adobe.com/resources/help/pt_BR/mcvid/getting-started.html).

## Implementação do [!UICONTROL Opt-in] na página

Toda essa configuração e material de backend estão sendo preparados para fornecer uma interface para que os visitantes do site tenham opções de consentimento. Essa interface pode ser criada por você ou você pode usar um parceiro CMP (Plataforma de gerenciamento de consentimento) para criar a interface.

Ao configurar uma interface para usar o [!UICONTROL Opt-in] para coletar o consentimento, ela deve ser configurada para chamar APIs que entrarão no [!UICONTROL Opt-in] e informá-la para dar consentimento a algumas ou todas as soluções da Adobe Experience Cloud. Informações detalhadas sobre essas APIs podem ser encontradas na [documentação de Referência do Opt-in](https://marketing.adobe.com/resources/help/pt_BR/mcvid/api.html). Informações adicionais sobre o Opt-in também podem ser encontradas nas páginas de documentação adjacentes.

## Demonstração do [!UICONTROL Opt-in]

No vídeo a seguir, assista uma rápida demonstração do [!UICONTROL Opt-in] funcionando na página e como isso pode afetar se as soluções da Experience Cloud podem ou não definir cookies, iniciar beacons etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12&captions=por_br)

**NOTA:** é importante observar que, no momento da redação deste artigo, o [!UICONTROL Opt-in] não foi integrado nas bibliotecas para todas as soluções da Experience Cloud. As bibliotecas atualmente compatíveis com o [!UICONTROL Opt-in] são:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
