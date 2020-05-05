---
description: Uma visão geral da solicitação de ID e do processo de resposta. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes diversos da Experience Cloud com suas próprias IDs da organização.
keywords: ID Service
seo-description: Uma visão geral da solicitação de ID e do processo de resposta. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes diversos da Experience Cloud com suas próprias IDs da organização.
seo-title: Como o serviço de identidade da Experience Cloud solicita e define IDs
title: Como o serviço de identidade da Experience Cloud solicita e define IDs
uuid: ff7f5b7e-e959-4391-b75c-b7a36286e0ea
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Como o serviço de identidade da Experience Cloud solicita e define IDs{#how-the-experience-cloud-id-service-requests-and-sets-ids}

Uma visão geral da solicitação de ID e do processo de resposta. Esses exemplos cobrem a atribuição de ID em sites individuais, em sites diferentes e para sites gerenciados por clientes diversos da Experience Cloud com suas próprias IDs da organização.

>[!NOTE]
>
>Se não estiver familiarizado com a forma como o serviço de identidade da Experience Cloud cria a ID de visitante, consulte [Experience Cloud](../introduction/cookies.md).

**Dica:** Consulte também nosso vídeo do serviço de [ID sobre o rastreamento](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html)entre domínios.

## Solicitar uma Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

Os exemplos a seguir demonstram como o serviço de ID solicita e recebe a ID de visitante da Experience Cloud. Esses exemplos usam duas empresas fictícias, a Food Company e a Sports Company, para demonstrar os fluxos de dados das solicitações e respostas da ID. Cada empresa tem uma ID de empresa exclusiva da Experience Cloud e implementou o código do serviço de ID em todos os sites. Esses casos de uso representam fluxos de dados para uma implementação de serviço de ID genérica sem o Analytics, IDs herdadas ou navegadores que bloqueiam cookies de terceiros.

![](assets/sample_sites.png)

**Primeira solicitação**

Neste exemplo, um novo visitante chega ao site de pizza gerenciado pela Empresa Food. A Empresa Food tem o código do serviço de ID no site de pizza. Quando o site de pizza é carregado, o código do serviço de ID verifica o cookie AMCV no domínio do site de pizza.

* Se o cookie AMCV estiver definido, o visitante do site terá uma Experience Cloud ID. Nesse caso, o cookie rastreia o visitante e compartilha dados com outras soluções da Experience Cloud.
* If the AMCV cookie is not set, the ID service code calls a regional [data collection server](https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html) (DCS) at `dpm.demdex.net/id` (see also, [Understanding Calls to the Demdex Domain](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/reference/demdex-calls.html)). A chamada inclui a ID da organização da Food Company. A ID da organização está definida na função `Visitor.getInstance` do código do serviço de ID.

![](assets/request1.png)

**Primeira resposta**

Na resposta, o DCS retorna a [!DNL Experience Cloud] ID (MID) e o cookie demdex. O código do serviço de ID grava o valor MID no cookie AMCV. Por exemplo, digamos que o DCS retorne um valor MID de 1234. Ele estaria armazenado no cookie AMCV como `mid|1234` e definido no domínio principal do site de pizza. O cookie demdex também contém uma ID exclusiva (vamos chamá-la de 5678). Este cookie é definido no domínio demdex.net de terceiros, que é separado do domínio do site de pizza.

![](assets/response1.png)

Como você verá no próximo exemplo, a ID demdex e a ID da organização permitem que o serviço de ID crie e retorne a MID correta quando o visitante for para outro site pertencente à Empresa de alimentos.

## Respostas e solicitações entre sites {#section-15ea880453af467abd2874b8b4ed6ee9}

Neste exemplo, nosso visitante de Empresa de comida navega até o site de tacos do site de pizza. A Empresa Food tem código de serviço de ID no site de tacos. O visitante nunca esteve no site dos tacos.

Dadas estas condições, não há cookie AMCV no site de tacos. Além disso, o serviço de ID não pode usar o cookie AMCV definido no site de pizza porque ele é específico ao domínio de pizza. Como resultado, o serviço de ID deve chamar o DCS para verificar e solicitar uma ID de visitante. Nesse caso, a chamada DCS inclui a ID da organização da Empresa alimentar *e* a ID demdex. E lembre-se, a ID demdex é retirada do site de pizza e armazenada como um cookie de terceiros sob o domínio demdex.net.

![](assets/request2.png)

Depois que o DCS recebe a ID da organização e a ID demdex, ele cria e retorna a MID correta para o visitante do site. Como a é derivada matematicamente da ID da organização e da ID demdex, o cookie AMCV contém o valor da MID `mid = 1234`mid = .

![](assets/response2.png)

## Solicitações de ID de outros sites {#section-ba9a929e50d64b0aba080630fd83b6f1}

Neste exemplo, nosso visitante deixa os sites de Empresa de comida e navega até o site de futebol pertencente à Empresa de Esportes. Quando o visitante chega ao site de futebol, o processo de solicitação e verificação de ID funciona da mesma forma descrita nos exemplos anteriores. No entanto, como a Empresa de Esportes tem sua própria ID de empresa, o serviço de ID retorna uma MID diferente. A nova MID é exclusiva ao domínio controlado pela Sports Company e permite que a empresa rastreie e compartilhe os dados do visitante em todas as soluções da [!DNL Experience Cloud]. A ID demdex permanece a mesma para esse visitante porque ela está contida no cookie de terceiros e continua por diferentes domínios.

![](assets/req_resp.png)

