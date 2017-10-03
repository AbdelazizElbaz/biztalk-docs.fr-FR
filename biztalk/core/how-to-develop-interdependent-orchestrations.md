---
title: "Le développement d’Orchestrations interdépendantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5464096e-66d8-48de-bc02-c754c5cfbada
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93f8d086a60487e144b02c01a393eb6f10a63b40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-develop-interdependent-orchestrations"></a>Développement d'orchestrations interdépendantes
Vous pouvez vous servir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour développer un ensemble d'orchestrations dotées de services Web interdépendants. Cette situation peut survenir lorsque vos orchestrations font référence à des types de données et/ou des ports dans l'orchestration depuis laquelle ils ont été appelés. Ce type de scénario se présente comme suit :  
  
-   Vous possédez au moins deux orchestrations.  
  
-   La première orchestration (Orch1) appelle la seconde orchestration (Orch2) via un appel de service Web unidirectionnel.  
  
-   Orch2 répond à Orch1 via un appel de service Web.  
  
 Pour un exemple de ce type de projet, consultez [didacticiel 2 : processus de bon de commande](http://msdn.microsoft.com/library/a324ef1b-39b3-49ab-9719-a13f526cb467).  
  
### <a name="to-develop-two-interdependent-orchestrations-orch1-and-orch2"></a>Pour développer deux orchestrations interdépendantes Orch1 et Orch2  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez une version partielle de l'orchestration Orch1 avec un port de réception qui sera affiché en tant que service Web.  
  
2.  Compilez Orch1.  
  
3.  Exécutez l'Assistant Publication de services Web et publiez le port.  
  
4.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], créez et terminez intégralement Orch2, en utilisant le service Web d'Orch1.  
  
5.  Compilez Orch2.  
  
6.  Exécutez l'Assistant Publication de services Web et publiez le ou les ports.  
  
7.  Terminez Orch1, en utilisant le(s) service(s) Web d'Orch2, si nécessaire.  
  
8.  Recompilez Orch1.  
  
9. Déployez Orch1 et Orch2.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier une Orchestration en tant que Service Web](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)