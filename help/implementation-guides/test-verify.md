---
description: Essas instruções, ferramentas e procedimentos ajudam você a determinar se o serviço de ID está funcionando adequadamente. Os testes se aplicam ao serviço de ID em geral, bem como para combinações diferentes do serviço de ID e soluções da Experience Cloud.
keywords: Serviço de ID
title: Testar e verificar o serviço de identidade da Experience Cloud
exl-id: afdf9778-e73d-46ca-9d2f-a65abaae2fe6
TQID: https://experienceleague.adobe.com/LPXZ0ydoky48kzyRnMK0kHsfoQyK3mi5IeXM0vtQV0s
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 689
ht-degree: 100%

---

# Testar e verificar o serviço de identidade da Experience Cloud{#test-and-verify-the-experience-cloud-id-service}

Essas instruções, ferramentas e procedimentos ajudam você a determinar se o serviço de ID está funcionando adequadamente. Os testes se aplicam ao serviço de ID em geral, bem como para combinações diferentes do serviço de ID e soluções da Experience Cloud.

## Antes de começar {#section-b1e76ad552ed4eb793b6e521a55127d4}

Informações importantes a saber antes de iniciar o teste e a verificação do serviço de ID.

**Ambientes do navegador**

Ao testar em uma sessão normal do navegador, limpe o cache do navegador antes de cada teste.

Como alternativa, você pode testar o serviço de ID em uma sessão anônima ou incógnita do navegador. Em uma sessão anônima, não é necessário limpar os cookies ou o cache do navegador antes de cada teste.

**Ferramentas**

O [depurador da Adobe](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=pt-BR) e o [proxy HTTP Charles](https://www.charlesproxy.com/) podem ajudar você a determinar se o serviço de ID foi configurado adequadamente para funcionar com o Analytics. As informações nesta seção baseiam-se nos resultados retornados pelo Adobe Debugger e Charles. Entretanto, você pode usar qualquer ferramenta ou depurador adequado para suas necessidades.

## Teste com o Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

A integração de serviço é configurada adequadamente ao visualizar uma [!DNL Experience Cloud ID] (MID) na resposta do depurador da [!DNL Adobe]. Consulte [Cookies e o serviço de identidade da Experience Cloud](../introduction/cookies.md) para obter mais informações sobre a MID.

Para verificar o status do serviço de ID com o [depurador](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=pt-BR) da [!DNL Adobe]:

1. Limpe os cookies do navegador ou abra uma sessão de navegação anônima.
1. Carregue a página de teste que contém o código do serviço de ID.
1. Abra o depurador da [!DNL Adobe].
1. Verifique se nos resultados há uma MID.

## Compreender os resultados do Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

A MID é armazenada em um par de valores chave que usa a sintaxe: `MID= *`Experience Cloud ID`*`. O depurador exibe essas informações, como mostrado abaixo.

**Sucesso**

O serviço de ID foi implementado corretamente se você visualizar uma resposta semelhante a esta:

```
mid=20265673158980419722735089753036633573
```

Se você for um cliente do [!DNL Analytics], é possível visualizar uma ID do [!DNL Analytics] (AID) além da MID. Isso acontece:

* Com alguns de seus visitantes do site precoces ou de longa data.
* Se você tiver um período de carência habilitado.

**Falha**

Entre em contato com o [atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) se o depurador:

* Não retornar uma MID.
* Retornar uma mensagem de erro indicando que a ID do parceiro não foi fornecida.

## Teste com o Charles HTTP proxy {#section-d9e91f24984146b2b527fe059d7c9355}

Para verificar o status do serviço de ID com o Charles:

1. Limpe os cookies do navegador ou abra uma sessão de navegação anônima.
1. Iniciar o Charles.
1. Carregue a página de teste que contém o código do serviço de ID.
1. Verifique as chamadas de solicitação e resposta e os dados descritos abaixo.

## Como entender os resultados do Charles {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Consulte esta seção para obter informações sobre o que e onde procurar, ao usar o Charles para monitorar chamadas HTTP.

**Solicitações de serviço de ID com sucesso no Charles**

O código do serviço de ID está funcionando adequadamente quando a função `Visitor.getInstance` efetua uma chamada de JavaScript para `dpm.demdex.net`. Uma solicitação bem sucedida inclui a [ID da organização](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). A ID da empresa é passada como um par de valores chave que utiliza a sintaxe: `d_orgid= *`ID da organização`*`. Procure o `dpm.demdex.net` e as chamadas de JavaScript na guia [!UICONTROL Structure]. Procure a ID da organização na guia [!UICONTROL Request].

![](assets/charles_request.png)

**Solicitações do serviço de ID com sucesso no Charles**

Sua conta recebe corretamente o serviço de ID quando a resposta dos [Servidores de coleta de dados](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-data-collection.html?lang=pt-BR) (DCS) retornar uma MID. A MID é retornada em um par de valores chave que usa a sintaxe: `d_mid: *`Experience Cloud ID do visitante`*`. Procure a MID na guia [!UICONTROL Response], como mostrado abaixo.

![](assets/charles_response_success.png)

**Falha de resposta do serviço de ID no Charles**

A conta não foi provisionada adequadamente se a MID estiver faltando na resposta do DCS. Uma resposta sem sucesso retorna um código de erro e a mensagem na guia [!UICONTROL Response], como mostrado abaixo. Entre em contato com o atendimento ao cliente se você visualizar essa mensagem de erro na resposta do DCS.

![](assets/charles_response_unsuccessful.png)

Para obter mais informações sobre os códigos de erro, consulte [Códigos de erro, mensagens e exemplos de DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html?lang=pt-BR).

