---
description: Uma Política de Segurança de Conteúdo (CSP) é um cabeçalho HTTP e um recurso de segurança que fornece aos navegadores controle sobre que tipo de recursos são carregados em uma página da Web. Incluir na lista de permissões Revise esta seção se você usar o serviço de ID e tiver CSPs rigorosas que usam para aceitar recursos de domínios confiáveis. Será necessário adicionar os domínios do Adobe listados aqui às suas listas de permissões CSP.
keywords: Serviço de ID
title: Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
source-git-commit: c56bbaa6a3639e421c11a8231e14afb58a4fa305
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 62%

---

# Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud {#content-security-policies-and-the-experience-cloud-id-service}

Uma Política de Segurança de Conteúdo (CSP) é um cabeçalho HTTP e um recurso de segurança que fornece aos navegadores controle sobre que tipo de recursos são carregados em uma página da Web. Incluir na lista de permissões Revise esta seção se você usar o serviço de ID e tiver CSPs rigorosas que usam para aceitar recursos de domínios confiáveis. Será necessário adicionar os domínios do Adobe listados aqui às suas listas de permissões CSP.

## Análise da CSP {#section-5fde5c00a678455c914b8307a8caab82}

As CSPs usam o cabeçalho HTTP `Content-Security-Policy` para controlar o tipo de recursos que os navegadores aceitam ou carregam em uma página. A aplicação de um CSP pode ajudá-lo a evitar:

* o carregamento de arquivos JavaScript incluir na lista de permissões se a origem for desconhecida ou não estiver incluída em um arquivo de pesquisa.
* Ataques de script entre sites (XXS).
* Ataques de injeção de dados.
* Ataques de deformação do site.
* Distribuição de malware.

A utilização de documentos de estratégia por país é comum e bem compreendida. Não é objetivo desta documentação explicar em detalhes os documentos de estratégia por país (para mais informações, consulte os links de informação relacionadas abaixo). É importante saber quais nomes de domínio da Adobe você deve adicionar a uma CSP se você os utilizar e tiver políticas de segurança restritas. A adição desses domínios permite que os navegadores de visitantes que acessam seu site façam essas chamadas importantes para os recursos da Experience Cloud que você usa.

## Domínios Experience Cloud para Incluir na lista de permissões {#section-30693e9a96834edfbf04de9e698cf2aa}

Adicione esses nomes de domínio ou URLs à CSP para cada solução ou serviço da lista da Experience Cloud que você usa.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">Solução ou serviço da Experience Cloud</th>
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
    <p><b>Serviço da Experience Cloud ID e Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>Modifique sua CSP para incluir os domínios abaixo.</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>Se você usar o Adobe Launch para implantar tags, também precisará adicionar <code>https://assets.adobedtm.com</code> à lista de domínios.</li>
    </ul>
    <p>As chamadas para o domínio <span class="codeph">demdex.net</span> são usadas para gerar os <a href="../introduction/cookies.md" format="dita" scope="local">Cookies e o Serviço de Identidade da Experience Cloud</a> e para sincronizações de ID. Consulte também <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=pt-BR" format="https" scope="external">Compreender as chamadas para o domínio Demdex</a>.</p>
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
    <p>Se você restringir os parâmetros da cadeia de caracteres de consulta, incluirá na lista de permissões os seguintes parâmetros:</p>
    <ul>
     <li><code>s_kwcid</code> (que usa <code>!</code>)</li>
     <li><code>ef_id</code> (que usa <code>:</code>)</li>
    </ul>
    <p>Se você bloquear o caractere <code>!</code> em URLs, também o incluirá na lista de permissões.</p>
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
