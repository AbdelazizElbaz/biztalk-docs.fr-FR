---
title: "Comment supprimer un serveur d’un groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- managing [groups], deleting servers
- servers, deleting
- deleting, groups
- servers
- managing [servers], deleting from groups
- groups, deleting
- servers, groups
- deleting, servers
ms.assetid: 85596e18-fa17-4f44-bc20-2e4cb578e109
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b69eb694da320e598c7d0cfe5a03d58e0a723a8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-server-from-a-group"></a>Suppression d'un serveur d'un groupe
Un serveur peut uniquement être associé à un groupe BizTalk. Si un serveur appartient déjà à un autre groupe, vous devez le supprimer de son groupe actuel avant de l'ajouter à un nouveau groupe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs Windows.  
  
### <a name="to-remove-a-server-from-a-group"></a>Pour supprimer un serveur d'un groupe  
  
1.  Sur l’ordinateur que vous souhaitez supprimer d’un groupe BizTalk Server, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **deConfigurationdeBizTalkServer**.  
  
2.  Dans la barre de menus, cliquez sur **annuler la configuration des fonctionnalités**.  
  
3.  Dans le **annuler la configuration des fonctionnalités** boîte de dialogue, sélectionnez **groupe**, puis cliquez sur **OK**.  
  
    > [!CAUTION]
    >  L'annulation de la configuration d'un groupe annule également la configuration de tous les composants dépendants déjà configurés sur l'ordinateur.  
  
4.  Cliquez sur **Oui**.  
  
5.  Dans l’Assistant Configuration de Microsoft BizTalk Server, cliquez sur **suivant**.  
  
     La configuration du groupe et de ses composants dépendants est annulée.  
  
6.  Cliquez sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des groupes](../core/managing-groups.md)   
 [Groupes BizTalk](../core/biztalk-groups.md)   
 [Comment ajouter un serveur à un groupe](../core/how-to-add-a-server-to-a-group.md)   
 [Comment déplacer un serveur à partir d’un groupe à un autre](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [Comment modifier les propriétés du groupe](../core/how-to-modify-group-properties.md)   
 [Gestion des serveurs](../core/managing-servers.md)