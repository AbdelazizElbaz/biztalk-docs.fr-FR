---
title: "Comment créer un serveur lié | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, linking for backups
- backing up, linking servers
ms.assetid: 7d4aba3d-77c0-4cdf-8547-71e821ce34a1
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ae08df9b522e1a772d7c8a9ad7d02c36dcb999
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-linked-server"></a>Comment créer un serveur lié
Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé dans une topologie distribuée, les bases de données appartenant à un groupe BizTalk existent sur plusieurs serveurs [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Vous devez configurer une connexion au serveur lié avec chaque serveur distant avant que vous ne puissiez sauvegarder l'intégralité de l'environnement BizTalk Server à partir du serveur de gestion BizTalk. Un serveur lié est une source de données OLE DB qui est utilisée dans les requêtes distribuées [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
 Dans le cadre du processus de sauvegarde et de restauration, le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée automatiquement des serveurs liés. Vous pouvez toutefois en créer manuellement à l'aide de cette procédure.  
  
 Serveurs liés peuvent également être créées à l’aide de la *sp_addlinkedserver* procédure stockée. Il existe des mesures de sécurité concernant cette opération. Lorsqu'un serveur lié est créé à l'aide de cette procédure, toutes les connexions locales sont mappées par défaut vers le nouveau serveur lié. Pour contrôler l’accès au serveur lié, le *sp_droplinkedsvrlogin* procédure doit être utilisée pour supprimer le mappage de connexion global suivi *sp_addlinkedsvrlogin* pour mapper les comptes de connexion de votre choix pour le nouveau serveur lié. Lorsque vous utilisez la procédure sp_addlinkedsvrlogin, il est recommandé de définir la @useself paramètre = TRUE. De cette manière, vous n'avez pas besoin d'incorporer un nom d'utilisateur et un mot de passe dans votre script SQL.  

> [!TIP]
> Ces étapes peuvent changer au fil du temps. Nous vous recommandons de faire référence à la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation à l’adresse [créer des serveurs liés](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine).
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] **sysadmin** rôle serveur fixe  
  
-   Créer une variable locale [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] connexion. Dans les étapes suivantes, ce compte est mappé à une connexion sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] souhaitée. 
  
## <a name="create-a-linked-server"></a>Créer un serveur lié
  
1.  Ouvrez **SQL Server Management Studio**, entrez le nom de votre revendeur local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], puis sélectionnez **Connect**.  
  
2.  Développez **objets serveur**, avec le bouton droit **des serveurs liés**, puis sélectionnez **nouveau serveur lié**.  

    Pour voir **objets serveur**, se connecter à un site local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Ensuite, **objets serveur** doit être affiché.
  
3.  Dans le **serveur lié** texte, entrez le nom complet du réseau le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] vous voulez lier à.  
  
    > [!NOTE]
    >  Cette procédure fait souvent référence au serveur auquel vous vous connectez avec le nom de serveur distant. Ce nom est uniquement employé pour des raisons de commodité, dans le but d'expliciter la relation existant entre le serveur lié (ou « distant ») et le serveur local.  
  
4.  Sous **type de serveur**, sélectionnez **SQL Server**.  
  
5.  Dans le volet gauche, sélectionnez **Sécurité**. 

    Dans cette étape, vous mappez le compte local créé pour la connexion au serveur distant. Vos options : 
    
    | | | 
    |---|---|
    | **Être effectuées à l’aide du contexte de sécurité de la connexion en cours** | Dans les environnements de domaine, les utilisateurs généralement se connecter avec leurs connexions de domaine. Cette option est préférable étant donné que le contexte de sécurité du compte de domaine connecté est mappé au compte local que vous avez créé.|
    | **Seront effectuées dans ce contexte de sécurité** | Lorsque les utilisateurs se connectent au serveur SQL local à l’aide d’une connexion SQL Server, cette option est préférable. Entrez ensuite la connexion et le mot de passe pour le compte sur le serveur lié. |


6. Sélectionnez **ajouter**et entrez les informations suivantes : 

    1. Sous **connexion locale**, sélectionnez le compte local que vous avez créé. 
    2. Vérifiez **Impersonate** si la connexion locale existe également sur le serveur distant. 
    3. Vous pouvez également, si la connexion locale est mappée à l’ordinateur distant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] connexion, entrez le **utilisateur distant** nom et **mot de passe distant** pour la connexion au serveur distant.  
  
    > [!NOTE]
    >  Pour utiliser l'emprunt d'identité, la configuration de votre serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et vos comptes d'ouverture de session doivent satisfaire aux exigences de délégation. Consultez [configuration des serveurs liés pour la délégation](https://msdn.microsoft.com/library/ms189580.aspx) pour plus d’informations.  

7. Dans le volet gauche, choisissez **Options de serveur**. Définir le **RPC** et **sortie RPC** paramètres **True**, puis sélectionnez **OK**. 
 
> [!TIP]
> Pour plus d’informations et les recommandations lors de la création de serveurs liés, à l’aide d’inclus de la `sp_addlinkedserver` stockées procedcure, consultez [créer des serveurs liés](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine).

  
## <a name="see-also"></a>Voir aussi  
 [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)