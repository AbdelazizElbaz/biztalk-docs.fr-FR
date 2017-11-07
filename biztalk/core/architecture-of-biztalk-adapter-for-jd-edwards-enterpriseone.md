---
title: "Architecture de l’adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft"
description: "Décrit les services entrants au moment du design et moment de l’exécution, les événements sortants au moment du design et le moment de l’exécution dans l’adaptateur JD Edwards EnterpriseOne dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0441c5d2-6a46-45b6-8ab5-0bdac3590f56
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b495ee9a34cf464bd5cc11caed53c5df54948a49
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="da504-103">Architecture de l'adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="da504-103">Architecture of BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="da504-104">L'adaptateur Microsoft BizTalk pour Edwards EnterpriseOne permet d'accéder aux fonctions commerciales de JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="da504-104">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides access to JD Edwards EnterpriseOne business functions.</span></span> <span data-ttu-id="da504-105">JD Edwards EnterpriseOne communique entre les ordinateurs client et serveur à l'aide d'une architecture de messagerie propriétaire nommée JDENet.</span><span class="sxs-lookup"><span data-stu-id="da504-105">JD Edwards EnterpriseOne communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="da504-106">Celle-ci est implémentée par les classes de connecteur JD Edwards EnterpriseOne figurant dans les fichiers JAR, Connector.jar et Kernel.jar.</span><span class="sxs-lookup"><span data-stu-id="da504-106">JDENet is implemented by the JD Edwards EnterpriseOne connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="da504-107">La communication est implémentée à l’aide de TCP/IP comme protocole de transport, avec le port par défaut 6009 ou 6010.</span><span class="sxs-lookup"><span data-stu-id="da504-107">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="da504-108">Pour obtenir une description de l’emplacement où cette valeur est définie, consultez [ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md).</span><span class="sxs-lookup"><span data-stu-id="da504-108">For a description of where this value is set, see [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md).</span></span>  
  
 <span data-ttu-id="da504-109">L'architecture de l'adaptateur BizTalk pour JD Edwards EnterpriseOne est représentée dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="da504-109">The following figure shows the architecture for BizTalk Adapter for JD Edwards EnterpriseOne.</span></span>  
  
 ![](../core/media/jd-enterpriseone-arch.gif "JD_EnterpriseOne_arch")  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="da504-110">Services entrants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="da504-110">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="da504-111">Au moment de la conception, vous créez un port, sélectionnez un adaptateur et fournissez les informations d'identification pour la connexion au serveur JD Edwards EnterpriseOne cible.</span><span class="sxs-lookup"><span data-stu-id="da504-111">At design time, you create a port, select an adapter, and provide credential information to connect to the target JD Edwards EnterpriseOne server.</span></span> <span data-ttu-id="da504-112">L'environnement de développement Visual Studio appelle l'infrastructure d'adaptateurs pour demander des informations de conception pour ce port.</span><span class="sxs-lookup"><span data-stu-id="da504-112">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="da504-113">L'adaptateur utilise Browsingagent pour ce port.</span><span class="sxs-lookup"><span data-stu-id="da504-113">The adapter uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="da504-114">Au moment de la conception, BizTalk Server demande des informations en appelant l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="da504-114">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="da504-115">Browsingagent convertit la demande en code natif JD Edwards EnterpriseOne et la transmet à JD Edwards EnterpriseOne via la connexion API ThinNet (établie dans Connector.jar et Kernel.jar).</span><span class="sxs-lookup"><span data-stu-id="da504-115">The Browsingagent converts the request into native JD Edwards EnterpriseOne code and transmits the requests to JD Edwards EnterpriseOne through the ThinNet API connection (established in Connector.jar and Kernel.jar).</span></span>  
  
-   <span data-ttu-id="da504-116">La liste des modules de JD Edwards EnterpriseOne est initialement renvoyée et transportée vers l'environnement de développement Visual Studio, dans lequel elle renseigne l'Assistant Adaptateur.</span><span class="sxs-lookup"><span data-stu-id="da504-116">A list of Modules in JD Edwards EnterpriseOne is initially returned and transported to the Visual Studio development environment, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="da504-117">Vous pouvez développer la hiérarchie en affichant le nom de la bibliothèque puis le nom du module.</span><span class="sxs-lookup"><span data-stu-id="da504-117">You can expand the hierarchy by displaying the library name and then the module name.</span></span>  
  
