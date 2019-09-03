---
description: Essa implementação permite que os clientes usem o serviço de ID em dispositivos que não podem aceitar ou trabalhar com nosso código JavaScript ou o SDK. Isso inclui dispositivos como consoles de jogos, smart TVs ou outros dispositivos que se conectam à Internet. Consulte esta seção para saber mais sobre a sintaxe, os exemplos de código e as definições.
keywords: Serviço de ID
seo-description: Essa implementação permite que os clientes usem o serviço de ID em dispositivos que não podem aceitar ou trabalhar com nosso código JavaScript ou o SDK. Isso inclui dispositivos como consoles de jogos, smart TVs ou outros dispositivos que se conectam à Internet. Consulte esta seção para saber mais sobre a sintaxe, os exemplos de código e as definições.
seo-title: Integração direta com o serviço de identidade da Experience Cloud
title: Integração direta com o serviço de identidade da Experience Cloud
uuid: de502f7e-cffd-4130-b3ca-7d6b9a9caae9
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Integração direta com o serviço de identidade da Experience Cloud {#direct-integration-with-the-experience-cloud-id-service}

Essa implementação permite que os clientes usem o serviço de ID em dispositivos que não podem aceitar ou trabalhar com nosso código JavaScript ou o SDK. Isso inclui dispositivos como consoles de jogos, smart TVs ou outros dispositivos que se conectam à Internet. Consulte esta seção para saber mais sobre a sintaxe, os exemplos de código e as definições.

## Sintaxe {#section-a4754afec5ad40b6be00d6f1011d68bb}

Os dispositivos que não podem usar VisitorAPI.js ou as bibliotecas de código do SDK podem fazer chamadas diretamente para os servidores de coleta de dados (DCS) usados pelo serviço de ID. Para fazer isso, é necessário chamar `dpm.demdex.net` e formatar a solicitação como mostrado abaixo. *Itálico* indica um marcador de posição variável.

![](assets/directSyntax.png)

Neste exemplo de sintaxe, o `d_` prefixo identifica os pares de valores chave na chamada como uma variável do sistema. Você pode passar alguns `d_` parâmetros para o serviço de ID, mas manter o foco nos pares de valores chave como mostrado no código acima. Para obter mais informações sobre outras variáveis, consulte [Atributos compatíveis para chamadas de API DCS ](https://marketing.adobe.com/resources/help/en_US/aam/dcs-keys.html).

O serviço de ID oferece suporte às chamadas HTTP e HTTPS. Use HTTPS para passar dados de uma página segura.

## Solicitação de exemplo {#section-26302b8851704888b6f8e6b2071bcdb0}

Sua solicitação pode ser semelhante ao exemplo mostrado abaixo. As variáveis longas foram reduzidas.

![](assets/directExample.png)

## Resposta de exemplo {#section-89bc103b3e9e4a8b98e74c32897b1200}

O serviço de ID retorna dados em um objeto JSON, como mostrado abaixo. Sua resposta pode ser diferente.

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## Parâmetros de solicitação e resposta definidos {#section-4a9912b545364dc4acad4f1ea5ec641d}

**Parâmetros da solicitação**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parâmetro </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p>Um domínio herdado controlado pela <span class="keyword">Adobe</span>. Consulte <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Compreender as chamadas para o domínio Demdex</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>A ID de visitante da Experience Cloud. Consulte <a href="../introduction/cookies.md" format="dita" scope="local"> Cookies e o serviço de identidade da Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>Sua ID da organização da Experience Cloud. Para obter ajuda e encontrar essa ID, consulte  <a href="../reference/requirements.md" format="dita" scope="local"> Requisitos do serviço de identidade da Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>Um parâmetro opcional que passa a ID do provedor de dados (DPID), a ID de usuário exclusiva (DPUUID) e uma <a href="../reference/authenticated-state.md" format="dita" scope="local"> ID de estado autenticada</a> para o serviço de ID. Como mostrado na amostra de código, separe a DPID e a DPUUID com o caractere de controle não imprimível, <span class="codeph">%01</span>. </p> <p> <b>DPID e DPUUID</b> </p> <p>No parâmetro <span class="codeph">d_cid</span>, atribua cada combinação de DPID e DPUUID relacionada ao mesmo parâmetro <span class="codeph">d_cid</span>. Isso permite que você retorne diversos conjuntos de IDs em uma única solicitação. Além disso, separe a DPID, a DPUUID e o sinalizador de autenticação opcional com o caractere de controle não imprimível, <span class="codeph">%01</span>. Nos exemplos abaixo, o provedor e as IDs do usuário são destacadas com texto em <b>negrito</b>. </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">Sintaxe: <span class="codeph">...d_cid=DPID%01DPUUID%01estado de autenticação...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">Exemplo: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
    </ul> <p> <b>Estado de autenticação</b> </p> <p>Essa é uma ID opcional no parâmetro <span class="codeph">d_cid</span>. Expressa como um inteiro, identifica os usuários de acordo com o status de autenticação como mostrado abaixo: </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph"> 0</span> (Desconhecido) </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph"> 1</span> (Autenticado) </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph"> 2</span> (Logout realizado) </li> 
    </ul> <p>Para especificar um estado de autenticação, você define esse sinalizador após a variável da ID de usuário (UUID). Separe a UUID e o sinalizador de autenticação com o caractere de controle não imprimível, <span class="codeph">%01</span>. Nos exemplos abaixo, as IDs de autenticação estão destacadas com texto em <b>negrito</b>. </p> <p>Sintaxe: <span class="codeph">...d_cid=DPID%01DPUUID%01estado de autenticação</span> </p> <p>Exemplos: </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">Desconhecido: <span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">Autenticado: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">Logout: <span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>O serviço de ID é um sistema de carga balanceada distribuído geograficamente. A ID identifica a região do data center que processa a chamada. Consulte <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external">IDs da região do DCS, locais e nomes de host</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(Opcional)</i> Um parâmetro de retorno de chamada que permite a você executar uma função do JavaScript no corpo da solicitação. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>Uma parte criptografada dos metadados do JavaScript. As restrições de tamanho limitam a bolha a 512 bytes ou menos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>Obrigatório. Isso define o número de versão da API. Deixe essa opção configurada como <span class="codeph">d_ver=2</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Parâmetros de resposta**

Alguns parâmetros de resposta fazem parte da solicitação e foram definidos na seção acima.

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parâmetro </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>O intervalo da nova sincronização, especificado em segundos. O intervalo padrão é de 604.800 segundos (7 dias). </p> </td> 
  </tr> 
 </tbody> 
</table>

