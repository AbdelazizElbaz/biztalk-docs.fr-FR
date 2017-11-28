---
title: "L’exemple d’adaptateur SQL en cours d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13566d08-7a59-4065-b0d7-19ae2765555e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf04c06a1ef96974912ce3affe278d5a98936325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-sql-adapter-sample"></a><span data-ttu-id="1ab97-102">L’exemple d’adaptateur SQL en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="1ab97-102">Running the SQL Adapter Sample</span></span>
<span data-ttu-id="1ab97-103">L’exemple d’adaptateur SQL utilise une application de client Windows Forms test fournie avec l’exemple de feuille de route rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1ab97-103">The SQL Adapter sample uses a Windows Forms test client application provided with the Itinerary On-Ramp sample.</span></span>  
  
 <span data-ttu-id="1ab97-104">**Pour exécuter l’exemple d’adaptateur SQL**</span><span class="sxs-lookup"><span data-stu-id="1ab97-104">**To run the SQL Adapter sample**</span></span>  
  
1.  <span data-ttu-id="1ab97-105">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="1ab97-105">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="1ab97-106">Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.</span><span class="sxs-lookup"><span data-stu-id="1ab97-106">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="1ab97-107">Désactivez le **utiliser le Service WCF** case à cocher afin qu’un itinéraire côté client peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="1ab97-107">Clear the **Use WCF Service** check box so that a client-side itinerary can be used.</span></span>  
  
4.  <span data-ttu-id="1ab97-108">Sélectionnez le **deux manière Service** option</span><span class="sxs-lookup"><span data-stu-id="1ab97-108">Select the **Two Way Service** option</span></span>  
  
5.  <span data-ttu-id="1ab97-109">Cliquez sur le **charge itinéraire** bouton, puis sélectionnez un des itinéraires de l’exemple situés dans le dossier \Source\Samples\SqlAdapter \Itineraries.</span><span class="sxs-lookup"><span data-stu-id="1ab97-109">Click the **Load Itinerary** button, and then select one of the sample itineraries located in the folder \Source\Samples\SqlAdapter \Itineraries.</span></span>  
  
6.  <span data-ttu-id="1ab97-110">Cliquez sur le **LoadMessage** , puis l’exemple de message OrderDoc.xml dans le dossier \Source\Samples\SqlAdapter \Test.</span><span class="sxs-lookup"><span data-stu-id="1ab97-110">Click the **LoadMessage** button, and then select the OrderDoc.xml sample message in the folder \Source\Samples\SqlAdapter \Test.</span></span>  
  
7.  <span data-ttu-id="1ab97-111">Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1ab97-111">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span>  
  
8.  <span data-ttu-id="1ab97-112">Assurez-vous d’une ligne est insérée dans la table Product de la base de données GlobalBankESB.</span><span class="sxs-lookup"><span data-stu-id="1ab97-112">Make sure one row is inserted in the Product table of the GlobalBankESB database.</span></span>  
  
 <span data-ttu-id="1ab97-113">Pour plus d’informations sur le fonctionne de l’exemple d’adaptateur SQL, consultez [SQL adaptateur exemple fonctionnement](../esb-toolkit/how-the-sql-adapter-sample-works.md).</span><span class="sxs-lookup"><span data-stu-id="1ab97-113">For information about how the SQL Adapter sample works, see [How the SQL Adapter Sample Works](../esb-toolkit/how-the-sql-adapter-sample-works.md).</span></span>