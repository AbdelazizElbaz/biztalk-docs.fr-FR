---
title: Architecture de JD Edwards OneWorld | Documents Microsoft
description: "Décrit les services entrants au moment du design et moment de l’exécution, les événements sortants au moment du design et le moment de l’exécution dans l’adaptateur JD Edwards OneWorld dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9200a090-a587-4b60-9447-d281580f2078
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f866e5d72e392136d19c155785aaf6b71db2ce3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-jd-edwards-oneworld"></a><span data-ttu-id="41eaa-103">Architecture de JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="41eaa-103">Architecture of JD Edwards OneWorld</span></span>
<span data-ttu-id="41eaa-104">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld permet d'accéder aux fonctions commerciales de JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="41eaa-104">Microsoft BizTalk Adapter for JD Edwards OneWorld provides access to JD Edwards OneWorld business functions.</span></span> <span data-ttu-id="41eaa-105">JD Edwards OneWorld communique entre les ordinateurs client et serveur à l'aide d'une architecture de messagerie propriétaire nommée JDENet.</span><span class="sxs-lookup"><span data-stu-id="41eaa-105">JD Edwards OneWorld communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="41eaa-106">Celle-ci est implémentée par les classes de connecteur JD Edwards OneWorld figurant dans les fichiers JAR, Connector.jar et Kernel.jar.</span><span class="sxs-lookup"><span data-stu-id="41eaa-106">JDENet is implemented by the JD Edwards OneWorld connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="41eaa-107">La communication est implémentée à l’aide de TCP/IP comme protocole de transport, avec le port par défaut 6009 ou 6010.</span><span class="sxs-lookup"><span data-stu-id="41eaa-107">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="41eaa-108">Pour obtenir une description de l’emplacement où cette valeur est définie, consultez [ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md).</span><span class="sxs-lookup"><span data-stu-id="41eaa-108">For a description of where this value is set, see [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md).</span></span>  
  
 <span data-ttu-id="41eaa-109">**Architecture de l’adaptateur BizTalk pour JD Edwards OneWorld**</span><span class="sxs-lookup"><span data-stu-id="41eaa-109">**Architecture for BizTalk Adapter for JD Edwards OneWorld**</span></span>  
  
 ![](../core/media/jdedadapter-01-architecture.gif "JDEdAdapter_01_Architecture")  
  
 <span data-ttu-id="41eaa-110">Les appels des fonctions commerciales de JD Edwards OneWorld requièrent deux messages :</span><span class="sxs-lookup"><span data-stu-id="41eaa-110">Calls to JD Edwards OneWorld business functions require two messages:</span></span>  
  
-   <span data-ttu-id="41eaa-111">Le premier message répond avec l'emplacement du serveur qui traite la fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="41eaa-111">The first message responds with the location of the server that processes the business function.</span></span> <span data-ttu-id="41eaa-112">Cela est accompli en effectuant une recherche dans un ensemble de tables appelé *objet configuration le mappage de*.</span><span class="sxs-lookup"><span data-stu-id="41eaa-112">This is accomplished by performing a lookup in a set of tables called *object configuration mapping (OCM)*.</span></span>  
  
-   <span data-ttu-id="41eaa-113">Le second message envoie un tampon de message mis en forme contenant les arguments à transmettre via JD Edwards OneWorld au serveur approprié et attend une réponse.</span><span class="sxs-lookup"><span data-stu-id="41eaa-113">The second message sends a formatted message buffer containing the arguments to pass to or from JD Edwards OneWorld to the appropriate server, and waits for a reply.</span></span> <span data-ttu-id="41eaa-114">Les tampons sont mis en forme conformément aux définitions de type des structures C++ sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="41eaa-114">The buffers are formatted according to the typedefs of the underlying C++ structs.</span></span>  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="41eaa-115">Services entrants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="41eaa-115">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="41eaa-116">Au moment de la conception, vous créez votre port, sélectionnez l'adaptateur et fournissez les informations d'identification pour la connexion au serveur JD Edwards OneWorld cible.</span><span class="sxs-lookup"><span data-stu-id="41eaa-116">At design time, you create your port, select the adapter, and provide credential information to connect to the target JD Edwards OneWorld server.</span></span> <span data-ttu-id="41eaa-117">L'environnement de développement Visual Studio appelle l'infrastructure d'adaptateurs pour demander des informations de conception pour ce port.</span><span class="sxs-lookup"><span data-stu-id="41eaa-117">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="41eaa-118">L'adaptateur BizTalk pour JD Edwards OneWorld utilise Browsingagent pour ce port.</span><span class="sxs-lookup"><span data-stu-id="41eaa-118">BizTalk Adapter for JD Edwards OneWorld uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="41eaa-119">Au moment de la conception, BizTalk Server demande des informations en appelant l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="41eaa-119">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="41eaa-120">Browsingagent convertit la demande en code natif JD Edwards OneWorld, puis la transmet à JD Edwards OneWorld via la connexion API ThinNet (établie dans Connector.jar et Kernel.jar).</span><span class="sxs-lookup"><span data-stu-id="41eaa-120">The Browsingagent converts the request into native JD Edwards OneWorld code and then transmits the requests to JD Edwards OneWorld through the ThinNet API connection (established in the Connector and Kernel.jars).</span></span>  
  
