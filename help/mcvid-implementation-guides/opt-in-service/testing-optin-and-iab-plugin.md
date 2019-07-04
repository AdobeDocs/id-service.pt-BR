---
description: Depois de ativar o Opt-in no site, use os métodos de validação para testar se o serviço funciona conforme o esperado usando as ferramentas de desenvolvedor do seu navegador.
seo-description: Depois de ativar o Opt-in no site, use os métodos de validação para testar se o serviço funciona conforme o esperado usando as ferramentas de desenvolvedor do seu navegador.
seo-title: Validação do serviço de Opt-in
title: Validação do serviço de Opt-in
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

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

No Chrome, clique com o botão direito na página da web e selecione Inspecionar. Como mostrado na captura de tela acima, selecione a guia *Rede* para ver as solicitações feitas do navegador.

No exemplo acima, temos as seguintes tags JS da Adobe instaladas na página: ECID, AAM, Analytics e Target.

**Como comprovar que o Opt-in está funcionando conforme o esperado:**

Você não deve ver nenhuma solicitação aos servidores da Adobe:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>Você poderá ver uma chamada para `http://dpm.demdex.net/optOutStatus`, que é um ponto de extremidade SOMENTE LEITURA usado para recuperar o status de Opt-in do visitante. Esse ponto de extremidade não resultará na criação de um cookie de terceiros e não coletará informações da página.

Você não deve ver cookies criados pelas tags da Adobe: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

No Chrome, acesse a guia *Aplicativos*, expanda a seção *Cookies* em *Armazenamento* e selecione o nome do domínio do seu site:

![](assets/use_case_1_2.png)

## Caso de uso 2: Ativar o Opt-in e o armazenamento {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

A única diferença no caso de uso 2 é que você verá *um novo cookie* contendo as permissões de Opt-in fornecidas pelo visitante: **adobeujs-optin**

## Caso de uso 3: Ativar o Opt-in e pré-aprovar o Adobe Analytics {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Como o Adobe Analytics tem Opt-in pré-aprovado, você verá solicitações ao servidor de rastreamento na guia Rede:

![](assets/use_case_3_1.png)

e verá cookies do Analytics na guia Aplicativo:

![](assets/use_case_3_2.png)

## Caso de uso 4: Ativar o Opt-in e o IAB {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Como visualizar o consentimento atual do IAB na página:**

Abra as ferramentas do desenvolvedor e selecione a guia *Console*. Cole o seguinte fragmento de código e pressione Enter:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Este é um exemplo de quando as finalidades 1, 2 e 5 e a ID do fornecedor do Audience Manager estão aprovadas:

* demdex.net/id: a presença dessa chamada comprova que a ECID solicitou uma ID do demdex.net
* demdex.net/event: a presença dessa chamada comprova que a chamada de coleta de dados DIL está funcionando conforme o esperado.
* demdex.net/dest5.html: a presença dessa chamada comprova que as Sincronizações de ID estão sendo disparadas.

![](assets/use_case_4_1.png)

Se um dos seguintes não for válido, você não verá solicitações para os servidores da Adobe, nem cookies da Adobe:

* Finalidades 1, 2 OU 5 não estão aprovadas.
* A ID do fornecedor do Audience Manager não está aprovada.