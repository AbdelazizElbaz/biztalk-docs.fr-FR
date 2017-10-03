---
title: "Comment supprimer un Port d’envoi à partir d’un groupe de ports d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send port groups, deleting send ports
- managing [send port groups], deleting send ports
- managing [send ports], deleting send ports
- deleting, send ports
- send ports, deleting from send port groups
ms.assetid: a2289bfe-5bc9-4bc7-949c-5152ffb5bc62
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d109064a1286bcd622479a4075ef2d23dc8d320c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-send-port-from-a-send-port-group"></a>Suppression d'un port d'envoi d'un groupe de ports d'envoi
La présente rubrique explique comment supprimer un port d'envoi d'un groupe de ports d'envoi à l'aide de la console Administration de BizTalk Server. Lors de cette opération, le port d'envoi n'est pas supprimé de l'application ou de la base de données de gestion BizTalk.  
  
 Avant de pouvoir supprimer un port d'envoi, il doit être arrêté ou désinscrit.  
  
> [!NOTE]
>  Afin de pouvoir acheminer des messages, un groupe de ports d'envoi doit contenir au moins un port d'envoi.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-remove-a-send-port-from-a-send-port-group"></a>Pour supprimer un port d'envoi d’un groupe de ports d’envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dans laquelle supprimer un port d'envoi d'un groupe de ports d'envoi.  
  
3.  Cliquez sur **groupes de ports d’envoi**, cliquez sur le groupe de ports d’envoi, puis cliquez sur **propriétés**.  
  
4.  Sous **nom**, cliquez sur le port d’envoi à supprimer, puis cliquez sur **supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md)   
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)