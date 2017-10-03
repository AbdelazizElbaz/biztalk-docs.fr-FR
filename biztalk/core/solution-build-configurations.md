---
title: Configurations de Build de solution | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configuration Manager
- building, solutions
- building, Configuration Manager
- solutions, deploying
- deploying, building
- solutions, developing
- solutions, build configuration
ms.assetid: 6f2cce47-388d-4c93-9146-768f53b8207e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e537ca4bc2dd85722ddf3afd4eaba443aab7a25b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="solution-build-configurations"></a>Configurations de version de solution
Comme c'est le cas avec d'autres projets que vous créez dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez utiliser le Gestionnaire de configuration pour spécifier des configurations de version de solution. Celles-ci vous permettent de déterminer les projets à inclure dans les différentes versions d'une solution et si elles seront déployées ou non. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]prend en charge les **déboguer** et **version** configurations de build.  
  
 Une solution de générer la configuration avec une coche dans le **générer** colonne vous permet de créer une solution et générer un assembly lorsque vous avez terminé. Si la case à cocher correspondante est également présente dans le **déployer** colonne, puis l’application sera déployée en fonction des paramètres de déploiement dans le Concepteur de projet.  
  
 Une référence complète à Configuration Manager et la configuration des options fournies par la boîte de dialogue zone, consultez le lien de référence suivant : [http://go.microsoft.com/fwlink/?LinkId=125365](http://go.microsoft.com/fwlink/?LinkId=125365).  
  
### <a name="to-configure-build-properties-in-configuration-manager"></a>Pour configurer les propriétés de version dans Gestionnaire de configuration  
  
1.  Dans le menu **Générer** , cliquez sur **Gestionnaire de configurations**.  
  
2.  Dans le **Configuration Manager** boîte de dialogue, sélectionnez une des options suivantes pour configurer les propriétés de génération.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Configuration**|Choisissez **version** ou **déboguer** configurations pour le projet. Vous pouvez également créer une configuration ou en modifier une.|  
    |**Plateforme**|Choisissez une plateforme pour le projet représentant l'architecture d'UC de l'assembly compilé. Vous pouvez également créer une plateforme ou en modifier une.|  
    |**Build**|Activez la case à cocher dans cette colonne pour qu'un projet soit généré ou regénéré en réponse à une commande de création pour la solution.|  
    |**Déployer**|Activez la case à cocher dans cette colonne pour qu'un projet soit déployé sur la base de paramètres de déploiement lorsqu'une commande de création est émise pour la solution ou le projet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment déployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)   
 [Comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md)