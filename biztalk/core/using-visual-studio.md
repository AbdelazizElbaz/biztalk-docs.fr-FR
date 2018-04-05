---
title: À l’aide de Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio
ms.assetid: 1ef68df2-5205-4d96-9e0f-0ae78800a121
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b48f5aca0bd1e5c17d942e332f7f3d223d752b67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-visual-studio"></a>Utilisation de Visual Studio
Dans le système de projet BizTalk, vous pouvez utiliser de nombreux outils disponibles dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ainsi que de nombreux outils conçus spécifiquement pour créer des applications qui s'exécutent dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette rubrique décrit certaines des procédures courantes que vous pouvez utiliser pour créer une application s'exécutant sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Lorsque vous utilisez le système de projet BizTalk, vous utilisez de nombreux composants de la même interface utilisateur, tels que l'Explorateur de solutions et la fenêtre Propriétés, pour créer votre application. De plus, il existe des composants, tels que l’Éditeur BizTalk, qui ne sont disponibles qu'une fois que vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez utiliser ces composants d'interface utilisateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec n'importe quel système de projet, mais ils vous permettent plus spécifiquement de construire des applications s’exécutant sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Le système de projet BizTalk utilise de nombreux menus et de nombreuses options identiques aux autres systèmes de projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Toutefois, certaines de ces options sont nouvelles, non disponibles, développées ou limitées lorsque vous utilisez le système de projet BizTalk. Cette rubrique décrit les différents menus disponibles dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et la façon dont ils interagissent avec le système de projet BizTalk.  
  
> [!NOTE]
>  Les rubriques suivantes se concentrent sur la présentation des menus et options de menus dont le comportement diffère de celui de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="file-menu"></a>Menu Fichier  
 La plupart de la **fichier** commandes de menu fonctionnent de manière identique pour les projets BizTalk et pour les autres [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projets. Certaines ne sont pas prises en charge ou ne sont pas disponibles lorsque vous travaillez sur les projets BizTalk. Par exemple, le **impression** commande n’est pas prise en charge lorsque vous travaillez avec des pipelines.  
  
## <a name="view-menu"></a>Menu Afficher  
 Le tableau suivant répertorie les fenêtres de système de projet BizTalk, les barres d’outils et boîtes à outils disponibles à partir de la **vue** menu.  
  
|Nom de sous-menu|Nom de sous-menu (le cas échéant)| Description|  
|------------------|------------------------------------|-----------------|  
||||  
|**Autres fenêtres**|**Vue Orchestration**|La Vue Orchestration est une fenêtre disponible permettant d’ajouter, de supprimer et d’examiner des paramètres d'orchestration, des ports et des types de ports, des messages et des types de messages à parties multiples, des ensembles de corrélations et des types de corrélations, des liens de rôle et des types de liens de rôle, des étendues et des propriétés d'orchestration. **Remarque :** cette fenêtre est disponible uniquement à partir d’une orchestration ouverte.|  
|**Autres fenêtres**|**Éditeur d’expression**|L'Éditeur d'expression est une fenêtre disponible correspondant à un éditeur de texte [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] standard dans lequel les options IntelliSense permettent d'entrer des expressions complexes.|  
|**Boîte à outils**|**Composants de Pipeline BizTalk**|Il s’agit d’une liste des composants de pipeline que vous pouvez faire glisser vers la surface de conception de pipeline. Vous ne pouvez ajouter que des composants de pipeline disponibles à votre pipeline actif.|  
|**Boîte à outils**|**Orchestrations BizTalk**|Il s’agit d’une liste des formes d’orchestration que vous pouvez faire glisser vers la surface de conception d’orchestration.|  
|**Boîte à outils**|**Mappeur BizTalk**|Il s’agit d’une liste des fonctoids que vous pouvez faire glisser vers la surface de grille de mappage. Les fonctoids sont groupés selon leur fonction.|  
|**Barres d'outils**|**Éditeur BizTalk**|Outil visuel facilitant le processus de création de schémas de documents structurés, spécifié dans le langage XSD (XML Schema definition language) pour les formats XML et non XML.|  
|**Barres d'outils**|**Mappeur BizTalk**|Outil d’interface utilisateur graphique simplifiant le processus de spécification d’une transformation de document XML, à partir de deux schémas créés avec l’Éditeur BizTalk, produisant une feuille de style XSLT (Extensible Stylesheets Language Transformations) comme résultat de compilation.|  
  
## <a name="project-menu"></a>Menu Projet  
 Le tableau suivant répertorie certaines des commandes sur le **projet** menu.  
  
|Nom de sous-menu| Description|  
|------------------|-----------------|  
|**Ajouter une référence**|Utilisez cette option de menu pour faire référence à d’autres projets, projets .NET ou projets COM.|  
|**Ajouter une référence de Service**|Utilisez cette option de menu pour ajouter des références de service WCF. Vous utilisez également cet élément pour ajouter des références Web en cliquant sur **avancé** sur la **ajouter une référence de Service** boîte de dialogue.|  
|**Ajouter les éléments générés**|Utilisez cette option de menu pour ajouter un fichier de schéma ou d'adaptateur ou pour utiliser un service WCF.|  
|**Ajouter une référence de Service d’adaptateur**|Cette option de menu permet de parcourir (et rechercher dans) les métadonnées, et de générer des classes de proxy .NET CLR à l'aide des opérations ou des types sélectionnés. **Remarque :** cet élément apparaît dans le menu BizTalk uniquement si au moins une carte (fourni avec [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]) est installé sur votre ordinateur.|  
|**Ajouter consommer la référence d’adaptateur**|Cette option de menu permet de parcourir (et rechercher dans) les métadonnées de l'adaptateur, puis de générer des schémas XML pour des opérations sélectionnées. **Remarque :** cet élément apparaît dans le menu BizTalk uniquement si au moins une carte (fourni avec [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]) est installé sur votre ordinateur.|  
  
 Pour plus d’informations sur l’ajout de références Web aux services BizTalk Web, consultez [Ajout de références Web](../core/adding-web-references.md).  
  
## <a name="build-menu"></a>Menu Version  
 Le **générer** menu contient les commandes de génération. Il contient également la commande à exécuter **Configuration Manager** pour définir des options de configuration de build et déploiement. Pour déployer un projet, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, puis cliquez sur le **déployer** commande. Vous ne devez utiliser cette méthode de déploiement que lorsque vous développez votre application ou avec un scénario simple. Cette méthode de déploiement ne **pas** effectuer le suivi des versions, et vous pouvez facilement remplacer les versions précédentes d’un assembly. Réutiliser la même version est utile dans une étape de développement ou de test, mais pas dans l'environnement de production. Pour plus d’informations sur le déploiement, consultez [gestion et déploiement d’applications BizTalk compréhension](../core/understanding-biztalk-application-deployment-and-management.md).  
  
 Pour ajouter vos artefacts BizTalk à la base de données de gestion BizTalk, exécutez l'Assistant Déploiement. Pour plus d’informations sur l’Assistant Déploiement des assemblys, consultez [comment déployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  
  
> [!NOTE]
>  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] contient une version de Dotfuscator qui obscurcira un assembly compilé, en renommant les symboles et les autres identificateurs afin de préserver votre propriété intellectuelle. Les assemblys exécutés via cet outil ne peuvent être déployés.  
  
