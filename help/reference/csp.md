---
description: Uma Política de Segurança de Conteúdo (CSP) é um cabeçalho HTTP e um recurso de segurança que fornece aos navegadores controle sobre que tipo de recursos são carregados em uma página da Web. Revise esta seção se você usar o serviço de ID e tiver CSPs restritas que usam listas de permissões para aceitar recursos de domínios confiáveis. Será necessário adicionar os domínios da Adobe listados aqui às suas listas brancas de CSP.
keywords: ID Service
seo-description: Uma Política de Segurança de Conteúdo (CSP) é um cabeçalho HTTP e um recurso de segurança que fornece aos navegadores controle sobre que tipo de recursos são carregados em uma página da Web. Revise esta seção se você usar o serviço de ID e tiver CSPs restritas que usam listas de permissões para aceitar recursos de domínios confiáveis. Será necessário adicionar os domínios da Adobe listados aqui às suas listas brancas de CSP.
seo-title: Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud
title: Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '539'
ht-degree: 100%

---


# Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud {#content-security-policies-and-the-experience-cloud-id-service}

Uma Política de Segurança de Conteúdo (CSP) é um cabeçalho HTTP e um recurso de segurança que fornece aos navegadores controle sobre que tipo de recursos são carregados em uma página da Web. Revise esta seção se você usar o serviço de ID e tiver CSPs restritas que usam listas de permissões para aceitar recursos de domínios confiáveis. Será necessário adicionar os domínios da Adobe listados aqui às suas listas brancas de CSP.

## Análise da CSP {#section-5fde5c00a678455c914b8307a8caab82}

As CSPs usam o cabeçalho HTTP `Content-Security-Policy` para controlar o tipo de recursos que os navegadores aceitam ou carregam em uma página. A aplicação de um CSP pode ajudá-lo a evitar:

* O carregamento de arquivos JavaScript se a fonte for desconhecida ou não estiver incluída em uma lista de permissões.
* Ataques de script entre sites (XXS).
* Ataques de injeção de dados.
* Ataques de deformação do site.
* Distribuição de malware.

A utilização de documentos de estratégia por país é comum e bem compreendida. Não é objetivo desta documentação explicar em detalhes os documentos de estratégia por país (para mais informações, consulte os links de informação relacionadas abaixo). É importante saber quais nomes de domínio da Adobe você deve adicionar a uma CSP se você os utilizar e tiver políticas de segurança restritas. A adição desses domínios permite que os navegadores de visitantes que acessam seu site façam essas chamadas importantes para os recursos da Experience Cloud que você usa.

## Domínios da Experience Cloud para listas de permissões {#section-30693e9a96834edfbf04de9e698cf2aa}

Adicione esses nomes de domínio ou URLs à CSP para cada solução ou serviço da lista da Experience Cloud que você usa.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solução ou serviço da Experience Cloud </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>Modifique sua CSP para incluir o seguinte: </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>Modifique sua CSP para incluir <span class="codeph">*.tt.omtrdc.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Serviço da Experience Cloud ID e Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>Modifique sua CSP para incluir os domínios abaixo.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Se você usar o Adobe Launch para implantar tags, também precisará adicionar <code>https://assets.adobedtm.com</code> à lista de domínios.</li></ul></p> <p>As chamadas para o domínio <span class="codeph"> demdex.net</span> são usadas para gerar os <a href="../introduction/cookies.md" format="dita" scope="local">Cookies e o Serviço de identidade da Experience Cloud</a> e para sincronizações de ID. Consulte, <a href="https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Compreender as chamadas para o domínio Demdex</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Plug-in do Activity Map</b> </p> </td> 
 <td colname="col2"> <p>Modifique sua CSP para incluir *.adobe.com. **Nota**: Se você já tiver o Activity Map instalado antes de janeiro de 2020, seu navegador ainda verá uma solicitação inicial para *.omniture.com, mas será redirecionado para *.adobe.com. </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [Referência da política de segurança de conteúdo](https://content-security-policy.com/)
>* [MDN: política de segurança de conteúdo](https://developer.mozilla.org/pt/docs/Web/HTTP/CSP)
>* [Wikipedia: política de segurança de conteúdo](https://en.wikipedia.org/wiki/Content_Security_Policy)

