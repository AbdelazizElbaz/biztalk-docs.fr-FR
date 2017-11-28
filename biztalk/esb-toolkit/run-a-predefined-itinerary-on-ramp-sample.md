---
title: "Exécuter un exemple de rampe d’entrée d’itinéraire prédéfini | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4400193-20ac-479a-8bf9-b1c99eb35231
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 167d18f0eba624d62b03b3b0a5386fcac04e5b18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-a-predefined-itinerary-on-ramp-sample"></a><span data-ttu-id="1ac2a-102">Exécuter un exemple de rampe d’entrée d’itinéraire prédéfini</span><span class="sxs-lookup"><span data-stu-id="1ac2a-102">Run a Predefined Itinerary On-Ramp Sample</span></span>
<span data-ttu-id="1ac2a-103">La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut 20 cas d’usage itinéraire prédéfinis que vous pouvez exécuter.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes 20 predefined Itinerary use cases you can execute.</span></span> <span data-ttu-id="1ac2a-104">Pour obtenir la liste de ces cas d’usage, consultez [les exemples de scénarios de feuille de route](../esb-toolkit/the-sample-itinerary-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="1ac2a-104">For a list of these use cases, see [The Sample Itinerary Scenarios](../esb-toolkit/the-sample-itinerary-scenarios.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ac2a-105">Avant d’exécuter les exemples, vous devez importer manuellement le fichier de liaison d’itinéraire correspondant à partir du dossier \Source\Samples\Itinerary\Install\Binding dans l’application BizTalk de GlobalBank.ESB.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-105">Before you run any of the samples, you must manually import the appropriate itinerary binding file from the \Source\Samples\Itinerary\Install\Binding folder into the GlobalBank.ESB BizTalk application.</span></span> <span data-ttu-id="1ac2a-106">Ce fichier de liaison réinitialise les propriétés sur les deux ports d’envoi dynamique.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-106">This binding file resets the properties on the two dynamic send ports.</span></span> <span data-ttu-id="1ac2a-107">Importez le fichier de liaison nommé GlobalBank.ESB.Itinerary_Bindings.xml.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-107">Import the binding file named GlobalBank.ESB.Itinerary_Bindings.xml.</span></span>  
  
### <a name="to-run-one-of-the-pre-defined-itinerary-on-ramp-samples"></a><span data-ttu-id="1ac2a-108">Pour exécuter un des exemples de feuille de route rampe d’entrée prédéfinis</span><span class="sxs-lookup"><span data-stu-id="1ac2a-108">To run one of the pre-defined Itinerary On-Ramp samples</span></span>  
  
1.  <span data-ttu-id="1ac2a-109">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-109">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="1ac2a-110">Dans l’Explorateur Windows, ouvrez le sous-dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test\bin\Debug où votre installé les exemples de BizTalk ESB Toolkit, puis démarrez l’application nommée Esb.Itinerary.Test.exe.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-110">In Windows Explorer, open the subfolder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test\bin\Debug where you installed the BizTalk ESB Toolkit samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="1ac2a-111">Cliquez sur le **LoadItinerary** , puis sur l’itinéraire d’exemple nommé TwoWay (bidirectionnel)-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml à partir du dossier \Source\Samples\Itinerary\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-111">Click the **LoadItinerary** button, and then select the sample itinerary named TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml from the \Source\Samples\Itinerary\Itineraries folder.</span></span>  
  
4.  <span data-ttu-id="1ac2a-112">Dans le **Options du Service Web** section, sélectionnez le **bidirectionnel Service** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-112">In the **Web Service Options** section, select the **Two-Way Service** check box.</span></span> <span data-ttu-id="1ac2a-113">Cela fait en sorte que le client de test pour effectuer une opération de service d’itinéraire de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-113">This instructs the test client to perform a request-response itinerary service operation.</span></span>  
  
5.  <span data-ttu-id="1ac2a-114">(Facultatif) Sélectionnez le **utiliser un Service WCF** case à cocher si vous souhaitez que l’application pour utiliser le OnRamp.Itinerary.Response.WCF l’emplacement de réception au lieu de la valeur par défaut OnRamp.Itinerary.Response.SOAP emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-114">(Optional) Select the **Use WCF Service** check box if you want the application to use the OnRamp.Itinerary.Response.WCF receive location instead of the default OnRamp.Itinerary.Response.SOAP receive location.</span></span>  
  
6.  <span data-ttu-id="1ac2a-115">Cliquez sur le **LoadMessage** , puis l’exemple de message NAOrderDoc.xml à partir du dossier \Source\Samples\Itinerary\Test\Data.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-115">Click the **LoadMessage** button, and then select the NAOrderDoc.xml sample message from the \Source\Samples\Itinerary\Test\Data folder.</span></span>  
  
7.  <span data-ttu-id="1ac2a-116">Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-116">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span> <span data-ttu-id="1ac2a-117">La figure 1 illustre le résultat.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-117">Figure 1 shows the result.</span></span>  
  
 <span data-ttu-id="1ac2a-118">![Itinéraire sur rampe](../esb-toolkit/media/ch6-itineraryonramp.gif "§ 6-ItineraryOnRamp")</span><span class="sxs-lookup"><span data-stu-id="1ac2a-118">![Itinerary On Ramp](../esb-toolkit/media/ch6-itineraryonramp.gif "Ch6-ItineraryOnRamp")</span></span>  
  
 <span data-ttu-id="1ac2a-119">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="1ac2a-119">**Figure 1**</span></span>  
  
 <span data-ttu-id="1ac2a-120">**L’application cliente de feuille de route rampe d’entrée en cours d’exécution un des exemples de la feuille de route rampe d’entrée**</span><span class="sxs-lookup"><span data-stu-id="1ac2a-120">**The Itinerary On-Ramp client application running one of the Itinerary On-Ramp samples**</span></span>  
  
 <span data-ttu-id="1ac2a-121">Le nom du service spécifié dans la définition d’itinéraire correspond directement à la **ServiceName** propriété du service à laquelle s’abonne l’exemple.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-121">The name of the service specified in the itinerary definition corresponds directly to the **ServiceName** property of the service to which the sample subscribes.</span></span> <span data-ttu-id="1ac2a-122">Dans l’exemple d’itinéraire exécutée dans la procédure précédente (TwoWay (bidirectionnel)-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml), le premier service exécuté est un service d’orchestration qui effectue une transformation.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-122">In the itinerary sample executed in the previous procedure (TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml), the first service executed is an orchestration-based service that performs a transformation.</span></span> <span data-ttu-id="1ac2a-123">La section suivante de l’itinéraire spécifie ce service.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-123">The following section of the itinerary specifies this service.</span></span>  
  
```  
<Service uuid="" beginTime="" completeTime=""   
    name="Microsoft.Practices.ESB.Services.Transform"  
    type="Orchestration" state="Pending" isRequestResponse="false"  
    position="0" serviceInstanceId="" />  
```  
  
 <span data-ttu-id="1ac2a-124">Le service d’orchestration dans ce  **\<Service >** élément spécifie l’orchestration à liaison directe qui a les propriétés de filtre indiquées dans la Figure 2.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-124">The orchestration service in this **\<Service>** element specifies the direct-bound orchestration that has the filter properties shown in Figure 2.</span></span> <span data-ttu-id="1ac2a-125">Notez que l’orchestration s’abonne uniquement aux messages qui ont la valeur **Microsoft.Practices.ESB.Services.Transform** pour le **ServiceName** propriété de contexte, la valeur  **En attente** pour le **ServiceState** propriété de contexte et la valeur d’Orchestration pour les **ServiceType** propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="1ac2a-125">Notice that the orchestration subscribes only to messages that have the value **Microsoft.Practices.ESB.Services.Transform** for the **ServiceName** context property, the value **Pending** for the **ServiceState** context property, and the value Orchestration for the **ServiceType** context property.</span></span>  
  
 <span data-ttu-id="1ac2a-126">![Expression de filtre](../esb-toolkit/media/ch6-filterexpression.gif "§ 6-FilterExpression")</span><span class="sxs-lookup"><span data-stu-id="1ac2a-126">![Filter Expression](../esb-toolkit/media/ch6-filterexpression.gif "Ch6-FilterExpression")</span></span>  
  
 <span data-ttu-id="1ac2a-127">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="1ac2a-127">**Figure 2**</span></span>  
  
 <span data-ttu-id="1ac2a-128">**L’expression de filtre pour l’orchestration à liaison directe utilisée dans l’exemple de feuille de route rampe d’entrée**</span><span class="sxs-lookup"><span data-stu-id="1ac2a-128">**The filter expression for the direct-bound orchestration used in the Itinerary On-Ramp sample**</span></span>