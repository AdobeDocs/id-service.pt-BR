---
audience: end-user
user-guide-title: Ajuda do serviço de identidade da Experience Cloud
breadcrumb-title: Guia do Identity Service
user-guide-description: O Serviço de identidade da Adobe Experience Cloud fornece uma ID contínua e universal que identifica seus visitantes em todas as soluções da Experience Cloud. Ele ajuda a substituir o código de geração de ID herdado para soluções e serviços da Experience Cloud.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 6ef86bdb7bc10e24dbd3efe2481cb2e6e6c270fb
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 100%

---


# Ajuda do serviço de identidade da Experience Cloud {#using}

+ [Ajuda do Serviço de identidade](home.md)
+ Visão geral {#intro}
   + [Visão geral](introduction/overview.md)
   + [Sobre o serviço de ID](introduction/about-id-service.md)
   + [Cookies e o serviço de ID](introduction/cookies.md)
   + [Como o serviço de ID solicita e define IDs](introduction/id-request.md)
   + [Como entender a sincronização e taxas de correspondência](introduction/match-rates.md)
+ Implementação {#implementation}
   + [Métodos de implementação](implementation-guides/implementation-methods.md)
   + [Guias de implementação](implementation-guides/implementation-guides.md)
   + [Implementar com as tags da Experience Platform](implementation-guides/ecid-implement-with-launch.md)
   + [Implementar para o Analytics](implementation-guides/setup-analytics.md)
   + [Implementar para o Target](implementation-guides/setup-target.md)
   + [Implementar para o Analytics e o Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementar para o Analytics, Audience Manager e Target](implementation-guides/setup-aam-analytics-target.md)
   + [Usar o serviço de ID com o A4T e uma implementação do lado do servidor do Target](implementation-guides/ecid-a4t-target.md)
   + [Integração direta com o serviço de ID](implementation-guides/direct-integration.md)
   + [Casos de uso da integração direta](implementation-guides/direct-integration-examples.md)
   + [Teste e verifique o serviço de ID](implementation-guides/test-verify.md)
   + Serviço de Opt-in {#opt-in-service}
      + [Visão geral do serviço de Opt-in](implementation-guides/opt-in-service/optin-overview.md)
      + [Configuração do serviço de Opt-in](implementation-guides/opt-in-service/getting-started.md)
      + [Validação do serviço de Opt-in](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Configuração do Opt-in com a Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Configuração do Opt-in com o DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Controlar atividades da Experience Cloud com base no consentimento do usuário](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Casos de uso de Opt-in](implementation-guides/opt-in-service/use-cases.md)
      + [Referência de Opt-in](implementation-guides/opt-in-service/api.md)
      + [Utilização dos serviços de Opt-in com a Estrutura IAB](implementation-guides/opt-in-service/iab.md)
+ API do serviço de ID {#id-service-api}
   + [Visão geral da API do serviço de ID](library/library.md)
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
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [Configurações de Secure e SameSite](library/function-vars/secure-samesite-config.md)
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
   + [Visão geral da referência](reference/reference.md)
   + Referência do Analytics {#analytics-reference}
      + [Visão geral da referência do Analytics](reference/analytics-reference/analytics-reference.md)
      + [Visão geral da implementação de CNAME](reference/analytics-reference/cname.md)
      + [Definir Analytics e Experience Cloud IDs](reference/analytics-reference/analytics-ids.md)
      + [Ordem de operação das IDs do Analytics](reference/analytics-reference/analytics-order-of-operations.md)
      + [Pontos de decisão da migração do serviço de ID](reference/analytics-reference/migration-decisions.md)
      + [Cenários de migração do serviço de ID](reference/analytics-reference/migration-scenarios.md)
      + [Solicitações do Analytics e de Identidade](reference/analytics-reference/legacy-analytics.md)
      + [Implementação do lado do servidor combinada com JavaScript](reference/analytics-reference/server-side.md)
      + [Período de carência do serviço de ID](reference/analytics-reference/grace-period.md)
   + [Alterações na rotulagem do SameSite no Google Chrome](reference/chrome-samesite-labelling.md)
   + [Políticas de segurança de conteúdo e o serviço de ID](reference/csp.md)
   + [Suporte para COPPA no serviço de ID](reference/coppa.md)
   + [Suporte para CORS no serviço de ID](reference/cors.md)
   + [Estados de autenticação e IDs do cliente](reference/authenticated-state.md)
   + [Métodos de biblioteca da ECID em um mundo de ITP do Safari](reference/ecid-library-methods.md)
   + [Identificação dos visitantes únicos](reference/unique-vis-method.md)
   + [Obter as IDs de região e usuário do cookie AMCV ou do serviço de ID](reference/regions.md)
   + [Requisitos para o serviço de ID](reference/requirements.md)
   + [Video Heartbeat e o serviço de ID](reference/heartbeat.md)
   + [Data Workbench e o serviço de ID](reference/dwb.md)
   + [Suporte a hash SHA-256 para setCustomerIDs](reference/hashing-support.md)
+ Perguntas frequentes {#faqs}
   + [Visão geral das perguntas frequentes](faq-intro/faq-intro.md)
   + [Perguntas frequentes sobre o serviço de ID](faq-intro/faq.md)
   + [Perguntas frequentes do Analytics e do serviço de ID](faq-intro/analytics-faq.md)
   + [Perguntas frequentes de outras soluções da Experience Cloud](faq-intro/other-faq.md)
+ Notas de versão do serviço de ID {#release-notes}
   + [Notas de versão de 2022](release-notes/notes-2022.md)
   + [Notas de versão de 2021](release-notes/notes-2021.md)
   + [Notas de versão de 2020](release-notes/notes-2020.md)
   + [Notas de versão de 2019](release-notes/notes-2019.md)
   + [Notas de versão de 2018](release-notes/notes-2018.md)
   + [Notas de versão de 2017](release-notes/notes-2017.md)
   + [Notas de versão de 2016](release-notes/notes-2016.md)
   + [Notas de versão de 2015](release-notes/notes-2015.md)
+ [Teste de análise oculto do sumário](analytics-test-file-hidetoc.md)
