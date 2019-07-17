---
description: Os navegadores usam o CORS (Cross Origin Resource Sharing, Compartilhamento de recursos de várias origens) para solicitar recursos de um domínio diferente do atual. O Serviço de identidade da Experience Cloud é compatível com os padrões CORS que permitem solicitações de recursos entre origens do cliente. O serviço de ID reverte solicitações JSONP em navegadores antigos ou incompatíveis com CORS.
keywords: Serviço de ID
seo-description: Os navegadores usam o CORS (Cross Origin Resource Sharing, Compartilhamento de recursos de várias origens) para solicitar recursos de um domínio diferente do atual. O Serviço de identidade da Experience Cloud é compatível com os padrões CORS que permitem solicitações de recursos entre origens do cliente. O serviço de ID reverte solicitações JSONP em navegadores antigos ou incompatíveis com CORS.
seo-title: Suporte ao CORS no serviço de identidade da Experience Cloud
title: Suporte ao CORS no serviço de identidade da Experience Cloud
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# CORS Support in the Experience Cloud Identity Service {#cors-support-in-the-experience-cloud-id-service}

Os navegadores usam o CORS (Cross Origin Resource Sharing, Compartilhamento de recursos de várias origens) para solicitar recursos de um domínio diferente do atual. O Serviço de identidade da Experience Cloud é compatível com os padrões CORS que permitem solicitações de recursos entre origens do cliente. O serviço de ID reverte solicitações JSONP em navegadores antigos ou incompatíveis com CORS.

## Problemas com políticas de mesma origem e solicitações do serviço de ID {#section-6608cf46d27143eeaeabacaa6aa14e8e}

As políticas de mesma origem são controles ou restrições de segurança aplicadas por um navegador. Quando aplicadas nesse nível, o navegador determina se uma solicitação de recursos efetuada de uma página para outra será permitida ou bloqueada. Para determinar se uma solicitação é de mesma origem, o navegador compara:

* Identificadores de recursos uniformes (URIs)
* Nomes de host (por exemplo, http://www.my-webpage-example.com)
* Números de porta (por exemplo, porta 80 e 440 para solicitações de HTTP e HTTPS)

O navegador permite a solicitação se ambas as páginas compartilham essas características, do contrário, bloqueia solicitações de recursos.

## O CORS soluciona problemas com políticas de mesma origem {#section-76c87ec3295d447bab220c84f138c235}

O CORS fornece um modo seguro e eficaz de solicitar recursos de vários domínios. A especificação do CORS inclui um conjunto de cabeçalhos HTTP que os navegadores podem usar para enviar, receber e avaliar solicitações de recursos. A avaliação de uma solicitação de recursos é chamada de *`preflight check`*. Essa verificação permite que os navegadores e servidores determinem quais solicitações são permitidas ou bloqueadas. A verificação é transparente para o aplicativo, a API ou o script que solicita um recurso. Dois cabeçalhos importantes no processo de solicitação de recursos incluem:

* `Origin`: um cabeçalho de solicitação que identifica a origem de uma solicitação.
* `Access-Control-Allow-Origin`: um cabeçalho de resposta que indica se um recurso pode ser compartilhado com o solicitante.

Vamos analisar como esses cabeçalhos funcionam. Neste exemplo, considere uma empresa de serviços financeiros que implementou o serviço da [!DNL Experience Cloud] ID no seu site, www.finance-website.com. A tabela a seguir define como os cabeçalhos de solicitação e resposta do CORS verificam o acesso a um recurso.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ação </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Solicitação</b> </p> </td> 
   <td colname="col2"> <p>Enquanto a página da empresa de finanças é carregada, o navegador faz uma solicitação para <span class="codeph">dpm.demdex.net</span>. Essa é uma chamada para o domínio dos servidores de coleta de dados (DCS) usados pelo serviço de ID. Essa solicitação entre domínios inclui o cabeçalho: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Resposta</b> </p> </td> 
   <td colname="col2"> <p>A resposta do domínio do DCS inclui os cabeçalhos que ao site da empresa financeira o acesso aos recursos necessários: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Controle de acesso com permissão de origem: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Controle de acesso com permissão de credenciais: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

Consulte também [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## Outros benefícios de uso do CORS {#section-6f44f30694c44f95bf9854b8a2af8449}

A tabela abaixo descreve algumas das vantagens do CORS para os clientes que usam o serviço de ID.

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Benefícios </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Aumento da segurança</b> </p> </td> 
   <td colname="col2"> <p>O CORS usa a <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" format="https" scope="external">XMLHttpRequest</a> para solicitar e transferir dados. Esse método é mais seguro do que uma solicitação JSONP. Ele garante que não existe uma maneira de executar um JavaScript arbitrário, que pode estar contido na resposta do DCS. A carga de resposta XMLHttpRequest do CORS é analisada pelo JavaScript do serviço de ID e não é executada em uma função de retorno de chamada. </p> <p> <p>Observação: para aceitar cookies, o objeto <span class="codeph">XMLHttpRequest</span> precisa ter a propriedade <span class="codeph">withCredentials</span> definida como <span class="codeph">true</span>. Essa propriedade é compatível com Chrome, Firefox, Internet Explorer (v10+), Opera e Safari. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Melhorias de desempenho</b> </p> </td> 
   <td colname="col2"> <p>O CORS ajuda a melhorar o desempenho porque: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">O navegador gerencia solicitações de recursos. O processo de solicitação é transparente no serviço de ID. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">Diferente das solicitações JSONP assíncronas, o navegador não desprioriza e consulta solicitações de CORS. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">O serviço de ID responde de forma permissiva. Ou seja, quando um URL é passado como <span class="codeph">Origem</span>, o serviço de ID concede à página o acesso aos recursos necessários. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

