---
title: "Parcourir, rechercher et obtenir des métadonnées de la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MetadataExchange
- metadata, searching
- metadata, browsing
- POLLINGSTMT
- metadata, retrieving
- IMetadataRetrievalContract
- SQLEXECUTE
ms.assetid: 828d5a8e-f0a3-47b4-8298-5571cff64b52
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765663d51fa1bab4f700aa3aff726085e5464716
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-oracle-database-metadata"></a>Parcourir, rechercher et obtenir des métadonnées de la base de données Oracle
Le[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces des métadonnées à partir de la base de données Oracle qui décrit la structure du message pour la communication avec la base de données Oracle à l’aide de l’adaptateur. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge deux interfaces de récupération des métadonnées.  
  
-   MetadataExchange fournie par [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF fournit un point de terminaison d’échange de métadonnées pour toutes les liaisons WCF, ce qui permet aux clients d’obtenir des métadonnées à partir de la base de données Oracle.  
  
-   IMetadataRetrievalContract fournie par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], qui prend en charge les métadonnées de parcourir et rechercher des fonctions de l’adaptateur.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces Oracle de la base de données des artefacts et des opérations respectives que les clients de l’adaptateur peuvent appeler. L’adaptateur met également en évidence les opérations SQLEXECUTE, POLLINGSTMT et de Notification qui peuvent être utilisées pour effectuer des opérations spécifiques sur la base de données Oracle. Ces opérations sont décrites plus loin dans cette rubrique.  
  
 Les clients de l’adaptateur peuvent parcourir, rechercher et récupérer des métadonnées à l’aide du modèle de canal WCF, à l’aide du modèle de service WCF ou en créant un projet BizTalk dans Visual Studio. Lorsque vous utilisez le modèle de service WCF, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer les classes proxy pour effectuer des opérations sur la base de données Oracle. Lorsque vous utilisez un projet BizTalk, vous devez utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des métadonnées pour les opérations que vous souhaitez effectuer sur la base de données Oracle. Pour plus d’informations sur la navigation, la recherche et la récupération de métadonnées à l’aide [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).  
  
## <a name="browsing-metadata"></a>Exploration des métadonnées  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet aux clients d’adaptateur parcourir les tables de base de données, vues de table, procédures stockées, fonctions et les packages qui sont disponibles dans la base de données Oracle. Dans le cadre de l’opération de parcourir des métadonnées, l’adaptateur met également en évidence les opérations qui peuvent être effectuées sur la base de données Oracle, notamment certaines opérations personnalisées prises en charge par les adaptateurs. Ces opérations sont disponibles à partir de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] met en évidence les opérations suivantes :  
  
 **Opérations sortantes**  
  
 Contient une liste de schémas dans la base de données Oracle. Développez un nœud de schéma pour voir les artefacts suivants :  
  
-   **Table**: une liste de toutes les tables dans le schéma. Sélectionnez une table pour afficher l’insertion, de sélectionner, de mise à jour et les opérations de suppression.  
  
-   **Procédure**: une liste des procédures stockées dans le schéma qui sont exposées en tant qu’opérations.  
  
-   **Fonction**: une liste de fonctions dans le schéma qui sont exposées en tant qu’opérations.  
  
-   **Package**: une liste de tous les packages dans le schéma. Sélectionnez un package pour afficher les procédures et fonctions qui sont exposées en tant qu’opérations à l’intérieur du package.  
  
-   **Vue**: une liste de toutes les vues dans le schéma. Sélectionnez une vue pour afficher l’insertion, de sélectionner, de mise à jour et les opérations de suppression.  
  
 En outre, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose également le **SQLEXECUTE** opération sortante, ce qui permet aux clients l’adaptateur d’exécuter n’importe quel langage de manipulation de données génériques (DML) ou d’une procédure stockée dans une base de données Oracle. L’opération SQLEXECUTE est disponible lorsque vous sélectionnez le nœud racine (/). Notez que la sortie de SQLEXECUTE est un tableau de lecteurs de données (sortie en tant que tableau d’enregistrements génériques). Par conséquent, tout simple, les paramètres de sortie ne sont pas signalées à l’aide de l’opération SQLEXECUTE. Pour plus d’informations sur l’opération, consultez [opération SQLEXECUTE dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md).  
  
 **Opérations entrantes**  
  
 Contient une liste de schémas dans la base de données Oracle. Développez un nœud de schéma pour voir les artefacts suivants :  
  
-   **Procédure**: une liste des procédures stockées dans le schéma qui sont exposées en tant qu’opérations pour l’interrogation.  
  
-   **Fonction**: une liste de fonctions dans le schéma qui sont exposées en tant qu’opérations pour l’interrogation.  
  
-   **Package**: une liste des packages dans le schéma. Sélectionnez un package pour afficher les procédures empaquetées et les fonctions qui sont exposées en tant qu’opérations pour l’interrogation.  
  
 En outre, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose également le **POLLINGSTMT** et **Notification** opérations entrantes. L’opération POLLINGSTMT permet aux clients de carte obtenir les données entrantes à partir de la base de données Oracle basé sur une requête d’interrogation mécanisme pris en charge par l’adaptateur. L’opération de Notification permet aux clients de l’adaptateur inscrire une instruction SELECT en tant que la notification de requête sur la base de données et la base de données envoie une notification au client en tant que carte et lorsque le jeu de résultats de l’instruction SELECT est modifiée. Les opérations POLLINGSTMT et les notifications sont disponibles lorsque vous sélectionnez le nœud racine (/). Pour plus d’informations sur les opérations, consultez [prise en charge des Messages de modification de données basés sur la réception d’interrogation](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md).md) et [considérations relatives à la réception de base de données changeur des Notifications à l’aide de l’adaptateur de base de données Oracle ](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).  
  
 Pour plus d’informations sur la façon dont les métadonnées sont catégorisée, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).  
  
