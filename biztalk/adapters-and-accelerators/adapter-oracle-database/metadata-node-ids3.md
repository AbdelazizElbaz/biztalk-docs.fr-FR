---
title: "ID de nœud de métadonnées de l’adaptateur de base de données Oracle dans le Pack d’adaptateurs BizTalk | Documents Microsoft"
description: "Métadonnées, search, les types de nœuds de récupération et les identificateurs utilisés dans les composants Oracle qui sont exposées dans la carte de base de données Oracle - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 523c7611-b21f-4598-ac77-ba71075db073
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acb916e376a5e2dfa72483a9039b0d6cea4bae81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="node-types-and-ids-for-the-oracle-database-adapter"></a>Types de nœuds et ID de l’adaptateur de base de données Oracle

## <a name="metadata-node-types-and-ids"></a>Types de nœuds de métadonnées et des ID 
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces Oracle base de données des artefacts de façon hiérarchique. Le tableau suivant répertorie les types de nœuds et l’ID de nœud pour les artefacts de base de données Oracle qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces. L’ID de nœud est le chemin d’accès absolu du nœud qui est utilisé dans le **IMetadataRetrievalContractBrowse**, **recherche**, et **GetMetadata** méthodes.  
  
|Nom complet de l’objet|Type de nœud|ID de nœud|Exemple| Description|  
|---------------------------|---------------|-------------|-------------|-----------------|  
|--|CATÉGORIE|/|/|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]nœud racine. Retourne tous les nœuds de premier niveau ; Cela inclut le nœud d’opération SQLEXECUTE, le nœud d’opération POLLINGSTMT et tous les nœuds de schéma|  
|SQLEXECUTE|OPERATION|[VERSION] / SQLEXECUTE|http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE|Nœud d’opération SQLEXECUTE. Retourne le WSDL pour l’opération SQLEXECUTE.|  
|POLLINGSTMT|OPERATION|[VERSION] / POLLINGSTMT|http://Microsoft.LobServices. OracleDB/2007/03/POLLINGSTMT|Nœud d’opération POLLINGSTMT. Retourne le WSDL pour l’opération POLLINGSTMT.|  
|[DB_SCHEMA]|CATÉGORIE|[VERSION] / [DB_SCHEMA]|http://Microsoft.LobServices.OracleDB/2007/03/Scott|Nœud de schéma. Retourne les nœuds de catégorie générale (Table, vue, procédure, fonction et Package) pour le schéma spécifié.|  
|Table|CATÉGORIE|[VERSION] / [DB_SCHEMA] / de Table|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table|Nœud de schéma tables. Retourne tous les nœuds de table pour le schéma spécifié.|  
|[DB_TABLE]|CATÉGORIE|[VERSION] / [DB_SCHEMA] /Table/ [DB_TABLE]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp|Nœud de la table. Retourne tous les nœuds d’opération (Insert, Select, Update, Delete, ReadLOB et UpdateLOB) pour la table spécifiée. (ReadLOB et UpdateLOB ne sont renvoyées pour les tables qui contiennent une colonne LOB.)|  
|Insert|OPERATION|[VERSION] / [DB_SCHEMA] /Table/ [DB_TABLE] / insertion|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/INSERT|Insérer un nœud de fonctionnement de la table. Retourne le WSDL pour l’opération d’insertion pour la table spécifiée.|  
|Select|OPERATION|[VERSION] / [DB_SCHEMA] /Table/ [DB_TABLE] / sélectionner|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/SELECT|Nœud d’opération de sélection de table. Retourne le WSDL pour l’opération de sélection pour la table spécifiée.|  
|Update|OPERATION|[VERSION] / [DB_SCHEMA] /Table/ [DB_TABLE] / mise à jour|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Update|Nœud d’opération de mise à jour de la table. Retourne le WSDL pour l’opération de mise à jour pour la table spécifiée.|  
|DELETE|OPERATION|[VERSION] / [DB_SCHEMA] /Table/ [DB_TABLE] / Delete|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Delete|Nœud d’opération de suppression de la table. Retourne le WSDL pour l’opération de suppression pour la table spécifiée.|  
|ReadLOB|OPERATION|[VERSION] / [DB_SCHEMA] /Table/ [DB_TABLE] / ReadLOB|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/ReadLOB|Nœud d’opération ReadLOB de la table. Retourne le WSDL pour l’opération ReadLOB pour la table spécifiée. (Visible uniquement si la table contient une colonne LOB).|  
|UpdateLOB|OPERATION|[VERSION] / [DB_SCHEMA] /Table/ [DB_TABLE] / UpdateLOB|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/UpdateLOB|Nœud d’opération UpdateLOB de la table. Retourne le WSDL pour l’opération UpdateLOB pour la table spécifiée. (Visible uniquement si la table contient une colonne LOB).|  
|Affichage|CATÉGORIE|[VERSION] / [DB_SCHEMA] / afficher|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View|Nœud de vues de schéma. Retourne tous les nœuds d’affichage pour le schéma spécifié.|  
|[DB_VIEW]|CATÉGORIE|[VERSION] / [DB_SCHEMA] /View/ [DB_VIEW]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View/SALES_VIEW|Nœud de la vue. Retourne tous les nœuds d’opération (Insert, Select, Update, Delete, ReadLOB et UpdateLOB) pour la vue spécifiée. (ReadLOB et UpdateLOB ne sont renvoyées pour les vues qui contiennent une colonne LOB.)|  
|Insert|OPERATION|[VERSION] / [DB_SCHEMA] /View/ [DB_VIEW] / insertion|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View/SALES_VIEW/INSERT|Afficher le nœud d’opération Insert. Retourne le WSDL pour l’opération d’insertion pour la vue spécifiée.|  
|Select|OPERATION|[VERSION] / [DB_SCHEMA] /View/ [DB_VIEW] / sélectionner|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View/SALES_VIEW/SELECT|Nœud d’opération de sélection de vue. Retourne le WSDL pour l’opération de sélection pour la vue spécifiée.|  
|Update|OPERATION|[VERSION] / [DB_SCHEMA] /View/ [DB_VIEW] / mise à jour|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View/SALES_VIEW/Update|Afficher le nœud d’opération de mise à jour. Retourne le WSDL de l’opération de mise à jour de la vue spécifiée.|  
|DELETE|OPERATION|[VERSION] / [DB_SCHEMA] /View/ [DB_VIEW] / Delete|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View/SALES_VIEW/Delete|Afficher le nœud d’opération de suppression. Retourne le WSDL pour l’opération de suppression de l’affichage spécifié.|  
|ReadLOB|OPERATION|[VERSION] / [DB_SCHEMA] /View/ [DB_VIEW] / ReadLOB|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View/SALES_VIEW/ReadLOB|Afficher le nœud d’opération ReadLOB. Retourne le WSDL pour l’opération ReadLOB pour la vue spécifiée. (Visible uniquement si la vue contient une colonne LOB).|  
|UpdateLOB|OPERATION|[VERSION] / [DB_SCHEMA] /View/ [DB_VIEW] / UpdateLOB|http://Microsoft.LobServices.OracleDB/2007/03/Scott/View/SALES_VIEW/UpdateLOB|Afficher le nœud d’opération de mise à jour. Retourne le WSDL pour l’opération UpdateLOB pour la table spécifiée. (Visible uniquement si la vue contient une colonne LOB).|  
|Procédure|CATÉGORIE|[VERSION] / [DB_SCHEMA] / procédure|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Procedure|Nœud de schéma des procédures. Retourne toutes les procédures pour le schéma spécifié.|  
|[DB_PROCEDURE]|OPERATION|[VERSION] / [DB_SCHEMA] /Procedure/ [DB_PROCEDURE]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Procedure/SP_GENREPORT|Nœud de la procédure. Retourne le langage WSDL pour la procédure spécifiée.|  
|Fonction|CATÉGORIE|[VERSION] / [DB_SCHEMA] / fonction|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Function|Nœud de fonctions de schéma. Retourne toutes les fonctions pour le schéma spécifié.|  
|[DB_FUNCTION]|OPERATION|[VERSION] / [DB_SCHEMA] /Function/ [DB_FUNCTION]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/Function/FN_GETUSERID|Nœud de fonction. Retourne le langage WSDL pour la fonction spécifiée.|  
|Package|CATÉGORIE|[VERSION] / [DB_SCHEMA] / Package|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package|Nœud packages de schéma. Retourne tous les packages pour le schéma spécifié.|  
|[DB_PACKAGE]|CATÉGORIE|[VERSION] / [DB_SCHEMA] /Package/ [DB_PACKAGE]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package/ACCOUNT_PKG|Nœud des packages. Retourne toutes les procédures et fonctions pour le package spécifié.|  
|[PACK_PROCEDURE]|OPERATION|[VERSION] / [DB_SCHEMA] /Package/ [DB_PACKAGE] / [PACK_PROCEDURE]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package/ACCOUNT_PKG/GET_ACCOUNT|Noeud de procédure du package. Retourne le langage WSDL pour la procédure de package spécifié.|  
|[PACK_FUNCTION]|OPERATION|[VERSION] / [DB_SCHEMA] /Package/ [DB_PACKAGE] / [PACK_FUNCTION]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/package/ACCOUNT_PKG/CREATE_ACCOUNT|Nœud de fonction de package. Retourne le langage WSDL pour la fonction de package spécifié.|  
  
 [VERSION] = la chaîne de version ; par exemple, http://Microsoft.LobServices.OracleDB/2007/03.  
  
 [DB_SCHEMA] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [DB_TABLE] = le nom d’une table Oracle ; par exemple, EMP.  
  
 [DB_VIEW] = le nom d’une vue d’Oracle ; par exemple, SALES_VIEW.  
  
 [DB_PROCEDURE] = le nom d’une procédure d’Oracle ; par exemple, SP_GENREPORT.  
  
 [DB_FUNCTION] = le nom d’une fonction d’Oracle ; par exemple, FN_GETUSERID.  
  
 [DB_PACKAGE] = le nom d’un package Oracle ; par exemple, ACCOUNT_PKG.  
  
 [PACK_PROCEDURE] = le nom d’une procédure de package ; par exemple, GET_ACCOUNT.  
  
 [PACK_FUNCTION] = le nom d’une fonction de package ; par exemple, CREATE_ACCOUNT.  
  
