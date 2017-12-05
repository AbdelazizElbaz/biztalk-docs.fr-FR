---
title: "ID de nœud de métadonnées de l’adaptateur SQL dans le Pack d’adaptateurs BizTalk | Documents Microsoft"
description: "Métadonnées, search, les types de nœuds de récupération et les identificateurs utilisés dans les composants SQL qui sont exposés dans l’adaptateur SQL Server - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8601a328-5380-4577-a121-c926e0fd3140
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6e603643ba1d969534e9954733572dc92acd04a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="node-types-and-ids-for-the-sql-server-adapter"></a>Types de nœuds et ID de l’adaptateur SQL Server

## <a name="metadata-node-ids"></a>ID de nœud de métadonnées
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces SQL Server de base de données artefacts de façon hiérarchique. Le tableau suivant répertorie les types de nœuds et l’ID de nœud pour les artefacts de base de données SQL Server qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces. L’ID de nœud est le chemin d’accès absolu du nœud qui est utilisé dans le **IMetadataRetrievalContractBrowse**, **recherche**, et **GetMetadata** méthodes.  
  
|Nom complet de l’objet|Type de nœud|ID de nœud|Exemple| Description|  
|---------------------------|---------------|-------------|-------------|-----------------|  
|--|CATÉGORIE|/|/|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]nœud racine. Retourne tous les nœuds de premier niveau ; Cela inclut les nœuds d’opération ExecuteNonQuery, ExecuteReader et ExecuteScalar et tous les nœuds de schéma pour les opérations sortantes et le nœud d’opération d’interrogation pour l’opération entrante.|  
|ExecuteNonQuery|OPÉRATION SORTANTE|GenericOp/ExecuteNonQuery|GenericOp/ExecuteNonQuery|Nœud d’opération ExecuteNonQuery. Retourne le WSDL pour l’opération ExecuteNonQuery.|  
|ExecuteReader|OPÉRATION SORTANTE|GenericOp/ExecuteReader|GenericOp/ExecuteReader|Nœud d’opération ExecuteReader. Retourne le WSDL pour l’opération ExecuteReader.|  
|ExecuteScalar|OPÉRATION SORTANTE|GenericOp/ExecuteScalar|GenericOp/ExecuteScalar|Nœud d’opération ExecuteScalar. Retourne le WSDL pour l’opération ExecuteScalar.|  
|Interrogation|OPÉRATION ENTRANTE|Interrogation|Interrogation|Nœud d’opération d’interrogation. Retourne le WSDL pour l’opération d’interrogation.|  
|Notification|OPÉRATION ENTRANTE|Notification|Notification|Nœud d’opération de notification. Retourne le WSDL pour l’opération de Notification.|  
|Procédures|CATÉGORIE|Procédures /|Procédures /|Nœud de schéma des procédures. Retourne toutes les procédures pour le schéma spécifié.|  
|[DB_PROCEDURE]|OPÉRATION SORTANTE|Procédure / [DB_SCHEMA] / [nom_procédure]|Procédure/dbo/ADD_EMP_DETAILS|Nœud de la procédure. Retourne le langage WSDL pour la procédure spécifiée.|  
|Tables|CATÉGORIE|Tables /|Tables /|Nœud de schéma tables. Retourne tous les nœuds de table pour le schéma spécifié.|  
|[DB_TABLE]|CATÉGORIE|-|-|Nœud de la table. Retourne tous les nœuds d’opération (Insert, Select, Update, Delete et ensemble) pour la table spécifiée.<br /><br /> L’opération Set est renvoyée uniquement pour les tables qui contiennent des colonnes avec un type de données suivant : varchar (max), nvarchar (max) ou varbinary (max).|  
|Insert|OPÉRATION SORTANTE|TableOp/Insert / [DB_SCHEMA] / [DB_TABLE]|TableOp/Insert/dbo/employé|Insérer un nœud de fonctionnement de la table. Retourne le WSDL pour l’opération d’insertion pour la table spécifiée.|  
|Select|OPÉRATION SORTANTE|TableOp/sélectionner / [DB_SCHEMA] / [DB_TABLE]|TableOp/sélectionner/dbo/employé|Nœud d’opération de sélection de table. Retourne le WSDL pour l’opération de sélection pour la table spécifiée.|  
|Update|OPÉRATION SORTANTE|TableOp/mettre à jour / [DB_SCHEMA] / [DB_TABLE]|TableOp/mise à jour/dbo/employé|Nœud d’opération de mise à jour de la table. Retourne le WSDL pour l’opération de mise à jour pour la table spécifiée.|  
|DELETE|OPÉRATION SORTANTE|TableOp/Delete / [DB_SCHEMA] / [DB_TABLE]|TableOp/Delete/dbo/employé|Nœud d’opération de suppression de la table. Retourne le WSDL pour l’opération de suppression pour la table spécifiée.|  
|Ensemble [nom_colonne]|OPÉRATION SORTANTE|TableOp/WriteText / [DB_SCHEMA] / [DB_TABLE] / [nom_colonne]|TableOp/WriteText/dbo/employé/Job_Description|Nœud de l’opération table ensemble. Retourne le WSDL pour l’opération de définition de la colonne spécifiée dans la table. (Uniquement visible si la table contient des colonnes avec un type de données suivant : (Max), nvarchar (max) ou varbinary.|  
|Vues|CATÉGORIE|Vues /|Vues /|Nœud de vues de schéma. Retourne tous les nœuds d’affichage pour le schéma spécifié.|  
|[DB_VIEW]|CATÉGORIE|-|-|Nœud de la vue. Retourne tous les nœuds d’opération (Insert, Select, Update et Delete) pour la vue spécifiée.|  
|Insert|OPÉRATION SORTANTE|ViewOp/Insert / [DB_SCHEMA] / [DB_VIEW]|ViewOp/Insert/dbo/Employee_View|Afficher le nœud d’opération Insert. Retourne le WSDL pour l’opération d’insertion pour la vue spécifiée.|  
|Select|OPÉRATION SORTANTE|ViewOp/sélectionner / [DB_SCHEMA] / [DB_VIEW]|ViewOp/sélectionner/dbo/Employee_View|Nœud d’opération de sélection de vue. Retourne le WSDL pour l’opération de sélection pour la vue spécifiée.|  
|Update|OPÉRATION SORTANTE|ViewOp/mettre à jour / [DB_SCHEMA] / [DB_VIEW]|ViewOp/mise à jour/dbo/Employee_View|Afficher le nœud d’opération de mise à jour. Retourne le WSDL de l’opération de mise à jour de la vue spécifiée.|  
|DELETE|OPÉRATION SORTANTE|ViewOp/Delete / [DB_SCHEMA] / [DB_VIEW]|ViewOp/Delete/dbo/Employee_View|Afficher le nœud d’opération de suppression. Retourne le WSDL pour l’opération de suppression de l’affichage spécifié.|  
|Fonctions scalaires|CATÉGORIE|ScalarFunctions /|ScalarFunctions /|Nœud de fonctions scalaires de schéma. Retourne toutes les fonctions scalaires pour le schéma spécifié.|  
|[DB_SCLR_FUNCTION]|OPÉRATION SORTANTE|ScalarFunction / [DB_SCHEMA] / [DB_SCLR_FUNCTION]|ScalarFunction/dbo/GET_EMP_ID|Nœud de fonction scalaire. Retourne le langage WSDL pour la fonction scalaire spécifiée.|  
|Fonctions table|CATÉGORIE|TableFunctions /|TableFunctions /|Nœud de fonctions de table de schéma. Retourne toutes les fonctions de table pour le schéma spécifié.|  
|[DB_TBL_FUNCTION]|OPÉRATION SORTANTE|TableFunction / [DB_SCHEMA] / [DB_TBL_FUNCTION]|TableFunction/dbo/TVF_EMPLOYEE|Nœud de la fonction de la table. Retourne le langage WSDL pour la fonction table spécifié.|  
  
 [DB_SCHEMA] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
 [DB_TABLE] = le nom d’une table SQL Server ; par exemple, les employés.  
  
 [DB_VIEW] = le nom d’une vue SQL Server ; par exemple, Employee_View.  
  
 [DB_PROCEDURE] = le nom d’une procédure stockée SQL Server ; par exemple, ADD_EMP_DETAILS.  
  
 [DB_SCLR_FUNCTION] = le nom d’une fonction scalaire SQL Server ; par exemple, GET_EMP_ID.  
  
 [DB_TBL_FUNCTION] = le nom d’une fonction de table SQL Server ; par exemple, TVF_EMPLOYEE.  
  
## <a name="metadata-search-and-node-ids"></a>Recherche de métadonnées et les ID de nœud  
 Recherche de métadonnées est une puissante fonctionnalité le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] surfaces dans le cadre de son **MetadataRetrievalContract** interface. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise cette fonctionnalité pour prendre en charge la recherche sur les artefacts suivants de SQL Server. L’étendue de recherche de métadonnées est limitée au niveau immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée. Par exemple, pour rechercher une fonction scalaire, vous devez être fonction recherche sous/scalaire / [Schema]. Une recherche récursive n’est pas pris en charge.  
  
