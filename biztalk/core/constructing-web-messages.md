---
title: Construction de Messages Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, about Web messages
- Web messages, message types
- Web services, Web messages
- Web messages, parts
- Web messages
- messages, Web messages
ms.assetid: ca1792be-5fba-4f5d-a88e-b854f6a8ce33
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c344bbb836a6524ec1fd2656a5ba3f8bc8fad7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-web-messages"></a><span data-ttu-id="7e683-102">Création des messages Web</span><span class="sxs-lookup"><span data-stu-id="7e683-102">Constructing Web Messages</span></span>
<span data-ttu-id="7e683-103">Vous générez un message Web à partir d'un type de message Web.</span><span class="sxs-lookup"><span data-stu-id="7e683-103">You construct a Web message from a Web message type.</span></span> <span data-ttu-id="7e683-104">Lorsque vous ajoutez une référence Web, BizTalk crée automatiquement des types de messages Web basés sur les méthodes Web du service Web ajouté.</span><span class="sxs-lookup"><span data-stu-id="7e683-104">When you add a Web reference, BizTalk automatically creates Web message types, which BizTalk creates based on the Web methods from the added Web service.</span></span> <span data-ttu-id="7e683-105">Vous ajoutez un message Web à votre orchestration en définissant le type de message sur l'un des types de messages Web.</span><span class="sxs-lookup"><span data-stu-id="7e683-105">You add a Web message to your orchestration, setting the message type to one of the Web message types.</span></span> <span data-ttu-id="7e683-106">Vous créez des parties de message individuelles basées sur un type .NET primitif ou de schéma.</span><span class="sxs-lookup"><span data-stu-id="7e683-106">You create individual message parts based on primitive .NET or schema types.</span></span> <span data-ttu-id="7e683-107">Vous pouvez générer un message Web qui ne contient aucune partie de message.</span><span class="sxs-lookup"><span data-stu-id="7e683-107">You can construct a Web message that contains no message parts.</span></span>  
  
 <span data-ttu-id="7e683-108">**Types de messages Web**</span><span class="sxs-lookup"><span data-stu-id="7e683-108">**Web message types**</span></span>  
  
 <span data-ttu-id="7e683-109">Les types de messages Web (définis dans Reference.odx) sont identiques à un type de message normal, sauf que vous ne pouvez pas les modifier, les renommer ou les supprimer.</span><span class="sxs-lookup"><span data-stu-id="7e683-109">Web message types, defined in the Reference.odx, are identical to a normal message type, except you cannot modify, rename or delete them.</span></span> <span data-ttu-id="7e683-110">Pour supprimer un type de message Web, vous devez supprimer la référence Web de votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7e683-110">To delete a Web message type, you must remove the Web reference from your BizTalk project.</span></span>  
  
 <span data-ttu-id="7e683-111">Le projet BizTalk crée une demande et un type de message Web de réponse pour chaque méthode Web dans le service Web ajouté.</span><span class="sxs-lookup"><span data-stu-id="7e683-111">BizTalk project creates one request and one response Web message type for each Web method in the added Web service.</span></span> <span data-ttu-id="7e683-112">Si la méthode Web est une opération unidirectionnelle, BizTalk crée uniquement un type de message Web de demande.</span><span class="sxs-lookup"><span data-stu-id="7e683-112">If the Web method is a one-way operation, BizTalk only creates a request Web message type.</span></span> <span data-ttu-id="7e683-113">Un type de message Web de demande contient une partie de message pour chaque paramètre d'entrée de la méthode Web.</span><span class="sxs-lookup"><span data-stu-id="7e683-113">A request Web message type contains one message part for each input parameter of the Web method.</span></span> <span data-ttu-id="7e683-114">Un type de message Web de réponse contient une partie de message pour la valeur renvoyée et une partie de message pour chaque paramètre de sortie de la méthode Web.</span><span class="sxs-lookup"><span data-stu-id="7e683-114">A response Web message type contains one message part for the return value and one message part for each output parameter of the Web method.</span></span>  
  
 <span data-ttu-id="7e683-115">Selon le paramètre de méthode Web (entrée ou sortie), BizTalk crée un type de message Web à partir d'un type .NET primitif ou de schéma.</span><span class="sxs-lookup"><span data-stu-id="7e683-115">Depending on the Web method parameter (input or output), BizTalk creates a Web message type from a primitive .NET type or a schema type.</span></span> <span data-ttu-id="7e683-116">Si le paramètre de méthode Web est un type .NET primitif, la partie de message utilise un type .NET primitif.</span><span class="sxs-lookup"><span data-stu-id="7e683-116">If the Web method parameter is a primitive .NET type, the message part uses a primitive .NET type.</span></span> <span data-ttu-id="7e683-117">Si le paramètre de méthode Web est un type de schéma, BizTalk ajoute le type de schéma au projet BizTalk en tant que schéma dans Reference.xsd.</span><span class="sxs-lookup"><span data-stu-id="7e683-117">If the Web method parameter is a schema type, BizTalk adds the schema type to the BizTalk project as a schema in Reference.xsd.</span></span> <span data-ttu-id="7e683-118">Le schéma constitue la base de la partie du message.</span><span class="sxs-lookup"><span data-stu-id="7e683-118">The schema is the basis for the message part.</span></span> <span data-ttu-id="7e683-119">Le fichier Reference.xsd se trouve dans le dossier des références Web.</span><span class="sxs-lookup"><span data-stu-id="7e683-119">You can find Reference.xsd in the Web references folder.</span></span>  
  
 <span data-ttu-id="7e683-120">Vous pouvez également créer des types .NET primitifs et de schéma en appelant une classe .NET.</span><span class="sxs-lookup"><span data-stu-id="7e683-120">Alternatively, you can create both primitive and schema .NET types by calling a .NET class.</span></span> <span data-ttu-id="7e683-121">Pour plus d’informations sur la création de types de messages à l’aide d’une classe .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).</span><span class="sxs-lookup"><span data-stu-id="7e683-121">For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
 <span data-ttu-id="7e683-122">**Messages Web**</span><span class="sxs-lookup"><span data-stu-id="7e683-122">**Web messages**</span></span>  
  
 <span data-ttu-id="7e683-123">Les messages Web sont des messages utilisés dans le cadre de l'utilisation (appel) d'un service Web.</span><span class="sxs-lookup"><span data-stu-id="7e683-123">Web messages are the messages you use when you consume (call) a Web service.</span></span> <span data-ttu-id="7e683-124">Vous ajoutez un message Web à une orchestration comme vous le faites pour un message normal. Vous devez seulement définir le type de message sur un des types de messages Web créés par BizTalk lorsque vous avez ajouté une référence Web.</span><span class="sxs-lookup"><span data-stu-id="7e683-124">You add a Web message to an orchestration the same way that you add a regular message, except that you set the message type to one of the Web message types that BizTalk created when you added a Web reference.</span></span>  
  
 <span data-ttu-id="7e683-125">**Parties de message**</span><span class="sxs-lookup"><span data-stu-id="7e683-125">**Message parts**</span></span>  
  
 <span data-ttu-id="7e683-126">Une fois que vous avez créé le message Web, vous générez les parties de message individuelles.</span><span class="sxs-lookup"><span data-stu-id="7e683-126">After you create the Web message, you construct the individual message parts.</span></span> <span data-ttu-id="7e683-127">Si votre partie de message utilise un type .NET primitif, vous utilisez un **assignation du Message** forme.</span><span class="sxs-lookup"><span data-stu-id="7e683-127">If your message part uses a primitive .NET type, you use a **Message Assignment** shape.</span></span> <span data-ttu-id="7e683-128">Si votre partie de message utilise un type de schéma, vous utilisez un **transformer** forme ou **assignation du Message** forme.</span><span class="sxs-lookup"><span data-stu-id="7e683-128">If your message part uses a schema type, you use a **Transform** shape or **Message Assignment** shape.</span></span> <span data-ttu-id="7e683-129">Pour plus d’informations, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).</span><span class="sxs-lookup"><span data-stu-id="7e683-129">For more information, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e683-130">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7e683-130">In This Section</span></span>  
  
