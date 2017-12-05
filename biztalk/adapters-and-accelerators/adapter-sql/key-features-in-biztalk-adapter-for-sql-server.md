---
title: "Principales fonctionnalités de l’adaptateur BizTalk pour SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6beab8d-c2c4-4add-860c-054b9aed8d70
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af3177e3004c81d368eab8738a201e90c95d1b69
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="key-features-in-biztalk-adapter-for-sql-server"></a>Principales fonctionnalités de l’adaptateur BizTalk pour SQL Server
Cette section répertorie les fonctionnalités de [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].  
  
> [!NOTE]
>  Cette rubrique a été utilisée à partir de la version précédente de [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] aide.  
  
## <a name="features-in-the-sql-adapter"></a>Fonctionnalités de l’adaptateur SQL  
 Voici les fonctionnalités introduites dans les versions précédentes de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
### <a name="technology-related-features"></a>Fonctionnalités liées à la technologie  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Utilisation de Windows Communication Foundation (WCF)|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] repose sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ([!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]). À son tour, le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est basé sur WCF. L’adaptateur est exposé comme un canal WCF aux clients de la carte. Cela permet la connectivité, échange de métadonnées et échange des données avec des systèmes externes.|  
|Prise en charge pour le modèle de canal WCF et le modèle de service WCF|Dans le modèle de canal WCF, les clients de carte peuvent consommer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] par directement envoyer et recevoir des messages XML. Dans le modèle de service WCF, les clients de l’adaptateur peuvent générer une classe de proxy .NET à partir de la Description langage WSDL (Web Services) obtenu à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].|  
|Prise en charge des plateformes 64 bits|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est désormais disponible pour les plateformes 64 bits.|  
  
### <a name="metadata-related-features"></a>Fonctionnalités de métadonnées  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Parcourir, rechercher et récupérer des métadonnées|Les clients de l’adaptateur peuvent parcourir et rechercher des métadonnées dans des lots en spécifiant une taille de lot. Cette fonctionnalité est disponible uniquement lors de la programmation à l’adaptateur et non via le complément à consommer de projet d’adaptateur Service BizTalk. La recherche de métadonnées est prise en charge aux niveaux de Tables, vues, procédures, fonctions scalaires et fonctions table. La chaîne de recherche est utilisée directement dans une instruction SQL.|  
|Prise en charge pour l’appel d’artefacts avec le même nom dans différentes bases de données|Dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], les espaces de noms dans le fichier de définition de schéma XML (XSD) contenu uniquement le schéma, le nom et dans certains cas, le nom d’objet. Toutefois, si une application souhaite exécuter des opérations sur les objets portant le même nommés avec des métadonnées différentes à différentes bases de données, les métadonnées générées en conflit. Pour distinguer les métadonnées, la seule consiste à utiliser le nom de la base de données dans les espaces de noms XSD.<br /><br /> La version actuelle de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] vous permet de spécifier le nom de la base de données dans les espaces de noms XSD en définissant la valeur de la **UseDatabaseNameInXsdNamespace** liaison de propriété à TRUE. La valeur par défaut de la propriété de liaison a la valeur false, ce qui implique que les espaces de noms XSD ne contient pas le nom de la base de données. Pour plus d’informations sur la **UseDatabaseNameInXsdNamespace** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).|  
  
### <a name="performance-related-features"></a>Fonctionnalités de performances  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Prise en charge pour les compteurs de performances|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge les compteurs de performances basée sur WCF pour une utilisation par les clients de la carte. Pour plus d’informations sur les compteurs de performance, consultez [utiliser des compteurs de performances avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md).|  
  
