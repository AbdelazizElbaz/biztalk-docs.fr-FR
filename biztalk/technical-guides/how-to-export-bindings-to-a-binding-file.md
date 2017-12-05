---
title: Comment exporter des liaisons vers un fichier de liaison | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3734ae6d-b790-40f2-8403-d7c7fdbe381b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d1d39bfa1bfd4cc837a77586d6c462c6b7d7f06
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-export-bindings-to-a-binding-file"></a>Comment exporter des liaisons vers un fichier de liaison
Vous pouvez exporter les liaisons d’une application BizTalk dans une autre application BizTalk existante à l’aide d’un fichier de liaison. Vous pouvez également exporter toutes les liaisons dans un groupe ou la liaison d’un assembly. Par la suite, vous pouvez importer ces liaisons dans une application ou un groupe.  
  
 Un fichier de liaison est un fichier XML qui décrit les artefacts dans la base de données de gestion BizTalk et leurs relations. Il contient des informations de liaison pour chaque orchestration BizTalk Server, le pipeline, mappage ou schéma dans l’étendue d’un assembly, une application ou un groupe BizTalk. Il contient les paramètres de configuration pour chaque port d’envoi, un groupe de ports d’envoi, port de réception, emplacement de réception et tiers. Elle décrit également chaque orchestration est liée à l’hôte et son niveau de confiance.  
  
## <a name="why-to-export-to-a-binding-file"></a>Pourquoi exporter vers un fichier de liaison  
 Fichiers de liaison peuvent accélérer le déploiement dans les scénarios suivants en évitant le recours à la configuration manuelle :  
  
-   **Déplacement d’une application à partir d’un environnement de déploiement à un autre**  
  
     À l’aide d’un fichier de liaison permettre accélérer le déploiement en évitant le recours à la configuration manuelle pour différents environnements de déploiement, par exemple à partir d’un environnement de développement à un environnement de test.  
  
-   **Mise à jour d’un assembly**  
  
     Vous pouvez utiliser un fichier de liaison à appliquer automatiquement ou de réappliquer les liaisons pour un assembly après une mise à jour de l’assembly.  
  
-   **Déploiement d’un assembly dans plusieurs groupes BizTalk**  
  
     Vous pouvez éviter d’avoir à configurer séparément les liaisons pour un assembly déployé dans plusieurs groupes BizTalk à l’aide d’un fichier de liaison.  
  
 À l’aide d’un fichier de liaison vous donne une grande souplesse dans l’application des liaisons à une application. Lorsque vous exportez une application vers un fichier .msi, vous ne pouvez spécifier que toutes les liaisons de l’application seront exportés vers le fichier .msi. Fichiers de liaison vous pouvez effectuer les tâches suivantes :  
  
-   Exporter vers un fichier de liaison toutes les liaisons à partir de l’application en cours, toutes les liaisons du groupe actif ou uniquement les liaisons pour un seul assembly. (Cela à l’aide de la commande Exporter les liaisons pour une application dans la console d’Administration.)  
  
-   Vous pouvez ajouter un fichier de liaison à une application (à l’aide de la commande Ajouter des ressources) afin que ses liaisons sont appliquées immédiatement, ou pour les liaisons sont appliquées lorsque l’application est importée dans un autre groupe.  
  
-   Vous pouvez ajouter plusieurs fichiers de liaison à une application (à l’aide de la commande Ajouter des ressources) et spécifiez un environnement de déploiement cible pour chacun d’eux. Cela vous permet d’utiliser un package de déploiement unique pour plusieurs environnements de déploiement. Lorsque vous importez l’application, vous pouvez sélectionner les liaisons à appliquer.  
  
-   Vous pouvez exporter des fichiers de liaison distincts pour plusieurs assemblys dans une application.  
  
-   Vous pouvez modifier les fichiers de liaison après leur génération s'il vous faut modifier leurs informations de liaison.  
  
## <a name="how-to-export-to-a-binding-file"></a>Comment exporter vers un fichier de liaison  
 Vous exportez les liaisons d’une application vers un fichier de liaison en exécutant la commande Exporter les liaisons de l’application dans la console Administration de BizTalk Server, ou à l’aide de la commande BTSTask ExportBindings sur la ligne de commande.  
  
 Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, BizTalk Server ne conserve pas les mots de passe des liaisons du fichier. Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent. Vous configurez ces mots de passe dans la boîte de dialogue Propriétés du transport de la console Administration de BizTalk Server pour le port d'envoi ou l'emplacement de réception.  
  
 Les informations contenues dans un fichier de liaison annulent et remplacement celles de la configuration existante. Si le nom d'un artefact dans un fichier de liaison correspond au nom d'un artefact dans votre configuration existante, l'artefact du fichier de liaison met à jour l'artefact de votre configuration existante lorsque vous importez le fichier de liaison.  
  
 Pour plus d’informations sur le stockage des ordinateurs hôtes et les niveaux de confiance dans les fichiers de liaison, la correspondance des niveaux d’hôte et l’approbation dans un fichier de liaison pour les ordinateurs hôtes et l’approbation de niveaux dans l’application et l’ordre dans lequel les liaisons sont appliquées, consultez [fichiers de liaison et Déploiement d’applications](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.microsoft.com/fwlink/?LinkID=154726). Pour obtenir des instructions sur l’exportation des liaisons pour une application BizTalk, consultez [comment exporter les liaisons d’une Application BizTalk](http://go.microsoft.com/fwlink/?LinkId=155009) (http://go.microsoft.com/fwlink/?LinkId=155009).