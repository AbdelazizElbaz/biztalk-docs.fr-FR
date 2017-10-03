---
title: "Erreur lors de la sérialisation. Le document informatisé contenue dans le groupe fonctionnel est interrompu avec les erreurs suivantes de X12 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49b13038-2637-4435-91e9-d6fe2b80ca7a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c8b1402974c53007e8488df3fbdedc666ac2753
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-x12-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a>Erreur lors de la sérialisation. Le document informatisé X12 contenu dans le groupe fonctionnel est interrompu avec les erreurs suivantes :
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12TransactionSetSendError|  
|Texte du message|Erreur lors de la sérialisation. Le X12 document informatisé avec l’id '{0}' contenue dans groupe fonctionnel avec l’id « {{1} », dans l’échange avec l’id « {{2} », avec l’expéditeur id '{3}', id de destinataire '\{4\' est interrompu avec les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi EDI a rencontré un problème lors de la sérialisation d'un échange X12 sortant en raison des erreurs indiquées au niveau du document informatisé identifié.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le document informatisé et déterminer une méthode de résolution dans l'aide du produit.