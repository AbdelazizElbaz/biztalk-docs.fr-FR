---
title: "Comment ajouter une référence à une autre Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: applications, referencing
ms.assetid: 6a177560-ee1f-403a-a68a-ade409a39a35
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25668e7cfcb7d810d999c01eef28e5116b46c298
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-reference-to-another-application"></a>Ajout d'une référence à une autre application
La présente rubrique explique comment ajouter une référence d'une application vers une autre application à l'aide de la console Administration de BizTalk Server. Vous pouvez également ajouter une référence à l’autre application lorsque vous importez votre application à l’aide de l’Assistant Importation, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
 Vous ajoutez une référence lorsque vous voulez utiliser dans l'application actuelle un artefact existant déjà dans une autre application du même groupe BizTalk. Ceci est dû au fait que la plupart des types d'artefact doivent être uniques au sein d'un groupe BizTalk. Au lieu d'ajouter l'artefact en double à l'application actuelle, vous ajoutez une référence à l'application qui contient déjà cet artefact. Pour plus d’informations, consultez [artefacts que doit être Unique dans une Application ou d’un groupe](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  
  
 Il n'est pas nécessaire d'ajouter une référence pour utiliser un certificat ou un répertoire virtuel existant déjà dans une autre application. Par ailleurs, nous déconseillons cette pratique car elle peut entraîner la création de références circulaires.  
  
 Lorsque vous importez une application comportant des dépendances, les références peuvent également être importées. Si vous ajoutez une référence à une autre application, n'oubliez pas que cela conditionnera la manière dont vous devrez déployer les deux applications. Pour plus d’informations, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-add-a-reference-to-another-application"></a>Pour ajouter une référence à une autre application  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis cliquez avec le bouton droit sur l'application dans laquelle vous souhaitez créer une référence. Il s'agit de l'application dans laquelle vous voulez utiliser un artefact provenant d'une autre application.  
  
3.  Pointez sur **ajouter** puis cliquez sur **références**.  
  
4.  Dans **Applications**, activez la case à cocher de l’application à laquelle vous souhaitez ajouter une référence (l’application contenant l’ou les artefacts que vous souhaitez utiliser), puis cliquez sur **OK**.  
  
     La référence est ajoutée à l'application actuelle. Dans l'arborescence de la console, une icône Main est ajoutée à l'application référencée à partir de cette application afin d'indiquer qu'elle fait l'objet d'une référence par une ou plusieurs applications.  
  
     ![Icône d’application partagé](../core/media/sharedapplicationicon.gif "SharedApplicationIcon")  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)