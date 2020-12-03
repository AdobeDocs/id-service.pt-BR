---
description: Implemente o serviço de Opt-in como o único ponto de referência usado pelas soluções da Experience Cloud (referido como Categorias no Opt-in) para determinar se os cookies devem ser criados no dispositivo de um visitante.
seo-description: Implemente o serviço de Opt-in como o único ponto de referência usado pelas soluções da Experience Cloud (referido como Categorias no Opt-in) para determinar se os cookies devem ser criados no dispositivo de um visitante.
seo-title: Configuração do serviço de Opt-in
title: Configuração do serviço de Opt-in
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 88%

---


# Configuração do serviço de Opt-in{#setting-up-opt-in-service}

Implemente o serviço de Opt-in como o único ponto de referência usado pelas soluções da Experience Cloud (referido como Categorias no Opt-in) para determinar se os cookies devem ser criados no dispositivo de um visitante.

O serviço de Opt-in é uma biblioteca JavaScript fornecida com a Experience Cloud ID (ECID) e existe no Visitor JS no `adobe` objeto global como o `adobe.optIn` objeto. O serviço de Opt-in instalado permite especificar se um visitante pode aderir às soluções da Adobe de uma só vez ou apresentar as soluções em sequência para fornecer permissões para cada uma delas. O recurso de gerenciamento de consentimento do serviço de Opt-in permite implementar com várias configurações para suas necessidades de privacidade específicas.

O serviço de Opt-in permite especificar se um visitante pode aderir às soluções da Adobe de uma só vez ou apresentar as soluções em sequência para fornecer permissões para cada uma delas. Quando o processo de aprovação é concluído e registrado pelo cliente, as aprovações do visitante da CMP pode ser recuperadas por todas as soluções da Adobe, que respondem com as chamadas de consentimento relacionadas.

