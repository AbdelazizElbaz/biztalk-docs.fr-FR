---
title: "Informations pour les exemples de scénarios d’arrière-plan | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security examples [TMA], background information
- DFD
- TMA, examples
ms.assetid: f9518fe7-9892-44f5-8e05-fe48bdb5161a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dbb247e42116d5b308170d5ef365ed9f20d793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="background-information-for-sample-scenarios"></a><span data-ttu-id="590ba-102">Informations générales sur les exemples de scénarios</span><span class="sxs-lookup"><span data-stu-id="590ba-102">Background Information for Sample Scenarios</span></span>
<span data-ttu-id="590ba-103">Cette rubrique contient des informations générales relatives aux scénarios de cette section.</span><span class="sxs-lookup"><span data-stu-id="590ba-103">This topic contains background information for the scenarios in this section.</span></span>  
  
## <a name="background-for-all-scenarios"></a><span data-ttu-id="590ba-104">Informations générales pour tous les scénarios</span><span class="sxs-lookup"><span data-stu-id="590ba-104">Background for all scenarios</span></span>  
 <span data-ttu-id="590ba-105">Avant la principale réunion sur le modèle des menaces, nous avons recueilli les informations générales suivantes.</span><span class="sxs-lookup"><span data-stu-id="590ba-105">Before the main threat model meeting, we collected the following background information.</span></span> <span data-ttu-id="590ba-106">Ces informations s'appliquent à tous les scénarios d'utilisation que nous avons identifiés pour l'exemple d'architecture :</span><span class="sxs-lookup"><span data-stu-id="590ba-106">This information applies to all the usage scenarios we identified for the sample architecture:</span></span>  
  
-   <span data-ttu-id="590ba-107">Limites et étendue de l'architecture</span><span class="sxs-lookup"><span data-stu-id="590ba-107">Boundaries and scope of the architecture</span></span>  
  
-   <span data-ttu-id="590ba-108">Limites entre les composants approuvés et non approuvés</span><span class="sxs-lookup"><span data-stu-id="590ba-108">Boundaries between trusted and untrusted components</span></span>  
  
-   <span data-ttu-id="590ba-109">Modèle de configuration et d'administration pour chaque composant</span><span class="sxs-lookup"><span data-stu-id="590ba-109">Configuration and administration model for each component</span></span>  
  
-   <span data-ttu-id="590ba-110">Hypothèses sur les autres composants et applications</span><span class="sxs-lookup"><span data-stu-id="590ba-110">Assumptions about other components and applications</span></span>  
  
### <a name="boundaries-and-scope-of-the-architecture"></a><span data-ttu-id="590ba-111">Limites et étendue de l'architecture</span><span class="sxs-lookup"><span data-stu-id="590ba-111">Boundaries and scope of the architecture</span></span>  
  
-   <span data-ttu-id="590ba-112">Le pare-feu 2 aide à protéger les serveurs et les applications dans le domaine E-Business du réseau de périmètre et d'autres domaines de votre environnement (par exemple, un domaine d'entreprise ou des domaines pour d'autres applications).</span><span class="sxs-lookup"><span data-stu-id="590ba-112">Firewall 2 helps protect the servers and applications in the E-Business domain both from the perimeter network and from any other domains in your environment (for example, a corporate domain or domains for other applications).</span></span>  
  
-   <span data-ttu-id="590ba-113">Le pare-feu 2 achemine tout le trafic entrant et sortant vers le domaine E-Business.</span><span class="sxs-lookup"><span data-stu-id="590ba-113">Firewall 2 routes all incoming and outgoing traffic to the E-Business domain.</span></span>  
  
-   <span data-ttu-id="590ba-114">Tous les groupes et comptes d'utilisateur qui accèdent à l'environnement BizTalk Server doivent être des groupes globaux dans le domaine E-Business.</span><span class="sxs-lookup"><span data-stu-id="590ba-114">All user groups and accounts that access the BizTalk Server environment must be global groups in the E-Business domain.</span></span>  
  
