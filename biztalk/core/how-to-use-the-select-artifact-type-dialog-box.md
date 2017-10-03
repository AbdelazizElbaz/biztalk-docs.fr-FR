---
title: "L’utilisation de la boîte de dialogue Sélectionnez artefact Type | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Select Artifact Type dialog box
- artifacts, Select Artifact Type dialog box
- Orchestration Designer, items
ms.assetid: f0f767f1-4130-4ff0-a898-a089343ee71f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3027971059d99a921bd743ff28aca1617c5d628d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-select-artifact-type-dialog-box"></a>Comment utiliser le Type de boîte de dialogue Sélectionnez artefact
Un *élément* est utilisé pour configurer les éléments d’une orchestration dans le Concepteur d’Orchestration. Cet élément peut être un schéma, un mappage, un pipeline, un type de port ou un type de message à parties multiples. Lorsque vous développez une orchestration et les parties qui la constituent, telles que des formes Port, des formes Transformer et des messages, vous pouvez avoir besoin de faire référence à des éléments résidant en dehors de l'orchestration active, mais figurant dans le projet en cours ou dans un autre projet compilé dans un assembly BizTalk Server. Vous utilisez la **sélectionner le Type d’artefact** boîte de dialogue pour rechercher et spécifier ensuite les éléments lors de la configuration d’un élément dans une orchestration.  
  
 Le **sélectionner le Type d’artefact** boîte de dialogue est disponible à partir de plusieurs emplacements dans le Concepteur d’Orchestration. Vous pouvez sélectionner \<sélectionner dans l’assembly référencé > dans une liste déroulante qui affiche les options de configuration ; cliquez sur ce texte pour ouvrir le **sélectionner le Type d’artefact** boîte de dialogue.  
  
 Avant de sélectionner un élément, vous devez choisir le composant à configurer.  
  
 Vous pouvez utiliser la **sélectionner le Type d’artefact** boîte de dialogue pour les actions suivantes :  
  
|Action|Fonction|  
|------------|-------------|  
|Sélectionner un pipeline|Sélectionner un pipeline pour la propriété de pipeline lors de la configuration d'un port pour une liaison directe (anticipée).|  
|Sélectionner un mappage|Sélectionnez un mappage à utiliser avec un **transformer** forme.|  
|Sélectionner un schéma|Sélectionner des schémas dans le projet lors de la création de types de message à parties multiples.|  
|Sélectionner un type de port|Faire référence aux types de ports existants lors de la création d'un port.|  
|Sélectionner un type de message à parties multiples|Faire référence aux types à parties multiples existants lors de la création d'un message.|  
|Sélectionner un type .NET|Faire référence aux types .NET existants lors de la création d'une variable ou d'un message.|  
  
 **Volet de référence**  
  
 Le volet de référence de la **sélectionner le Type d’artefact** boîte de dialogue affiche les références dans le projet actuel et dans d’autres assemblys disponibles. Pour sélectionner une référence dans ce volet, cliquez dessus. Pour développer un conteneur dans ce volet (tel que le **assemblys** conteneur), cliquez sur le signe plus (+) à côté de lui.  
  
 **Volet de l’élément**  
  
 Le volet de l’élément de la **sélectionner le Type d’artefact** boîte de dialogue affiche les éléments contenus dans la référence actuellement sélectionnée dans le volet de référence. Le volet de l’élément a deux colonnes, **élément** et **nom qualifié**, qui contiennent des informations sur les éléments de la référence active.  
  
### <a name="to-use-the-select-artifact-type-dialog-box"></a>Pour utiliser la boîte de dialogue Sélectionner le type d'artefact  
  
1.  Développez le **références** nœud dans le volet gauche. Le volet affiche les projets et assemblys disponibles.  
  
2.  Développez le **assemblys** nœud. Un ou plusieurs assemblys s'affichent, tels que SYSTEM.DLL et MICROSOFT.BIZTALK.PIPELINES.DLL.  
  
3.  Cliquez sur un assembly. Si l'assembly contient des éléments, ceux-ci s'affichent dans le volet de droite. Le nom complet d'un élément s'affiche dans la colonne de droite du volet droit.  
  
    > [!NOTE]
    >  Si le projet en cours contient des éléments, vous pouvez cliquer dessus pour afficher ces éléments et en sélectionner un.  
  
4.  Pour sélectionner un élément dans le volet droit, cliquez dessus, puis cliquez sur **OK** pour quitter le **sélectionner le Type d’artefact** boîte de dialogue. L'élément sélectionné devient le type du composant choisi. Pour fermer la **sélectionner le Type d’artefact** boîte de dialogue sans sélectionner et attribuer un élément, cliquez sur **Annuler**.  
  
## <a name="see-also"></a>Voir aussi  
 [Formes d’orchestration](../core/orchestration-shapes.md)   
 [Comment ajouter des formes aux Orchestrations](../core/how-to-add-shapes-to-orchestrations.md)   
 [Comment ajouter des paramètres aux Orchestrations](../core/how-to-add-parameters-to-orchestrations.md)