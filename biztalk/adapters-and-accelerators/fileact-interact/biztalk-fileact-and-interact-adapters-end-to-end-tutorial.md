---
title: BizTalk FileAct et interagir didacticiel de bout en bout vers adaptateurs | Documents Microsoft
ms.custom: 
ms.date: 2015-12-10
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73fbfb10-73e8-4365-a943-bcb9055f4f74
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15f2908abdb039d531fc0829efa7e019a6d0ca03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-fileact-and-interact-adapters-end-to-end-tutorial"></a><span data-ttu-id="ef622-102">BizTalk FileAct et interagir didacticiel de bout en bout pour les cartes</span><span class="sxs-lookup"><span data-stu-id="ef622-102">BizTalk FileAct and InterAct Adapters End-to-End Tutorial</span></span>
<span data-ttu-id="ef622-103">The Microsoft® [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] didacticiel de bout en bout fournit des informations spécifiques sur la façon dont vous pouvez utiliser [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] à installer en temps réel et stocker et transmettre des scénarios d’échange de message.</span><span class="sxs-lookup"><span data-stu-id="ef622-103">The Microsoft® [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] End-to-End Tutorial provides specific information about how you can use [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to set up real-time and store and forward message exchange scenarios.</span></span>  
  
 <span data-ttu-id="ef622-104">Le [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] didacticiel de bout en bout fournit quatre scénarios distincts qui incluent des instructions détaillées sous la forme de didacticiels pour chaque type de solution.</span><span class="sxs-lookup"><span data-stu-id="ef622-104">The [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] End-To-End Tutorial provides four separate scenarios that include detailed steps in the form of tutorials for each type of solution.</span></span> <span data-ttu-id="ef622-105">Avant de commencer ces didacticiels, vous devez comprendre les concepts fondamentaux liés à BizTalk Server et être familiarisé avec la documentation de la passerelle de Alliance SWIFT (trous).</span><span class="sxs-lookup"><span data-stu-id="ef622-105">Before you begin these tutorials, you should understand the fundamental concepts surrounding BizTalk Server, and be familiar with the SWIFT Alliance Gateway (SAG) documentation.</span></span>  
  
 <span data-ttu-id="ef622-106">Le didacticiel de bout en bout A4SWIFT fournit les étapes détaillées pour configurer en temps réel et les scénarios de stockage et transfert avec à la fois les adaptateurs FileAct et InterAct pour A4Swift.</span><span class="sxs-lookup"><span data-stu-id="ef622-106">The A4SWIFT end-to-end tutorial provides you with detailed steps to configure real-time and store-and-forward scenarios with both the FileAct and InterAct adapters for A4Swift.</span></span> <span data-ttu-id="ef622-107">Pour chacun des scénarios, vous effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ef622-107">For each of the scenarios, you will do the following:</span></span>  
  
-   <span data-ttu-id="ef622-108">Configurez la carte SWIFT</span><span class="sxs-lookup"><span data-stu-id="ef622-108">Configure the SWIFT adapter</span></span>  
  
-   <span data-ttu-id="ef622-109">Configurer la paramfile SWIFTNet</span><span class="sxs-lookup"><span data-stu-id="ef622-109">Configure the SWIFTNet paramfile</span></span>  
  
-   <span data-ttu-id="ef622-110">Créer des ports d’envoi et ports de réception</span><span class="sxs-lookup"><span data-stu-id="ef622-110">Create send ports and receive ports</span></span>  
  
-   <span data-ttu-id="ef622-111">Le scénario de test</span><span class="sxs-lookup"><span data-stu-id="ef622-111">Test the scenario</span></span>  
  
 <span data-ttu-id="ef622-112">Dans ce didacticiel, vous allez jouer les deux rôles : expéditeur et récepteur.</span><span class="sxs-lookup"><span data-stu-id="ef622-112">In this tutorial, you will play two roles: Sender and Receiver.</span></span> <span data-ttu-id="ef622-113">Vous allez créer les ports qui envoient des messages et de les recevoir.</span><span class="sxs-lookup"><span data-stu-id="ef622-113">You will create ports that send messages and receive them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef622-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ef622-114">In This Section</span></span>  
  
-   [<span data-ttu-id="ef622-115">Préparation à l’utilisation du didacticiel</span><span class="sxs-lookup"><span data-stu-id="ef622-115">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)  
  
-   [<span data-ttu-id="ef622-116">Interagir scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="ef622-116">InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)  
  
-   [<span data-ttu-id="ef622-117">Interagir Store et le scénario de transfert (Push)</span><span class="sxs-lookup"><span data-stu-id="ef622-117">InterAct Store and Forward (Push) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)  
  
-   [<span data-ttu-id="ef622-118">Scénario en temps réel de FileAct</span><span class="sxs-lookup"><span data-stu-id="ef622-118">FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)  
  
-   [<span data-ttu-id="ef622-119">Scénario de transfert et de FileAct</span><span class="sxs-lookup"><span data-stu-id="ef622-119">FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)