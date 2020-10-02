---
title: Alterações na rotulagem do Google Chrome SameSite
seo-title: Alterações na rotulagem do Google Chrome SameSite
description: Documentação da biblioteca da Adobe ECID (serviço de ID).
seo-description: Documentação da biblioteca da Adobe ECID (serviço de ID).
translation-type: tm+mt
source-git-commit: 592ca6ca6a72e57b728e286d0b730c5bd93c0c7b
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---


# Alterações na rotulagem do Google Chrome SameSite {#google-chrome-samesite-labelling-changes}

O atributo SameSite informa aos navegadores quando e como disparar cookies em cenários originais e de terceiros. O atributo SameSite pode ter um de três valores: `strict`, `lax`ou `none`. Chrome, Firefox, Edge, Safari e Opera têm suporte `strict` e `lax` desde novembro de 2017, enquanto `none` foi introduzido em 2018. No entanto, alguns navegadores mais antigos não suportam essa configuração.

Em fevereiro de 2020, o Google lançou o Chrome 80 e alterou a configuração padrão de `none` para `lax` quando um cookie não tem um valor de atributo SameSite especificado. Essa configuração impede que um cookie seja usado em um contexto de terceiros, também conhecido como &quot;entre sites&quot;. Todos os cookies subsequentes de terceiros devem ser definidos `SameSite=none` e rotulados como seguros.

Os cookies sem um valor de atributo SameSite especificado assumirão como padrão `lax`.

Visite o documento [padrão de](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) cookie para obter mais informações sobre os atributos do SameSite.

## Valores de atributo SameSite

| Valor do atributo SameSite | Descrições |
| ------ | ------------ |
| `strict` | Os cookies com essa configuração só são enviados quando a página de referência e a landing page fazem parte do mesmo domínio que o cookie. |
| `lax` | Os cookies com essa configuração só são enviados quando o domínio exibido no URL do navegador corresponde ao domínio do cookie. Este é o novo padrão para cookies no Chrome. |
| `none` | Os cookies com essa configuração estão disponíveis para acesso externo ou de terceiros, como &quot;entre sites&quot;. Antes dessa alteração, `none` era a configuração padrão do SameSite para cookies, portanto, usar essa configuração faz com que um cookie se comporte de forma mais semelhante à forma como funcionava tradicionalmente. No entanto, o Google exige que qualquer cookie com essa configuração agora especifique o sinalizador seguro, o que significa que o cookie só será criado e enviado com solicitações em HTTPS. Todos os cookies entre sites sem o sinalizador seguro serão rejeitados pelo Google. |

## O que você precisa saber como cliente da Adobe Experience Cloud

**Nenhuma atualização do JavaScript necessária**

Os produtos Adobe já lançaram atualizações do lado do servidor para definir cookies de terceiros com os atributos apropriados. Não são necessárias atualizações da biblioteca JavaScript para nossos clientes.

**Verifique se os pontos de extremidade de terceiros estão usando HTTPS**

Todos os clientes devem confirmar que sua configuração JavaScript está usando o HTTPS para suas chamadas para serviços de Adobe. Público alvo, Audience Manager e o Experience Cloud Identity Service (ECID) estão redirecionando chamadas HTTP de terceiros para seus respectivos pontos finais HTTPS, o que pode aumentar a latência. Isso significa que você não precisa alterar sua configuração. Os clientes do Analytics devem atualizar suas implementações para usar exclusivamente HTTPS, já que os redirecionamentos específicos do Analytics podem causar perda de dados.

**Cookies corretamente rotulados devem coletar dados conforme planejado**

Desde que os cookies estejam rotulados corretamente, os navegadores não tomarão nenhuma ação para bloqueá-los. Os consumidores terão a opção de bloquear determinados tipos de cookies, mas, atualmente, essa opção parece ser apenas uma configuração de aceitação.

**Cookies de terceiros existentes sem os rótulos atualizados serão ignorados**

Cookies de terceiros criados antes do Chrome 80 começar a aplicar as configurações de SameSite=`none` e sinalizadores seguros serão ignorados pelo Chrome 80 se esses sinalizadores não estiverem presentes.

Muitos dos cookies de terceiros existentes do Adobe não têm esses sinalizadores e precisarão ser atualizados pelos servidores Edge antes que os usuários atualizem para o Chrome 80 ou esses cookies sejam perdidos. A atualização dos servidores Edge ocorre automaticamente quando os usuários visitam qualquer site onde o cookie é usado.

