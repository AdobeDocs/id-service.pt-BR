---
description: Uma configuração booleana opcional que determina se o serviço de ID envia (ou não) dados ao Adobe Experience Cloud Device Co-op.
keywords: ID Service
seo-description: Uma configuração booleana opcional que determina se o serviço de ID envia (ou não) dados ao Adobe Experience Cloud Device Co-op.
seo-title: isCoopSafe
title: isCoopSafe
uuid: 4dfa1f35-0a88-48d1-9484-d88cb53ad461
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# isCoopSafe{#iscoopsafe}

Uma configuração booleana opcional que determina se o serviço de ID envia (ou não) dados ao Adobe Experience Cloud Device Co-op.

Conteúdo:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Requisitos </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Casos de uso </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Sintaxe e amostra de código </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> Parâmetros POST da chamada de evento </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> APIs pós-instanciamento </a> </li> 
</ul>

## Exigências {#section-4883eda6beb8437182bcc82bb58fae41}

Para usar o `isCoopSafe` é necessário:

* Usar o código do serviço de ID versão 2.4 ou posterior.
* Participe do Device Co-op da [Experience Cloud](https://docs.adobe.com/content/help/en/device-co-op/using/about/overview.html). Os membros em potencial também devem consultar essa documentação para determinar se `isCoopSafe` responde possíveis dúvidas sobre como os dados são usados para criar o gráfico do dispositivo.

* Trabalhe com seu consultor da [!DNL Adobe] para definir um sinalizador de lista de permissões ou lista de bloqueios na conta do Device Co-op. Não há um caminho de autoatendimento para habilitar esses sinalizadores.

## Casos de uso {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` ajuda a resolver dois casos de uso relacionados à coleta de dados pelos membros atuais ou em potencial do Device Co-op. Esses casos de uso estão relacionados à forma como os dados do visitante do site são passados para o Device co-op para ajudar a criar o gráfico do dispositivo. A tabela a seguir descreve como o `isCoopSafe` funciona com esses casos de uso para bloquear ou enviar dados para o gráfico do dispositivo

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso de uso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Visitantes autenticados</b> </p> </td> 
   <td colname="col2"> <p>Adicione <span class="codeph">isCoopSafe</span> ao seu código do serviço de ID para controlar como os dados para visitantes autenticados que aceitaram ou não os contratos de termos de uso são usados pelo Device Co-op para criar o gráfico do dispositivo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL em sites de terceiros</b> </p> </td> 
   <td colname="col2"> <p>Adicione <span class="codeph">isCoopSafe</span> ao seu código do serviço de ID para uso em sites de terceiros nos quais você: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">Não é possível garantir que visitantes autenticados tenham ou não aceitos contratos de termo de uso. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">É necessário controlar como esses dados são usados pelo Device Co-op para criar o gráfico do dispositivo. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sintaxe e amostra de código {#section-952f56724a2b4d349340e26fbaf33ddd}

**Sintaxe:** `isCoopSafe: true | false`

As opções booleanas determinam como os dados do cliente são usados ou não pelo Device Co-op.

* `isCoopSafe: true`: os dados do visitante coletados por um SDK móvel ou site *podem* ser usados para ajudar a criar o gráfico do dispositivo.

* `isCoopSafe: false`: os dados do visitante coletados por um SDK móvel ou site *não podem* ser usados para ajudar a criar o gráfico do dispositivo.

**Amostra de código**

Defina isso quando o código do serviço de ID instanciar:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## Parâmetros POST da chamada de evento {#section-fcd441933506493faefaa6b51f194a17}

Dependendo do sinalizador definido (`true` ou `false`), o serviço de ID converte `isCoopSafe` nesses parâmetros de POST e os envia para a [!DNL Adobe] em uma chamada de evento:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

Os parâmetros de POST informam o [!DNL Experience Cloud] Device Co-op se é possível incluir ou não os dados do usuário no gráfico do dispositivo. A tabela abaixo define a relação entre os sinalizadores booleanos `isCoopSafe` e os parâmetros POST passados em uma chamada de evento. Se você não usar `isCoopSafe`, nenhum é passado em uma chamada de evento.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status da configuração </th> 
   <th colname="col2" class="entry"> Parâmetro POST </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>O Device Co-op pode usar os dados do visitante para ajudar a criar o gráfico do dispositivo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>O Device Co-op não pode usar os dados do visitante para ajudar a criar o gráfico do dispositivo. </p> </td> 
  </tr> 
 </tbody> 
</table>

## APIs pós-instanciamento {#section-9281c39c8b6249d7864100b5cbca7dc6}

Essas APIs permitem que você substitua o status de `isCoopSafe`. Elas são necessárias porque permitem alterar o status de pós-instanciação/pós-login de um visitante em um site ou em um aplicativo de página única no qual a página não é atualizada. Por exemplo, você precisará chamar essas APIs se um usuário se autenticar em seu site ou aplicativo e, posteriormente, aceitar uma política de termos de uso que permita que o Device Co-op use seus dados.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>Define o parâmetro POST <span class="codeph">d_coop_safe=1</span> em todas as chamadas de evento subsequentes. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Define o parâmetro POST <span class="codeph">d_coop_unsafe=1</span> em todas as chamadas de evento subsequentes. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://docs.adobe.com/content/help/en/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

