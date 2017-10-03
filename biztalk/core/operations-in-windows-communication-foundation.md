---
title: "Opérations dans Windows Communication Foundation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1728d2f-ac74-446e-a36f-4b645a6e042a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c6b5344b8fb2c5a5ba7a68b112adb50133198c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-in-windows-communication-foundation"></a>Opérations dans Windows Communication Foundation
Cette section contient les opérations personnalisées prises en charge par l'intercepteur WCF BAM.  
  
 Notez que, si un élément de nom d'opération contient un attribut Action :  
  
1.  le nom d'opération est celui identifié par l'attribut de nom pour le client et le serveur ;  
  
2.  pour les chemins de réponse (réponse de rappel), réponse de client et réponse de service, le nom d'opération est identifié par l'attribut de nom.  
  
> [!NOTE]
>  Les messages de réponse auront un nœud nommé par l'ajout du mot « Result » au nom spécifié par l'attribut de nom. Vous devez vous assurer que les expressions XPath reflètent cette convention d'affectation de noms.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [AutoGenerateCorrelationToken](../core/autogeneratecorrelationtoken.md)  
  
-   [GetContextProperty](../core/getcontextproperty1.md)  
  
-   [GetEndpointName](../core/getendpointname.md)  
  
-   [GetOperationName](../core/getoperationname.md)  
  
-   [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md)  
  
-   [XPath](../core/xpath.md)