---
description: Depois de ativar o Opt-in no site, use os métodos de validação para testar se o serviço funciona conforme o esperado usando as ferramentas de desenvolvedor do seu navegador.
title: Validação do serviço de Opt-in
exl-id: f0bcb32a-ccad-40a4-b031-2584e4136ace
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 94%

---

# Validação do serviço de Opt-in{#validating-opt-in-service}

Depois de ativar o Opt-in no site, use os métodos de validação para testar se o serviço funciona conforme o esperado usando as ferramentas de desenvolvedor do seu navegador.

## Caso de uso 1: Ativar o Opt-in {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Antes de carregar a página, limpe o cache e os cookies.

No Chrome, clique com o botão direito na página da web e selecione Inspecionar. Como na captura de tela acima, selecione a guia *Rede* para visualizar as solicitações feitas do navegador.

No exemplo acima, temos as seguintes tags JS da Adobe instaladas na página: ECID, AAM, Analytics e Target.

**Como comprovar que o Opt-in está funcionando conforme o esperado:**

Você não deve ver solicitações para servidores da Adobe:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>Você poderá ver uma chamada para `http://dpm.demdex.net/optOutStatus`, que é um ponto de extremidade SOMENTE LEITURA usado para recuperar o status de Opt-in do visitante. Esse endpoint não resultará na criação de cookies de terceiros e não coletará informações da página.

Você não deve ver cookies criados pelas tags Adobe: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

No Chrome, acesse a guia *Aplicativo*, expanda a seção *Cookies* em *Armazenamento* e selecione o nome de domínio do seu site:

![](assets/use_case_1_2.png)

## Caso de uso 2: Ativar o Opt-in e o armazenamento {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

A única diferença no caso de uso 2 é que você verá *um novo cookie* que conterá as permissões de aceitação fornecidas pelo visitante: **adobeujs-optin**

## Caso de uso 3: Ativar o Opt-in e pré-aprovar o Adobe Analytics {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Como o Adobe Analytics é aceito previamente, você verá solicitações na guia Rede para o servidor de rastreamento:

![](assets/use_case_3_1.png)

e você verá os cookies do Analytics na guia Aplicativo:

![](assets/use_case_3_2.png)

## Caso de uso 4: Ativar o Opt-in e o IAB {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Como visualizar seu consentimento atual do IAB na página:**

Abra as ferramentas do desenvolvedor e selecione a guia *Console*. Cole o seguinte trecho de código e pressione Enter:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Este é um exemplo de saída quando as finalidades 1, 2 e 5 são aprovadas e a ID do fornecedor do Audience Manager é aprovada:

* demdex.net/id: a presença dessa chamada comprova que a ECID solicitou uma ID do demdex.net
* demdex.net/event: a presença dessa chamada comprova que a chamada de coleção de dados do DIL está funcionando como esperado.
* demdex.net/dest5.html: a presença dessa chamada comprova que as Sincronizações de ID estão sendo acionadas.

![](assets/use_case_4_1.png)

Se um dos itens a seguir não for válido, você não verá solicitações para servidores da Adobe e nenhum cookie da Adobe:

* As finalidades 1, 2 OU 5 não são aprovadas.
* A ID do fornecedor do Audience Manager não foi aprovada.