-   <span data-ttu-id="da504-118">Lorsque vous sélectionnez un module spécifique, des schémas pour toutes les fonctions de ce module s'affichent.</span><span class="sxs-lookup"><span data-stu-id="da504-118">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="da504-119">L'adaptateur obtient les informations requises auprès de JD Edwards EnterpriseOne, et Browsingagent crée les schémas.</span><span class="sxs-lookup"><span data-stu-id="da504-119">The adapter gets the required information from JD Edwards EnterpriseOne, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="da504-120">Les schémas sont ajoutés à l'orchestration du projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="da504-120">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="da504-121">Services entrants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="da504-121">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="da504-122">BizTalk Server appelle l'adaptateur pour envoyer un message sur un port spécifique.</span><span class="sxs-lookup"><span data-stu-id="da504-122">BizTalk Server calls the adapter to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="da504-123">L'agent d'exécution convertit le XML en code JDE natif.</span><span class="sxs-lookup"><span data-stu-id="da504-123">The run-time agent converts the XML into native JDE code.</span></span>  
  
-   <span data-ttu-id="da504-124">L'agent d'exécution envoie la demande via ThinNet au système JD Edwards EnterpriseOne spécifié dans les propriétés de transport du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="da504-124">The run-time agent submits the request through the ThinNet to the JD Edwards EnterpriseOne system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="da504-125">La fonction commerciale principale est exécutée sur le système JD Edwards EnterpriseOne, qui génère ensuite un document de réponse, lequel indique si l'opération a réussi ou échoué, ainsi que les paramètres de données renvoyés par la fonction commerciale.</span><span class="sxs-lookup"><span data-stu-id="da504-125">The Master Business Function is executed on the JD Edwards EnterpriseOne system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="da504-126">Le message envoyé à JD Edwards EnterpriseOne constitue une architecture à message unique et à réponse unique.</span><span class="sxs-lookup"><span data-stu-id="da504-126">The message sent to JD Edwards EnterpriseOne is a single message, single reply architecture.</span></span> <span data-ttu-id="da504-127">Il est impossible de traiter plusieurs messages simultanément.</span><span class="sxs-lookup"><span data-stu-id="da504-127">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="da504-128">Le document de réponse est renvoyé via ThinNet, converti au format XML et retransmis à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="da504-128">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="da504-129">Événements sortants au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="da504-129">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="da504-130">Aucune création systématique de métadonnées d'événement n'est disponible.</span><span class="sxs-lookup"><span data-stu-id="da504-130">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="da504-131">Une télécopie du document d'événements doit être fournie à Visual Studio afin qu'un schéma puisse être généré et incorporé au projet avec l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="da504-131">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="da504-132">Événements sortants au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="da504-132">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="da504-133">Un mécanisme de transport de fichier est mis en place dans le serveur JD Edwards EnterpriseOne pour transporter le document XML résultant de l'opération, déclenché par la fin de l'événement, vers le répertoire cible de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="da504-133">A file transport mechanism is established in the JD Edwards EnterpriseOne server to transport the resulting XML document, triggered by the event completion, to the target directory on that computer.</span></span>  
  
-   <span data-ttu-id="da504-134">L'ordinateur BizTalk Server possède un lecteur mappé au répertoire figurant sur le serveur EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="da504-134">The BizTalk Server computer has a mapped drive to the directory on the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="da504-135">Les propriétés de transport du port de réception sont configurées pour le lecteur mappé.</span><span class="sxs-lookup"><span data-stu-id="da504-135">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="da504-136">Le port de réception reçoit les messages, qui sont envoyés vers un répertoire par le serveur EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="da504-136">The receive port receives messages, which are posted to a directory by the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="da504-137">L'identification de l'espace de noms permet de s'assurer que les messages appropriés sont acheminés vers le port de réception configuré</span><span class="sxs-lookup"><span data-stu-id="da504-137">The target namespace identification ensures that the correct messages are routed to the configured receive port</span></span>  
  
-   <span data-ttu-id="da504-138">Le port de réception envoie le document XML dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="da504-138">The receive port submits the XML document in BizTalk Server.</span></span>  
  
## <a name="more-good-stuff"></a><span data-ttu-id="da504-139">Autre contenu intéressant</span><span class="sxs-lookup"><span data-stu-id="da504-139">More good stuff</span></span>
[<span data-ttu-id="da504-140">Sécurité de l’adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="da504-140">Security in BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[<span data-ttu-id="da504-141">Créer les artefacts de l’application</span><span class="sxs-lookup"><span data-stu-id="da504-141">Create the application artifacts</span></span>](../core/developing-applications2.md)  
[<span data-ttu-id="da504-142">Importer votre JD Edwards EnterpriseOne application</span><span class="sxs-lookup"><span data-stu-id="da504-142">Import your JD Edwards EnterpriseOne app</span></span>](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[<span data-ttu-id="da504-143">Utiliser la gestion des exceptions BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="da504-143">Use BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling3.md)  
[<span data-ttu-id="da504-144">Dépanner</span><span class="sxs-lookup"><span data-stu-id="da504-144">Troubleshoot</span></span>](../core/troubleshooting-jd-edwards-enterpriseone.md)  
