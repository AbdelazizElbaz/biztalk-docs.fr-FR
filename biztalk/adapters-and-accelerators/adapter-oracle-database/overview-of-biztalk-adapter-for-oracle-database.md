---
title: "Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter, overview
- ODP.NET
- Oracle Data Provider for .NET 2.0
ms.assetid: 852b8f82-ab34-45b8-ad7f-263d719a87f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b874b5523256342a4e8ae14b2c475ede11fe279
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-biztalk-adapter-for-oracle-database"></a>Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose la base de données Oracle en tant qu’un service WCF. Les clients de carte peuvent effectuer des opérations sur la base de données Oracle en échangeant des messages SOAP avec l’adaptateur. L’adaptateur utilise le message WCF et effectue des appels ODP.NET appropriés pour effectuer l’opération. L’adaptateur renvoie la réponse à partir de la base de données Oracle au client sous la forme des messages SOAP.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] des métadonnées de surfaces d’artefacts de base de données Oracle (tables, fonctions, procédures, etc.) qui décrivent la structure d’un protocole SOAP du message sous la forme de WSDL. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], et [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour permettre aux clients d’adaptateur récupérer des métadonnées pour les opérations et génère des artefacts de programmation qui peuvent être utilisés dans votre solution de programmation.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise le fournisseur de données Oracle pour .NET (ODP.NET) pour communiquer avec la base de données Oracle. Vous pouvez utiliser la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour communiquer avec la base de données Oracle comme suit :  
  
-   En développant des applications BizTalk. Consultez [développer vos applications BizTalk](../../core/develop-your-biztalk-applications.md) pour plus d’informations.  
  
-   À l’aide de la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service. Consultez [applications développer la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md) pour plus d’informations.  
  
-   À l’aide du modèle de canal WCF. Consultez [applications développer la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) pour plus d’informations.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment l’adaptateur effectue la connexion à une base de données Oracle ?](https://msdn.microsoft.com/library/cc185360(v=bts.10).aspx)  
  
-   [Quels sont les métadonnées de la surface d’exposition Oracle adaptateur ?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)  
  
-   [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)  
  
-   [Quels sont les Transactions de gérer de carte ?](https://msdn.microsoft.com/library/dd788428.aspx)  
  
-   [Prise en charge de diffusion en continu pour les Types de données LOB dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)  
  
-   [Les opérations sont prises en charge par l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/what-operations-are-supported-by-the-oracle-database-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’adaptateur Biztalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)