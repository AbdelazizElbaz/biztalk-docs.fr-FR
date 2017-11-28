---
title: "Erreur : fonctoid Index ne comporte aucun Index | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.indexFunctoidHasNoIndex
ms.assetid: a523705e-6134-4d98-8ea6-dbfc7b43dae5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8143442b9d77d6881efe2b64dfb7f5888ab2d466
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---index-functoid-has-no-index"></a>Erreur : fonctoid Index ne comporte aucun Index
**Code d’erreur**  
  
 btm1014  
  
 **Explication**  
  
 Aucune valeur d’index n’ont été fournis pour le fonctoid **Index** fonctoid.  
  
 **Action de l’utilisateur**  
  
 Fournir un nombre approprié de paramètres d’entrée d’index pour le fonctoid **Index** fonctoid, où le nombre approprié est déterminé par le nombre de bouclage **enregistrement** nœuds au sein de laquelle le **Champ** nœud dans le schéma source est imbriqué. Pour la création des paramètres d’entrée d’index, sélectionnez le fonctoid indiqué, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis utiliser le ![](../core/media/bts-tls-paraminsert.gif "bts_tls_paraminsert") bouton dans le **configurer \< Fonctoid > fonctoid** boîte de dialogue pour ajouter un ou plusieurs paramètres d’entrée constants, où la première représente un index dans le parent immédiat de bouclage **enregistrement** nœud et les paramètres suivants représentent l’ancêtre de plus en plus à distance bouclage **enregistrement** nœuds.