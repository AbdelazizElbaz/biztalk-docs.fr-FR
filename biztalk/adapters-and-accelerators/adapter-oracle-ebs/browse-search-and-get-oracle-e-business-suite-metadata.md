---
title: "Parcourir, rechercher et obtenir des métadonnées d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b516c6e9-dbb3-4977-bb27-aa039e021912
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ce665ef71cbf0849caab334cf62c5f7a659ea96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-oracle-e-business-suite-metadata"></a>Parcourir, rechercher et obtenir des métadonnées d’Oracle E-Business Suite
Les métadonnées qui [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] surfaces à partir d’Oracle E-Business Suite et de la base de données Oracle décrit la structure du message pour la communication avec Oracle E-Business Suite à l’aide de l’adaptateur. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge deux interfaces de récupération des métadonnées.  
  
-   MetadataExchange fournie par [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF fournit un point de terminaison d’échange de métadonnées pour toutes les liaisons WCF, ce qui permet aux clients d’obtenir des métadonnées à partir d’Oracle E-Business Suite.  
  
-   IMetadataRetrievalContract fournie par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], qui prend en charge les métadonnées de parcourir et rechercher des fonctions de l’adaptateur.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces Oracle E-Business Suite et des artefacts de base de données sous-jacente et opérations respectives que les clients de l’adaptateur peuvent appeler. Ces opérations sont décrites plus loin dans cette rubrique.  
  
 Vous pouvez utiliser les clients de la carte pour parcourir, rechercher et récupérer des métadonnées par :  
  
-   Création d’un projet BizTalk dans Visual Studio  
  
-   À l’aide du modèle de canal WCF  
  
