---
title: "À l’aide du Concepteur de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, how to
- pipelines, Pipeline Designer
ms.assetid: bdb2f5c7-f8a2-4bd6-a8d8-8b7a64f97bd0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce7a8bc7c7943ff96f0d70a802a2756f8d8c4783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-pipeline-designer"></a>Utilisation du Concepteur de pipeline
Le Concepteur de pipeline est un éditeur graphique hébergé dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] qui permet de créer des pipelines, d'afficher les modèles de pipeline inclus dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], de déplacer les composants de pipeline au sein d'un pipeline et de configurer les pipelines, leurs étapes et leurs composants.  
  
 Le Concepteur de pipeline utilise trois outils principaux du shell [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] :  
  
-   la fenêtre Propriétés, qui permet d'afficher et de modifier la plupart des caractéristiques des objets d'un pipeline ;  
  
-   la boîte à outils, utilisée en tant que source pour la surface de conception ;  
  
-   la surface de conception, où l'on fait glisser et où l'on dépose les composants de la boîte à outils.  
  
 La figure suivante présente l'environnement du Concepteur de pipeline.  
  
 ![L’environnement d’édition du Concepteur de Pipeline](../core/media/ebiz-prog-usepipe.gif "ebiz_prog_usepipe")  
Illustration de l'environnement du Concepteur de pipeline  
  
 Le Concepteur de pipeline est intégré au modèle de projet BizTalk pour faciliter le développement. Après avoir utilisé le système de projet pour créer un projet BizTalk, vous pouvez utiliser la **ajouter un nouvel élément** commande sur le **fichier** menu pour ajouter un pipeline à votre solution. Pour plus d’informations sur le modèle de projet BizTalk, consultez [à l’aide du système de projet BizTalk](../core/using-the-biztalk-project-system.md).  
  
> [!NOTE]
>  Dans les précédentes versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le concept de pipeline était encapsulé dans les ports et les canaux de message qui définissaient un ensemble de composants spécifiques qui étaient appliqués à un document. Dans cette version, le pipeline est souple, car vous êtes libre de réagencer les composants à chaque étape du pipeline et vous pouvez insérer facilement des composants personnalisés dans le pipeline.  
  
 La surface de conception du Concepteur de pipeline permet de tracer une représentation graphique d'un pipeline. Elle occupe la section principale de la fenêtre [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et permet de modifier les pipelines d'un projet BizTalk. Vous pouvez naviguer entre les pipelines en cliquant sur les onglets situés au-dessus de la surface de conception.  
  
 Chaque pipeline est composé d'étapes dont chacune contient un ou plusieurs composants. Si une étape n'a pas de composants, un filigrane avec du texte indique qu'il est possible d'insérer des formes à partir de la boîte à outils. Quand la première forme est insérée dans une étape, le texte initial disparaît. La surface de conception présente le pipeline verticalement, s'exécutant du haut (début) vers le bas (fin).  
  
 Comme avec d’autres programmes Microsoft Windows courants, vous pouvez effectuer plusieurs tâches, telles que **ouvrir** et **enregistrer** à partir de la **fichier** menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Pipelines avec le Concepteur de Pipeline](../core/creating-pipelines-with-pipeline-designer.md)   
 [Création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md)