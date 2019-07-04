---
description: Essa configuração permite limpar Experience Cloud IDs (ECIDs) órfãs ou desatualizadas com base na versão do Serviço de ID que está sendo atualizado.
keywords: Serviço de ID
seo-description: Essa configuração permite limpar Experience Cloud IDs (ECIDs) órfãs ou desatualizadas com base na versão do Serviço de ID que está sendo atualizado.
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# resetBeforeVersion{#resetbeforeversion}

Essa configuração permite limpar Experience Cloud IDs (ECIDs) órfãs ou desatualizadas com base na versão do Serviço de ID que está sendo atualizado.

Fornecer a versão do seu serviço de ID como o valor da variável `resetBeforeVersion` fará com que as ECIDs desatualizadas sejam apagadas das IDs do lado do cliente.

Algumas condições, como tempo limite de sessão, às vezes podem resultar na geração de uma ID do lado do cliente sem a obtenção bem-sucedida de uma ID do lado do servidor pelo Serviço de ID. Quando isso acontece, uma ID do lado do cliente órfã é rastreada pelo Serviço de ID sem poder ser rastreada entre os domínios ou sincronizada corretamente com as outras soluções. O comportamento compara a versão no cookie AMCV atual com o valor de `resetBeforeVersion`. Se o cookie não existir ou sua versão for anterior (mais antiga) à versão mais recente de `resetBeforeVersion`, o cookie AMCV será removido e o Serviço de ID solicitará uma nova ECID.

Para os visitante que possuem cookies Demdex de terceiros em seus navegadores, a ECID é verificada para ver ele foi gerado corretamente usando a UUID no cookies Demdex. Se a verificação for verdadeira, a nova ECID será a mesma e o visitante será considerado novo. Se por algum motivo a ECID que está sendo apagada não tiver sido gerada usando o cookie Demdex ou se não houver um cookie Demdex, o visitante receberá uma nova ECID e será considerado novo.

**Sintaxe:** `resetBeforeVersion = "3.3"`

**Amostra de código**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```

