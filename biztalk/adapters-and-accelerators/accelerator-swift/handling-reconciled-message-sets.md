---
title: "La gestion des ensembles de messages rapprochées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAA
- messages, reconciled sets
ms.assetid: 05cd0cf6-f0fd-4cbe-83c6-1ed5f2da8822
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fc9f35f9381f82df90acb92e9536bbd967901a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-reconciled-message-sets"></a>Gestion des ensembles de messages de rapprochement
Lorsque SAA renvoie une réponse à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] enregistre la réponse dans la MessageBox et correspond à la réponse ou les réponses au message d’origine. Vous pouvez implémenter le comportement d’application personnalisée à l’aide de ces informations. Pour ce faire, développer des gestionnaires personnalisés qui implémentent les réactions de client spécifiques aux jeux de message rapprochées/réponse. Vous pouvez créer des gestionnaires personnalisés qui effectuent les opérations suivantes :  
  
-   Traiter les messages FRR a mis en corrélation avec un message MTS21_FIN_ACKNAK-accusé de réception négatif, ce qui indique que SWIFT n’a pas reçu correctement le message à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. Cela peut permettre un réparateur résoudre le message et le renvoyer à SAA et le réseau SWIFT, ce qui, après la réparation, espère sera en mesure de recevoir le message avec succès. Pour plus d’informations sur cette solution, consultez [FRR NAK Gestionnaire exemple](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).  
  
-   Supprimer les jeux de réponse de message publiés par l’orchestration dans un dossier de fichiers avec des noms de fichier unique qui indique les relations entre les messages dans le jeu. Vous pouvez ensuite effectuer une logique métier sur ces messages.  
  
-   Traiter les messages expiré.  
  
-   Enregistrez les résultats de la transmission du message et supprime ensuite les messages réels.