A maioria dos produtos Adobe já tem os sinalizadores apropriados atribuídos aos cookies. A exceção são implementações do Analytics que usam coleta de dados de terceiros e não usam a ECID. Os clientes podem experimentar um pequeno aumento temporário em novos visitantes que, de outra forma, teriam retornado visitantes.

**Possível diminuição da correspondência de cookies para parceiros de destino e de mercado (somente Audience Manager)**

Embora a Adobe tenha controle sobre a atualização de seus cookies, a Adobe não pode forçar os parceiros a fazer as alterações necessárias. A correspondência de cookies pode diminuir para clientes do Audience Manager que usam parceiros de destino ou parceiros do mercado que não fizeram essas atualizações.

**Cookies de terceiros amigáveis ao Analytics (somente`s_vi`cookies do Analytics)**

Algumas implementações do Analytics usam um alias CNAME do Analytics para permitir a criação do `s_vi` cookie no domínio desse CNAME. Se o CNAME estiver no mesmo domínio do site, ele será designado como um cookie primário. No entanto, se você possuir vários domínios e usar o mesmo CNAME para a coleta de dados em todos os domínios, ele será designado como um cookie de terceiros nesses outros domínios.

Com `lax` a nova configuração padrão SameSite no Chrome, o CNAME não fica mais visível em outros domínios.

Para acomodar a alteração, o Analytics agora está definindo explicitamente o valor de `s_vi` cookie para SameSite `lax`. Para usar esse cookie em um contexto amigável de terceiros, defina o valor de SameSite como `none`, o que significa que você sempre deve usar HTTPS. Entre em contato com o Atendimento ao cliente para alterar o valor de SameSite para seus CNAMEs protegidos.

>[!IMPORTANT]
>
>Essa ação não é necessária para clientes do Analytics que usam ECID, clientes que usam um CNAME separado para cada um de seus domínios ou clientes que usam somente a coleta de dados de terceiros do Analytics.

## Cookies de Visitante padrão do Adobe

Somente os cookies padrão comuns do visitante estão listados na tabela abaixo. Para obter configurações de cookies adicionais, consulte a documentação específica do produto ou entre em contato com o representante do Adobe.

### ECID

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Cliente primário | Sem valor adicionado *O padrão do Chrome é a `lax` configuração | Configurável |
| AMCVS_###@AdobeOrg | Cliente primário | Sem valor adicionado *O padrão do Chrome é a `lax` configuração | Configurável |
| s_ecid | Primeiro participante do servidor | SameSite==`lax` | Não definido |

### Audience Manager

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Terceiros | `none` | Definir para proteger |
| Dextp | Terceiros | `none` | Definir para proteger |

### Analytics

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Primeiro participante do servidor se estiver usando `CNAME` </li> <li>Terceiros se estiverem usando 2o7.net ou omtrdc.net</li></ul> | <ul><li>`lax` if first-party</li> <li>`none` se terceiros</li></ul> *Os clientes podem editar a configuração por meio do ticket do Atendimento ao cliente para domínios primários* | Definir, se estiver usando `none` uma solicitação HTTPS |
| s_fid | Cliente primário | Nenhum valor adicionado *Padrão do Chrome para `lax` definir | Não definido |

### Target

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Primários | Sem valor adicionado *O padrão do Chrome é a `lax` configuração | Não definido |

### Ad Cloud

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Terceiros | `none` *Somente em navegadores baseados no Google Chrome e Chromo* | Definir, se estiver usando `none` uma solicitação HTTPS |
| data_adcloud | Primários | Sem valor adicionado *O padrão do Chrome é a `lax` configuração | Não definido |
| ev_tm | Terceiros | `none` *Somente em navegadores baseados no Google Chrome e Chromo* | Definir, se estiver usando `none` uma solicitação HTTPS |

### Bizible

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Terceiros | `none` | Seguro |

### Marketo Munchkin

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Cliente primário | Sem valor adicionado *O padrão do Chrome é a `lax` configuração | Configurável para páginas externas |

> !![IMPORTANT] Cookies de terceiros Adobe são definidos no servidor

Para obter mais informações, consulte o documento sobre as políticas [do](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)Público alvo Google Chrome SameSite.