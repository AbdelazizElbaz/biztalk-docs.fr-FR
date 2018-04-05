---
title: Obtenir les métadonnées pour les opérations de SAP dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving for SAP operations in Visual Studio
ms.assetid: 1be5934a-a5d4-4734-8bea-fb8274f59c71
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c786ea9b1acbc3ed88c79187725697ce279ea5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-sap-operations-in-visual-studio"></a><span data-ttu-id="f2d15-102">Obtenir les métadonnées pour les opérations de SAP dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f2d15-102">Get Metadata for SAP Operations in Visual Studio</span></span>
<span data-ttu-id="f2d15-103">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] fournit deux [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] les composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur, le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2d15-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] provides two [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter—the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="f2d15-104">Les clients de l’adaptateur doivent utiliser ces composants pour se connecter à un système SAP et générer ensuite les métadonnées pour les artefacts SAP qu’ils veulent appeler.</span><span class="sxs-lookup"><span data-stu-id="f2d15-104">Adapter clients must use these components to connect to an SAP system and then generate metadata for the SAP artifacts they want to invoke.</span></span>  
  
 <span data-ttu-id="f2d15-105">Tous ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :</span><span class="sxs-lookup"><span data-stu-id="f2d15-105">All these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
-   <span data-ttu-id="f2d15-106">En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="f2d15-106">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
-   <span data-ttu-id="f2d15-107">La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="f2d15-107">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
-   <span data-ttu-id="f2d15-108">Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.</span><span class="sxs-lookup"><span data-stu-id="f2d15-108">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
 <span data-ttu-id="f2d15-109">Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2d15-109">This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="f2d15-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2d15-110">See Also</span></span>  
[<span data-ttu-id="f2d15-111">Développer vos applications SAP</span><span class="sxs-lookup"><span data-stu-id="f2d15-111">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)