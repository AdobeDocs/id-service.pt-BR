---
description: Lançamentos, atualizações ou alterações de recursos no Serviço de identidade da Experience Platform para 2017.
keywords: Serviço de ID
seo-description: Lançamentos, atualizações ou alterações de recursos no Serviço de identidade da Experience Platform para 2017.
seo-title: Notas de versão de 2017
title: Notas de versão de 2017
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Notas de versão de 2017 {#release-notes}

Lançamentos, atualizações ou alterações de recursos no Serviço de identidade da Experience Platform para 2017.

Essas alterações também estão contempladas nas [notas de versão da Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/). Para consultar as notas de versão antigas do serviço de ID, consulte as [notas de versão anteriores](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) ou os links no fim desta página.

>[!NOTE]
>
>Não existem notas de versão do cliente ou alterações no código para março, abril, maio e outubro de 2017. Para esses meses, o código do serviço de ID permanece inalterado na v2.1.

## Versão 2.5 {#section-27b441509124493f80984ed09bd9e88b}

Setembro de 2017

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>Esta é uma API assíncrona que retorna os identificadores para o Analytics, o serviço de ID, o cancelamento da coleta de dados, a localização geográfica e o conteúdo “blob” de metadados por padrão. Além disso, você pode controlar quais IDs deseja retornar com a enumeração opcional <span class="codeph">visitor.FIELDS</span>. See <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correções de erros e outras alterações**

* Correção de um erro relacionado ao Chrome que fazia com que o serviço de ID mostrasse um erro ao clicar no botão Voltar no navegador.
* O serviço de ID agora rearquiva sincronizações de ID quando a ID da região na resposta da chamada do evento muda.
* Adicionada nova documentação, [Políticas de segurança do conteúdo e o Serviço de identidade da Experience Platform](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3), que explica como fazer chamadas de lista de permissões para domínios da Adobe usados pelo serviço de ID.

## Versão 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

Agosto de 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>Uma configuração booleana opcional que determina se o serviço de ID envia (ou não) dados ao Adobe Experience Cloud Device Co-op. Consulte <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Documentação revisada**

Atualização e revisão de [Perguntas frequentes](/help/faq-intro/faq-intro.md) para incluir perguntas frequentes separadas de diferentes soluções da [!DNL Experience Cloud].

## Versão 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

Julho de 2017

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>Quando adicionada à função <span class="codeph">Visitor.getInstance</span>, essa configuração permite substituir o intervalo de expiração padrão da ID de dados complementares (SDID) ao passar essa ID de uma página para a outra. Você usaria a <span class="codeph">sdidParamExpiry</span> com a função auxiliar <span class="codeph">appendSupplimentalDataTo</span>. Consulte <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>Essa função foi projetada principalmente para clientes do A4T e tem como objetivo ajudar a solucionar problemas que podem surgir ao trabalhar com IDs em sites/telas ou aplicativos de uma única página. Consulte <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correções de erros e outras alterações**

* Correção de um erro na VisitorAPI.js v2.2 que impedia que o serviço de ID e o Target funcionassem juntos no Internet Explorer.
* Código revisado para ajudar a melhorar a maneira que o serviço de ID envia dados para o iFrame de publicação de destino. Essa ação ajuda a reduzir o uso da CPU.

## Versão 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Data de lançamento: de junho de 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain e whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>Essas configurações permitem que diferentes instâncias do código do serviço de ID que foram implementados em um iFrame e na página principal comuniquem-se entre si. Foram projetadas para ajudar a resolver problemas com casos de uso específicos onde pode-se ou não controlar a página ou o domínio principal e onde há código do serviço de ID sendo carregado no iFrame de um domínio sob seu controle.  </p> </td> 
  </tr> 
 </tbody> 
</table>

## Atualizações da documentação de maio {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Tópico </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> Perguntas frequentes </a> </p> </td> 
   <td colname="col2"> <p>Atualização da seção <span class="keyword">Analytics</span> com informações sobre como encontrar informações do servidor de rastreamento. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Atualizações da documentação de abril {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Tópico </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer e audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Adicionados links para a documentação do <span class="keyword">Audience Manager</span> descrevendo as chamadas para o domínio <span class="codeph">demdex.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> Como entender a sincronização de ID e as taxas de correspondência </a> </p> </td> 
   <td colname="col2"> <p>Seção <span class="keyword">Media Optimizer</span> revisada para descrever a chamada para <span class="codeph">cm.eversttech.net</span>. Essa é a sincronização de ID automática que o serviço de ID executa com o <span class="keyword">Media Optimizer</span>. Esse recurso foi lançado em janeiro de 2017. Consulte a <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">Versão 2.0</a> abaixo. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versão 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Data de lançamento: de fevereiro de 2017

**Recursos**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recurso </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> Propriedade da API do serviço de ID, <span class="codeph">idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>Essa propriedade configura a ID de contêiner usada pelo <span class="keyword">Audience Manager</span> para sincronizações de ID. Consulte <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Método da API do serviço de ID, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>,<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Este método público anexa a <span class="wintitle">ID de Dados Suplementares</span> (SDID) como um parâmetro de sequência de caracteres de consulta a um URL de redirecionamento. Consulte <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correções**

Corrigida uma falha que causava o serviço de ID a fazer chamadas redundantes para uma ID em vez de usar a ID arquivada no cookie AMCV. (MCID-296)

**Nova documentação**

[Uso da busca DNS prévia com diferentes soluções e serviços da Experience Cloud`Learn how to use DNS prefetch to help reduce page load times.`](https://marketing.adobe.com/resources/help/en_US/mcloud/dns-prefetch.html)

## Versão 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

Janeiro de 2017

>[!IMPORTANT]
>
>O serviço de ID da v2.0 sincroniza IDs automaticamente com o Adobe Media Optimizer por padrão. Isso significa que você visualizará uma chamada da página para `cm.eversttech.net`, que é uma domínio herdado do [!DNL Media Optimizer] controlado pela [!DNL Adobe]. Consulte também [Como entender a sincronização de IDs e as taxas de correspondência](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Correções e melhorias**

* Correção de um bug que prevenia o AppMeasurement de fazer chamadas de rastreamento para o Analytics. (MCID-254, MCID-256, MCID-286)
* Correção de um bug que prevenia a falha imediata do serviço de ID caso o bloqueador de anúncios do visitante estivesse ativado e configurado para excluir o domínio demdex.net. Esse bug é raro e incomum, pois a maioria das ferramentas de bloqueio de anúncios não bloqueia o domínio demdex.net. (MCID-233)
* Correção de um bug causado por interações do código do serviço de ID e um script personalizado em um site de cliente. Esse problema impedia o Internet Explorer 9 de carregar páginas da Web. (MCID-206)

## Anos anteriores {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Notas de versão antigas do serviço de ID.
