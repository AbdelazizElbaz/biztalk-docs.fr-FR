---
title: "HL7 2.3.1 dossiers XML et les événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events, HL7 2.XML versions
- HL7, default sub-folders
- HL7, events
ms.assetid: b3598cc5-46d6-489a-84a7-266ee3c40276
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79b25e0563f404d0f8b0600829398729a6c80e65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-231-xml-folders-and-events"></a>HL7 2.3.1 dossiers XML et les événements
Le tableau suivant répertorie les sous-dossiers créés par l’Assistant Installation dans le dossier de version 2.3.1 HL7 pour les messages encodés en XML. Ces sous-dossiers contiennent les schémas utilisés par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pour valider, analyser et sérialiser les événements répertoriés dans la colonne d’événements de cette table. Les noms des sous-dossiers décrivent les types d’événements que prend en charge de ces schémas.  
  
|Sous-dossier|Événements|  
|---------------|------------|  
|Administration patient|A01-A51|  
|Entrée de commande|O01, O02, Q06, R0R, RAR, RDR, RER, RGR, V01-V04|  
|Requête|CNQ, Q01-Q03, Q05, Q07-Q09, R07, R08, R09|  
|Gestion financière|P01-P06|  
|Création de rapports d’observation|C01-C12, P06, P07, P09, R01-R06, W01, W02|  
|Fichiers principaux|M01-M11, L’AUTHENTIFICATION MULTIFACTEUR|  
|Gestion des enregistrements/informations médicales|T01-T12|  
|Planifier|S01-S26|  
|Référence patient|I01-I15|  
|Soins|EN-TÊTE PRÉCOMPILÉ PC1, PCJ, PCK, PCL|  
|Gestion de réseau|N01, N02|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)