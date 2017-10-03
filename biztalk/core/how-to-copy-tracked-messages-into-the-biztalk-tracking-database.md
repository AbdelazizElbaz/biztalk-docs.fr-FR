---
title: "Comment copier des Messages suivis dans la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, copying between servers
- MessageBox database, Tracking database
- Tracking database, linking servers
- MessageBox database, copying messages
- linking, servers
- Tracking database, archiving
- archiving [Tracking database], linking servers
- Tracking database, MessageBox database
- Tracking database, copying messages
- archiving [Tracking database], MessageBox database
- MessageBox database, linking servers
- MessageBox database, archiving
ms.assetid: 369e972a-efbe-4ad5-a68f-aa3bbfb9ad54
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23aaa8e3bea3405d51a18da1778d420550ad4584
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-tracked-messages-into-the-biztalk-tracking-database"></a>Copie des messages suivis dans la base de données des suivis BizTalk
Les processus d'archivage et de purge pouvant utiliser ou modifier des bases de données présentes sur différents serveurs SQL Server, vous devez configurer des serveurs liés entre les instances de SQL Server concernées. Vous pouvez copier directement les messages suivis à partir du serveur MessageBox (BizTalkMsgBoxDb) vers votre base de données des suivis BizTalk (BizTalkDTADb) par l'intermédiaire d'un serveur lié. Vous devez configurer des serveurs liés entre :  
  
-   chacune de vos bases de données MessageBox BizTalk (BizTalkMsgBoxDb) et la base de données des suivis BizTalk (BizTalkDTADb) ;  
  
-   la base de données des suivis BizTalk (BizTalkDTADb) et le serveur de validation pour la validation de l'archivage.  
  
-   Les comptes de service de l'Agent SQL Server sur l'ordinateur qui héberge la base de données MessageBox BizTalk (BizTalkMsgBoxDb) doivent disposer des autorisations db_datareader et db_datawriter pour la base de données des suivis BizTalk (BizTalkDTADb) qui réside sur le serveur lié.  
  
> [!NOTE]
>  Dans SQL Server Agent, vérifiez que la tâche de copie est exécutée sans erreurs. En cas d'erreurs, le transfert des données dans la base de données des suivis risque d'échouer.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-copy-tracked-messages-into-the-biztalk-tracking-database-sql-server-2008"></a>Pour copier des messages suivis dans la base de données des suivis BizTalk (SQL Server 2008)  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL server approprié.  
  
3.  Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.  
  
4.  Dans le volet détails, cliquez sur **TrackedMessages_Copy_BizTalkMsgBoxDb**, puis cliquez sur **propriétés**.  
  
5.  Dans le **propriétés du travail - TrackedMessages_Copy_BizTalkMsgBoxDb** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.  
  
6.  Sous **liste des étapes du travail**, cliquez sur **purger**, puis cliquez sur **modifier**.  
  
7.  Dans le **commande** zone, modifiez le serveur de suivi et les paramètres de noms de base de données approprié, puis cliquez sur **OK**.  
  
8.  Sur le **propriétés du travail - TrackedMessages_Copy_BizTalkMsgBoxDb** boîte de dialogue **sélectionner une page**, cliquez sur **général**, sélectionnez le **activé** case à cocher, puis cliquez sur **OK**.  
  
     Les messages seront copiés de la base de données MessageBox  BizTalk  (BizTalkMsgBoxDb) vers la base de données des suivis BizTalk (BizTalkDTADb).  
  
> [!IMPORTANT]
>  Si vous ajoutez une nouvelle base de données MessageBox, vous devez effectuer à nouveau cette procédure pour cette dernière.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)