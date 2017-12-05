---
title: "Création d’un gestionnaire personnalisé pour les Messages rejetés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom handlers
- Message Repair and New Submission, rejected messages
- Message Repair and New Submission, custom handlers
ms.assetid: 28d74504-6c62-427a-b75d-456fbe43ec3a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baa02ad0fcb0236ec879e43b44a891fcdf591beb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-custom-handler-for-rejected-messages"></a>Création d’un gestionnaire personnalisé pour les Messages rejetés
Si vous le rejetez un message à l’étape de vérification ou de l’approbation [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] retourne le message à la première étape définie pour le flux de travail (dans ce cas est toujours réparer, même si Create est la première étape dans le flux de travail). Toutefois, si la première étape du flux de travail rejette le message, l’orchestration de réparation publie le message dans la MessageBox avec des propriétés promues indiquant que l’orchestration MrsrRepair a refusé le message. Pour gérer ces messages, vous pouvez créer un gestionnaire personnalisé (orchestration) qui s’abonne à ces propriétés promues et traite les messages en fonction des besoins.  
  
 Échec d’un message dans l’orchestration MrsrRepair pour plusieurs raisons. Dans ce cas, l’orchestration promeut les propriétés dans le tableau suivant et affecte ces propriétés, la valeur ou l’une des valeurs, indiquées dans la colonne de droite de la table.  
  
|Propriété|Valeurs|  
|--------------|------------|  
|BIZTALK SERVER. Opération|A4SWIFT_MRSRFailed|  
|A4SWIFT_MRSRFailedReason|Délai d'expiration<br /><br /> Rejeté (signifie que le message a été rejeté par la première étape)<br /><br /> CantRepairInInfoPath|  
|A4SWIFT_MRSRLastStage|\<nom de la dernière étape (rôle) le message a été dans avant d’échouer\>|  
|A4SWIFT_MRSRDepartment|\<nom du service\>|