---
title: "Exécution de l’exemple d’enrichissement de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7015a2fe-3727-48f3-a2ed-c368e0630626
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4ed3b3ebc24a908dfefd70711db0d40638c2d3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-message-enrichment-sample"></a><span data-ttu-id="3b8b8-102">L’exemple d’enrichissement de Message en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="3b8b8-102">Running the Message Enrichment Sample</span></span>
<span data-ttu-id="3b8b8-103">L’exemple d’enrichissement de Message utilise une application de client Windows Forms test fournie avec l’exemple de feuille de route rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-103">The Message Enrichment sample uses a Windows Forms test client application provided with the Itinerary On-Ramp sample.</span></span>  
  
 <span data-ttu-id="3b8b8-104">**Pour exécuter l’exemple d’enrichissement de Message**</span><span class="sxs-lookup"><span data-stu-id="3b8b8-104">**To run Message Enrichment sample**</span></span>  
  
1.  <span data-ttu-id="3b8b8-105">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-105">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="3b8b8-106">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-106">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="3b8b8-107">Désactivez le **utiliser le Service WCF** case à cocher afin qu’un itinéraire côté client peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-107">Clear the **Use WCF Service** check box so that a client-side itinerary can be utilized.</span></span>  
  
4.  <span data-ttu-id="3b8b8-108">Cliquez sur le **charge itinéraire** bouton, puis sélectionnez parmi les itinéraires de l’exemple situés dans le dossier \Source\Samples\MessageEnrichment\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-108">Click the **Load Itinerary** button, and then select one of the sample itineraries located in the \Source\Samples\MessageEnrichment\Itineraries folder.</span></span>  
  
5.  <span data-ttu-id="3b8b8-109">Cliquez sur le **LoadMessage** , puis l’exemple de message OrderDoc.xml à partir du dossier \Source\Samples\MessageEnrichment\Test\.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-109">Click the **LoadMessage** button, and then select the OrderDoc.xml sample message from the \Source\Samples\MessageEnrichment\Test\ folder.</span></span>  
  
6.  <span data-ttu-id="3b8b8-110">Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-110">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span>  
  
7.  <span data-ttu-id="3b8b8-111">Accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out\\%MessageID%.xml pour afficher le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-111">Browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out\\%MessageID%.xml to see the output message.</span></span>  
  
 <span data-ttu-id="3b8b8-112">Pour plus d’informations sur le fonctionne de l’exemple d’enrichissement de Message, consultez [Message enrichissement exemple fonctionnement](../esb-toolkit/how-the-message-enrichment-sample-works.md).</span><span class="sxs-lookup"><span data-stu-id="3b8b8-112">For information about how the Message Enrichment sample works, see [How the Message Enrichment Sample Works](../esb-toolkit/how-the-message-enrichment-sample-works.md).</span></span>