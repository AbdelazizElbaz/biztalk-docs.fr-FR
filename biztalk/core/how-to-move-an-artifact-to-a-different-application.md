---
title: "Comment déplacer un artefact vers une autre Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, moving
- applications, artifacts
ms.assetid: 861e7782-0566-4478-a0bd-f8ced1ea6d56
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdc28eb92b09d459ba5f05439572f07e3f35411f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-an-artifact-to-a-different-application"></a>Déplacement d'un artefact vers une autre application
Cette rubrique explique comment déplacer un artefact d'une application vers une autre au sein d'un groupe BizTalk à l'aide de la commande Déplacer vers l'application de la console Administration de BizTalk Server. Vous pouvez effectuer cette opération si vous devez utiliser un artefact qui existe déjà dans une autre application du même groupe BizTalk.  
  
 Lorsque vous déplacez un artefact, gardez les points importants suivants à l'esprit :  
  
-   **Les applications doivent être dans le même groupe.** La commande Déplacer vers l'application fonctionne uniquement si l'application contenant l'artefact à déplacer est dans le même groupe BizTalk que celle de destination. Pour déplacer un artefact vers une application se trouvant dans un autre groupe, exportez-le de l'application dans laquelle il est actuellement, puis importez-le dans la nouvelle, ou bien ajoutez-le à l'application. Pour obtenir des instructions, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md), [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md), et [comment créer ou ajouter un artefact](../core/how-to-create-or-add-an-artifact.md). Vous devez ensuite supprimer manuellement l’artefact à partir de l’application d’origine, comme décrit dans [comment supprimer un artefact d’une Application](../core/how-to-remove-an-artifact-from-an-application.md).  
  
-   **Déplacement d’un artefact peut également déplacer des artefacts sur laquelle il dépend ou qui en dépendent.** Lorsque vous déplacez un artefact vers une nouvelle application, les autres artefacts dont il dépend sont également déplacés, sauf si la nouvelle application comporte une référence aux applications contenant les artefacts dont celui déplacé dépend. Les artefacts qui dépendent de celui déplacé sont également déplacés, sauf si les applications les contenant comportent une référence à la nouvelle application. Lorsque vous déplacez un artefact, la liste des autres artefacts seront également déplacés sont affichés.  
  
> [!NOTE]
>  Pour utiliser le même artefact dans plusieurs applications, vous devez créer une référence de l'application dans laquelle vous souhaitez l'utiliser vers celle dans laquelle il se trouve actuellement. Ceci est dû au fait que certains types d'artefact doivent être uniques au sein d'un groupe BizTalk. Pour plus d’informations, consultez [artefacts que doit être Unique dans une Application ou d’un groupe](../core/artifacts-that-must-be-unique-in-an-application-or-group.md). Pour obtenir des instructions sur l’ajout de références, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md). Sachez que l'ajout d'une référence à une autre application crée des dépendances entre les applications et affecte la manière dont vous devez les déployer. Pour plus d’informations, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-move-an-artifact-to-a-different-application"></a>Pour déplacer un artefact vers une autre application  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk, puis l'application contenant l'artefact à déplacer.  
  
3.  Cliquez sur le dossier contenant l’artefact que vous souhaitez déplacer, cliquez sur l’artefact, puis cliquez sur **déplacer vers l’Application**.  
  
4.  Dans le **application de Destination** zone, cliquez sur la flèche, puis cliquez sur l’application à laquelle vous souhaitez déplacer l’artefact.  
  
     Le **déplacement des artefacts** affiche l’artefact à déplacer, ainsi que tous les artefacts dépendants, qui seront également déplacés.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)