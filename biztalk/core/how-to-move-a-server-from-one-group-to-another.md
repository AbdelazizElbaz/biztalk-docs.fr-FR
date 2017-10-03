---
title: "Comment déplacer un serveur à partir d’un groupe vers un autre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, servers
- groups, moving
- managing [groups], moving servers
- servers, moving
- managing [servers], moving
- servers, groups
ms.assetid: 3f789a62-f597-426b-9cea-74c1fe22b694
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c9e5dfdf266d2205283afa7cd9804c31fc93ff3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-a-server-from-one-group-to-another"></a>Transfert d'un serveur d'un groupe à un autre
Un serveur ne peut être associé qu'à un seul groupe BizTalk Server. Pour déplacer un serveur d'un groupe à un autre, vous devez d'abord supprimer le serveur du groupe d'origine en annulant sa configuration, puis l'ajouter au nouveau groupe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs de l'authentification unique et du groupe des administrateurs Windows.  
  
### <a name="to-move-a-server-from-one-biztalk-group-to-another"></a>Pour déplacer un serveur d'un groupe BizTalk à un autre  
  
1.  Sur l’ordinateur que vous souhaitez déplacer le groupe BizTalk vers un autre, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **deConfigurationdeBizTalkServer**.  
  
2.  Dans la barre de menus, cliquez sur **annuler la configuration des fonctionnalités**.  
  
3.  Dans le **annuler la configuration des fonctionnalités** boîte de dialogue, sélectionnez **Enterprise SSO**, sélectionnez **groupe**, puis cliquez sur **OK**.  
  
    > [!CAUTION]
    >  L'annulation de la configuration d'un groupe annule également la configuration de tous les composants dépendants déjà configurés sur l'ordinateur.  
  
4.  Cliquez sur **Oui**.  
  
5.  Dans le **Configuration de Microsoft BizTalk Server** fenêtre, cliquez sur **suivant**.  
  
     La configuration de l'authentification unique de l'entreprise, du groupe et de leurs composants dépendants est annulée.  
  
6.  Cliquez sur **Terminer**.  
  
7.  Dans le **Configuration de Microsoft BizTalk Server** fenêtre, sélectionnez **configuration personnalisée**.  
  
8.  Dans **nom du serveur de base de données**, tapez le nom du serveur SQL pour le groupe BizTalk sur lequel vous déplacez le serveur.  
  
9. Dans **informations d’identification du Service**, tapez le nom d’utilisateur et un mot de passe que les services utilisera, puis cliquez sur **configurer**.  
  
10. Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **Enterprise SSO**.  
  
11. Sur le **Enterprise Single Sign-On** , cliquez sur **joindre un système SSO existant**.  
  
     Assurez-vous que le nom du serveur et le nom de la base de données pointent vers le serveur de base de données de l'authentification unique principal du groupe BizTalk Server sur lequel vous déplacez le serveur.  
  
12. Dans l’arborescence de navigation sur le côté gauche de l’écran, cliquez sur **groupe**.  
  
13. Sur le **groupe** , cliquez sur **joindre un groupe BizTalk existant**.  
  
     Assurez-vous que le nom du serveur et le nom de la base de données pointent vers les bases de données du groupe BizTalk Server sur lequel vous déplacez le serveur.  
  
14. Dans la barre de menus, cliquez sur **appliquer la Configuration** pour configurer Enterprise Single Sign-On et que le groupe sur cet ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des groupes](../core/managing-groups.md)   
 [Groupes BizTalk](../core/biztalk-groups.md)   
 [Comment ajouter un serveur à un groupe](../core/how-to-add-a-server-to-a-group.md)   
 [Comment supprimer un serveur d’un groupe](../core/how-to-remove-a-server-from-a-group.md)   
 [Comment modifier les propriétés du groupe](../core/how-to-modify-group-properties.md)   
 [Utilisation de Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md)   
 [L’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md)   
 [Gestion des serveurs](../core/managing-servers.md)