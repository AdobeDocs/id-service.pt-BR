---
description: O serviço de ID usa a ID da empresa, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
keywords: playstation, serviço de ID
seo-description: O serviço de ID usa a ID da empresa, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
seo-title: Cookies e o serviço de identidade da Experience Cloud
title: Cookies e o serviço de identidade da Experience Cloud
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Cookies and the Experience Cloud Identity Service{#cookies-and-the-experience-cloud-id-service}

O serviço de ID usa a ID da empresa, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.

## Como entender os cookies do serviço de ID {#section-f438168beaec409ab8b2cc58bd021e26}

O serviço de ID depende dos cookies AMCV, AMCVS e demdex para funcionar corretamente. Esses cookies são apenas arquivos que armazenam dados usados pelo serviço de ID. Esses cookies do serviço de ID não são perigosos, maliciosos nem diferentes dos outros cookies próprios ou de terceiros armazenados por um site ou serviço em um navegador e seguem as mesmas regras que regem os outros cookies próprios e de terceiros. Consulte as seções abaixo para obter mais informações sobre os cookies usados pelo serviço de ID.

**O que os cookies do serviço de ID podem fazer**

* Definir e armazenar uma ID exclusiva para visitantes do seu site (a MID).
* Continuar com essa ID exclusiva para que o serviço de ID possa coletar e compartilhar dados com outras soluções da Experience Cloud.
* Rastrear usuários nos seus domínios. No entanto, isso exige que você seja o proprietário desses domínios e que o código do serviço de ID seja implantado neles.

**O que os ookies do serviço de ID não podem fazer**

* Armazenar, transmitir ou executar vírus de computador.
* Acessar ou armazenar informações pessoais identificáveis (PII), como seu endereço de email.
* Controlar o hardware ou o software do computador.
* Deixar os computadores instáveis ou causar problemas de desempenho.
* Rastrear os usuários em sites que não usam o serviço de ID.

## cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

Os seguintes atributos do cookie definido pelo serviço de ID.

**Nome**

O nome do cookie AMCV segue a sintaxe `AMCV_<variable name>@AdobeOrg`. No nome, os `<variable name>` elementos são marcadores de posição de parte da ID da organização da Experience Cloud. Essa ID é passada no DCS pela `Visitor.getInstance` função no código do serviço de ID.

Um nome de cookie completamente formado seria parecido com isto:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Conteúdo**

O cookie AMCV contém a MID ou ID de visitante da Experience Cloud. A MID é armazenada em um par de valores chave que segue a sintaxe `mid|<Experience Cloud ID>`.

Um par de valor principal completamente formado seria parecido com:

```
mid|20265673158980419722735089753036633573
```

O identificador contínuo permite o compartilhamento de dados entre soluções.

**Domínio**

O cookie AMCV é definido no domínio próprio de um navegador. Isso significa que ele é definido no domínio do site que o usuário está visitando no momento. Assim, o código do serviço de ID e outras bibliotecas de códigos da Experience Cloud podem ler a MID armazenada no cookie AMCV.

No entanto, como o cookie AMCV está definido no domínio primário, ele não pode ser usado para rastrear e identificar usuários entre domínios diferentes. Em vez disso, o serviço de ID recorre à ID da organização e à ID demdex para retornar a MID correta quando um visitante do site navega para um domínio diferente.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nome**

O nome do cookie AMCVS segue a sintaxe `AMCVS_####@AdobeOrg`. No nome, os elementos #### são marcadores de posição de parte da ID da organização da Experience Cloud. Essa ID é passada no DCS pela `theVisitor.getInstance` função no código do serviço de ID.

Um nome de cookie completamente formado seria parecido com isto:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Conteúdo**

O cookie AMCVS serve como um sinalizador que indica que a sessão está sendo inicializada. Seu valor é sempre `1` e descontinua quando a sessão é encerrada.

**Domínio**

O cookie AMCVS é definido no domínio próprio de um navegador. Isso significa que ele é definido no domínio do site que o usuário está visitando no momento.

![](assets/AMCVS-cookie.png)

## Cookie demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

A tabela a seguir lista e define alguns atributos importantes do cookie demdex.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Atributo </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Nome</b> </p> </td> 
   <td colname="col2"> <p>O nome do cookie é “demdex”. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Conteúdo</b> </p> </td> 
   <td colname="col2"> <p>O cookie demdex contém a ID demdex, gerada pelo DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domínio</b> </p> </td> 
   <td colname="col2"> <p>O cookie demdex é definido no domínio demdex.net de terceiros no navegador. Esse domínio é separado do site que o usuário visita no momento. </p> <p>Diferente do cookie primário, o cookie AMCV, a ID e o cookie demdex persistem em todos os diferentes domínios. A ID demdex e a ID da organização são os valores comuns que permitem ao serviço de ID retornar e identificar um visitante do site com a ID de visitante adequada. </p> </td> 
  </tr> 
 </tbody> 
</table>

For related information, see [Understanding Calls to the Demdex Domain](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

## Gerar a Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

A Experience Cloud ID (MID) é derivada matematicamente da ID da organização e da ID demdex. Enquanto essas IDs permanecerem constantes, a geração da MID correta para um usuário específico é apenas um problemas matemático. Com a mesma ID da organização e ID demdex, é possível obter o mesmo valor de MID todas as vezes. Isso permite que o serviço de ID rastreie visitantes nos domínios que você controla e configurou com o código do serviço de ID.

O serviço de ID começa a criar uma MID enquanto a página carrega. Durante esse processo, o código fornecido pela `visitorAPI.js` biblioteca de códigos enviar a ID da organização em uma chamada de evento para o serviço de ID. O serviço de ID cria e retorna a MID, além de uma ID demdex nos cookies AMCV e demdex, respectivamente.

## Próximas etapas {#section-8db1727a63bc4ff68b495f270315d453}

See [How the Experience Cloud Identity Service Requests and Sets IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
