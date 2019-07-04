---
description: Essas instruções, ferramentas e procedimentos ajudam você a determinar se o serviço de ID está funcionando adequadamente. Os testes se aplicam ao serviço de ID em geral, bem como para combinações diferentes do serviço de ID e soluções da Experience Cloud.
keywords: Serviço de ID
seo-description: Essas instruções, ferramentas e procedimentos ajudam você a determinar se o serviço de ID está funcionando adequadamente. Os testes se aplicam ao serviço de ID em geral, bem como para combinações diferentes do serviço de ID e soluções da Experience Cloud.
seo-title: Teste e verifique o serviço da Experience Cloud ID
title: Teste e verifique o serviço da Experience Cloud ID
uuid: 442de9c3-c265-4412-89bd-aeaa286ddad6
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Teste e verifique o serviço da Experience Cloud ID{#test-and-verify-the-experience-cloud-id-service}

Essas instruções, ferramentas e procedimentos ajudam você a determinar se o serviço de ID está funcionando adequadamente. Os testes se aplicam ao serviço de ID em geral, bem como para combinações diferentes do serviço de ID e soluções da Experience Cloud.

## Antes de começar {#section-b1e76ad552ed4eb793b6e521a55127d4}

Informações importantes a saber antes de iniciar o teste e a verificação do serviço de ID.

**Ambientes do navegador**

Ao testar em uma sessão normal do navegador, limpe o cache do navegador antes de cada teste.

Como alternativa, você pode testar o serviço de ID em uma sessão de navegador anônima ou incógnita. Em uma sessão anônima, não é necessário apagar os cookies do navegador ou o cache antes de cada teste.

**Ferramentas**

O [Adobe Debugger](https://marketing.adobe.com/resources/help/pt_BR/sc/implement/debugger.html) e o [Charles HTTP proxy](https://www.charlesproxy.com/) podem ajudar a determinar se o serviço de ID foi configurado para funcionar corretamente com o Analytics. As informações nesta seção têm por base os resultados retornados pelo depurador da Adobe e o Charles. Entretanto, você pode usar qualquer ferramenta ou depurador adequado para suas necessidades.

## Teste com o Adobe Debugger {#section-861365abc24b498e925b3837ea81d469}

A integração de serviço é configurada adequadamente ao visualizar uma [!DNL Experience Cloud ID] (MID) na resposta do depurador da [!DNL Adobe]. Consulte [Cookies e o serviço da Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md) para obter mais informações sobre a MID.

Para verificar o status do serviço de ID com o [!DNL Adobe] [depurador](https://marketing.adobe.com/resources/help/pt_BR/sc/implement/debugger.html):

1. Apague os cookies do navegador ou abra uma sessão de navegação anônima.
1. Carregue a página de teste com o código do serviço de ID.
1. Abra o depurador da [!DNL Adobe].
1. Verifique se nos resultados há uma MID.

## Compreender os resultados do Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

A MID é armazenada em um par de valores chave que usa a sintaxe: `MID= *`Experience Cloud ID`*`. O depurador exibe essas informações, como mostrado abaixo.

**Sucesso**

O serviço de ID terá sido implementado adequadamente se você observar uma resposta semelhante a:

```
mid=20265673158980419722735089753036633573
```

Se você for um cliente do [!DNL Analytics], é possível visualizar uma ID do [!DNL Analytics] (AID) além da MID. O seguinte ocorre:

* Com alguns dos primeiros visitantes ou os mais antigos.
* Se você tem um período de carência.

**Falha**

Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html) se o depurador:

* Não retornar uma MID.
* Retornar uma mensagem de erro indicando que a ID do parceiro não foi fornecida.

## Teste com o Charles HTTP proxy {#section-d9e91f24984146b2b527fe059d7c9355}

Para verificar o status do serviço de ID com Charles:

1. Apague os cookies do navegador ou abra uma sessão de navegação anônima.
1. Inicie o Charles.
1. Carregue a página de teste com o código do serviço de ID.
1. Verifique as chamadas de solicitação e resposta, além dos dados descritos abaixo.

## Como entender os resultados do Charles {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Consulte esta seção para obter informações sobre o que e onde procurar, ao usar o Charles para monitorar chamadas HTTP.

**Solicitações de serviço de ID com sucesso no Charles**

O código do serviço de ID está funcionando adequadamente quando a função `Visitor.getInstance` efetua uma chamada de JavaScript para `dpm.demdex.net`. Uma solicitação bem sucedida inclui a [ID da organização](../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26). A ID da empresa é passada como um par de valores chave que utiliza a sintaxe: `d_orgid= *`ID da organização`*`. Procure o `dpm.demdex.net` e as chamadas de JavaScript na guia [!DNL Structure]. Procure a ID da organização na guia [!DNL Request].

![](assets/charles_request.png)

**Solicitações do serviço de ID com sucesso no Charles**

A conta foi provisionada corretamente para o serviço de ID quando a resposta dos [Servidores de coleta de dados](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) retornou uma MID. A MID é retornada em um par de valores chave que usa a sintaxe: `d_mid: *`Experience Cloud ID do visitante`*`. Procure a MID na guia [!DNL Response], como mostrado abaixo.

![](assets/charles_response_success.png)

**Falha de resposta do serviço de ID no Charles**

A conta não foi provisionada adequadamente se a MID estiver faltando na resposta do DCS. Uma resposta sem sucesso retorna um código de erro e a mensagem na guia [!DNL Response], como mostrado abaixo. Entre em contato com o atendimento ao cliente se você visualizar essa mensagem de erro na resposta do DCS.

![](assets/charles_response_unsuccessful.png)

Para obter mais informações sobre os códigos de erro, consulte [Códigos de erro, mensagens e exemplos de DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html).
