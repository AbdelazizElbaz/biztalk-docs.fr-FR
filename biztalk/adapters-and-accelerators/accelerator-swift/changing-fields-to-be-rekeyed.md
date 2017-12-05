---
title: "Modification des champs à être régénérée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rekeyed fields
- Message Repair and New Submission, modifying fields
- Message Repair and New Submission, rekeyed fields
ms.assetid: aaf353f7-0e43-403e-b72a-88e5dd07f4ac
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04693bf4c4d441487a3ce38f886bc680b1db368b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="changing-fields-to-be-rekeyed"></a>Modification des champs à être régénérée
Dans l’étape de vérification d’un flux de travail de réparation message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] supprime les données à partir d’un nombre de champs afin que le vérificateur d’entrer à nouveau ou recomposition, ces données. Vous pouvez personnaliser les champs dans le RekeyVerify [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire doit être régénérée. Faire dans le fichier MrsrXpathConfig.xml, qui se trouve dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour le dossier SWIFT\MRSR.  
  
 Le fichier MrsrXpathConfig.xml contient une série de nœuds pour le type de message traité. Chaque nœud de type de message contient une série de nœuds de champ, un pour chaque champ. Vous pouvez modifier les champs à être régénérée en ouvrant MrsrXpathConfig.xml dans un éditeur de texte, tel que le bloc-notes et en ajoutant ou en supprimant un \<chemin d’accès\> nœud pour le champ.  
  
 Le \<chemin d’accès\> nœud contient les chemins d’accès pour le type de message et le champ. Par exemple, l’entrée pour le chemin d’accès de Destination dans le bloc d’en-tête Application d’entrée d’un message MT103 est le suivant :  
  
```  
<path>/*[local-name()='SWIFT_CATEGORY1_MT103_Interchange' and namespace-uri()'http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category1/MT103']/*[local-name()='SWIFTHeader' and namespace-uri=']'']/*[local-name()='ApplicationHeaderBlock_Input' and namespace-uri90='']/*[local-name()='DestinationAddress' and namespace-uri()='']</path>  
```  
  
 Il est plus facile d’ajouter un nouveau champ à être régénérée en copiant et en collant ensuite d’une entrée existante, puis en remplaçant les chemins d’accès appropriés. Par exemple, pour forcer la régénération du champ de Date dans la section de 32 a valeur Date Interbank réglée montant en devise d’un message MT103, effectuez les remplacements de trois suivants pour le code précédent. Le reste du code reste le même.  
  
|Remplacez ceci|Avec cette|  
|------------------|---------------|  
|`SWIFTHeader`|`SWIFT_CATEGORY1_MT103`|  
|`ApplicationHeaderBlock_Input`|`ValueDateCurrencyInterbankSettledAmount_32A`|  
|`DestinationAddress`|`Date`|  
  
 Pour plus d’informations sur la régénération des champs, consultez [un traitement spécial dans le Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md).