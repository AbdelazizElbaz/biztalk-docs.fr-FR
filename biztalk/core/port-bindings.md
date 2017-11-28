---
title: Liaisons de port | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, warnings
- ports, bindings
- bindings, Web ports
- bindings, design time
- Web ports, port bindings
- bindings, ports
- bindings, direct
- bindings, warnings
- bindings, deployment
- bindings, dynamic
ms.assetid: b61c725a-0082-42d3-b88a-533583161734
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 943cbbaa6db9413ffad15bfcf3302d2216e3ab17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="port-bindings"></a><span data-ttu-id="e019b-102">Liaisons de port</span><span class="sxs-lookup"><span data-stu-id="e019b-102">Port Bindings</span></span>
<span data-ttu-id="e019b-103">Une liaison de port représente les informations de configuration permettant de déterminer comment et où un message sera envoyé ou reçu.</span><span class="sxs-lookup"><span data-stu-id="e019b-103">A port binding is the configuration information that determines where and how a message will be sent or received.</span></span> <span data-ttu-id="e019b-104">Selon son type, une liaison de port peut faire référence à des emplacements physiques, pipelines ou autres orchestrations.</span><span class="sxs-lookup"><span data-stu-id="e019b-104">Depending on its type, a port binding might refer to physical locations, pipelines, or other orchestrations.</span></span>  
  
 <span data-ttu-id="e019b-105">Il existe trois types de liaison de port pour les ports de réception des messages :</span><span class="sxs-lookup"><span data-stu-id="e019b-105">There are three types of port binding for ports that receive messages:</span></span>  
  
-   <span data-ttu-id="e019b-106">Spécifier maintenant</span><span class="sxs-lookup"><span data-stu-id="e019b-106">Specify now</span></span>  
  
-   <span data-ttu-id="e019b-107">Spécifier plus tard</span><span class="sxs-lookup"><span data-stu-id="e019b-107">Specify later</span></span>  
  
-   <span data-ttu-id="e019b-108">Direct</span><span class="sxs-lookup"><span data-stu-id="e019b-108">Direct</span></span>  
  
 <span data-ttu-id="e019b-109">Il existe quatre types de liaison de port pour les ports d'envoi de message :</span><span class="sxs-lookup"><span data-stu-id="e019b-109">There are four types of port binding for ports that send messages:</span></span>  
  
-   <span data-ttu-id="e019b-110">Spécifier maintenant</span><span class="sxs-lookup"><span data-stu-id="e019b-110">Specify now</span></span>  
  
-   <span data-ttu-id="e019b-111">Spécifier plus tard</span><span class="sxs-lookup"><span data-stu-id="e019b-111">Specify later</span></span>  
  
-   <span data-ttu-id="e019b-112">Direct</span><span class="sxs-lookup"><span data-stu-id="e019b-112">Direct</span></span>  
  
-   <span data-ttu-id="e019b-113">Dynamique</span><span class="sxs-lookup"><span data-stu-id="e019b-113">Dynamic</span></span>  
  
## <a name="binding-at-deployment-time"></a><span data-ttu-id="e019b-114">Liaison lors du déploiement</span><span class="sxs-lookup"><span data-stu-id="e019b-114">Binding at Deployment Time</span></span>  
 <span data-ttu-id="e019b-115">Vous pouvez lier votre port à un emplacement de réception ou à un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="e019b-115">You can bind your port to a receive location or to a send port.</span></span> <span data-ttu-id="e019b-116">Si vous n’avez pas toutes les informations que vous devez spécifier un emplacement physique, vous pouvez sélectionner le **spécifier plus tard** option de liaison de port dans le Concepteur d’Orchestration et vous devez uniquement spécifier le type de port qui décrit le port.</span><span class="sxs-lookup"><span data-stu-id="e019b-116">If you do not have all of the information you need to specify a physical location, you can select the **Specify later** port binding option in Orchestration Designer, and you only need to specify the port type that describes the port.</span></span> <span data-ttu-id="e019b-117">Une fois l'application déployée, vous pouvez indiquer les informations relatives à l'emplacement à l'aide de la console Administration de BizTalk Server ou d'un programme.</span><span class="sxs-lookup"><span data-stu-id="e019b-117">After the application has been deployed, you can specify information about the location by using the BizTalk Server Administration console, or you can configure the location information programmatically.</span></span>  
  
