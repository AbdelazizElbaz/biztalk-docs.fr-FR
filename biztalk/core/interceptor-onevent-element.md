---
title: "Élément OnEvent de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d684ac8e-61bc-410b-97a2-6fd3549e0d97
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6fb70b2536dbf5db5b0abc03bc194de154b4317
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-onevent-element"></a>Élément OnEvent de l'intercepteur
Le **OnEvent** élément décrit un événement réel qui est mappé à l’activité BAM associée.  
  
## <a name="format"></a>Format  
 L'élément `OnEvent` contient des éléments enfants qui spécifient un filtre d'événements, l'ID de corrélation et, de manière facultative, les données à mettre à jour, les données de référence et un jeton de liaison.  
  
### <a name="attributes"></a>Attributs  
  
|Nom de l'attribut| Description|  
|--------------------|-----------------|  
|Nom|Nom défini par l'utilisateur pour cet événement.|  
|Source|Nom de l’événement source tel qu’il apparaît dans un **EventSource** élément.|  
|IsBegin|Valeur booléenne indiquant si l'événement représente le début d'une nouvelle activité BAM (`true`) ou non (`false`).|  
|IsEnd|Valeur booléenne indiquant si l'événement représente la fin d'une activité BAM (`true`) ou non (`false`).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|État de l'exécution| Description|  
|----------------------|-----------------|  
|Filtrer|Fournit une méthode permettant de restreindre l'événement à des critères spécifiques.|  
|CorrelationID|Indique l'ID de corrélation (l'ID de l'instance d'activité).|  
|ContinuationToken|Spécifie le jeton de liaison, c'est-à-dire un ID de corrélation utilisé par des événements futurs qui contribueront à la même instance d'activité.|  
|Update|Spécifie les données à extraire de l'événement et à importer dans l'activité BAM.|  
|Référence|Ajoute une relation à une activité BAM.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une manière classique **OnEvent** bloc pour WF :  
  
```  
<ic:OnEvent Name="BeginAct" IsBegin="true" Source="ResWF">  
  <ic:Filter>  
    <ic:Expression>  
      <wf:Operation Name="GetActivityName"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <wf:Operation Name="GetActivityEvent"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Closed</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <ic:Operation Name="And"/>  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>InstanceId</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>EventTime</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  <ic:Update DataItemName="FoodItem" Type="NVARCHAR">  
    <ic:Expression>  
      <wf:Operation Name="GetWorkflowProperty">  
        <wf:Argument>foodItem</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
 Cet exemple présente un standard **OnEvent** bloc pour le service WCF :  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="AuthorizationRequestService" Source="ESCreditCardService">  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals"/>  
      <wcf:Operation Name="GetOperationName" />  
      <ic:Operation Name="Constant">  
        <ic:Argument>AuthorizeWithDataContract</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals" />  
      <ic:Operation Name ="And" />  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="Name" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:FirstName</wcf:Argument>  
      </wcf:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:LastName</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name ="Concatenate"/>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Filter](../core/filter.md)  
  
-   [ID de corrélation](../core/correlationid.md)  
  
-   [ContinuationToken](../core/continuationtoken.md)  
  
-   [Référence](../core/reference.md)  
  
-   [Update](../core/update2.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Structure d’un fichier de Configuration de l’intercepteur](../core/structure-of-an-interceptor-configuration-file.md)