---
description: Antes de implantar o serviço da Experience Cloud ID, você deve entender como esse serviço afeta o rastreamento do visitante em vários domínios e problemas potenciais se você estiver coletando dados com métodos diferentes ou por meio de arquivos javascript.
keywords: Serviço de ID
seo-description: Antes de implantar o serviço da Experience Cloud ID, você deve entender como esse serviço afeta o rastreamento do visitante em vários domínios e problemas potenciais se você estiver coletando dados com métodos diferentes ou por meio de arquivos javascript.
seo-title: Pontos de decisão da migração do serviço da Experience Cloud ID
title: Pontos de decisão da migração do serviço da Experience Cloud ID
uuid: ee 56 b 5 de-fcf 3-4 cfb -9 e 53-762 af 7 c 4 ff 2 ff
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Pontos de decisão da migração do serviço da Experience Cloud ID

Antes de implantar o serviço da Experience Cloud ID, você deve entender como esse serviço afeta o rastreamento do visitante em vários domínios e problemas potenciais se você estiver coletando dados com métodos diferentes ou por meio de arquivos javascript.

As respostas às perguntas desta seção ajudam a determinar as etapas de migração adicionais que devem ser realizadas.

## Você possui uma coleta de dados CNAME?

Muitos clientes podem migrar de uma coleta de dados CNAME como parte da migração do serviço de ID.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Método de coleta de dados </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Com um CNAME </p> </td> 
   <td colname="col2"> <p>Veja a próxima pergunta para decidir se deve migrar de uma coleta de dados CNAME. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Sem um CNAME </p> </td> 
   <td colname="col2"> <p>Pule para <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">Caso não tenha uma coleta de dados CNAME, seu servidor de coleta de dados é o *.2o7.net ou o *.sc.omtrdc.net?</a> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Caso tenha uma coleta de dados CNAME, você possui vários domínios?

Se você tem vários domínios que enviam dados para o *mesmo conjunto de relatórios*, então recomendamos a coleta de dados com um CNAME. Isso ajuda a rastrear visitantes por domínios. Se você estiver coletando dados em um único domínio, não há vantagem em manter uma coleta de dados CNAME.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Coleta de dados de </th> 
   <th colname="col2" class="entry"> Descrição </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>vários domínios </p> </td> 
   <td colname="col2"> <p>Se estiver rastreando visitantes em vários domínios e também possuir um site principal no qual os clientes podem ser identificados antes de visitar outros domínios, continue usando sua coleta de dados CNAME. Consulte <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">Coletas de dados CNAME e rastreamento entre domínios</a> para obter uma explicação detalhada. </p> <p>Observe que você deve especificar mais dois parâmetros de servidor de rastreamento, <span class="codeph">visitor.marketingCloudServer</span> e <span class="codeph">visitor.marketingCloudServerSecure</span>, para configurar um CNAME com o serviço de ID. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Domínio único </p> </td> 
   <td colname="col2"> <p>Trabalhar com um domínio único significa poder migrar de um CNAME de coleta de dados se não desejar mais gerenciá-lo. No entanto, não há necessidade de realizar essa alteração se o CNAME estiver funcionando. </p> <p>Caso remova o CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Certifique-se de que o novo servidor de rastreamento é <a href="https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/" format="https" scope="external">compatível com o RDC</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Mude de CNAME para um servidor de rastreamento de RDC alguns meses antes da migração para o serviço da <span class="keyword">Experience Cloud</span> ID. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>Não</i> use um servidor de rastreamento <span class="codeph">*.2o7.net</span>. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Entre em contato com o <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external">Atendimento ao cliente</a> para configurar uma migração de visitante. Isso ajuda a garantir contagens consistentes dos visitantes. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Você possui vários arquivos JavaScript do Analytics, ou está rastreando aplicativos ou vídeos Flash?

Se você tiver diversos arquivos JavaScript do Analytics, ou aplicativos Flash ou vídeos em seu site enviando dados para o *mesmo conjunto de relatórios*, é necessário configurar um período de carência para que os visitantes continuem a ser identificados por uma Analytics ID enquanto distribuem o serviço da [!DNL Experience Cloud] ID.

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Coleta de dados com </th> 
   <th colname="col2" class="entry"> Ações necessárias </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Vários arquivos JavaScript do Analytics </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Outros métodos de coleta de dados </li> 
    </ul> </td> 
   <td colname="col2"> <p>Configure um período de carência do serviço de ID de visitante para que possa executar o serviço de ID de visitante em cada arquivo JavaScript e em outras bibliotecas de coleta de dados. See <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> ID Service Grace Period</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Arquivo único JavaScript do Analytics </p> </td> 
   <td colname="col2"> <p>Você pode atualizar seu único arquivo de JavaScript para usar o serviço de ID de visitante sem um período de carência. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Você usa métodos de coleta de dados não compatíveis?

Talvez seja necessário atualizar a maneira de rastrear links ou sair do Silverlight.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Método de coleta de dados </th> 
   <th colname="col2" class="entry"> Ações necessárias </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript e/ou Flash </p> </td> 
   <td colname="col2"> <p>Nenhum. O serviço da <span class="keyword">Experience Cloud</span> ID oferece suporte a esses métodos de coleta de dados. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>É necessário migrar do Silverlight se os visitantes conseguirem acessar o conteúdo do Silverlight e outras seções do seu site que usam o serviço da <span class="keyword">Experience Cloud</span> ID. O Silverlight não é compatível com o serviço de ID. </p> <p> Caso esteja rastreando um reprodutor de vídeo baseado no Silverlight, o fornecedor provavelmente disponibilizará APIs de JavaScript capazes de substituí-lo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Tags de imagem codificadas permanentemente </p> </td> 
   <td colname="col2"> <p>Atualize links codificados permanentemente para usar o JavaScript. </p> </td> 
  </tr> 
 </tbody> 
</table>