|Artefact|ID de nœud|Type de nœud retourné| Description|  
|--------------|-------------|------------------------|-----------------|  
|/ (autrement dit, le nœud racine)|/|CATÉGORIE|Retourner tous les nœuds de schéma qui correspond à l’expression de recherche.|  
|[DB_PROCEDURE]|/PROCEDURE/ [DB_SCHEMA]|OPÉRATION SORTANTE|Retourner tous les nœuds de procédure dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_TABLE]|/Table/ [DB_SCHEMA]|CATÉGORIE|Retourner tous les nœuds de table dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_VIEW]|/View/ [DB_SCHEMA]|CATÉGORIE|Retourner tous les nœuds de vue dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_SCLR_FUNCTION]|/ScalarFunction/ [DB_SCHEMA]|OPÉRATION SORTANTE|Retourner tous les nœuds de fonction scalaire dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_TBL_FUNCTION]|/TableFunction/ [DB_SCHEMA]|OPÉRATION SORTANTE|Retourner tous les nœuds de fonction table incluse dans le schéma spécifié qui correspondent à l’expression de recherche.|  
  
 [DB_SCHEMA] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
 [DB_TABLE] = le nom d’une table SQL Server ; par exemple, les employés.  
  
 [DB_VIEW] = le nom d’une vue SQL Server ; par exemple, Employee_View.  
  
 [DB_PROCEDURE] = le nom d’une procédure SQL Server ; par exemple, ADD_EMP_DETAILS.  
  
 [DB_SCLR_FUNCTION] = le nom d’une fonction scalaire SQL Server ; par exemple, GET_EMP_ID.  
  
 [DB_TBL_FUNCTION] = le nom d’une fonction de table SQL Server ; par exemple, TVF_EMPLOYEE.  
  
 Vous pouvez spécifier des expressions de recherche qui sont compatibles avec n’importe quelle expression valide qui peut être utilisée pour l’opérateur de SQL Server comme. Par exemple, pour effectuer une recherche sur les tables contenues dans un schéma, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction SQL suivante : `SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE ‘[SEARCH_STR]’`.  
  
 Le tableau suivant répertorie les caractères spéciaux qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge dans les expressions de recherche.  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|% (pourcentage)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, « Un % » correspond à « A », « AB », « ABC » et ainsi de suite.|  
