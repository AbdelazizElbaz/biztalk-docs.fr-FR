---
title: "Scénario : Déploiement d’une nouvelle Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, applications
- applications, deploying
- deploying [applications], examples
- applications, examples
- examples, deploying
ms.assetid: 6d34a626-9fd4-4c33-a067-b66333eec01f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 938767237d21b74829c786bdd5d57c7d9df15c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-deploying-a-new-application"></a>Scénario : Déploiement d’une nouvelle Application
Cette rubrique décrit un scénario de déploiement d'une application dans un nouvel environnement où elle n'a encore jamais été déployée; par exemple le déploiement d'une application configurée dans un environnement intermédiaire vers un environnement de production.  
  
 Comme décrit dans [le processus de déploiement d’Application](../core/the-application-deployment-process.md), lorsque vous souhaitez déplacer une application d’un environnement à un autre, vous exportez l’application dans un fichier .msi. Vous importez ensuite le fichier .msi dans le groupe BizTalk au sein du nouvel environnement. Vous installez également l'application sur les ordinateurs du groupe qui doivent l'exécuter. Pour qu'elle puisse fonctionner, vous devez installer l'application sur chaque ordinateur qui devra l'exécuter et démarrer l'application.  
  
 Dans le schéma suivant, Application1 est importée à partir d'un fichier .msi dans le groupe BizTalk B.  
  
 ![Déploiement d’une application BizTalk](../core/media/deployapplication.gif "DeployApplication")  
  
 Ceci importe les artefacts dans les différentes bases de données de BizTalk Server, comme suit :  
  
-   L'assembly BizTalk, l'assembly .NET, les liaisons, le fichier de liaisons, le modèle BAM, le composant COM, le certificat et le fichier texte sont tous ajoutés à la base de données de gestion BizTalk.  
  
-   La stratégie et le vocabulaire sont ajoutés à la base de données du moteur de règles.  
  
-   Le modèle BAM et le fichier de définition d'analyse BAM sont tous deux ajoutés à la base de données d'importation principale BAM.  
  
 Chacun de ces artéfacts est également associé à Application1 dans la base de données de gestion BizTalk.  
  
 L'application est aussi installée sur un ordinateur local à partir du fichier .msi. Ceci installe différents artefacts inclus dans le fichier .msi, comme suit :  
  
-   Le répertoire virtuel, appelé VirtualDirectory, est créé dans la métabase Internet Information Services (IIS).  
  
-   Le certificat est ajouté au magasin de certificats local.  
  
-   Le fichier texte et le composant COM sont copiés dans le système de fichiers local.  
  
-   L'assembly BizTalk et l'assembly .NET sont ajoutés au GAC (Global Assembly Cache), si cette option de déploiement a été sélectionnée.  
  
-   L'assembly .NET et le composant COM sont ajoutés au registre Windows, si cette option de déploiement a été sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications et scénarios de gestion](../core/application-deployment-and-management-scenarios.md)   
 [Déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md)