---
title: "À l’aide de l’infrastructure de gestion d’Exception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b69c9c01-e7e4-4788-8fe2-43d32075155d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47442604831a3a11bb9d00b65f9dc34961de2367
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-exception-management-framework"></a><span data-ttu-id="905dc-102">À l’aide de l’infrastructure de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="905dc-102">Using the Exception Management Framework</span></span>
<span data-ttu-id="905dc-103">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise des exceptions pour communiquer des erreurs (par exemple, une carte non déployée ou les règles qui ne retournent pas un nom de mappage) pour les transformations dynamiques et le routage.</span><span class="sxs-lookup"><span data-stu-id="905dc-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses exceptions to communicate failures (for example, a non-deployed map or rules that do not return a map name) for dynamic transformations and routing.</span></span> <span data-ttu-id="905dc-104">En cas d’échec d’une transformation ou un processus de routage, l’architecture ESB crée un message d’exception et la soumet via un port de liaison directe à la base de données de la boîte de Message.</span><span class="sxs-lookup"><span data-stu-id="905dc-104">When a transformation or routing process fails, the ESB creates an exception message and submits it through a direct-bound port to the Message Box database.</span></span> <span data-ttu-id="905dc-105">L’architecture ESB implémente également un port d’envoi nommé tous. Exceptions qui s’abonne à et récupère les messages d’exception et les publie dans le portail de gestion ESB.</span><span class="sxs-lookup"><span data-stu-id="905dc-105">The ESB also implements a send port named ALL.Exceptions that subscribes to and retrieves exception messages and publishes them to the ESB Management Portal.</span></span>  
  
 <span data-ttu-id="905dc-106">En outre, tous les exemples d’orchestration utilisent l’Orchestration d’échec ESB API de routage Exception pour la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="905dc-106">In addition, all orchestration samples use the ESB Failed Orchestration Exception Routing API to handle exceptions.</span></span> <span data-ttu-id="905dc-107">Vous pouvez utiliser cette API dans n’importe quel projet d’orchestration que vous déployez.</span><span class="sxs-lookup"><span data-stu-id="905dc-107">You can use this API in any orchestration project you deploy.</span></span> <span data-ttu-id="905dc-108">La fonctionnalité d’ESB Échec de l’Orchestration Exception routage fournit un moyen standard pour intercepter et signaler toutes les exceptions dans un environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="905dc-108">The ESB Failed Orchestration Exception Routing feature provides a standard way to trap and report all exceptions in a BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="905dc-109">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient plusieurs projets d’exemples qui montrent comment utiliser l’infrastructure de gestion d’Exception ESB.</span><span class="sxs-lookup"><span data-stu-id="905dc-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains several sample projects that demonstrate how to use the ESB Exception Management Framework.</span></span> <span data-ttu-id="905dc-110">Les deux projets suivants encapsulent l’ESB Échec de l’Orchestration routage API de l’Exception :</span><span class="sxs-lookup"><span data-stu-id="905dc-110">The following two projects encapsulate the ESB Failed Orchestration Exception Routing API:</span></span>  
  
-   <span data-ttu-id="905dc-111">**ESB. ExceptionHandling**.</span><span class="sxs-lookup"><span data-stu-id="905dc-111">**ESB.ExceptionHandling**.</span></span> <span data-ttu-id="905dc-112">Ce projet contient toutes les méthodes publiques pour gérer le traitement de message d’erreur dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="905dc-112">This project contains all the public methods for handling fault message processing in orchestrations.</span></span> <span data-ttu-id="905dc-113">Vous devez inscrire l’assembly de ce projet dans le global assembly cache sur le serveur local.</span><span class="sxs-lookup"><span data-stu-id="905dc-113">You must register the assembly in this project in the global assembly cache on the local server.</span></span>  
  
-   <span data-ttu-id="905dc-114">**ESB. ExceptionHandling.Schemas.Faults**.</span><span class="sxs-lookup"><span data-stu-id="905dc-114">**ESB.ExceptionHandling.Schemas.Faults**.</span></span> <span data-ttu-id="905dc-115">Ce projet contient le schéma de message d’erreur défini par l’espace de noms **http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling** et le schéma de propriété système.</span><span class="sxs-lookup"><span data-stu-id="905dc-115">This project contains the fault message schema defined by the namespace **http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling** and the system property schema.</span></span> <span data-ttu-id="905dc-116">Vous devez déployer ce projet sur le conteneur d’application Microsoft.Practices.ESB.</span><span class="sxs-lookup"><span data-stu-id="905dc-116">You must deploy this project to the Microsoft.Practices.ESB application container.</span></span>  
  
 <span data-ttu-id="905dc-117">Tous les projets qui utilisent l’Orchestration d’échec ESB API de routage Exception doivent référencer les assemblys principaux :</span><span class="sxs-lookup"><span data-stu-id="905dc-117">All projects that use the ESB Failed Orchestration Exception Routing API must reference the core assemblies:</span></span>  
  
-   <span data-ttu-id="905dc-118">**Microsoft.Practices.ESB.ExceptionHandling.dll**</span><span class="sxs-lookup"><span data-stu-id="905dc-118">**Microsoft.Practices.ESB.ExceptionHandling.dll**</span></span>  
  
-   <span data-ttu-id="905dc-119">**Microsoft.Practices.ESB.ExceptionHandling.Schemas.Faults.dll**</span><span class="sxs-lookup"><span data-stu-id="905dc-119">**Microsoft.Practices.ESB.ExceptionHandling.Schemas.Faults.dll**</span></span>  
  
 <span data-ttu-id="905dc-120">Les sections suivantes fournissent plus d’informations sur l’utilisation de l’infrastructure de gestion d’Exception ESB :</span><span class="sxs-lookup"><span data-stu-id="905dc-120">The following sections provide more information about using the ESB Exception Management Framework:</span></span>  
  
-   [<span data-ttu-id="905dc-121">Les membres de l’Exception API ESB</span><span class="sxs-lookup"><span data-stu-id="905dc-121">The ESB Exception API Members</span></span>](../esb-toolkit/the-esb-exception-api-members.md)  
  
-   [<span data-ttu-id="905dc-122">Création et la publication des Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="905dc-122">Creating and Publishing Fault Messages</span></span>](../esb-toolkit/creating-and-publishing-fault-messages.md)  
  
-   [<span data-ttu-id="905dc-123">S’abonner à et l’extraction des Messages</span><span class="sxs-lookup"><span data-stu-id="905dc-123">Subscribing to and Extracting Messages</span></span>](../esb-toolkit/subscribing-to-and-extracting-messages.md)  
  
-   [<span data-ttu-id="905dc-124">Étapes Solution du scénario</span><span class="sxs-lookup"><span data-stu-id="905dc-124">Scenario Solution Steps</span></span>](../esb-toolkit/scenario-solution-steps.md)