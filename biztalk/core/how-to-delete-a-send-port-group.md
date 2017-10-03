---
title: "Comment supprimer un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send port groups, deleting
- managing [send port groups], deleting
- deleting, send port groups
ms.assetid: 90c01e58-d35c-4cb2-ac6d-92199199fb42
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86ddecbe657b8ea52a47133c5237bbad6a10b2f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-send-port-group"></a>Suppression d'un groupe de ports d'envoi
La présente rubrique explique comment supprimer un groupe de ports d'envoi d'une application BizTalk à l'aide de la console Administration de BizTalk Server. Lors de cette opération, le groupe de ports d'envoi est également supprimé de la base de données de gestion BizTalk associée au groupe. Supprimer un groupe de ports d'envoi ne supprime aucun des ports d'envoi qu'il contient.  
  
 Vous ne pouvez supprimer un groupe de ports d'envoi que s'il remplit les conditions suivantes :  
  
-   Le groupe de ports d'envoi n'est lié à aucune orchestration. Si c’est le cas, vous pouvez supprimer la liaison en suivant les instructions de [comment annuler une Orchestration](../core/how-to-unbind-an-orchestration.md).  
  
-   Le groupe de ports d'envoi est arrêté et désinscrit. Pour obtenir des instructions sur l’arrêt et Désinscription d’un port d’envoi, consultez [comment désinscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-unenlist-a-send-port-or-send-port-group.md) et [comment arrêter un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-stop-a-send-port-or-send-port-group.md).  
  
-   Le groupe de ports d'envoi n'est pas référencé par un tiers. Pour obtenir des instructions sur la suppression d’une référence à un groupe de ports d’envoi d’un tiers, consultez [comment afficher ou modifier un tiers](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-delete-a-send-port-group"></a>Pour supprimer un groupe de ports d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, **Applications**, puis développez l’application contenant le groupe de ports d’envoi que vous souhaitez supprimer.  
  
3.  Cliquez sur **groupes de ports d’envoi**, cliquez sur le groupe de ports d’envoi, puis cliquez sur **supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md)