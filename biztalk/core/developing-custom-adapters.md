---
title: "Développement d’adaptateurs personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44765fbb-b24d-43b6-a40c-d28e319b90a5
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c13aba7e378d67523ec755837ac65b26989730a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-adapters"></a><span data-ttu-id="9f520-102">Développement d'adaptateurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="9f520-102">Developing Custom Adapters</span></span>
<span data-ttu-id="9f520-103">Pour échanger des messages avec des systèmes, des applications et des entités externes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fait appel aux adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="9f520-103">To exchange messages with external systems, applications, and entities, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the concept of an adapter.</span></span> <span data-ttu-id="9f520-104">Les adaptateurs sont COM ou [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] composants qui transfèrent les messages vers et depuis la fin de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="9f520-104">Adapters are COM or [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] components that transfer messages to and from business end.</span></span> <span data-ttu-id="9f520-105">points (tels que les systèmes de fichiers, les bases de données et les applications d’entreprise personnalisées) à l’aide de divers protocoles de communication.</span><span class="sxs-lookup"><span data-stu-id="9f520-105">points (such as file systems, databases, and custom business applications) by using various communication protocols.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9f520-106">Fournit des adaptateurs natifs qui prennent en charge divers protocoles.</span><span class="sxs-lookup"><span data-stu-id="9f520-106"> provides native adapters that support various protocols.</span></span> <span data-ttu-id="9f520-107">notamment :</span><span class="sxs-lookup"><span data-stu-id="9f520-107">These include:</span></span>  
  
-   <span data-ttu-id="9f520-108">un adaptateur File qui gère l'envoi et la réception des messages depuis un emplacement File ;</span><span class="sxs-lookup"><span data-stu-id="9f520-108">A File adapter that supports sending and receiving messages from a File location</span></span>  
  
-   <span data-ttu-id="9f520-109">des adaptateurs pour les protocoles EDI, FTP, HTTP, MSMQ, SMTP, POP3 et SOAP ;</span><span class="sxs-lookup"><span data-stu-id="9f520-109">Adapters for EDI, FTP, HTTP, MSMQ, SMTP, POP3, and SOAP protocols</span></span>  
  
