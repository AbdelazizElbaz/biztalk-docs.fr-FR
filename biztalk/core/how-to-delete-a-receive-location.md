---
title: "Comment supprimer un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive locations], deleting
- receive locations, deleting
- deleting, receive locations
ms.assetid: aa859355-af4c-48d9-b224-78fd3ef618fc
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19828b7b456e872af78c2bae3c89ed75828a32ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-receive-location"></a>Suppression d'un emplacement de réception
Cette rubrique explique comment supprimer un emplacement de réception à l'aide de la console Administration de BizTalk Server. Lorsque vous supprimez un emplacement de réception, il disparaît de la base de données de gestion BizTalk et ne s'affiche plus dans la console Administration de BizTalk Server.  
  
 Lorsque vous supprimez un emplacement de réception, gardez les points importants suivants à l'esprit :  
  
-   Avant de pouvoir supprimer un emplacement de réception, il doit d’abord être désactivé, comme décrit dans [comment désactiver un emplacement de réception](../core/how-to-disable-a-receive-location.md).  
  
-   Il est impossible de supprimer l'emplacement de réception principal pour un port de réception. Lorsque vous tentez d'effectuer cette action, un message d'erreur s'affiche. Pour supprimer un emplacement de réception principal, vous pouvez supprimer le port de réception, ce qui supprime également tous les emplacements de réception qu'il contient, ou vous pouvez faire d'un autre emplacement de réception l'emplacement principal, puis supprimer l'emplacement principal d'origine. Pour obtenir des instructions sur la création d’un emplacement de réception l’emplacement de réception principal, consultez [comment modifier les propriétés d’un emplacement de réception](../core/how-to-edit-the-properties-of-a-receive-location.md).  
  
-   Après avoir supprimé un emplacement de réception, redémarrez les processus de travail de l'hôte isolé correspondant à l'emplacement de réception supprimé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-delete-a-receive-location"></a>Pour supprimer un emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle vous souhaitez supprimer un emplacement de réception.  
  
3.  Cliquez sur **emplacements de réception**, avec le bouton droit à l’emplacement de réception à supprimer, puis cliquez sur **supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)