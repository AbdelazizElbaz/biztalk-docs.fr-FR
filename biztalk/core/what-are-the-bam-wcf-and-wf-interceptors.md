---
title: "Que sont les intercepteurs WCF et WF BAM ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 198bfdc9-86ff-4017-b65f-19616deeb9f4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c819d219a9796b485434101ee1c2f2d4be136ae0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-are-the-bam-wcf-and-wf-interceptors"></a><span data-ttu-id="b366b-103">Que sont les intercepteurs WCF et WF BAM ?</span><span class="sxs-lookup"><span data-stu-id="b366b-103">What Are the BAM WCF and WF Interceptors?</span></span>
<span data-ttu-id="b366b-104">Le composant d'analyse BAM (Business Activity Monitoring) est un ensemble d'outils, d'API et de services qui permet de gérer des agrégations, des alertes et des profils, et d'instrumenter des processus automatiques pour envoyer des événements en vue d'analyser les mesures de performances relatives à une activité commerciale.</span><span class="sxs-lookup"><span data-stu-id="b366b-104">Business Activity Monitoring (BAM) is a collection of tools, APIs, and services that allow you to manage aggregations, alerts, and profiles, and to instrument automated processes to send events to monitor relevant business metrics.</span></span> <span data-ttu-id="b366b-105">Ensemble, ils fournissent une visibilité de bout en bout des processus d'entreprise et permettent d'avoir une vue d'ensemble des états et résultats des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b366b-105">Together, these provide end-to-end visibility into business processes and enable you to stay abreast of business process status and results.</span></span>  
  
 <span data-ttu-id="b366b-106">Les intercepteurs BAM étendent ces fonctionnalités dans Windows Workflow Foundation (WF), Windows Communication Foundation (WCF) et d'autres environnements d'exécution.</span><span class="sxs-lookup"><span data-stu-id="b366b-106">BAM interceptors extend this same functionality into Windows Workflow Foundation (WF), Windows Communication Foundation (WCF), and other runtime environments.</span></span> <span data-ttu-id="b366b-107">Ils permettent de suivre vos processus d’entreprise sans recompiler votre solution WF ou WCF (l’intégration est effectuée via un fichier de configuration).</span><span class="sxs-lookup"><span data-stu-id="b366b-107">By using a BAM interceptor, you can track your business processes without recompiling your WF or WCF solution—integration is done through a configuration file.</span></span>  
  
 <span data-ttu-id="b366b-108">L'utilisation de l'intercepteur WF ou WCF BAM dans un projet vous permet d'effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="b366b-108">By using the BAM WF or WCF interceptor in your project, you can:</span></span>  
  
-   <span data-ttu-id="b366b-109">utiliser le portail BAM pour consulter les informations relatives aux processus d'entreprise exécutés dans votre application WF ou WCF ;</span><span class="sxs-lookup"><span data-stu-id="b366b-109">Use the BAM portal to view information about the business processes running in your WF or WCF application.</span></span>  
  
-   <span data-ttu-id="b366b-110">utiliser les fonctionnalités de l'analyse BAM sans ajouter de code à votre application ;</span><span class="sxs-lookup"><span data-stu-id="b366b-110">Use BAM functionality without adding additional code to your application.</span></span>  
  
-   <span data-ttu-id="b366b-111">déployer votre solution à l'aide d'outils et d'utilitaires BizTalk Server familiers ;</span><span class="sxs-lookup"><span data-stu-id="b366b-111">Deploy your solution using familiar BizTalk Server tools and utilities.</span></span>  
  
-   <span data-ttu-id="b366b-112">utiliser votre environnement BizTalk Server existant pour les applications WF et WCF existantes et nouvelles.</span><span class="sxs-lookup"><span data-stu-id="b366b-112">Leverage your existing BizTalk Server environment for existing and new WF and WCF applications.</span></span>  
  
## <a name="interceptor-components"></a><span data-ttu-id="b366b-113">Composants d'un intercepteur</span><span class="sxs-lookup"><span data-stu-id="b366b-113">Interceptor Components</span></span>  
 <span data-ttu-id="b366b-114">L'ensemble de composants Common Interceptor Foundation constitue l'élément central d'un intercepteur BAM. Il fournit la base pour créer des intercepteurs personnalisés pour les environnements hétérogènes.</span><span class="sxs-lookup"><span data-stu-id="b366b-114">At the core of each BAM interceptor is the Common Interceptor Foundation, a set of components that provide the foundation for building custom interceptors for heterogeneous environments.</span></span> <span data-ttu-id="b366b-115">Il inclut les composants partagés suivants :</span><span class="sxs-lookup"><span data-stu-id="b366b-115">The Common Interceptor Foundation contains the following shared components:</span></span>  
  
-   <span data-ttu-id="b366b-116">**BM.exe**, une version améliorée de l’utilitaire de déploiement BAM étendu pour modifier les configurations d’intercepteurs associées, y compris ajouter, supprimer, mettre à jour et fonctionnalités de liste.</span><span class="sxs-lookup"><span data-stu-id="b366b-116">**bm.exe**, an enhanced version of the BAM deployment utility extended to modify interceptor configurations including add, remove, update, and list functionality.</span></span>  
  
-   <span data-ttu-id="b366b-117">**CommonInterceptorConfiguration.xsd**, le schéma XML de configuration Common Interceptor Foundation.</span><span class="sxs-lookup"><span data-stu-id="b366b-117">**CommonInterceptorConfiguration.xsd**, the Common Interceptor Foundation configuration XML schema.</span></span> <span data-ttu-id="b366b-118">Les configurations des intercepteurs doivent au moins être validées par rapport à ce schéma.</span><span class="sxs-lookup"><span data-stu-id="b366b-118">At minimum, all interceptor configurations must validate against this schema.</span></span>  
  
