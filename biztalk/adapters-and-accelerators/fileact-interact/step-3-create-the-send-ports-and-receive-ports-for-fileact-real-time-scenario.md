---
title: "Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d7d39c7-a08b-4fbb-85fe-b30a8d62524b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa7b0465ca6909998379ea94ef173d30387da602
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-the-send-ports-and-receive-ports-for-the-fileact-real-time-scenario"></a><span data-ttu-id="c57d2-102">Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="c57d2-102">Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="c57d2-103">Avant de commencer les étapes décrites dans cette section, vous devez effectuer [étape 2 : ajouter une Configuration pour le Paramfile pour le scénario en temps réel de FileAct SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="c57d2-103">Before you begin the steps in this section, you must complete [Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-real-time-scenario.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c57d2-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c57d2-104">In This Section</span></span>  
  
-   [<span data-ttu-id="c57d2-105">Étape 3 a : ajouter un fichier emplacement de réception pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="c57d2-105">Step 3A: Add a FILE Receive Location for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)  
  
-   [<span data-ttu-id="c57d2-106">Étape 3 b : ajouter un FILEACT emplacement de réception pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="c57d2-106">Step 3B: Add a FILEACT Receive Location for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)  
  
-   [<span data-ttu-id="c57d2-107">Étape 3c : ajouter un Port d’envoi FILE pour capturer les messages Sw:HandleRequest pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="c57d2-107">Step 3C: Add a FILE Send Port to Capture Sw:HandleRequest Message for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)  
  
-   [<span data-ttu-id="c57d2-108">Étape 3D : ajouter un Port d’envoi FILEACT pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="c57d2-108">Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)  
  
-   [<span data-ttu-id="c57d2-109">Étape 3E : ajouter un Port d’envoi FILE pour capturer les messages Sw:ExchangeFileResponse pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="c57d2-109">Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)  
  
-   [<span data-ttu-id="c57d2-110">Étape 3 : ajouter un Port d’envoi de fichier pour le scénario en temps réel FileAct capturer les Messages Sw-HandleFileEventRequest</span><span class="sxs-lookup"><span data-stu-id="c57d2-110">Step 3F: Add a FILE Send Port for the FileAct Real-Time Scenario to Capture Sw-HandleFileEventRequest Messages</span></span>](../../adapters-and-accelerators/fileact-interact/step-3f-add-file-send-port-to-get-sw-handlefileeventrequest-messages--fileact.md)