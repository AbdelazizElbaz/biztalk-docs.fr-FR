---
title: "Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overview, adapter
- adapter, overview of
- adapter, overview
ms.assetid: 41ab7d42-7096-45ef-9763-a5ccf88eb652
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efcc3a90f7025a5f396cd778676f5f3152bc7657
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="53d3d-102">Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="53d3d-102">Overview of BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="53d3d-103">Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose le système Siebel comme service WCF.</span><span class="sxs-lookup"><span data-stu-id="53d3d-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes the Siebel system as a WCF service.</span></span> <span data-ttu-id="53d3d-104">Les clients de carte peuvent effectuer des opérations sur le système Siebel en échangeant des messages SOAP avec l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="53d3d-104">Adapter clients can perform operations on the Siebel system by exchanging SOAP messages with the adapter.</span></span> <span data-ttu-id="53d3d-105">L’adaptateur utilise le message WCF et appelle approprié au système Siebel pour effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="53d3d-105">The adapter consumes the WCF message and makes appropriate calls to the Siebel system to perform the operation.</span></span> <span data-ttu-id="53d3d-106">L’adaptateur renvoie la réponse à partir du système Siebel au client sous la forme des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="53d3d-106">The adapter returns the response from the Siebel system back to the client in the form of SOAP messages.</span></span>  
  
 <span data-ttu-id="53d3d-107">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] des métadonnées de surfaces d’artefacts Siebel (composants d’entreprise, services d’entreprise) qui décrivent la structure d’un protocole SOAP du message sous la forme de WSDL.</span><span class="sxs-lookup"><span data-stu-id="53d3d-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces metadata of Siebel artifacts (business components, business services) that describes the structure of a SOAP message in the form of WSDL.</span></span> <span data-ttu-id="53d3d-108">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour permettre aux clients d’adaptateur récupérer des métadonnées pour les opérations et génère des artefacts de programmation qui peuvent être utilisés dans votre solution de programmation.</span><span class="sxs-lookup"><span data-stu-id="53d3d-108">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution.</span></span>  
  
 <span data-ttu-id="53d3d-109">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise le contrôle de données Siebel COM d’accéder au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="53d3d-109">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses the Siebel COM Data Control to access the Siebel system.</span></span> <span data-ttu-id="53d3d-110">Le contrôle de données Siebel COM est fourni avec le client Siebel Web.</span><span class="sxs-lookup"><span data-stu-id="53d3d-110">The Siebel COM Data Control comes bundled with the Siebel Web client.</span></span> <span data-ttu-id="53d3d-111">Par conséquent, assurez-vous que le client Siebel Web est installé sur le même ordinateur que le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53d3d-111">Hence, make sure you have the Siebel Web client installed on the same computer as the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="53d3d-112">Vous pouvez utiliser la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour communiquer avec le système Siebel comme suit :</span><span class="sxs-lookup"><span data-stu-id="53d3d-112">You can use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to communicate with the Siebel system in the following ways:</span></span>  
  
-   <span data-ttu-id="53d3d-113">En développant des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="53d3d-113">By developing BizTalk applications.</span></span> <span data-ttu-id="53d3d-114">Consultez [développement d’Applications de BizTalk Server](../../core/developing-biztalk-server-applications.md).</span><span class="sxs-lookup"><span data-stu-id="53d3d-114">See [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md).</span></span>
  
-   <span data-ttu-id="53d3d-115">À l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="53d3d-115">By using the WCF service model.</span></span> <span data-ttu-id="53d3d-116">Consultez [développer des Applications Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="53d3d-116">See [Develop Siebel Applications by Using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="53d3d-117">À l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="53d3d-117">By using the WCF channel model.</span></span> <span data-ttu-id="53d3d-118">Reportez-vous à développer des Applications de base de données Oracle à l’aide du modèle de canal WCF[Entrez la description du lien ici](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).</span><span class="sxs-lookup"><span data-stu-id="53d3d-118">See Develop Oracle Database Applications by Using the WCF Channel Model[enter link description here](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53d3d-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="53d3d-119">In This Section</span></span>  
  
-   <span data-ttu-id="53d3d-120">[Comment l’adaptateur effectue la connexion à un système Siebel ?](https://msdn.microsoft.com/library/cc185212(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="53d3d-120">[How Does the Adapter Connect to a Siebel System?](https://msdn.microsoft.com/library/cc185212(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="53d3d-121">[Quels sont les métadonnées Siebel aire de conception d’adaptateur ?](https://msdn.microsoft.com/library/cc185267(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="53d3d-121">[How Does the Adapter Surface Siebel Metadata?](https://msdn.microsoft.com/library/cc185267(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="53d3d-122">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="53d3d-122">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="53d3d-123">[Autres fonctionnalités prises en charge par l’adaptateur](https://msdn.microsoft.com/library/cc185252(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="53d3d-123">[Other Features Supported by the Adapter](https://msdn.microsoft.com/library/cc185252(v=bts.10).aspx)</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="53d3d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53d3d-124">See Also</span></span>  
 [<span data-ttu-id="53d3d-125">Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="53d3d-125">Understand BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)