## <a name="metadata-search-and-node-ids"></a>Recherche de métadonnées et les ID de nœud  
 Recherche de métadonnées est une puissante fonctionnalité le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] surfaces dans le cadre de son **MetadataRetrievalContract** interface. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise cette fonctionnalité pour prendre en charge la recherche sur les artefacts Oracle suivants. L’étendue de recherche de métadonnées est limitée au niveau immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée. Par exemple, pour rechercher une fonction, vous devez être recherche sous \\[schéma] \Functions. Une recherche récursive n’est pas pris en charge.  
  
|Artefact|ID de nœud|Type de nœud retourné| Description|  
|--------------|-------------|------------------------|-----------------|  
|[DB_SCHEMA]|/ (autrement dit, le nœud racine)|CATÉGORIE|Retourner tous les nœuds de schéma qui correspond à l’expression de recherche.|  
|[DB_TABLE]|/ [VERSION] / [DB_SCHEMA] / de Table|CATÉGORIE|Retourner tous les nœuds de table dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_VIEW]|/ [VERSION] / [DB_SCHEMA] / afficher|CATÉGORIE|Retourner tous les nœuds de vue dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_PROCEDURE]|/ [VERSION] / [DB_SCHEMA] / procédure|OPERATION|Retourner tous les nœuds de procédure dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_FUNCTION]|/ [VERSION] / [DB_SCHEMA] / fonction|OPERATION|Retourner tous les nœuds de fonction dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[DB_PACKAGE]|/ [VERSION] / [DB_SCHEMA] / Package|CATÉGORIE|Retourner tous les nœuds de package (catégorie) dans le schéma spécifié qui correspondent à l’expression de recherche.|  
|[PACK_PROCEDURE] et [PACK_FUNCTION]|/ [VERSION] / [DB_SCHEMA] /Package/ [DB_PACKAGE]|OPERATION|Retourner tous les nœuds de fonction et procédure (opération) dans le package spécifié qui correspondent à l’expression de recherche.|  
  
 [VERSION] = la chaîne de version ; par exemple, http://Microsoft.LobServices/2007/03.  
  
 [DB_SCHEMA] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [DB_TABLE] = le nom d’une table Oracle ; par exemple, EMP.  
  
 [DB_VIEW] = le nom d’une vue d’Oracle ; par exemple, SALES_VIEW.  
  
 [DB_PROCEDURE] = le nom d’une procédure d’Oracle ; par exemple, SP_GENREPORT.  
  
 [DB_FUNCTION] = le nom d’une fonction d’Oracle ; par exemple, FN_GETUSERID.  
  
 [DB_PACKAGE] = le nom d’un package Oracle ; par exemple, ACCOUNT_PKG.  
  
 [PACK_PROCEDURE] = le nom d’une procédure de package ; par exemple, GET_ACCOUNT.  
  
 [PACK_FUNCTION] = le nom d’une fonction de package ; par exemple, CREATE_ACCOUNT.  
  
 Vous pouvez spécifier des expressions de recherche qui sont compatibles avec n’importe quelle expression valide qui peut être utilisée pour l’opérateur LIKE Oracle. Par exemple, pour effectuer une recherche sur les tables contenues dans un schéma, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute l’instruction SQL suivante : `SELECT TABLE_NAME FROM ALL_TABLES WHERE OWNER = '[OWNER_NAME]' AND TABLE_NAME LIKE ‘[SEARCH_STR]’`.  
  
 Le tableau suivant répertorie les caractères spéciaux qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge dans les expressions de recherche.  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|% (pourcentage)|Correspond à zéro ou plusieurs caractères ; par exemple, « Un % » correspond à « A », « AB », « ABC » et ainsi de suite.|  
