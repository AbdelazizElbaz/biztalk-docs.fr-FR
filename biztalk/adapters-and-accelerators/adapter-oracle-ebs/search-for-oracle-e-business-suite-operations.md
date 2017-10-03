---
title: "Recherchez des opérations Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2970ddd4-a534-4da4-9bd5-28bb9da4deca
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 797f89b5032d6bcfdb1a4d16f5a83d53d01f1c7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="search-for-oracle-e-business-suite-operations"></a>Rechercher des opérations Oracle E-Business Suite
Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour rechercher les artefacts dans Oracle E-Business Suite. Cette rubrique fournit des informations sur la façon dont la recherche est prise en charge des vues différentes, et ce qu’il caractères génériques peuvent être utilisés pour la recherche d’artefacts d’Oracle. Cette rubrique fournit également des informations sur la recherche à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  


  
> [!NOTE]
>  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des deux composants sont traités dans les rubriques mêmes.  
  
 Pour plus d’informations, consultez [utiliser l’adaptateur Oracle E-Business Suite avec SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez vous connecter à Oracle E-Business Suite avant que vous pouvez rechercher des métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à Oracle de base de données lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
## <a name="support-for-wildcard-characters"></a>Prise en charge des caractères génériques  
 Lors de la recherche de métadonnées d’Oracle E-Business Suite à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge des caractères génériques et d’échappement dans l’expression de recherche.  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|_ (souligné)|Correspond à exactement un caractère<br /><br /> Par exemple, A_ correspond à AB, CA, Active Directory.|  
|% (pourcentage)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, un % correspond à un, AB, ABC.|  
|\ (échappement)|Remplace une signification spéciale % et _<br /><br /> Par exemple, un\\_B correspond à A_B.|  
  
> [!NOTE]
>  Caractère d’échappement est un caractère qui est placé avant un caractère générique pour indiquer que le caractère générique doit être interprété comme un caractère normal et non comme un caractère générique.  
  
## <a name="searching-under-different-views"></a>Recherche dans des vues différentes  
 Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] classe les données dans trois vues : vue basée sur l’application, vue basée sur un artefact et vue basée sur le schéma. Une des raisons pour classer les artefacts sous ces trois affichages est de faciliter la recherche en fonction de ce que vous recherchez. Le tableau suivant décrit comment la recherche peut différer entre ces vues.  
  