-   À l’aide du modèle de service WCF  
  
 Lorsque vous utilisez un projet BizTalk, vous devez utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des métadonnées pour les opérations que vous souhaitez effectuer dans Oracle E-Business Suite. Lorsque vous utilisez le modèle de service WCF, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer les classes proxy pour effectuer des opérations dans Oracle E-Business Suite. Pour plus d’informations sur la navigation, la recherche et la récupération de métadonnées à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [obtenir les métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
## <a name="browsing-metadata"></a>Exploration des métadonnées  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] permet aux clients d’adaptateur parcourir les tables d’interface, les vues de l’interface, les programmes simultanés et de requête définit dans Oracle E-Business Suite et des tables, des vues, des procédures stockées, des fonctions et des packages dans la base de données sous-jacente. Dans le cadre de l’opération de parcourir des métadonnées, l’adaptateur met également en évidence les opérations qui peuvent être effectuées sur la base de données Oracle, notamment certaines opérations personnalisées prises en charge par les adaptateurs. Ces opérations sont disponibles à partir de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] met en évidence la plupart des opérations sous les trois nœuds suivants :  
  
1.  **Vue application**: contient les opérations regroupées par chaque application pour les artefacts d’Oracle E-Business Suite.  
  
2.  **Vue basée sur un artefact**: contient les opérations regroupées par type d’artefact (par exemple, les Tables d’Interface, les vues de l’Interface, etc.) dans Oracle E-Business Suite et de la base de données sous-jacente.  
  
3.  **Vue schéma**: contient les opérations regroupées par chaque schéma pour les artefacts de base de données sous-jacente.  
  
 Certaines opérations sont spécifiques génériques exposées au niveau racine qui sont applicables pour les deux nœuds. En outre, les différentes opérations sont signalées en fonction du type d’opération : entrant ou sortant.  
  
 Le tableau suivant répertorie les opérations entrantes et sortantes exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:  
  
|Opérations sortantes|Opérations entrantes|  
|-------------------------|------------------------|  
|**Vue application**:<br /><br /> Contient une liste d’Applications Oracle dans Oracle E-Business Suite sous-jacent. Développez un nœud de l’Application Oracle pour voir les artefacts suivants :<br /><br /> <ul><li>**Tables de l’interface**: une liste de toutes les tables d’interface. Sélectionnez une table d’interface pour afficher l’insertion, de sélectionner, de mise à jour et les opérations de suppression.</li><li>**Vues de l’interface**: une liste de toutes les vues de l’interface. Sélectionnez une interface pour afficher l’opération Select.</li><li>**Programmes simultanés**: les opérations suivantes pour les programmes simultanés :<br /><br /> <ul><li>Un ensemble de tous les simultanées programmes spécifiques à l’Application Oracle qui sont exposées en tant qu’opérations.</li><li>L’opération Get_Status pour obtenir l’état d’un programme simultané.</li><li>L’opération Wait_For_Request à attendre une demande soit terminé avant le renvoi d’état.</li><li>L’opération Submit_Request pour appeler ou exécuter un programme simultané en spécifiant les paramètres requis pour l’exécution du programme simultanée.</li></ul></li><li>**Requête définit**: un ensemble de tous les la demande définit spécifique à l’Application Oracle qui sont exposées en tant qu’opérations.</li></ul>|**Vue application**:<br /><br /> Contient une liste d’Applications Oracle dans Oracle E-Business Suite sous-jacent. Développez un nœud de l’Application Oracle pour voir les artefacts suivants :<br /><br /> -   **Tables de l’interface**: opération de l’interrogation pour les tables d’interface qui permet aux clients d’adaptateur obtenir les données entrantes à partir d’Oracle E-Business Suite basée sur un mécanisme d’interrogation de requête pris en charge par l’adaptateur.<br />-   **Vues de l’interface**: opération de l’interrogation pour les vues de l’interface qui permet aux clients d’adaptateur obtenir les données entrantes à partir d’Oracle E-Business Suite basée sur un mécanisme d’interrogation de requête pris en charge par l’adaptateur.|  
|**Vue basée sur un artefact**:<br /><br /> Contient tous les artefacts dans Oracle E-Business Suite et de la base de données sous-jacente. Développez un nœud d’artefact pour afficher une liste d’Applications Oracle ou des schémas en fonction de l’origine de l’artefact (base de données ou des applications). Par exemple, le **Tables d’Interface** nœud affiche une liste d’Applications Oracle tandis que le **Tables** nœud affiche une liste de schémas de base de données.<br /><br /> Le **vue basée sur un artefact** affiche les artefacts répertoriés sous **vue basée sur les Applications** et **basée sur un schéma de vue**. Chaque nœud d’artefact répertorie les opérations appropriées pour une Application Oracle ou d’un schéma de base de données.|**Vue basée sur un artefact**:<br /><br /> À l’exception des programmes simultanés et ensembles de requêtes, contient tous les artefacts dans Oracle E-Business Suite et tous les artefacts dans la base de données sous-jacente. Développez un nœud d’artefact pour afficher une liste d’Applications Oracle ou des schémas en fonction de l’origine de l’artefact (base de données ou des applications). Par exemple, le **Tables d’Interface** nœud affiche une liste d’Applications Oracle tandis que le **Tables** nœud affiche une liste de schémas de base de données.<br /><br /> Le **vue basée sur un artefact** affiche les artefacts répertoriés sous **vue basée sur les Applications** et **basée sur un schéma de vue**. Chaque nœud d’artefact répertorie les opérations appropriées pour une Application Oracle ou d’un schéma de base de données.|  
|**Vue schéma**:<br /><br /> Contient une liste de schémas dans la base de données Oracle. Développez le nœud de schéma pour voir les artefacts suivants :<br /><br /> -   **Les API PL/SQL**: une liste de toutes les API PL/SQL. Sélectionnez une API PL/SQL pour afficher les procédures empaquetées et les fonctions qui sont exposées en tant qu’opérations.<br />-   **Procédures**: une liste des procédures dans le schéma qui sont exposées en tant qu’opérations.<br />-   **Fonctions**: une liste de fonctions dans le schéma qui sont exposées en tant qu’opérations.<br />-   **Tables**: une liste de toutes les tables. Sélectionnez une table pour afficher l’insertion, de sélectionner, de mise à jour et les opérations de suppression.<br />-   **Vues**: une liste de toutes les vues. Sélectionnez une vue pour afficher l’opération Select.|**Vue schéma**:<br /><br /> Contient une liste de schémas dans la base de données Oracle. Développez le nœud de schéma pour voir les artefacts suivants :<br /><br /> -   **Les API PL/SQL**: une liste de toutes les API PL/SQL. Sélectionnez une API PL/SQL pour afficher les procédures empaquetées et les fonctions qui sont exposées en tant qu’opérations pour l’interrogation.<br />-   **Procédures**: une liste des procédures dans le schéma qui sont exposées en tant qu’opérations pour l’interrogation.<br />-   **Fonctions**: une liste de fonctions dans le schéma qui sont exposées en tant qu’opérations pour l’interrogation.<br />-   **Tables**: une liste de toutes les tables. Sélectionnez une table pour afficher l’opération d’interrogation pour la table.<br />-   **Vues**: une liste de toutes les vues. Sélectionnez une vue pour afficher l’opération d’interrogation de la vue.|  
|Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose également les opérations sortantes génériques suivantes au niveau racine : ExecuteReader, ExecuteScalar et ExecuteNonQuery. Pour plus d’informations sur ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).|Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose également l’opération de Notification au niveau racine qui permet aux clients d’adaptateur recevoir des messages de notification de modification de base de données à partir d’Oracle E-Business Suite. Pour plus d’informations sur l’opération de notification, consultez [considérations relatives à la réception des Notifications de modification de base de données](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).|  
  
 Pour plus d’informations sur la façon dont les métadonnées sont catégorisée, consultez [Parcourir, rechercher et récupérer des métadonnées pour des opérations Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
## <a name="searching-metadata"></a>Recherche de métadonnées  
 À l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous pouvez effectuer une requête de recherche dans Oracle E-Business Suite et sur la base de données Oracle sous-jacente à l’aide d’Oracle rechercher les expressions qui sont compatibles avec l’opérateur LIKE. Par exemple, les clients de l’adaptateur peuvent utiliser une expression de recherche telles que « EMP % » pour obtenir des tables commençant par EMP. L’adaptateur convertit en la requête SQL suivante :  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%' AND OWNER = 'SCOTT'  
```  
  
 WHERE, SCOTT est le schéma avec une collection d’objets de base de données Oracle.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|_ (souligné)|Correspond à exactement un caractère<br /><br /> Par exemple, A_ correspond à AB, CA et Active Directory.|  
|% (pourcentage)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, un % correspond à un, AB, ABC.|  
|\ (échappement)|Remplace une signification spéciale % et _. Le \ (échappement) caractère est utilisé avant un caractère générique pour indiquer que le caractère générique doit être interprété comme un caractère normal.<br /><br /> Par exemple, un\\_B correspond à A_B.|  
  
> [!IMPORTANT]
>  -   La chaîne de recherche respecte la casse.  
> -   La recherche fonctionne différemment sous l’autre vue (vue basée sur l’Application, vue basée sur un artefact et vue basée sur le schéma). Pour savoir comment vous pouvez rechercher des artefacts et opérations sous chaque vue, consultez « Recherche sous différentes vues » dans [recherche pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md).  
> -   Pour rechercher une application, vous pouvez spécifier le nom convivial ou le nom court de l’application. Par exemple, pour rechercher la **des comptes clients** application, vous pouvez spécifier la chaîne de recherche en tant que **réception %** ou **AR**. AR est le nom court de l’application.  
> -   Pour rechercher un programme simultané, vous pouvez spécifier le nom convivial ou le nom réel du programme simultané. Par exemple, pour rechercher la **Interface client** programme simultané, vous pouvez spécifier la chaîne de recherche en tant que **Interface client %** ou **RACUST %**. RACUST est le nom réel du programme simultané. En outre, le résultat de recherche contient toujours les programmes simultanés standards indépendamment de si leur nom correspondant à la chaîne de recherche spécifié.  
  
## <a name="retrieving-metadata"></a>La récupération des métadonnées  
 Lors de la récupération des métadonnées, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] peut extraire des métadonnées dans un schéma, y compris l’ensemble ou un sous-ensemble de la base de données des objets avec les paramètres respectifs de l’objet et l’opération. L’adaptateur présente les entités à partir d’Oracle E-Business Suite et de la base de données Oracle en tant que noms d’éléments XML. Étant donné que des traits de soulignement sont les seuls caractères spéciaux qui peuvent être inclus, tous les autres caractères spéciaux dans les noms d’élément sont encodés à l’aide des traits de soulignement. Par exemple, `emp$name` est encodé comme `emp_x0024_name`. Pour plus d’informations, consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)   
 [Parcourir, rechercher et de récupérer les métadonnées pour des opérations Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)   
 [Obtenir les métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)