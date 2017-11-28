---
title: "Exécute le site Web de plusieurs Services exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b201c7c3-213a-4009-8872-5a4c1cbb8195
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ec54fabb7ed140fd88b5a2d5a07d788805c741e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-multiple-web-services-sample"></a><span data-ttu-id="394ca-102">Exécution de l’exemple de Services Web multiples</span><span class="sxs-lookup"><span data-stu-id="394ca-102">Running the Multiple Web Services Sample</span></span>
<span data-ttu-id="394ca-103">L’exemple de plusieurs Services Web utilise l’application de client Windows Forms test fournie avec l’exemple de feuille de route rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="394ca-103">The Multiple Web Services sample uses the Windows Forms test client application provided with the Itinerary On-Ramp sample.</span></span>  
  
 <span data-ttu-id="394ca-104">**Pour exécuter l’exemple de plusieurs Services Web**</span><span class="sxs-lookup"><span data-stu-id="394ca-104">**To run the Multiple Web Services sample**</span></span>  
  
1.  <span data-ttu-id="394ca-105">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="394ca-105">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="394ca-106">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.</span><span class="sxs-lookup"><span data-stu-id="394ca-106">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="394ca-107">Désactivez le **utiliser le Service WCF** case, afin qu’un itinéraire côté client peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="394ca-107">Clear the **Use WCF Service** check box, so that a client-side itinerary can be utilized.</span></span>  
  
4.  <span data-ttu-id="394ca-108">Cliquez sur le **charge itinéraire** bouton, puis sélectionnez parmi les itinéraires de l’exemple situés dans le dossier \Source\Samples\MultipleWebServices\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="394ca-108">Click the **Load Itinerary** button, and then select one of the sample itineraries located in the \Source\Samples\MultipleWebServices\Itineraries folder.</span></span>  
  
5.  <span data-ttu-id="394ca-109">Sélectionnez le **deux manière Service** case à cocher afin de l’application effectue un itinéraire bidirectionnels services l’opération.</span><span class="sxs-lookup"><span data-stu-id="394ca-109">Select the **Two Way Service** check box so the application will perform a two-way itinerary services operation.</span></span>  
  
6.  <span data-ttu-id="394ca-110">Cliquez sur le **LoadMessage** , puis l’exemple de message NAOrderDoc.xml à partir du dossier \Source\Samples\Itinerary\Test\Data.</span><span class="sxs-lookup"><span data-stu-id="394ca-110">Click the **LoadMessage** button, and then select the NAOrderDoc.xml sample message from the \Source\Samples\Itinerary\Test\Data folder.</span></span>  
  
7.  <span data-ttu-id="394ca-111">Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="394ca-111">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span> <span data-ttu-id="394ca-112">Attendre un message de réponse s’affichent dans le **résultat** boîte.</span><span class="sxs-lookup"><span data-stu-id="394ca-112">Wait for a response message to appear in the **Result** box.</span></span>  
  
 <span data-ttu-id="394ca-113">Pour savoir comment l’exemple de plusieurs Services Web utilise le service de l’itinéraire d’ESB, consultez [plusieurs Web Services exemple fonctionnement](../esb-toolkit/how-the-multiple-web-services-sample-works.md).</span><span class="sxs-lookup"><span data-stu-id="394ca-113">For information about how the Multiple Web Services sample uses the ESB Itinerary service, see [How the Multiple Web Services Sample Works](../esb-toolkit/how-the-multiple-web-services-sample-works.md).</span></span>