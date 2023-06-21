---
title: Alterações na rotulagem do Google Chrome SameSite
description: Documentação da biblioteca da Adobe ECID (serviço de ID).
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
source-git-commit: ee4b7f8df5766372034da2a76e7acb81ba2a65f0
workflow-type: ht
source-wordcount: '1064'
ht-degree: 100%

---

# Alterações na rotulagem do SameSite no Google Chrome {#google-chrome-samesite-labelling-changes}

O atributo SameSite informa aos navegadores quando e como acionar cookies em cenários originais e de terceiros. O atributo SameSite pode ter um de três valores: `strict`, `lax`ou `none`. Chrome, Firefox, Edge, Safari e Opera são compatíveis com `strict` e com `lax` desde novembro de 2017, enquanto `none` foi introduzido em 2018. No entanto, alguns navegadores mais antigos não são compatíveis com essa configuração.

Em fevereiro de 2020, o Google lançou o Chrome 80 e alterou a configuração padrão de `none` para `lax` quando um cookie não tem um valor de atributo SameSite especificado. Essa configuração impede que um cookie seja usado em um contexto de terceiros, também conhecido como &quot;entre sites&quot;. Todos os cookies de terceiros subsequentes devem ser definidos como `SameSite=none` e rotulados como seguros.

Os cookies sem um valor de atributo SameSite especificado assumirão `lax` como padrão.

Visite o [documento padrão de cookie](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) para mais informações sobre os atributos do SameSite.

## Valores de atributo do SameSite

| Valor de atributo do SameSite | Descrições |
| ------ | ------------ |
| `strict` | Os cookies com essa configuração só são enviados quando a página de referência e a página de destino fazem parte do mesmo domínio que o cookie. |
| `lax` | Os cookies com essa configuração só são enviados quando o domínio exibido no URL do navegador corresponde ao domínio do cookie. Este é o novo padrão para cookies no Chrome. |
| `none` | Os cookies com essa configuração estão disponíveis para acesso externo ou de terceiros, como “entre sites”. Antes dessa alteração, `none` era a configuração padrão do SameSite para cookies, ou seja, usar essa configuração faz com que um cookie se comporte de forma mais semelhante à forma tradicional. No entanto, o Google exige que qualquer cookie com essa configuração agora especifique o sinalizador seguro, significando que o cookie só será criado e enviado com solicitações em HTTPS. Todos os cookies entre sites sem o sinalizador seguro serão rejeitados pelo Google. |

## O que você precisa saber como cliente da Adobe Experience Cloud

**Não é necessária nenhuma atualização do JavaScript**

A Adobe já lançou atualizações do lado do servidor para definir cookies de terceiros com atributos apropriados. Não são necessárias atualizações da biblioteca JavaScript para nossos clientes.

**Verifique se os pontos de extremidade de terceiros usam HTTPS**

Todos os clientes do Analytics devem confirmar se a configuração JavaScript usa HTTPS para as chamadas com os serviços da Adobe. O Target, o Audience Manager e o Experience Cloud Identity Service (ECID) redirecionam chamadas HTTP de terceiros para seus respectivos pontos de extremidade HTTPS, o que pode aumentar a latência. Isso significa que você não precisa alterar sua configuração. Os clientes do Analytics devem atualizar suas implementações para usar exclusivamente HTTPS, já que os redirecionamentos específicos do Analytics podem causar perda de dados.

**Cookies rotulados corretamente devem coletar dados conforme planejado**

Desde que os cookies estejam rotulados corretamente, os navegadores não executarão nenhuma ação para bloqueá-los. Os clientes terão a opção de bloquear determinados tipos de cookies, mas atualmente essa opção parece ser apenas uma configuração de aceitação.

**Cookies de terceiros existentes sem os rótulos atualizados serão ignorados**

Cookies de terceiros que foram criados antes do Chrome 80 começar a aplicar as configurações de SameSite=`none` e sinalizadores seguros serão ignorados pelo Chrome 80 se esses sinalizadores não estiverem presentes.

Muitos dos cookies de terceiros existentes da Adobe não têm esses sinalizadores e precisarão ser atualizados pelos servidores Edge antes que os usuários atualizem para o Chrome 80 ou eles serão perdidos. A atualização dos servidores Edge ocorre automaticamente quando os usuários visitam qualquer site onde o cookie é usado.

