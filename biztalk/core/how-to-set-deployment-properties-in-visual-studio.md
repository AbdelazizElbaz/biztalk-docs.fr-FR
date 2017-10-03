---
title: "Comment définir des propriétés de déploiement dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2c6752e-c50d-4dd0-ac07-bf36ca10559c
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 079167f7607f434e48e29e90029468cd952c5620
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-deployment-properties-in-visual-studio"></a>Définition des propriétés de déploiement dans Visual Studio
Pour pouvoir déployer une solution de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans une application BizTalk, vous devez au préalable définir des propriétés de projet. Si une solution dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] contient plusieurs projets, vous devez configurer les propriétés de chacun d'entre eux séparément.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures décrites dans cette rubrique, vous devez être connecté avec un compte disposant d'une autorisation de lecture/écriture sur le système de fichiers local. Le compte des administrateurs de l'ordinateur local dispose de cette autorisation.  
  
### <a name="to-enable-project-deployment-in-configuration-manager"></a>Pour activer le déploiement de projet dans le Gestionnaire de configuration  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] cliquez sur **générer** dans le menu principal, puis cliquez sur **Configuration Manager**.  
  
2.  Vérifiez le **déployer** option pour chaque projet qui doit être déployé à partir de la solution ouverte.  
  
### <a name="to-configure-project-properties"></a>Pour configurer les propriétés de projet  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions avec le bouton droit un projet pour lequel vous souhaitez configurer les propriétés, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur le **déploiement** onglet Concepteur de projets.  
  
3.  Configurer les propriétés de projet, comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
4.  Répétez les étapes 1 à 3 pour chaque projet de la solution.  
  
    |Propriété|Valeur|Explication|  
    |--------------|-----------|-----------------|  
    |Application Name|\<Name>|Nom de l'application BizTalk dans laquelle déployer les assemblys de ce projet. Si l'application existe déjà, les assemblys seront ajoutés à celle-ci lors du déploiement du projet. Si l'application n'existe pas, elle sera créée. Si ce champ est vide, les assemblys sont déployés dans l'applications BizTalk par défaut du groupe actuel. Les noms incluant des espaces doivent être placés entre guillemets doubles (").|  
    |Base de données de configuration|\<Nom de base de données de gestion BizTalk >|Nom de la base de données de gestion BizTalk pour le groupe, BizTalkMgmtDb par défaut.|  
    |Server|\<Nom du serveur >|Nom de l'instance SQL Server qui héberge la base de données de gestion BizTalk sur l'ordinateur local. Dans le cas d'une installation sur un seul ordinateur, il s'agit généralement du nom de l'ordinateur local. **Remarque :** si vous déplacez ce projet BizTalk vers un autre ordinateur, vous devrez probablement modifier la propriété de serveur afin de refléter le nouveau nom d’ordinateur avant de pouvoir déployer l’assembly.|  
    |Redéployer|True ou False|La définition de cette propriété sur True (valeur par défaut) vous permet de redéployer les assemblys BizTalk sans changer le numéro de version.|  
    |Installer dans le Global Assembly Cache|True ou False|La définition de cette propriété sur True (valeur par défaut) installe les assemblys dans le Global Assembly Cache (GAC) de l'ordinateur local lors de l'installation de l'application. Définissez cette propriété sur False uniquement si vous prévoyez d'utiliser d'autres outils pour cette installation, tels que gacutil.|  
    |Redémarrer les instances d'hôte|True ou False|La définition de cette propriété sur True redémarre automatiquement toues les instances d'hôte s'exécutant sur l'ordinateur local lors du redéploiement de l'assembly. Si vous la définissez sur False (valeur par défaut), vous devez redémarrer les instances d'hôte manuellement lors du redéploiement d'un assembly. **Remarque :** si vous redéployez des assemblys de niveau de la solution, les instances d’hôte seront redémarrées une fois pour chaque projet dispose cette option est définie sur True. Cela peut donner lieu à des redémarrages multiples. Si vous prévoyez de redéployer au niveau de la solution, vous pouvez définir cette propriété sur True sur un seul projet de la solution afin d'éviter des redémarrages d'instance d'hôte multiples. Elle doit être définie sur le dernier projet qui sera redéployé dans la solution. Par ailleurs, si une instance d'hôte est arrêtée lors de l'exécution du redéploiement, elle ne sera pas démarrée.|  
    |Activer les tests unitaires|True ou False|Spécifie s’il faut activer les tests unitaires pour le projet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)