## <a name="debug-menu"></a>Menu Débogage  
 Le système de projet BizTalk prend en charge la **déboguer** commandes de menu. Pour plus d’informations sur le débogage dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [débogage des Orchestrations](../core/debugging-orchestrations.md).  
  
## <a name="biztalk-menu"></a>Menu BizTalk  
 Lorsque vous travaillez avec un projet, le **BizTalk** menu s’affiche lorsque vous ouvrez l’Éditeur BizTalk ou le Mappeur BizTalk ou le Concepteur d’Orchestration BizTalk. En d'autres termes, il s'affiche lorsque vous tentez de modifier un schéma, un mappage ou une orchestration.  
  
> [!NOTE]
>  Il est possible d'accéder aux outils Concepteur d'orchestration, Éditeur BizTalk et Mappeur BizTalk à partir d'autres systèmes de projets dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], mais leur comportement risque alors d'être imprévisible. Utilisez le Concepteur d'orchestration, l'Éditeur BizTalk et le Mappeur BizTalk dans le contexte d'un projet BizTalk.  
  
## <a name="help-menu"></a>Menu aide  
 Le tableau suivant répertorie certaines des commandes sur le **aide** menu comme ils se rapportent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
|Commande de menu| Description|  
|------------------|-----------------|  
|**Aide dynamique**|Cette commande de menu ouvre le **aide dynamique** onglet qui génère dynamiquement des rubriques basées sur la tâche.|  
|**Sommaire**|Cette commande de menu ouvre le **contenu** onglet et affiche toutes les collections d’aide installées. Pour pouvoir afficher le sommaire, la documentation des produits [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit être installée.|  
|**À propos de Microsoft BizTalk Server**|Cette commande de menu ouvre le **sur Microsoft BizTalk Server** boîte de dialogue. Celle-ci affiche des informations sur le produit [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|**Index**|La documentation d'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'est pas accessible à partir de l'index dans cette version.|  
|**Recherche**|Absence de filtre pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide dans cette version, mais si vous sélectionnez **(aucun filtre)** dans les **filtrés par** la liste déroulante, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation d’aide est disponible pour recherches.|  
  
## <a name="property-pages"></a>Pages de propriétés  
 Les pages de propriétés du Concepteur de projet permettent de configurer les propriétés d'assembly et de déploiement de votre projet BizTalk.  
  
### <a name="procedures"></a>Procédures  
  
##### <a name="to-configure-assembly-project-properties"></a>Pour configurer les propriétés d'assembly d'un projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet.  
  
2.  Sur le **projet** menu, cliquez sur **propriétés** pour activer le Concepteur de projet.  
  
3.  Cliquez sur le **Application** onglet.  
  
4.  Cliquez sur **informations de l’Assembly** et mettre à jour les propriétés de l’assembly de votre choix.  
  
    > [!NOTE]
    >  Utilisez le **signature** onglet du Concepteur de projet pour spécifier l’emplacement du fichier de clé de l’assembly si vous utilisez des certificats avec votre application s’exécute sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##### <a name="to-configure-deployment-properties"></a>Pour configurer les propriétés de déploiement  
  
1.  Sélectionnez le projet dont vous souhaitez configurer les propriétés de déploiement.  
  
2.  Sur le **projet** menu, cliquez sur **propriétés** pour activer le Concepteur de projet.  
  
3.  Cliquez sur le **déploiement** onglet et mettre à jour les propriétés de votre déploiement.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de développement](../core/developer-tools.md)