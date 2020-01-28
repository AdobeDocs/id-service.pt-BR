---
description: Uma Política de segurança de conteúdo (CSP) é um recurso de cabeçalho HTTP e segurança que permite aos navegadores controlar o tipo de recursos carregados em uma página da Web. Consulte essa seção se você usa o serviço de ID e tem CSPs estritos que usam listas de permissões para aceitar recursos de domínios confiáveis. É necessário adicionar os domínios da Adobe listados aqui para as listas de permissões da CSP.
keywords: ID Service
seo-description: Uma Política de segurança de conteúdo (CSP) é um recurso de cabeçalho HTTP e segurança que permite aos navegadores controlar o tipo de recursos carregados em uma página da Web. Consulte essa seção se você usa o serviço de ID e tem CSPs estritos que usam listas de permissões para aceitar recursos de domínios confiáveis. É necessário adicionar os domínios da Adobe listados aqui para as listas de permissões da CSP.
seo-title: Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud
title: Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: ht
source-git-commit: 4c642bd9f1ca6841f6d532cef2c11ce4acca0b61

---


# Políticas de segurança de conteúdo e o serviço de identidade da Experience Cloud {#content-security-policies-and-the-experience-cloud-id-service}

Uma Política de segurança de conteúdo (CSP) é um recurso de cabeçalho HTTP e segurança que permite aos navegadores controlar o tipo de recursos carregados em uma página da Web. Consulte essa seção se você usa o serviço de ID e tem CSPs estritos que usam listas de permissões para aceitar recursos de domínios confiáveis. É necessário adicionar os domínios da Adobe listados aqui para as listas de permissões da CSP.

## Análise da CSP {#section-5fde5c00a678455c914b8307a8caab82}

As CSPs usam o cabeçalho HTTP `Content-Security-Policy` para controlar o tipo de recursos que os navegadores aceitam ou carregam em uma página. A aplicação de uma CSP pode ajudar você a impedir:

* O carregamento de arquivos JavaScript se a origem for desconhecida ou não estiver incluída em uma lista de permissões.
* Ataques de script intersite (XXS).
* Ataques de injeção de dados.
* Ataques de desfiguração de site.
* Distribuição de malware.

O uso de CSPs é comum e bem compreendido. O objetivo desta documentação não é explicar CSPs em detalhes (consulte os links com informações relacionadas abaixo para obter mais informações). O mais importante é compreender quais nomes de domínio da Adobe você deve adicionar à CSP caso use-os e se tiver políticas de segurança rígidas. Se você adicionar esses domínios, os navegadores dos visitantes que acessam o seu site poderão fazer chamadas importantes aos recursos da Experience Cloud que você utiliza.

## Domínios da Experience Cloud para listas de permissões {#section-30693e9a96834edfbf04de9e698cf2aa}

Adicione esses nomes de domínio ou URLs à sua CSP para cada lista da solução ou serviço da Experience Cloud que você usa.

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
   <td colname="col1"> <p> <b>Serviço de ID de visitante</b> </p> </td> 
   <td colname="col2"> <p>Modifique sua CSP para incluir <span class="codeph">*.demdex.net</span>. </p> <p>As chamadas para o domínio <span class="codeph"> demdex.net</span> são usadas para gerar os <a href="../introduction/cookies.md" format="dita" scope="local">Cookies e o Serviço de identidade da Experience Cloud</a> e para sincronizações de ID. Consulte, <a href="https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/reference/demdex-calls.translate.html" format="https" scope="external">Compreender as chamadas para o domínio Demdex</a>. </p> </td> </tr> 
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

