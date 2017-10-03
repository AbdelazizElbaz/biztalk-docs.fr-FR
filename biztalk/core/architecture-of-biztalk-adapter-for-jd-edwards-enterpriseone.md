---
title: "Architecture de l’adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: architecture
ms.assetid: 0441c5d2-6a46-45b6-8ab5-0bdac3590f56
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 828d0ed6affc44edbf49beb204cd4afe21196747
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="282dc-102">Architecture de l'adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="282dc-102">Architecture of BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="282dc-103">L'adaptateur Microsoft BizTalk pour Edwards EnterpriseOne permet d'accéder aux fonctions commerciales de JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="282dc-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides access to JD Edwards EnterpriseOne business functions.</span></span> <span data-ttu-id="282dc-104">JD Edwards EnterpriseOne communique entre les ordinateurs client et serveur à l'aide d'une architecture de messagerie propriétaire nommée JDENet.</span><span class="sxs-lookup"><span data-stu-id="282dc-104">JD Edwards EnterpriseOne communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="282dc-105">Celle-ci est implémentée par les classes de connecteur JD Edwards EnterpriseOne figurant dans les fichiers JAR, Connector.jar et Kernel.jar.</span><span class="sxs-lookup"><span data-stu-id="282dc-105">JDENet is implemented by the JD Edwards EnterpriseOne connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="282dc-106">La communication est implémentée à l’aide de TCP/IP comme protocole de transport, avec le port par défaut 6009 ou 6010.</span><span class="sxs-lookup"><span data-stu-id="282dc-106">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="282dc-107">Pour obtenir une description de l’emplacement où cette valeur est définie, consultez [comment définir les propriétés Transport JD Edwards OneWorld](../core/how-to-set-jd-edwards-oneworld-transport-properties.md).</span><span class="sxs-lookup"><span data-stu-id="282dc-107">For a description of where this value is set, see [How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md).</span></span>  
  
 <span data-ttu-id="282dc-108">L'architecture de l'adaptateur BizTalk pour JD Edwards EnterpriseOne est représentée dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="282dc-108">The following figure shows the architecture for BizTalk Adapter for JD Edwards EnterpriseOne.</span></span>  
  
 ![](../core/media/jd-enterpriseone-arch.gif "JD_EnterpriseOne_arch")  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="282dc-109">Services entrants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="282dc-109">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="282dc-110">Au moment de la conception, vous créez un port, sélectionnez un adaptateur et fournissez les informations d'identification pour la connexion au serveur JD Edwards EnterpriseOne cible.</span><span class="sxs-lookup"><span data-stu-id="282dc-110">At design time, you create a port, select an adapter, and provide credential information to connect to the target JD Edwards EnterpriseOne server.</span></span> <span data-ttu-id="282dc-111">L'environnement de développement Visual Studio appelle l'infrastructure d'adaptateurs pour demander des informations de conception pour ce port.</span><span class="sxs-lookup"><span data-stu-id="282dc-111">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="282dc-112">L'adaptateur utilise Browsingagent pour ce port.</span><span class="sxs-lookup"><span data-stu-id="282dc-112">The adapter uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="282dc-113">Au moment de la conception, BizTalk Server demande des informations en appelant l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="282dc-113">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="282dc-114">Browsingagent convertit la demande en code natif JD Edwards EnterpriseOne et la transmet à JD Edwards EnterpriseOne via la connexion API ThinNet (établie dans Connector.jar et Kernel.jar).</span><span class="sxs-lookup"><span data-stu-id="282dc-114">The Browsingagent converts the request into native JD Edwards EnterpriseOne code and transmits the requests to JD Edwards EnterpriseOne through the ThinNet API connection (established in Connector.jar and Kernel.jar).</span></span>  
  
-   <span data-ttu-id="282dc-115">La liste des modules de JD Edwards EnterpriseOne est initialement renvoyée et transportée vers l'environnement de développement Visual Studio, dans lequel elle renseigne l'Assistant Adaptateur.</span><span class="sxs-lookup"><span data-stu-id="282dc-115">A list of Modules in JD Edwards EnterpriseOne is initially returned and transported to the Visual Studio development environment, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="282dc-116">Vous pouvez développer la hiérarchie en affichant le nom de la bibliothèque puis le nom du module.</span><span class="sxs-lookup"><span data-stu-id="282dc-116">You can expand the hierarchy by displaying the library name and then the module name.</span></span>  
  
