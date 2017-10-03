---
title: Architecture de JD Edwards OneWorld | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: architecture
ms.assetid: 9200a090-a587-4b60-9447-d281580f2078
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1daee7d44152817da1ac536dd98cbaf898e2ac7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-jd-edwards-oneworld"></a><span data-ttu-id="afb34-102">Architecture de JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="afb34-102">Architecture of JD Edwards OneWorld</span></span>
<span data-ttu-id="afb34-103">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld permet d'accéder aux fonctions commerciales de JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="afb34-103">Microsoft BizTalk Adapter for JD Edwards OneWorld provides access to JD Edwards OneWorld business functions.</span></span> <span data-ttu-id="afb34-104">JD Edwards OneWorld communique entre les ordinateurs client et serveur à l'aide d'une architecture de messagerie propriétaire nommée JDENet.</span><span class="sxs-lookup"><span data-stu-id="afb34-104">JD Edwards OneWorld communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="afb34-105">Celle-ci est implémentée par les classes de connecteur JD Edwards OneWorld figurant dans les fichiers JAR, Connector.jar et Kernel.jar.</span><span class="sxs-lookup"><span data-stu-id="afb34-105">JDENet is implemented by the JD Edwards OneWorld connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="afb34-106">La communication est implémentée à l’aide de TCP/IP comme protocole de transport, avec le port par défaut 6009 ou 6010.</span><span class="sxs-lookup"><span data-stu-id="afb34-106">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="afb34-107">Pour obtenir une description de l’emplacement où cette valeur est définie, consultez [comment définir les propriétés Transport JD Edwards OneWorld](../core/how-to-set-jd-edwards-oneworld-transport-properties.md).</span><span class="sxs-lookup"><span data-stu-id="afb34-107">For a description of where this value is set, see [How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md).</span></span>  
  
 <span data-ttu-id="afb34-108">**Architecture de l’adaptateur BizTalk pour JD Edwards OneWorld**</span><span class="sxs-lookup"><span data-stu-id="afb34-108">**Architecture for BizTalk Adapter for JD Edwards OneWorld**</span></span>  
  
 ![](../core/media/jdedadapter-01-architecture.gif "JDEdAdapter_01_Architecture")  
  
 <span data-ttu-id="afb34-109">Les appels des fonctions commerciales de JD Edwards OneWorld requièrent deux messages :</span><span class="sxs-lookup"><span data-stu-id="afb34-109">Calls to JD Edwards OneWorld business functions require two messages:</span></span>  
  
-   <span data-ttu-id="afb34-110">Le premier message répond avec l'emplacement du serveur qui traite la fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="afb34-110">The first message responds with the location of the server that processes the business function.</span></span> <span data-ttu-id="afb34-111">Cela est accompli en effectuant une recherche dans un ensemble de tables appelé *objet configuration le mappage de*.</span><span class="sxs-lookup"><span data-stu-id="afb34-111">This is accomplished by performing a lookup in a set of tables called *object configuration mapping (OCM)*.</span></span>  
  
-   <span data-ttu-id="afb34-112">Le second message envoie un tampon de message mis en forme contenant les arguments à transmettre via JD Edwards OneWorld au serveur approprié et attend une réponse.</span><span class="sxs-lookup"><span data-stu-id="afb34-112">The second message sends a formatted message buffer containing the arguments to pass to or from JD Edwards OneWorld to the appropriate server, and waits for a reply.</span></span> <span data-ttu-id="afb34-113">Les tampons sont mis en forme conformément aux définitions de type des structures C++ sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="afb34-113">The buffers are formatted according to the typedefs of the underlying C++ structs.</span></span>  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="afb34-114">Services entrants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="afb34-114">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="afb34-115">Au moment de la conception, vous créez votre port, sélectionnez l'adaptateur et fournissez les informations d'identification pour la connexion au serveur JD Edwards OneWorld cible.</span><span class="sxs-lookup"><span data-stu-id="afb34-115">At design time, you create your port, select the adapter, and provide credential information to connect to the target JD Edwards OneWorld server.</span></span> <span data-ttu-id="afb34-116">L'environnement de développement Visual Studio appelle l'infrastructure d'adaptateurs pour demander des informations de conception pour ce port.</span><span class="sxs-lookup"><span data-stu-id="afb34-116">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="afb34-117">L'adaptateur BizTalk pour JD Edwards OneWorld utilise Browsingagent pour ce port.</span><span class="sxs-lookup"><span data-stu-id="afb34-117">BizTalk Adapter for JD Edwards OneWorld uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="afb34-118">Au moment de la conception, BizTalk Server demande des informations en appelant l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="afb34-118">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="afb34-119">Browsingagent convertit la demande en code natif JD Edwards OneWorld, puis la transmet à JD Edwards OneWorld via la connexion API ThinNet (établie dans Connector.jar et Kernel.jar).</span><span class="sxs-lookup"><span data-stu-id="afb34-119">The Browsingagent converts the request into native JD Edwards OneWorld code and then transmits the requests to JD Edwards OneWorld through the ThinNet API connection (established in the Connector and Kernel.jars).</span></span>  
  
-   <span data-ttu-id="afb34-120">Une fonction commerciale personnalisée est installée via l’installation BTSREL : il expose les principales fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="afb34-120">A custom business function is installed through the BTSREL installation: it exposes the master business functions.</span></span>  
  
