---
title: "Étape 16 : Démarrer l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, starting
- message enrichment tutorial, orchestrations
ms.assetid: a9032b0b-1497-4f6a-8474-a94c14976be0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5256d33dc6751db34d1d827624d2dbe2644639e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-16-start-the-orchestration"></a><span data-ttu-id="3c5c7-102">Étape 16 : Démarrer l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="3c5c7-102">Step 16: Start the Orchestration</span></span>
<span data-ttu-id="3c5c7-103">Dans cette étape, vous inscrivez le service afin d’associer le processus d’entreprise que vous avez créée dans l’orchestration à l’environnement physique dans lequel l’orchestration sera exécuté.</span><span class="sxs-lookup"><span data-stu-id="3c5c7-103">In this step, you enlist the service in order to associate the business process that you designed in the orchestration with the physical environment in which the orchestration will run.</span></span> <span data-ttu-id="3c5c7-104">En outre, vous démarrez le traitement de l’orchestration afin que vous puissiez tester votre application.</span><span class="sxs-lookup"><span data-stu-id="3c5c7-104">Additionally, you start the processing of the orchestration so that you can test your application.</span></span>  
  
### <a name="to-start-the-orchestration"></a><span data-ttu-id="3c5c7-105">Pour démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="3c5c7-105">To start the orchestration</span></span>  
  
1.  <span data-ttu-id="3c5c7-106">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration de la console, dans le volet d’arborescence de la console, sous **Orchestrations**, avec le bouton droit **BTAHL7_Project.Doorbell_Orchestration**, puis cliquez sur **Enlist** .</span><span class="sxs-lookup"><span data-stu-id="3c5c7-106">In the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, in the console tree pane, under **Orchestrations**, right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Enlist**.</span></span>  
  
2.  <span data-ttu-id="3c5c7-107">Avec le bouton droit **BTAHL7_Project.Doorbell_Orchestration**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="3c5c7-107">Right-click **BTAHL7_Project.Doorbell_Orchestration**, and then click **Start**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c5c7-108">Vérifiez que vous avez démarré le **MLLPSendPort** port d’envoi et activé le **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="3c5c7-108">Ensure that you have started the **MLLPSendPort** send port and enabled the **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort** receive location.</span></span>  
  
 <span data-ttu-id="3c5c7-109">Passez à [étape 17 : créer l’Application WSClient](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md).</span><span class="sxs-lookup"><span data-stu-id="3c5c7-109">Proceed to [Step 17: Create the WSClient Application](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5c7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c5c7-110">See Also</span></span>  
 [<span data-ttu-id="3c5c7-111">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="3c5c7-111">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)