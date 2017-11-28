---
title: "À l’aide de la Transformation dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1e4aac7-242a-41b6-8df4-4881371f44d1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d7f6bc57d009e558188950d9bcb0387f808f835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-dynamic-transformation"></a><span data-ttu-id="f1518-102">À l’aide de la Transformation dynamique</span><span class="sxs-lookup"><span data-stu-id="f1518-102">Using Dynamic Transformation</span></span>
## <a name="overview"></a><span data-ttu-id="f1518-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="f1518-103">Overview</span></span>  
 <span data-ttu-id="f1518-104">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge trois mécanismes pour la transformation dynamique :</span><span class="sxs-lookup"><span data-stu-id="f1518-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports three mechanisms for dynamic transformation:</span></span>  
  
-   <span data-ttu-id="f1518-105">Un agent de transformation dynamique implémenté en tant qu’orchestration</span><span class="sxs-lookup"><span data-stu-id="f1518-105">A dynamic transformation agent implemented as an orchestration</span></span>  
  
-   <span data-ttu-id="f1518-106">Une transformation dynamique de service Web incluse avec les services Web principaux</span><span class="sxs-lookup"><span data-stu-id="f1518-106">A dynamic transformation Web service included with the core Web services</span></span>  
  
-   <span data-ttu-id="f1518-107">Transformations exécutées par les composants de pipeline ESB</span><span class="sxs-lookup"><span data-stu-id="f1518-107">Transformations executed by ESB pipeline components</span></span>  
  
 <span data-ttu-id="f1518-108">Cette section se concentre sur l’agent de transformation implémenté en tant qu’orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1518-108">This section focuses on the transformation agent implemented as an orchestration.</span></span> <span data-ttu-id="f1518-109">Pour plus d’informations sur la transformation de service Web, consultez [à l’aide des Services Web BizTalk ESB Toolkit](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="f1518-109">For information about the transformation Web service, see [Using the BizTalk ESB Toolkit Web Services](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md).</span></span> <span data-ttu-id="f1518-110">Pour plus d’informations sur les composants de pipeline ESB répartiteur, consultez [à l’aide de composants de prise en charge du Pipeline](../esb-toolkit/using-the-pipeline-support-components.md).</span><span class="sxs-lookup"><span data-stu-id="f1518-110">For information about the ESB Dispatcher pipeline components, see [Using the Pipeline Support Components](../esb-toolkit/using-the-pipeline-support-components.md).</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="f1518-111">Fonctionnement</span><span class="sxs-lookup"><span data-stu-id="f1518-111">How It Works</span></span>  
 <span data-ttu-id="f1518-112">L’agent de remise de transformation est une orchestration qui s’abonne aux messages où le **nom** attribut actuelles **ServiceInstance** élément dans l’itinéraire est  **Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="f1518-112">The transformation delivery agent is an orchestration that subscribes to messages where the **Name** attribute of the current **ServiceInstance** element in the itinerary is **Microsoft.Practices.ESB.Services.Transform**.</span></span> <span data-ttu-id="f1518-113">L’agent exécute la séquence d’opérations suivante :</span><span class="sxs-lookup"><span data-stu-id="f1518-113">The agent performs the following sequence of operations:</span></span>  
  
1.  <span data-ttu-id="f1518-114">Il reçoit un message non typé (System.Xml.XmlDocument).</span><span class="sxs-lookup"><span data-stu-id="f1518-114">It receives an un-typed message (System.Xml.XmlDocument).</span></span>  
  
2.  <span data-ttu-id="f1518-115">Si le nom de la carte est disponible en tant qu’une valeur statique dans l’itinéraire, l’agent tente de résoudre le nom de la carte à l’aide du Gestionnaire de programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="f1518-115">If the name of the map is available as a static value in the itinerary, the agent attempts to resolve the name of the map using the resolver manager.</span></span>  
  
3.  <span data-ttu-id="f1518-116">Il applique le mappage approprié au message entrant source.</span><span class="sxs-lookup"><span data-stu-id="f1518-116">It applies the appropriate map to the inbound source message.</span></span>  
  
4.  <span data-ttu-id="f1518-117">Elle publie la sortie de la table dans la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f1518-117">It publishes the map output to the BizTalk Message Box database.</span></span>  
  
