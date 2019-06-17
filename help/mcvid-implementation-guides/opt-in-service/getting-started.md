---
description: Implemente o serviço de aceitação como o ponto de referência único usado pelas soluções da Experience Cloud (referido como Categorias na aceitação) para determinar se deseja criar cookies no dispositivo de um visitante.
seo-description: Implemente o serviço de aceitação como o ponto de referência único usado pelas soluções da Experience Cloud (referido como Categorias na aceitação) para determinar se deseja criar cookies no dispositivo de um visitante.
seo-title: Configuração do serviço de aceitação
title: Configuração do serviço de aceitação
uuid: f 1 c 27139-cef 2-4122-af 12-c 839 cfc 82 e 6 e
translation-type: tm+mt
source-git-commit: ae65e9c7da5ac9cbe22de3f956bcd7cbef2052a7

---


# Configuração do serviço de aceitação{#setting-up-opt-in-service}

Implemente o serviço de aceitação como o ponto de referência único usado pelas soluções da Experience Cloud (referido como Categorias na aceitação) para determinar se deseja criar cookies no dispositivo de um visitante.

O serviço de aceitação é uma biblioteca javascript com [a Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) e existe no Visitante JS no `adobe` objeto global como `adobe.optIn` objeto. O serviço de aceitação instalado permite especificar se um visitante pode aceitar as soluções da Adobe de uma vez ou para apresentar soluções em sequência para permissão para cada uma. O recurso de gerenciamento de consentimento do serviço de aceitação permite implementar com várias configurações para seus requisitos de privacidade específicos.

O serviço de aceitação permite especificar se um visitante pode aceitar as soluções da Adobe de uma vez ou para apresentar soluções em sequência para permissão para cada uma. Quando o processo de aprovação é concluído e registrado pelo cliente, as aprovações do visitante da CMP pode ser recuperadas por todas as soluções da Adobe, que respondem com as chamadas de consentimento relacionadas.