-   <span data-ttu-id="282dc-117">Lorsque vous sélectionnez un module spécifique, des schémas pour toutes les fonctions de ce module s'affichent.</span><span class="sxs-lookup"><span data-stu-id="282dc-117">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="282dc-118">L'adaptateur obtient les informations requises auprès de JD Edwards EnterpriseOne, et Browsingagent crée les schémas.</span><span class="sxs-lookup"><span data-stu-id="282dc-118">The adapter gets the required information from JD Edwards EnterpriseOne, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="282dc-119">Les schémas sont ajoutés à l'orchestration du projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="282dc-119">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="282dc-120">Services entrants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="282dc-120">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="282dc-121">BizTalk Server appelle l'adaptateur pour envoyer un message sur un port spécifique.</span><span class="sxs-lookup"><span data-stu-id="282dc-121">BizTalk Server calls the adapter to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="282dc-122">L'agent d'exécution convertit le XML en code JDE natif.</span><span class="sxs-lookup"><span data-stu-id="282dc-122">The run-time agent converts the XML into native JDE code.</span></span>  
  
-   <span data-ttu-id="282dc-123">L'agent d'exécution envoie la demande via ThinNet au système JD Edwards EnterpriseOne spécifié dans les propriétés de transport du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="282dc-123">The run-time agent submits the request through the ThinNet to the JD Edwards EnterpriseOne system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="282dc-124">La fonction commerciale principale est exécutée sur le système JD Edwards EnterpriseOne, qui génère ensuite un document de réponse, lequel indique si l'opération a réussi ou échoué, ainsi que les paramètres de données renvoyés par la fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="282dc-124">The Master Business Function is executed on the JD Edwards EnterpriseOne system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="282dc-125">Le message envoyé à JD Edwards EnterpriseOne constitue une architecture à message unique et à réponse unique.</span><span class="sxs-lookup"><span data-stu-id="282dc-125">The message sent to JD Edwards EnterpriseOne is a single message, single reply architecture.</span></span> <span data-ttu-id="282dc-126">Il est impossible de traiter plusieurs messages simultanément.</span><span class="sxs-lookup"><span data-stu-id="282dc-126">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="282dc-127">Le document de réponse est renvoyé via ThinNet, converti au format XML et retransmis à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="282dc-127">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="282dc-128">Événements sortants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="282dc-128">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="282dc-129">Aucune création systématique de métadonnées d'événement n'est disponible.</span><span class="sxs-lookup"><span data-stu-id="282dc-129">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="282dc-130">Une télécopie du document d'événements doit être fournie à Visual Studio afin qu'un schéma puisse être généré et incorporé au projet avec l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="282dc-130">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="282dc-131">Événements sortants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="282dc-131">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="282dc-132">Un mécanisme de transport de fichier est mis en place dans le serveur JD Edwards EnterpriseOne pour transporter le document XML résultant de l'opération, déclenché par la fin de l'événement, vers le répertoire cible de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="282dc-132">A file transport mechanism is established in the JD Edwards EnterpriseOne server to transport the resulting XML document, triggered by the event completion, to the target directory on that computer.</span></span>  
  
-   <span data-ttu-id="282dc-133">L'ordinateur BizTalk Server possède un lecteur mappé au répertoire figurant sur le serveur EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="282dc-133">The BizTalk Server computer has a mapped drive to the directory on the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="282dc-134">Les propriétés de transport du port de réception sont configurées pour le lecteur mappé.</span><span class="sxs-lookup"><span data-stu-id="282dc-134">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="282dc-135">Le port de réception reçoit les messages, qui sont envoyés vers un répertoire par le serveur EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="282dc-135">The receive port receives messages, which are posted to a directory by the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="282dc-136">L'identification de l'espace de noms permet de s'assurer que les messages appropriés sont acheminés vers le port de réception configuré</span><span class="sxs-lookup"><span data-stu-id="282dc-136">The target namespace identification ensures that the correct messages are routed to the configured receive port</span></span>  
  
-   <span data-ttu-id="282dc-137">Le port de réception envoie le document XML dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="282dc-137">The receive port submits the XML document in BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="282dc-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="282dc-138">See Also</span></span>  
 [<span data-ttu-id="282dc-139">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="282dc-139">Planning and Architecture</span></span>](../core/planning-and-architecture8.md)