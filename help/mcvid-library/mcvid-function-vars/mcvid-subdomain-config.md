---
description: Altere o nome de domínio padrão usado pelas chamadas do serviço da Experience Cloud ID para o nome do seu subdomínio com essas configurações.
keywords: Serviço de ID
seo-description: Altere o nome de domínio padrão usado pelas chamadas do serviço da Experience Cloud ID para o nome do seu subdomínio com essas configurações.
seo-title: audienceManagerServer e audienceManagerServerSecure
title: audienceManagerServer e audienceManagerServerSecure
uuid: e 21 cacbf -5151-4 d 34-b 0 f 7-9 e 90275 f 4 c 7 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# audienceManagerServer e audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Altere o nome de domínio padrão usado pelas chamadas do serviço da Experience Cloud ID para o nome do seu subdomínio com essas configurações.

**Sintaxe:**

* ` audienceManagerServer: " *`o nome do seu subdomínio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`o nome do seu subdomínio`*.demdex.net"`

**Propósito**

Normalmente, o serviço [!DNL Experience Cloud] de ID faz chamadas para [!DNL Adobe]`dpm.demdex.net`. Às vezes, você pode não querer fazer chamadas para esse destino porque parece muito genérico ou de “terceiros”. Para que a chamada do serviço de ID pareça mais uma chamada primária, use essas configurações para adicionar o nome do seu subdomínio do [!DNL Audience Manager] ao `demdex.net` como mostrado abaixo. Para obter mais informações sobre a chamada de `dpm.demdex.net`, consulte [Entender chamadas para o domínio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Requisitos**

Essas configurações exigem que você use:

* O nome [!DNL Audience Manager] de subdomínio do registro para a sua empresa. Verifique ou obtenha esse nome de seu consultor.
* O nome do subdomínio associado ao seu [!DNL Organization ID].
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

