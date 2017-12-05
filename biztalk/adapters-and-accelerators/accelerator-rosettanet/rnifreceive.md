---
title: RNIFReceive | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf1253b0-ceca-4e7a-91ed-3837bd904472
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57af8140157b901d7e6265fc26249c7fbfef0c46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="rnifreceive"></a>RNIFReceive
Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] fichier RNIFReceive.aspx qui reçoit un message RNIF et le prépare pour le traitement par le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus public. Vous pouvez personnaliser la page ASPX pour effectuer les opérations suivantes :  
  
-   Ajouter ou supprimer des compteurs de performances  
  
-   Ajouter des fonctionnalités à la page, comme l'écriture de données dans une base de données ou la personnalisation de la fonctionnalité de suivi  
  
-   Ajouter la validation à la page  
  
 Cet exemple se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFReceiver.  
  
## <a name="demonstrates"></a>Montre  
 Cet exemple montre comment préparer les messages entrants pour le processus public, notamment les opérations suivantes :  
  
-   Réception du message à partir du fichier RNIFSend.aspx du partenaire  
  
-   Validation de l'en-tête MIME  
  
-   Suppression de l'en-tête MIME et des limites du message  
  
-   Routage du message vers le fichier RNIFReceive.aspx du partenaire  
  
-   Retour d'un message de signal  
  
## <a name="see-also"></a>Voir aussi  
 [Envoyer et recevoir des Pages ASPX](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Exemples d’applications web](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)