-   <span data-ttu-id="41eaa-121">Une fonction commerciale personnalisée est installée via l’installation BTSREL : il expose les principales fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="41eaa-121">A custom business function is installed through the BTSREL installation: it exposes the master business functions.</span></span>  
  
-   <span data-ttu-id="41eaa-122">La liste des modules de JD Edwards OneWorld est initialement renvoyée et transportée vers Visual Studio, dans lequel elle renseigne l'Assistant Adaptateur.</span><span class="sxs-lookup"><span data-stu-id="41eaa-122">A list of modules in JD Edwards OneWorld is initially returned and transported to Visual Studio, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="41eaa-123">Vous pouvez développer la hiérarchie pour afficher le nom de la bibliothèque et le nom du module.</span><span class="sxs-lookup"><span data-stu-id="41eaa-123">You can expand the hierarchy to display the library name and module name.</span></span>  
  
-   <span data-ttu-id="41eaa-124">Lorsque vous sélectionnez un module spécifique, des schémas pour toutes les fonctions de ce module s'affichent.</span><span class="sxs-lookup"><span data-stu-id="41eaa-124">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="41eaa-125">L'adaptateur obtient les informations requises auprès de JD Edwards OneWorld, et Browsingagent crée les schémas.</span><span class="sxs-lookup"><span data-stu-id="41eaa-125">The adapter obtains the required information from JD Edwards OneWorld, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="41eaa-126">Les schémas sont ajoutés à l'orchestration du projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="41eaa-126">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="41eaa-127">Services entrants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="41eaa-127">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="41eaa-128">BizTalk Server appelle l'adaptateur BizTalk pour JD Edwards OneWorld pour envoyer un message sur un port spécifique.</span><span class="sxs-lookup"><span data-stu-id="41eaa-128">BizTalk Server calls the BizTalk Adapter for JD Edwards OneWorld to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="41eaa-129">L'agent d'exécution convertit le code XML en code JD Edwards natif.</span><span class="sxs-lookup"><span data-stu-id="41eaa-129">The run-time agent converts the XML into native JD Edwards code.</span></span>  
  
-   <span data-ttu-id="41eaa-130">L'agent d'exécution envoie la demande via ThinNet au système d'entreprise JD Edwards spécifié dans les propriétés de transport du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="41eaa-130">The run-time agent submits the request through the ThinNet to the JD Edwards enterprise system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="41eaa-131">La fonction commerciale principale est exécutée sur le système JD Edwards, qui génère ensuite un document de réponse, lequel indique si l'opération a réussi ou échoué, ainsi que les paramètres de données renvoyés par la fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="41eaa-131">The master business function is executed on the JD Edwards system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="41eaa-132">Le message envoyé à JD Edwards OneWorld constitue une architecture à message unique et à réponse unique.</span><span class="sxs-lookup"><span data-stu-id="41eaa-132">The message sent to JD Edwards OneWorld is a single message, single reply architecture.</span></span> <span data-ttu-id="41eaa-133">Il est impossible de traiter plusieurs messages simultanément.</span><span class="sxs-lookup"><span data-stu-id="41eaa-133">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="41eaa-134">Le document de réponse est renvoyé via ThinNet, converti au format XML et retransmis à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="41eaa-134">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="41eaa-135">Événements sortants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="41eaa-135">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="41eaa-136">Aucune création systématique de métadonnées d'événement n'est disponible.</span><span class="sxs-lookup"><span data-stu-id="41eaa-136">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="41eaa-137">Une télécopie du document d'événements doit être fournie à Visual Studio afin qu'un schéma puisse être généré et incorporé au projet avec l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="41eaa-137">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="41eaa-138">Événements sortants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="41eaa-138">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="41eaa-139">Un mécanisme de transport de fichier est mis en place dans le serveur d'entreprise JD Edwards pour transporter le document XML résultant de l'opération, déclenché par la fin de l'événement, vers le répertoire cible de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="41eaa-139">A file transport mechanism is established in the JD Edwards enterprise server to transport the resulting XML document, triggered by the event completion, to the target directory on that server.</span></span>  
  
-   <span data-ttu-id="41eaa-140">L'ordinateur BizTalk Server possède un lecteur mappé au répertoire figurant sur le serveur d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="41eaa-140">The BizTalk Server computer has a mapped drive to the directory on the enterprise server.</span></span>  
  
-   <span data-ttu-id="41eaa-141">Les propriétés de transport du port de réception sont configurées pour le lecteur mappé.</span><span class="sxs-lookup"><span data-stu-id="41eaa-141">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="41eaa-142">Le port de réception reçoit les messages envoyés au répertoire par le serveur d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="41eaa-142">The receive port receives messages posted to directory by the enterprise server.</span></span>  
  
-   <span data-ttu-id="41eaa-143">L'identification de l'espace de noms permet de s'assurer que les messages appropriés sont acheminés vers le port de réception configuré.</span><span class="sxs-lookup"><span data-stu-id="41eaa-143">The target namespace identification ensures that the correct messages are routed to the configured receive port.</span></span>  
  
-   <span data-ttu-id="41eaa-144">Le port de réception envoie le document XML à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="41eaa-144">The receive port submits the XML document to BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41eaa-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41eaa-145">See Also</span></span>  
 <span data-ttu-id="41eaa-146">[Ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="41eaa-146">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="41eaa-147">Planification et architecture</span><span class="sxs-lookup"><span data-stu-id="41eaa-147">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)