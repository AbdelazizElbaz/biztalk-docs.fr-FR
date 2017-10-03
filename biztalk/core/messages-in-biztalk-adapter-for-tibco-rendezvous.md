---
title: "Messages de l’adaptateur BizTalk pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- TIBCO Rendezvous
- messages
- message passing
- messages, passing
ms.assetid: 12699550-22e7-4a11-a024-2302570970af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4bc1eadbefdeb5c59df9a1b999ffdd3e530587a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-in-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="6b65d-102">Messages dans l'adaptateur BizTalk pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="6b65d-102">Messages in BizTalk Adapter for TIBCO Rendezvous</span></span>
<span data-ttu-id="6b65d-103">L'adaptateur BizTalk pour TIBCO Rendezvous assure la connectivité bidirectionnelle entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="6b65d-103">BizTalk Adapter for TIBCO Rendezvous provides bi-directional connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and TIBCO Rendezvous.</span></span> <span data-ttu-id="6b65d-104">Il utilise l'API TIBCO Rendezvous et l'API d'infrastructure d'adaptateurs BizTalk pour offrir une intégration étroite.</span><span class="sxs-lookup"><span data-stu-id="6b65d-104">This adapter uses both the TIBCO Rendezvous API and the BizTalk Adapter Framework API to provide tight integration.</span></span>  
  