|_ (souligné)|Correspond à exactement 1 caractère ; par exemple, « A_ » correspond à « AB », « CA », « AD », et ainsi de suite.|  
|\ (échappement)|Remplace la signification de '%' et '_' ; par exemple, « A\\_B » correspond à « A_B ».|  
  
## <a name="metadata-retrieval-and-node-ids"></a>Récupération de métadonnées et les ID de nœud  
 Le tableau suivant résume les caractéristiques des métadonnées retournées par [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
|Artefact|Caractéristiques des métadonnées|  
|--------------|------------------------------|  
|Table ou vue|<ul><li>Nom de la table.</li><li>Noms de champs de table.</li><li>Types de données de champ de table sont mappés aux types WSDL simples ou complexes.</li><li>Longueur de champ de table est mappée à la facette maxLength.</li><li>Contrainte de clé primaire de table champ est mappé à la facette minOccurs = 1.</li><li>Contrainte de table champ NULL est mappée à la facette isNillable = true.</li><li>Opérations de table<br /><br /> <ul><li>INSERT</li><li>SELECT</li><li>UPDATE</li><li>DELETE</li><li>READLOB (si la table contient un champ de type Oracle LOB)</li><li>UPDATELOB (si la table contient un champ de type Oracle LOB)</li></ul></li></ul>|  
|Procédure ou fonction|-Nom de fonction ou procédure est mappé au nom de l’opération.<br />-Noms de paramètre procédure ou fonction.<br />-Les types de données de paramètre procédure ou fonction sont mappés aux types WSDL.<br />-Direction du paramètre procédure ou fonction est mappée à la direction du paramètre WSDL.<br />-Procédure paramètre ou une fonction paramètre type longueur des données est mappée à la facette maxLength.<br />-Ordre des paramètres de fonction ou procédure est mappé à la séquence d’éléments.<br />-Fonction retourne le type de données est mappé au type WSDL.<br />-Fonction retourne la longueur du type de données est mappée à la facette maxLength.|  
|Procédure de package ou une fonction.|-Nom package.<br />-Les autres caractéristiques procédure et la fonction comme indiqué ci-dessus.|  
  
 Pour plus d’informations sur le format des métadonnées qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose pour les artefacts et les opérations sur la base de données Oracle, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  
  
## <a name="see-also"></a>Voir aussi  
[Obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](get-metadata-for-oracle-database-operations-in-visual-studio.md)