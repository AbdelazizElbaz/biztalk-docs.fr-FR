---
title: "Erreur lors de la sérialisation. Le document informatisé Edifact contenu dans le groupe fonctionnel est interrompu avec les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b76086-334b-45fb-85f8-82e3335daac4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb09bfecc2efc5e6878b7cc3d0149f2b56c07b68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a>Erreur lors de la sérialisation. Le document informatisé EDIFACT contenu dans le groupe fonctionnel est en cours d'interruption avec les erreurs suivantes
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactTransactionSetSendError|  
|Texte du message|Erreur lors de la sérialisation. Le document informatisé avec l’id de groupe fonctionnel avec l’id « {{1} », ' {0}' dans l’échange avec l’id « {{2} », avec l’expéditeur id '{3}', id de destinataire '\{4\' est interrompu avec les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange EDIFACT sortant en raison des erreurs mentionnées pour le document informatisé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le document informatisé et déterminer une méthode de résolution dans l'aide du produit.