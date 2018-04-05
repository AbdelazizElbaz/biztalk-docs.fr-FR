---
title: 'Erreur : Code généré par les enfants du fonctoid copie de masse | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.massCopyChildtenGenCode
ms.assetid: c791009b-241b-4004-b0c6-f1536bb119c5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68183a90be46b176d13100b02cbed2798fe24b34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---children-of-mass-copy-functoid-generate-code"></a>Erreur : Code généré par les enfants du fonctoid copie de masse
**Code d’erreur**  
  
 btm1068  
  
 **Explication**  
  
 Un scénario qui se révèle contradictoire avec la fonctionnalité de la **copie de masse** fonctoid a été trouvé dans le mappage. Dans le schéma de destination, les descendants d’un nœud qui est lié à la sortie d’un **copie de masse** fonctoid tentent de générer leur propre code XSLT.  
  
 **Action de l’utilisateur**  
  
 Supprimer l’incompatibilité en modifiant l’utilisation de la **copie de masse** fonctoid ou modifiez les nœuds enfants, tels qu’ils ne sont plus de générer leur propre code XSLT.