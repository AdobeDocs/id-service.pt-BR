---
description: Referência de ajustes da API da biblioteca de Opt-in e das configurações.
title: Referência de opt-in
exl-id: aa61aed7-695b-47e4-a922-9841e00aa09d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 99%

---

# Referência de opt-in{#opt-in-reference}

Referência de ajustes da API da biblioteca de Opt-in e das configurações.

As configurações de consentimento são fornecidas para as funções de Opt-in como categorias:

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## Parâmetros de configuração de opt-in {#section-d66018342baf401389f248bb381becbf}

Essa seção discute o uso da API para configurar o Opt-in. A maior parte da configuração e implementação pode ser feita usando a extensão da Experience Platform Launch.

As configurações de Opt-in são fornecidas na função `getInstance()` do JavaScript do visitante, que instancia o objeto global `adobe`. Abaixo encontram-se as configurações do JS do Visitante relacionadas ao serviço de Opt-in.

**`doesOptInApply (boolean or function that evaluates to a boolean)`**

Se falso, indica que os visitantes não precisam aceitar. Resulta na criação de cookies pela Experience Cloud, independentemente das categorias aderidas ou não. Essa configuração habilita ou desabilita a aceitação de forma holística.

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

Defina quais categorias são aprovadas ou negadas quando nenhuma preferência tiver sido definida ainda pelo visitante, referidas como padrões da organização.

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

As preferências definidas explicitamente pelo visitante. As permissões dessa configuração substituem os padrões da organização (`previousPermissions` substitui `preOptInApprovals`).

**`isOptInStorageEnabled (boolean)`**

Permita que o Opt-in armazene as permissões em um cookie próprio (no domínio do cliente atual)

(Opcional) **`optInCookiesDomain (string)`**

Domínio ou subdomínio próprio usado para o cookie Opt-in (se `isOptInStorageEnabled` for verdadeiro)

(Opcional) **`optInStorageExpiry (integer)`**

Número de segundos para substituir a expiração padrão de 13 meses

## Alterações nos parâmetros de Consentimento {#section-c3d85403ff0d4394bd775c39f3d001fc}

A qualquer momento durante sua experiência no site, um visitante pode definir preferências pela primeira vez ou alterar suas preferências usando o CMP. Quando o JS do Visitante é inicializado com as configurações iniciais, as permissões do visitante podem ser alteradas usando estas funções:

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Função que aprova ou faz opt-in do visitante a todas as categorias de uma lista. Para obter mais informações sobre o parâmetro shouldWaitForComplete, consulte [Fluxo de trabalho de aceitação](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5).

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

Função que nega ou faz opt-out do visitante de todas as categoria especificadas.

**`adobe.optIn.approveAll()`**

Se a solicitação de permissão para o seu site criar cookies for formulada de modo a um blanket de visitante concedê-la ou negá-la, use `approveAll()` ou `denyAll()` de acordo com a resposta deles.

**`adobe.optIn.denyAll()`**

Se a solicitação de permissão para o seu site criar cookies for formulada de modo a um blanket de visitante concedê-la ou negá-la, use `approveAll()` ou `denyAll()` de acordo com a resposta.

## Parâmetros de fluxos de trabalho de Opt-in {#section-2c5adfa5459c4e72b96d2693123a53c2}

O objeto Opt-in é compatível com um fluxo de trabalho no qual as permissões podem ser coletadas por mais de um ciclo de solicitação, como quando as preferências são fornecidas uma a uma. Usando as seguintes funções e fornecendo *true* para a configuração `shouldWaitForComplete`, a solução poderá coletar o consentimento para uma solução ou para um subconjunto do total de categorias e, em seguida, coletar o consentimento para a próxima categoria ou subconjunto de categorias. Começando na primeira chamada, a propriedade `adobe.optIn.status` estará pendente até que `adobe.optIn.complete()` seja chamado no fim do fluxo. Uma vez coletado, o status é definido para *Complete*.

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

Função que aprova ou faz opt-in do visitante a todas as categorias de uma lista.

