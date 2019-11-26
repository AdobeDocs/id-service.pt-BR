---
description: Conecte o CMP (Consent Management Platform) ao plug-in do Audience Manager de aceitação para a TCF (Transparency and Consent Framework, Estrutura de transparência e consentimento) da IAB.
seo-description: Conecte o Consent Management Platform (CMP) com o plug-in Audience Manager para a TCF da IAB.
seo-title: (beta) Uso dos serviços de Opt-in com a Estrutura IAB
title: (beta) Uso dos serviços de Opt-in com a Estrutura IAB
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: ht
source-git-commit: cb75ac6a9d7a5a001fcb0a1d9d978d3845a4e829

---


# (beta) Uso dos serviços de Opt-in com a Estrutura IAB {#beta-using-opt-in-services-with-iab-framework}

Conecte o Consent Management Platform (CMP) ao plug-in IAB de aceitação para o Audience Manager.

Os clientes do Audience Manager que usam o [TCF da IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) podem conectar o Consent Management Platform (CMP) ao plug-in do Audience Manager de aceitação para TCF da IAB. Opt-in é um recurso integrado à biblioteca JavaScript da ECID que pode desativar bibliotecas de soluções individuais da Adobe, dependendo das preferências do visitante definidas em uma CMP. Quando o plugin IAB é implementado com a biblioteca ECID, as preferências do visitante do CMP compatível com IAB são mapeadas automaticamente ao Opt-in. Essas preferências habilitarão as bibliotecas do Audience Manager (DIL e ECID) e as chamadas associadas ao receber o consentimento.

## Implementar uma CMP compatível com IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para integrar o Opt-In ao consentimento do IAB, é necessário fazer o seguinte:

1. Implemente uma CMP que seja compatível com IAB e seja [registrada como um fornecer de IAB](https://vendorlist.consensu.org/vendorlist.json) ou desenvolva uma CMP interna que implemente a especificação do IAB e seja registrada como uma CMP com IAB na Europa.
1. Defina/carregue `__cmp` antes de carregar o Adobe JS.

Para obter mais detalhes, leia os [documentos do Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md).

## Ativar o plugin IAB na sua biblioteca JavaScript da ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>O Opt-in está disponível somente na ECID 4.0+

Use a Adobe Experience Platform Launch para implementar a aceitação e o plugin IAB no seu site. Leia a [documentação da extensão de aceitação ECID](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/) para saber como configurar a extensão do Experience Platform Launch.

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
>O Audience Manager exige consentimento para as *finalidades 1,2 e 5, além do consentimento do fornecedor* para implantar cookies e iniciar ou honrar as sincronizações de ID. Leia mais sobre o plugin IAB na documentação do Audience Manager [aqui](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html).

Para obter mais informações sobre como validar o plugin de Opt-in e do IAB, confira o caso de uso 4 no guia de validação [aqui](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentação relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Estrutura de transparência e consentimento (TCF) do IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - Para obter mais informações sobre o padrão IAB
* [Opt-in da Adobe](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - Para obter mais informações sobre Opt-in, um componente obrigatório do gerenciamento de consentimento nas soluções de plataforma
* Suporte da Estrutura de transparência e consentimento (TCF) do IAB [no Audience Manager](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)
* [Suas opções de privacidade](https://www.adobe.com/br/privacy/opt-out.html#customeruse) - Outra opção de privacidade à disposição dos usuários é a capacidade de não aderir à coleta de dados usando outras ferramentas de opt-out global. O Opt-out global tem precedência sobre a verificação de Opt-in e IAB

