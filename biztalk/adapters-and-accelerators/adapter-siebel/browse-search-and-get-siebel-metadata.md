---
title: Parcourir, rechercher et obtenir des métadonnées Siebel | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving
- metadata, surfacing
- retrieving, metadata
- metadata, browsing
- browsing, metadata
- metadata, searching
- searching, metadata
ms.assetid: 48fc3bb1-b949-4b8d-ab62-a41cd8c2f0a0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef1ed7d74b4e69f56c53beda8273533bb6891a55
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="browse-search-and-get-siebel-metadata"></a>Parcourir, rechercher et obtenir des métadonnées Siebel
Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces des métadonnées à partir du système Siebel qui décrit la structure du message pour la communication avec un système Siebel à l’aide de l’adaptateur. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge deux interfaces de récupération des métadonnées.  
  
-   MetadataExchange fournie par [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF fournit un point de terminaison d’échange de métadonnées pour toutes les liaisons WCF, ce qui permet aux clients d’obtenir les métadonnées à partir du système Siebel.  
  
-   IMetadataRetrievalContract fournie par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], qui prend en charge les métadonnées de parcourir et rechercher des fonctions de l’adaptateur.  
  
 L’objectif de la [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] consiste à exposer le système Siebel comme service WCF. L’adaptateur met en évidence des artefacts Siebel (des objets métier et les services) en tant qu’opérations que les clients de l’adaptateur peuvent appeler.  
  
 Les clients de l’adaptateur peuvent parcourir, rechercher et récupérer des métadonnées à l’aide du modèle de service WCF, à l’aide du modèle de canal WCF ou en créant un BizTalk de projet dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Lorsque vous utilisez le modèle de service WCF, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer les classes proxy pour effectuer des opérations sur le système Siebel. Lorsque vous utilisez un projet BizTalk, vous devez utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées pour les opérations que vous souhaitez exécuter sur le système Siebel. Pour plus d’informations sur la navigation, la recherche et la récupération de métadonnées à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
## <a name="browsing-metadata"></a>Exploration des métadonnées  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] permet aux clients d’adaptateur parcourir les objets métier et les services professionnels exposées par le système Siebel. Dans le cadre de l’opération de parcourir des métadonnées, l’adaptateur catégorise les artefacts dans plusieurs niveaux logiques et expose une vue hiérarchique des métadonnées pour les clients de la carte. Les métadonnées à partir d’un système Siebel sont classée sous les nœuds suivants :  
  
-   **Objets métier**. Ce nœud contient les objets métier dans un système Siebel, qui est une collection logique de composants d’entreprise. Les objets métier sont plus considérés comme des composants d’entreprise. Le niveau le plus bas de la hiérarchie sont les opérations que vous pouvez appeler sur les composants d’entreprise.  
  
-   **Services professionnels**. Ce nœud contient les services d’entreprise exposées par un système Siebel. Un service d’entreprise Siebel est une collection de méthodes de service d’entreprise ou des fonctions qui peuvent être appelées directement dans le système Siebel.  
  
 Pour plus d’informations sur la façon dont les métadonnées sont catégorisée, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).  
  
## <a name="searching-metadata"></a>Recherche de métadonnées  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] permet aux clients d’adaptateur rechercher des métadonnées dans un système Siebel. Pour cela, à l’aide de Siebel valide des expressions de recherche compatible avec Siebel de LIKE (opérateur) sur le champ [nom] du composant d’entreprise de référentiel Siebel utilisé pour parcourir les métadonnées. Le tableau suivant répertorie les artefacts Siebel et la hiérarchie de métadonnées sous lequel ils peuvent rechercher.  
  
|Artefact|Recherches sous le nœud dans l’interface utilisateur graphique|  
|--------------|----------------------------------------|  
|Objet métier|/ Objets métier|  
|Composant d’entreprise|/ Nom de l’objet métier objets/entreprise|  
|Service d’entreprise|/ Services professionnels|  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
|Caractère spécial|Interpretation|  
|-----------------------|--------------------|  
|? (point d’interrogation)|Correspond à exactement un caractère.<br /><br /> Par exemple, un ? correspond à AB, CA, Active Directory|  
|* (astérisque)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, A * correspond à un, AB, ABC.|  
  
## <a name="retrieving-metadata"></a>Récupération de métadonnées  
 Lors de la récupération des métadonnées, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut extraire des métadonnées dans un schéma, y compris tout ou un sous-ensemble d’objets métier ou des services d’entreprise avec les paramètres de l’opération. Elle présente les entités à partir du système Siebel en tant que noms d’éléments XML. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] permet aux clients d’adaptateur récupérer des métadonnées pour le système Siebel, y compris les caractéristiques des métadonnées détaillées :  
  
-   Pour les composants de l’entreprise, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] récupère des éléments, tels que le nom d’objet métier, nom de composant d’entreprise, noms de champs, types de données, les longueurs de champ, champ obligatoire, ce champ est facultatif et champ de liste de choix. L’adaptateur récupère également les opérations possibles sur le composant de gestion telles que INSERT, UPDATE, DELETE et requête.  
  
-   Pour les méthodes de service d’entreprise, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] récupère des éléments, tels que le nom du service, le nom de la méthode (identique à l’opération), les paramètres de méthode et les types de données de paramètre.  
  
 Pour plus d’informations sur la récupération des métadonnées, consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)