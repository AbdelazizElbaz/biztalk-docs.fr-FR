---
title: "Parcourir, rechercher et obtenir les métadonnées de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 368dd5ca-456c-4cae-9e85-bcf504c4e7ed
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba7a1b7644cc3a2e3e00b7a931250932359ab7b7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="browse-search-and-get-sql-server-metadata"></a>Parcourir, rechercher et obtenir les métadonnées de SQL Server
Les métadonnées qui [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces à partir de la base de données SQL Server décrit la structure du message pour la communication avec la base de données SQL Server à l’aide de l’adaptateur. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge deux interfaces de récupération des métadonnées.  
  
-   MetadataExchange fournie par [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF fournit un point de terminaison d’échange de métadonnées pour toutes les liaisons WCF, ce qui permet aux clients d’obtenir des métadonnées à partir de la base de données SQL Server.  
  
-   IMetadataRetrievalContract fournie par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], qui prend en charge les métadonnées de parcourir et rechercher des fonctions de l’adaptateur.  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces le serveur SQL Server de la base de données des artefacts et des opérations respectives que les clients de l’adaptateur peuvent appeler. L’adaptateur met également en évidence les opérations (telles que la méthode ExecuteNonQuery, ExecuteReader et ExecuteScalar) qui peuvent être utilisées pour effectuer des opérations spécifiques sur la base de données SQL Server. Ces opérations sont décrites plus loin dans cette rubrique.  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] met en évidence des artefacts dans la base de données SQL Server que l’utilisateur actuellement connecté a accès à tous les schémas. Cela implique que, mis à part le schéma par défaut (dbo), les clients de l’adaptateur peuvent également effectuer des opérations sur les artefacts dans d’autres schémas dans la base de données SQL Server autant que les informations d’identification d’utilisateur utilisé pour se connecter à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] a accès à ces schémas dans la base de données SQL Server. Pour plus d’informations sur un schéma de base de données SQL Server, consultez [http://go.microsoft.com/fwlink/?LinkId=130148](http://go.microsoft.com/fwlink/?LinkId=130148).  
  
 Vous pouvez utiliser les clients de la carte pour parcourir, rechercher et récupérer des métadonnées par :  
  
-   Création d’un projet BizTalk dans Visual Studio  
  
-   À l’aide du modèle de service WCF  
  
-   À l’aide du modèle de canal WCF  
  
 Lorsque vous utilisez un projet BizTalk, vous devez utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des métadonnées pour les opérations que vous souhaitez effectuer sur la base de données SQL Server. Lorsque vous utilisez le modèle de service WCF, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer les classes proxy pour effectuer des opérations sur la base de données SQL Server. Pour plus d’informations sur la navigation, la recherche et la récupération de métadonnées à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## <a name="browsing-metadata"></a>Exploration des métadonnées  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients d’adaptateur parcourir les tables de base de données, vues, procédures stockées et fonctions qui sont disponibles dans la base de données SQL Server. Dans le cadre de l’opération de parcourir des métadonnées, l’adaptateur met également en évidence les opérations qui peuvent être effectuées sur la base de données SQL Server, y compris certaines opérations personnalisées prises en charge par les adaptateurs. Ces opérations sont disponibles à partir de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] met en évidence les opérations suivantes :  
  
-   Les opérations sur les tables, vues, procédures, fonctions scalaires et fonctions table. Par exemple, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut surface Insert, Update, Select et les opérations de suppression de la table EMPLOYEE.  
  
-   Le jeu de\<nom de la colonne\> opération pour les tables et vues qui permet aux clients de carte à écrire des valeurs de données de grande taille en flux continu. L’opération Set est renvoyée uniquement pour les tables et les vues qui contiennent des colonnes avec les types de données suivants : varchar (max), nvarchar (max) ou varbinary (max). Pour plus d’informations, consultez [opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).  
  
-   Les opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar qui permettent aux clients d’adaptateur exécuter des instructions SQL arbitraires dans SQL Server. Pour plus d’informations sur ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
-   Les opérations d’interrogation et de Notification pour recevoir des messages entrants à partir de SQL Server. Pour plus d’informations sur l’opération d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md); pour plus d’informations sur l’opération de Notification, consultez [considérations relatives à la réception de Notifications de requête à l’aide de l’instruction SQL adaptateur](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md).  
  
 Pour plus d’informations sur la façon dont les métadonnées sont catégorisée, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md).  
  
## <a name="searching-metadata"></a>Recherche de métadonnées  
 Avec la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], il est possible d’effectuer une requête de recherche sur la base de données SQL Server en utilisant les expressions de recherche de SQL Server qui sont compatibles avec l’opérateur LIKE. Par exemple, les clients de l’adaptateur peuvent utiliser une expression de recherche telles que « EMP % » pour obtenir des tables commençant par EMP. L’adaptateur convertit en la requête SQL suivante :  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%'  
```  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|_ (souligné)|Correspond à exactement un caractère.<br /><br /> Par exemple, « A_ » correspond à « AB », « CA », « AD ».|  
|% (pourcentage)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, « Un % » correspond à « A », « AB », « ABC ».|  
|[ ]|-Remplace une signification spéciale _ et %.<br />-Spécifie une plage ou un jeu de caractères à être présents.<br /><br /> Exemple :<br /><br /> -% [%] correspond à tous les noms qui incluent un symbole %.<br />-[a-f] correspond à tous les noms qui ont des caractères entre et en incluant « a » et « f ».<br />-[abc] correspond à tous les noms contenant des caractères « a », « b » et « c ».|  
|[^]|Spécifie une plage ou un jeu de caractères ne devant ne pas être présents.<br /><br /> Exemple :<br /><br /> -[^ a-f] correspond à tous les noms qui n’ont pas de caractères entre et en incluant « a » et « f ».<br />-[^ abc] correspond à tous les noms qui n’ont pas de caractères « a », « b » et « c ».|  
  
> [!IMPORTANT]
>  L’étendue de recherche de métadonnées est limitée au niveau immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée. Par exemple, pour rechercher une fonction scalaire, vous devez être fonction recherche sous/scalaire / [Schema]. Recherche de plusieurs niveaux n’est pas pris en charge.  
  
## <a name="retrieving-metadata"></a>Récupération de métadonnées  
 Lors de la récupération des métadonnées, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut extraire des métadonnées dans un schéma, y compris l’ensemble ou un sous-ensemble de la base de données des objets avec les paramètres respectifs de l’objet et l’opération. L’adaptateur présente les entités à partir de la base de données SQL Server en tant que noms d’éléments XML. Étant donné que des traits de soulignement sont les seuls caractères spéciaux qui peuvent être inclus, tous les autres caractères spéciaux dans les noms d’élément sont encodés à l’aide des traits de soulignement. Par exemple, `emp$name` est encodé comme `emp_x0024_name`.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)   
 [Comprendre l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)   
 [Obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)