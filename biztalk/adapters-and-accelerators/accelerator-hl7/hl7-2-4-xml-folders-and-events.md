---
title: "Dossiers XML 2,4 HL7 et événements | Documents Microsoft"
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
ms.assetid: bc6c5d75-66c7-4269-bfb9-59cab5999a73
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10c9445a1d5c7978b526fd0347dc6defa3214640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-24-xml-folders-and-events"></a>Les événements et les dossiers XML 2,4 HL7
Le tableau suivant répertorie les sous-dossiers créés par l’Assistant Installation dans le dossier de la version 2.4 HL7 pour les messages encodés en XML. Ces sous-dossiers contiennent les schémas utilisés par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pour valider, analyser et sérialiser les événements répertoriés dans la colonne d’événements de cette table. Les noms des sous-dossiers décrivent les types d’événements que prend en charge de ces schémas.  
  
|Sous-dossier|Événements|  
|----------------|------------|  
|Administration patient|A01-A62, K21, K22, K23, K24, Q21-Q24|  
|Entrée de commande|O01-O22, Q06, Q26-Q30, RAR, RDR, RER, RGR, ROR, V01-V04, Z73, Z74|  
|Requête|J01, J02, K11, K13, K15, Q01-Q05, Q07-Q09, Q 11, Q 13, QUESTION Q15-17, R07-R09, Z75-Z99|  
|Gestion financière|P01 ~ P06, P10|  
|Création de rapports d’observation|C01-C12, P07, P08, P09, R01, R02, R04, R21, W01, W02|  
|Fichiers principaux|M01-M12, L’AUTHENTIFICATION MULTIFACTEUR|  
|Gestion des enregistrements/informations médicales|T01-T12|  
|Planification|S01-S26|  
|Référence patient|I01-I15|  
|Soins|EN-TÊTE PRÉCOMPILÉ PC1, PCJ, PCK, PCL|  
|Automation de laboratoire|U01-U13|  
|Gestion des applications|N01, N02|  
|Gestion du personnel|B01-B06, K25, Q25|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)