A maioria dos produtos da Adobe já tem os sinalizadores apropriados atribuídos aos cookies. A exceção são implementações do Analytics que usam coleta de dados de terceiros e não usam o ECID. Os clientes podem presenciar um pequeno aumento temporário em novos visitantes, que caso contrário seriam visitantes recorrentes.

**Possível diminuição da correspondência de cookies para parceiros de destino e de marketplace (somente Audience Manager)**

Embora tenha o controle sobre a atualização dos próprios cookies, a Adobe não pode forçar os parceiros a fazer as alterações necessárias. A correspondência de cookies pode diminuir para clientes do Audience Manager que usam parceiros de destino ou parceiros de marketplace que não fizeram essas atualizações.

**Cookies de terceiros compatíveis com o Analytics (somente cookies `s_vi` do Analytics)**

Algumas implementações do Analytics usam um codinome CNAME do Analytics para permitir a criação do cookie `s_vi` no domínio desse CNAME. Se o CNAME estiver no mesmo domínio do site, ele será designado como um cookie primário. No entanto, se você tiver vários domínios e usar o mesmo CNAME para a coleta de dados em todos, ele será tratado como um cookie de terceiros nesses outros.

Com o `lax` sendo a nova configuração padrão SameSite no Chrome, o CNAME não fica mais visível em outros domínios.

Para acomodar a alteração, o Analytics agora define explicitamente o valor do SameSite do cookie `s_vi` como `lax`. Para usar esse cookie em um contexto amigável de terceiros, defina o valor do SameSite como `none`, o que significa que sempre deve usar HTTPS. Entre em contato com o Atendimento ao cliente para alterar o valor do SameSite dos CNAMEs protegidos.

>[!IMPORTANT]
>
>Essa ação não é necessária para clientes do Analytics que usam ECID, clientes que usam um CNAME separado para cada um de seus domínios ou clientes que usam somente a coleta de dados de terceiros do Analytics.

## Cookies de visitante padrão da Adobe

Somente os cookies padrão comuns de visitante estão listados na tabela abaixo. Para configurações de cookies adicionais, consulte a documentação específica do produto ou entre em contato com o representante da Adobe.

### ECID

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Primário do lado do cliente | Sem valor adicionado *O padrão do Chrome é a configuração `lax` | Configurável |
| AMCVS_###@AdobeOrg | Primário do lado do cliente | Sem valor adicionado *O padrão do Chrome é a configuração `lax` | Configurável |
| s_ecid | Primário do lado do servidor | SameSite==`lax` | Não definido |

### Audience Manager

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Terceiros | `none` | Definir para proteger |
| Dextp | Terceiro | `none` | Definir para proteger |

### Analytics

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Primário do lado do servidor se usar `CNAME` </li> <li>Terceiros se usar 2o7.net ou omtrdc.net</li></ul> | <ul><li>`lax` se primário</li> <li>`none` se de terceiros</li></ul> *Os clientes podem editar a configuração por meio do ticket do Atendimento ao cliente para domínios primários* | Definir, se usar `none` e uma solicitação HTTPS |
| s_fid | Primário do lado do cliente | Nenhum valor adicionado *Padrão do Chrome para definir `lax` | Não definido |

### Target

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Primários | Sem valor adicionado *O padrão do Chrome é a configuração `lax` | Não definido |

### Ad Cloud

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Terceiros | `none` *Somente em navegadores baseados no Google Chrome e Chromium* | Definir, se usar `none` e uma solicitação HTTPS |
| data_adcloud | Primários | Sem valor adicionado *O padrão do Chrome é a configuração `lax` | Não definido |
| ev_tm | Terceiros | `none` *Somente em navegadores baseados no Google Chrome e Chromium* | Definir, se usar `none` e uma solicitação HTTPS |

### Bizible

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Terceiros | `none` | Seguro |

### Marketo Munchkin

| Cookie | Tipo | Atributo SameSite | Atributo seguro |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Primário do lado do cliente | Sem valor adicionado *O padrão do Chrome é a configuração `lax` | Configurável para páginas externas |

>  Cookies de terceiros da Adobe são definidos no lado do servidor.

Para mais informações, consulte o documento sobre as [Políticas do SameSite do Google Chrome no Target](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/google-chrome-samesite-cookie-policies.html?lang=pt-BR).
