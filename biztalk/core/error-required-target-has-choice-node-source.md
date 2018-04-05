---
title: 'Erreur : cible obligatoire avec Source dans nœud choix | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.reqdTargetHasChoiceNodeSource
ms.assetid: 5b5af999-d100-4e5d-a959-c8b11d574d3b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91c9ad912b03bbb475efcc9eb8207a388400b43b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---required-target-has-choice-node-source"></a>Erreur : cible obligatoire avec Source dans nœud choix
**Code d’erreur**  
  
 btm1029  
  
 **Explication**  
  
 Le nœud indiqué dans le schéma de destination est défini comme étant requis, mais est lié à un nœud dans le schéma source qui se trouve dans un **choix** nœud. Compte tenu que le nœud indiqué dans le schéma source risque de ne pas apparaître dans le message de l'instance d'entrée, il se peut qu'aucune source à partir de laquelle créer le nœud requis dans le schéma de destination n'existe.  
  
 **Action de l’utilisateur**  
  
 Si nécessaire, définissez le nœud indiqué dans le schéma de destination comme étant facultatif ou spécifiez une source différente pour le nœud indiqué dans le schéma de destination qui apparaîtra dans tous les messages de l'instance d'entrée valides.