`adobe.optIn.deny(categories, shouldWaitForComplete)`

Função que nega ou faz opt-out do visitante de todas as categoria especificadas.

`adobe.optIn.complete()`

Função que dispara a agregação das chamadas procedentes para approve() e deny() em uma única solicitação para definir as preferências de um visitante. Ao se inscrever nas alterações de Opt-in (consulte `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`) abaixo, o retorno de chamada será disparado somente quando essa função for chamada.

## Parâmetros de permissões de Opt-in do visitante {#section-7fe57279b5b44b4f8fe47e336df60155}

Colete as permissões de Opt-in para um visitante a qualquer momento usando uma das funções de permissões:

`adobe.optIn.permissions`

Um objeto que lista todas as soluções da Experience Cloud, como categorias, que foram concedidas ou negadas pelo visitante.

`adobe.optIn.isApproved(categories)`

Se todas as categorias tiverem sido aprovadas, essa função retornará verdadeiro.

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

Recupera a lista de permissões de maneira assíncrona. A chamada de retorno é recebida com a lista de permissões após a conclusão do processo de concessão/negação de permissões. Fornecer um valor de *true* para `shouldAutoSubscribe` registra a chamada de retorno para qualquer alteração de Opt-in no futuro. Estas são as propriedades de `adobe.OptIn`:

**`permissions`**

Um objeto que lista todas as soluções da Experience Cloud, como categorias, que foram concedidas ou negadas pelo visitante. Exemplo: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* pendente
* alterado
* conclúido

**`doesOptInApply`**

Verdadeiro ou falso, representando a configuração fornecida na inicialização

**`isPending`**

Verdadeiro ou falso, dependendo do valor de status. A aceitação relata essa propriedade como verdadeira para um visitante que ainda não aceitou ou negou a permissão

**`isComplete`**

Verdadeiro ou falso, dependendo do valor de status. A aceitação pode relatar falso para essa propriedade quando um consentimento do estilo de fluxo de trabalho foi iniciado, mas não concluído.

## Métodos do objeto Opt-in {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: uma ou mais categorias para aprovar. Por exemplo: `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**: (opcional) parâmetro booleano, falso por padrão. Se você passar verdadeiro, o Opt-in não concluirá o processo de aprovação até que `adobe.optIn.complete()` seja chamado. Esse processo é semelhante a um fluxo de trabalho.

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* Analise 1 ou mais categorias para verificar se estão aprovadas.
* Se nenhuma categoria for aprovada, TODAS as categorias disponíveis serão verificadas.

**`isApproved(categories)`**

Verifique se uma ou mais categorias foram aprovadas pelo cliente.

**`isPreApproved(categories)`**

Verifique se uma ou mais categorias foram aprovadas pelo cliente. (Se foram transmitidos na `preOptInApprovals` configuração).

**`fetchPermissions(callback, shouldAutoSubscribe)`**

A API assíncrona recupera a lista de permissões. A chamada de retorno é recebida com a lista de permissões após a conclusão do processo de concessão/negação de permissões. **`shouldAutoSubscribe`:** um utilitário assistente inscreverá automaticamente essa chamada de retorno a todos os eventos futuros. Isso significa que a chamada de retorno será recebido sempre que uma aprovação ou negação for disparada no Opt-in. Dessa forma, você está sempre atualizado sem se inscrever nos eventos.

**Exemplo**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>Use somente se tiver passado o `shouldWaitForComplete` parâmetro para aprovar ou negar. Essa API conclui o processo de aprovação. Exemplo: `adobe.optIn.complete()`.

**`approveAll()`:**

Aprova todas as Categorias existentes.

**`denyAll()`**

Negue todas as Categorias existentes.

## Eventos do objeto Opt-in {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

Conclui os disparos de eventos quando o processo de aprovação for concluído. Se você chamar aprovar/negar sem passar `shouldWaitForComplete` ou `approveAll`/ `denyAll`, esse evento será disparado. Ou, se você passar `shouldWaitForComplete`, esse evento será disparado quando `complete` for chamado.

**Exemplo**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