## <a name="searching-metadata"></a>Recherche de métadonnées  
 Avec la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], il est possible d’effectuer une requête de recherche sur la base de données Oracle à l’aide d’expressions de recherche Oracle qui sont compatibles avec l’opérateur LIKE. Par exemple, les clients de l’adaptateur peuvent utiliser une expression de recherche telles que « EMP % » pour obtenir des tables commençant par EMP. L’adaptateur convertit en la requête SQL suivante :  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%' AND OWNER = 'SCOTT'  
```  
  
 WHERE, SCOTT est le schéma avec une collection d’objets de base de données Oracle.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|_ (souligné)|Correspond à exactement un caractère<br /><br /> Par exemple, A_ correspond à AB, CA, Active Directory.|  
|% (pourcentage)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, un % correspond à un, AB, ABC.|  
|\ (échappement)|Remplace une signification spéciale % et _<br /><br /> Par exemple, un\\_B correspond à A_B.|  
  
> [!IMPORTANT]
>  L’étendue de recherche de métadonnées est limitée au niveau immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée. Par exemple, pour rechercher une fonction, vous devez être recherche sous \\[schéma] \Functions. Une recherche récursive n’est pas pris en charge.  
  
## <a name="retrieving-metadata"></a>Récupération de métadonnées  
 Lors de la récupération des métadonnées, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] peut extraire des métadonnées dans un schéma, y compris l’ensemble ou un sous-ensemble de la base de données des objets avec les paramètres respectifs de l’objet et l’opération. L’adaptateur présente les entités à partir de la base de données Oracle en tant que noms d’éléments XML. Étant donné que des traits de soulignement sont les seuls caractères spéciaux qui peuvent être inclus, tous les autres caractères spéciaux dans les noms d’élément sont encodés à l’aide des traits de soulignement. Par exemple, `emp$name` est encodé comme `emp_x0024_name`.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)   
 [Comprendre l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)   
[Obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)