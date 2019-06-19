---
description: O serviço de aceitação permite configurar protocolos para o visitante determinar se você pode definir um cookie no dispositivo ou no navegador do usuário ao visitar o site.
seo-description: O serviço de aceitação permite configurar protocolos para o visitante determinar se você pode definir um cookie no dispositivo ou no navegador do usuário ao visitar o site.
seo-title: Serviço de aceitação
title: Serviço de aceitação
uuid: aebd 72 ad -4118-471 b -9755-d 08 a 72 caa 0 fd
translation-type: tm+mt
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b

---


# Serviço de aceitação{#opt-in-service}

O serviço de aceitação permite configurar protocolos para o visitante determinar se você pode definir um cookie no dispositivo ou no navegador do usuário ao visitar o site.

O serviço de aceitação é uma extensão da Experience Cloud ID (ECID), projetada para controlar se e quais soluções da Experience Cloud podem criar cookies em páginas da Web para visitantes antes do consentimento do usuário. O serviço de aceitação também permite definir protocolos para integrar com seu CMP (Application Management Platform) e sistemas existentes como parte do seu design maior.

Usando o serviço de aceitação, você pode especificar se um visitante pode aceitar as soluções da Adobe de uma vez ou apresentar soluções em sequência para permissões. Quando o processo de aprovação é concluído e registrado pelo cliente, você pode recuperar as aprovações do visitante da CMP para todas as soluções da Adobe.

O serviço de aceitação é implementado e configurado facilmente usando [o Adobe Launch](https://docs.adobelaunch.com/) com a extensão [de aceitação](../../implementation-guides/opt-in-service/launch.md). Ele também pode ser implementado e configurado com o [DTM](../../implementation-guides/opt-in-service/optin-dtm.md).

Consulte [Configurar o serviço de aceitação](../../implementation-guides/opt-in-service/getting-started.md) para começar.

>[!NOTE]
>
>O serviço de aceitação permite que você configure um sistema para aprovar ou negar somente os cookies da Adobe. Não fornece suporte para a obtenção das preferência de consentimento do usuário, nem serve como um repositório para as preferências.

>[!IMPORTANT]
>
>O conteúdo deste documento não é um aviso jurídico e não se destina a substituir conselhos legais. Consulte o departamento jurídico da sua empresa para obter aconselhamento e práticas para configurar sua implementação de opt-in.

## Opt-in nas solução da Experience Cloud {#section-053e6224505542cf961896f0ca869e52}

O serviço de aceitação é uma ferramenta para criar um fluxo de trabalho de aceitação de consentimento de acordo com suas próprias necessidades, permitindo que você projete um fluxo de trabalho para reagir (tags de disparo) antes e depois de receber o consentimento do usuário ou do seu controlador de consentimento.

O serviço de aceitação permite configurar as práticas de gerenciamento de consentimento para soluções da Adobe para:

* Indicar se os requisitos de obtenção de consentimento se aplicam no geral para um usuário.
* Especificar quais soluções podem gerar cookies.
* Aplicar preferências padrão às soluções cujas categorias não estão explicitamente consentidas ou negadas pelo usuário.
* Disparar respostas personalizadas com base em alterações nas configurações de consentimento de um usuário, permitindo persistir ou atualizar as configurações do usuário.

Usando os serviços de aceitação, você pode configurar o site para permitir que alguns cookies sejam carregados com pré-consentimento antes da escolha do usuário. Você pode definir serviços de aceitação para novos clientes para permitir que os cookies sejam carregados depois que o usuário é consertado ou depois que uma opção é disponibilizada. Você também pode armazenar e recuperar consentimentos da sua Plataforma de gerenciamento de consentimento ou simplesmente armazenar as permissões de adesão em um cookie.

![](assets/Opt-in-approval.png)

As soluções da Adobe podem verificar se a tag foi aprovada, assinar as alterações e recuperar todos os clientes que aderiram. O serviço de aceitação permite obter permissões diretamente pelas bibliotecas javascript da solução ou por ECID, se implementado.
