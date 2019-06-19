---
cloud: experience-cloud
product: Serviço de ID
audience: usuário final
user-guide-title: Ajuda do serviço de ID
user-guide-url: /content/help/en/id-service/using/mcvid-home.html
translation-type: tm+mt
source-git-commit: 4dc668afd37cd1d6f9104adb1b102f1dd4c5746e

---


# Ajuda do serviço de ID {#using}

+ [Serviço da Experience Cloud ID](mcvid-home.md)
+ Visão geral {#mcvid-introduction}
   + [Visão geral](mcvid-introduction/mcvid-overview.md)
   + [Sobre o serviço de ID](mcvid-introduction/mcvid-about-id-service.md)
   + [Cookies e o serviço de Experience Cloud ID](mcvid-introduction/mcvid-cookies.md)
   + [Como o serviço da Experience Cloud ID solicita e define IDs](mcvid-introduction/mcvid-id-request.md)
   + [Como entender a sincronização de ID e taxas de correspondência](mcvid-introduction/mcvid-match-rates.md)
+ Guias de implementação {#implementation-guides}
   + [Guias de implementação](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [Métodos de implementação](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [Implementação com o Launch](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [Implementação com o Gerenciamento dinâmico de tags](mcvid-implementation-guides/mcvid-standard.md)
   + [Implementar o serviço da Experience Cloud ID no Analytics](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [Implementar o serviço da Experience Cloud ID no Target](mcvid-implementation-guides/mcvid-setup-target.md)
   + [Implementar o serviço da Experience Cloud ID para o Analytics e o Audience Manager](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [Implementar o serviço da Experience Cloud ID para o Analytics, o Audience Manager e o Target](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [Usar o serviço da Experience Cloud ID com A4T e uma implementação de servidor do Target](mcvid-implementation-guides/ecid-a4t-target.md)
   + [Integração direta com o serviço da Experience Cloud ID](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [Casos de uso da integração direta](mcvid-implementation-guides/mcvid-direct-integration-examples.md)
   + [Testar e verificar o serviço da Experience Cloud ID](mcvid-implementation-guides/mcvid-test-verify.md)
   + Documentação de aceitação {#opt-in-service}
      + [Visão geral do serviço de aceitação](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [Configuração do serviço de aceitação](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [Validação do serviço de aceitação](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuração do Opt-in com o Launch](mcvid-implementation-guides/opt-in-service/launch.md)
      + [Configuração do Opt-in com o DTM](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [Casos de uso de opt-in](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [Referência de opt-in](mcvid-implementation-guides/opt-in-service/api.md)
      + [(beta) Uso de serviços de aceitação com IAB Framework](mcvid-implementation-guides/opt-in-service/iab.md)
+ API do serviço de ID {#id-service-api}
   + [Visão geral da API do serviço de ID](mcvid-library/mcvid-library.md)
   + Configuração {#configurations}
      + [Visão geral das configurações](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer e audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [disableThirdPartyCalls](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain e whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + Métodos {#methods}
      + [Métodos](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (rastreamento entre domínios)](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [Métodos de callTimeOut](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [Sincronização de ID por URL ou fonte de dados](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ Referência {#reference}
   + [Visão geral de referência](mcvid-reference/mcvid-reference.md)
   + Referência do Analytics {#analytics-reference}
      + [Visão geral de referência do Analytics](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [Definição de IDs do Analytics e da Experience Cloud](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Ordem de operação das IDs do Analytics](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Pontos de decisão da migração do serviço da Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Cenários de migração do serviço da Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Solicitações do Analytics e da Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [Coletas de dados CNAMEs e Rastreamento entre domínios](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [Implementação do lado do servidor combinada com JavaScript](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [Período de carência do serviço de ID](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) 
   + [Políticas de segurança de conteúdo e o serviço da Experience Cloud ID](mcvid-reference/mcvid-csp.md)
   + [Suporte para COPPA no serviço de Experience Cloud ID](mcvid-reference/mcvid-coppa.md)
   + [Suporte para CORS no serviço de Experience Cloud ID](mcvid-reference/mcvid-cors.md)
   + [Estados de autenticação e IDs do cliente](mcvid-reference/mcvid-authenticated-state.md)
   + [Métodos de biblioteca ECID em um world do Safari ITP](mcvid-reference/ecid-library-methods.md)
   + [Obter IDs de região e usuário do cookie AMCV ou do serviço de ID](mcvid-reference/mcvid-regions.md)
   + [Requisitos para o serviço de Experience Cloud ID](mcvid-reference/mcvid-requirements.md)
   + [Pulsação de vídeo e o serviço da Experience Cloud ID](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench e o serviço da Experience Cloud ID](mcvid-reference/mcvid-dwb.md)
+ Perguntas frequentes {#faqs}
   + [Visão geral das perguntas frequentes](mcvid-faq-intro/mcvid-faq-intro.md)
   + [Perguntas frequentes do serviço de ID](mcvid-faq-intro/mcvid-faq.md)
   + [Perguntas frequentes do Analytics e do serviço de ID](mcvid-faq-intro/mcvid-analytics-faq.md)
   + [Perguntas frequentes de outras soluções da Experience Cloud](mcvid-faq-intro/mcvid-other-faq.md)
+ Notas de versão do serviço de ID {#release-notes}
   + [Notas de versão de 2019](mcvid-release-notes/mcvid-release-notes.md)
   + [Notas de versão de 2018](mcvid-release-notes/mcvid-notes-2018.md)
   + [Notas de versão de 2017](mcvid-release-notes/mcvid-notes-2017.md)
   + [Notas de versão de 2016](mcvid-release-notes/mcvid-notes-2016.md)
   + [Notas de versão de 2015](mcvid-release-notes/mcvid-notes-2015.md)
