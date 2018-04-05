---
title: 'Erreur : mappage devant être migré | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.mapNeedsMigrating
ms.assetid: f10af4a4-6e40-4eec-a2fd-e526821aebe6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f49ef4aae0db47216f6117f1053185df6fae0a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---map-needs-to-be-migrated"></a>Erreur : mappage devant être migré
**Code d’erreur**  
  
 btm1064  
  
 **Explication**  
  
 Impossible de compiler le mappage, car il a été créé avec une version précédente du Mappeur BizTalk. Vous devez migrer ces mappages vers la version actuelle du Mappeur BizTalk pour pouvoir les compiler.  
  
 **Action de l’utilisateur**  
  
 Migrez le mappage vers la version actuelle du Mappeur BizTalk en remplaçant l'extension de fichier « xml » par « btm », puis ajoutez-le au projet Microsoft BizTalk Server approprié. Utilisez le **ajouter un élément existant** commande disponible sur le **fichier** menu et dans le menu contextuel pour BizTalk de projet dans l’Explorateur de solutions, puis ouvrez le mappage en double-cliquant dessus dans l’Explorateur de solutions. Si vous êtes arrivé à cette rubrique, cela signifie que les deux premières étapes ont probablement déjà été réalisées. L'ouverture du mappage dans la version actuelle du Mappeur BizTalk entraînera la migration immédiate de ce mappage.