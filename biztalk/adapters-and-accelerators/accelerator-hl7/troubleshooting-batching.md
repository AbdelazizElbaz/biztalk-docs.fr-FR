---
title: "Résolution des problèmes de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, troubleshooting
- troubleshooting, batching
ms.assetid: f47e1a16-47fd-4bd8-8dad-fcdba31a833e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94c8413a8022529e6ace56c50d5e6d75267a72e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-batching"></a>Résolution des problèmes de traitement par lot
Traite des problèmes liés à [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le traitement par lot.  
  
## <a name="error-activating-batch"></a>Traitement d’activation erroné  
  
### <a name="symptom"></a>Symptôme  
 Impossible d’activer un lot. Vous obtenez une erreur réseau générale.  
  
**Cause possible** : [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] a été redémarré, mais [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] n’était pas dans l’Explorateur de Configuration.  
  
**Résolution** : redémarrez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
## <a name="messages-are-not-batched-when-the-target-namespace-is-not-the-default"></a>Les messages ne sont pas traités par lot lorsque l’espace de noms cible n’est pas la valeur par défaut  
  
### <a name="symptom"></a>Symptôme  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]est pas le traitement par lot les messages.  
  
**Cause possible** : parties Source et de destination ne sont pas dans le même espace de noms du schéma.  
  
**Résolution** : parties Source et de destination doivent utiliser le même espace de noms du schéma si la validation est requise. Assurez-vous que les parties de la source et de destination utilisent le même espace de noms du schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus et dépannage dans HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)