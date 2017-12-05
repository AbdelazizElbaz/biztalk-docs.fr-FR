---
title: "Comment mettre à jour d’un Pipeline à l’aide de la gestion des versions côte-à-côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd884a76-71dd-4c90-b4ba-f1cd7f48eb04
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a5b977d8f0d1964df33c2b2f549bd420d0d3179
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a>Comment mettre à jour d’un Pipeline à l’aide de la gestion des versions côte à côte
Pour utiliser un pipeline ajouté par le contrôle de version côte à côte, la simple consiste à sélectionner la version de pipeline qui vient d’être déployé dans le port d’envoi ou emplacement de réception. Cela remplace le pipeline ancien par le nouveau. Toutefois, si vous avez besoin des fonctionnalités côte-à-côte true pour la compatibilité descendante, puis vous devez créer nouveaux ports d’envoi et emplacements de réception et les lier à la nouvelle version de pipeline spécifiée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a>Pour ajouter une nouvelle version d’un composant de pipeline  
  
1.  Dans Visual Studio, créez une nouvelle version du composant de pipeline, et signer l’assembly.  
  
2.  Ajouter le composant de pipeline dans le **composants de Pipeline** dossier (\<*dossier d’installation*\>\Pipeline Components).  
  
3.  Ajouter le composant de pipeline à votre pipeline.  
  
4.  Après la création du pipeline ou déploiement de votre solution, supprimer le composant de pipeline à partir de la **composants de Pipeline** dossier.  
  
5.  Ajouter le composant de pipeline dans le global assembly cache (GAC).  
  
 Une fois que vous aurez effectué ces étapes, l’assembly de pipeline compilé fait référence à la version correcte du composant de pipeline, et que le domaine d’application utilisé par BizTalk Server trouvera la nouvelle version du composant de pipeline dans le GAC, au lieu de recherche précédent version du composant de pipeline dans le dossier composants de Pipeline.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour en utilisant la gestion des versions côte à côte](../technical-guides/updating-using-side-by-side-versioning.md)