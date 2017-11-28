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
# <a name="overview-of-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="fc4a8-102">Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="fc4a8-102">Overview of BizTalk Adapter for Oracle Database</span></span>
<span data-ttu-id="fc4a8-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose la base de données Oracle en tant qu’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes the Oracle database as a WCF service.</span></span> <span data-ttu-id="fc4a8-104">Les clients de carte peuvent effectuer des opérations sur la base de données Oracle en échangeant des messages SOAP avec l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-104">Adapter clients can perform operations on the Oracle database by exchanging SOAP messages with the adapter.</span></span> <span data-ttu-id="fc4a8-105">L’adaptateur utilise le message WCF et effectue des appels ODP.NET appropriés pour effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-105">The adapter consumes the WCF message and makes appropriate ODP.NET calls to perform the operation.</span></span> <span data-ttu-id="fc4a8-106">L’adaptateur renvoie la réponse à partir de la base de données Oracle au client sous la forme des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-106">The adapter returns the response from the Oracle database back to the client in the form of SOAP messages.</span></span>  
  
 <span data-ttu-id="fc4a8-107">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] des métadonnées de surfaces d’artefacts de base de données Oracle (tables, fonctions, procédures, etc.) qui décrivent la structure d’un protocole SOAP du message sous la forme de WSDL.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-107">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces metadata of Oracle database artifacts (tables, functions, procedures, etc.) that describes the structure of a SOAP message in the form of WSDL.</span></span> <span data-ttu-id="fc4a8-108">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], et [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour permettre aux clients d’adaptateur récupérer des métadonnées pour les opérations et génère des artefacts de programmation qui peuvent être utilisés dans votre solution de programmation.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-108">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], and [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution.</span></span>  
  
 <span data-ttu-id="fc4a8-109">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise le fournisseur de données Oracle pour .NET (ODP.NET) pour communiquer avec la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-109">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the Oracle Data Provider for .NET (ODP.NET) to communicate with the Oracle database.</span></span> <span data-ttu-id="fc4a8-110">Vous pouvez utiliser la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour communiquer avec la base de données Oracle comme suit :</span><span class="sxs-lookup"><span data-stu-id="fc4a8-110">You can use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to communicate with the Oracle database in the following ways:</span></span>  
  
-   <span data-ttu-id="fc4a8-111">En développant des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-111">By developing BizTalk applications.</span></span> <span data-ttu-id="fc4a8-112">Consultez [développer vos applications BizTalk](../../core/develop-your-biztalk-applications.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-112">See [Develop your BizTalk applications](../../core/develop-your-biztalk-applications.md) for more information.</span></span>  
  
-   <span data-ttu-id="fc4a8-113">À l’aide de la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-113">By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model.</span></span> <span data-ttu-id="fc4a8-114">Consultez [applications développer la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-114">See [Develop Oracle Database applications using the WCF Service model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md) for more information.</span></span>  
  
-   <span data-ttu-id="fc4a8-115">À l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-115">By using the WCF channel model.</span></span> <span data-ttu-id="fc4a8-116">Consultez [applications développer la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="fc4a8-116">See [Develop Oracle Database applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md) for more information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc4a8-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fc4a8-117">In This Section</span></span>  
  
-   <span data-ttu-id="fc4a8-118">[Comment l’adaptateur effectue la connexion à une base de données Oracle ?](https://msdn.microsoft.com/library/cc185360(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="fc4a8-118">[How Does the Adapter Connect to an Oracle Database?](https://msdn.microsoft.com/library/cc185360(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="fc4a8-119">[Quels sont les métadonnées de la surface d’exposition Oracle adaptateur ?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="fc4a8-119">[How Does the Adapter Surface Oracle Metadata?](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="fc4a8-120">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="fc4a8-120">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)</span></span>  
  
-   [<span data-ttu-id="fc4a8-121">Quels sont les Transactions de gérer de carte ?</span><span class="sxs-lookup"><span data-stu-id="fc4a8-121">How does the Adapter Handle Transactions?</span></span>](https://msdn.microsoft.com/library/dd788428.aspx)  
  
-   [<span data-ttu-id="fc4a8-122">Prise en charge de diffusion en continu pour les Types de données LOB dans une base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="fc4a8-122">Streaming Support for LOB Data Types in Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)  
  
-   [<span data-ttu-id="fc4a8-123">Les opérations sont prises en charge par l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="fc4a8-123">What operations are supported by the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/what-operations-are-supported-by-the-oracle-database-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="fc4a8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc4a8-124">See Also</span></span>  
 [<span data-ttu-id="fc4a8-125">Présentation de l’adaptateur Biztalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="fc4a8-125">Understanding the Biztalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)