---
title: "Gérer des schémas | Documents Microsoft"
description: "Utiliser l’Administration de BizTalk pour utiliser des schémas dans BizTalk Server, y compris l’affichage et masquage des propriétés, afficher le langage XSD, activer le suivi"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5632e79-b182-41c9-9138-eb88b44e3172
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0d7fe3eee97cf81c668ffe90fd9c0897af23cc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-schemas"></a>Gérer des schémas

## <a name="overiew"></a>Présentation
Cette section fournit des instructions sur la gestion des orchestrations à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les schémas sont utilisés par les pipelines et les orchestrations pour représenter le message qui sera traité.  
  
 Ils sont créés dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et compilés dans les assemblys BizTalk. Vous ne pouvez pas ajouter un schéma de manière individuelle à une application. L'ajout s'effectue dans les cas suivants :  
  
-   Lorsque vous ajoutez un assembly BizTalk contenant un schéma à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
-   Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant un schéma, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
-   Lorsqu’un développeur déploie dans une application d’un assembly contenant un schéma à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
 Pour des informations générales sur les schémas, consultez [schémas](../core/schemas.md). Pour plus d’informations sur le développement des schémas, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md).  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Afficher et masquer les schémas de propriété](../core/how-to-show-and-hide-property-schemas.md)  
  
-   [Afficher la définition de schéma (XSD) d’un schéma](../core/how-to-view-the-schema-definition-xsd-of-a-schema.md)  
  
-   [Configurer le suivi d’un schéma](../core/how-to-configure-tracking-for-a-schema.md)  
  
-   [Supprimer un schéma à partir d’une Application](../core/how-to-remove-a-schema-from-an-application.md)