---
description: Altere o nome de domínio padrão usado pelas chamadas do serviço de identidade da Experience Cloud para o nome do seu subdomínio com essas configurações.
keywords: ID Service
seo-description: Altere o nome de domínio padrão usado pelas chamadas do serviço de identidade da Experience Cloud para o nome do seu subdomínio com essas configurações.
seo-title: audienceManagerServer e audienceManagerServerSecure
title: audienceManagerServer e audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# audienceManagerServer e audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Altere o nome de domínio padrão usado pelas chamadas do serviço de identidade da Experience Cloud para o nome do seu subdomínio com essas configurações.

**Sintaxe:**

* ` audienceManagerServer: " *`o nome do seu subdomínio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`o nome do seu subdomínio`*.demdex.net"`

**Propósito**

Normalmente, o serviço da [!DNL Experience Cloud] ID faz chamadas para a [!DNL Adobe] em `dpm.demdex.net`. Às vezes, você pode não querer fazer chamadas para esse destino porque parece muito genérico ou de “terceiros”. Para que a chamada do serviço de ID pareça mais uma chamada primária, use essas configurações para adicionar o nome do seu [!DNL Audience Manager] subdomínio do ao `demdex.net` como mostrado abaixo. For more information about the `dpm.demdex.net` call, see [Understanding Calls to the Demdex Domain](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/reference/demdex-calls.html).

**Requisitos**

Essas configurações exigem o uso de:

* O nome do [!DNL Audience Manager] subdomínio do registrado da sua empresa. Verifique ou obtenha esse nome de seu consultor.
* The subdomain name associated with your [!UICONTROL Organization ID].
* *Ambos* os parâmetros de configuração com o mesmo nome de subdomínio.

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

