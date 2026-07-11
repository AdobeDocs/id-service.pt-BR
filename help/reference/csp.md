---
description: Uma Política de Segurança de Conteúdo (CSP) é um cabeçalho HTTP e um recurso de segurança que fornece aos navegadores controle sobre que tipo de recursos são carregados em uma página da Web. Revise esta seção se você usar o Serviço de ID de visitante e tiver CSPs restritas que usam incluis na lista de permissões para aceitar recursos de domínios confiáveis. Será necessário adicionar os domínios do Adobe listados aqui às suas incluis na lista de permissões da CSP.
keywords: Serviço de ID de visitante
title: Políticas de segurança de conteúdo e o serviço de ID de visitante da Adobe
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
TQID: https://experienceleague.adobe.com/UX0RWE7v912XEHJCJE49yt1sy13t1P0I0I79gG9Z7m8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 527
ht-degree: 49%

---

# Políticas de segurança de conteúdo e o serviço de ID de visitante da Adobe {#content-security-policies-and-the-experience-cloud-id-service}

Uma Política de Segurança de Conteúdo (CSP) é um cabeçalho HTTP e um recurso de segurança que fornece aos navegadores controle sobre que tipo de recursos são carregados em uma página da Web. Revise esta seção se você usar o Serviço de ID de visitante e tiver CSPs restritas que usam incluis na lista de permissões para aceitar recursos de domínios confiáveis. Será necessário adicionar os domínios do Adobe listados aqui às suas incluis na lista de permissões da CSP.

## Análise da CSP {#section-5fde5c00a678455c914b8307a8caab82}

As CSPs usam o cabeçalho HTTP `Content-Security-Policy` para controlar o tipo de recursos que os navegadores aceitam ou carregam em uma página. A aplicação de um CSP pode ajudá-lo a evitar:

* o carregamento de arquivos JavaScript se a origem for desconhecida ou não estiver incluída em um incluo na lista de permissões.
* Ataques de script entre sites (XXS).
* Ataques de injeção de dados.
* Ataques de deformação do site.
* Distribuição de malware.

A utilização de documentos de estratégia por país é comum e bem compreendida. Não é objetivo desta documentação explicar em detalhes os documentos de estratégia por país (para mais informações, consulte os links de informação relacionadas abaixo). É importante saber quais nomes de domínio da Adobe você deve adicionar a uma CSP se você os utilizar e tiver políticas de segurança restritas. A adição desses domínios permite que os navegadores de visitantes que acessam seu site façam essas chamadas importantes para os recursos do CX Enterprise que você usa.

## Domínios corporativos CX para o Incluir na lista de permissões {#section-30693e9a96834edfbf04de9e698cf2aa}

Adicione esses nomes de domínio ou URLs à CSP para cada solução ou serviço corporativo da lista CX que você usa.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">Solução ou serviço corporativo CX</th>
   <th colname="col2" class="entry">Descrição</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>Modifique sua CSP para incluir o seguinte:</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Target</b></p>
   </td>
   <td colname="col2">
    <p>Modifique sua CSP para incluir <span class="codeph">*.tt.omtrdc.net</span>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Serviço de ID de visitante e Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>Modifique sua CSP para incluir os domínios abaixo.</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>Se você usar marcas, também precisará adicionar <code>https://assets.adobedtm.com</code> à lista de domínios.</li>
    </ul>
    <p>As chamadas para o domínio <span class="codeph">demdex.net</span> são usadas para gerar os <a href="../introduction/cookies.md" format="dita" scope="local">Cookies e o Serviço de ID do Visitante</a> e para sincronizações de ID. Consulte também <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=pt-BR" format="https" scope="external">Compreender as chamadas para o domínio Demdex</a>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Plug-in do Activity Map</b></p>
   </td>
   <td colname="col2">
    <p>Modifique sua CSP para incluir *.adobe.com. **Nota**: Se você já tiver o Activity Map instalado antes de janeiro de 2020, seu navegador ainda verá uma solicitação inicial para *.omniture.com, mas será redirecionado para *.adobe.com.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>Se você restringir os parâmetros da string de consulta, inclua na lista de permissões os seguintes parâmetros:</p>
    <ul>
     <li><code>s_kwcid</code> (que usa <code>!</code>)</li>
     <li><code>ef_id</code> (que usa <code>:</code>)</li>
    </ul>
    <p>Se você bloquear o caractere <code>!</code> em URLs, inclua na lista de permissões-o também.</p>
    <p>O Advertising Analytics usa somente <code>s_kwcid</code>, mas o Advertising Search, Social, &amp; Commerce e Advertising DSP também usam <code>ef_id</code>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>Modifique sua CSP para incluir os seguintes domínios:</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [Referência da política de segurança de conteúdo](https://content-security-policy.com/)
>* [MDN: política de segurança de conteúdo](https://developer.mozilla.org/pt/docs/Web/HTTP/CSP)
>* [Wikipedia: política de segurança de conteúdo](https://en.wikipedia.org/wiki/Content_Security_Policy)

