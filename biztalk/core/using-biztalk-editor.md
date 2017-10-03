---
title: "À l’aide de l’Éditeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22021272-f028-4db3-ad8a-fb89a5340910
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdb293e6255042a46ecef16855d723c38543310c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-editor"></a>Utilisation de l'Éditeur BizTalk

## <a name="overview"></a>Vue d'ensemble
L'Éditeur BizTalk réside dans le shell Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Certaines fonctionnalités de l'Éditeur BizTalk utilisent des éléments d'interface utilisateur existants du shell [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Par exemple, vous utilisez la **fichier**, **modifier**, et **vue** menus comme vous le feriez pour d’autre développement dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Informations sur ces fonctionnalités communes sont disponibles à partir de la **aide** menu.  
  
 L'Éditeur BizTalk devient actif lorsque vous ajoutez un nouveau schéma à un projet BizTalk, lorsque vous ouvrez un schéma existant (un fichier .xsd) dans un projet BizTalk, ou lorsque vous réactivez un schéma en cliquant sur son onglet dans la fenêtre d'édition principale de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  L’Éditeur BizTalk enregistre les fichiers de schéma avec le codage de caractères utf-16.  

## <a name="views"></a>Vues  
 La figure suivante montre les différentes vues dans le shell Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] qui font partie de l'Éditeur BizTalk.  
  
 ![Différentes parties d’un projet BizTalk](../core/media/differentpartsofbiztalkserver.gif "DifferentpartsofBizTalkServer")  
  
 L'Éditeur BizTalk se compose des vues suivantes dans le shell Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ainsi que des boîtes de dialogue qui leur sont associées :  
  
-   **Arborescence du schéma.** Cette vue se trouve sur le côté gauche de la main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre d’édition. Vous créez activement votre schéma dans cette vue en élaborant la structure arborescente décrivant la structure du message que le schéma définit. Pour plus d’informations sur la représentation des schémas BizTalk dans l’arborescence de schéma, consultez [représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md).  
  
-   **Vue XSD.** Cette vue se trouve sur le côté droit de la main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre d’édition. Elle présente la structure du langage XSD (XML Schema definition) qui représente le schéma que vous créez dans l'arborescence de schéma. Cette vue est en lecture seule et vous est proposée pour vous familiariser avec la syntaxe XSD du schéma que vous créez. Si vous préférez, vous pouvez ajuster le séparateur de vue afin que la vue XSD ne soit qu’à peine visible.  
  
-   **Explorateur de solutions.** Cette vue se trouve sur le côté droit de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell. Elle affiche le projet BizTalk et les différents éléments qu’il contient. Utilisez l’Explorateur de solutions pour ajouter des schémas nouveaux et existants au projet et pour ouvrir les schémas qui font déjà partie du projet. Par exemple, pour créer un nouveau schéma, cliquez sur le projet BizTalk dans la fenêtre de l’Explorateur de solutions, cliquez sur **ajouter**, cliquez sur **un nouvel élément**, puis utilisez le **ajouter un nouvel élément** boîte de dialogue boîte de nommer et de créer un nouveau schéma.  
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]  **Fenêtre Propriétés.** vous utilisez cette vue pour examiner et définir la plupart des propriétés de schéma et de nœud. Quand vous sélectionnez un nœud dans l'arborescence de schéma ou que vous sélectionnez un schéma dans la fenêtre Explorateur de solutions, les propriétés correspondantes de ce nœud ou schéma sont affichées dans la fenêtre Propriétés à l’aide des paradigmes standard Visual Studio. Par exemple, les propriétés sont groupées en catégories, et peuvent être affichées par catégories ou dans l’ordre alphabétique. Pour plus d’informations sur les différents ensembles de propriétés qui sont disponibles lorsque différents types de nœuds, ou le schéma, sont sélectionnés, consultez la **référence du schéma de propriété** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 En plus de ces vues, vous pouvez interagir avec plusieurs boîtes de dialogue. Vous ouvrez généralement ces boîtes de dialogue lorsque vous modifiez une propriété complexe telle qu’une collection.  
  
 Cette section propose des informations sur les vues, les options et les touches de raccourci disponibles dans l’Éditeur BizTalk.  
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Comment gérer l’arborescence du schéma](../core/how-to-manage-the-schema-tree-view.md)  
  
-   [Comment gérer la vue XSD](../core/how-to-manage-the-xsd-view.md)  
  
-   [Comment gérer la fenêtre Propriétés](../core/how-to-manage-the-properties-window.md)  
  
-   [Comment gérer les autres fenêtres Visual Studio](../core/how-to-manage-other-visual-studio-windows.md)  
  
-   [À l’aide des commandes de l’Éditeur BizTalk](../core/using-biztalk-editor-commands.md)  
  
-   [Utilisation de grands schémas](../core/working-with-large-schemas.md)