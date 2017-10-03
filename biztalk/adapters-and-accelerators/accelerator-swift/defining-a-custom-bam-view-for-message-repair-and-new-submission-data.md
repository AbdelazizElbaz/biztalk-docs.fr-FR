---
title: "Définition d’une vue BAM personnalisées pour Message Repair et les nouvelles données de soumission | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM views
- Message Repair and New Submission, BAM views
ms.assetid: 76a6e78d-9b11-4b43-a500-a9d7666ee468
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 760865f6f69559031b10bc9f4e609bbb3cfffa33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-a-custom-bam-view-for-message-repair-and-new-submission-data"></a>Définition d’une vue BAM personnalisées pour Message Repair et les nouvelles données de la soumission
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Le programme d’installation fournit un fichier de définition BAM qui définit une activité d’entreprise et de la vue de l’entreprise. Vous pouvez déployer le fichier de définition BAM pour utiliser cette vue, ou vous pouvez créer un affichage personnalisé que vous pouvez ajouter au fichier de définition BAM.  
  
 Le fichier de définition BAM est MrsrActivities.xml dans  *\<lecteur >*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\BAMTracking. Il définit une activité de Message et une vue RepairView. Pour plus d’informations sur le déploiement de MrsrActivities.xml à l’aide de la bm utilitaire de déploiement, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 Créer la vue personnalisée de l’Assistant Vue BAM à partir du classeur BAM. Pour plus d’informations sur la création d’un affichage personnalisé, consultez « Création d’une vue BAM » dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] traitement des informations utiles.  
  
 L’activité d’un Message dans MrsrActivities.xml inclut les éléments suivants que vous pouvez ajouter à la vue personnalisée :  
  
> [!NOTE]
>  Lors du calcul des durées de l’analyse BAM, ils sont mesurés en unités d’un jour (14,4 minutes =.01).  
  
|Élément|Utiliser|Type d’élément|  
|----------|---------|---------------|  
|Destination BIC|L’adresse LT du récepteur du message (provenant de l’Application en-tête bloc d’entrée pour les messages SWIFT ou à partir de 1 bloc de messages SWIFT où le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] institution constitue la destination).<br /><br /> Ces données sont toujours présentes (à partir de l’Application en-tête entrée Destination LT pour les messages SWIFTBound ou à partir de la base LT d’en-tête pour les messages reçus à partir de SWIFT).|Données de l'entreprise - Texte|  
|Heure de fin|Date et heure de fin de l’orchestration MRSRRepair du traitement du message (MRSR_Completed ou MRSR_Failed).<br /><br /> Ces données sont présentes uniquement pour les messages qui ont été les flux de travail MRSR, autrement dit, terminés avec **BTS. Opération** == **A4SWIFT_MRSRCompleted** ou **A4SWIFT_MRSRFailed**.|Étape majeure commerciale|  
|Référence|L’identificateur de référence unique pour ce message ou d’une transaction attribué par l’établissement d’envoi ; provenant du champ 20 ou 20C(SEME)|Données de l'entreprise - Texte|  
|Type de message|Le type de message FIN ou amp.<br /><br /> Ces données sont toujours présentes (Application en-tête entrée ou sortie d’en-tête de l’Application).|Données de l'entreprise - Texte|  
|Nouvelle soumission|Un indicateur qui signale si cela est une nouvelle entrée (Y) ou un message qui provenance d’un autre système ou SWIFT (N).<br /><br /> Ces données sont présentes uniquement les messages qui ont été émis par rôle avec la capacité de créer.|Données de l'entreprise - Texte|  
|Priorité|La priorité du message SWIFT (N = normal, U = urgente, S = system).<br /><br /> Ces données sont toujours présentes.|Données de l'entreprise - Texte|  
|Heure de réception|La date et l’heure auxquelles l’orchestration MRSRRepair reçu le dernier message (voir l’étape ci-dessous à partir de l’étape précédente.).<br /><br /> Ces données sont toujours présentes.|Étape majeure commerciale|  
|Expéditeur BIC|L’adresse LT de l’expéditeur du message (provenant de bloc 1 pour les messages pour SWIFT où le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] institution est l’expéditeur, ou à partir de l’en-tête de sortie de l’Application pour les messages SWIFT).<br /><br /> Ces données sont toujours présentes (de base adresse LT en-tête SWIFTBound Messages, ou à partir de l’en-tête de sortie de l’Application pour les messages reçus à partir de SWIFT).|Données de l'entreprise - Texte|  
|Heure d’envoi|Date et heure à laquelle l’orchestration MRSRRepair dernière envoyé le message au site MRSR (pour l’étape actuelle).<br /><br /> Ces données sont toujours présentes, sauf si le message est en cours de l’orchestration.|Étape majeure commerciale|  
|Start Time|Date et heure auxquelles l’orchestration MRSRRepair initialement a reçu le message sous la forme d’un nouvel envoi ou un message à partir d’une interface (système interne ou SWIFT).<br /><br /> Ces données sont toujours présentes.|Étape majeure commerciale|  
|Dernière étape|La dernière étape effectuée dans le flux de travail (toujours l’étape avant où le message est présent)|Données de l'entreprise - Texte|  
|État|Valeurs possibles :<br /><br /> -Terminé (en cas de réussite)<br />-Permet de réinitialiser et de la raison (pour les flux de travail réinitialiser si le flux de travail est redémarré)<br />-Échec et de la raison (si message effectué avec succès, autrement dit, a été rejetée ou a expiré).<br /><br /> Ces données sont toujours présentes.|Données de l'entreprise - Texte|  
|Service|Le service sélectionné par l’orchestration MRSRRepair conformément à la stratégie de service (dépend de la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] institution)|Données de l'entreprise - Texte|  
|Utilisateur|Le nom de l’utilisateur associé à l’étape précédente (voir l’étape ci-dessus)|Données de l'entreprise - Texte|  
|Phase actuelle|L’étape de flux de travail à laquelle l’orchestration MRSRRepair a remis le message (par exemple, la boîte de réception).<br /><br /> Ces données sont présentes, sauf si le message a terminé la réparation du message.|Données de l'entreprise - Texte|