---
title: "Création d’un Port et l’hôte de HTTP PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP port
- HTTP host
ms.assetid: 3e1ce5fd-32ee-409f-b4c8-f2bc68470f17
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e673b2a2acdcd5248391f245ab990d424aefd298
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-peoplesoft-http-host-and-port"></a><span data-ttu-id="ac2bd-102">Création d'hôtes et de ports HTTP PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="ac2bd-102">Creating a PeopleSoft HTTP Host and Port</span></span>
<span data-ttu-id="ac2bd-103">L'architecture de publication des messages de PeopleSoft est appelée Integration Broker.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-103">The Message publication architecture in PeopleSoft is known as Integration Broker.</span></span> <span data-ttu-id="ac2bd-104">Elle inclut les principaux composants suivants :</span><span class="sxs-lookup"><span data-stu-id="ac2bd-104">The main components of Integration Broker are as follows:</span></span>  
  
-   <span data-ttu-id="ac2bd-105">Passerelle</span><span class="sxs-lookup"><span data-stu-id="ac2bd-105">Gateway</span></span>  
  
-   <span data-ttu-id="ac2bd-106">nœud de publication ;</span><span class="sxs-lookup"><span data-stu-id="ac2bd-106">Publishing node</span></span>  
  
-   <span data-ttu-id="ac2bd-107">nœud d'abonné.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-107">Subscriber node</span></span>  
  
 <span data-ttu-id="ac2bd-108">Ces trois composants fonctionnent ensemble pour publier un message vers une URL pour un écouteur HTTP.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-108">All three work together to publish a message to a URL for an HTTP listener.</span></span> <span data-ttu-id="ac2bd-109">Vous devez définir le nœud de publication.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-109">You must set the Publishing node.</span></span> <span data-ttu-id="ac2bd-110">PeopleSoft inclut un nœud de publication par défaut, également appelé nœud de message local.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-110">PeopleSoft has a default publishing node, also known as local message node.</span></span> <span data-ttu-id="ac2bd-111">Vous devez activer le nœud et les transactions pour le nœud de publication.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-111">You must activate the node and the transactions for the publishing node.</span></span> <span data-ttu-id="ac2bd-112">Vous devez définir le type du nœud d'abonnement comme nœud externe, puis l'activer, ainsi que les transactions.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-112">You must set the Subscription node with the type as external node, and then activate the node and the transactions.</span></span> <span data-ttu-id="ac2bd-113">Pour ce nœud, vous devez également définir le type sur HTTP et définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-113">For this node, you also set the type to be HTTP and set the connection information.</span></span>  
  
 <span data-ttu-id="ac2bd-114">PeopleSoft Integration Broker permet de créer un hôte et un port HTTP PeopleSoft auxquels PeopleSoft envoie des événements.</span><span class="sxs-lookup"><span data-stu-id="ac2bd-114">You use PeopleSoft Integration Broker to create a PeopleSoft HTTP Host and Port where PeopleSoft sends events.</span></span> <span data-ttu-id="ac2bd-115">Vous vous assurer que le message est actif et acheminé à l’aide de la procédure décrite dans [vérifier statut d’activité d’un Message](../core/how-to-verify-activity-status-of-a-message.md).</span><span class="sxs-lookup"><span data-stu-id="ac2bd-115">You make sure that the message is active and routed by using the procedure in [How to Verify Activity Status of a Message](../core/how-to-verify-activity-status-of-a-message.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac2bd-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ac2bd-116">In This Section</span></span>  
  
-   [<span data-ttu-id="ac2bd-117">Comment vérifier l’état de l’activité d’un Message</span><span class="sxs-lookup"><span data-stu-id="ac2bd-117">How to Verify Activity Status of a Message</span></span>](../core/how-to-verify-activity-status-of-a-message.md)  
  
-   [<span data-ttu-id="ac2bd-118">Comment configurer la passerelle d’intégration et d’un connecteur de sortie HTTP</span><span class="sxs-lookup"><span data-stu-id="ac2bd-118">How to Configure the Integration Gateway and HTTP Output Connector</span></span>](../core/how-to-configure-the-integration-gateway-and-http-output-connector.md)  
  
-   [<span data-ttu-id="ac2bd-119">Comment créer un nouveau nœud de passerelle</span><span class="sxs-lookup"><span data-stu-id="ac2bd-119">How to Create a New Gateway Node</span></span>](../core/how-to-create-a-new-gateway-node.md)  
  
-   [<span data-ttu-id="ac2bd-120">L’ajout d’une Transaction</span><span class="sxs-lookup"><span data-stu-id="ac2bd-120">How to Add a Transaction</span></span>](../core/how-to-add-a-transaction.md)  
  
-   [<span data-ttu-id="ac2bd-121">Comment tester le nœud HTTP</span><span class="sxs-lookup"><span data-stu-id="ac2bd-121">How to Test the HTTP Node</span></span>](../core/how-to-test-the-http-node.md)