---
title: "Comment modifier l’Application par défaut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, default
- applications, modifying
- modifying, applications
ms.assetid: cfa5e88f-0bbb-4edd-a840-722dcdcce266
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33b4ffb6fbbb2463b20a7d344d0f7f27811de23b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-default-application"></a>Comment modifier l’Application par défaut
Cette rubrique décrit comment changer d'application par défaut en modifiant les propriétés d'une application dans la console Administration de BizTalk Server. Vous pouvez également modifier l’application par défaut en créant une nouvelle application et en spécifiant que l’application par défaut, comme décrit dans [la création d’une Application](../core/how-to-create-an-application.md).  
  
 Lorsque vous installez BizTalk Server, une application par défaut baptisée BizTalk Application 1 est créée dans la base de données de gestion BizTalk et apparaît dans la console Administration de BizTalk Server. Lorsque vous effectuez une mise à niveau d'une version antérieure de BizTalk Server, vos artefacts sont automatiquement placés dans cette application. En outre, si vous importez un fichier Windows Installer (.msi) à l'aide de BTSTask sans spécifier d'application, les artefacts de ce fichier .msi sont importés dans l'application par défaut.  
  
 Vous n'êtes pas autorisé à supprimer l'application par défaut, vous ne pouvez qu'en changer. Si vous changez d'application par défaut, vous pouvez si vous le souhaitez supprimer l'ancienne application par défaut. Pour obtenir des instructions, consultez [comment supprimer une Application BizTalk du groupe BizTalk](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).  
  
 Si vous changez d'application par défaut, tous les artefacts sont conservés dans l'application par défaut initiale. Si vous le désirez, vous pouvez explicitement les en extraire. Pour obtenir des instructions, consultez [comment déplacer un artefact vers une autre Application](../core/how-to-move-an-artifact-to-a-different-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-change-the-default-application"></a>Modification de l'application par défaut  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, cliquez sur l’application que vous souhaitez rendre la valeur par défaut, puis cliquez sur **propriétés**.  
  
3.  Sélectionnez le **transformer en application par défaut** case à cocher, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)