---
description: O Serviço de ID do visitante (ECID) é compatível com o algoritmo de hash SHA -256 que permite transmitir IDs do cliente ou endereços de email e enviar IDs com hash. Este é um método opcional Javascript para enviar identificadores com hash ao CX Enterprise. Você pode continuar a usar seus próprios métodos de hash antes de enviar IDs do cliente.
keywords: Serviço de ID de visitante
title: Suporte a hash SHA256 para setCustomerIDs
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
TQID: https://experienceleague.adobe.com/-JBVon-Qf2jtfd5f4UdWcHVyO7c887p1w-k3GnntUCA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 603
ht-degree: 55%

---

# Suporte a hash SHA256 para `setCustomerIDs` {#hashing-support}

O Serviço de ID do visitante (ECID) é compatível com o algoritmo de hash SHA -256 que permite transmitir IDs do cliente ou endereços de email e enviar IDs com hash. Este é um método opcional Javascript para enviar identificadores com hash ao CX Enterprise. Você pode continuar a usar seus próprios métodos de hash antes de enviar IDs do cliente.Há duas maneiras de implementar o suporte de hash com setCustomerIDs, conforme descrito nas seções abaixo:

* [Usar o método setCustomerIDs no ECID](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Adicionar uma ação nas tags](/help/reference/hashing-support.md#add-action-launch)

## Usar o método `setCustomerIDs` no ECID {#use-setcustomerids-method}

O primeiro método aproveita o uso do método [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`).

Antes do hash, a biblioteca ECID realiza normalização de dados nas customerIDs. Esse processo elimina os espaços em branco das customerIDs e converte todos os caracteres em minúsculas. Por exemplo, no caso de endereços de email: &quot;ecid@adobe.com&quot; torna-se &quot;ecid@adobe.com&quot;

Consulte abaixo um exemplo de código de como você define uma única ID do cliente (o endereço de email mencionado acima) com hash SHA -256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

Juntamente com a ECID, é possível associar outras IDs do cliente, status de autenticação e tipo de hash (SHA-256) com cada visitante. Se não fornecer nenhum tipo de hash, será considerado como nenhum hash.

O `setCustomerIDs` método aceita várias IDs do cliente para o mesmo visitante. Isso ajuda a identificar ou direcionar um usuário individual em diferentes dispositivos. Por exemplo, você pode fazer o upload dessas IDs como [atributos do cliente](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=pt-BR) para a CX Enterprise e acessar esses dados em diferentes soluções.

As IDs do cliente, os estados autenticados e o tipo de hash *não são* armazenados em um cookie a ser usado posteriormente. Em vez disso, as IDs do cliente, os estados autenticados e o tipo de hash devem ser armazenados em uma variável de instância, a ser recuperada usando [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), como mostrado abaixo:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

O uso do método `setCustomerIDs` resulta em uma chamada para o Serviço de ID de Visitante, para `dpm.demdex.net`, com a adição do parâmetro de consulta `d_cid_ic`, que contém a ID do cliente com hash. Uma chamada de amostra pode ter a aparência abaixo. Quebras de linha foram adicionadas para maior clareza.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

Consulte a tabela abaixo para obter uma descrição do parâmetro `d_cid_ic` e do estado de autenticação.

| Parâmetro | Descrição |
|------------|----------|
| `d_cid_ic` | Transmite o Código de integração, o identificador de usuário único (DPUUID) e uma ID de estado autenticada para o Serviço de ID do visitante. Separe o Código de Integração e a DPUUID com o caractere de controle não imprimível, <code>%01</code>: <br> Exemplo: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Estado de autenticação</b> <br> Essa é uma ID opcional no parâmetro d_cid_ic. Expressa como um inteiro, identifica os usuários de acordo com o status de autenticação como mostrado abaixo: <br> <ul><li>0 (Desconhecido ou nunca autenticado)</li><li>1 (Atualmente autenticado para esta instância/página/contexto de aplicativo)</li><li>2 (Logout realizado)</li></ul> <br> Exemplos: <br> <ul><li>Desconhecido: ...d_cid=123%01456%01<b>0</b></li><li>Autenticado: ...d_cid=123%01456%01<b>1</b></li><li>Logout: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Adicionar uma ação nas tags {#add-action-launch}

Tags na Coleção de dados da Adobe Experience Platform é a próxima geração de recursos de gerenciamento de tags da Adobe. Leia mais na [documentação de tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=pt-BR).

Para adicionar uma ação nas tags, leia a [documentação de regras](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html?lang=pt-BR) e veja a captura de tela abaixo:

![](/help/reference/assets/hashing-support.png)

<br> 

Depois de confirmar sua configuração, as tags vinculam os dados em um objeto, como abaixo:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Aqui está uma amostra de código:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

De modo semelhante ao método `setCustomerIDs` descrito na primeira seção, isso resulta em uma chamada com o Serviço de ID de Visitante, além do parâmetro de consulta `d_cid_ic`.

