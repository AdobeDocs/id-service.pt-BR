---
description: Altere o nome de domínio padrão usado por chamadas para o Serviço de identidade da plataforma Experience Platform com o seu próprio nome de subdomínio nessas configurações.
keywords: Serviço de ID
seo-description: Altere o nome de domínio padrão usado por chamadas para o Serviço de identidade da plataforma Experience Platform com o seu próprio nome de subdomínio nessas configurações.
seo-title: audienceManagerServer e audienceManagerServerSecure
title: audienceManagerServer e audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# audienceManagerServer e audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Altere o nome de domínio padrão usado por chamadas para o Serviço de identidade da plataforma Experience Platform com o seu próprio nome de subdomínio nessas configurações.

**Sintaxe:**

* ` audienceManagerServer: " *`o nome do seu subdomínio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`o nome do seu subdomínio`*.demdex.net"`

**Propósito**

Normalmente, o serviço da [!DNL Experience Cloud] ID faz chamadas para a [!DNL Adobe] em `dpm.demdex.net`. Às vezes, você pode não querer fazer chamadas para esse destino porque parece muito genérico ou de “terceiros”. Para que a chamada do serviço de ID pareça mais uma chamada primária, use essas configurações para adicionar o nome do seu [!DNL Audience Manager] subdomínio do ao `demdex.net` como mostrado abaixo. Para obter mais informações sobre a chamada de `dpm.demdex.net`, consulte [Entender chamadas para o domínio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Requisitos**

Essas configurações exigem que você use:

* O nome do [!DNL Audience Manager] subdomínio do registrado da sua empresa. Verifique ou obtenha esse nome de seu consultor.
* O nome do subdomínio associado à [!DNL Organization ID]
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

