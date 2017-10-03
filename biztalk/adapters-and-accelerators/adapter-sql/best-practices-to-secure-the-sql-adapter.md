---
title: "Meilleures pratiques pour sécuriser l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e32379d7-800a-49b7-a09a-6b3f04a6e5ef
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd3f60d95c7e642dc456b6e860b3cde32ab9f59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-to-secure-the-sql-adapter"></a>Meilleures pratiques pour sécuriser l’adaptateur SQL
Meilleures pratiques que vous devez suivre plus complètement protéger les données sensibles lorsque vous utilisez ou développerez des applications qui consomment le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].  
  
## <a name="security-best-practices-for-the-connection-between-the-sql-adapter-and-the-sql-server-database"></a>Meilleures pratiques de sécurité pour la connexion entre l’adaptateur SQL et la base de données SQL Server  
  
-   Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne fournit aucune prise en charge pour aider à sécuriser la communication entre elle et la base de données SQL Server. Vous devez fournir un mécanisme pour garantir un niveau adéquat de sécurité pour les données échangées entre l’adaptateur et la base de données SQL Server.  
  
-   Pour des raisons de sécurité, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’autorise pas vous permet de fournir des informations d’identification de mot de passe utilisateur pour la base de données SQL Server dans l’URI de connexion. Consultez le reste de cette rubrique pour d’autres méthodes permettent de fournir des informations d’identification pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] vous permet également d’utiliser l’authentification Windows lors de la connexion à SQL Server pour générer des métadonnées et effectuer des opérations, que ce soit via [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Avant d’utiliser l’authentification Windows, vous devez ajouter l’utilisateur Windows en tant qu’utilisateur dans SQL Server Management Studio. Pour plus d’informations, consultez [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
 Pour plus d’informations, consultez [sécurité entre le serveur SQL Server et de la carte](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md).
  
## <a name="security-best-practices-for-consuming-the-sql-adapter-with-biztalk-server"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur SQL avec BizTalk Server  
  
-   Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’autorise pas vous permet de fournir des informations d’identification de mot de passe utilisateur pour la base de données SQL Server dans l’URI de connexion.  
  
-   Lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], entrez les informations d’identification de mot de passe de nom utilisateur pour la base de données SQL Server à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur un port d’envoi, entrez les informations d’identification de mot de passe de nom utilisateur pour la base de données SQL Server à partir de la **informations d’identification** onglet du **Transport personnalisé WCF Propriétés** boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur un emplacement de réception, entrez les informations d’identification de mot de passe de nom utilisateur pour la base de données SQL Server à partir de la **autres** onglet du **Transport personnalisé WCF Propriétés** boîte de dialogue.  
  
-   Lors de l’utilisation [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des métadonnées, configuration de port d’envoi, ou la configuration de port de réception, vous pouvez également utiliser l’authentification Windows. Avant d’utiliser l’authentification Windows, vous devez ajouter l’utilisateur Windows en tant qu’utilisateur dans SQL Server Management Studio. Pour plus d’informations, consultez [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
 Pour plus d’informations, consultez [sécurité avec l’adaptateur SQL et BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).
  
## <a name="security-best-practices-for-consuming-the-sql-adapter-with-programming-solutions"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur SQL avec des Solutions de programmation  
  
-   Il est parfois nécessaire fournir des informations d’identification de mot de passe de l’utilisateur pour la base de données SQL Server dans l’URI ; de connexion Toutefois, si possible, vous devez éviter cette opération.  
  
-   Lorsque vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], entrez les informations d’identification de mot de passe de nom utilisateur pour la base de données SQL Server à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Dans la programmation de modèle de canal WCF, vous devez utiliser le **informations d’identification** propriété sur la fabrication de canal pour définir les informations d’identification de mot de passe nom utilisateur pour la base de données SQL Server.  
  
-   Dans la programmation de modèle de service WCF, vous devez utiliser le **ClientCredentials** propriété sur le client WCF pour définir les informations d’identification de mot de passe nom utilisateur pour la base de données SQL Server.  
  
-   Si une application qui consomme la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, assurez-vous que ces messages ont des mesures de sécurité suffisantes appliqués pour fournir les données adéquates protection de votre environnement.  
  
-   Lors de l’utilisation [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou de la connexion à SQL Server à partir d’une application .NET, vous pouvez également utiliser l’authentification Windows. Avant d’utiliser l’authentification Windows, vous devez ajouter l’utilisateur Windows en tant qu’utilisateur dans SQL Server Management Studio. Pour plus d’informations, consultez [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
 Pour plus d’informations, consultez [programmation sécurisée avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md). 
  
## <a name="security-best-practices-for-hosting-the-sql-adapter-in-iis"></a>Meilleures pratiques de sécurité pour l’hébergement de l’adaptateur SQL dans IIS  
 Qui héberge le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans Microsoft Internet Information Services (IIS) comme un site Web service expose les opérations exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] aux clients Web. Ces opérations peuvent impliquer l’échange de données sensibles sur Internet, donc vous devez prendre des mesures afin de garantir que ces données sont aussi sécurisées que possible.  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]fournit deux liaisons standard de transport HTTP : le **BasicHttpBinding** fournit élémentaire de transport HTTP avec aucun mécanisme de sécurité ; le **WSHttpBinding** prend en charge à la fois au niveau du transport et mécanismes de sécurité de niveau message.  
  
 Vous pouvez utiliser la **BasicHttpBinding** via une connexion HTTPS, ou utilisez le **WSHttpBinding** pour aider à protéger vos données. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] inclut le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] pour générer le service WCF pour des artefacts LOB. Cet Assistant prend uniquement en charge l’utilisation de **BasicHttpBinding**.  
  
 Vous pouvez également développer une liaison HTTP personnalisée pour tirer parti des mécanismes de sécurité supplémentaire qui fournit de votre environnement. Pour plus d’informations sur la sécurité des fonctionnalités offertes par [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx). 
  
 Lorsque vous hébergez le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en un service Web, les développeurs Web doivent prendre des mesures afin d’éviter les chaînes tapées par les utilisateurs de passer directement dans la base de données SQL Server. Par exemple, si un site Web permet à l’utilisateur permet d’entrer une valeur qui faire partie d’une clause WHERE dans une instruction SELECT, la chaîne d’entrée doit être analysée pour empêcher l’ajout d’autres commandes à l’instruction.  
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>Meilleures pratiques de sécurité pour le suivi de Diagnostic WCF et la journalisation des messages  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]prend en charge le suivi de diagnostic et de journalisation des messages. Vous configurez le suivi de diagnostic et de journalisation des messages des fichiers de configuration ou à l’aide de Windows Management Instrumentation (WMI). Selon les options de configuration que vous définissez, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] le suivi de diagnostic ou message de journalisation peut émettre des informations sensibles pour vous connecter de fichiers, où il pourrait potentiellement être exposée à d’observation par les utilisateurs non autorisés.  
  
 Suivez les recommandations fournies dans la documentation WCF pour atténuer les menaces de sécurité potentielles exposées par l’activation de ces fonctionnalités. Au minimum, vous devez observer les meilleures pratiques suivantes pour le suivi de diagnostic et de journalisation des messages :  
  
