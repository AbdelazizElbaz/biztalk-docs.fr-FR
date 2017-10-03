---
title: Comment actualiser une ressource | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [resources], refreshing
- refreshing resources
- resources, refreshing
ms.assetid: d6ff7c9d-8aaf-42a4-b1a3-00c05f6ac869
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bee05b9f137bbec92eccfa217084b66f1e5bf8ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-refresh-a-resource"></a>Actualisation d'une ressource
La présente rubrique explique comment actualiser un artefact de ressource à l'aide de la console Administration de BizTalk Server. Cette opération permet de mettre à jour les informations liées à l'artefact dans la base de données de gestion BizTalk. Une autre façon de procéder consiste à ajouter l’artefact à l’application à l’aide de l’outil BTSTask [commande AddResource](../core/addresource-command.md) avec l’option de remplacement.  
  
 Les artefacts de ressource se trouvent dans le dossier Ressources de l'application. Vous pouvez actualiser un artefact de ressource lorsque vous modifiez le fichier source et que vous souhaitez remplacer ce fichier par le nouveau dans l'application.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-refresh-a-resource-artifact"></a>Pour actualiser un artefact de ressource  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant l’artefact de ressource à actualiser, puis développez l’application contenant l’artefact.  
  
3.  Cliquez sur le **ressources** dossier, avec le bouton droit le fichier à actualiser, puis cliquez sur **modifier**.  
  
4.  Dans le **modifier les ressources** boîte de dialogue, sélectionnez le fichier à actualiser, puis cliquez sur **Actualiser**.  
  
5.  Accédez au fichier mis à jour avec lequel vous souhaitez remplacer le fichier actuel, puis cliquez sur **OK**.  
  
     Le fichier existant est remplacé par le fichier mis à jour. En outre, la configuration, les paramètres affichés sur la **Options** onglet de la **modifier les ressources** boîte de dialogue sont appliquées au fichier actualisé. Pour plus d’informations sur la modification de ces paramètres, cliquez sur **aide** dans la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Scripts de pré-traitement et post-traitement](../core/managing-pre-and-post-processing-scripts.md)   
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [La gestion des ressources](../core/managing-resources.md)