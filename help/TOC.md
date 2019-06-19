---
cloud: platform-cloud
product: Serviço de identidade
audience: usuário final
user-guide-title: Ajuda do Serviço de identidade da Experience Platform
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b

---


# Ajuda do serviço de identidade {#using}

+ [Ajuda do serviço de identidade](home.md)
+ Visão geral {#intro}
   + [Visão geral](introduction/overview.md)
   + [Sobre o serviço de identidade](introduction/about-id-service.md)
   + [Cookies e o serviço de identidade](introduction/cookies.md)
   + [Como o serviço de identidade solicita e define IDs](introduction/id-request.md)
   + [Noções básicas sobre sincronização e taxas de correspondência](introduction/match-rates.md)
+ Guias de implementação {#implementation-guides}
   + [Guias de implementação](implementation-guides/implementation-guides.md)
   + [Métodos de implementação](implementation-guides/implementation-methods.md)
   + [Implementação com o Launch](implementation-guides/ecid-implement-with-launch.md)
   + [Implementação com DTM](implementation-guides/standard.md)
   + [Implementação do Analytics](implementation-guides/setup-analytics.md)
   + [Implementar para o Target](implementation-guides/setup-target.md)
   + [Implementação do Analytics e do Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementação do Analytics, do Audience Manager e do Target](implementation-guides/setup-aam-analytics-target.md)
   + [Uso do Serviço de identidade com A 4 T e uma implementação do lado do servidor do Target](implementation-guides/ecid-a4t-target.md)
   + [Integração direta com o serviço de identidade](implementation-guides/direct-integration.md)
   + [Casos de uso da integração direta](implementation-guides/direct-integration-examples.md)
   + [Testar e verificar o serviço de identidade](implementation-guides/test-verify.md)
   + Documentação de aceitação {#opt-in-service}
      + [Visão geral do serviço de aceitação](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuração do serviço de aceitação](implementation-guides/opt-in-service/getting-started.md)
      + [Validação do serviço de aceitação](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuração do Opt-in com o Launch](implementation-guides/opt-in-service/launch.md)
      + [Configuração do Opt-in com o DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Casos de uso de opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Referência de opt-in](implementation-guides/opt-in-service/api.md)
      + [(beta) Uso de serviços de aceitação com IAB Framework](implementation-guides/opt-in-service/iab.md)
+ API de serviço de identidade {#id-service-api}
   + [Visão geral da API de serviço de identidade](library/library.md)
   + Configuração {#configurations}
      + [Visão geral das configurações](library/function-vars/function-vars.md)
      + [audienceManagerServer e audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [isCoopSafe](library/function-vars/coopsafe.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain e whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + Métodos {#methods}
      + [Métodos](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (rastreamento entre domínios)](library/get-set/appendvisitorid.md)
      + [Métodos de callTimeOut](library/get-set/timeout-functions.md)
      + [Sincronização de ID por URL ou fonte de dados](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ Referência {#reference}
   + [Visão geral de referência](reference/reference.md)
   + Referência do Analytics {#analytics-reference}
      + [Visão geral de referência do Analytics](reference/analytics-reference/analytics-reference.md)
      + [Definição de IDs do Analytics e da Experience Cloud](reference/analytics-reference/analytics-ids.md)
      + [Ordem de operação das IDs do Analytics](reference/analytics-reference/analytics-order-of-operations.md)
      + [Pontos de decisão de migração do serviço de identidade](reference/analytics-reference/migration-decisions.md)
      + [Cenários de migração do serviço de identidade](reference/analytics-reference/migration-scenarios.md)
      + [Análises e solicitações de identidade](reference/analytics-reference/legacy-analytics.md)
      + [Coletas de dados CNAMEs e Rastreamento entre domínios](reference/analytics-reference/cname.md)
      + [Implementação do lado do servidor combinada com JavaScript](reference/analytics-reference/server-side.md)
      + [Período de carência do serviço de identidade](reference/analytics-reference/grace-period.md)
   + [Políticas de segurança de conteúdo e serviço de identidade](reference/csp.md)
   + [Suporte à lei COPPA no serviço de identidade](reference/coppa.md)
   + [Suporte ao CORS no serviço de identidade](reference/cors.md)
   + [Estados de autenticação e IDs do cliente](reference/authenticated-state.md)
   + [Métodos de biblioteca ECID em um world do Safari ITP](reference/ecid-library-methods.md)
   + [Obter as IDs de região e de usuário do cookie AMCV ou do serviço de identidade](reference/regions.md)
   + [Requisitos para o serviço de identidade](reference/requirements.md)
   + [Video Heartbeat e o serviço de identidade](reference/heartbeat.md)
   + [Análise de big data e serviço de identidade](reference/dwb.md)
+ Perguntas frequentes {#faqs}
   + [Visão geral das perguntas frequentes](faq-intro/faq-intro.md)
   + [Perguntas frequentes do serviço de identidade](faq-intro/faq.md)
   + [Perguntas frequentes sobre o serviço de identidade e do Analytics](faq-intro/analytics-faq.md)
   + [Perguntas frequentes de outras soluções da Experience Cloud](faq-intro/other-faq.md)
+ Notas de versão do Serviço de identidade {#release-notes}
   + [Notas de versão de 2019](release-notes/release-notes.md)
   + [Notas de versão de 2018](release-notes/notes-2018.md)
   + [Notas de versão de 2017](release-notes/notes-2017.md)
   + [Notas de versão de 2016](release-notes/notes-2016.md)
   + [Notas de versão de 2015](release-notes/notes-2015.md)
