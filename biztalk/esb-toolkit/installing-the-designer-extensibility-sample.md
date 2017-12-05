---
title: "Installation de l’exemple de l’extensibilité du Concepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eba13a4a-1b87-4268-af91-29af3a5bc5ef
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea0cd71c22fdd614d2e49c996939b785ecadf8bd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-the-designer-extensibility-sample"></a><span data-ttu-id="3b61e-102">Installation de l’exemple de l’extensibilité du Concepteur</span><span class="sxs-lookup"><span data-stu-id="3b61e-102">Installing the Designer Extensibility Sample</span></span>
<span data-ttu-id="3b61e-103">Cette section décrit le processus d’installation de l’exemple de l’extensibilité du concepteur.</span><span class="sxs-lookup"><span data-stu-id="3b61e-103">This section describes the process for installing the Designer Extensibility sample.</span></span> <span data-ttu-id="3b61e-104">Vous devez installer les exemples de [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) et [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) avant d’installer et utiliser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="3b61e-104">You must install the samples in [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) and [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) before you install and use this sample.</span></span>  
  
 <span data-ttu-id="3b61e-105">**Pour installer l’exemple de l’extensibilité du Concepteur**</span><span class="sxs-lookup"><span data-stu-id="3b61e-105">**To install the Designer Extensibility sample**</span></span>  
  
1.  <span data-ttu-id="3b61e-106">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample, où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et ouvrez le fichier de solution Microsoft Visual Studio nommé Extenders.Itinerary.OrchestrationSample.sln.</span><span class="sxs-lookup"><span data-stu-id="3b61e-106">In Windows Explorer, open the folder \Source\Samples\Designer Extensibility Samples\Extenders.Itinerary.OrchestrationSample, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Microsoft Visual Studio solution file named Extenders.Itinerary.OrchestrationSample.sln.</span></span>  
  
2.  <span data-ttu-id="3b61e-107">Dans Visual Studio, cliquez sur **générer la Solution** sur la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="3b61e-107">In Visual Studio, click **Build Solution** on the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="3b61e-108">Fermez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b61e-108">Close Visual Studio.</span></span>  
  
4.  <span data-ttu-id="3b61e-109">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample, où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et ouvrez le fichier de solution Visual Studio nommé Extenders.Resolvers.ResolverSample.sln.</span><span class="sxs-lookup"><span data-stu-id="3b61e-109">In Windows Explorer, open the folder \Source\Samples\Designer Extensibility Samples\Extenders.Resolvers.ResolverSample, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Visual Studio solution file named Extenders.Resolvers.ResolverSample.sln.</span></span>  
  
5.  <span data-ttu-id="3b61e-110">Dans Visual Studio, cliquez sur **générer la Solution** sur la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="3b61e-110">In Visual Studio, click **Build Solution** on the **Build** menu.</span></span>  
  
6.  <span data-ttu-id="3b61e-111">Fermez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b61e-111">Close Visual Studio.</span></span>  
  
7.  <span data-ttu-id="3b61e-112">Dans l’Explorateur Windows, ouvrez le dossier \Lib sous le chemin d’installation de concepteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="3b61e-112">In Windows Explorer, open the \Lib folder under the Itinerary Designer install path.</span></span>  
  
8.  <span data-ttu-id="3b61e-113">Parmi les dossiers \bin\Debug des solutions Visual Studio créées à l’étape précédente, copiez les fichiers Extenders.Resolvers.ResolverSample.dll et Extenders.Itinerary.OrchestrationSample.dll dans le répertoire \Lib.</span><span class="sxs-lookup"><span data-stu-id="3b61e-113">From the \bin\Debug folders of the Visual Studio solutions built in the preceding steps, copy the files Extenders.Resolvers.ResolverSample.dll and Extenders.Itinerary.OrchestrationSample.dll to the \Lib directory.</span></span>