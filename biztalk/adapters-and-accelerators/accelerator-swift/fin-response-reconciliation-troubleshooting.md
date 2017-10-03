---
title: "Réponse FIN rapprochement dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, troubleshooting
- troubleshooting, FIN Response Reconciliation
ms.assetid: f62326aa-9a4e-4941-a9bb-20bde980f99e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a92812086f191d5777b387d9861b32a3147c1e96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-reconciliation-troubleshooting"></a>Réponse de la FIN la résolution des problèmes de rapprochement
## <a name="the-frr-bam-view-does-not-show-the-message-type-of-a-message"></a>La vue FRR BAM n’affiche pas le type de message d’un message  
  
### <a name="symptom"></a>Symptôme  
 La vue FRR BAM dans le site MRSR n’affiche pas le type de message pour un ou plusieurs messages. Toutes les autres données pour l’ou les messages sont indiquées, et le type de message s’affiche pour les instances de tous les autres types de message.  
  
### <a name="possible-cause"></a>Cause possible  
 L’activité FRRMessageOut n’enregistre pas le type de message pour les messages F21 (accusés de réception/NAKs).  
  
### <a name="solution"></a>Solution  
 Si vous rencontrez ce problème, interpréter les messages qui ne sont pas un type de message répertorié dans la vue FRR BAM dans le site MRSR sous forme de message F21.  
  
## <a name="deploying-system-level-schemas-in-a-project-generates-an-error"></a>Déploiement de schémas au niveau du système dans un projet génère une erreur  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous tentez de déployer les schémas au niveau du système dans FrrSchemas.dll dans un projet, vous recevez une erreur. Pour obtenir la liste de ces schémas, consultez [les Types de réponse de FIN](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md).  
  
### <a name="possible-cause"></a>Cause possible  
 Les schémas au niveau du système dans FrrSchemas.dll sont déjà déployés dans FrrSchemas.dll. Essayez de les déployer à nouveau entraîne une erreur.  
  
### <a name="solution"></a>Solution  
 Il n’est pas nécessaire de déployer les schémas dans FrrSchemas.dll au niveau du système.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes : Problèmes et résolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)