---
title: "Collecte des Exceptions et la persistance de la charge utile à l’aide du processeur d’Exception ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52650eed-e760-4ade-bc3f-2b5b2a1c43ff
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec3ca7a33b5a38b625894e391c5bf014eb824414
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="collecting-exceptions-and-persisting-the-payload-using-the-esb-exception-processor"></a><span data-ttu-id="a2b66-102">Collecte des Exceptions et la persistance de la charge utile à l’aide du processeur d’Exception ESB</span><span class="sxs-lookup"><span data-stu-id="a2b66-102">Collecting Exceptions and Persisting the Payload Using the ESB Exception Processor</span></span>
<span data-ttu-id="a2b66-103">Dans ce cas de figure, le Gestionnaire d’exceptions pour une orchestration publie un message d’erreur ESB le [!INCLUDE[prague](../includes/prague-md.md)] boîte de Message ou le mécanisme de routage des messages a échoué BizTalk génère un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a2b66-103">In this use case, either the exception handler for an orchestration publishes an ESB fault message to the [!INCLUDE[prague](../includes/prague-md.md)] Message Box or the BizTalk Failed Message Routing mechanism generates a fault message.</span></span> <span data-ttu-id="a2b66-104">Un port d’envoi, préconfiguré avec le composant de pipeline encodeur d’Exception ESB, s’abonne à des types de message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a2b66-104">A send port, preconfigured with the ESB Exception Encoder pipeline component, subscribes to both of the fault message types.</span></span> <span data-ttu-id="a2b66-105">Il traite les messages d’erreur, puis les en tant que fichiers de disque que vous pouvez consulter à l’aide d’InfoPath, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="a2b66-105">It processes the fault messages and then persists them as disk files that you can view using InfoPath, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="a2b66-106">![Collecte de charge utile d’Exceptions](../esb-toolkit/media/ch3-collectingexceptionspayload.gif "Ch3-CollectingExceptionsPayload")</span><span class="sxs-lookup"><span data-stu-id="a2b66-106">![Collecting Exceptions Payload](../esb-toolkit/media/ch3-collectingexceptionspayload.gif "Ch3-CollectingExceptionsPayload")</span></span>  
  
 <span data-ttu-id="a2b66-107">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="a2b66-107">**Figure 1**</span></span>  
  
 <span data-ttu-id="a2b66-108">**Capture d’un message d’erreur et les rend persistantes dans un fichier de disque**</span><span class="sxs-lookup"><span data-stu-id="a2b66-108">**Capturing a fault message and persisting it to a disk file**</span></span>  
  
 <span data-ttu-id="a2b66-109">La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a2b66-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes the following:</span></span>  
  
-   <span data-ttu-id="a2b66-110">**Un préconfigurés port d’envoi qui utilise le pipeline d’envoi ESB erreur processeur.**</span><span class="sxs-lookup"><span data-stu-id="a2b66-110">**A preconfigured send port that uses the ESB Fault Processor send pipeline.**</span></span> <span data-ttu-id="a2b66-111">Vous pouvez configurer ce port d’envoi en fonction de vos besoins spécifiques.</span><span class="sxs-lookup"><span data-stu-id="a2b66-111">You can configure this send port according to your own specific requirements.</span></span>  
  
-   <span data-ttu-id="a2b66-112">**L’exemple de gestionnaire d’exceptions Message persistance personnalisée.**</span><span class="sxs-lookup"><span data-stu-id="a2b66-112">**The Message Persisting Custom Exception Handler sample.**</span></span> <span data-ttu-id="a2b66-113">Cet exemple montre comment un gestionnaire d’exceptions génériques faiblement couplée peut recevoir des messages d’erreur, extraire les messages BizTalk Server qu’ils contiennent, normalisent et enrichissement les messages et les écrivent sous forme de fichiers de disque dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a2b66-113">This sample shows how a loosely coupled generic exception handler can receive fault messages, extract the BizTalk Server messages they contain, normalize and enrich the messages, and write them as disk files to the file system.</span></span>  
  
-   <span data-ttu-id="a2b66-114">**L’exemple de routage des messages a échoué BizTalk.**</span><span class="sxs-lookup"><span data-stu-id="a2b66-114">**The BizTalk Failed Message Routing sample.**</span></span> <span data-ttu-id="a2b66-115">Cet exemple montre comment l’infrastructure de gestion d’Exception ESB normaliser et enrichir les messages d’erreur en mode natif par le mécanisme de routage des messages d’échec dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a2b66-115">This sample shows how the ESB Exception Management Framework can normalize and enrich fault messages natively generated by the Failed Message Routing mechanism in BizTalk Server.</span></span>  
  
 <span data-ttu-id="a2b66-116">Pour plus d’informations, consultez [exécution de l’exemple Gestionnaire de Message de persistance personnalisé Exception](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md) et [le BizTalk Échec de routage ESB traitement exemple de Message en cours d’exécution](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a2b66-116">For more information, see [Running the Message Persisting Custom Exception Handler Sample](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md) and [Running the BizTalk Failed Message Routing ESB Processing Sample](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md).</span></span>