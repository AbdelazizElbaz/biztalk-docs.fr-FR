---
title: "Obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7ac720-e573-4564-8d15-8212a815f1f7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec993dd308abf0f364eb73f6f35d48d618d6807e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter"></a><span data-ttu-id="5293b-102">Obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="5293b-102">Get metadata for SQL Server operations in Visual Studio using the SQL adapter</span></span>
<span data-ttu-id="5293b-103">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] fournit trois [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] les composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur, le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5293b-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] provides three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter—the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="5293b-104">Les clients de l’adaptateur doivent utiliser ces composants pour se connecter à SQL Server et générer ensuite des métadonnées pour les opérations à effectuer.</span><span class="sxs-lookup"><span data-stu-id="5293b-104">Adapter clients must use these components to connect to SQL Server and then generate metadata for the operations they want to perform.</span></span>  
  
 <span data-ttu-id="5293b-105">Tous ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :</span><span class="sxs-lookup"><span data-stu-id="5293b-105">All these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
-   <span data-ttu-id="5293b-106">En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="5293b-106">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
-   <span data-ttu-id="5293b-107">La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="5293b-107">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
-   <span data-ttu-id="5293b-108">Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.</span><span class="sxs-lookup"><span data-stu-id="5293b-108">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
 <span data-ttu-id="5293b-109">Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5293b-109">This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
