---
title: "Comment gérer le groupe d’administrateurs BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Administrators group, user accounts
- BizTalk Administrators group
- user accounts, BizTalk Administrators group
- Windows Management Instrumentation (WMI), administering
- BizTalk Administrators group, privileges
- security, BizTalk Administrators group
- Administration Console [BizTalk Server], security
- Administration Console [BizTalk Server], administering
- BizTalk Administrators group, about BizTalk Administrators group
ms.assetid: 60ea689b-0b93-4fcc-b49c-6436e7be473f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fe92c9c43ccef242d8c14b5f1aa48e0b1a8d852
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-the-biztalk-server-administrators-group"></a>Gestion des groupes Administrateurs BizTalk Server
Le groupe Administrateurs BizTalk Server dispose des privilèges minimaux requis pour exécuter les tâches d'administration. Vous pouvez ajouter des utilisateurs au groupe Administrateurs BizTalk Server pour leur permettre d'effectuer des tâches d'administration à l'aide de la console Administration de BizTalk Server ou du fournisseur WMI. Vous pouvez également supprimer des utilisateurs du groupe Administrateurs BizTalk Server lorsque ceux-ci n'ont plus besoin d'effectuer des tâches d'administration à l'aide de la console Administration de BizTalk Server ou du fournisseur WMI.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être membre du groupe Administrateurs ou Administrateurs de domaine pour effectuer cette procédure.  
  
### <a name="to-add-users-to-the-local-biztalk-server-administrators-group"></a>Pour ajouter des utilisateurs au groupe Administrateurs BizTalk Server local  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.  
  
2.  Développez **Outils système**, développez **utilisateurs et groupes locaux**, puis cliquez sur le **groupes** dossier. Le contenu du dossier apparaît dans le volet Détails.  
  
3.  Dans le volet détails, cliquez sur **administrateurs de BizTalk Server**.  
  
4.  Sur le **Action** menu, pointez sur **toutes les tâches**, puis cliquez sur **ajouter au groupe**.  
  
5.  Dans le **propriétés du groupe Administrateurs BizTalk Server** boîte de dialogue, cliquez sur **ajouter**.  
  
6.  Dans le **Regarder dans** , sélectionnez le nom de votre ordinateur ou de domaine.  
  
7.  Dans la liste qui contient les utilisateurs et les ordinateurs associés au domaine ou l’ordinateur que vous avez sélectionné à l’étape 6, sélectionnez le compte d’utilisateur à ajouter, cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
8.  Cliquez sur **OK** pour fermer la **propriétés du groupe Administrateurs BizTalk Server** boîte de dialogue.  
  
### <a name="to-remove-users-from-local-the-biztalk-server-administrators-group"></a>Pour supprimer des utilisateurs du groupe Administrateurs BizTalk Server local  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.  
  
2.  Développez **Outils système**, développez **utilisateurs et groupes locaux**, puis cliquez sur le **groupes** dossier. Le contenu du dossier apparaît dans le volet Détails.  
  
3.  Dans le volet détails, cliquez sur **administrateurs de BizTalk Server**.  
  
4.  Sur le **Action** menu, cliquez sur **propriétés**.  
  
5.  Dans le **propriétés du groupe Administrateurs BizTalk Server** boîte de dialogue, sélectionnez le compte d’utilisateur à supprimer, puis cliquez sur **supprimer**.  
  
6.  Cliquez sur **OK**.  
  
### <a name="to-add-users-to-the-domain-biztalk-server-administrators-group"></a>Pour ajouter des utilisateurs au groupe Administrateurs BizTalk Server du domaine  
  
1.  Ouvrez une session sur le contrôleur de domaine dans lequel les bases de données SQL Server sont regroupées à l'aide du compte Administrateurs de domaine.  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Active Directory Users and Computers** à Démarrer le **Active Directory Users and Computers** console.  
  
    1.  Dans l'arborescence de la console, cliquez sur le dossier contenant le groupe Administrateurs BizTalk Server auquel ajouter un membre.  
  
    2.  Dans le volet de détails, cliquez sur le groupe d’administrateurs BizTalk Server, puis cliquez sur **propriétés**.  
  
    3.  Sur le **membres** , cliquez sur **ajouter**.  
  
    4.  Dans **Entrez les noms des objets à sélectionner**, tapez le nom de l’utilisateur, puis cliquez sur **OK**.  
  
### <a name="to-remove-users-from-the-domain-biztalk-server-administrators-group"></a>Pour supprimer des utilisateurs du groupe Administrateurs BizTalk Server du domaine  
  
1.  Ouvrez une session sur le contrôleur de domaine dans lequel les bases de données SQL sont regroupées à l'aide du compte Administrateurs de domaine.  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Active Directory Users and Computers** à Démarrer le **Active Directory Users and Computers** console.  
  
    1.  Dans l'arborescence de la console, cliquez sur le dossier contenant le groupe Administrateurs BizTalk Server auquel ajouter un membre.  
  
    2.  Dans le volet de détails, cliquez sur le groupe d’administrateurs BizTalk Server, puis cliquez sur **propriétés**.  
  
    3.  Sur le **membres** , cliquez sur le membre que vous souhaitez supprimer, puis cliquez sur **supprimer**.  
  
    4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md)   
 [Gestion des hôtes et des comptes de Service](../core/managing-hosts-and-service-accounts.md)   
 [Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)   
 [Groupes Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [La gestion des comptes d’utilisateurs et groupes Windows](../core/managing-windows-groups-and-user-accounts.md)