---
description: Conecte o CMP (Consent Management Platform) ao plug-in do Audience Manager de aceitação para a TCF (Transparency and Consent Framework, Estrutura de transparência e consentimento) da IAB.
seo-description: Conecte o Consent Management Platform (CMP) com o plug-in Audience Manager para a TCF da IAB.
seo-title: Uso dos serviços de Opt-in com a Estrutura IAB
title: Uso dos serviços de Opt-in com a Estrutura IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 67%

---


# Uso dos serviços de Opt-in com a Estrutura IAB {#using-opt-in-services-with-iab-framework}

Conecte o CMP (Consent Management Platform) ao plug-in de Opt-in do Audience Manager para a TCF (Transparency and Consent Framework, Estrutura de transparência e consentimento) do IAB.

Os clientes do Audience Manager que usam o [TCF da IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) podem conectar o Consent Management Platform (CMP) ao plug-in do Audience Manager de aceitação para TCF da IAB. Opt-in é um recurso integrado à biblioteca JavaScript da ECID que pode desativar bibliotecas de soluções individuais da Adobe, dependendo das preferências do visitante definidas em uma CMP. Quando o plug-in do Gerenciador de Audiências para IAB TCF é implementado com a biblioteca ECID, as preferências de visitante do CMP que suporta IAB TCF são mapeadas automaticamente para Opt-in. Essas preferências habilitarão as bibliotecas do Audience Manager (DIL e ECID) e as chamadas associadas ao receber o consentimento.

## Implementar uma CMP compatível com IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para que a aceitação seja integrada ao TCF do IAB, é necessário concluir o seguinte:

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. Defina/carregue `__cmp` antes de carregar o Adobe JS.

Para obter mais detalhes, leia os [documentos do Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Ative o plug-in do Audience Manager para IAB na Biblioteca Javascript ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>O Opt-in está disponível somente na ECID 4.0+.

Use o Adobe Experience Platform Launch para implementar o plug-in do Opt-in e do Audience Manager para IAB TCF no site. Ao ativar o IAB para aceitação manual, verifique se as seguintes configurações estão definidas como true no objeto de Visitante:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Depois que as configurações forem definidas corretamente, as bibliotecas ECID e DIL serão ativadas/desativadas, dependendo dos critérios de consentimento do CMP e do IAB TCF.

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. Leia mais sobre o Plug-in do Audience Manager para TCF do IAB na documentação do Audience Manager [aqui](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

Para obter mais informações sobre como validar o plug-in do Opt-in e do Audience Manager para TCF do IAB, confira o caso de uso nº 4 no guia de validação [aqui](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentação relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Estrutura de transparência e consentimento (TCF) do IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Para obter mais informações sobre o padrão IAB
* [Opt-in da Adobe](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Para obter mais informações sobre Opt-in, um componente obrigatório do gerenciamento de consentimento nas soluções de plataforma
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.translate.html)
* [Suas opções de privacidade](https://www.adobe.com/br/privacy/opt-out.html#customeruse) - Outra opção de privacidade à disposição dos usuários é a capacidade de não aderir à coleta de dados usando outras ferramentas de opt-out global. A opção de não participação global tem prioridade sobre a verificação de aceitação e TCF da IAB

