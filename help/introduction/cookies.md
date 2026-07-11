---
description: O Serviço de ID de visitante usa a ID da organização IMS, o cookie AMCV da CX Enterprise e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o Serviço de ID do visitante rastreie visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da CX Enterprise.
keywords: playstation;Serviço de ID de visitante
title: Cookies e o serviço de ID de visitante da Adobe
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
TQID: https://experienceleague.adobe.com/iLOFGQ9t-DqYfqOZs3K5yZI7903dMPEjANaJ7lH8K0o
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 990
ht-degree: 42%

---

# Cookies e o serviço de ID de visitante da Adobe{#cookies-and-the-experience-cloud-id-service}

O Serviço de ID de visitante usa a ID da organização IMS, o cookie AMCV da CX Enterprise e o cookie demdex para criar e armazenar identificadores contínuos e exclusivos para os visitantes do site. Esses cookies permitem que o Serviço de ID do visitante rastreie visitantes em domínios diferentes e permite o compartilhamento de dados entre diferentes soluções da CX Enterprise.

## Compreensão de cookies do Serviço de ID do visitante {#section-f438168beaec409ab8b2cc58bd021e26}

O Serviço de ID de visitante depende dos cookies AMCV, AMCVS e demdex para funcionar corretamente. Esses cookies são apenas arquivos que armazenam dados usados pelo Serviço de ID do visitante. Esses cookies do Serviço de ID do visitante não são perigosos, maliciosos nem diferentes dos outros cookies próprios ou de terceiros armazenados por um site ou serviço em um navegador e seguem as mesmas regras que regem os outros cookies próprios e de terceiros. Consulte as seções a seguir para obter mais informações sobre os cookies usados pelo Serviço de ID do visitante.

### O que os cookies do Serviço de ID de visitante podem fazer

* Defina e armazene um identificador exclusivo para os visitantes do site (a MID).
* Mantenha esse identificador exclusivo para que o Serviço de ID do visitante possa coletar e compartilhar dados com outras soluções da CX Enterprise.
* Rastrear usuários em seus domínios. No entanto, isso requer que você seja o proprietário desses outros domínios e tenha o código do Serviço de ID de visitante implantado neles.

### O que os cookies do Serviço de ID do visitante não podem fazer

* Armazene, transmita ou execute vírus de computador.
* Acesse ou armazene informações de identificação pessoal (PII) como seu endereço de email.
* Controle o hardware ou software do computador.
* Torne os computadores instáveis ou cause problemas de desempenho.
* Rastrear usuários em sites que não usam o Serviço de ID de visitante.

## Cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

Os seguintes atributos do cookie definido pelo Serviço de ID do visitante.

**Nome**

O nome do cookie AMCV segue a sintaxe `AMCV_<variable name>@AdobeOrg`. No nome, os elementos `<variable name>` são espaços reservados para parte da ID da organização IMS. Essa ID é passada no DCS pela função `Visitor.getInstance` no código do Serviço de ID de visitante.

Um nome de cookie completamente formado seria parecido com isto:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Conteúdo**

O cookie AMCV contém a ECID ou a MID. A MID é armazenada em um par de valores chave que segue a sintaxe `MCMID|<ECID>`.

Um par de valor principal completamente formado seria parecido com:

```
MCMID|20265673158980419722735089753036633573
```

Esse identificador persistente permite o compartilhamento de dados entre soluções.

**Domínio**

O cookie AMCV é definido no domínio próprio de um navegador. Isso significa que ele é definido no domínio do site visitado atualmente por um usuário. Dessa forma, o código do Serviço de ID de visitante e outras bibliotecas de código corporativo CX podem ler a MID armazenada no cookie AMCV.

No entanto, como o cookie AMCV está definido no domínio primário, ele não pode ser usado para rastrear e identificar usuários em domínios diferentes. Em vez disso, o Serviço de ID de visitante depende da ID da organização IMS e da ID demdex para retornar a MID correta quando um visitante do site navega para um domínio diferente.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nome**

O nome do cookie AMCVS segue a sintaxe `AMCVS_####@AdobeOrg`. No nome, os elementos #### são espaços reservados para parte da ID da organização IMS. Essa ID é passada no DCS pela função `theVisitor.getInstance` no código do Serviço de ID de visitante.

Um nome de cookie completamente formado seria parecido com isto:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Conteúdo**

O cookie AMCVS serve como um sinalizador que indica que a sessão está sendo inicializada. Seu valor é sempre `1` e descontinua quando a sessão é encerrada.

**Domínio**

O cookie AMCVS é definido no domínio próprio de um navegador. Isso significa que ele é definido no domínio do site visitado atualmente por um usuário.

![](assets/AMCVS-cookie.png)

## Cookie Demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

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
   <td colname="col2"> <p>O cookie demdex é definido no domínio demdex.net de terceiros no navegador. Este domínio é separado do site visitado atualmente por um usuário. </p> <p>Diferentemente do cookie primário, AMCV, o cookie e a ID demdex persistem em domínios diferentes. A ID demdex e a ID da organização IMS são os valores comuns que permitem que o Serviço de ID de visitante retorne e identifique um visitante do site com a ID de visitante correta. </p> </td> 
  </tr> 
 </tbody> 
</table>

Para obter informações sobre divulgações relacionadas ao Demdex, consulte as [Divulgações de armazenamento de dispositivos do Audience Manager](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json).

Para obter informações relacionadas, leia a documentação [Como entender as chamadas para o domínio Demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=pt-BR).

## Gerar a ECID {#section-15f69c0bac394b4b9966a23fbc586d17}

A ECID é derivada matematicamente da ID da organização IMS e da ID demdex. Desde que essas IDs permaneçam constantes, gerar a MID certa para um usuário específico é simplesmente um problema matemático. Com a mesma ID organizacional IMS e ID demdex, você obtém o mesmo valor de MID sempre. Isso permite que o Serviço de ID do visitante rastreie visitantes em domínios que você controla e configurados com o código do Serviço de ID do visitante.

O Serviço de ID de visitante começa a criar uma MID à medida que a página é carregada. Durante esse processo, o código fornecido pela biblioteca de códigos do `VisitorAPI.js` envia sua ID da organização IMS em uma chamada de evento para o Serviço de ID do visitante. O Serviço de ID do visitante cria e retorna a MID, além de uma ID demdex nos cookies AMCV e demdex, respectivamente.

## Sinalizadores de cookies

A tabela a seguir descreve os flags dos Cookies Corporativos CX:

| Cookie (definido por) | httpOnly | Seguro | SameSite |
|--- |--- |--- |--- |
| demdex (resposta http) | Não | Sim | &quot;Nenhum&quot; |
| AMCV (JavaScript) | Não | Configurável | Unset (padrões para Lax) |
| AMCVS (JavaScript) | Não | Configurável | Unset (padrões para Lax) |

*Observação: para obter informações sobre como configurar o cookie AMCV e AMCVS com atributos seguros, consulte o tópico do [secureCookie](../library/function-vars/securecookie.md).*

## Próximas etapas {#section-8db1727a63bc4ff68b495f270315d453}

Consulte [Como o Serviço de ID de visitante solicita e define IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