## Pré-requisitos {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versão 4.0.

   [Baixe](https://github.com/Adobe-Marketing-Cloud/id-service/releases) a versão mais recente do ECID.

1. Bibliotecas de suporte:

   * ECID 4.0 ou posterior
   * AppMeasurement 2.11 ou posterior
   * DIL 9.0
   * AT.js versão 1.7.0
   * AT.js Launch versão 9.0
   * Para o Analytics, App Measurement 2.11 com extensão 1.6
   * Para o Público alvo, extensão 0.9.1

1. Conheça bem a estrutura de gerenciamento de consentimento que você usará com a opção Aceitar e entenda quaisquer pré-requisitos adicionais.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Os requisitos de privacidade da sua empresa serão específicos quanto à maneira como você permanece em conformidade com o GDPR. Esteja ciente de quais bibliotecas suas equipes de privacidade de empresa estão em condições de usar em um estado de pré-consentimento.

If using [Adobe Launch](https://docs.adobe.com/content/help/pt-BR/launch/using/overview.html), take advantage of the [Opt-in extension](../../implementation-guides/opt-in-service/launch.md) to configure Opt-in service.

## Categorias de Opt-in {#section-9ab0492ab4414f0ca16dc08d3a905f47}

As preferências de Opt-in de um visitante são relativas a uma solução da Adobe Experience Cloud, sendo que cada solução é representada como uma categoria. As categorias são fornecidas pelo `adobe.OptInCategories` objeto, no qual, por exemplo, o componente ECID é referido como `adobe.OptInCategories`. `ECID`. Esta é a definição de `adobe.OptInCategories`:

As configurações de Opt-in são mantidas por categoria, sendo que cada solução da Experience Cloud é representada por uma categoria:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

O serviço de Opt-in permite definir as preferências de permissão dos visitantes para cada soluções da Adobe usada no site. Inclui uma biblioteca para salvar as configurações de um visitante por categoria aprovada e oferece suporte a um fluxo sequencial, no qual o processo de aprovação recebe as preferências “confirmar” ou “negar” para cada categoria, uma a uma. Você pode definir soluções/categorias para aderir como um todo ou como soluções individuais. 
Todas as bibliotecas do lado do cliente das soluções da Adobe dependem do serviço de Opt-in e não gerarão cookies se uma permissão não for concedida a elas. O Opt-in é compatível com várias abordagens para fornecer e atualizar as configurações de consentimento para o visitante atual. Essa seção fornece exemplos para definir as preferências do serviço de Opt-in. Consulte a [Referência da API de Opt-in](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) para obter uma lista completa de funções e parâmetros.

As configurações do serviço de Opt-in são fornecidas na `getInstance()` função do JS do visitante, que instancia o `adobe` objeto global. Abaixo encontram-se as [configurações](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) do JS do visitante para o serviço de Opt-in.

**Exemplo de configuração de Opt-in na inicialização do `Visitor` objeto global**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**Tratar alterações para consentimento**

A qualquer momento durante a experiência de um visitante no site, ele pode definir preferências pela primeira vez ou alterar suas preferências usando o CMP. Quando o JS do Visitante é inicializado com as configurações iniciais, as permissões do visitante podem ser alteradas. Consulte [Alterações no consentimento](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) para obter uma lista das funções de consentimento gerenciadas.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Fluxos de trabalho de Opt-in {#section-70cd243dec834c8ea096488640ae20a5}

O serviço de Opt-in é compatível com um fluxo de trabalho no qual as permissões podem ser coletadas por mais de um ciclo de solicitação e as preferências são fornecidas uma a uma. Usando as seguintes funções e fornecendo *true* para `shouldWaitForComplete`, a solução poderá coletar o consentimento para uma ou para um subconjunto do total de categorias e, em seguida, coletar o consentimento para a próxima categoria ou subconjunto de categorias. Começando na primeira chamada, a propriedade `adobe.optIn.status` estará *pendente* até que `adobe.optIn.complete()` seja chamado no fim do fluxo. Uma vez coletado, o status é definido para *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Consulte as [configurações do fluxo de trabalho](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Inspecionar as permissões de Opt-in do visitante {#section-f136a9024e054d84881e6667fb7c94eb}

Conforme os visitantes fazem alterações em suas permissões, será necessário obter informações sobre as permissões resultantes para sincronizar o armazenamento de consentimentos com as alterações feitas no serviço de Opt-in. Inspect suas preferências de visitante usando as funções [de](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)permissões, por exemplo:

**amostra fetchPermissions**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

See [API documentation](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) for more details on these and any functions, properties, or configurations mentioned in this document.

## Armazenando as preferências do visitante {#section-ef2884ae67e34879bf7c7c3372706c9f}

O serviço de Opt-in fornece uma opção para armazenar as preferências de consentimento adequadas a um ambiente de desenvolvimento ou a um ambiente em que não seja viável usar um CRM. Especificar a propriedade de configuração `isOptInStorageEnabled` como *true* aciona o serviço de Opt-in para criar um cookie no sistema do visitante no seu domínio.

O `adobe.optIn` objeto não tem estado e não fornece um mecanismo de armazenamento. Em vez disso, você precisa gerenciar as configurações de consentimento da Adobe na sua Plataforma de gerenciamento de consentimento (CMP) existente se ela permitir o armazenamento de dados personalizados. Ou você pode armazenar as preferências do visitante em um cookie em seu navegador. Existem duas opções para fornecer as preferências do usuário para o serviço de Opt-in:

* Se sua solução de persistência de consentimento, seja ela um CMP ou um cookie no navegador do visitante, permitir a recuperação oportuna das preferências do visitante, você poderá fornecê-las ao serviço de Opt-in durante a inicialização do Visitante.
* No entanto, se a recuperação demorar muito ou puder ser realizada melhor como um processo assíncrono, você pode usar a `approve()` função do serviço para fornecer as configurações depois de serem carregadas com sucesso.

