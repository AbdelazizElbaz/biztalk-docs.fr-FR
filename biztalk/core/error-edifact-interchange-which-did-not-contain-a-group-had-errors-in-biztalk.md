---
title: "Erreur lors de la sérialisation. L’échange Edifact qui ne contenait pas de groupe comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af693139-e4cd-4bcb-922c-79caa148d3b7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72108104b359d4d06233cf9a623097bfd046a0ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a>Erreur lors de la sérialisation. L'échange EDIFACT qui ne contenait pas de groupe comportait les erreurs suivantes
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactFunctionalGroupSendErrorWithoutGroup|  
|Texte du message|Erreur lors de la sérialisation. L’échange Edifact qui ne contenait pas de groupe, avec l’id d’échange '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comporte les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange EDIFACT sortant en raison des erreurs mentionnées pour l'échange identifié. Notez que l'échange ne contient pas de groupe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci dans l'échange et déterminer la méthode de résolution dans l'aide du produit.