|_ (souligné)|Correspond à exactement 1 caractère.<br /><br /> Par exemple, « A_ » correspond à « AB », « CA », « AD », et ainsi de suite.|  
|[ ]|-Remplace une signification spéciale _ et %.<br />-Spécifie une plage ou un jeu de caractères à être présents.<br /><br /> Exemple :<br /><br /> -% [%] correspond à tous les noms qui incluent un symbole %.<br />-[a-f] correspond à tous les noms qui ont des caractères entre et en incluant « a » et « f ».<br />-[abc] correspond à tous les noms contenant des caractères « a », « b » et « c ».|  
|[^]|Spécifie une plage ou un jeu de caractères ne devant ne pas être présents.<br /><br /> Exemple :<br /><br /> -[^ a-f] correspond à tous les noms qui n’ont pas de caractères entre et en incluant « a » et « f ».<br />-[^ abc] correspond à tous les noms qui n’ont pas de caractères « a », « b » et « c ».|  
  
## <a name="metadata-retrieval-and-node-ids"></a>Récupération de métadonnées et les ID de nœud  
 Le tableau suivant résume les caractéristiques des métadonnées retournées par [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
|Artefact|Caractéristiques des métadonnées|  
|--------------|------------------------------|  
|Table ou vue|<ul><li>Nom de la table.</li><li>Noms de champs de table.</li><li>Types de données de champ de table sont mappés aux types WSDL simples ou complexes.</li><li>Longueur de champ de table est mappée à la facette maxLength.</li><li>Contrainte de clé primaire de table champ est mappé à la facette minOccurs = 1.</li><li>Contrainte de table champ NULL est mappée à la facette isNillable = true.</li><li>Opérations de table<br /><br /> <ul><li>INSERT</li><li>SELECT</li><li>UPDATE</li><li>DELETE</li><li>Définissez\<nom de la colonne\></li></ul></li></ul>|  
|Procédure ou fonction|-Nom de fonction ou procédure est mappé au nom de l’opération.<br />-Noms de paramètre procédure ou fonction.<br />-Les types de données de paramètre procédure ou fonction sont mappés aux types WSDL.<br />-Direction du paramètre procédure ou fonction est mappée à la direction du paramètre WSDL.<br />-Procédure paramètre ou une fonction paramètre type longueur des données est mappée à la facette maxLength.<br />-Ordre des paramètres de fonction ou procédure est mappé à la séquence d’éléments.<br />-Fonction retourne le type de données est mappé au type WSDL.<br />-Fonction retourne la longueur du type de données est mappée à la facette maxLength.|  
  
 Pour plus d’informations sur le format des métadonnées qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose pour les artefacts et les opérations sur la base de données SQL Server, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).  
  