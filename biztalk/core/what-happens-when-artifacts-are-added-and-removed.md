---
title: "Que se passe-t-il quand les artefacts sont ajoutés et supprimés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, deleting
- artifacts, creating
- deleting, artifacts
ms.assetid: 811166ba-3ff4-4224-9d84-a2f4ed31bf4d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 464964714993205ef65d5a67de3399935f79320f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-when-artifacts-are-added-and-removed"></a>Effets de l'ajout et de la suppression d'artefacts
Cette rubrique décrit les effets de l'ajout d'artefacts à une application. Vous pouvez ajouter des artefacts basés sur des fichiers à une application en utilisant la console Administration de BizTalk Server ou l'outil de ligne de commande BTSTask. Les artefacts basés sur des fichiers incluent les types suivants :  
  
-   Assemblys BizTalk  
  
-   Assemblys .NET non spécifiques à BizTalk  
  
-   Fichiers de liaison (.xml)  
  
-   composants des services COM  
  
-   Certificats  
  
-   Scripts de pré-traitement et de post-traitement  
  
-   Stratégies  
  
-   Fichiers ad hoc, tels que les fichiers Lisezmoi  
  
-   Répertoires virtuels  
  
-   Artefacts BAM  
  
> [!NOTE]
>  Les ports d’envoi, groupes de ports d‘envoi, emplacements de réception et ports de réception ne sont pas des artefacts basés sur un fichier et ils ne peuvent pas être ajoutés à une application. Vous devez créer ces artefacts dans une application donnée. Vous pouvez ensuite les déplacer vers une autre application, si vous le souhaitez. Les orchestrations, schémas, mappages et pipelines sont tous déployés et gérés dans le cadre des assemblys dont ils font partie.  
  
 Lorsque vous ajoutez un artefact à une application, l'artefact est associé à l'application dans la base de données de gestion BizTalk et les données de fichier destinées à l'artefact sont également ajoutées à la base de données de gestion. Cela vous permet de transporter facilement des applications et des artefacts d'un groupe BizTalk à un autre car vous pouvez exporter l'application et les données des artefacts dans un fichier .msi à partir de la base de données de gestion, puis les réimporter dans une base de données de gestion dans un autre groupe BizTalk.  
  
 Lorsque vous ajoutez un fichier de liaison à une application, vous pouvez spécifier l'environnement de déploiement cible dans lequel vous souhaitez appliquer les liaisons. Contrairement à ce qui se passe lors de l'importation d'un fichier de liaison, lorsque vous ajoutez un fichier de liaison, ses liaisons ne sont pas appliquées.  
  
 Lorsque vous ajoutez un assembly BizTalk ou .NET à une application, vous pouvez spécifier à l'aide de l'option appropriée l'installation de l'assembly dans le GAC (global assembly cache).  
  
## <a name="see-also"></a>Voir aussi  
 [Que se passe-t-il pour les artefacts au cours du déploiement](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [Comment créer ou ajouter un artefact](../core/how-to-create-or-add-an-artifact.md)   
 [Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md)   
 [Comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md)