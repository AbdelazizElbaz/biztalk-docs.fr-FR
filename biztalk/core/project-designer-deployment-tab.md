---
title: "Concepteur de projet : Onglet déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties, Configuration database [BizTalk Server]
- Redeploy property
- configuration properties [deployment], Server property
- Server property
- configuration properties [deployment], Install to Global Assembly Cache (GAC) property
- properties, Management database
- Install to Global Assembly Cache (GAC) property
- Configuration database [BizTalk Server], properties
- Management database, properties
- Administration Group property
- configuration properties [deployment], Redeploy property
- configuration properties [deployment], Management database property
- configuration properties [deployment], Administration Group property
ms.assetid: 5b64f99c-4ec6-4ed3-8590-46420e2f75b8
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972f3956a19d66d47238ee8170584b4faf6ba886
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="project-designer-deployment-tab"></a>Concepteur de projet : onglet Déploiement
Le **déploiement** onglet de propriétés du Concepteur de projets permet de configurer les attributs de déploiement pour le projet BizTalk. Vous devez configurer les deux le **Server** et **base de données de Configuration** (également appelée la base de données BizTalk Management) propriétés en tant qu’ensemble pour le déploiement réussisse.  
  
## <a name="application-name"></a>Application Name  
 Indiquer l'application BizTalk dans laquelle déployer l'assembly. Si ce champ est vide, le projet sera déployé dans l'application par défaut.  
  
## <a name="configuration-database"></a>Base de données de configuration  
 Ce champ permet de spécifier le nom de la base de données de configuration BizTalk pour l'assembly déployé. Cela est nécessaire si vous avez configuré le projet BizTalk en tant que projet de déploiement.  
  
> [!NOTE]
>  La base de données de configuration BizTalk est également appelée « base de données de gestion BizTalk ».  
  
 Le nom par défaut de la base de données de configuration est BizTalkMgmtDb.  
  
## <a name="server"></a>Server  
 Il s'agit du nom du serveur sur lequel se trouve l'espace de stockage Configuration (également appelé base de données de gestion ou de configuration BizTalk). Vous déployez le projet BizTalk sur ce serveur si vous configurez le projet BizTalk en tant que « Déploiement ».  
  
## <a name="redeploy"></a>Redéployer  
 Vous utilisez la **redéployer** propriété pour déterminer s’il faut supprimer la configuration existante et recréez la configuration de chaque fois que vous déployez l’assembly. La valeur par défaut est `True`.  
  
## <a name="install-to-global-assembly-cache"></a>Installer dans le Global Assembly Cache  
 Vous utilisez la **installer dans le Global Assembly Cache** propriété pour indiquer si [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] doit installer l’assembly BizTalk dans le global assembly cache (GAC).  
  
## <a name="restart-host-instances"></a>Redémarrer les instances d'hôte  
 Si vous définissez **redémarrer les Instances d’hôte** à **True**, les instances d’hôte sur l’ordinateur local seront redémarrés une fois le projet est déployé par [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Ceci est utile lors du cycle de développement lorsque vous effectuez des modifications et de fréquents redéploiements ; vous n'aurez pas à redémarrer manuellement les instances d'hôte associées.  
  
 Si vous ne redémarrez pas les instances d'hôte associées, vos dernières modifications risquent de ne pas être reflétées dans votre application BizTalk car l'ancienne version risque d'être toujours en mémoire cache. Le redémarrage des instances d'hôte purge les assemblys mis en cache.  
  
## <a name="enable-unit-testing"></a>Activer les tests unitaires  
 Spécifie s'il faut activer les tests unitaires pour le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment déployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)   
 [Fenêtre des propriétés de projet BizTalk](../core/biztalk-project-properties-window.md)