---
title: Obtenir les métadonnées par programme à partir de la base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving programmatically from the Oracle database
ms.assetid: 28a55935-6078-41d0-abfa-ac86e9ca8471
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c36fcd6a791f1d960a4dd4dfd78ca199d2e49cb5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-programmatically-from-the-oracle-database"></a>Obtenir les métadonnées par programme à partir de la base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] est une liaison WCF personnalisée qui expose une base de données Oracle en tant qu’un service WCF. L’adaptateur expose la base de données Oracle en tant qu’autodescriptif service ; Autrement dit, un service qui est capable de publication des métadonnées sur les opérations qu’il prend en charge. Les métadonnées décrivent l’interface logique à un service WCF ; Autrement dit, le contrat de service, les messages et les schémas de message qui doivent être utilisés pour interagir avec le service.  
  
 Ces métadonnées sont utilisées par des outils tels que :  
  
-   Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer des représentations sous forme de code managé du contrat de service, et  
  
-   Le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des schémas de message.  
  
 Toutefois, vous pouvez récupérer également de métadonnées par programme à partir de l’adaptateur. Par exemple, vous pouvez souhaiter procéder ainsi pour créer un outil de récupération de métadonnées personnalisées à utiliser dans une application existante.  
  
 L’adaptateur publie les métadonnées via deux points de terminaison :  
  
-   Un point de terminaison WS-MEX (Metadata Exchange). WCF fournit automatiquement un point de terminaison MEX pour toutes les liaisons WCF. Vous pouvez utiliser l’échange de métadonnées à récupérer des métadonnées pour les opérations prises en charge par l’adaptateur sur la base de données Oracle.  
  
-   Un **IMetadataRetrievalContract** point de terminaison. Le **IMetadataRetrievalContract** interface est implémentée par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]. Il classe les artefacts de base de données Oracle à plusieurs niveaux logiques et les présente sous la forme d’une arborescence de nœuds de métadonnées. Vous pouvez utiliser les méthodes exposées par le **IMetadataRetrievalContract** interface pour parcourir et rechercher les nœuds de cette arborescence et pour retourner des métadonnées pour les opérations qui vous intéressent.  
  
 Les rubriques de cette section décrivent comment utiliser MEX et **IMetadataRetrievalContract** points de terminaison pour récupérer des métadonnées par programme à partir de l’adaptateur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Obtenir les métadonnées à l’aide de WS-Metadata Exchange dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-using-ws-metadata-exchange-in-oracle-database.md)  
  
-   [Obtient les métadonnées de la base de données Oracle à l’aide de IMetadataRetrievalContract](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-in-oracle-database-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)