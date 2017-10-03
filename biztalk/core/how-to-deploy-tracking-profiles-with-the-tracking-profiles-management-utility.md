---
title: "Comment déployer des modèles de suivi avec le suivi des profils d’utilitaire de gestion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, deploying
- deploying, tracking profiles
- bttdeploy.exe [BAM]
- managing [BAM], deploying tracking profiles
ms.assetid: b3023379-cae1-45fc-a773-2660d3e4abf1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a2c3c464e4b06e65ab15059da6ec3c36179ff25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility"></a>Déploiement de modèles de suivi à l'aide de l'utilitaire de gestion des modèles de suivi
Un gestionnaire des activités demande à un développeur de solutions de créer un modèle de suivi ou d'en modifier un pour mieux gérer et contrôler un processus d'entreprise spécifique à votre entreprise.  
  
 Le développeur de solutions utilise l'Éditeur de modèle de suivi pour définir les données que l'analyste d'entreprise requiert.  
  
 Une fois que le développeur de solutions a créé ou modifié le modèle de suivi, un administrateur utilise l'utilitaire de ligne de commande bttdeploy.exe pour le déployer de manière à ce que les modifications prennent effet et que les données soient collectées. Le développeur de solutions peut déployer des modèles de suivi avec l'Éditeur de modèle de suivi.  
  
> [!IMPORTANT]
>  Avant de déployer le modèle de suivi, vous devez déployer les assemblys qui lui sont associés.  
  
> [!IMPORTANT]
>  Vous devez disposer des privilèges d'administrateur BizTalk® pour utiliser cet outil.  
  
### <a name="to-deploy-the-tracking-profile-from-the-command-line-utility"></a>Pour déployer le modèle de suivi à partir de l'utilitaire de ligne de commande  
  
1.  À partir d’une invite de commandes, accédez au répertoire \<chemin d’installation > \Program Files\Microsoft BizTalk Server \<version > \Tracking\\.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
2.  Type **bttdeploy.exe \<nom du profil > .btt**.  
  
3.  Appuyez sur Entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Recommandations de sécurité BAM](../core/bam-security-recommendations.md)   
 [Business Activity Monitoring (BAM)](../core/business-activity-monitoring-bam.md)