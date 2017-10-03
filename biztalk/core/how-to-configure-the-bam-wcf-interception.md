---
title: "Comment configurer l’Interception WCF BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85aa130-3219-4df1-8974-a44a51a15002
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e90577a73abc0291635bf4b7d9bad34a11d1f806
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-bam-wcf-interception"></a>Configuration de l'interception WCF BAM
Pour configurer l'analyse BAM pour l'interception WCF, vous devez modifier le fichier de configuration de l'intercepteur de manière à ce qu'il puisse accéder au manifeste d'assembly correspondant à vos sources d'événements.  
  
 Lorsque vous configurez les événements, vous devez spécifier correctement mis en forme [XPath](../core/xpath.md) expressions pour les actions.  
  
 Vous pouvez créer correctement mis en forme [XPath](../core/xpath.md) expressions à utiliser dans la configuration de l’intercepteur en activant le suivi WCF et l’application en cours d’exécution pour générer un exemple de journal WCF qui contient le message. Vous pouvez utiliser la **Microsoft Service Trace Viewer** (SvcTraceViewer.exe) pour afficher le journal et extraire le message. Cet outil est inclus dans le Kit de développement WCF SDK. L’élément [XPath](../core/xpath.md) expression peut être formée en fonction du message et appliquée à la configuration de l’intercepteur.  
  
 Lors de la configuration de l'interception WCF de l'analyse BAM, il est essentiel que l'extension de comportement utilisée dans le fichier machine.config corresponde à celle utilisée dans la configuration de comportement personnalisée de l'emplacement de réception. La modification du nom d'extension d'un emplacement de réception configuré dans le fichier machine.config provoque l'échec du chargement du comportement. En outre, l'interface utilisateur de configuration de l'emplacement de réception échouera également.  
  
 Dans un scénario de mise en cluster, le comportement personnalisé n'est configuré qu'une seule fois. Vous devez alors veiller à ce que tous les fichiers machine.config sur les ordinateurs du cluster indiquent une extension de nom de fichier identique.  
  
### <a name="to-set-the-manifest"></a>Pour définir le manifeste  
  
1.  Pour la propriété EventSource de la configuration de l'interception, définissez le manifeste comme suit : « Microsoft.BizTalk.Adapter.Wcf.Runtime.ITwoWayAsyncVoid, Microsoft.BizTalk.Adapter.Wcf.Runtime, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 ».  
  
    > [!NOTE]
    >  L'interface est alors modifiée en fonction du type de service/port de réception utilisé. D'après le tableau suivant, modifiez la ligne concernant le manifeste de manière à refléter le type de port que vous utilisez :  
  
    |Type de port|Utiliser|  
    |---------------|---------|  
    |Ports bidirectionnels|ITwoWayAsync|  
    |Ports unidirectionnels avec une liaison qui est, par nature, bidirectionnelle (par exemple, HTTP).|ITwoWayAsyncVoid|  
    |Ports unidirectionnels avec une liaison qui est, par nature, bidirectionnelle avec transactions.|ITwoWayAsyncVoidTxn|  
    |Liaisons unidirectionnelles (par exemple, MSMQ).|IOneWayAsync|  
    |Liaisons unidirectionnelles avec transactions.|IOneWayAsyncTxn|  
  
    > [!IMPORTANT]
    >  Dans le filtre, au lieu d’utiliser le [GetOperationName](../core/getoperationname.md) opération, utilisez l’opération XPath en surbrillance dans l’exemple suivant. Pour les contrats génériques, tous les messages parviennent à une opération générique, à partir de laquelle ils sont acheminés vers des opérations particulières sur la base du message lui-même (attribut Action).  
  
2.  À ce stade, le nom de l'opération est toujours le même. Pour les adaptateurs WCF (lesquels utilisent des contrats génériques), la méthode utilisée est BizTalkSubmit. Pour extraire le nom de l'opération, vous pouvez utiliser une opération XPath pour le nœud Action au lieu d'employer l'opération GetOperationName. Vous pouvez ensuite filtrer sur le nom de l'opération.  
  
## <a name="sample-interceptor-configurations"></a>Exemple de configurations de l'intercepteur  
 Cet exemple illustre l'utilisation de ServiceRequest et de ServiceReply pour l'adaptateur WCF. Dans la section en surbrillance une [XPath](../core/xpath.md) expression de l’Action est utilisée pour filtrer sur l’opération au lieu d’utiliser [GetOperationName](../core/getoperationname.md). Vous pouvez également filtrer sur la réponse, mais uniquement pour ITwoWayAsync. Toutes les autres interfaces ne renvoient rien ou renvoient void.  
  
### <a name="servicerequest"></a>ServiceRequest  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="WCFServiceRequest" Source="WCFService">  
      <ic:Filter>  
        <ic:Expression>  
          <wcf:Operation Name="GetServiceContractCallPoint"/>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>ServiceRequest</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
          <wcf:Operation Name ="XPath">  
            <wcf:Argument>//s:Header/a:Action</wcf:Argument>  
          </wcf:Operation>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>Operation1</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
          <ic:Operation Name ="And" />  
        </ic:Expression>  
      </ic:Filter>  
  
      <ic:CorrelationID>  
        <ic:Expression>  
          <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
        </ic:Expression>  
      </ic:CorrelationID>  
  
      <ic:Update DataItemName ="Activity Date" Type ="DATETIME">  
        <ic:Expression>  
          <wcf:Operation Name ="GetContextProperty">  
            <wcf:Argument>EventTime</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
      <ic:Update DataItemName ="Source" Type ="NVARCHAR">  
        <ic:Expression>  
          <ic:Operation Name="Constant">  
            <ic:Argument>WcfAdapter_ServiceRequest</ic:Argument>  
          </ic:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
    </ic:OnEvent>  
```  
  
### <a name="servicereply"></a>ServiceReply  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="WCFServiceReply" Source="WCFService">  
      <ic:Filter>  
        <ic:Expression>  
          <wcf:Operation Name="GetServiceContractCallPoint"/>  
          <ic:Operation Name ="Constant">  
            <ic:Argument>ServiceReply</ic:Argument>  
          </ic:Operation>  
          <ic:Operation Name ="Equals" />  
        </ic:Expression>  
      </ic:Filter>  
  
      <ic:CorrelationID>  
        <ic:Expression>  
          <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
        </ic:Expression>  
      </ic:CorrelationID>  
  
      <ic:Update DataItemName ="Activity Date" Type ="DATETIME">  
        <ic:Expression>  
          <wcf:Operation Name ="GetContextProperty">  
            <wcf:Argument>EventTime</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
      <ic:Update DataItemName ="Name" Type ="NVARCHAR">  
        <ic:Expression>  
          <ic:Operation Name="Constant">  
            <ic:Argument>WcfAdapter_ServiceReply</ic:Argument>  
          </ic:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
    </ic:OnEvent>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF pour intercepter les données BAM](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)