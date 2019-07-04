---
description: O serviço de Opt-in permite configurar os protocolos para o visitante a fim de determinar se você pode adicionar um cookie no dispositivo ou no navegador do usuário quando ele visitar o site.
seo-description: O serviço de Opt-in permite configurar os protocolos para o visitante a fim de determinar se você pode adicionar um cookie no dispositivo ou no navegador do usuário quando ele visitar o site.
seo-title: Serviço de Opt-in
title: Serviço de Opt-in
uuid: aebd72ad-4118-471b-9755-d08a72caa0fd
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Serviço de Opt-in{#opt-in-service}

O serviço de Opt-in permite configurar os protocolos para o visitante a fim de determinar se você pode adicionar um cookie no dispositivo ou no navegador do usuário quando ele visitar o site.

O serviço de Opt-in é uma extensão do serviço da [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/pt_BR/mcvid/) desenvolvido para permitir controlar se e quais soluções da Experience Cloud podem criar cookies nas páginas da web para os visitantes ante do consentimento do usuário. O serviço de Opt-in também permite configurar protocolos para integração com a sua Plataforma de gerenciamento de consentimento (CMP) e sistemas existentes como parte do projeto geral.

Usando o serviço de Opt-in, você pode especificar se um visitante pode aderir às soluções da Adobe de uma só vez ou apresentar as soluções em sequência para fornecer permissões. Quando o processo de aprovação é concluído e registrado pelo cliente, você pode recuperar as aprovações do visitante da CMP para todas as soluções da Adobe.

O serviço de Opt-in é implementado e configurado facilmente usando o [Adobe Launch](https://docs.adobelaunch.com/) com a [extensão de Opt-in](../../mcvid-implementation-guides/opt-in-service/launch.md). Também pode ser implementado e configurado usando o [DTM](../../mcvid-implementation-guides/opt-in-service/optin-dtm.md).

Consulte a [Configuração do serviço de Opt-in](../../mcvid-implementation-guides/opt-in-service/getting-started.md) para começar.

>[!NOTE]
>
>O serviço de Opt-in permite definir um sistema para aprovar ou negar o download dos cookies da Adobe somente. Não fornece suporte para a obtenção das preferência de consentimento do usuário, nem serve como um repositório para as preferências.

>[!IMPORTANT]
>
>O conteúdo deste documento não é um aconselhamento jurídico e não se destina a substituir tal aconselhamento. Consulte o departamento jurídico da sua empresa para obter aconselhamento e práticas para configurar sua implementação de opt-in.

## Opt-in nas solução da Experience Cloud {#section-053e6224505542cf961896f0ca869e52}

O serviço de Opt-in é uma ferramenta usada para criar um fluxo de trabalho de adesão ao consentimento de acordo com as suas necessidades e permite projetar um fluxo de trabalho para reagir (disparar tags) antes e depois da obtenção do consentimento do usuário ou do controlador de consentimento.

O serviço de Opt-In permite definir práticas de gerenciamento de consentimento para as soluções da Adobe para:

* Indicar se os requisitos de obtenção de consentimento se aplicam no geral para um usuário.
* Especificar quais soluções podem gerar cookies.
* Aplicar preferências padrão às soluções cujas categorias não estão explicitamente consentidas ou negadas pelo usuário.
* Disparar respostas personalizadas com base em alterações nas configurações de consentimento de um usuário, permitindo persistir ou atualizar as configurações do usuário.

Usando o serviço de Opt-in, você pode configurar o site para permitir que alguns cookies sejam carregados com pré-consentimento antes da escolha do usuário. Você pode definir serviços de Opt-in para novos clientes para permitir o carregamento de cookies após a obtenção do consentimento do usuário ou após a disponibilização de uma escolha. Você também pode armazenar e recuperar consentimentos da sua Plataforma de gerenciamento de consentimento ou simplesmente armazenar as permissões de adesão em um cookie.

![](assets/Opt-in-approval.png)

As soluções da Adobe podem verificar se a tag foi aprovada, assinar as alterações e recuperar todos os clientes que aderiram. O serviço de Opt-in permite obter as permissões diretamente das bibliotecas JavaScript da solução ou pela ECID, se tiver sido implementada.