-   N’activez pas « commentaires » ou le suivi des « informations » dans un environnement de production. Cela peut entraîner une dégradation des performances. Toutefois, vous devez activer « avertissement » et le suivi de « erreur » dans un environnement de production. Si vous activez le traçage, vous devez prendre des mesures de sécurité appropriées pour protéger vos données. Consultez la documentation WCF pour plus d’informations.  
  
-   Assurez-vous que les fichiers de configuration et les fichiers journaux sont protégés par des listes de contrôle d’accès (ACL).  
  
 Les avertissements suivants s’appliquent spécifiquement aux messages échangés entre une application cliente et le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
-   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]le suivi de diagnostic peut enregistrer l’en-tête (mais pas le corps) des messages échangés avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. L’action du message se trouve dans l’en-tête du message, cela révèle des opérations appelé sur le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] par le client.  
  
-   Si [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] journalisation des messages est activée et `logMessagesAtServiceLevel` est `true`, l’en-tête de message (mais pas le corps du message) des messages échangés entre le client de l’adaptateur et le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sont enregistrés. L’action du message se trouve dans l’en-tête du message, cela révèle les opérations que le client est appelé sur le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Si `logEntireMessage` est également `true`, le corps du message doivent être enregistré. Cela peut révéler des informations sensibles de la base de données.  
  
 Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez le traçage de diagnostic, consultez [problèmes de sécurité et des conseils utiles pour le traçage](https://msdn.microsoft.com/library/ms733053.aspx). Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez la journalisation des messages, consultez [problèmes de sécurité pour la journalisation des messages](https://msdn.microsoft.com/library/ms730318.aspx).
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications SQL](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)