-   [<span data-ttu-id="7e683-131">Comment ajouter des Messages Web</span><span class="sxs-lookup"><span data-stu-id="7e683-131">How to Add Web Messages</span></span>](../core/how-to-add-web-messages.md)  
  
-   [<span data-ttu-id="7e683-132">Comment déterminer un Type de partie de Message Web</span><span class="sxs-lookup"><span data-stu-id="7e683-132">How to Determine a Web Message Part Type</span></span>](../core/how-to-determine-a-web-message-part-type.md)  
  
-   [<span data-ttu-id="7e683-133">Comment construire une partie de Message Web à partir d’un Type .NET primitif</span><span class="sxs-lookup"><span data-stu-id="7e683-133">How to Construct a Web Message Part from a Primitive .NET Type</span></span>](../core/how-to-construct-a-web-message-part-from-a-primitive-net-type.md)  
  
-   [<span data-ttu-id="7e683-134">Comment construire une partie de Message Web à partir d’un Type de schéma</span><span class="sxs-lookup"><span data-stu-id="7e683-134">How to Construct a Web Message Part from a Schema Type</span></span>](../core/how-to-construct-a-web-message-part-from-a-schema-type.md)  
  
-   [<span data-ttu-id="7e683-135">Comment construire un Message Web sans partie de Message</span><span class="sxs-lookup"><span data-stu-id="7e683-135">How to Construct a Web Message with No Message Parts</span></span>](../core/how-to-construct-a-web-message-with-no-message-parts.md)