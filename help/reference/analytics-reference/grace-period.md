---
description: Caso tenha vários arquivos JavaScript que enviam dados para o mesmo conjunto de relatórios, ou se estiver usando outras tecnologias no seu site, como a medição de vídeo Flash, recomendamos configurar um período de carência.
keywords: Serviço de ID
title: Período de carência do serviço de ID
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '417'
ht-degree: 100%

---

# Período de carência do serviço de ID {#the-id-service-grace-period}

Caso tenha vários arquivos JavaScript que enviam dados para o mesmo conjunto de relatórios, ou se estiver usando outras tecnologias no seu site, como a medição de vídeo Flash, recomendamos configurar um período de carência.

Depois de implantar o serviço da [!DNL Experience Cloud] ID, os novos visitantes não recebem uma ID de visitante do Analytics de um servidor de coleta de dados. Se as seções no seu site ainda não implementaram o serviço da [!DNL Experience Cloud] ID, quando os visitantes navegam até essas seções, a Experience Cloud ID não é reconhecida e os visitantes recebem uma ID de visitante herdada do Analytics. Isso pode criar contagens de visitas duplicadas e atribuição incorreta.

Por exemplo, se a seção de suporte do seu site for gerenciada em um CMS diferente, você terá um arquivo JavaScript do Analytics diferente para essa seção. Se você implantar a ID de visitante no site principal antes de implantar o serviço de ID de visitante no site de suporte, os novos visitantes receberão uma ID do Analytics herdada quando visitarem a seção de suporte, e as visitas que abrangerem ambas as seções do site serão relatadas como visitas diferentes.

A implantação do serviço da [!DNL Experience Cloud] ID nos sites que usam diversos arquivos JavaScript ou outras tecnologias (como Flash) pode causar problemas de coordenação, pois é necessário habilitar o serviço de ID em todas as partes do site ao mesmo tempo. Ao configurar um período de carência, os novos visitantes continuam a receber uma ID de visitante do Analytics pelo serviço da [!DNL Experience Cloud], portanto, os visitantes podem ser identificados consistentemente em seções do site que não foram atualizadas para usar o serviço de ID.

>[!NOTE]
>
>O suporte do período de carência exige a versão 1.3 ou posterior do serviço de ID [!DNL Experience Cloud].

## Eu preciso de um período de carência? {#section-fd34c7ff697348a39f49258b7d39eb42}

Se você tiver um único arquivo JavaScript do Analytics e não estiver usando outras bibliotecas do AppMeasurement, não será preciso um período de carência. Você pode efetuar a atualização no único arquivo JavaScript, e os novos visitantes serão continuamente identificados usando a Experience Cloud ID durante a visita.

Caso tenha vários arquivos JavaScript que enviam dados para o *mesmo conjunto de relatórios* ou se estiver usando outras tecnologias no seu site, como a medição de vídeo Flash, recomendamos configurar um período de carência

## Como ativar o período de carência? {#section-512d5cd8570e483cbdd8b04457a16ced}

Entre em contato com o [Atendimento ao cliente](https://helpx.adobe.com/br/marketing-cloud/contact-support.html).
