---
title: "Se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45c54b2a-e056-496f-9f10-f19b6a3ca1a6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db7d0cbe07155d09085091d995b524b3058c0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-using-windows-authentication-with-the-sql-adapter"></a>Se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL
Le [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] permet aux clients de carte à utiliser l’authentification Windows pour établir une connexion avec SQL Server. Pour utiliser l’authentification Windows, les clients de l’adaptateur doivent entrer un nom d’utilisateur vide et un mot de passe. 

Pour vous connecter à SQL Server à l’aide de l’authentification Windows dans Visual Studio, consultez [se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).  
  
 Pour activer la carte aux clients d’utiliser l’authentification Windows pour se connecter à SQL Server, activez l’authentification Windows pour l’utilisateur sur l’ordinateur exécutant SQL Server.  

> [!TIP]
> Si SQL Server Management Studio n’est pas installé sur votre serveur SQL Server, vous pouvez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)et l’installer. 
 
## <a name="add-the-user-in-sql-server"></a>Ajoutez l’utilisateur dans SQL Server  
  
1.  Ouvrez SQL Server Management Studio. Dans **se connecter au serveur**, sélectionnez **moteur de base de données**, entrez votre SQL **nom du serveur**, puis entrez les informations d’identification d’administrateur pour se connecter au serveur.  

    Sélectionnez **Se connecter**.
  
2.  Dans **l’Explorateur d’objets**, développez le serveur SQL Server, **sécurité**, avec le bouton droit **connexions**, puis sélectionnez **nouvelle connexion**.  
  
3.  Pour le **nom de connexion**, entrez le nom d’utilisateur Windows dans le `domain\username` format.  

    > [!NOTE]
    >* Lorsque vous utilisez cet adaptateur avec BizTalk, le nom de connexion que vous entrez, est l’identité du compte de l’instance d’hôte.  
    >
    >* Lorsque vous utilisez cet adaptateur dans le code .NET, le nom de connexion que vous entrez, est l’identité de ce processus.
  
4.  Sélectionnez **mappage de l’utilisateur** (volet gauche). Sélectionnez une base de données à associer à l’utilisateur. Un utilisateur BizTalk doit être associé à des bases de données suivantes : 

* BizTalkDTADb
* BizTalkMgmtDb
* BizTalkMsgBoxDb
* BTAHL7
* SSODB

5. Dans le **appartenance au rôle de la base de données** boîte, sélectionnez **db_owner** pour toutes les bases de données BizTalk.  

    > [!NOTE]
    > [Rôles de serveur et base de données dans SQL Server](https://msdn.microsoft.com/library/bb669065.aspx) fournit de bonnes informations sur les rôles. 
  
6.  Sélectionnez **OK** pour enregistrer vos modifications.
  
 Une fois que vous avez ajouté l’utilisateur, l’utilisateur peut se connecter et s’authentifier auprès de SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], l’enregistrement avec un nom d’utilisateur et un mot de passe.  



## <a name="see-also"></a>Voir aussi  
 [Créer une connexion à SQL Server](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)