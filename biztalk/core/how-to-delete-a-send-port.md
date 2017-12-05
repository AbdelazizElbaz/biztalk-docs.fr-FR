---
title: "Comment supprimer un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [send ports], deleting
- send ports, deleting
- deleting, send ports
ms.assetid: aff5980e-57bf-400c-82bd-3d02e143f227
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63355f742f12fbbaf57ccde7a1406dbb694ee073
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-delete-a-send-port"></a>Suppression d'un port d'envoi
Cette rubrique explique comment supprimer un port d'envoi d'une application BizTalk à l'aide de la console Administration de BizTalk Server. Lors de cette opération, le port d'envoi est également supprimé de la base de données de gestion BizTalk associée au groupe.  
  
> [!IMPORTANT]
>  Lorsque vous supprimez un port d'envoi, les instances de service en cours d'exécution associées à ce port ne peuvent plus obtenir d'informations de configuration sur celui-ci, telles que son nom. Bien que ces informations sont mises en cache, si l'instance de service doit renvoyer un message, elle ne parviendra pas à le faire, et le message sera interrompu. Avant de supprimer un port d’envoi, vous devez vérifier qu’il n’y a aucune exécution service des instances, comme décrit dans [comment afficher les informations d’Instance pour un Port d’envoi](../core/how-to-view-instance-information-for-a-send-port.md).  
  
 Vous ne pouvez supprimer un port d'envoi que s'il remplit les conditions suivantes :  
  
-   Aucune orchestration n'est liée au port d'envoi. Si c’est le cas, vous pouvez supprimer la liaison en suivant les instructions de [comment annuler une Orchestration](../core/how-to-unbind-an-orchestration.md).  
  
-   Le port d'envoi est arrêté et désinscrit. Pour obtenir des instructions sur l’arrêt et Désinscription d’un port d’envoi, consultez [comment désinscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-unenlist-a-send-port-or-send-port-group.md) et [comment arrêter un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-stop-a-send-port-or-send-port-group.md).  
  
-   Le port d'envoi n'est pas référencé par un tiers. Pour obtenir des instructions sur la suppression d’une référence à un port d’envoi d’un tiers, consultez [comment afficher ou modifier un tiers](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).  
  
-   Le port d'envoi n'est pas inclus dans un groupe de ports d'envoi. Pour obtenir des instructions sur la suppression d’un port d’envoi à partir d’un groupe de ports d’envoi, consultez [comment supprimer un Port d’envoi à partir d’un groupe de ports d’envoi](../core/how-to-remove-a-send-port-from-a-send-port-group.md).  
  
> [!NOTE]
>  Le développeur peut supprimer un port d'envoi au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-delete-a-send-port"></a>Pour supprimer un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez Administration de BizTalk Server, développez le groupe BizTalk, développez Applications, puis développez l’application contenant le port d’envoi que vous souhaitez supprimer  
  
3.  Cliquez sur **Ports d’envoi**, cliquez sur le port d’envoi, puis cliquez sur **supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des ports d’envoi](../core/creating-and-configuring-send-ports.md)