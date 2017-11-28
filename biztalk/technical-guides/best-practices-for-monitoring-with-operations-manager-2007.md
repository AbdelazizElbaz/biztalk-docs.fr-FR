---
title: "Meilleures pratiques pour l’analyse d’Operations Manager 2007 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67a5026c-ef59-498b-9bef-ea0f1c932eae
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29d83f647c40801260890a99cef4b0b2bfa0551b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-monitoring-with-operations-manager-2007"></a><span data-ttu-id="ed8f0-102">Meilleures pratiques pour l’analyse d’Operations Manager 2007</span><span class="sxs-lookup"><span data-stu-id="ed8f0-102">Best Practices for Monitoring with Operations Manager 2007</span></span>
<span data-ttu-id="ed8f0-103">Respecter les méthodes conseillées répertoriées dans cette rubrique pour surveiller efficacement vos applications à l’aide d’Operations Manager 2007.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-103">Adhere to the best practices listed in this topic to effectively monitor your applications using Operations Manager 2007.</span></span>  
  
 <span data-ttu-id="ed8f0-104">**Installer des packs d’administration supplémentaires pour une couverture plus complète**</span><span class="sxs-lookup"><span data-stu-id="ed8f0-104">**Install additional management packs for more complete coverage**</span></span>  
  
-   <span data-ttu-id="ed8f0-105">Pour vous assurer qu’Operations Manager 2007 surveille les applications principales dans votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, vous devez installer les packs d’administration suivants :</span><span class="sxs-lookup"><span data-stu-id="ed8f0-105">To help ensure that Operations Manager 2007 monitors the key applications in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, you should install the following management packs:</span></span>  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ed8f0-106">(obligatoire)</span><span class="sxs-lookup"><span data-stu-id="ed8f0-106"> (required)</span></span>  
  
    -   <span data-ttu-id="ed8f0-107">Système d’exploitation Windows Server (facultatif)</span><span class="sxs-lookup"><span data-stu-id="ed8f0-107">Windows Server Operating System (optional)</span></span>  
  
    -   <span data-ttu-id="ed8f0-108">Microsoft Windows Server Failover Cluster (si les clusters sont utilisés, facultatif)</span><span class="sxs-lookup"><span data-stu-id="ed8f0-108">Microsoft Windows Server Failover Cluster (if clusters are used, optional)</span></span>  
  
    -   <span data-ttu-id="ed8f0-109">Surveillance de SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed8f0-109">SQL Server Monitoring</span></span>  
  
    -   <span data-ttu-id="ed8f0-110">Internet Information Services 7</span><span class="sxs-lookup"><span data-stu-id="ed8f0-110">Internet Information Services 7</span></span>  
  
    -   <span data-ttu-id="ed8f0-111">Message Queuing (MSMQ) 5.0 (facultatif)</span><span class="sxs-lookup"><span data-stu-id="ed8f0-111">Message Queuing (MSMQ) 5.0 (optional)</span></span>  
  
 <span data-ttu-id="ed8f0-112">**Passez en revue et hiérarchiser les alertes sur une base quotidienne**</span><span class="sxs-lookup"><span data-stu-id="ed8f0-112">**Review and prioritize alerts on a daily basis**</span></span>  
  
-   <span data-ttu-id="ed8f0-113">Consulter les alertes chaque jour et définir un ordre de priorité permet de s'assurer que les problèmes sont résolus en temps voulu.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-113">Reviewing and prioritizing alerts on a daily basis helps to ensure that issues are resolved in a timely manner.</span></span>  
  
 <span data-ttu-id="ed8f0-114">**Vérifiez que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] communique avec le serveur Operations Manager 2007.**</span><span class="sxs-lookup"><span data-stu-id="ed8f0-114">**Verify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is communicating with the Operations Manager 2007 server.**</span></span>  
  
-   <span data-ttu-id="ed8f0-115">Si l’échec de la communication entre les serveurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l’infrastructure d’analyse, vous ne recevrez pas d’alertes.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-115">If communication fails between the servers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the monitoring infrastructure, you will not receive alerts.</span></span>  
  
 <span data-ttu-id="ed8f0-116">**Activer et désactiver les règles selon les besoins**</span><span class="sxs-lookup"><span data-stu-id="ed8f0-116">**Enable and disable rules as necessary**</span></span>  
  