## <a name="binding-at-design-time"></a><span data-ttu-id="e019b-118">Liaison lors de la conception</span><span class="sxs-lookup"><span data-stu-id="e019b-118">Binding at Design Time</span></span>  
 <span data-ttu-id="e019b-119">Vous pouvez sélectionner le **spécifier maintenant** option de liaison dans le Concepteur d’Orchestration pour spécifier le transport et le pipeline au moment du design de port.</span><span class="sxs-lookup"><span data-stu-id="e019b-119">You can select the **Specify now** port binding option in Orchestration Designer to specify the transport and pipeline at design time.</span></span> <span data-ttu-id="e019b-120">Lorsque vous spécifiez le port de réception des messages, seuls les transports HTTP, SOAP et FILE sont disponibles dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e019b-120">When specifying the port for receiving messages, only HTTP, SOAP, and FILE transports are available from the drop-down list.</span></span> <span data-ttu-id="e019b-121">Lorsque vous spécifiez le port d'envoi des messages, seuls les transports HTTP, FILE et SMTP sont disponibles dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e019b-121">When specifying the port for sending messages, only HTTP, FILE, and SMTP transports are available from the drop-down list.</span></span> <span data-ttu-id="e019b-122">Cette option est pratique si vous connaissez à l'avance la source ou la destination des messages transmis.</span><span class="sxs-lookup"><span data-stu-id="e019b-122">This option is useful if you know in advance the source or destination of transmitted messages.</span></span>  
  
## <a name="direct-binding"></a><span data-ttu-id="e019b-123">Liaison directe</span><span class="sxs-lookup"><span data-stu-id="e019b-123">Direct Binding</span></span>  
 <span data-ttu-id="e019b-124">Les ports à liaison directe sont des ports logiques unidirectionnels ou bidirectionnels de vos orchestrations qui ne sont pas liés explicitement à des ports physiques.</span><span class="sxs-lookup"><span data-stu-id="e019b-124">Direct bound ports are logical one-way or two-way ports in your orchestrations that are not explicitly bound to any physical ports.</span></span> <span data-ttu-id="e019b-125">Ils vous permettent de disposer de différents modèles de communication dans vos services.</span><span class="sxs-lookup"><span data-stu-id="e019b-125">Direct bound ports allow you to have different communication patterns among your services.</span></span> <span data-ttu-id="e019b-126">Pour implémenter la liaison directe, sélectionnez le **Direct** option de liaison dans le Concepteur d’Orchestration au moment du design de port.</span><span class="sxs-lookup"><span data-stu-id="e019b-126">To implement direct binding, select the **Direct** port binding option in Orchestration Designer at design time.</span></span>  
  
 <span data-ttu-id="e019b-127">Il existe trois types de ports à liaison directe :</span><span class="sxs-lookup"><span data-stu-id="e019b-127">There are three types of direct bound ports:</span></span>  
  
-   <span data-ttu-id="e019b-128">Port à liaison directe MessageBox</span><span class="sxs-lookup"><span data-stu-id="e019b-128">MessageBox direct bound port</span></span>  
  
-   <span data-ttu-id="e019b-129">Port d'autocorrélation à liaison directe</span><span class="sxs-lookup"><span data-stu-id="e019b-129">Self-correlating direct bound port</span></span>  
  