## Pré-requisitos {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID versão 4.0.

   [Baixe](https://github.com/Adobe-Marketing-Cloud/id-service/releases) a versão mais recente da ECID.

1. Bibliotecas compatíveis:

   * ECID 4.0 ou posterior
   * AppMeasurement 2.11 ou posterior
   * DIL 9.0
   * AT.js versão 1.7.0
   * Extensão AT.js do Launch versão 9.0
   * Para o Analytics, AppMeasurement 2.11 com extensão 1.6
   * Para o Target, a extensão 0.9.1

1. Familiarize-se bem com a estrutura de gerenciamento de consentimento que você usará com o Opt-in e entenda qualquer pré-requisito adicional.

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. Os requisitos de privacidade da sua empresa serão específicos quanto à maneira como você permanece em conformidade com o GDPR. Saiba quais bibliotecas as equipes de privacidade da sua empresa aceitam usar em um estado pré-consentimento.

Se estiver usando o [Adobe Launch](https://docs.adobelaunch.com/), aproveite a [Extensão de aceitação](../../mcvid-implementation-guides/opt-in-service/launch.md) para configurar o serviço de aceitação.

## Categorias de aceitação {#section-9ab0492ab4414f0ca16dc08d3a905f47}

As preferências de Opt-in de um visitante são relativas a uma solução da Adobe Experience Cloud, sendo que cada solução é representada como uma categoria. As categorias são fornecidas pelo objeto `adobe.OptInCategories`, no qual, por exemplo, o componente ECID é referido como `adobe.OptInCategories`. `ECID`. Esta é a definição de `adobe.OptInCategories`:

As configurações de Opt-in são mantidas por categoria, sendo que cada solução da Experience Cloud é representada por uma categoria:

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

O serviço de aceitação permite definir as preferências de permissão de visitantes por cada solução da Adobe usada em seu site. Inclui uma biblioteca para salvar as configurações de um visitante por categoria aprovada e oferece suporte a um fluxo sequencial, no qual o processo de aprovação recebe as preferências “confirmar” ou “negar” para cada categoria, uma a uma. Você pode definir soluções/categorias para aderir como um todo ou como soluções individuais.
Todas as bibliotecas do cliente da Adobe dependem do serviço de aceitação e não geram cookies a menos que a solução tenha permissão. O Opt-in é compatível com várias abordagens para fornecer e atualizar as configurações de consentimento para o visitante atual. Esta seção fornece exemplos para definir preferências de serviço de aceitação. Consulte a Referência da API [de aceitação](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) para obter uma lista completa de funções e parâmetros.

As configurações de serviço de aceitação são fornecidas na `getInstance()` função do Visitante JS que instancia o `adobe` objeto global. A seguir, as configurações de [configuração do Visitante JS](../../mcvid-implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) para o serviço de aceitação.

**Exemplo de configuração de aceitação na inicialização do`Visitor`objeto global**

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

**Lida com as alterações de consentimento**

A qualquer momento durante a experiência de um visitante no site, ele pode definir preferências pela primeira vez ou alterar suas preferências usando o CMP. Quando o JS do Visitante é inicializado com as configurações iniciais, as permissões do visitante podem ser alteradas. Consulte [Alterações no consentimento](../../mcvid-implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) para obter uma lista de funções de consentimento.

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## Fluxos de trabalho de aceitação {#section-70cd243dec834c8ea096488640ae20a5}

O serviço de aceitação oferece suporte para um fluxo de trabalho em que as permissões podem ser coletadas em mais de um ciclo de solicitação e as preferências são fornecidas uma de cada vez. Usando as seguintes funções e fornecendo *true* para `shouldWaitForComplete`, a solução poderá coletar o consentimento para uma ou para um subconjunto do total de categorias e, em seguida, coletar o consentimento para a próxima categoria ou subconjunto de categorias. A partir da primeira chamada, a `adobe.optIn.status` propriedade *será pendente* até `adobe.optIn.complete()` que seja chamada no final do fluxo. Uma vez coletado, o status é definido para *complete*.

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

Consulte [Configurações de configuração do fluxo de trabalho](../../mcvid-implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2).

## Inspecionar as permissões de Opt-in do visitante {#section-f136a9024e054d84881e6667fb7c94eb}

Conforme os seus visitantes fazem alterações nas permissões, você precisará de insight sobre as permissões resultantes para sincronizar a loja de consentimento com alterações feitas no serviço de aceitação. Inspecione as preferências do visitante usando as [funções de permissões](../../mcvid-implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155), por exemplo:

**Exemplo de fetchPermissions**

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

Consulte  [Documentação da API](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) para obter mais informações sobre essas e outras funções, propriedades ou configurações mencionadas neste documento.

## Armazenamento das preferências do visitante {#section-ef2884ae67e34879bf7c7c3372706c9f}

O serviço de aceitação fornece uma opção para armazenar preferências de consentimento apropriadas para um ambiente dev ou um ambiente em que não é possível usar um CRM. A especificação da propriedade de configuração `isOptInStorageEnabled` como *verdadeiro* aciona o serviço de aceitação para criar um cookie no sistema do visitante dentro do seu domínio.

O objeto `adobe.optIn` não tem estado e não fornece um mecanismo de armazenamento. Em vez disso, você precisa gerenciar as configurações de consentimento da Adobe na sua Plataforma de gerenciamento de consentimento (CMP) existente se ela permitir o armazenamento de dados personalizados. Ou você pode armazenar as preferências do visitante em um cookie em seu navegador. Você tem duas opções para fornecer as preferências do usuário para o serviço de aceitação:

* Se a solução de persistência de consentimento, seja ela um CMP ou um cookie no navegador do visitante, permite a recuperação oportuna das preferências do visitante, você pode fornecê-las ao serviço de aceitação durante a inicialização do visitante.
* No entanto, se a recuperação puder ser um processo longo ou for melhor fornecida como um processo assíncrono, você poderá usar `approve()` a função do serviço para fornecer essas configurações depois de carregadas com sucesso.

