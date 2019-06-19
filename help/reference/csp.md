---
description: Uma Política de segurança de conteúdo (CSP) é um recurso de cabeçalho HTTP e segurança que permite aos navegadores controlar o tipo de recursos carregados em uma página da Web. Consulte essa seção se você usa o serviço de ID e tem CSPs estritos que usam listas de permissões para aceitar recursos de domínios confiáveis. É necessário adicionar os domínios da Adobe listados aqui para as listas de permissões da CSP.
keywords: Serviço de ID
seo-description: Uma Política de segurança de conteúdo (CSP) é um recurso de cabeçalho HTTP e segurança que permite aos navegadores controlar o tipo de recursos carregados em uma página da Web. Consulte essa seção se você usa o serviço de ID e tem CSPs estritos que usam listas de permissões para aceitar recursos de domínios confiáveis. É necessário adicionar os domínios da Adobe listados aqui para as listas de permissões da CSP.
seo-title: Políticas de segurança de conteúdo e o serviço de identidade da plataforma Experience Platform
title: Políticas de segurança de conteúdo e o serviço de identidade da plataforma Experience Platform
uuid: 7399 fed 3-01 c 1-4730-834 e-e 2 dd 2 c 5791 ff
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Políticas de segurança de conteúdo e o serviço de identidade da plataforma Experience Platform {#content-security-policies-and-the-experience-cloud-id-service}

Uma Política de segurança de conteúdo (CSP) é um recurso de cabeçalho HTTP e segurança que permite aos navegadores controlar o tipo de recursos carregados em uma página da Web. Consulte essa seção se você usa o serviço de ID e tem CSPs estritos que usam listas de permissões para aceitar recursos de domínios confiáveis. É necessário adicionar os domínios da Adobe listados aqui para as listas de permissões da CSP.

## Análise da CSP {#section-5fde5c00a678455c914b8307a8caab82}

Os csps usam o cabeçalho HTTP `Content-Security-Policy` para controlar o tipo de recursos que um navegador aceita ou carrega em uma página. A aplicação de uma CSP pode ajudar você a impedir:

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
   <td colname="col2"> <p>Modifique sua CSP para incluir <span class="codeph">*.demdex.net</span>. </p> <p>As chamadas para o domínio <span class="codeph"> demdex. net</span> são usadas para gerar <a href="../introduction/cookies.md" format="dita" scope="local"> os Cookies e o Serviço de identidade da plataforma Experience Platform</a> e para sincronizações de ID. Consulte, <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Compreender as chamadas para o domínio Demdex</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ LIKE_ THIS]
>
>* [Referência da política de segurança de conteúdo](https://content-security-policy.com/)
>* [MDN: política de segurança de conteúdo](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: política de segurança de conteúdo](https://en.wikipedia.org/wiki/Content_Security_Policy)