## <a name="how-to-configure-dynamic-transformation"></a><span data-ttu-id="f1518-118">Comment configurer la Transformation dynamique</span><span class="sxs-lookup"><span data-stu-id="f1518-118">How to Configure Dynamic Transformation</span></span>  
 <span data-ttu-id="f1518-119">Pour plus d’informations sur la façon de configurer la Transformation dynamique à l’aide du Concepteur d’itinéraire, consultez [création d’itinéraires à l’aide du Concepteur de feuille de route](../esb-toolkit/creating-itineraries-using-itinerary-designer.md).</span><span class="sxs-lookup"><span data-stu-id="f1518-119">For more information about how to configure Dynamic Transformation using Itinerary Designer, see [Creating Itineraries Using Itinerary Designer](../esb-toolkit/creating-itineraries-using-itinerary-designer.md).</span></span>  
  
## <a name="dynamic-transformation-errors"></a><span data-ttu-id="f1518-120">Erreurs de Transformation dynamique</span><span class="sxs-lookup"><span data-stu-id="f1518-120">Dynamic Transformation Errors</span></span>  
 <span data-ttu-id="f1518-121">Le mécanisme de transformation dynamique sera créer et publier un message d’erreur ESB dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="f1518-121">The dynamic transformation mechanism will create and publish an ESB fault message in the following cases:</span></span>  
  
-   <span data-ttu-id="f1518-122">Le composant de programme de résolution ne peut pas déterminer qui est mappé à appliquer.</span><span class="sxs-lookup"><span data-stu-id="f1518-122">The resolver component cannot determine which map to apply.</span></span>  
  
-   <span data-ttu-id="f1518-123">Le mappage spécifié n’est pas disponible (par exemple, vous spécifié un type de carte incorrect ou une carte pas encore déployé dans BizTalk Server 2009).</span><span class="sxs-lookup"><span data-stu-id="f1518-123">The specified map is not available (for example, you specified an incorrect map type or a map not yet deployed in BizTalk Server 2009).</span></span>  
  
-   <span data-ttu-id="f1518-124">Une défaillance se produit lors du mappage (par exemple, le document source n’est pas du type source correcte ou les références de carte une fonction personnalisée dans un assembly externe n’est pas déployée sur BizTalk).</span><span class="sxs-lookup"><span data-stu-id="f1518-124">A failure occurs during mapping (for example, the source document is not of the correct source type or the map references a custom function in an external assembly is not deployed to BizTalk).</span></span>  
  
-   <span data-ttu-id="f1518-125">Une exception se produit pendant la résolution juste-à-temps (JIT) du type de carte.</span><span class="sxs-lookup"><span data-stu-id="f1518-125">An exception occurs during just-in-time (JIT) resolution of the map type.</span></span>  
  
-   <span data-ttu-id="f1518-126">Aucun abonné n’existe pour le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="f1518-126">No subscriber exists for the output message.</span></span>  
  
-   <span data-ttu-id="f1518-127">Toute exception système se produit.</span><span class="sxs-lookup"><span data-stu-id="f1518-127">Any system exception occurs.</span></span>  
  
 <span data-ttu-id="f1518-128">Il incombe au développeur de fournir les informations de contexte utilisées pour remplir les messages d’exception et de créer des gestionnaires pour réagir à l’exception.</span><span class="sxs-lookup"><span data-stu-id="f1518-128">It is the developer's responsibility to provide the context information used to populate the exception messages and create handlers to react to the exception.</span></span> <span data-ttu-id="f1518-129">Certaines des données est automatiquement disponible, et un gestionnaire générique prennent en charge le message d’exception si aucun gestionnaire de cible n’est spécifié ou disponible.</span><span class="sxs-lookup"><span data-stu-id="f1518-129">Some of the data is automatically available, and a generic handler will pick up the exception message if no target handler is specified or available.</span></span> <span data-ttu-id="f1518-130">Pour plus d’informations sur la gestion des exceptions de transformation dynamique, consultez [à l’aide de gestion des exceptions ESB](../esb-toolkit/using-esb-exception-management.md).</span><span class="sxs-lookup"><span data-stu-id="f1518-130">For more information about handling dynamic transformation exceptions, see [Using ESB Exception Management](../esb-toolkit/using-esb-exception-management.md).</span></span>