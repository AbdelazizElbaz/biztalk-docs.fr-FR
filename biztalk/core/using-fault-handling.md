---
title: "À l’aide de la gestion des erreurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc793386-d2ec-4e02-9283-3237f65c9e01
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00547917da65253123cb2067715a09633547eb4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-fault-handling"></a>Utilisation de la gestion des erreurs
Au cours de [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] un message d’exception de gestion d’erreurs n’est pas retournée au client, sauf si un **FaultException** (ou un sous-type) est levée ou un **FaultContract** est implémentée. Dans de tels scénarios, vous pouvez donc assurer le suivi des données uniquement à partir du message d'erreur. Une exception dans les implémentations de rappel automatiquement se présente comme un message d’erreur pour les deux **ServerFault** et **ClientFault** points de suivi. Toutefois, une erreur générique est toujours renvoyée avec un message générique. Pour plus d’informations sur les contrats d’erreur WCF, consultez [http://go.microsoft.com/fwlink/?LinkId=83132](http://go.microsoft.com/fwlink/?LinkId=83132).  
  
 Vous pouvez également suivre les constantes et les propriétés de contexte via les trackpoints d'erreur.  
  
 Si les détails de l’exception sont renvoyés dans les erreurs à l’aide de la **IncludeExceptionDetailInFaults** attribut, vous extrayez le message d’exception réel via XPath.  
  
 Gestion d’erreurs est fournie par les trackpoints d’erreur définis dans [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md):  
  
-   ServiceFault  
  
-   ClientFault  
  
-   CallbackFault  
  
 À l'aide de ces trackpoints d'erreur, les données de l'erreur sont toujours rendues persistantes, même dans un scénario basé sur une transaction. L'intégrité transactionnelle est conservée sur toutes les données suivies non erronées, qui sont restaurées sous forme de réponse à l'erreur.  
  
> [!NOTE]
>  Ces suivi points sont appliquées pour le chemin d’accès de la réponse et s’appliquent uniquement aux ServiceReply, ClientReply et CallbackReply contrat appel de points de service fournis par [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md).  
  
## <a name="fault-configuration-sample"></a>Exemple de configuration d'erreur  
 L’exemple suivant illustre le suivi de message d’exception sur une **ServiceFault** lorsque le service lève une **FaultException** dans les **AuthorizationServiceFault** événement ; Sinon, il effectue le suivi de l’expression booléenne renvoyée par l’opération dans le **AuthorizationServiceReply** événement. Soit le **AuthorizationServiceReply** OnEvent ou **AuthorizationServiceFault** OnEvent est rendu persistant.  
  
> [!NOTE]
>  L'implémentation de cet exemple illustre le fait que les trackpoints ServiceReply et ServiceFault s'excluent mutuellement.  
  
```  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceReply" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceReply</ic:Argument>  
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
      <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
    </ic:Expression>  
  </ic:CorrelationID>  
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Success</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName="Result" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name ="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:AuthorizeWithDataContractResult</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceFault" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceFault</ic:Argument>  
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
      <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
    </ic:Expression>  
  </ic:CorrelationID>  
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Fault</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
      <ic:Update DataItemName="Source" Type="NVARCHAR">  
        <ic:Expression>  
          <wcf:Operation Name ="XPath">  
            <wcf:Argument>//s:Body/Fault/Reason/Text</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF pour intercepter les données BAM](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)