-   <span data-ttu-id="590ba-115">L'accès est limité au compte de service pour l'instance de l'hôte, à toute application qui dépose des messages dans le serveur de réception pour FILE, SQL ou Message Queuing, et aux administrateurs pour BizTalk Server, l'authentification unique de l'entreprise et Windows.</span><span class="sxs-lookup"><span data-stu-id="590ba-115">Access is limited to the service account for the host instance; any applications that drop messages in the receive server for File, SQL, or Message Queuing; and administrators for BizTalk Server, Enterprise Single Sign-On (SSO), and Windows.</span></span>  
  
### <a name="boundaries-between-trusted-and-untrusted-companies"></a><span data-ttu-id="590ba-116">Limites entre les composants approuvés et non approuvés</span><span class="sxs-lookup"><span data-stu-id="590ba-116">Boundaries between trusted and untrusted companies</span></span>  
  
-   <span data-ttu-id="590ba-117">Le pare-feu 2 achemine tout le trafic entrant et sortant vers le domaine E-Business.</span><span class="sxs-lookup"><span data-stu-id="590ba-117">Firewall 2 routes all incoming and outgoing traffic to the E-Business domain.</span></span>  
  
-   <span data-ttu-id="590ba-118">Utilisez différents hôtes BizTalk comme limite de sécurité entre les applications au sein de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="590ba-118">Use different BizTalk Hosts as a security boundary between applications within BizTalk Server.</span></span>  
  
-   <span data-ttu-id="590ba-119">Utilisez des hôtes approuvés uniquement lorsque vous faites confiance au code au sein de l'application (par exemple, n'exécutez pas de composants tiers dans un hôte approuvé).</span><span class="sxs-lookup"><span data-stu-id="590ba-119">Use trusted hosts only when you trust the code within the application (for example, do not run third-party components in a trusted host).</span></span>  
  
### <a name="configuration-and-administration-model-for-each-component"></a><span data-ttu-id="590ba-120">Modèle de configuration et d'administration pour chaque composant</span><span class="sxs-lookup"><span data-stu-id="590ba-120">Configuration and administration model for each component</span></span>  
 <span data-ttu-id="590ba-121">**Modèle de configuration :**</span><span class="sxs-lookup"><span data-stu-id="590ba-121">**Configuration model:**</span></span>  
  
-   <span data-ttu-id="590ba-122">Les composants d'exécution BizTalk Server sont installés uniquement sur les serveurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="590ba-122">BizTalk Server runtime components are installed only on the BizTalk Servers.</span></span>  
  
-   <span data-ttu-id="590ba-123">Le serveur de secret principal ne possède aucun composant supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="590ba-123">Master secret server has no additional components.</span></span>  
  
-   <span data-ttu-id="590ba-124">SQL Server contient toutes les bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="590ba-124">SQL Server contains all BizTalk Server databases.</span></span>  
  
-   <span data-ttu-id="590ba-125">Les serveurs dans les réseaux de périmètre ne disposent pas de composants BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="590ba-125">Servers in the perimeter networks do not have any BizTalk Server components.</span></span>  
  
-   <span data-ttu-id="590ba-126">Le client d'administration est utilisé pour administrer tous les serveurs du domaine E-Business.</span><span class="sxs-lookup"><span data-stu-id="590ba-126">Administration client is used to administer all servers in the E-Business domain.</span></span>  
  
 <span data-ttu-id="590ba-127">**Modèle d’administration :**</span><span class="sxs-lookup"><span data-stu-id="590ba-127">**Administration model:**</span></span>  
  
