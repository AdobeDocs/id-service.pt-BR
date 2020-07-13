---
description: Conecte o CMP (Consent Management Platform) ao plug-in do Audience Manager de aceitação para a TCF (Transparency and Consent Framework, Estrutura de transparência e consentimento) da IAB.
seo-description: Conecte o Consent Management Platform (CMP) com o plug-in Audience Manager para a TCF da IAB.
seo-title: Uso dos serviços de Opt-in com a Estrutura IAB
title: Uso dos serviços de Opt-in com a Estrutura IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 100%

---


# Uso dos serviços de Opt-in com a Estrutura IAB {#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>O documento a seguir se aplica somente ao IAB 2.0. Os usuários precisam usar o Visitante.js versão 5.0 para trabalhar com o IAB 2.0.

Conecte a Plataforma de gestão de consentimento (CMP) com o plug-in da Estrutura de transparência e consentimento (TCF) do IAB de Opt-in..

Os clientes do Adobe Audience Manager que usam a [TCF do IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) podem conectar sua Plataforma de gerenciamento de consentimento (CMP) com o plug-in da TCF do IAB de Opt-in. Opt-in é um recurso integrado à biblioteca JavaScript da ECID que pode desativar bibliotecas de soluções individuais da Adobe, dependendo das preferências do visitante definidas em uma CMP. Quando o plug-in da TCF do IAB de Opt-in é implementado com a biblioteca ECID, as preferências do visitante da CMP compatíveis com a TCF do IAB são mapeadas automaticamente para Opt-in. Essas preferências habilitarão as bibliotecas do Audience Manager (DIL e ECID) e as chamadas associadas ao receber o consentimento.

## Implementar uma CMP compatível com IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para integrar o Opt-In ao IAB TCF, é necessário fazer o seguinte:

1. Implementar uma CMP que seja compatível com IAB e seja [registrada como um fornecer de IAB](https://vendorlist.consensu.org/vendorlist.json) ou desenvolver uma CMP interna que implemente a especificação do IAB TCF e seja registrada como uma CMP com IAB TCF.
1. Defina/carregue `__tcfapi` antes de carregar o Adobe JS.

Para obter mais detalhes, leia os [documentos do Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## Ativar o plugin da TCF do IAB na sua biblioteca JavaScript da ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>O Opt-in está disponível somente na ECID 4.0+.

Use o Adobe Experience Platform Launch para implementar o plug-in TCF do IAB de Opt-in no seu site. Ao ativar o IAB para Opt-in manual, verifique se as seguintes configurações estão definidas como true no objeto Visitante:

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Depois que as configurações forem definidas corretamente, as bibliotecas ECID e DIL serão ativadas/desativadas, dependendo dos critérios de consentimento do CMP e do IAB TCF.

>[!IMPORTANT]
>
>O Audience Manager exige consentimento para *Finalidade 1 e Finalidade 10 além do consentimento do fornecedor* para implantar cookies e iniciar ou honrar as sincronizações de ID. Leia mais sobre o plugin TCF do IAB de Opt-in na documentação do Audience Manager [aqui](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

Para obter mais informações sobre como validar o plugin da TCF do IAB de Opt-in, confira o caso de uso 4 no guia de validação [aqui](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentação relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Estrutura de transparência e consentimento (TCF) do IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Para obter mais informações sobre o padrão IAB
* [Opt-in da Adobe](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Para obter mais informações sobre Opt-in, um componente obrigatório do gerenciamento de consentimento nas soluções de plataforma
* Suporte da Estrutura de transparência e consentimento (TCF) do IAB [no Audience Manager](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.translate.html)
* [Suas opções de privacidade](https://www.adobe.com/br/privacy/opt-out.html#customeruse) - Outra opção de privacidade à disposição dos usuários é a capacidade de não aderir à coleta de dados usando outras ferramentas de opt-out global. O Opt-out global tem precedência sobre a verificação de Opt-in e IAB TCF