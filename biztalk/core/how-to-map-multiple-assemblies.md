---
title: Comment mapper plusieurs assemblys | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, tracking profiles
- tracking profiles, mapping assemblies
- assemblies, maps
ms.assetid: 136f1943-9643-4551-8b5b-150c4b4bfebe
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20a55b6e88889ccfa36adcac11fe548ab1b25bc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-multiple-assemblies"></a>Mappage de plusieurs assemblys
Des applications BizTalk peuvent être constituées de plusieurs assemblys dans lesquels résident les éléments de données référencés par une activité BAM. La procédure suivante vous indique comment mapper plusieurs assemblys vers un modèle de suivi.  
  
### <a name="to-map-multiple-assemblies"></a>Pour mapper plusieurs assemblys  
  
1.  Ouvrez un modèle de suivi existant ou créez-en un. Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).  
  
2.  Cliquez sur le **Source d’événement sélectionnez** bouton (située au-dessus du volet droit dans l’éditeur de modèle de suivi).  
  
3.  Sélectionnez le **sélectionner une planification d’Orchestration** dans le menu en cascade.  
  
4.  Sélectionnez l’assembly parent à partir duquel dessiner l’orchestration en cliquant sur l’assembly contenant l’orchestration dans le **nom de l’Assembly** zone de liste, puis cliquez sur **suivant**.  
  
5.  Sélectionnez l’orchestration qui est la source pour les éléments de données dans le **nom de l’Orchestration** zone de liste, puis cliquez sur **OK**.  
  
6.  Dans le volet droit, sélectionnez les éléments de données et faites-les glisser vers les nœuds appropriés de l'activité dans le volet gauche.  
  
7.  Pour mapper d'autres assemblys, répétez les étapes 2 à 6.  
  
### <a name="to-map-the-second-assembly"></a>Pour mapper le deuxième assembly  
  
1.  Cliquez sur le **sélectionner la Source de l’événement**.  
  
2.  Sélectionnez le **sélectionner une planification d’Orchestration** dans le menu en cascade.  
  
3.  Sélectionnez l’assembly parent suivant à partir duquel dessiner l’orchestration en cliquant sur l’assembly contenant l’orchestration dans le **nom de l’Assembly** zone de liste, puis cliquez sur le **suivant** bouton.  
  
4.  Sélectionnez l’orchestration qui est la source pour les éléments de données dans le **nom de l’Orchestration** zone de liste, puis cliquez sur **OK**.  
  
5.  Dans le volet droit, sélectionnez les éléments de données et faites-les glisser vers les nœuds appropriés de l'activité dans le volet gauche.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment mapper des Sources d’événements](../core/how-to-map-event-sources.md)   
 [Création de modèles de suivi](../core/creating-tracking-profiles.md)