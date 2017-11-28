---
title: "Obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata, retrieving in Visual Studio
- metadata
ms.assetid: d903b408-1144-4625-909d-710826e37769
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fdf1d1943c471591e35f1efb6ca6e08f36948fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-oracle-database-operations-in-visual-studio"></a><span data-ttu-id="8ab70-102">Obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8ab70-102">Get metadata for Oracle Database operations in Visual Studio</span></span>
<span data-ttu-id="8ab70-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] fournit trois [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8ab70-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] provides three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter.</span></span>  
  
-   <span data-ttu-id="8ab70-104">Le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] et [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] sont disponibles dans les projets BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8ab70-104">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] and the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] are available in BizTalk Server projects.</span></span> <span data-ttu-id="8ab70-105">Vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8ab70-105">You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution.</span></span> <span data-ttu-id="8ab70-106">Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [BizTalk de développer les applications à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="8ab70-106">For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)</span></span>  
  
-   <span data-ttu-id="8ab70-107">Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] est disponible dans les projets de programmation non-BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8ab70-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] is available in non-BizTalk programming projects.</span></span> <span data-ttu-id="8ab70-108">Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="8ab70-108">You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model.</span></span> <span data-ttu-id="8ab70-109">Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [développer les Applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="8ab70-109">For more information about developing solutions with the WCF service model, see [Develop Oracle Database Applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="8ab70-110">Ces trois [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :</span><span class="sxs-lookup"><span data-stu-id="8ab70-110">All these three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
-   <span data-ttu-id="8ab70-111">En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="8ab70-111">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
-   <span data-ttu-id="8ab70-112">La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="8ab70-112">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
-   <span data-ttu-id="8ab70-113">Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.</span><span class="sxs-lookup"><span data-stu-id="8ab70-113">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
 <span data-ttu-id="8ab70-114">Cette section fournit des instructions sur l’utilisation de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ab70-114">This section provides instructions about how to use [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ab70-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8ab70-115">In This Section</span></span>  
  
-   [<span data-ttu-id="8ab70-116">Se connecter à la base de données Oracle dans Visual Studio à l’aide de Consume Adapter Service</span><span class="sxs-lookup"><span data-stu-id="8ab70-116">Connect to the Oracle Database in Visual Studio using the Consume Adapter Service</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md) 
  
-   [<span data-ttu-id="8ab70-117">Parcourir, rechercher et obtenir des métadonnées pour les opérations de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="8ab70-117">Browse, search, and get metadata for Oracle Database operations</span></span>](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ab70-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ab70-118">See Also</span></span>  
[<span data-ttu-id="8ab70-119">Développer vos applications de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="8ab70-119">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)