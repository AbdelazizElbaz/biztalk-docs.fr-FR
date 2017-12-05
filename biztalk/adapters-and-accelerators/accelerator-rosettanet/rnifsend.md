---
title: RNIFSend | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 780f7446-56c5-40bf-95e2-25d0cff12f12
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73cf8a832e495944ce7c891421645ae2566e3575
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="rnifsend"></a>RNIFSend
Cet exemple fournit un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] fichier fichier RNIFSend.aspx prépare un message pour le traitement RNIF et envoie le message à la page RNIFReceive.aspx au répondeur. Vous pouvez personnaliser la page ASPX pour effectuer les opérations suivantes :  
  
-   Ajouter ou supprimer des compteurs de performances  
  
-   Ajouter des fonctionnalités à la page, comme l'écriture de données dans une base de données ou la personnalisation de la fonctionnalité de suivi  
  
-   Ajouter la validation à la page  
  
 Cet exemple se trouve dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFSender.  
  
## <a name="demonstrates"></a>Montre  
 Cet exemple montre comment préparer les messages sortants pour RNIF du traitement, y compris les suivantes :  
  
-   Validation des données pour l’en-tête MIME  
  
-   Ajout d’un en-tête MIME et limites MIME au message  
  
-   Envoyer le message au fichier de RNIFReceive.aspx du partenaire  
  
-   Traitement d’un message de signal retourné  
  
## <a name="see-also"></a>Voir aussi  
 [Envoyer et recevoir des Pages ASPX](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Exemples d’applications web](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)