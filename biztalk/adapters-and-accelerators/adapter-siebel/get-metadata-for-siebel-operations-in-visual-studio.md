---
title: "Obtenir les métadonnées pour les opérations Siebel dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata, retrieving for Siebel operations in Visual Studio
ms.assetid: 63643942-6497-4891-ad7d-34b1df9acbc1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30935631052adf4c455e730c476104b54a6a352b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-siebel-operations-in-visual-studio"></a><span data-ttu-id="200c4-102">Obtenir les métadonnées pour les opérations Siebel dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="200c4-102">Get Metadata for Siebel Operations in Visual Studio</span></span>
<span data-ttu-id="200c4-103">Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] fournit deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="200c4-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] provides two [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter.</span></span>  
  
-   <span data-ttu-id="200c4-104">Le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] est disponible dans les projets BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="200c4-104">The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] is available in BizTalk Server projects.</span></span> <span data-ttu-id="200c4-105">Vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="200c4-105">You use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate message schemas (XSDs) for operations that you want to target in your BizTalk solution.</span></span> <span data-ttu-id="200c4-106">Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [BizTalk de développer les applications à l’aide de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="200c4-106">For more information about developing solutions with BizTalk Server, see [Develop BizTalk applications using the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).</span></span>
  
-   <span data-ttu-id="200c4-107">Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] est disponible dans les projets de programmation non-BizTalk.</span><span class="sxs-lookup"><span data-stu-id="200c4-107">The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] is available in non-BizTalk programming projects.</span></span> <span data-ttu-id="200c4-108">Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="200c4-108">You use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client class or a WCF service callback interface when you develop solutions using the WCF service model.</span></span> <span data-ttu-id="200c4-109">Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [Siebel de développer les applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="200c4-109">For more information about developing solutions with the WCF service model, see [Develop Siebel applications using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="200c4-110">Ces deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :</span><span class="sxs-lookup"><span data-stu-id="200c4-110">Both of these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
-   <span data-ttu-id="200c4-111">En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="200c4-111">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
-   <span data-ttu-id="200c4-112">La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="200c4-112">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
-   <span data-ttu-id="200c4-113">Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.</span><span class="sxs-lookup"><span data-stu-id="200c4-113">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
 <span data-ttu-id="200c4-114">Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="200c4-114">This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="200c4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="200c4-115">See Also</span></span>  
[<span data-ttu-id="200c4-116">Développer vos applications Siebel</span><span class="sxs-lookup"><span data-stu-id="200c4-116">Develop your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)