---
title: "Traitement des messages JSON à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6db1421-9478-477c-8645-09eefba06246
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c2e4adac7c7d1503a49f68208e45e09f86b67ac
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="processing-json-messages-using-biztalk-server"></a><span data-ttu-id="45fc4-102">Traitement des messages JSON à l'aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="45fc4-102">Processing JSON messages using BizTalk Server</span></span>
> [!NOTE]
>  <span data-ttu-id="45fc4-103">Ce didacticiel s’applique uniquement à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="45fc4-103">This tutorial applies to BizTalk Server only.</span></span>  
  
 <span data-ttu-id="45fc4-104">Ce didacticiel explique comment traiter les messages JSON à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45fc4-104">This tutorial demonstrates how to process JSON messages using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="45fc4-105">Le didacticiel utilise des composants de pipeline personnalisé maintenant disponibles avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="45fc4-105">The tutorial uses custom pipeline components, now available with BizTalk Server.</span></span> <span data-ttu-id="45fc4-106">Ces composants de pipeline convertissent le message JSON en XML lors de la réception du message dans l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et convertit le message du format XML au format JSON lors de l'envoi du message.</span><span class="sxs-lookup"><span data-stu-id="45fc4-106">These pipeline components convert the JSON message to XML (while receiving the message into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration, and converts the message from XML to JSON while sending the message out.</span></span>  
  
## <a name="what-does-this-tutorial-do"></a><span data-ttu-id="45fc4-107">À quoi sert ce didacticiel ?</span><span class="sxs-lookup"><span data-stu-id="45fc4-107">What does this tutorial do?</span></span>  
 <span data-ttu-id="45fc4-108">Pour illustrer le traitement JSON, nous créons une [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui effectue ce qui suit, dans l'ordre indiqué :</span><span class="sxs-lookup"><span data-stu-id="45fc4-108">To demonstrate JSON processing, we create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that does the following, in the given order:</span></span>  
  
1.  <span data-ttu-id="45fc4-109">Reçoit un bon de commande JSON et, dans le pipeline de réception, utilise un composant du décodeur JSON pour transformer le message JSON en message XML.</span><span class="sxs-lookup"><span data-stu-id="45fc4-109">Receives a JSON purchase order and in the receive pipeline, uses a JSON decoder component to transform the JSON message to XML message.</span></span>  
  
2.  <span data-ttu-id="45fc4-110">Transforme le bon de commande XML en facture XML à l'aide d'un mappage.</span><span class="sxs-lookup"><span data-stu-id="45fc4-110">Transforms the XML purchase order into an XML invoice using a map.</span></span>  
  
3.  <span data-ttu-id="45fc4-111">Dans le pipeline d'envoi, utilise un encodeur JSON pour transformer la facture XML en une facture JSON et l'envoie.</span><span class="sxs-lookup"><span data-stu-id="45fc4-111">In the send pipeline, uses a JSON encoder to transform the XML invoice into a JSON invoice and sends it out.</span></span>  
  
 <span data-ttu-id="45fc4-112">![Traitement des messages JSON dans BizTalk Server](../core/media/btsjson-flow.png "BTSJSON_Flow")</span><span class="sxs-lookup"><span data-stu-id="45fc4-112">![Processing JSON messages in BizTalk Server](../core/media/btsjson-flow.png "BTSJSON_Flow")</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="45fc4-113">Comment utiliser ce didacticiel ?</span><span class="sxs-lookup"><span data-stu-id="45fc4-113">How to use this tutorial?</span></span>  
 <span data-ttu-id="45fc4-114">Ce didacticiel est construit autour d’un exemple (**BTSJSON**) qui peut être téléchargé à partir de la [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=403197).</span><span class="sxs-lookup"><span data-stu-id="45fc4-114">This tutorial is built around a sample (**BTSJSON**) that can be downloaded from the [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=403197).</span></span> <span data-ttu-id="45fc4-115">Vous pouvez utiliser l'exemple et parcourir ce didacticiel pour comprendre comment l'exemple a été construit.</span><span class="sxs-lookup"><span data-stu-id="45fc4-115">You could use the sample and go through this tutorial to understand how the sample was built.</span></span> <span data-ttu-id="45fc4-116">Vous pouvez également utiliser ce didacticiel pour créer votre propre solution de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="45fc4-116">Or, you could use this tutorial to create your own solution ground-up.</span></span> <span data-ttu-id="45fc4-117">Ce didacticiel cible la seconde approche afin que vous compreniez comment cette solution a été construite.</span><span class="sxs-lookup"><span data-stu-id="45fc4-117">This tutorial is targeted towards the second approach so that you understand how this solution was built.</span></span> <span data-ttu-id="45fc4-118">Dans toute la mesure du possible, ce didacticiel est également compatible avec l'exemple et utilise les mêmes noms des artefacts (par exemple, des schémas, des transformations) que ceux employés dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="45fc4-118">Also, as much as possible, the tutorial is consistent with the sample and uses the same names for artifacts (for example, schemas, transforms) as used in the sample.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45fc4-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="45fc4-119">In This Section</span></span>  
  
-   [<span data-ttu-id="45fc4-120">Générer un schéma XSD pour un message JSON</span><span class="sxs-lookup"><span data-stu-id="45fc4-120">Generate an XSD schema for JSON message</span></span>](../core/generate-an-xsd-schema-for-json-message.md)  
  
-   [<span data-ttu-id="45fc4-121">Créer des pipelines personnalisés pour traiter les messages JSON</span><span class="sxs-lookup"><span data-stu-id="45fc4-121">Create custom pipelines to process JSON messages</span></span>](../core/create-custom-pipelines-to-process-json-messages.md)  
  
-   [<span data-ttu-id="45fc4-122">Créer une orchestration BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="45fc4-122">Create a BizTalk Server orchestration</span></span>](../core/create-a-biztalk-server-orchestration.md)  
  
-   [<span data-ttu-id="45fc4-123">Déployer et tester l’application</span><span class="sxs-lookup"><span data-stu-id="45fc4-123">Deploy and test the application</span></span>](../core/deploy-and-test-the-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="45fc4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45fc4-124">See Also</span></span>  
 [<span data-ttu-id="45fc4-125">Didacticiels BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="45fc4-125">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)