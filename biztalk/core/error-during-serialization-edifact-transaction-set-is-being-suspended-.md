---
title: "Document informatisé EDIFACT contenu dans l’erreur d’échange | Documents Microsoft"
description: "Erreur lors de la sérialisation. Le document informatisé EDIFACT contenu dans l'échange (sans groupe) est en cours d'interruption avec les erreurs suivantes"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a0a33ac-d83e-495c-ba75-88c15ad7cfcd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f089e49941ffec7d3392b3bc35edcbc4eefec5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-transaction-set-is-suspended-error-and-details"></a>Document informatisé EDIFACT est détails et l’erreur suspendu

`Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors`

## <a name="details"></a>Détails  
  
|||  
|---|---|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EfactTransactionSetSendErrorWithoutGroup|  
|Texte du message|Erreur lors de la sérialisation. Le document informatisé avec l’id '{0}' contenu dans l’échange (sans groupe) avec l’id « {{1}', id d’expéditeur « {{2} », id de destinataire '{3}' est interrompu avec les erreurs suivantes :|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange EDIFACT sortant en raison des erreurs mentionnées pour le document informatisé. Notez que le document informatisé ne fait pas partie d'un groupe dans l'échange.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, utilisez les informations dans le message d’erreur pour identifier l’erreur dans le document informatisé et déterminer la résolution du problème.