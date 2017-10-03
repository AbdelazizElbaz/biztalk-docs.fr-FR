---
title: "L’utilisation d’IntelliSense pour créer un fichier de Configuration de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 349ea1bf-a5d1-4464-bf4b-d8746c622377
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7be3f79545db81a0127fc8d004d71c758069a55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-intellisense-to-create-an-interceptor-configuration-file"></a>Utilisation d'IntelliSense pour créer un fichier de configuration d'intercepteur
Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], la fonctionnalité IntelliSense et la validation de schéma vous permettent de créer des fichiers de configuration de l'intercepteur valides au niveau du schéma. L'utilitaire de gestion de l'analyse BAM valide un fichier de configuration de l'intercepteur d'après un schéma de configuration de base et, si le fichier n'est pas valide, il n'autorise pas le déploiement de ce schéma. Si un fichier réussit cette validation, il est ensuite soumis à validation au moment de l'exécution sur la base de schémas spécifiques à la technologie, comme les schémas [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] ou [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]. Si des erreurs surviennent, l'interception n'a pas lieu. Ces erreurs peuvent être évitées en utilisant la validation de schéma dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] au moment de la création du fichier de configuration de l'intercepteur.  
  
> [!NOTE]
>  Les exemples de fichiers XSD de configuration de l'intercepteur de l'analyse BAM sont installés avec les fichiers du Kit de développement logiciel (SDK). Ils se trouvent dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\BAM\InterceptorXSDs :  
>   
>  -   CommonInterceptorConfiguration.xsd  
> -   WcfInterceptorConfiguration.xsd  
> -   WorkflowInterceptorConfiguration.xsd  
  
### <a name="to-obtain-a-copy-of-the-interceptor-schemas"></a>Pour obtenir une copie des schémas de l'intercepteur  
  
1.  Ouvrez le Bloc-notes ou un autre éditeur de texte.  
  
2.  Accédez à la [schéma de Configuration de l’intercepteur](../core/interceptor-configuration-schema.md) rubrique.  
  
3.  Coller le contenu dans un nouveau document dans l’éditeur de texte ouvert, puis enregistrez le fichier comme un fichier texte en utilisant le nom **CommonInterceptorConfiguration.xsd** (ou un de votre choix) sur votre disque dur.  
  
4.  Répétez ces étapes pour le [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] schéma et [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] rubriques de schéma en utilisant les noms de fichier **WorkflowInterceptorConfiguration.xsd** et **WcfInterceptorConfiguration.xsd** ou des noms de votre choix.  
  
### <a name="to-use-intellisense-with-your-interceptor-configuration-file"></a>Pour utiliser la fonctionnalité IntelliSense avec le fichier de configuration de l'intercepteur  
  
1.  Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **fichier**.  
  
3.  Dans le **nouveau fichier** boîte de dialogue, sélectionnez **fichier XML** puis cliquez sur **ouvrir**.  
  
4.  Afficher le volet Propriétés en cliquant sur le volet d’édition, puis en cliquant **propriétés**.  
  
5.  Dans le volet Propriétés, cliquez sur **schémas**, puis cliquez sur le bouton de sélection (**...** ).  
  
6.  Dans le **schémas XML** boîte de dialogue, cliquez sur **ajouter** , puis accédez à l’emplacement des schémas et sélectionnez **CommonInterceptorConfiguration.xsd** et  **WcfInterceptorConfiguration.xsd** si vous travaillez avec un [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] fichier de configuration de l’intercepteur, ou **WorkflowInterceptorConfiguration.xsd** si vous travaillez avec un [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] fichier de configuration de l’intercepteur.  
  
    > [!NOTE]
    >  Si vous avez enregistré ces fichiers sous des noms différents, sélectionnez-les.  
  
7.  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] valide alors le fichier de configuration de l'intercepteur une fois celui-ci ouvert et offre une aide IntelliSense à mesure que vous créez et modifiez le fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma Windows Workflow Foundation](../core/windows-workflow-foundation-schema.md)   
 [Schéma Windows Communication Foundation](../core/windows-communication-foundation-schema.md)