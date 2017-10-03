---
title: "La phase de vérification de recomposition | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rekey verification
- stages, rekey verification
ms.assetid: 8a2880b6-bb25-4af5-9f51-d0b090ca38c8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9fe163a8351b0edc904f81d77a7ea341de13df6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rekey-verification-stage"></a>Recomposition la phase de vérification
Quand une vérification recomposition étape se produit dans le flux de travail de réparation de message, une copie du message d’origine est conservée par Message réparer et New Submission et une copie exacte du message est envoyée à la boîte de réception ses recomposition vérification. Dans la vérification de changement de clé, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair et New Submission efface les champs spécifiés pour rentrée manuelle.  
  
 Ce concept est expliqué plus en détail la [sécurité du Runtime serveur](../../adapters-and-accelerators/accelerator-swift/server-runtime-security.md) rubrique. Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur participe à la phase de vérification de recomposition doit manuellement entrer à nouveau dans les champs effacés, via le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran, les valeurs qui correspondent exactement à ceux du message d’origine (à partir de l’étape de la création ou de la réparation). Le vérificateur signe le message avec un certificat valide, puis envoie le message.  
  
 Si les valeurs des champs rekeyed ne correspondent pas exactement les champs de message d’origine, le Message Repair et New Submission réinitialise l’étape dans le flux de travail et renvoie le message à la boîte de réception du réparateur. Il valide également la signature du vérificateur qui régénérée les champs. Si le vérificateur n’est pas validé, il envoie le message à la boîte de réception de la vérification.