---
title: "Exécution de l’exemple de ventilation-regroupement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53676974-ea1f-4c95-9dbb-98fff92286fa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dcafa519aac074ccb339373a591b590846c9341
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-scatter-gather-sample"></a><span data-ttu-id="a33a4-102">Exécution de l’exemple de ventilation-regroupement</span><span class="sxs-lookup"><span data-stu-id="a33a4-102">Running the Scatter-Gather Sample</span></span>
<span data-ttu-id="a33a4-103">L’exemple de ventilation-regroupement utilise une application cliente fournie avec l’exemple de feuille de route rampe d’entrée pour illustrer comment ce modèle applique les fonctionnalités du service itinéraire de test de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a33a4-103">The Scatter-Gather sample uses a the Windows Forms test client application provided with the Itinerary On-Ramp sample to demonstrate how this pattern applies the features of the Itinerary service.</span></span>  
  
 <span data-ttu-id="a33a4-104">**Pour exécuter l’exemple de ventilation-regroupement**</span><span class="sxs-lookup"><span data-stu-id="a33a4-104">**To run the Scatter-Gather sample**</span></span>  
  
1.  <span data-ttu-id="a33a4-105">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="a33a4-105">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="a33a4-106">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.</span><span class="sxs-lookup"><span data-stu-id="a33a4-106">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="a33a4-107">Cliquez sur le **LoadItinerary** , puis sur l’itinéraire d’exemple nommé ScatterGatherItinerary.xml à partir du dossier \Source\Samples\ScatterGather\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="a33a4-107">Click the **LoadItinerary** button, and then select the sample itinerary named ScatterGatherItinerary.xml from the \Source\Samples\ScatterGather\Itineraries folder.</span></span>  
  
4.  <span data-ttu-id="a33a4-108">Désactivez le **réponse à la demande est** case à cocher afin de l’application effectue un itinéraire à sens unique de services d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="a33a4-108">Clear the **Is Request Response** check box so the application will perform a one-way itinerary services operation.</span></span>  
  
5.  <span data-ttu-id="a33a4-109">(Facultatif) Définir le **utiliser un Service WCF** case à cocher si vous souhaitez que l’application pour utiliser le OnRamp.Itinerary.Response.WCF l’emplacement de réception au lieu de la valeur par défaut OnRamp.Itinerary.Response.SOAP emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="a33a4-109">(Optional) Set the **Use WCF Service** check box if you want the application to use the OnRamp.Itinerary.Response.WCF receive location instead of the default OnRamp.Itinerary.Response.SOAP receive location.</span></span>  
  
6.  <span data-ttu-id="a33a4-110">Cliquez sur le **LoadMessage** , puis l’exemple de message NAOrderDoc.xml à partir du dossier \Source\Samples\Itinerary\Test\Data.</span><span class="sxs-lookup"><span data-stu-id="a33a4-110">Click the **LoadMessage** button, and then select the NAOrderDoc.xml sample message from the \Source\Samples\Itinerary\Test\Data folder.</span></span>  
  
7.  <span data-ttu-id="a33a4-111">Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a33a4-111">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span> <span data-ttu-id="a33a4-112">Ouvrez le dossier \Source\Samples\DynamicResolution\Test\FileDrop\Out pour afficher le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="a33a4-112">Open the folder \Source\Samples\DynamicResolution\Test\FileDrop\Out to see the response message.</span></span>  
  
 <span data-ttu-id="a33a4-113">Pour savoir comment l’exemple de nuage de points de rassembler utilise le service de l’itinéraire d’ESB, consultez [ventilation-regroupement exemple fonctionnement](../esb-toolkit/how-the-scatter-gather-sample-works.md).</span><span class="sxs-lookup"><span data-stu-id="a33a4-113">For information about how the Scatter Gather sample uses the ESB Itinerary service, see [How the Scatter-Gather Sample Works](../esb-toolkit/how-the-scatter-gather-sample-works.md).</span></span>