---
title: Usar o Opt-in para controlar atividades corporativas do CX com base no consentimento do usuário
description: O Adobe Opt-in Object é uma extensão do serviço de ID de visitante da Adobe, projetada para ajudá-lo a controlar se e quais soluções da CX Enterprise podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 28%

---

# Controlar atividades corporativas do CX com base no consentimento do usuário

O Adobe [!UICONTROL Opt-in] Object é uma extensão do Serviço de ID de visitante da Adobe, projetada para ajudá-lo a controlar se e quais soluções da CX Enterprise podem criar cookies em páginas da Web ou iniciar beacons, com base no consentimento do usuário final.

## Noções básicas do [!UICONTROL Opt-In]

Um aspecto importante das regras de privacidade é a aquisição e a transmissão do consentimento dos utilizadores sobre a forma como os seus dados pessoais podem ser utilizados e por quem. A versão mais recente do Serviço de ID de visitante inclui uma funcionalidade que fornece um disparo condicional (como pré e pós-consentimento) das tags da solução CX Enterprise, com base no consentimento do usuário final. Esse processo é mostrado na imagem a seguir:

![Diagrama de como [!UICONTROL Opt-in] funciona](assets/opt-in.png)

[!UICONTROL Opt-in] funciona da seguinte maneira:

**Se [!UICONTROL Opt-in] estiver habilitado no Serviço de ID do Visitante (por meio de uma variável Booliana), ele faz com que as bibliotecas de soluções do CX Enterprise atrasem o disparo de tags ou a definição de cookies até que seja dado consentimento para essa solução.**

[!UICONTROL Opt-in] também permite decidir se as tags são acionadas antes do consentimento do usuário. Depois, essas informações de consentimento (junto com o consentimento dado pelo usuário final) são armazenadas para que possam ser usadas em ocorrências subsequentes. O armazenamento do consentimento está disponível nas opções [!UICONTROL Opt-in], ou você pode se integrar a um CMP e fazer com que ele armazene seleções de consentimento.

## Habilitando e configurando [!UICONTROL Opt-In]

[!UICONTROL Opt-in] é configurado mais facilmente com tags. Assista ao vídeo a seguir para saber como.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Se você não estiver usando marcas, poderá definir a configuração de [!UICONTROL Opt-in] na inicialização do objeto de Visitante global, como mostrado na [documentação](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=pt-BR).

## Implementando [!UICONTROL Opt-In] na página

Toda essa configuração e material de backend estão sendo preparados para fornecer uma interface para que os visitantes do site tenham opções de consentimento. Essa interface pode ser criada por você ou você pode usar um parceiro CMP (Plataforma de gerenciamento de consentimento) para criar a interface.

Ao configurar uma interface para usar o [!UICONTROL Opt-in] para coletar o consentimento, ela deve ser configurada para chamar APIs que se conectarão ao [!UICONTROL Opt-in] e informá-la para dar consentimento a algumas ou todas as soluções corporativas do Adobe CX. Informações detalhadas sobre essas APIs podem ser encontradas na [documentação de Referência do Opt-in](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=pt-BR). Informações adicionais sobre o Opt-in também podem ser encontradas nas páginas de documentação adjacentes.

## Demonstração do [!UICONTROL Opt-In]

No vídeo a seguir, assista uma rápida demonstração do trabalho de [!UICONTROL Opt-in] na página e como isso pode influenciar se as soluções do CX Enterprise podem ou não definir cookies, iniciar beacons, etc.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**OBSERVAÇÃO:** é importante observar que, no momento da redação deste artigo, o [!UICONTROL Opt-in] não foi integrado nas bibliotecas de todos os aplicativos do CX Enterprise. As bibliotecas atualmente com suporte para [!UICONTROL Opt-in] são:

* Serviço de ID de visitante
* Analytics
* Audience Manager
* Target