-   <span data-ttu-id="ed8f0-117">Par défaut, certaines des règles du pack d'administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-117">By default, some of the rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack are disabled.</span></span> <span data-ttu-id="ed8f0-118">Ces règles désactivées sont les suivants : les règles nécessitant une personnalisation, les règles qui servent de modèles et les règles de surveillance supplémentaires [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] événements.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-118">These disabled rules are of the following types: rules needing customization, rules that serve as templates, and rules for monitoring additional [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] events.</span></span> <span data-ttu-id="ed8f0-119">Assurez-vous que les règles appropriées votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement sont activés.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-119">Make sure the relevant rules for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment are enabled.</span></span>  
  
 <span data-ttu-id="ed8f0-120">**Personnaliser les règles selon les besoins de votre environnement**</span><span class="sxs-lookup"><span data-stu-id="ed8f0-120">**Customize rules as necessary for your environment**</span></span>  
  
-   <span data-ttu-id="ed8f0-121">Vous devez personnaliser les règles dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pack d’administration en fonction de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-121">You should customize the rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack to suit your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span> <span data-ttu-id="ed8f0-122">Certaines règles requièrent la surveillance des seuils ou les seuils de temps qui sont définis en fonction des vos [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-122">Some rules require monitoring thresholds or time thresholds that are best defined based on your specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span>  
  
 <span data-ttu-id="ed8f0-123">**Créer des règles supplémentaires si nécessaire, selon les règles incluses dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration**</span><span class="sxs-lookup"><span data-stu-id="ed8f0-123">**Create additional rules as necessary, based on the rules included in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack**</span></span>  
  
-   <span data-ttu-id="ed8f0-124">Les règles sont fournies pour une utilisation en tant que modèles pour les artefacts que vous créez, tel que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hôtes.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-124">Rules are provided for use as templates for artifacts that you create, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosts.</span></span> <span data-ttu-id="ed8f0-125">Vous devez utiliser ces modèles comme référence lorsque vous créez des règles spécifiques à un artefact, par exemple :</span><span class="sxs-lookup"><span data-stu-id="ed8f0-125">You should use these template rules as a reference when creating artifact-specific rules such as:</span></span>  
  
    -   <span data-ttu-id="ed8f0-126">Les règles spécifiques à l’hôte, par exemple, hébergent la surveillance de la file d’attente et hébergent la limitation d’analyse</span><span class="sxs-lookup"><span data-stu-id="ed8f0-126">Host-specific rules, for example, host queue monitoring, and host throttling monitoring</span></span>  
  
    -   <span data-ttu-id="ed8f0-127">Règles spécifiques à la MessageBox</span><span class="sxs-lookup"><span data-stu-id="ed8f0-127">MessageBox-specific rules</span></span>  
  
    -   <span data-ttu-id="ed8f0-128">des règles pour des composants tiers supplémentaires, comme l'adaptateur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="ed8f0-128">Rules for additional third party components, for example, MQSeries adapter</span></span>  
  
 <span data-ttu-id="ed8f0-129">**Surveiller tous les composants liés à BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="ed8f0-129">**Monitor all the BizTalk Server related components**</span></span>  
  
 <span data-ttu-id="ed8f0-130">Les composants de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement que vous devez surveiller pour vous assurer qu’ils sont en cours d’exécution incluent, mais ne sont pas nécessairement limité à :</span><span class="sxs-lookup"><span data-stu-id="ed8f0-130">The components of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that you should monitor to ensure that they are running include, but are not necessarily limited to:</span></span>  
  
-   <span data-ttu-id="ed8f0-131">Instances d'hôte BizTalk</span><span class="sxs-lookup"><span data-stu-id="ed8f0-131">BizTalk Host instances</span></span>  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]<span data-ttu-id="ed8f0-132">Travaux de l’agent installé avec[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed8f0-132"> Agent jobs installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="ed8f0-133">Des services personnalisés développés pour la solution BizTalk</span><span class="sxs-lookup"><span data-stu-id="ed8f0-133">Any custom services developed for the BizTalk solution</span></span>  
  
-   <span data-ttu-id="ed8f0-134">État de toutes les bases de données personnalisés développés pour la solution BizTalk</span><span class="sxs-lookup"><span data-stu-id="ed8f0-134">Status of any custom databases developed for the BizTalk solution</span></span>  
  
-   <span data-ttu-id="ed8f0-135">Toutes les entrées de journal des événements personnalisé pertinentes pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement</span><span class="sxs-lookup"><span data-stu-id="ed8f0-135">Any custom event log entries relevant to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed8f0-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed8f0-136">See Also</span></span>  
 [<span data-ttu-id="ed8f0-137">Analyse de BizTalk Server avec System Center Operations Manager 2007</span><span class="sxs-lookup"><span data-stu-id="ed8f0-137">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)