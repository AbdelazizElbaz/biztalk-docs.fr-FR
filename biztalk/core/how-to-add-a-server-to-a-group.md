---
title: "Comment ajouter un serveur à un groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- adding, servers
- managing [groups], adding servers
- servers, groups
- managing [servers], adding to groups
ms.assetid: 6eca1eeb-1a56-4470-b3bc-c64865cf6270
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db5c7b760167f3e17d3ea82bf1023884b65e725
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-server-to-a-group"></a>Ajout d'un serveur à un groupe
La configuration de BizTalk Server permet d'ajouter un serveur à un groupe BizTalk. Cette opération permet d'étendre le déploiement de l'environnement BizTalk Server.  
  
 Un serveur peut uniquement être associé à un groupe BizTalk. Si un serveur appartient déjà à un autre groupe, vous devez le supprimer de son groupe actuel avant de l'ajouter à un nouveau groupe. Pour plus d’informations sur la suppression d’un serveur à partir d’un groupe BizTalk, consultez [comment supprimer un serveur d’un groupe](../core/how-to-remove-a-server-from-a-group.md).  
  
> [!NOTE]
>  Il n'y a pas d'interaction entre les groupes BizTalk associés à différents serveurs dans un environnement BizTalk Server, excepté dans le cadre d'échanges de message.  
  
> [!IMPORTANT]
>  Le composant d'exécution de BizTalk Server doit être installé sur l'ordinateur que vous voulez ajouter au groupe BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs de l'authentification unique et du groupe des administrateurs Windows.  
  
### <a name="to-add-a-server-to-a-biztalk-group"></a>Pour ajouter un serveur à un groupe BizTalk  
  
1.  Sur l’ordinateur que vous souhaitez ajouter à un groupe BizTalk Server pour, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.  
  
2.  Dans **Configuration de Microsoft BizTalk Server**, sélectionnez **configuration personnalisée**.  
  
3.  Dans **nom du serveur de base de données**, tapez le nom du serveur SQL pour le groupe BizTalk auquel associer le serveur.  
  
4.  Dans **informations d’identification du Service**, tapez le nom d’utilisateur et un mot de passe que les services utilisera, puis cliquez sur **configurer**.  
  
5.  Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **Enterprise SSO**.  
  
6.  Sur le **Enterprise Single Sign-On** , cliquez sur **joindre un système SSO existant**.  
  
     Assurez-vous que le nom du serveur et le nom de la base de données pointent vers le serveur de base de données de l'authentification unique principal du groupe BizTalk Server auquel associer le serveur.  
  
7.  Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **groupe**.  
  
8.  Sur le **groupe** , cliquez sur **joindre un groupe BizTalk existant**.  
  
     Assurez-vous que le nom du serveur et le nom de la base de données pointent vers les bases de données du groupe BizTalk Server auquel associer le serveur.  
  
9. Dans la barre de menus, cliquez sur **appliquer la Configuration** pour configurer Enterprise Single Sign-On et que le groupe sur cet ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md)   
 [Gestion des groupes](../core/managing-groups.md)   
 [Groupes BizTalk](../core/biztalk-groups.md)   
 [Comment déplacer un serveur à partir d’un groupe à un autre](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [Comment supprimer un serveur d’un groupe](../core/how-to-remove-a-server-from-a-group.md)   
 [Comment modifier les propriétés du groupe](../core/how-to-modify-group-properties.md)   
 [Gestion des serveurs](../core/managing-servers.md)