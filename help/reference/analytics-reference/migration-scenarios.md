---
description: Contém as configurações de exemplo do servidor e as etapas de migração necessárias.
keywords: Serviço de ID
seo-description: Contém as configurações de exemplo do servidor e as etapas de migração necessárias.
seo-title: Cenários de migração do serviço de identidade da plataforma Experiência
title: Cenários de migração do serviço de identidade da plataforma Experiência
uuid: 9 e 229045-6508-48 c 4-ae 39-9537 b 4941853
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Cenários de migração do serviço de identidade da plataforma Experiência {#experience-cloud-id-service-migration-scenarios}

Contém as configurações de exemplo do servidor e as etapas de migração necessárias.

## Propriedade da Web única {#section-6ccfea84628d46c99507cb124e7f5445}

* **Cliente**: Example Company Inc.
* **Habilitado para Experience Cloud**: não
* **Propriedades da Web**: example.com
* **Servidores de coleta de dados**: metrics.example.com, smetrics.example.com
* **Arquivo JavaScript do Analytics**: um único arquivo para todas as páginas do site

Primeiro, este cliente deve ser habilitado para a Experience Cloud (consulte [exigências](../../reference/requirements.md)). E, como ele tem um único arquivo JavaScript, esse cliente não precisa de um período de carência. Esse cliente também irá configurar a migração do visitante e sair de sua coleta de dados CNAME, que não é necessária.

## Vários arquivos JavaScript, tags de imagem embutidas {#section-a665f6ee202940449198e4e7a5dcac54}

* **Cliente**: Another Example Company Inc.
* **Habilitado para Experience Cloud**: sim
* **Propriedades da Web**: anotherexample.com
* **Servidores de coleta de dados**: anotherexampleco.112.2o7.net
* **Arquivo JavaScript do Analytics**: vários arquivos JavaScript. Um arquivo para o site principal, outro arquivo para a seção de suporte que é mantida em um CMS diferente.
* **Outros métodos de coleta de dados**: tags de imagem embutidas em uma seção do site

Primeiro, esse cliente deve encontrar sua ID da organização da Adobe Experience Cloud (consulte [exigências](../../reference/requirements.md)). Depois, é necessário configurar um período de carência de migração devido ao uso de vários arquivos JavaScript. Este cliente também definirá a migração do visitante e a migração `*.2o7.net``*.sc.omtrdc.net`para.

Quando esse cliente atualizar para a versão mais recente do código JavaScript do Analytics em preparação para a distribuição do serviço da [!DNL Experience Cloud] ID, também será necessário atualizar todas as tags de imagem embutidas em código para usar o JavaScript.

## Várias propriedades da Web, vários arquivos JavaScript e um reprodutor de vídeo baseado em Flash {#section-34647995ff3740b999fdee22d885e515}

* **Cliente**: A Good Customer LLC
* **Habilitado para Experience Cloud**: sim
* **Propriedades da Web**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **Servidores de coleta de dados**: metrics.mymainsite.com, smetrics.mymainsite.com
* **Arquivo JavaScript do Analytics**: vários arquivos JavaScript. Um arquivo para cada propriedade da Web.
* **Outros métodos de coleta de dados**: um reprodutor de vídeo baseado em Flash

Primeiro, esse cliente deve encontrar sua ID da organização da Adobe Experience Cloud (consulte [exigências](../../reference/requirements.md)). Depois, é necessário configurar um período de carência de migração devido ao uso de vários arquivos JavaScript. Como o cliente rastreia os visitantes entre o domínio primário e os subdomínios, ele continuará usando sua coleta de dados CNAME com o serviço de ID de visitante.

Quando esse cliente atualiza para a versão mais recente do código JavaScript do Analytics em preparação para a distribuição do serviço da [!DNL Experience Cloud] ID, também será necessário atualizar o player com base em Flash para versão mais recente do AppMeasurement para o Flash.
