---
title: "Modifications apportées au système de projet BizTalk dans BizTalk Server 2013 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82f0dd18-073c-4cba-aa0d-48076c58f874
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dff1f35955229306bc2f39e0af670f939dec82da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="changes-to-biztalk-project-system-in-biztalk-server-2013"></a>Modifications apportées au système de projet BizTalk dans BizTalk Server 2013
Cette rubrique propose une présentation détaillée des modifications apportées au système de projet BizTalk dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="project-properties-are-displayed-in-project-designer-window"></a>Affichage des propriétés de projet dans la fenêtre du Concepteur de projet  
 Désormais, les propriétés d'un projet BizTalk Server sont affichées dans le Concepteur de projet de Visual Studio au lieu d'être affichées dans une boîte de dialogue Propriétés. Le Concepteur de projet centralise la gestion des propriétés, des paramètres et des ressources d'un projet. Il s'agit d'une fenêtre unique dans l'environnement de développement intégré (IDE) de Visual Studio, semblable à celle d'autres concepteurs tels que le Concepteur de formulaires ou le Concepteur de classes, et contient un nombre de pages accessibles via des onglets situés sur le côté gauche de la fenêtre. Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=190417](http://go.microsoft.com/fwlink/?LinkId=190417).  
  
## <a name="properties-for-schema-and-map-files-are-displayed-in-properties-window"></a>Affichage des propriétés relatives aux fichiers de schéma et de mappage dans la fenêtre Propriétés  
 Propriétés des fichiers de schéma et de mappage comme **nom d’Instance d’entrée** et **Instance d’entrée de mappage de Test** sont affichés dans la fenêtre Propriétés, avec à la place de dans une fonction **propriétés** boîte de dialogue.  
  
## <a name="add-web-reference-option-on-projects"></a>Option d'ajout de références Web aux projets  
 Le **ajouter une référence Web** option n’est pas disponible lorsque vous cliquez sur le nom du projet ou **références** dans l’Explorateur de solutions. Vous pouvez ajouter une référence Web à un service Web (.asmx) à l'aide de la procédure suivante :  
  
1.  Avec le bouton droit **références** dans le projet, puis cliquez sur **ajouter une référence de Service**.  
  
2.  Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **avancé**.  
  
3.  Dans le **paramètres de référence de Service** boîte de dialogue, cliquez sur **ajouter une référence Web**.  
  
4.  Tapez l’URL, puis cliquez sur **accédez**.  
  
5.  Cliquez sur **ajouter une référence** pour ajouter la référence Web.  
  
    > [!TIP]
    >  Après avoir ajouté une référence Web à un projet BizTalk, le **ajouter une référence Web** option est disponible sur les références, les références Web et les nœuds de projet.  
  
 Pour plus d’informations sur l’ajout de service et les références Web, consultez [http://go.microsoft.com/fwlink/?LinkId=131577](http://go.microsoft.com/fwlink/?LinkId=131577).  
  
## <a name="msbuild-integration"></a>Intégration de MSBUILD  
 Visual Studio utilise le format de fichier de projet MSBUILD pour stocker les informations de version des projets gérés, y compris des projets BizTalk. Pour plus d’informations, consultez [intégration de MSBUILD avec Visual Studio](../core/msbuild-integration-with-visual-studio.md).  
  
## <a name="team-foundation-server-integration"></a>Intégration de Team Foundation Server  
 Vous pouvez faire appel à Team Foundation Server en tant que système de contrôle de code source pour les projets BizTalk. Vous pouvez effectuer des opérations telles que l'archivage et l'extraction directement à partir de la fenêtre de l'Explorateur de solutions.  
  
## <a name="support-for-unit-testing"></a>Prise en charge des tests unitaires  
 Cette fonctionnalité vous permet de réaliser des tests unitaires sur les schémas, mappages et pipelines. Pour plus d’informations, consultez [tests unitaires avec les projets BizTalk Server](../core/unit-testing-with-biztalk-server-projects.md).  
  
## <a name="debug-map-feature"></a>Fonctionnalité de débogage des mappages  
 **Fonctionnalité de mappage de débogage**. vous pouvez déboguer un mappage (XSLT) à l'aide du débogueur Inline XSLT dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour plus d’informations, consultez [comment déboguer des mappages](../core/how-to-debug-maps.md).  
  
## <a name="migrating-biztalk-server-projects"></a>Migration des projets BizTalk Server  
 Les projets Visual Studio développés pour les versions antérieures à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent être migrés vers l’environnement de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] à l’aide de l’Assistant Conversion de Visual Studio. Pour plus d’informations, consultez [migration d’un projet BizTalk Server](../core/migrating-a-biztalk-server-project.md).  
  
## <a name="release-and-debug-build-types"></a>Types de version Débogage et Version finale  
 Projets BizTalk ont maintenant deux types de build : **version** et **déboguer**, qui remplace **développement** et **déploiement** de version antérieure versions. Toutefois, vous continuerez à voir les **développement** et **déploiement** configurations pour les projets qui sont migrés à partir de [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)].  
  
## <a name="embedding-tracking-and-debugging-information"></a>Incorporation du suivi et informations sur le débogage  
 Le **incorporer des informations de suivi** et **générer des informations de débogage** propriétés de configuration de sortie sont remplacées par le **définir la constante TRACE** et **Définir la constante DEBUG** options de génération le **générer** onglet du Concepteur de projet. Le **génération de code compatibilité BPEL** propriété de configuration est remplacée par **génération de code compatibilité BPEL** propriété dans la fenêtre de propriétés du projet.  
  
> [!IMPORTANT]
>  L'Assistant Conversion de Visual Studio se charge de migrer automatiquement les paramètres mentionnés précédemment vers le nouvel environnement.  
  
## <a name="user-access-control"></a>Contrôle d'accès d'utilisateur  
 Visual Studio bloque le déploiement d'un projet BizTalk sur un ordinateur où la fonctionnalité de contrôle d'accès d'utilisateur (UAC) est activée, à moins que vous n'exécutiez Visual Studio avec des privilèges d'administrateur. Pour exécuter Visual Studio avec des privilèges d’administrateur, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Visual Studio**, avec le bouton droit  **Microsoft Visual Studio \<version >**, puis cliquez sur **exécuter en tant qu’administrateur**.  
  
## <a name="c-files-in-a-biztalk-project"></a>Fichiers C# dans un projet BizTalk  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]vous permet de combiner des classes d’assistance et des artefacts BizTalk pour les besoins d’empaquetage souple uniquement.  Toutefois, vous ne pouvez pas ajouter un nouveau fichier c# directement à l’aide du **ajouter un nouvel élément** ou **ajouter une nouvelle classe** options de menu.  
  
## <a name="generatecsfiles-registry-key-is-obsolete"></a>Clé de Registre GenerateCSFiles obsolète  
 Le **GenerateCSFiles** clé de Registre est désormais obsolète. Tous les fichiers .cs générés sont affichés dans la fenêtre de l'Explorateur de solutions. Vous devrez peut-être cliquer sur **afficher tous les fichiers** élément de barre d’outils dans la fenêtre de l’Explorateur de solutions pour visualiser les fichiers .cs associés à certains des éléments BizTalk.