## <a name="windows-workflow-foundation-wf-interceptor"></a><span data-ttu-id="b366b-119">Intercepteur Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="b366b-119">Windows Workflow Foundation (WF) Interceptor</span></span>  
 <span data-ttu-id="b366b-120">L'intercepteur Windows Workflow Foundation permet d'ajouter de façon transparente les fonctionnalités de suivi BAM aux applications WF nouvelles et existantes.</span><span class="sxs-lookup"><span data-stu-id="b366b-120">The Windows Workflow Foundation interceptor enables you to transparently add BAM tracking functionality to new and existing WF applications.</span></span> <span data-ttu-id="b366b-121">Une fois la configuration de l'intercepteur déployée dans la base de données d'importation principale BAM et les instances de l'application WF configurées pour charger l'intercepteur WF BAM, les données de flux de travail sont écrites dans l'analyse BAM, sans code supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b366b-121">After the interceptor configuration has been deployed to the BAM Primary Import database and each instance of the WF application has been configured to load the BAM WF Interceptor, workflow data will be written to BAM with no additional code.</span></span> <span data-ttu-id="b366b-122">L'intercepteur WF présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b366b-122">The WF interceptor provides the following functionality:</span></span>  
  
-   <span data-ttu-id="b366b-123">s'intègre aux applications WF existantes sans modification ou recompilation du code.</span><span class="sxs-lookup"><span data-stu-id="b366b-123">Plugs into existing WF applications without requiring code changes or recompilation.</span></span>  
  
-   <span data-ttu-id="b366b-124">permet la détection au moment de l'exécution et prend en charge les fichiers de configuration modifiés.</span><span class="sxs-lookup"><span data-stu-id="b366b-124">Enables run-time detection and support for changed configuration files.</span></span> <span data-ttu-id="b366b-125">Si une nouvelle version du fichier de configuration d'un intercepteur est détectée, les nouvelles instances de flux de travail utilisent la nouvelle configuration tandis que les anciennes sont exécutées à l'aide de l'ancienne configuration.</span><span class="sxs-lookup"><span data-stu-id="b366b-125">If a new version of an interceptor configuration file is detected, new workflow instances will use the new configuration while old workflow instances will complete using the old configuration.</span></span>  
  
-   <span data-ttu-id="b366b-126">prend en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="b366b-126">Supports transactions.</span></span> <span data-ttu-id="b366b-127">L'intercepteur WF conserve les éléments suivis en maintenant la cohérence avec les transactions WF.</span><span class="sxs-lookup"><span data-stu-id="b366b-127">The WF interceptor persists tracked items in a transactionally consistent way with WF transactions.</span></span> <span data-ttu-id="b366b-128">Les éléments suivis ne sont conservés qu'une fois la transaction WF et la transaction d'intercepteur exécutées.</span><span class="sxs-lookup"><span data-stu-id="b366b-128">Tracked items are only persisted when the WF transaction and the interceptor trasaction complete successfully.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b366b-129">L'intercepteur Windows Workflow ne prend pas en charge SharedConnectionWorkflowCommitWorkBatchService qui utilise la même connexion SQL pour les services de suivi et les services de persistance.</span><span class="sxs-lookup"><span data-stu-id="b366b-129">The Windows Workflow interceptor does not support SharedConnectionWorkflowCommitWorkBatchService which uses the same SQL connection for both the tracking and persistence services.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b366b-130">Dans BizTalk Server, l’intercepteur Windows Workflow Foundation (WF) ne fonctionnera pas avec le nouveau moteur WF dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b366b-130">In BizTalk Server, the Windows Workflow Foundation (WF) interceptor will not work with the new WF engine in .NET Framework 4.</span></span> <span data-ttu-id="b366b-131">L’intercepteur WF continue de fonctionner dans .NET Framework 3.5 SP2.</span><span class="sxs-lookup"><span data-stu-id="b366b-131">The WF interceptor will continue to work in .NET Framework 3.5 SP2.</span></span>  
  
## <a name="windows-communication-foundation-wcf-interceptor"></a><span data-ttu-id="b366b-132">Intercepteur Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="b366b-132">Windows Communication Foundation (WCF) Interceptor</span></span>  
 <span data-ttu-id="b366b-133">L'intercepteur Windows Communication Foundation permet d'ajouter les fonctionnalités de suivi BAM à vos applications WCF.</span><span class="sxs-lookup"><span data-stu-id="b366b-133">The Windows Communication Foundation interceptor provides BAM tracking functionality to your WCF applications.</span></span> <span data-ttu-id="b366b-134">Il présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="b366b-134">It provides the following functionality:</span></span>  
  
-   <span data-ttu-id="b366b-135">s'intègre aux applications WCF existantes sans modification ou recompilation du code.</span><span class="sxs-lookup"><span data-stu-id="b366b-135">Plugs into existing WCF applications without requiring code changes or recompilation.</span></span>  
  
-   <span data-ttu-id="b366b-136">assure le suivi des messages contenus dans les appels de service WCF.</span><span class="sxs-lookup"><span data-stu-id="b366b-136">Tracks messages contained in WCF service calls.</span></span>  
  
-   <span data-ttu-id="b366b-137">assure le suivi des informations des messages dans les appels de service WCF.</span><span class="sxs-lookup"><span data-stu-id="b366b-137">Tracks information from messages in WCF service calls.</span></span>  
  
-   <span data-ttu-id="b366b-138">participe aux transactions transmises du client ou initiées en interne pour les appels de service traités.</span><span class="sxs-lookup"><span data-stu-id="b366b-138">Participates in transactions flowed from the client or initiated internally for transacted service calls.</span></span>