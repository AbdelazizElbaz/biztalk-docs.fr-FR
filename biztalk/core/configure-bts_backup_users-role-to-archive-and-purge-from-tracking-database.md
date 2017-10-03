---
title: "Comment configurer le rôle BTS_BACKUP_USERS pour l’archivage et la purge des données de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- purging, BTS_BACKUP_USERS role
- Tracking database, purging
- BTS_BACKUP_USERS role
- DTA Purge and Archive job
- archiving [Tracking database], BTS_BACKUP_USERS role
- archiving [Tracking database], DTA Purge and Archive job
- Tracking database, BTS_BACKUP_USERS role
- Tracking database, archiving
- purging, DTA Purge and Archive job
ms.assetid: c27aad2a-5788-4236-b5eb-ca730bf79851
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fb083f3755259ab2176541213d1637ce872c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a>Configuration du rôle BTS_BACKUP_USERS pour l'archivage et la purge des données de la base de données des suivis BizTalk
Le travail de purge et d'archivage de la base de données des suivis (BizTAlkDTADb) s'exécute normalement en utilisant les informations d'identification de l'utilisateur du compte de service SQL Server Agent connecté. Pour renforcer la sécurité, vous pouvez toutefois le configurer afin qu'il s'exécute en utilisant les informations d'identification d'un compte membre du rôle BTS_BACKUP_USERS. Cela permet d'exécuter les travaux SQL Server Agent sous des comptes disposant d'autorisations essentielles et évite de devoir octroyer des privilèges plus importants.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a>Pour configurer le rôle BTS_BACKUP_USERS pour l'archivage et la purge des données de la base de données des suivis BizTalk  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL Server approprié.  
  
3.  Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **BizTalkDTADb**, double-cliquez sur **sécurité**, double-cliquez sur **rôles**, et puis double-cliquez sur **des rôles de base de données**.  
  
4.  Dans le **détails de l’Explorateur d’objets** volet, double-cliquez sur **BTS_BACKUP_USERS**.  
  
5.  Dans le **propriétés du rôle de base de données – BTS_BACKUP_USERS** boîte de dialogue **membres de ce rôle**, cliquez sur **ajouter**.  
  
6.  Dans le **sélectionner un utilisateur de base de données ou rôle** boîte de dialogue, entrez un compte d’utilisateur avec les informations d’identification du Service SQL Server Agent, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)