---
title: "Obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d7f731-cd0f-4970-a3cd-072f09312989
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97ef4cc308979718f306958d0da1bb1eceaebaf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-oracle-e-business-suite-operations-in-visual-studio"></a><span data-ttu-id="1e6db-102">Obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1e6db-102">Get metadata for Oracle E-Business Suite operations in Visual Studio</span></span>
<span data-ttu-id="1e6db-103">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] fournit trois [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants que vous pouvez utiliser pour vous aider à développer des solutions à l’aide de l’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="1e6db-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] provides three [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components that you can use to help you develop solutions using the adapter:</span></span>  
  
-   [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]  
  
-   [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]  
  
 <span data-ttu-id="1e6db-104">Clients de l’adaptateur doivent utiliser ces composants pour se connecter à Oracle E-Business Suite, puis générer des métadonnées pour les opérations à effectuer.</span><span class="sxs-lookup"><span data-stu-id="1e6db-104">Adapter clients must use these components to connect to Oracle E-Business Suite, and then generate metadata for the operations they want to perform.</span></span> <span data-ttu-id="1e6db-105">Tous ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants simplifient le développement par :</span><span class="sxs-lookup"><span data-stu-id="1e6db-105">All these [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] components simplify development by:</span></span>  
  
-   <span data-ttu-id="1e6db-106">En fournissant une interface de Microsoft Windows par le biais duquel vous pouvez parcourir et rechercher pour les opérations que vous souhaitez utiliser dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="1e6db-106">Providing a Microsoft Windows interface through which you can browse and search for operations that you want to use in your solution.</span></span>  
  
-   <span data-ttu-id="1e6db-107">La récupération des métadonnées exposées par l’adaptateur pour ces opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="1e6db-107">Retrieving metadata exposed by the adapter for these target operations.</span></span>  
  
-   <span data-ttu-id="1e6db-108">Conversion de ces métadonnées, exprimé sous forme d’un document Web Services Description Language (WSDL) par l’adaptateur, dans un formulaire que vous pouvez utiliser dans votre solution (schémas de message XSD pour les projets BizTalk ou d’une représentation d’objet .NET d’un contrat de service WCF modèle de service) et son ajout à votre projet.</span><span class="sxs-lookup"><span data-stu-id="1e6db-108">Converting that metadata, which is expressed as a Web Services Description Language (WSDL) document by the adapter, into a form that you can use in your solution (XSD message schemas for BizTalk projects or a .NET object representation of a service contract for the WCF service model) and adding it to your project.</span></span>  
  
 <span data-ttu-id="1e6db-109">Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e6db-109">This section provides instructions about how to use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e6db-110">Si vous avez créé une solution à l’aide de l’adaptateur sur une version particulière d’Oracle E-Business Suite et que vous souhaitez maintenant déployer la solution sur une autre version d’Oracle E-Business Suite vous devez tester la solution avant de le déployer.</span><span class="sxs-lookup"><span data-stu-id="1e6db-110">If you have created a solution using the adapter on a particular version of Oracle E-Business Suite, and now want to deploy the solution on a different version of Oracle E-Business Suite then you should test the solution before deploying it.</span></span> <span data-ttu-id="1e6db-111">Vous risquez de rencontrer des problèmes lors du déploiement de la solution sur une autre version d’Oracle E-Business Suite, car les métadonnées de l’objet sous-jacent peuvent être différente.</span><span class="sxs-lookup"><span data-stu-id="1e6db-111">You might face issues while deploying the solution on a different version of Oracle E-Business Suite because the metadata of the underlying artifact might be different.</span></span> <span data-ttu-id="1e6db-112">Pour résoudre ce problème, vous devez régénérer les métadonnées à l’aide de la carte sur la même version d’Oracle E-Business Suite sur lequel vous prévoyez de déployer la solution.</span><span class="sxs-lookup"><span data-stu-id="1e6db-112">To resolve this issue, you should regenerate the metadata using the adapter on the same version of Oracle E-Business Suite on which you intend to deploy the solution.</span></span>  
  