## <a name="about-tibco-rendezvous"></a><span data-ttu-id="6b65d-105">À propos de TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="6b65d-105">About TIBCO Rendezvous</span></span>  
 <span data-ttu-id="6b65d-106">TIBCO Rendezvous est un logiciel qui inclut un bus de messages pour l'intégration des applications d'entreprise (IAE).</span><span class="sxs-lookup"><span data-stu-id="6b65d-106">TIBCO Rendezvous is a software product that provides a message bus for enterprise application integration (EAI).</span></span> <span data-ttu-id="6b65d-107">Il inclut des API de messagerie en C, C++, Java, Visual Basic et pour Microsoft .NET Framework recevoir des flux de données sur des feuilles de calcul Microsoft Office Excel et d’autres applications de choix.</span><span class="sxs-lookup"><span data-stu-id="6b65d-107">TIBCO provides messaging APIs in C, C++, Java, Visual Basic and for the Microsoft .NET Framework to receive data feeds on Microsoft Office Excel worksheets and other applications of choice.</span></span> <span data-ttu-id="6b65d-108">Pour plus d’informations, consultez [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="6b65d-108">For more information, see [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md).</span></span>  
  
### <a name="message-passing"></a><span data-ttu-id="6b65d-109">Transmission de messages</span><span class="sxs-lookup"><span data-stu-id="6b65d-109">Message Passing</span></span>  
 <span data-ttu-id="6b65d-110">Le concept de base de la transmission de messages est relativement simple :</span><span class="sxs-lookup"><span data-stu-id="6b65d-110">The basic concept of message passing is fairly simple:</span></span>  
  
-   <span data-ttu-id="6b65d-111">Un message inclut un sujet unique constitué d'éléments séparés par des points.</span><span class="sxs-lookup"><span data-stu-id="6b65d-111">A message has a single subject composed of elements separated by periods.</span></span> <span data-ttu-id="6b65d-112">Un message est envoyé à un démon Rendezvous (même s'il peut être transmis à d'autres démons).</span><span class="sxs-lookup"><span data-stu-id="6b65d-112">A message is sent to a single Rendezvous daemon, although it might eventually be broadcast onto other daemons.</span></span>  
  
-   <span data-ttu-id="6b65d-113">Un port d'écoute annonce ses sujets d'intérêt à un démon (à l'aide d'une fonction de caractère générique de base).</span><span class="sxs-lookup"><span data-stu-id="6b65d-113">A listener announces its subjects of interest to a daemon (with a basic wildcard facility).</span></span> <span data-ttu-id="6b65d-114">Les messages ayant des sujets correspondants lui sont remis si les deux démons sont connectés ou correspondent au même démon.</span><span class="sxs-lookup"><span data-stu-id="6b65d-114">Messages that have matching subjects are delivered to it if the two daemons are connected to each other, or are indeed the same daemon.</span></span>  
  
 <span data-ttu-id="6b65d-115">Des fonctionnalités pour l'entreprise peuvent être superposées à celle-ci (options Tolérance de panne/Fiable ou Certifié possibles), toutes implémentées via les messages de base sous-jacents.</span><span class="sxs-lookup"><span data-stu-id="6b65d-115">Significant "Enterprise" functionality is layered onto this if desired--with Fault Tolerance/Reliable or Certified options possible--all implemented through the underlying basic messages.</span></span>  
  
 <span data-ttu-id="6b65d-116">Les messages eux-mêmes peuvent être affichés comme champs nom/valeur ou nombre/valeur entrés (les deux mécanismes d'identification dans un message peuvent être combinés avec certaines restrictions).</span><span class="sxs-lookup"><span data-stu-id="6b65d-116">The messages themselves can be viewed as typed name-value fields or number-value fields (the two identification mechanisms in a message can mix and match with certain restrictions).</span></span> <span data-ttu-id="6b65d-117">Un message peut contenir des sous-messages, qui peuvent eux-mêmes contenir des sous-messages.</span><span class="sxs-lookup"><span data-stu-id="6b65d-117">A message itself can contain sub-messages, which can contain sub-messages.</span></span>  
  
 <span data-ttu-id="6b65d-118">Les noms de sujet sont constitués d'un ou plusieurs éléments séparés par des points.</span><span class="sxs-lookup"><span data-stu-id="6b65d-118">Subject names consist of one or more elements separated by dot characters (periods).</span></span> <span data-ttu-id="6b65d-119">Les éléments implémentent une hiérarchie de noms de sujet qui reflète la structure des informations dans un système d'application.</span><span class="sxs-lookup"><span data-stu-id="6b65d-119">The elements implement a subject name hierarchy that reflects the structure of information in an application system.</span></span> <span data-ttu-id="6b65d-120">Les chaînes suivantes sont des exemples de noms de sujet valides :</span><span class="sxs-lookup"><span data-stu-id="6b65d-120">The following strings are examples of valid subject names:</span></span>  
  
-   <span data-ttu-id="6b65d-121">RUN.HOME</span><span class="sxs-lookup"><span data-stu-id="6b65d-121">RUN.HOME</span></span>  
  
-   <span data-ttu-id="6b65d-122">RUN.for.Elected_Office</span><span class="sxs-lookup"><span data-stu-id="6b65d-122">RUN.for.Elected_Office</span></span>  
  
 <span data-ttu-id="6b65d-123">L'adaptateur BizTalk pour TIBCO Rendezvous utilise le Kit de développement logiciel (SDK) TIBCO Rendezvous pour publier des messages dans les sujets TIBCO Rendezvous et s'inscrire à des événements TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="6b65d-123">BizTalk Adapter for TIBCO Rendezvous uses the TIBCO Rendezvous SDK to publish messages to TIBCO Rendezvous subjects and to register for TIBCO Rendezvous events.</span></span> <span data-ttu-id="6b65d-124">Les classes associées à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont hébergées sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b65d-124">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related classes are hosted in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span> <span data-ttu-id="6b65d-125">Un processus distinct (agent d'exécution) est démarré et agit comme programme Rendezvous. L'accès à distance .NET Framework permet l'échange de messages entre les deux.</span><span class="sxs-lookup"><span data-stu-id="6b65d-125">A separate process (run-time agent) is started and acts as the Rendezvous program, and .NET Framework remoting is used to exchange messages between the two.</span></span>  
  
-   <span data-ttu-id="6b65d-126">Les messages des niveaux Informations, Avertissement et Erreur sont envoyés au journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="6b65d-126">Info-Level, Warning-Level, and Error-level messages are sent to the Windows event log.</span></span>  
  
-   <span data-ttu-id="6b65d-127">Tous les niveaux de message, y compris les messages de niveau Débogage, sont envoyés au journal des suivis Windows.</span><span class="sxs-lookup"><span data-stu-id="6b65d-127">All levels, including Debug-level messages, are sent to the Windows Tracing Log.</span></span>  
  
#### <a name="transmitter"></a><span data-ttu-id="6b65d-128">Émetteur</span><span class="sxs-lookup"><span data-stu-id="6b65d-128">Transmitter</span></span>  
 <span data-ttu-id="6b65d-129">L'adaptateur BizTalk pour TIBCO Rendezvous lance un agent d'exécution par port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="6b65d-129">BizTalk Adapter for TIBCO Rendezvous launches one run-time agent per send port.</span></span> <span data-ttu-id="6b65d-130">L'API .NET Framework TIBCO Rendezvous permet uniquement de définir le codage des caractères sur une étendue globale.</span><span class="sxs-lookup"><span data-stu-id="6b65d-130">The TIBCO Rendezvous .NET Framework API only allows setting character encoding at a global scope.</span></span> <span data-ttu-id="6b65d-131">Aussi, l'une des options de configuration des ports est un numéro de page de codes.</span><span class="sxs-lookup"><span data-stu-id="6b65d-131">Therefore, one of the port configuration options is a code page number.</span></span> <span data-ttu-id="6b65d-132">En démarrant un autre processus pour chaque page de codes, l'adaptateur offre une prise en charge optimisée de la globalisation.</span><span class="sxs-lookup"><span data-stu-id="6b65d-132">By starting a different process for each code page, the adapter can provide better support for globalization.</span></span>  
  
#### <a name="receiver"></a><span data-ttu-id="6b65d-133">Récepteur</span><span class="sxs-lookup"><span data-stu-id="6b65d-133">Receiver</span></span>  
 <span data-ttu-id="6b65d-134">L'adaptateur BizTalk pour TIBCO Rendezvous lance un agent d'exécution par emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="6b65d-134">BizTalk Adapter for TIBCO Rendezvous launches one run-time agent per receive location.</span></span>  
  
#### <a name="transactions"></a><span data-ttu-id="6b65d-135">Transactions</span><span class="sxs-lookup"><span data-stu-id="6b65d-135">Transactions</span></span>  
 <span data-ttu-id="6b65d-136">Le produit TIBCO Rendezvous n'est pas transactionnel.</span><span class="sxs-lookup"><span data-stu-id="6b65d-136">The TIBCO Rendezvous product is not transactional.</span></span> <span data-ttu-id="6b65d-137">Un produit distinct, TIBCO Rendezvous TX, est requis.</span><span class="sxs-lookup"><span data-stu-id="6b65d-137">A separate product, TIBCO Rendezvous TX, is required.</span></span> <span data-ttu-id="6b65d-138">Cette version de l'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="6b65d-138">BizTalk Adapter for TIBCO Rendezvous does not support transactions in this release.</span></span>  
  
#### <a name="security"></a><span data-ttu-id="6b65d-139">Sécurité</span><span class="sxs-lookup"><span data-stu-id="6b65d-139">Security</span></span>  
 <span data-ttu-id="6b65d-140">TIBCO Rendezvous prend uniquement en charge l'authentification entre les programmes et démons TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="6b65d-140">TIBCO Rendezvous only supports authentication between TIBCO Rendezvous programs and daemons.</span></span> <span data-ttu-id="6b65d-141">Il n'utilise pas l'autorisation ou le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6b65d-141">It does not perform authorization or encryption.</span></span> <span data-ttu-id="6b65d-142">Un produit distinct, TIBCO Rendezvous DataSecurity, est requis.</span><span class="sxs-lookup"><span data-stu-id="6b65d-142">A separate product, TIBCO Rendezvous DataSecurity, is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b65d-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b65d-143">See Also</span></span>  
 <span data-ttu-id="6b65d-144">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="6b65d-144">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="6b65d-145">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="6b65d-145">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)