---
title: "Erreur : fonctoid incompatibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.functoidFixedInputMismatch
ms.assetid: d235e7c3-efcf-4128-aef7-cdfdf1f317be
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8de4020105f357905e510be1694c0cf95a4af6c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---functoid-fixed-input-mismatch"></a>Erreur : fonctoid incompatibilité
**Code d’erreur**  
  
 btm1010  
  
 **Explication**  
  
 Le fonctoid indiqué ne comporte pas un nombre correct de paramètres d'entrée définis. Le nombre de paramètres d'entrée doit correspondre exactement au nombre indiqué.  
  
 **Action de l’utilisateur**  
  
 Utilisez une ou plusieurs des méthodes suivantes pour affecter le nombre correct de paramètres d'entrée au fonctoid concerné, tout en veillant à ce que l'ordre des paramètres soit respecté :  
  
-   Pour créer des liens supplémentaires, déplacez la souris pour créer un lien entre d'une part le fonctoid indiqué et d'autre part, soit des nœuds du schéma source, soit la sortie d'autres fonctoids situés à gauche du fonctoid indiqué dans la page de grille de mappage.  
  
-   Pour créer des liens supplémentaires, sélectionnez le fonctoid indiqué, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis configurez et organisez les paramètres d’entrée dans le **configurer \<Fonctoid\> fonctoid** boîte de dialogue. Dans cette boîte de dialogue, vous pouvez créer des paramètres d'entrée constants, leur affecter des valeurs et les classer dans le même ordre que celui des autres paramètres d'entrée.  
  
-   Pour supprimer des liens existants, chaque lien sur le côté gauche du fonctoid indiqué, cliquez sur le lien, puis **supprimer**.  
  
-   Pour supprimer des liens existants, sélectionnez le fonctoid indiqué, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis, dans le **configurer \<fonctoid\> fonctoid**boîte de dialogue, supprimez tous les paramètres d’entrée en sélectionnant et en cliquant sur le ![ ] (../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") bouton pour chacun d’eux. Cette méthode est recommandée pour la suppression des paramètres d'entrée constants.