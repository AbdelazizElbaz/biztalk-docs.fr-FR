---
title: "Obtenir les métadonnées par programme à partir de SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IMetadataRetrievalContract endpoint
- metadata, retrieving programmatically
- WS-Metadata Exchange (MEX) endpoint
ms.assetid: 8d75332e-c103-4bd5-a9a2-56d21747a04e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c856b3629d7d7dcd3f9aa5431c0406f6c822e54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-programmatically-from-sap"></a>Obtenir les métadonnées par programme à partir de SAP
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] est une liaison WCF personnalisée qui expose un système SAP comme un service WCF. L’adaptateur expose le système SAP en tant qu’autodescriptif service ; Autrement dit, un service qui est capable de publication des métadonnées sur les opérations qu’il prend en charge. Les métadonnées décrivent l’interface logique à un service WCF ; Autrement dit, le contrat de service, les messages et les schémas de message qui doivent être utilisés pour interagir avec le service.  
  
 Ces métadonnées sont utilisées par des outils tels que :  
  
-   Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer des représentations sous forme de code managé du contrat de service, et  
  
-   Le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des schémas de message.  
  
 Toutefois, vous pouvez récupérer également de métadonnées par programme à partir de l’adaptateur. Par exemple, vous pouvez souhaiter procéder ainsi pour créer un outil de récupération de métadonnées personnalisées à utiliser dans une application existante.  
  
 L’adaptateur publie les métadonnées via deux points de terminaison :  
  
-   Un point de terminaison WS-MEX (Metadata Exchange). WCF fournit automatiquement un point de terminaison MEX pour toutes les liaisons WCF. Vous pouvez utiliser l’échange de métadonnées à récupérer des métadonnées pour les opérations prises en charge par l’adaptateur sur le système SAP sous-jacent.  
  
-   Un **IMetadataRetrievalContract** point de terminaison. Le **IMetadataRetrievalContract** interface est implémentée par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]. Il classe les artefacts du système SAP à plusieurs niveaux logiques et les présente sous la forme d’une arborescence de nœuds de métadonnées. Vous pouvez utiliser les méthodes exposées par le **IMetadataRetrievalContract** interface pour parcourir et rechercher les nœuds de cette arborescence et pour retourner des métadonnées pour les opérations qui vous intéressent.  
  
 Les rubriques de cette section décrivent comment utiliser MEX et **IMetadataRetrievalContract** points de terminaison pour récupérer des métadonnées par programme à partir de l’adaptateur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [La récupération de métadonnées à l’aide de WS-Metadata Exchange dans SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-using-ws-metadata-exchange-in-sap.md)  
  
-   [La récupération des métadonnées dans SAP à l’aide de IMetadataRetrievalContract](../../adapters-and-accelerators/adapter-sap/get-metadata-in-sap-using-imetadataretrievalcontract.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SAP](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)