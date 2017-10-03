---
title: "Droits d’utilisateur pour la gestion de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Tracking Profile Editor
- Tracking Profile Editor, security
ms.assetid: a0353c4d-2aaa-49ac-8e50-88885962abba
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3319a807b1357201dade0c53d04c26146c2b1e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="user-rights-for-managing-tpe"></a>Droits d'utilisateur pour la gestion de l'Éditeur de modèle de suivi
Les développeur de solutions, les administrateurs système ou le personnel de services informatiques ou de back office doivent disposer de droits d'administration pour extraire ou déployer le modèle de suivi dans une base de données associée à un assembly.  
  
> [!IMPORTANT]
>  Vous ne pouvez pas vous servir de l'Éditeur de modèle de suivi pour définir des rôles d'utilisateur ou accorder ou refuser des autorisations d'utilisateur. Vous pouvez uniquement définir ces rôles d'utilisateur et les autorisations associées dans Microsoft SQL Server.  
  
 Grâce à l'Éditeur de modèle de suivi, les administrateurs peuvent :  
  
-   Extraire un modèle de suivi actif associé à un ou plusieurs assemblys à partir de la base de données de gestion BizTalk  
  
-   Modifier le modèle de suivi  
  
-   Appliquer un nouveau modèle de suivi ou un modèle de suivi modifié dans la base de données de gestion BizTalk  
  
-   Modifier des fichiers de modèle de suivi enregistrés (.btt)  
  
    > [!NOTE]
    >  Les fichiers de modèle de suivi ne constituent pas l'instance finale présidant au contenu d'un modèle. L'Éditeur de modèle de suivi peut enregistrer un modèle dans un fichier même si ses principales attributions sont l'extraction du contenu du modèle des bases de données BizTalk Server et BAM et la publication de ce dernier dans ces mêmes bases de données. Les fichiers de modèle de suivi peuvent toujours être utilisés pour modifier ou mettre à jour le modèle stocké tant que leur contenu correspond aux informations stockées dans les bases de données. De plus, les fichiers de modèle de suivi peuvent être intégrés à un package d'application BizTalk Sever. Les packages d’applications qui incluent des fichiers de profil de suivi automatiquement appellent BTTDeploy.exe pour appliquer le modèle de suivi lorsque le package MSI est importé dans une installation de BizTalk Server donnée.  
  
> [!IMPORTANT]
>  Dans le workflow de l'Éditeur de modèle de suivi, en supposant, comme c'est généralement le cas, que les tâches de développement et de déploiement sont séparées, la personne responsable du déploiement doit disposer d'un accès en lecture seule au fichier .btt et au fichier d'assembly associé.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de travail BAM](../core/bam-workflow.md)   
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)