---
description: Contém as configurações de exemplo do servidor e as etapas de migração necessárias.
keywords: Serviço de ID
title: Cenários de migração do serviço de identidade da Experience Cloud
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%

---

# Cenários de migração do serviço de identidade da Experience Cloud {#experience-cloud-id-service-migration-scenarios}

Contém as configurações de exemplo do servidor e as etapas de migração necessárias.

## Propriedade da Web única {#section-6ccfea84628d46c99507cb124e7f5445}

* **Cliente**: Example Company Inc.
* **Experience Cloud ativada**: Não
* **Propriedades da web**: example.com
* **Servidores de coleção de dados**: metrics.example.com, smetrics.example.com
* **Arquivo JavaScript do Analytics**: um único arquivo para todas as páginas do site

Primeiro, este cliente deve ser habilitado para a Experience Cloud (consulte [requisitos](../../reference/requirements.md)). E, como ele tem um único arquivo JavaScript, esse cliente não precisa de um período de carência. Esse cliente também configurará a migração do visitante e sairá de sua coleção de dados CNAME, que não é necessária.

## Vários arquivos JavaScript, tags de imagem embutidas {#section-a665f6ee202940449198e4e7a5dcac54}

* **Cliente**: Another Example Company Inc.
* **Experience Cloud ativada**: Sim
* **Propriedades da web**: anotherexample.com
* **Servidores de coleção de dados**: anotherexampleco.112.2o7.net
* **Arquivo JavaScript do Analytics**: vários arquivos JavaScript. Um arquivo para o site principal, outro arquivo para a seção de suporte que é mantida em um CMS separado.
* **Outros métodos de coleção de dados**: tags de imagem codificadas permanentemente em uma seção do site

Primeiro, esse cliente deve encontrar sua ID da organização da Adobe Experience Cloud (consulte [requisitos](../../reference/requirements.md)). Depois, é necessário configurar um período de carência de migração devido ao uso de vários arquivos JavaScript. Este cliente também irá configurar a migração do visitante e migrar do `*.2o7.net` para o `*.sc.omtrdc.net`.

Quando esse cliente atualizar para a versão mais recente do código JavaScript do Analytics em preparação para a distribuição do serviço da [!DNL Experience Cloud] ID, também será necessário atualizar todas as tags de imagem embutidas em código para usar o JavaScript.

## Várias propriedades da Web, vários arquivos JavaScript e um reprodutor de vídeo baseado em Flash {#section-34647995ff3740b999fdee22d885e515}

* **Cliente**: A Good Customer LLC
* **Experience Cloud ativada**: Sim
* **Propriedades da web**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **Servidores de coleção de dados**: metrics.mymainsite.com, smetrics.mymainsite.com
* **Arquivo JavaScript do Analytics**: vários arquivos JavaScript. Um arquivo para cada propriedade da web.
* **Outros métodos de coleção de dados**: um reprodutor de vídeo baseado em Flash

Primeiro, esse cliente deve encontrar sua ID da organização da Adobe Experience Cloud (consulte [requisitos](../../reference/requirements.md)). Depois, é necessário configurar um período de carência de migração devido ao uso de vários arquivos JavaScript. Esse cliente rastreia os visitantes entre o domínio principal e os subdomínios, portanto, continuará usando o CNAME da coleção de dados com o serviço de ID de visitante.

Quando esse cliente atualiza para a versão mais recente do código JavaScript do Analytics em preparação para a distribuição do serviço da [!DNL Experience Cloud] ID, também será necessário atualizar o player com base em Flash para versão mais recente do AppMeasurement para o Flash.
