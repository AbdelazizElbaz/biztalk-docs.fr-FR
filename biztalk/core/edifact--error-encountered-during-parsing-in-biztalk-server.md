---
title: "Erreur rencontrée lors de l'analyse. L’échange Edifact qui ne contenait pas de groupe comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6b324fd-f365-41b9-81aa-b6c5c5d3f673
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 550e5ca207bef7fdcb42ffcbd52e114ad3dc95ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a>Erreur rencontrée lors de l'analyse. L'échange EDIFACT qui ne contenait pas de groupe comportait les erreurs suivantes
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactFunctionalGroupReceiveErrorWithoutGroup|  
|Texte du message|Erreur rencontrée lors de l'analyse. L’échange Edifact qui ne contenait pas de groupe, avec l’id d’échange '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comporte les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors de l'analyse d'un échange EDIFACT entrant qui ne contenait pas de groupe en raison des erreurs mentionnées. Notez que les groupes sont facultatifs dans les échanges EDIFACT.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci et déterminer la méthode de résolution dans l'aide du produit.