-   <span data-ttu-id="9f520-110">un adaptateur pour [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f520-110">An adapter for [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]</span></span>  
  
 <span data-ttu-id="9f520-111">Il peut arriver que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doive acheminer des messages vers une application personnalisée ou utiliser un protocole pour lequel aucun adaptateur natif n'est prévu.</span><span class="sxs-lookup"><span data-stu-id="9f520-111">In some cases [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may need to transport messages to a specific custom application or use a protocol for which a native adapter does not exist.</span></span> <span data-ttu-id="9f520-112">Des entreprises tierces ont élaboré des adaptateurs qui prennent en charge des protocoles supplémentaires,</span><span class="sxs-lookup"><span data-stu-id="9f520-112">Third-party companies have written adapters to support additional protocols.</span></span> <span data-ttu-id="9f520-113">et vous souhaitez peut-être savoir s'il existe un adaptateur adapté à votre protocole avant d'écrire le vôtre.</span><span class="sxs-lookup"><span data-stu-id="9f520-113">You may want to determine if there is an adapter for your protocol before deciding to write a custom adapter.</span></span> <span data-ttu-id="9f520-114">Pour obtenir la liste des adaptateurs et fournisseurs associés, consultez [http://go.microsoft.com/fwlink/?LinkId=47140](http://go.microsoft.com/fwlink/?LinkId=47140).</span><span class="sxs-lookup"><span data-stu-id="9f520-114">For a list of adapters and associated vendors see [http://go.microsoft.com/fwlink/?LinkId=47140](http://go.microsoft.com/fwlink/?LinkId=47140).</span></span> <span data-ttu-id="9f520-115">Si vous ne parvenez pas à trouver un adaptateur qui prenne en charge vos conditions de communication, il vous reste la possibilité de développer votre propre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9f520-115">If you are unable to locate an adapter to support your communication requirements, you can develop your own custom adapter.</span></span>  
  
 <span data-ttu-id="9f520-116">L'écriture d'un adaptateur personnalisé peut se révéler difficile.</span><span class="sxs-lookup"><span data-stu-id="9f520-116">Writing a custom adapter can be a challenging exercise.</span></span> <span data-ttu-id="9f520-117">Pour vous faciliter la tâche, Microsoft a développé une structure de base appelée Infrastructure d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="9f520-117">To simplify this process Microsoft has developed a foundation called the Adapter Framework.</span></span> <span data-ttu-id="9f520-118">Vous pouvez vous baser sur cette infrastructure, de même que vous pouvez utiliser l'exemple de code source fourni dans le kit SDK de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f520-118">You can use this framework as a basis for your development along with sample adapter source code in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="9f520-119">Les rubriques de cette section contiennent les conseils et les recommandations qui vous permettront de développer votre propre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9f520-119">The topics in this section present custom adapter development tips and recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f520-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9f520-120">In This Section</span></span>  
  
-   [<span data-ttu-id="9f520-121">Quelle est l’infrastructure d’adaptateurs ?</span><span class="sxs-lookup"><span data-stu-id="9f520-121">What Is the Adapter Framework?</span></span>](../core/what-is-the-adapter-framework.md)  
  
-   [<span data-ttu-id="9f520-122">Comment BizTalk Server instancie un adaptateur</span><span class="sxs-lookup"><span data-stu-id="9f520-122">How BizTalk Server Instantiates an Adapter</span></span>](../core/how-biztalk-server-instantiates-an-adapter.md)  
  
-   [<span data-ttu-id="9f520-123">Lots de messages</span><span class="sxs-lookup"><span data-stu-id="9f520-123">Message Batches</span></span>](../core/message-batches.md)  
  
-   [<span data-ttu-id="9f520-124">Lots de messages transactionnels</span><span class="sxs-lookup"><span data-stu-id="9f520-124">Transactional Message Batches</span></span>](../core/transactional-message-batches.md)  
  
-   [<span data-ttu-id="9f520-125">Développement d’un adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="9f520-125">Developing a Receive Adapter</span></span>](../core/developing-a-receive-adapter.md)  
  
-   [<span data-ttu-id="9f520-126">Développement d’un adaptateur d’envoi</span><span class="sxs-lookup"><span data-stu-id="9f520-126">Developing a Send Adapter</span></span>](../core/developing-a-send-adapter.md)  
  
-   [<span data-ttu-id="9f520-127">Instanciation d’adaptateurs isolés</span><span class="sxs-lookup"><span data-stu-id="9f520-127">Instantiating Isolated Adapters</span></span>](../core/instantiating-isolated-adapters.md)  
  
-   [<span data-ttu-id="9f520-128">Problèmes de conception de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="9f520-128">Adapter Design Issues</span></span>](../core/adapter-design-issues.md)  
  
-   [<span data-ttu-id="9f520-129">Comment les adaptateurs de traiter les Messages volumineux</span><span class="sxs-lookup"><span data-stu-id="9f520-129">How Adapters Handle Large Messages</span></span>](../core/how-adapters-handle-large-messages.md)  
  
-   [<span data-ttu-id="9f520-130">Comment gérer les défaillances d’adaptateur</span><span class="sxs-lookup"><span data-stu-id="9f520-130">How to Handle Adapter Failures</span></span>](../core/how-to-handle-adapter-failures.md)  
  
-   [<span data-ttu-id="9f520-131">Comment arrêter un adaptateur</span><span class="sxs-lookup"><span data-stu-id="9f520-131">How to Terminate an Adapter</span></span>](../core/how-to-terminate-an-adapter.md)  
  
-   [<span data-ttu-id="9f520-132">Comment concevoir un adaptateur Performant</span><span class="sxs-lookup"><span data-stu-id="9f520-132">How to Design a Performant Adapter</span></span>](../core/how-to-design-a-performant-adapter.md)  
  
-   [<span data-ttu-id="9f520-133">Comment déployer un adaptateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="9f520-133">How to Deploy a Custom Adapter</span></span>](../core/how-to-deploy-a-custom-adapter.md)  
  
-   [<span data-ttu-id="9f520-134">Comment tester et déboguer un adaptateur</span><span class="sxs-lookup"><span data-stu-id="9f520-134">How to Test and Debug an Adapter</span></span>](../core/how-to-test-and-debug-an-adapter.md)  
  
-   [<span data-ttu-id="9f520-135">Comment ajouter des métadonnées de l’adaptateur à un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="9f520-135">How to Add Adapter Metadata to a BizTalk Project</span></span>](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md)  
  
-   [<span data-ttu-id="9f520-136">Problèmes de localisation de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="9f520-136">Adapter Localization Issues</span></span>](../core/adapter-localization-issues.md)  
  
-   [<span data-ttu-id="9f520-137">Conseils pour la conception de votre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="9f520-137">Tips for Designing Your Adapter</span></span>](../core/tips-for-designing-your-adapter.md)  
  
-   [<span data-ttu-id="9f520-138">Configuration de l’adaptateur au moment du Design</span><span class="sxs-lookup"><span data-stu-id="9f520-138">Adapter Design-Time Configuration</span></span>](../core/adapter-design-time-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="9f520-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f520-139">See Also</span></span>  
 [<span data-ttu-id="9f520-140">Développement de composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="9f520-140">Developing Custom Components</span></span>](../core/developing-custom-components.md)