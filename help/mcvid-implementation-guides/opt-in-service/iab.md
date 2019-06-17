---
description: Conecte sua Plataforma de Gerenciamento de Aprovação (CMP) com o plug-plugin IAB da aceitação.
seo-description: Conecte sua Plataforma de Gerenciamento de Aprovação (CMP) com o plug-plugin IAB da aceitação.
seo-title: (beta) Uso de serviços de aceitação com IAB Framework
title: (beta) Uso de serviços de aceitação com IAB Framework
uuid: 8 df 39 d 9 c-c 016-490 e-b 4 db-d 02 e 4044 b 480
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# (beta) Uso de serviços de aceitação com IAB Framework{#beta-using-opt-in-services-with-iab-framework}

Conecte sua Plataforma de Gerenciamento de Aprovação (CMP) com o plug-plugin IAB da aceitação.

Os clientes do Audience Manager que usam [IAB Transparency and Approval Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) podem conectar sua Plataforma de Gerenciamento de Aprovação (CMP) com o plug-plugin IAB da aceitação. A aceitação é um recurso incorporado na biblioteca do javascript ECID, que pode desativar bibliotecas de soluções individuais da Adobe, dependendo das preferências do visitante definidas em um CMP. Quando o plug-plugin IAB é implementado com a biblioteca ECID, as preferências do visitante do CMP compatível com IAB são mapeadas automaticamente para aceitar. Essas preferências habilitarão bibliotecas com base no Audience Manager (DIL e ECID) e chamadas associadas quando o consentimento for recebido.

## Implementar uma CMP compatível com IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para integrar o Opt-In ao consentimento do IAB, é necessário fazer o seguinte:

1. Implemente uma CMP que seja compatível com IAB e seja [registrada como um fornecer de IAB](https://vendorlist.consensu.org/vendorlist.json) ou desenvolva uma CMP interna que implemente a especificação do IAB e seja registrada como uma CMP com IAB na Europa.
1. Defina/carregue o `__cmp` antes de carregar o Adobe JS.

Para obter mais detalhes, leia os [documentos do Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Ativar o plugin IAB na sua biblioteca JavaScript da ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in só está disponível no ECID 4.0 +

Use o Adobe Launch para implementar o Opt-in e o plugin IAB no seu site. Leia a [documentação da extensão de Opt-in da ECID](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) para saber como configurar a extensão do Launch.

Ao ativar o IAB para Opt-in manualmente, verifique se as seguintes configurações estão definidas como verdadeiro no objeto Visitante:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

Depois de configurar corretamente, as bibliotecas da ECID e DIL serão ativadas/desativadas, dependendo dos critérios de consentimento da CMP e da estrutura do IAB.

>[!IMPORTANT]
>
>O Audience Manager exige consentimento para as *finalidades 1,2 e 5, além do consentimento do fornecedor* para implantar cookies e iniciar ou honrar as sincronizações de ID. Leia mais sobre o plug-plugin IAB na documentação do Audience Manager** [aqui](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)**.

Para obter mais informações sobre como validar o plugin de Opt-in e do IAB, confira o caso de uso 4 no guia de validação [**aqui** ](../../mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentação relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Estrutura de transparência e consentimento (TCF) do IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Para obter mais informações sobre o padrão IAB
* [Opt-in da Adobe](../../mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Para obter mais informações sobre Opt-in, um componente obrigatório do gerenciamento de consentimento nas soluções de plataforma
* Suporte da Estrutura de transparência e consentimento (TCF) do IAB [no Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Suas opções de privacidade](https://www.adobe.com/privacy/opt-out.html#customeruse) - Outra opção de privacidade à disposição dos usuários é a capacidade de não aderir à coleta de dados usando outras ferramentas de opt-out global. O Opt-out global tem precedência sobre a verificação de Opt-in e IAB

