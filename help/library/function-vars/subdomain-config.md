---
description: Altere o nome de domínio padrão usado pelas chamadas do serviço de identidade da Experience Cloud para o nome do seu subdomínio com essas configurações.
keywords: Serviço de ID
title: audienceManagerServer e audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 222
ht-degree: 100%

---

# audienceManagerServer e audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Altere o nome de domínio padrão usado pelas chamadas do serviço de identidade da Experience Cloud para o nome do seu subdomínio com essas configurações.

**Sintaxe:**

* `audienceManagerServer: " *`o nome do seu subdomínio`*.demdex.net"`
* `audienceManagerServerSecure: " *`o nome do seu subdomínio`*.demdex.net"`

**Propósito**

Normalmente, o serviço da [!DNL Experience Cloud] ID faz chamadas para a [!DNL Adobe] em `dpm.demdex.net`. Às vezes, você pode não querer fazer chamadas para esse destino porque parece muito genérico ou de “terceiros”. Para que a chamada do serviço de ID pareça mais uma chamada primária, use essas configurações para adicionar o nome do seu [!DNL Audience Manager] subdomínio do ao `demdex.net` como mostrado abaixo. Para obter mais informações sobre a chamada`dpm.demdex.net`, consulte [Compreender as chamadas para o domínio Demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=pt-BR).

**Requisitos**

Essas configurações exigem:

* O nome do [!DNL Audience Manager] subdomínio do registrado da sua empresa. Verifique ou obtenha esse nome de seu consultor.
* O nome do subdomínio associado à [!UICONTROL Organization ID]
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