### <a name="operations-related-features"></a>Liées aux opérations de fonctionnalités  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Prise en charge pour les types de données SQL Server 2005 et SQL Server 2008|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge les types de données suivantes introduites dans :<br /><br /> -   **SQL Server 2005**: XML, varchar (max) et varbinary (max).<br />-   **SQL Server 2008**: Date, Time, Datetimeoffset, Datetime2, Hierarchyid, Geography, Geometry et FILESTREAM.|  
|Prise en charge des Types définis par l’utilisateur (UDT)|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge l’exécution d’opérations sur les tables et vues qui contiennent des types UDT. Pour plus d’informations sur la prise en charge pour les UDT, consultez [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).|  
|Fonctions et procédures stockées de prise en charge pour l’exécution de Transact-SQL et CLR|Les clients de carte peuvent exécuter Transact-SQL et CLR :<br /><br /> -Les procédures stockées dans une base de données SQL Server.<br />-Scalaires et fonctions table dans une base de données SQL Server.<br /><br /> Pour plus d’informations, consultez [ce que les opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx).|  
|Prise en charge pour l’exécution de procédures stockées avec ou sans la clause FOR XML|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] vous permet d’exécuter des procédures stockées qui ont une instruction SELECT avec ou sans une clause FOR XML. La version précédente de l’adaptateur pris en charge uniquement les procédures stockées qui avait une clause FOR XML dans l’instruction SELECT. Pour plus d’informations sur l’exécution des procédures stockées, consultez [exécuter les procédures stockées de SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-the-sql-adapter.md).|  
|Prise en charge pour la diffusion en continu d’objets volumineux|Les clients de l’adaptateur peuvent diffuser caractères volumineux et champs binaires dans la base de données SQL Server à l’aide de l’ensemble de\<nom de la colonne\> opération, où < nom_colonne > est le nom de la colonne de type varchar (max), nvarchar (max) ou varbinary (max) . Le jeu de\<nom de la colonne\> opération vous permet également d’insérer ou de mettre à jour les données FILESTREAM dans une base de données SQL Server 2008. Pour plus d’informations, consultez [opérations sur les Tables et vues que contiennent des grands Types de données à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md). **Remarque :** pour lire des caractères et champs binaires dans les tables SQL Server et les vues, les clients de carte utilisent l’opération Select.|  
|Prise en charge des notifications de requête|Les clients de l’adaptateur peuvent recevoir des notifications de requête de SQL Server basée sur une instruction SELECT déclenchement ou une procédure stockée. La notification est envoyée par le serveur SQL Server pour les clients de la carte en tant qu’et lorsque le jeu de résultats pour l’instruction SELECT ou la procédure stockée est modifiée. Pour plus d’informations sur les notifications de requête, consultez [recevoir les Notifications de requête à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md).|  
|Prise en charge pour l’exécution des instructions SQL arbitraires|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients d’adaptateur exécuter des instructions SQL arbitraires à l’aide d’opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar. Pour plus d’informations sur ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).|  
|Prise en charge des opérations composites|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients d’adaptateur effectuer des opérations composites sur la base de données SQL Server. Une opération composite peut inclure plusieurs des opérations suivantes et dans n’importe quel ordre :<br /><br /> -Les opérations Insert, Update et Delete sur les tables et les vues.<br />-Les procédures stockées qui sont signalées en tant qu’opérations dans l’adaptateur.<br /><br /> Pour plus d’informations sur des opérations composites, consultez [des schémas de Message pour des opérations composites](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).|  
|Interrogation améliorée|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend désormais en charge deux types supplémentaires d’interrogation : **TypedPolling** et **XmlPolling**. Pour plus d’informations sur ces types d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).|  
|Prise en charge des opérations sur les artefacts dans plusieurs schémas|Outre le schéma par défaut (dbo), les clients de carte peuvent également effectuer des opérations sur artefacts dans d’autres schémas dans la base de données SQL Server autant que les informations d’identification d’utilisateur utilisé pour se connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] a accès à ces schémas dans SQL Server base de données. Pour plus d’informations sur un schéma de base de données SQL Server, consultez [http://go.microsoft.com/fwlink/?LinkId=130148](http://go.microsoft.com/fwlink/?LinkId=130148).|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)