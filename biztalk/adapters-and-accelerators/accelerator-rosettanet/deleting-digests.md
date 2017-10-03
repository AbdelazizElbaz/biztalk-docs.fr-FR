---
title: "Suppression des résumés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, digests
- messages, digests
- digests
- databases, deleting digests
- maintaining databases, deleting digests
ms.assetid: bcc7cb11-2f6a-4996-ad50-040d41993e09
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fefa59a7638b7dc4627d5d7a019d753b4f6290b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deleting-digests"></a>Suppression des résumés
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stocke des résumés pour les messages sortants, donc il peut valider les contenus de signal. Toutefois, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne supprime pas les résumés après la validation. Régulièrement, il pouvez que vous souhaitez supprimer ces résumés pour maintenir les performances du système.  
  
## <a name="when-and-how-to-delete-digests"></a>Quand et comment supprimer des résumés  
 Les résumés sont stockées dans la table MessageDigestHelper de la base de données BTARNDATA. Régulièrement, il pouvez que vous souhaitez supprimer ces résumés à partir de la table à l’aide d’une procédure stockée qui supprime uniquement les résumés qui sont antérieurs à une certaine période. La table MessageDigestHelper contient un `TimeCreated` propriété que vous pouvez utiliser à cet effet.  
  
 Créer une procédure stockée avec l’instruction SQL suivante (modifiée pour vos besoins) et exécutez la procédure stockée pour supprimer les anciens résumés. Cet exemple d’instruction supprime tous les résumés de plus de sept jours :  
  
```  
delete from MessageDigestHelper where datediff(day, TimeCreated, getutcdate()) > 7  
```  
  
> [!NOTE]
>  La procédure stockée doit inclure un appel à `getutcdate`, et non `getdate`, car tous les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] bases de données utilisent l’heure UTC (Universal Time Coordinate).  
  
## <a name="see-also"></a>Voir aussi  
 [Maintenance des bases de données BTARN](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)