|Affichage|Comment effectuer une recherche|  
|----------|-------------------|  
|**Vue basée sur l’application**|Cette vue est classée par les noms d’applications Oracle E-Business Suite. Vous devez utiliser cette vue lorsque vous savez quelle application contienne les artefacts que vous souhaitez utiliser.<br /><br /> Les utilisateurs à l’aide de cette vue seront être familiarisés avec les applications Oracle et sont prenant en charge les application qu’ils souhaitent utiliser. Par conséquent, la recherche sous cette vue est pris en charge uniquement au niveau de l’exécution. Par exemple, si le **vue basée sur l’Application** nœud est sélectionné, les utilisateurs peuvent rechercher une application dans Oracle E-Business Suite. De même, si le **Table d’Interface** nœud est sélectionné, les utilisateurs peuvent rechercher une table d’interface dans une application Oracle E-Business.|  
|**Vue basée sur un artefact**|Cette vue est classée par les artefacts d’Oracle E-Business Suite. Lorsque vous travaillez avec des artefacts de l’application Oracle E-Business Suite, les utilisateurs doivent utiliser cette vue lorsqu’ils connaissent les artefacts d’Oracle E-Business Suite à utiliser, mais ne savez pas quelle application l’artefact appartient à.<br /><br /> À l’aide de cette vue, les utilisateurs peuvent rechercher un artefact spécifique pour toutes les applications d’Oracle E-Business Suite. Par exemple, les utilisateurs peuvent sélectionner le **Tables d’Interface** nœud et recherche à l’aide de la chaîne `AR%`. Il s’agit de la recherche sera effectuée :<br /><br /> -Étant donné que les tables d’interface sont également dans des sous-catégories sous applications, toutes les applications démarrent avec AR apparaît.<br />-Toutes les tables d’interface en commençant par AR seront afficheront. Ces tables peuvent appartenir à n’importe quelle application de la suite Oracle E-Business.<br /><br /> Lorsque vous travaillez avec des artefacts de base de données Oracle à l’aide de cette vue, les utilisateurs peuvent rechercher un artefact spécifique soit sous le schéma actuel avec lequel vous êtes connecté ou tous les schémas. Par exemple, si les utilisateurs souhaitent utiliser une procédure CREATE_ACCOUNT, mais qui ne reconnaissent pas le schéma appartient la procédure, ils peuvent sélectionner le **tous les schémas** nœud et à l’aide de la chaîne de recherche puis `CREATE%`.|  
|**Vue schéma**|Cette vue est classée par les schémas disponibles dans la base de données Oracle. Vous devez utiliser cette vue lorsque vous savez quel schéma a les artefacts que vous souhaitez utiliser.<br /><br /> Les utilisateurs à l’aide de cette vue sera facile avec le schéma qui possède l’artefact qu'ils souhaitent utiliser. Par conséquent, la recherche sous cette vue est pris en charge uniquement au niveau de l’exécution. Par exemple, si le **basée sur un schéma de vue** nœud est sélectionné, les utilisateurs peuvent rechercher un schéma dans la base de données Oracle. De même, si le **Table** nœud est sélectionné, les utilisateurs peuvent rechercher une table dans une application Oracle E-Business.|  
  
## <a name="searching-for-operations"></a>Recherche d’opérations  
 Pour rechercher des métadonnées dans Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], procédez comme suit.  
  
#### <a name="to-search-metadata-in-oracle-e-business-suite"></a>Pour rechercher des métadonnées dans Oracle E-Business Suite  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** , sélectionnez le type de contrat selon si vous recherchez des opérations entrantes et sortantes.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le nœud de catégorie sous lequel vous souhaitez rechercher un objet spécifique. Par exemple, pour rechercher une application Oracle, cliquez sur le **vue basée sur l’Application** nœud.  
  
    > [!NOTE]
    >  Pour rechercher une application, vous pouvez spécifier le nom convivial ou le nom court de l’application. Par exemple, pour rechercher la **des comptes clients** application, vous pouvez spécifier la chaîne de recherche en tant que `Receive%` ou `AR`. AR est le nom court de l’application.  
  
4.  Dans le **recherche dans la catégorie** , tapez une expression de recherche pour rechercher un objet spécifique. Par exemple, pour rechercher des applications Oracle ayant « Client » dans leur nom, tapez `%Customer%`.  
  
    > [!NOTE]
    >  La chaîne de recherche respecte la casse.  
  
5.  Pour démarrer la recherche, cliquez sur le bouton avec l’icône de flèche droite. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les artefacts qui répondent aux critères de recherche.  
  
     La figure suivante illustre les tables d’applications Oracle qui contiennent « Client » dans leur nom.  
  
     ![Rechercher des métadonnées dans Oracle E &#45; Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/e6278992-a475-4a35-8371-db862f25a720.gif "e6278992-a475-4a35-8371-db862f25a720")  
  
    > [!NOTE]
    >  Pour rechercher un programme simultané, vous pouvez spécifier le nom convivial ou le nom réel du programme simultané. Par exemple, pour rechercher la **Interface client** programme simultané, vous pouvez spécifier la chaîne de recherche en tant que `%Customer Interface%` ou `%RACUST%`. RACUST est le nom réel du programme simultané.  
    >   
    >  En outre, le résultat de recherche contient toujours les programmes simultanés standards indépendamment de si leur nom correspondant à la chaîne de recherche spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)