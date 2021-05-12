---
description: O serviço de ID usa a ID da organização, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
keywords: playstation, serviço de ID
seo-description: O serviço de ID usa a ID da organização, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.
seo-title: Cookies e o serviço de identidade da Experience Cloud
title: Cookies e o serviço de identidade da Experience Cloud
uuid: c5cbd235-37ee-4605-8792-b1a991e190ad
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
source-git-commit: d2bc28329c68c54a85dcf714083b3fcb5afc5a14
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 99%

---

# Cookies e o serviço de identidade da Experience Cloud {#cookies-and-the-experience-cloud-id-service}

O serviço de ID usa a ID da organização, o cookie AMCV da Experience Cloud e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o serviço de ID acompanhe os visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da Experience Cloud.

## Como entender os cookies do serviço de ID {#section-f438168beaec409ab8b2cc58bd021e26}

O serviço de ID depende dos cookies AMCV, AMCVS e demdex para funcionar corretamente. Esses cookies são apenas arquivos que armazenam dados usados pelo serviço de ID. Esses cookies do serviço de ID não são perigosos, maliciosos nem diferentes dos outros cookies próprios ou de terceiros armazenados por um site ou serviço em um navegador e seguem as mesmas regras que regem os outros cookies próprios e de terceiros. Consulte as seções abaixo para obter mais informações sobre os cookies usados pelo serviço de ID.

### O que os cookies do serviço de ID podem fazer

* Defina e armazene um identificador exclusivo para os visitantes do site (a MID).
* Mantenha esse identificador exclusivo para que o serviço de ID possa coletar e compartilhar dados com outras soluções da Experience Cloud.
* Rastrear usuários em seus domínios. No entanto, isso requer que você seja o proprietário desses outros domínios e tenha o código do serviço de ID implantado neles.

### O que os cookies do serviço de ID não podem fazer

* Armazene, transmita ou execute vírus de computador.
* Acesse ou armazene informações de identificação pessoal (PII) como seu endereço de email.
* Controle o hardware ou software do computador.
* Torne os computadores instáveis ou cause problemas de desempenho.
* Rastreie usuários em sites que não usam o serviço de ID.

## cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

Os seguintes atributos do cookie definido pelo serviço de ID.

**Nome**

O nome do cookie AMCV segue a sintaxe `AMCV_<variable name>@AdobeOrg`. No nome, os `<variable name>` elementos são marcadores de posição de parte da ID da organização da Experience Cloud. Essa ID é passada no DCS pela `Visitor.getInstance` função no código do serviço de ID.

Um nome de cookie completamente formado seria parecido com isto:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Conteúdo**

O cookie AMCV contém a ID de visitante da Experience Cloud ou a MID. A MID é armazenada em um par de valores chave que segue a sintaxe `MCMID|<Experience Cloud ID>`.

Um par de valor principal completamente formado seria parecido com:

```
MCMID|20265673158980419722735089753036633573
```

Esse identificador persistente permite o compartilhamento de dados entre soluções.

**Domínio**

O cookie AMCV é definido no domínio próprio de um navegador. Isso significa que ele é definido no domínio do site visitado atualmente por um usuário. Dessa forma, o código do serviço de ID e outras bibliotecas de código da Experience Cloud podem ler a MID armazenada no cookie AMCV.

No entanto, como o cookie AMCV está definido no domínio primário, ele não pode ser usado para rastrear e identificar usuários em domínios diferentes. Em vez disso, o serviço de ID depende da ID da organização e da ID demdex para retornar a MID correta quando um visitante do site navega para um domínio diferente.

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

O cookie AMCVS é definido no domínio próprio de um navegador. Isso significa que ele é definido no domínio do site visitado atualmente por um usuário.

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
   <td colname="col2"> <p>O nome do cookie é "demdex." </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Conteúdo</b> </p> </td> 
   <td colname="col2"> <p>O cookie demdex contém a ID demdex, que é gerada pelo DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Domínio</b> </p> </td> 
   <td colname="col2"> <p>O cookie demdex é definido no domínio demdex.net de terceiros no navegador. Este domínio é separado do site visitado atualmente por um usuário. </p> <p>Diferentemente do cookie primário, AMCV, o cookie e a ID demdex persistem em domínios diferentes. A ID demdex e a ID da empresa são os valores comuns que permitem que o serviço de ID retorne e identifique um visitante do site com a ID de visitante correta. </p> </td> 
  </tr> 
 </tbody> 
</table>

Para obter informações relacionadas, consulte [Compreender as chamadas para o domínio Demdex](https://docs.adobe.com/content/help/pt-BR/audience-manager/user-guide/reference/demdex-calls.html).

## Gerar a Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

A Experience Cloud ID (MID) é derivada matematicamente da ID da organização e da ID demdex. Desde que essas IDs permaneçam constantes, gerar a MID certa para um usuário específico é simplesmente um problema matemático. Com a mesma ID de empresa e ID demdex, você obtém o mesmo valor de MID sempre. Isso permite que o serviço de ID rastreie visitantes em domínios que você controla e configurados com o código do serviço de ID.

O serviço de ID começa a criar uma MID à medida que a página é carregada. Durante esse processo, o código fornecido pela `visitorAPI.js` biblioteca de códigos enviar a ID da organização em uma chamada de evento para o serviço de ID. O serviço de ID cria e retorna a MID, além de uma ID demdex nos cookies AMCV e demdex, respectivamente.

## Sinalizadores de cookies

A tabela a seguir descreve os sinalizadores para Cookies da Experience Cloud:

| Cookie (definido por) | httpOnly | Seguro | SameSite |
|--- |--- |--- |--- |
| demdex (resposta http) | Não | Sim | &quot;Nenhum&quot; |
| AMCV (JavaScript) | Não | Configurável | Unset (padrões para Lax) |
| AMCVS (JavaScript) | Não | Configurável | Unset (padrões para Lax) |

*Observação: Para obter informações sobre como configurar o cookie AMCV e AMCVS com atributos seguros, consulte o tópico para [secureCookie](https://docs.adobe.com/content/help/pt-BR/id-service/using/id-service-api/configurations/securecookie.html).*

## Próximas etapas {#section-8db1727a63bc4ff68b495f270315d453}

Consulte [Como o serviço de identidade da Experience Cloud solicita e define IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).
