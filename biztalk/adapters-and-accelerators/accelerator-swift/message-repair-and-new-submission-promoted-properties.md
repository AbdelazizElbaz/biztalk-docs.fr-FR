---
title: "Propriétés promues du message Repair et New Submission | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- promoted properties, Message Repair and New Submission
- Message Repair and New Submission, promoted properties
ms.assetid: e980c905-d07f-4fc2-89ca-05e597410733
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76e4f57e9f5179ceea073ef281131a8cd3573703
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission-promoted-properties"></a>Propriétés promues du message Repair et New Submission
Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair et New Submission rapprochement inclut les propriétés promues suivantes.  
  
|Nom de promotion| Description|Type de données|Plage de valeurs|Exemple d’utilisation|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**BIZTALK SERVER. Opérations**|Indique l’état de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] du traitement. Les valeurs possibles sont les suivantes :<br /><br /> **A4SWIFT_MrsrCompleted** indique que le message repair et un nouveau processus de soumission a réussi.<br /><br /> **A4SWIFT_MrsrFailed** indique que le message repair et un nouveau processus de soumission a échoué.<br /><br /> **A4SWIFT_MrsrUnparsedFailed** indique que la réparation d’un message non analysée a échoué.<br /><br /> **A4SWIFT_MrsrUnparsedComplete** indique que la réparation d’un message non analysée a réussi.<br /><br /> **A4SWIFT_DasmMarkedAsFailed** indique que le message a échoué le traitement de l’étape de désassembleur de pipeline de réception.|Chaîne|-A4SWIFT_MrsrCompleted<br />-A4SWIFT_MrsrFailed<br />-A4SWIFT_MrsrUnparsedFailed<br />-A4SWIFT_MrsrUnparsedCompleted<br />-A4SWIFT_DasmMarkedAsFailed|Lorsque l’orchestration de MrsrRepair reçoit un message non analysé réparé après la réparation, il définit le **BTS. Opération** propriété « A4SWIFT_MRSRCompleted » et le **A4SWIFT_Failed** propriété à False, puis achemine le message vers la MessageBox. Ces propriétés garantissent que le message non analysé réparé n’entre pas dans le processus de réparation de message à nouveau.|  
|**Microsoft.Solutions.A4SWIFT. Property.A4SWIFT_Failed**|Indique si [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] avec succès ou non traité le message.|Booléen|True, False|Utilisé par l’orchestration MrsrRepair pour s’abonner uniquement aux messages à partir de la MessageBox qui ont échoué la validation.|  
|**Microsoft.Solutions.A4SWIFT. Property.A4SWIFT_SwiftBound**|Indique si le message est lié pour le réseau rapide.|Booléen|True, False|Utilisé par l’orchestration MrsrRepair pour s’abonner uniquement aux messages à partir de la MessageBox sont liés pour le réseau rapide.|  
|**Microsoft.Solutions.A4SWIFT. MRSRProperty.A4SWIFT_MRSRIsNewSubmission**|Indique si le message en cours de traitement est une nouvelle soumission.|Booléen|True, False|Utilisé par l’orchestration MrsrRepair pour indiquer qu’un message a été créé à l’étape de création du flux de travail.|  
|**Microsoft.Solutions.A4SWIFT. MRSRProperty.A4SWIFT_MRSRLastStage**|Indique la dernière étape du flux de travail de réparation a réussi.|Chaîne|-|Une des étapes définies pour un flux de travail de service. Peut être un créer, réparer, vérifiez que le changement de clé, ou une phase d’approbation.|  
|**Microsoft.Solutions.A4SWIFT. MRSRProperty.A4SWIFT_ MRSRDepartment**|Indique le service qui est utilisé dans le message repair et new submission, tel que spécifié par la stratégie BRE de MrsrDepartmentPolicy.|Chaîne|-|Définir dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Console d’Administration.|  
|**Microsoft.Solutions.A4SWIFT. MRSRProperty.A4SWIFT_ MRSRFailedReason**|Indique pourquoi le message repair et un nouveau processus de soumission a échoué. Les valeurs possibles sont les suivantes :<br /><br /> Rejeté indique que l’utilisateur a refusé le message depuis la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire.<br /><br /> InvalidDigitalSignature indique que le certificat de l’utilisateur n’est pas valide.<br /><br /> Délai d’attente indique que la valeur de délai d’attente MRSROrchestration a été atteinte.<br /><br /> InvalidWorkFlow indique que le flux de travail défini pour un service n’est pas valide.<br /><br /> CantRepairIn[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] indique que le message XML entrant ne peut pas être ouverts dans [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)].<br /><br /> Exception générale|Chaîne|-Rejeté<br />-InvalidDigitalSignature<br />-Timeout<br />-InvalidWorkFlow<br />-Exception générale<br />-CantRepairIn[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]|Définie par l’orchestration Message Repair et New Submission une fois que le processus a échoué.|  
  
## <a name="see-also"></a>Voir aussi  
 [A4SWIFT_ * propriétés promues](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   
 [Propriétés promues de rapprochement de réponse FIN](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation-promoted-properties.md)