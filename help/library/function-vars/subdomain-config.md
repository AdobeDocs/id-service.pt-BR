---
description: Altere o nome de domínio padrão usado por chamadas para o serviço da Experience Cloud ID com o seu próprio nome de subdomínio nessas configurações.
keywords: Serviço de ID
seo-description: Altere o nome de domínio padrão usado por chamadas para o serviço da Experience Cloud ID com o seu próprio nome de subdomínio nessas configurações.
seo-title: audienceManagerServer e audienceManagerServerSecure
title: audienceManagerServer e audienceManagerServerSecure
uuid: e 21 cacbf -5151-4 d 34-b 0 f 7-9 e 90275 f 4 c 7 c
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# audienceManagerServer e audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Altere o nome de domínio padrão usado por chamadas para o serviço da Experience Cloud ID com o seu próprio nome de subdomínio nessas configurações.

**Sintaxe:**

* ` audienceManagerServer: " *`o nome do seu subdomínio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`o nome do seu subdomínio`*.demdex.net"`

**Propósito**

Normally, the [!DNL Experience Cloud] ID service makes calls to [!DNL Adobe] at `dpm.demdex.net`. Às vezes, você pode não querer fazer chamadas para esse destino porque parece muito genérico ou de “terceiros”. Para que a chamada do serviço de ID pareça mais uma chamada primária, use essas configurações para adicionar o nome do seu subdomínio do [!DNL Audience Manager] ao `demdex.net` como mostrado abaixo. Para obter mais informações sobre a chamada de `dpm.demdex.net`, consulte [Entender chamadas para o domínio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Requisitos**

Essas configurações exigem que você use:

* The [!DNL Audience Manager] subdomain name of record for your company. Verifique ou obtenha esse nome de seu consultor.
* The subdomain name associated with your [!DNL Organization ID].
* *Ambos* os parâmetros de configuração com o mesmo nome do subdomínio.

**Amostra de código**

Nesse exemplo, considere que há uma empresa de entretenimento de mídia preocupada juridicamente em fazer chamadas para `dpm.demdex.net`. No [!DNL Audience Manager], o nome registrado do subdomínio da empresa é Music1. A amostra de código a seguir demonstra como criar uma chamada de dados do serviço de ID com o nome de subdomínio específico do cliente.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

