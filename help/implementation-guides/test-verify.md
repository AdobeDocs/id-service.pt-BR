---
description: Essas instruções, ferramentas e procedimentos ajudam você a determinar se o Serviço de ID de visitante está funcionando corretamente. Esses testes se aplicam ao Serviço de ID do visitante em geral, bem como para combinações diferentes do Serviço de ID do visitante e soluções da CX Enterprise.
keywords: Serviço de ID de visitante
title: Teste e verifique o serviço de ID de visitante da Adobe
exl-id: afdf9778-e73d-46ca-9d2f-a65abaae2fe6
TQID: https://experienceleague.adobe.com/LPXZ0ydoky48kzyRnMK0kHsfoQyK3mi5IeXM0vtQV0s
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 713
ht-degree: 46%

---

# Teste e verifique o serviço de ID de visitante da Adobe{#test-and-verify-the-experience-cloud-id-service}

Essas instruções, ferramentas e procedimentos ajudam você a determinar se o Serviço de ID de visitante está funcionando corretamente. Esses testes se aplicam ao Serviço de ID do visitante em geral, bem como para combinações diferentes do Serviço de ID do visitante e soluções da CX Enterprise.

## Antes de começar {#section-b1e76ad552ed4eb793b6e521a55127d4}

Informações importantes a saber antes de começar a testar e verificar o Serviço de ID do visitante.

**Ambientes do navegador**

Ao testar em uma sessão normal do navegador, limpe o cache do navegador antes de cada teste.

Como alternativa, você pode testar o Serviço de ID do visitante em uma sessão anônima ou incógnita do navegador. Em uma sessão anônima, não é necessário limpar os cookies ou o cache do navegador antes de cada teste.

**Ferramentas**

O [Adobe Debugger](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=pt-BR) e o [proxy HTTP Charles](https://www.charlesproxy.com/) podem ajudar você a determinar se o Serviço de ID do visitante foi configurado corretamente para funcionar com o Analytics. As informações nesta seção baseiam-se nos resultados retornados pelo Adobe Debugger e Charles. Entretanto, você pode usar qualquer ferramenta ou depurador adequado para suas necessidades.

## Teste com o Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

A integração de serviço é configurada adequadamente ao visualizar uma ECID na resposta do Adobe Debugger. Consulte [Cookies e o Serviço de ID de visitante](../introduction/cookies.md) para obter mais informações sobre a MID.

Para verificar o status do Serviço de ID de visitante com o [depurador](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=pt-BR) da Adobe:

1. Limpe os cookies do navegador ou abra uma sessão de navegação anônima.
1. Carregue a página de teste que contém o código do Serviço de ID de visitante.
1. Abra o Adobe Debugger.
1. Verifique se nos resultados há uma MID.

## Compreender os resultados do Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

A MID é armazenada em um par de valores chave que usa a sintaxe: `MID= *`ECID`*`. O depurador exibe essas informações, como mostrado abaixo.

**Sucesso**

O Serviço de ID de visitante foi implementado corretamente se você visualizar uma resposta semelhante a esta:

```
mid=20265673158980419722735089753036633573
```

Se você for um cliente do Analytics, é possível visualizar uma ID do Analytics (AID) além da MID. Isso acontece:

* Com alguns de seus visitantes do site precoces ou de longa data.
* Se você tiver um período de carência habilitado.

**Falha**

Entre em contato com o [atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) se o depurador:

* Não retornar uma MID.
* Retornar uma mensagem de erro indicando que a ID do parceiro não foi fornecida.

## Teste com o Charles HTTP proxy {#section-d9e91f24984146b2b527fe059d7c9355}

Para verificar o status do serviço de ID de visitante com o Charles:

1. Limpe os cookies do navegador ou abra uma sessão de navegação anônima.
1. Iniciar o Charles.
1. Carregue a página de teste que contém o código do Serviço de ID de visitante.
1. Verifique as chamadas de solicitação e resposta e os dados descritos abaixo.

## Como entender os resultados do Charles {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Consulte esta seção para obter informações sobre o que e onde procurar, ao usar o Charles para monitorar chamadas HTTP.

**Solicitações do Serviço de ID de visitante com êxito no Charles**

O código do Serviço de ID de visitante está funcionando adequadamente quando a função `Visitor.getInstance` faz uma chamada JavaScript para `dpm.demdex.net`. Uma solicitação bem-sucedida inclui sua [ID da Organização IMS](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). A ID da Organização IMS é passada como um par de valores chave que usa a sintaxe: `d_orgid= *`ID da Organização IMS`*`. Procure o `dpm.demdex.net` e as chamadas de JavaScript na guia [!UICONTROL Structure]. Procure a ID da organização IMS na guia [!UICONTROL Request].

![](assets/charles_request.png)

**Respostas do Serviço de ID de Visitante com êxito no Charles**

Sua conta foi provisionada corretamente para o Serviço de ID de Visitante quando a resposta dos [Servidores de Coleta de Dados](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-data-collection.html?lang=pt-BR) (DCS) retornou uma MID. A MID é retornada em um par de valores chave que usa a sintaxe: `d_mid: *`ECID de visitante`*`. Procure a MID na guia [!UICONTROL Response], como mostrado abaixo.

![](assets/charles_response_success.png)

**Falha de resposta do Serviço de ID do visitante no Charles**

A conta não foi provisionada adequadamente se a MID estiver faltando na resposta do DCS. Uma resposta sem sucesso retorna um código de erro e a mensagem na guia [!UICONTROL Response], como mostrado abaixo. Entre em contato com o atendimento ao cliente se você visualizar essa mensagem de erro na resposta do DCS.

![](assets/charles_response_unsuccessful.png)

Para obter mais informações sobre os códigos de erro, consulte [Códigos de erro, mensagens e exemplos de DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html?lang=pt-BR).