-   <span data-ttu-id="e019b-130">Port à liaison directe d'orchestration partenaire</span><span class="sxs-lookup"><span data-stu-id="e019b-130">Partner orchestration direct bound port</span></span>  
  
 <span data-ttu-id="e019b-131">Pour plus d’informations sur l’utilisation des ports à liaison directe, consultez [utilisation de Ports à liaison directe dans les Orchestrations](../core/working-with-direct-bound-ports-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="e019b-131">For more information about how to work with direct bound ports, see [Working with Direct Bound Ports in Orchestrations](../core/working-with-direct-bound-ports-in-orchestrations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e019b-132">Lorsque vous utilisez la liaison directe, vous ne pouvez pas échanger de messages entre un port requête-réponse et deux ports unidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="e019b-132">When you use direct binding, you cannot exchange messages between one request-response port and two one-way ports.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e019b-133">La liaison directe n'est pas compatible avec les normes du Business Process Engineering Language for Web Services (BPEL4WS).</span><span class="sxs-lookup"><span data-stu-id="e019b-133">Direct binding is not compliant with the standards of the Business Process Engineering Language for Web Services (BPEL4WS).</span></span> <span data-ttu-id="e019b-134">Si vous requérez la conformité avec BPEL4WS, utilisez un autre type de liaison.</span><span class="sxs-lookup"><span data-stu-id="e019b-134">If you require BPEL4WS compliance, use another kind of binding.</span></span>  
  
## <a name="dynamic-binding"></a><span data-ttu-id="e019b-135">Liaison dynamique</span><span class="sxs-lookup"><span data-stu-id="e019b-135">Dynamic Binding</span></span>  
 <span data-ttu-id="e019b-136">Dans les cas où la destination de la communication restera inconnue jusqu'à l'exécution, vous pouvez utiliser la liaison dynamique pour un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="e019b-136">If you will not know the destination of a communication until run time, you can use dynamic binding for a send port.</span></span> <span data-ttu-id="e019b-137">L’emplacement peut, par exemple, être déterminée à partir d’une propriété d’un message entrant et ensuite spécifié dans le **Expression** mettre en forme, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e019b-137">The location might, for example, be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following code:</span></span>  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
```  
  
 <span data-ttu-id="e019b-138">Pour plus d’informations sur la façon d’affecter dynamiquement des valeurs à des ports, consultez [comment affecter des valeurs à des Ports dynamiques](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md).</span><span class="sxs-lookup"><span data-stu-id="e019b-138">For information about how to dynamically assign values to ports, see [How to Assign Values to Dynamic Ports](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md).</span></span>  
  
## <a name="web-ports"></a><span data-ttu-id="e019b-139">Ports Web</span><span class="sxs-lookup"><span data-stu-id="e019b-139">Web Ports</span></span>  
 <span data-ttu-id="e019b-140">Si votre projet contient une référence à un service Web, le Concepteur d'orchestration la détectera et rendra disponible un type de port Web correspondant.</span><span class="sxs-lookup"><span data-stu-id="e019b-140">If your project contains a reference to a Web service, Orchestration Designer will detect it and will make available a corresponding Web port type.</span></span> <span data-ttu-id="e019b-141">Pour créer un port Web, ajoutez simplement un port à votre orchestration et affectez-lui un type de port Web existant.</span><span class="sxs-lookup"><span data-stu-id="e019b-141">To create a Web port, you simply add a port to your orchestration and assign it an existing Web port type.</span></span> <span data-ttu-id="e019b-142">Pour plus d’informations, consultez [création de Ports Web](../core/creating-web-ports.md).</span><span class="sxs-lookup"><span data-stu-id="e019b-142">For more information, see [Creating Web Ports](../core/creating-web-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e019b-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e019b-143">See Also</span></span>  
 <span data-ttu-id="e019b-144">[L’utilisation des Types de ports](../core/how-to-work-with-port-types.md) </span><span class="sxs-lookup"><span data-stu-id="e019b-144">[How to Work with Port Types](../core/how-to-work-with-port-types.md) </span></span>  
 <span data-ttu-id="e019b-145">[Modèle de communication](../core/communication-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="e019b-145">[Communication Pattern](../core/communication-pattern.md) </span></span>  
 <span data-ttu-id="e019b-146">[Direction de communication](../core/communication-direction.md) </span><span class="sxs-lookup"><span data-stu-id="e019b-146">[Communication Direction](../core/communication-direction.md) </span></span>  
 <span data-ttu-id="e019b-147">[L’utilisation de Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="e019b-147">[Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md) </span></span>  
 <span data-ttu-id="e019b-148">[Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e019b-148">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="e019b-149">Utilisation de Services Web</span><span class="sxs-lookup"><span data-stu-id="e019b-149">Consuming Web Services</span></span>](../core/consuming-web-services.md)