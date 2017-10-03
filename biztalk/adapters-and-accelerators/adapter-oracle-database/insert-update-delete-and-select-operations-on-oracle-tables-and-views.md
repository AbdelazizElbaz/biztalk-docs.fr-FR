---
title: "INSERT, Update, Delete et des opérations Select sur Oracle tables et vues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, on tables and views
- operations, performing
- data manipulation language
- Delete operation
- Insert operation
- Update operation
- DELETE statement
- DML operation
- Select operation
- INSERT statement
- UPDATE statement
ms.assetid: af65fac4-3c16-40c4-ae7a-9c1757223f99
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04770dd5004d46df93da71b910cc228be1751ae7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="insert-update-delete-and-select-operations-on-oracle-tables-and-views"></a>Insérer, mettre à jour, supprimer et sélectionnez les opérations sur les tables Oracle et des vues
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un ensemble d’opérations standards sur chaque table de base de données Oracle et de la vue. À l’aide de ces opérations, vous pouvez effectuer de simples sélectionnez SQL INSERT, UPDATE et supprimer les instructions qualifiées par une clause WHERE sur la table cible (ou vue). Ces opérations sont également appelées opérations data manipulation language (DML). Pour effectuer des opérations plus complexes, par exemple une requête SQL SELECT qui utilise l’opérateur de jointure, vous pouvez utiliser l’opération SQLEXECUTE. Pour plus d’informations sur l’opération SQLEXECUTE, consultez [opération SQLEXECUTE dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md).  
  
 Le tableau suivant présente les opérations DML qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge :  
  
|Opération| Description|  
|---------------|-----------------|  
|Insert|Effectue une opération d’insertion sur la table ou vue cible. L’opération d’insertion prend en charge plusieurs des insertions en bloc ou d’enregistrement dans la table ou vue cible :<br /><br /> -Une opération d’insertion plusieurs enregistrement insère des lignes dans une table ou une vue basée sur un jeu d’enregistrements fourni.<br /><br /> -Une opération d’insertion en bloc insère des lignes dans une table ou une vue basée sur un SQL SELECT de requêtes et de colonne liste fournie. La requête retourne les enregistrements sont insérés dans la table cible en fonction de la liste des colonnes.<br /><br /> La valeur de retour pour une opération d’insertion est le nombre de lignes insérées.<br /><br /> **Remarque :** les deux enregistrements multiples insérer et l’insertion en bloc ne peuvent pas être combinée dans le même message.<br /><br /> **InlineValue**<br /><br /> Pour tous les enregistrements de données simple dans une opération d’insertion plusieurs enregistrement, vous pouvez choisir remplacer la valeur d’un enregistrement en spécifiant une valeur d’un attribut facultatif appelé **InlineValue**. L’attribut InlineValue peut être utilisé pour insérer des valeurs calculées dans des tables ou vues, telles que le remplissage de la colonne de clé primaire à l’aide d’une séquence ou d’insérer la date système (à l’aide de SYSDATE) dans une colonne de date. Par exemple, dans l’instruction INSERT suivante :<br /><br /> `<Insert xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY">   <RECORDSET>     <ACCOUNTACTIVITYRECORDINSERT>       <ACCOUNT>10001</ACCOUNT>       <EMPNAME>John</EMPNAME>       <AMOUNT>1500</AMOUNT>       <TRANSDATE InlineValue="SYSDATE">2008-06-21T15:52:19</TRANSDATE>       </ACCOUNTACTIVITYRECORDINSERT >   </RECORDSET> </Insert>`<br /><br /> Bien que « 2008-06-21T15:52:19 » est spécifié en tant que valeur pour la colonne de date de transaction, la valeur de l’attribut InlineValue, « SYSDATE », (date système) est inséré dans la table cible.<br /><br /> Lors de l’utilisation de la InlineValue d’attribut :<br /><br /> -Évitez d’utiliser des valeurs de constante pour l’attribut InlineValue. Par exemple, dans l’instruction INSERT, si vous spécifiez `<EMPNAME InlineValue="John"/>` puis entraîne une erreur. C’est parce que la valeur de l’attribut InlineValue est passée comme-consiste à Oracle et dans ce cas *John* est transmis à la base de données Oracle, qui n’est pas la valeur attendue (valeur attendue est *« John »*). Vous devez utiliser des guillemets simples autour du nom de l’employé. Par exemple : `<EMPNAME InlineValue="’John’"/>`.<br /><br /> -Si vous souhaitez utiliser une requête select pour l’attribut InlineValue, vous devez placer l’instruction SELECT entre parenthèses et également vous assurer que la requête select n'extrait qu’un seul enregistrement. Par exemple : `<EMPNAME InlineValue="(SELECT NAME FROM MS_SAMPLE_EMPLOYEES WHERE ID=123)"/>`.<br /><br /> **Remarque :** si un élément est marqué comme NOT NULL dans la base de données Oracle, vous devez spécifier une valeur pour cet élément même si vous avez spécifié une valeur inline. Ne parvient pas à cela entraîne la validation de schéma échoue.|  
|Select|Effectue une requête SQL SELECT sur la table ou vue cible basée sur une liste de noms de colonne et une chaîne de filtrage qui spécifie une clause SQL WHERE fournie.<br /><br /> La valeur de retour pour une opération de sélection est un jeu de résultats de fortement typé qui contient les colonnes spécifiées et les lignes.|  
|Update|Effectue une opération de mise à jour sur la table ou vue cible. Les enregistrements doivent être mis à jour sont spécifiées par une chaîne de filtrage qui spécifie une clause SQL WHERE. Les valeurs pour la mise à jour sont spécifiées dans un enregistrement du modèle.<br /><br /> La valeur de retour pour une opération de mise à jour est le nombre de lignes mises à jour.|  
|DELETE|Effectue une opération de suppression sur la table ou vue cible basée sur une clause SQL WHERE qui est spécifiée dans une chaîne de filtre.<br /><br /> La valeur de retour pour une opération de suppression est le nombre de lignes supprimées.|  
  
 Pour plus d’informations sur :  
  
-   Effectuez ces opérations à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Insert, Update, Delete et sélectionnez les opérations à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-using-biztalk-server-with-oracle-db.md).  
  
-   Effectuez ces opérations à l’aide du modèle de service WCF, consultez [Insert, Update, Delete et sélectionnez les opérations à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md).  
  
-   Effectuez ces opérations à l’aide du modèle de canal WCF, consultez [exécuter une opération d’insertion dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md).  
  
-   Action SOAP pour effectuer des opérations DML et les structures de message, consultez [des schémas de Message pour la base opérations d’insertion, mise à jour, supprimer et sélectionnez sur les Tables et vues](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)