-   <span data-ttu-id="afb34-121">La liste des modules de JD Edwards OneWorld est initialement renvoyée et transportée vers Visual Studio, dans lequel elle renseigne l'Assistant Adaptateur.</span><span class="sxs-lookup"><span data-stu-id="afb34-121">A list of modules in JD Edwards OneWorld is initially returned and transported to Visual Studio, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="afb34-122">Vous pouvez développer la hiérarchie pour afficher le nom de la bibliothèque et le nom du module.</span><span class="sxs-lookup"><span data-stu-id="afb34-122">You can expand the hierarchy to display the library name and module name.</span></span>  
  
-   <span data-ttu-id="afb34-123">Lorsque vous sélectionnez un module spécifique, des schémas pour toutes les fonctions de ce module s'affichent.</span><span class="sxs-lookup"><span data-stu-id="afb34-123">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="afb34-124">L'adaptateur obtient les informations requises auprès de JD Edwards OneWorld, et Browsingagent crée les schémas.</span><span class="sxs-lookup"><span data-stu-id="afb34-124">The adapter obtains the required information from JD Edwards OneWorld, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="afb34-125">Les schémas sont ajoutés à l'orchestration du projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="afb34-125">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="afb34-126">Services entrants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="afb34-126">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="afb34-127">BizTalk Server appelle l'adaptateur BizTalk pour JD Edwards OneWorld pour envoyer un message sur un port spécifique.</span><span class="sxs-lookup"><span data-stu-id="afb34-127">BizTalk Server calls the BizTalk Adapter for JD Edwards OneWorld to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="afb34-128">L'agent d'exécution convertit le code XML en code JD Edwards natif.</span><span class="sxs-lookup"><span data-stu-id="afb34-128">The run-time agent converts the XML into native JD Edwards code.</span></span>  
  
-   <span data-ttu-id="afb34-129">L'agent d'exécution envoie la demande via ThinNet au système d'entreprise JD Edwards spécifié dans les propriétés de transport du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="afb34-129">The run-time agent submits the request through the ThinNet to the JD Edwards enterprise system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="afb34-130">La fonction commerciale principale est exécutée sur le système JD Edwards, qui génère ensuite un document de réponse, lequel indique si l'opération a réussi ou échoué, ainsi que les paramètres de données renvoyés par la fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="afb34-130">The master business function is executed on the JD Edwards system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="afb34-131">Le message envoyé à JD Edwards OneWorld constitue une architecture à message unique et à réponse unique.</span><span class="sxs-lookup"><span data-stu-id="afb34-131">The message sent to JD Edwards OneWorld is a single message, single reply architecture.</span></span> <span data-ttu-id="afb34-132">Il est impossible de traiter plusieurs messages simultanément.</span><span class="sxs-lookup"><span data-stu-id="afb34-132">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="afb34-133">Le document de réponse est renvoyé via ThinNet, converti au format XML et retransmis à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="afb34-133">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="afb34-134">Événements sortants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="afb34-134">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="afb34-135">Aucune création systématique de métadonnées d'événement n'est disponible.</span><span class="sxs-lookup"><span data-stu-id="afb34-135">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="afb34-136">Une télécopie du document d'événements doit être fournie à Visual Studio afin qu'un schéma puisse être généré et incorporé au projet avec l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="afb34-136">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="afb34-137">Événements sortants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="afb34-137">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="afb34-138">Un mécanisme de transport de fichier est mis en place dans le serveur d'entreprise JD Edwards pour transporter le document XML résultant de l'opération, déclenché par la fin de l'événement, vers le répertoire cible de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="afb34-138">A file transport mechanism is established in the JD Edwards enterprise server to transport the resulting XML document, triggered by the event completion, to the target directory on that server.</span></span>  
  
-   <span data-ttu-id="afb34-139">L'ordinateur BizTalk Server possède un lecteur mappé au répertoire figurant sur le serveur d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="afb34-139">The BizTalk Server computer has a mapped drive to the directory on the enterprise server.</span></span>  
  
-   <span data-ttu-id="afb34-140">Les propriétés de transport du port de réception sont configurées pour le lecteur mappé.</span><span class="sxs-lookup"><span data-stu-id="afb34-140">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="afb34-141">Le port de réception reçoit les messages envoyés au répertoire par le serveur d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="afb34-141">The receive port receives messages posted to directory by the enterprise server.</span></span>  
  
-   <span data-ttu-id="afb34-142">L'identification de l'espace de noms permet de s'assurer que les messages appropriés sont acheminés vers le port de réception configuré.</span><span class="sxs-lookup"><span data-stu-id="afb34-142">The target namespace identification ensures that the correct messages are routed to the configured receive port.</span></span>  
  
-   <span data-ttu-id="afb34-143">Le port de réception envoie le document XML à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="afb34-143">The receive port submits the XML document to BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb34-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb34-144">See Also</span></span>  
 <span data-ttu-id="afb34-145">[Comment définir les propriétés de JD Edwards OneWorld Transport](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span><span class="sxs-lookup"><span data-stu-id="afb34-145">[How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span></span>  
 [<span data-ttu-id="afb34-146">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="afb34-146">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)