---
title: BtarnClean | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BtarnClean utility
- assemblies, undeploying
- BTARN, deleting artifacts
- orchestrations, unenlisting
- ports, stopping
- orchestrations, stopping
- ports, deleting
- BTARN, BtarnClean utility
ms.assetid: fbecbb88-9b18-4b4b-a286-0bfa783f2320
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa8e448d4799329a798cc7b33f222b42c4a28b4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="btarnclean"></a>BtarnClean
Vous utilisez l’utilitaire BtarnClean pour nettoyer [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] artefacts sur un ordinateur. Cette opération inclut les actions suivantes :  
  
-   L’arrêt et désinscription de toutes les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] orchestrations  
  
-   Arrêt et suppression de tous les ports associés  
  
-   Annulation du déploiement de tous les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Assemblys Solutions.BTARN.*  
  
## <a name="location-in-sdk"></a>Emplacement dans le kit de développement logiciel (SDK)  
 \<*lecteur*\>\Program Files\ Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK  
  
## <a name="running-btarnclean"></a>Exécution de BtarnClean  
  
#### <a name="to-run-btarnclean"></a>Pour exécuter BtarnClean  
  
1.  Ouvrez une invite de commandes.  
  
2.  Déplacer vers \< *lecteur*\>\ programme Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\\.  
  
3.  À l'invite de commandes, tapez **BtarnClean**, puis appuyez sur Entrée.  
  
     L'utilitaire vous invite à confirmer que vous souhaitez continuer.  
  
## <a name="remarks"></a>Notes  
 Si vous exécutez l'utilitaire BtarnClean sur un ordinateur disposant d'un artefact BizTalk qui dépend d'autres artefacts, BtarnClean indique qu'il ne peut pas supprimer cet artefact. L'utilitaire laisse cet artefact en place et continue à supprimer d'autres artefacts. Vous pouvez supprimer des dépendances, puis réexécuter l'utilitaire.  
  
 Si vous exécutez l'utilitaire BtarnClean sur un ordinateur qui fait partie d'un déploiement sur plusieurs ordinateurs, la suppression des artefacts affecte le reste des serveurs de ce déploiement.  
  
 Si vous exécutez l'utilitaire BtarnClean lorsqu'il existe plusieurs processus créés par des développeurs, l'utilitaire ne supprime pas les processus qui sont encore en cours d'utilisation.  
  
 L'utilitaire BtarnClean ne supprime pas un emplacement de réception principal si l'artefact de l'utilisateur utilise cet emplacement de réception. Si c'est le cas, vous devez supprimer le port de réception.  
  
 Si vous souhaitez annuler la configuration [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] après l’exécution de l’utilitaire, exécutez Configuration.exe /u à partir de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)