-   <span data-ttu-id="590ba-128">À partir d'un ordinateur (ou d'un ordinateur portable), un administrateur se connecte à l'ordinateur qui a les outils d'administration (à l'aide des services Terminal Server ou de la connexion Bureau à distance).</span><span class="sxs-lookup"><span data-stu-id="590ba-128">From a desktop (or laptop), an administrator connects to the computer that has the administration tools (using either Terminal Services or Remote Desktop connection).</span></span> <span data-ttu-id="590ba-129">Une fois que l'administrateur s'est connecté à l'ordinateur qui a les outils d'administration, l'administrateur peut utiliser les outils d'administration de BizTalk pour gérer tous les serveurs et applications au sein du domaine.</span><span class="sxs-lookup"><span data-stu-id="590ba-129">After the administrator connects to the computer that has the administration tools, the administrator can use the BizTalk Administration tools to manage all servers and applications within the domain.</span></span>  
  
### <a name="assumptions-about-other-components-and-applications"></a><span data-ttu-id="590ba-130">Hypothèses sur les autres composants et applications</span><span class="sxs-lookup"><span data-stu-id="590ba-130">Assumptions about other components and applications</span></span>  
 <span data-ttu-id="590ba-131">Tous les autres applications et composants qui interagissent avec l'environnement BizTalk Server sont dans un domaine autre que le domaine E-Business (par exemple, dans un réseau de périmètre).</span><span class="sxs-lookup"><span data-stu-id="590ba-131">All other applications and components that interact with the BizTalk Server environment are in a domain other than the E-Business domain (for example, in a perimeter network).</span></span> <span data-ttu-id="590ba-132">Le trafic à partir de ces applications et composants vers et depuis l'environnement BizTalk Server passe par le pare-feu 2.</span><span class="sxs-lookup"><span data-stu-id="590ba-132">The traffic from those applications and components to and from the BizTalk Server environment goes through Firewall 2.</span></span>  
  
 <span data-ttu-id="590ba-133">Toutes les applications tierces pour BizTalk Server proviennent d'un fournisseur approuvé.</span><span class="sxs-lookup"><span data-stu-id="590ba-133">Any third-party applications for BizTalk Server come from a trusted vendor.</span></span>  
  
### <a name="data-flow-diagrams"></a><span data-ttu-id="590ba-134">Diagrammes de flux de données</span><span class="sxs-lookup"><span data-stu-id="590ba-134">Data flow diagrams</span></span>  
 <span data-ttu-id="590ba-135">L'élément final des informations générales pour chaque scénario d'utilisation est un diagramme de flux de données (DFD).</span><span class="sxs-lookup"><span data-stu-id="590ba-135">The final element of background information for each usage scenario is a data flow diagram (DFD).</span></span> <span data-ttu-id="590ba-136">Un diagramme de flux de données illustre le flux des données à travers l'architecture.</span><span class="sxs-lookup"><span data-stu-id="590ba-136">A DFD illustrates how data flows through the architecture.</span></span> <span data-ttu-id="590ba-137">Chaque scénario possède un diagramme de flux de données différent.</span><span class="sxs-lookup"><span data-stu-id="590ba-137">Each scenario has a different DFD.</span></span> <span data-ttu-id="590ba-138">Dans ce document, des diagrammes de flux de données contiennent les éléments indiqués dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="590ba-138">In this document, the data flow diagrams contain the elements shown in the following figure.</span></span>  
  
 <span data-ttu-id="590ba-139">**Figure 1 éléments de du diagramme**</span><span class="sxs-lookup"><span data-stu-id="590ba-139">**Figure 1 Elements of the DFD**</span></span>  
  
 <span data-ttu-id="590ba-140">![Éléments du diagramme](../core/media/tdi-sec-dfd-legend.gif "TDI_Sec_DFD_Legend")</span><span class="sxs-lookup"><span data-stu-id="590ba-140">![Elements of the DFD](../core/media/tdi-sec-dfd-legend.gif "TDI_Sec_DFD_Legend")</span></span>  
  
## <a name="background-for-adapter-scenarios"></a><span data-ttu-id="590ba-141">Informations générales pour les scénarios des adaptateurs</span><span class="sxs-lookup"><span data-stu-id="590ba-141">Background for adapter scenarios</span></span>  
 <span data-ttu-id="590ba-142">Dans notre exemple d'architecture, nous avons identifié les scénarios d'utilisation suivants en fonction de certains adaptateurs prêts à l'emploi que vous pouvez utiliser :</span><span class="sxs-lookup"><span data-stu-id="590ba-142">In our sample architecture, we identified the following usage scenarios based on some of the adapters you can use out-of-the-box:</span></span>  
  
-   <span data-ttu-id="590ba-143">Scénarios des adaptateurs HTTP et SOAP (services Web)</span><span class="sxs-lookup"><span data-stu-id="590ba-143">HTTP and SOAP (Web services) adapters scenario</span></span>  
  
-   <span data-ttu-id="590ba-144">Scénario de l'adaptateur de Message Queuing BizTalk</span><span class="sxs-lookup"><span data-stu-id="590ba-144">BizTalk Message Queuing adapter scenario</span></span>  
  
-   <span data-ttu-id="590ba-145">Scénario de l'adaptateur FILE</span><span class="sxs-lookup"><span data-stu-id="590ba-145">File adapter scenario</span></span>  
  
-   <span data-ttu-id="590ba-146">Scénario de l'adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="590ba-146">FTP adapter scenario</span></span>  
  
 <span data-ttu-id="590ba-147">Pour chaque scénario, nous avons suivi ces étapes pour compléter l'analyse du modèle des menaces :</span><span class="sxs-lookup"><span data-stu-id="590ba-147">For each scenario, we followed these steps to complete the threat model analysis:</span></span>  
  
-   <span data-ttu-id="590ba-148">Collecter les informations générales</span><span class="sxs-lookup"><span data-stu-id="590ba-148">Collect background information</span></span>  
  
-   <span data-ttu-id="590ba-149">Créer et analyser le modèle des menaces</span><span class="sxs-lookup"><span data-stu-id="590ba-149">Create and analyze the threat model</span></span>  
  
-   <span data-ttu-id="590ba-150">Passer en revue les menaces</span><span class="sxs-lookup"><span data-stu-id="590ba-150">Review threats</span></span>  
  
-   <span data-ttu-id="590ba-151">Identifier les techniques et technologies de prévention</span><span class="sxs-lookup"><span data-stu-id="590ba-151">Identify mitigation techniques and technologies</span></span>  
  
 <span data-ttu-id="590ba-152">Pour chaque scénario, nous avons tenté de mettre au point des degrés génériques de niveau de menace que les diverses attaques peuvent représenter.</span><span class="sxs-lookup"><span data-stu-id="590ba-152">For each scenario, we have tried to develop generic ratings of the level of threat that the various attacks might represent.</span></span> <span data-ttu-id="590ba-153">Cependant, votre environnement ou expérience peut suggérer qu'une menace particulière mérite un degré différent de celui attribué.</span><span class="sxs-lookup"><span data-stu-id="590ba-153">However, your environment or experience might suggest that a particular threat deserves a different rating than we have given it.</span></span> <span data-ttu-id="590ba-154">Comme dans tous les scénarios de sécurité, vos propres données sont les plus sûres pour déterminer les niveaux de menace et nous vous recommandons d'effectuer votre propre analyse, en vous servant de nos analyse et résultats.</span><span class="sxs-lookup"><span data-stu-id="590ba-154">As with all security scenarios, your own data is the most robust to determine threat levels, and we recommend that you conduct your own analysis, using our analysis and results as a guide.</span></span>  
  
 <span data-ttu-id="590ba-155">Les informations générales, à l'exception du diagramme de flux de données, sont les mêmes pour tous nos scénarios d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="590ba-155">The background information—except for the data flow diagram (DFD)—is the same for all our usage scenarios.</span></span> <span data-ttu-id="590ba-156">Dans les sections suivantes, nous présentons le diagramme de flux de données pour chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="590ba-156">In the next sections we show the DFD for each scenario.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590ba-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="590ba-157">See Also</span></span>  
 <span data-ttu-id="590ba-158">[Analyse du modèle](../core/threat-model-analysis.md) </span><span class="sxs-lookup"><span data-stu-id="590ba-158">[Threat Model Analysis](../core/threat-model-analysis.md) </span></span>  
 <span data-ttu-id="590ba-159">[Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md) </span><span class="sxs-lookup"><span data-stu-id="590ba-159">[Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md) </span></span>  
 <span data-ttu-id="590ba-160">[Planification de la sécurité](../core/planning-for-security.md) </span><span class="sxs-lookup"><span data-stu-id="590ba-160">[Planning for Security](../core/planning-for-security.md) </span></span>  
 [<span data-ttu-id="590ba-161">Exemples d’architecture pour les petites et moyennes entreprises</span><span class="sxs-lookup"><span data-stu-id="590ba-161">Sample Architectures for Small & Medium-Sized Companies</span></span>](../core/sample-architectures-for-small-medium-sized-companies.md)