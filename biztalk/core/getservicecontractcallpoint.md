---
title: GetServiceContractCallPoint | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be03d100-0cba-4b80-8056-b582a2cd74ce
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e291bcf733129991f6d3b5000ca8e9bc1353057
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getservicecontractcallpoint"></a>GetServiceContractCallPoint
Transmet le nom du point d'appel de contrat de service actuel sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wcf:Operation Name="GetServiceContractCallPoint" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant le point d'appel de contrat actuel.  
  
## <a name="remarks"></a>Notes  
 Un service Windows Communication Framework peut être intercepté à différents points pendant la durée de vie du contrat de service. Ces emplacements sont définis par l'énumération `System.BizTalk.Bam.Interceptors.Wcf.ContractCallPoint` :  
  
|Point d'appel de contrat|Description|  
|-------------------------|-----------------|  
|ClientReply|Point d'appel de réponse client.|  
|ClientRequest|Point d'appel de demande client.|  
|ClientFault|Point d'erreur client.|  
|ServiceReply|Point d'appel de réponse de service.|  
|ServiceRequest|Point d'appel de demande de service.|  
|ServiceFault|Point d'erreur de service.|  
|CallbackRequest|Point d'appel de demande de rappel.|  
|CallbackReply|Point d'appel de réponse de rappel.|  
|CallbackFault|Point d'erreur de rappel.|  
  
## <a name="example"></a> Exemple  
 L'exemple suivant contient une expression de filtre d'événements configurée pour rechercher une opération spécifique (« Réception ») dans l'état de réponse client à l'aide d'une combinaison d'opérations comprenant `GetOperationName`, `GetServiceContractCallPoint` ainsi que des opérations logiques.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ClientReply</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations dans Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)