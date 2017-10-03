---
title: "Suppression des pièces jointes orphelins | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maintaining databases, deleting orphaned attachments
- databases, deleting orphaned attachments
- attachments
ms.assetid: 38280464-9c9d-4890-9fc5-4b8031dd3f88
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7660182793cc82ac938f0dd25011a7c4ad7d7e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deleting-orphan-attachments"></a>Suppression des pièces jointes orphelins
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stocke des pièces jointes pour les messages reçus. Dans certaines circonstances, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] enregistre la pièce jointe, mais supprime le message associé à partir de la table MessagesToLOB, ce qui entraîne une pièce jointe orpheline. Cela peut se produire quand vous envoyez un message qui comporte une pièce jointe et qui possède un manifeste qui n’est pas valide, par exemple, un manifeste dans les NumberOfAttachments = 0. Régulièrement, il pouvez que vous souhaitez supprimer les pièces jointes orphelins pour maintenir les performances du système.  
  
## <a name="how-to-delete-orphan-attachments"></a>Comment supprimer les pièces jointes orphelins  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]stocke les pièces jointes dans la table de pièces jointes de la base de données BTARNDATA. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]stocke les messages associés dans la table MessagesToLOB. Une pièce jointe orpheline se produit lorsque la pièce jointe a un `outMessageID` propriété qui ne correspond pas à la `MessageID` propriété d’un message dans la table MessagesToLOB.  
  
 Régulièrement, il pouvez que vous souhaitez supprimer les pièces jointes de la table à l’aide d’une procédure stockée qui supprime uniquement les pièces jointes qui n’ont pas d’un message correspondant dans la table MessagesToLOB. Un exemple d’instruction SQL pour la procédure stockée est la suivante :  
  
```  
delete from attachments where outMessageID not in (select messageid from messagestolob)  
```  
  
 En outre, il est recommandé de supprimer les pièces jointes qui sont antérieurs à une certaine période et ne nécessitent pas les investigations plus poussées. La table de pièces jointes contient un `TimeCreated` propriété que vous pouvez utiliser pour supprimer les anciennes pièces jointes. Ce processus est similaire au processus utilisé pour supprimer les anciens résumés. Pour un exemple d’instruction SQL pour une procédure stockée qui supprime les anciens résumés, consultez [suppression des résumés](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md).  
  
 Il est également recommandé d’indexer les pièces jointes et MessagestoLOB tables sur les colonnes MessageID respectifs.  
  
## <a name="see-also"></a>Voir aussi  
 [Maintenance des bases de données BTARN](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)