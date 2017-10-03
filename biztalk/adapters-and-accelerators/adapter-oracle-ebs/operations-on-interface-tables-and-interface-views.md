---
title: "Opérations sur les Tables d’Interface et les vues de l’Interface | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c7f3453-848f-42df-b092-725d9ff466cf
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ec9b7c5f952b6be60a3c3463e6ea0682faa9d4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-interface-tables-and-interface-views"></a>Opérations sur les Tables d’Interface et les vues de l’Interface
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose un ensemble d’opérations standard (Select, Insert, Update et Delete pour chaque table d’interface) et l’opération de sélection pour chaque vue de l’interface dans Oracle E-Business Suite. À l’aide de ces opérations, vous pouvez effectuer le SELECT, l’insertion, la mise à jour et supprimer les instructions qualifiées par une clause WHERE sur la table d’interface cible et l’instruction SELECT qualifié par une clause WHERE de la vue d’interface cible. Ces opérations sont également appelées opérations data manipulation language (DML).  
  
> [!IMPORTANT]
>  Avant de pouvoir effectuer des opérations sur les tables d’interface et les vues de l’interface, vous devez définir le contexte des applications pour ces artefacts dans [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Il s’agit, car le contexte des applications paramètre facilite la sécurité des transactions dans Oracle E-Business Suite en définissant des préférences de l’utilisateur (telles que les paramètres de gestion, d’organisation et langage) et de contrôle d’accès pour un artefact. Pour plus d’informations sur le contexte des applications et comment le configurer, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  

## <a name="supported-dml-operations"></a>Prise en charge les opérations DML  
 Le tableau suivant présente les opérations DML qui le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge :  
  
|Opération| Description|  
|---------------|-----------------|  
|Select|Effectue une opération Select sur la vue de table ou une interface d’interface cible basée sur une liste de noms de colonne et une chaîne de filtrage qui spécifie une clause SQL WHERE fournie.<br /><br /> La valeur de retour pour une opération de sélection est un jeu de résultats de fortement typé qui contient les colonnes spécifiées et les lignes.|  
|Insert|Effectue une opération d’insertion sur la table d’interface cible. L’insertion opération prend en charge plusieurs enregistrements insérer dans la table d’interface cible basée sur un jeu d’enregistrements fourni.<br /><br /> La valeur de retour pour une opération d’insertion est le nombre de lignes insérées.<br /><br /> **InlineValue**<br /><br /> Pour tous les enregistrements de données simple dans une opération d’insertion, vous pouvez choisir de remplacer la valeur d’un enregistrement en spécifiant une valeur d’un attribut facultatif appelé **InlineValue**. L’attribut InlineValue peut être utilisé pour insérer des valeurs calculées dans les tables d’interface telles que le remplissage de la colonne de clé primaire à l’aide d’une séquence ou d’insérer la date système (à l’aide de SYSDATE) dans une colonne de date. Par exemple, dans l’instruction INSERT suivante :<br /><br /> `<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR_ARCHIVE_PURGE_INTERIM">   <RECORDSET>     <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">       <TRNS_DATE InlineValue="sysdate">2008-06-21T15:52:19</TRNS_DATE>       <EMPNAME>John</EMPNAME>     </InsertRecord>   </RECORDSET>   </Insert>`<br /><br /> Bien que « 2008-06-21T15:52:19 » est spécifié en tant que valeur pour TRNS_DATE, la valeur de la **InlineValue** attribut, « SYSDATE », (date système) est inséré dans la table d’interface cible.<br /><br /> Lors de l’utilisation de la InlineValue d’attribut :<br /><br /> -Évitez d’utiliser des valeurs de constante pour l’attribut InlineValue. Par exemple, dans l’instruction INSERT, si vous spécifiez `<EMPNAME InlineValue="John"/>` puis entraîne une erreur. C’est parce que la valeur de l’attribut InlineValue est passée comme-consiste à Oracle et dans ce cas *John* est passé pour Oracle E-Business Suite, qui n’est pas la valeur attendue (valeur attendue est *« John »*). Vous devez utiliser des guillemets simples autour du nom de l’employé. Par exemple : `<EMPNAME InlineValue="’John’"/>`.<br /><br /> -Si vous souhaitez utiliser une requête select pour l’attribut InlineValue, vous devez placer l’instruction SELECT entre parenthèses et également vous assurer que la requête select n'extrait qu’un seul enregistrement. Par exemple : `<EMPNAME InlineValue="(SELECT NAME FROM MS_SAMPLE_EMPLOYEES WHERE ID=123)"/>`.<br /><br /> **Remarque :** si un élément est marqué comme NOT NULL dans Oracle E-Business Suite, vous devez spécifier une valeur pour cet élément même si vous avez spécifié une valeur inline. Ne parvient pas à cela entraîne la validation de schéma échoue.|  
|Update|Effectue une opération de mise à jour sur la table d’interface cible. Les enregistrements doivent être mis à jour sont spécifiées par une chaîne de filtrage qui spécifie une clause SQL WHERE. Les valeurs pour la mise à jour sont spécifiées dans un enregistrement du modèle.<br /><br /> La valeur de retour pour une opération de mise à jour est le nombre de lignes mises à jour.|  
|DELETE|Effectue une opération de suppression sur la table d’interface cible basée sur une clause SQL WHERE qui est spécifiée dans une chaîne de filtre.<br /><br /> La valeur de retour pour une opération de suppression est le nombre de lignes supprimées.|  

## <a name="important-details"></a>Obtenir des informations importantes  
  -   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] met en évidence le même jeu d’opérations standard (Select, Insert, Update et Delete pour chaque table) et l’opération de sélection pour chaque vue dans la base de données Oracle. Les opérations DML sont également valides pour les tables de base de données Oracle sous-jacentes et les vues.  

 -   Il n’est pas nécessaire pour définir le contexte d’applications pour effectuer des opérations sur les tables et vues dans la base de données Oracle. Toutefois, pour des applications personnalisées Oracle E-Business Suite, les utilisateurs peuvent ou ne peuvent pas enregistrer les tables de base de données en tant que tables de l’interface. Si une table de base de données n’est pas enregistrée comme un tableau d’interface, il est disponible sous la **Tables** sous-noeud dans le **artefact basés sur une vue** nœud ou dans le **vue schéma** nœud au moment du design en utilisant [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
    Ces tables sont associées à une application Oracle E-Business. Par conséquent, pour toute opération sur ces tables, vous devez définir le contexte d’application. Consultez le contexte de l’Application définie[Entrez la description du lien ici](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)