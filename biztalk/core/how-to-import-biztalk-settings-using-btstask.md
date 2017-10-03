---
title: "Importer ou exporter des paramètres de BizTalk à l’aide de BTSTask | Documents Microsoft"
description: "Utilisez les commandes ImportSettings ou ExportSettings BTSTask pour déplacer les paramètres à partir d’un environnement à un autre dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3fdd8c9-3534-4c11-8acc-6cb6f5bf0989
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99aecaea767133fc5f3cb77d38dc174b09733674
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-btstask-to-import-or-export-biztalk-settings"></a><span data-ttu-id="d3ca5-103">Utilisez BTSTask pour importer ou exporter des paramètres de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d3ca5-103">Use BTSTask to import or export BizTalk settings</span></span>

## <a name="overview"></a><span data-ttu-id="d3ca5-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="d3ca5-104">Overview</span></span>
<span data-ttu-id="d3ca5-105">À l'aide de l'utilitaire de ligne de commande BTSTask, vous pouvez exporter les paramètres d'un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les importer vers un autre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], réduisant ainsi le délai global de mise en œuvre d'une solution.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-105">Using the BTSTask command-line utility, you can export the settings from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment and import them to another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, thereby reducing the overall time-to-solution.</span></span> <span data-ttu-id="d3ca5-106">Ceci est particulièrement utile dans les scénarios où les administrateurs tentent d'ajuster les performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement intermédiaire et, lorsque les résultats souhaités sont atteints, ils peuvent importer les paramètres dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-106">This is especially useful in scenarios where the administrators try to tune [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance in a staging environment, and upon achieving the desired results, they can import the settings into a production environment.</span></span> 

<span data-ttu-id="d3ca5-107">Cette rubrique répertorie les étapes pour importer ou exporter les paramètres de BizTalk Server à partir d’un environnement à l’autre **BTSTask.exe**.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-107">This topic lists the steps to import or export the BizTalk Server settings from one environment to another using **BTSTask.exe**.</span></span>  


## <a name="import-biztalk-settings"></a><span data-ttu-id="d3ca5-108">Importer les paramètres de BizTalk</span><span class="sxs-lookup"><span data-stu-id="d3ca5-108">Import BizTalk settings</span></span> 
> [!IMPORTANT]
>  <span data-ttu-id="d3ca5-109">Avant d'importer les paramètres de BizTalk Server à partir d'un environnement spécifique, vous devez exporter et enregistrer ceux-ci dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-109">To import the BizTalk settings from a certain environment, you should have already exported and saved those settings in an XML file.</span></span> <span data-ttu-id="d3ca5-110">Pour plus d’informations sur l’exportation des paramètres, consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) ou **exporter des paramètres de BizTalk à l’aide de BTSTask** (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="d3ca5-110">For more information about exporting the settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) or **Export BizTalk Settings Using BTSTask** (in this topic).</span></span>  
  
 <span data-ttu-id="d3ca5-111">En important le fichier XML, vous pouvez répliquer les paramètres de BizTalk Server requis sur l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-111">By importing the XML file, you can replicate the required BizTalk Server settings on the target machine.</span></span> <span data-ttu-id="d3ca5-112">À l’aide de la **BTSTask.exe**, vous pouvez importer les paramètres de groupe, d’hôte et d’Instance de l’hôte et mapper les propriétés d’une à l’autre.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-112">Using the **BTSTask.exe**, you can import the Group, Host, and Host Instance settings and map the properties of one to another.</span></span> <span data-ttu-id="d3ca5-113">Ci-après sont présentées les hypothèses nécessaires pour importer les paramètres :</span><span class="sxs-lookup"><span data-stu-id="d3ca5-113">Following are the necessary assumptions for importing the settings:</span></span>  
  
-   <span data-ttu-id="d3ca5-114">Vous pouvez importer les paramètres de BizTalk Server sur des topologies similaires.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-114">You can import the BizTalk Server settings across similar topologies.</span></span>  
  
-   <span data-ttu-id="d3ca5-115">Vous devez pouvoir mapper les instances d'hôte source et d'hôte à leurs équivalents de destination.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-115">You should be able to map the source Host and Host Instances to the destination counterparts.</span></span>  
  
-   <span data-ttu-id="d3ca5-116">L'environnement de destination possède un matériel similaire (sinon identique) à l'environnement source.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-116">The destination environment has hardware similar (if not identical) to the source environment.</span></span> <span data-ttu-id="d3ca5-117">Ceci est essentiel car certains paramètres dépendent du matériel sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-117">This is essential as some of the settings depend on the underlying hardware.</span></span>  
  
### <a name="importsettings-command"></a><span data-ttu-id="d3ca5-118">Commande ImportSettings</span><span class="sxs-lookup"><span data-stu-id="d3ca5-118">ImportSettings command</span></span> 
 <span data-ttu-id="d3ca5-119">Vous pouvez utiliser la **ImportSettings** commande BTSTask pour importer les paramètres de BizTalk Server à partir de l’environnement source vers l’environnement de destination.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-119">You can use the **ImportSettings** BTSTask command to import BizTalk Server settings from the source environment to destination environment.</span></span> <span data-ttu-id="d3ca5-120">Consultez [commande ImportSettings](../core/importsettings-command.md) pour des détails spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-120">See [ImportSettings Command](../core/importsettings-command.md) for specific details.</span></span>  
  
 <span data-ttu-id="d3ca5-121">Vous pouvez définir le mappage d'un hôte source à un hôte de destination et/ou d'une instance d'hôte source à une instance d'hôte de destination comme suit :</span><span class="sxs-lookup"><span data-stu-id="d3ca5-121">You can define the mapping from a source host to a destination host and/or a source host instance to a destination host instance as shown:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SettingsMap>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <HostMappings>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="BizTalkServerApplication">  
  <DestinationHosts>BizTalkServerApplication</DestinationHosts>   
  </SourceHost>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="BizTalkServerIsolatedHost">  
  <DestinationHosts>BizTalkServerIsolatedHost</DestinationHosts>   
  </SourceHost>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="Host1">  
  <DestinationHosts>Host2</DestinationHosts>   
  </SourceHost>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHost Name="Host2">  
  <DestinationHosts>Host1;Host3;Host4;Host5</DestinationHosts>   
  </SourceHost>  
  </HostMappings>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <HostInstanceMappings>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHostInstance Name="BizTalkServerApplication:COMPUTER_NAME1">  
  <DestinationHostInstances>BizTalkServerApplication:COMPUTER_NAME2</DestinationHostInstances>   
  </SourceHostInstance>  
 HYPERLINK "file:///C:\\Users\\v-dhgunt\\AppData\\Local\\Microsoft\\Windows\\Temporary%20Internet%20Files\\Content.Outlook\\05083AAB\\ImportMap_PosScenario.xml" - <SourceHostInstance Name="Host1:COMPUTER_NAME1">  
  <DestinationHostInstances>Host2:COMPUTER_NAME2;Host3:COMPUTER_NAME3;Host4:COMPUTER_NAME4;Host5:COMPUTER_NAME5</DestinationHostInstances>   
  </SourceHostInstance>  
  </HostInstanceMappings>  
  </SettingsMap>  
  
```  
  
 <span data-ttu-id="d3ca5-122">Dans un fichier de mappage, entrez une instance d’hôte en tant que « Nomhôte : nommachine ».</span><span class="sxs-lookup"><span data-stu-id="d3ca5-122">In a map file, enter a host instance as 'HostName:MachineName'.</span></span> <span data-ttu-id="d3ca5-123">Par exemple, « Host1:Server1 » signifie que l'instance de l'hôte « Host1 » s'exécute (ou est présente) sur l'ordinateur « Server1 ».</span><span class="sxs-lookup"><span data-stu-id="d3ca5-123">For example: "Host1:Server1" means the instance of host 'Host1' which is running (or present) on machine 'Server1".</span></span>  
  
 <span data-ttu-id="d3ca5-124">Pour entrer la source de 1 à n mappages de destination, utilisez une liste délimitée par des points-virgules.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-124">To enter 1:n source to destination mappings, use a semicolon-separated list.</span></span> <span data-ttu-id="d3ca5-125">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d3ca5-125">For example:</span></span>  
  
```  
SourceHost Name="SourceHost1"   
......DestinationHosts   
............DestHost1;DestHost2;DestHost3   
....../DestinationHosts   
/SourceHost  
```  
  
 <span data-ttu-id="d3ca5-126">Il n'est possible de mapper que les instances d'hôte pour lesquelles le mappage d'hôte correspondant a également été créé.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-126">Only those host-instances can be mapped for which the corresponding host mapping has also been created.</span></span> <span data-ttu-id="d3ca5-127">Si « SourceHost1 » a été mappé à « DestinationHost1 » dans les mappages de l'hôte, les (éventuelles) instances de « DestinationHost1 » ne pourront être mappées qu'aux (éventuelles) instances de « SourceHost1 ».</span><span class="sxs-lookup"><span data-stu-id="d3ca5-127">If 'SourceHost1' has been mapped to 'DestinationHost1' in host mappings, the instances (if any) of 'DestinationHost1' can be mapped only to the instances (if any) of 'SourceHost1'.</span></span> <span data-ttu-id="d3ca5-128">L'assistant d'importation de l'interface utilisateur tient compte de cette contrainte.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-128">The UI Import Wizard takes care of this constraint.</span></span> <span data-ttu-id="d3ca5-129">Ceci devrait être écrit de façon explicite dans le fichier de mappage.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-129">You would need to explicitly write it in the map file.</span></span>  


## <a name="export-biztalk-settings"></a><span data-ttu-id="d3ca5-130">Exporter les paramètres de BizTalk</span><span class="sxs-lookup"><span data-stu-id="d3ca5-130">Export BizTalk settings</span></span>  

<span data-ttu-id="d3ca5-131">Il existe deux façons pour exporter les paramètres de BizTalk :</span><span class="sxs-lookup"><span data-stu-id="d3ca5-131">There are a couple of ways to export the BizTalk settings:</span></span> 

1. <span data-ttu-id="d3ca5-132">Utilisez le **ExportSettings** commande BTSTask pour exporter les paramètres de BizTalk Server de l’environnement source vers un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-132">Use the **ExportSettings** BTSTask command to export the BizTalk Server settings of the source environment to an XML file.</span></span> <span data-ttu-id="d3ca5-133">Consultez [commande ExportSettings](../core/exportsettings-command.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-133">See [ExportSettings Command](../core/exportsettings-command.md) for more details.</span></span>  

2.  <span data-ttu-id="d3ca5-134">Dans Administration de BizTalk Server, utilisez le panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-134">Use the Settings Dashboard in BizTalk Server Administration.</span></span> <span data-ttu-id="d3ca5-135">Consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) pour connaître les étapes.</span><span class="sxs-lookup"><span data-stu-id="d3ca5-135">See [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) for the steps.</span></span>

 
> [!TIP]
>  <span data-ttu-id="d3ca5-136">Pour plus d’informations sur la façon dont les paramètres de BizTalk Server dans un fichier XML sont appliqués à l’environnement cible, consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md).</span><span class="sxs-lookup"><span data-stu-id="d3ca5-136">For information about how the BizTalk Server settings in an XML file are applied to the target environment, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="d3ca5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3ca5-137">See Also</span></span>  
 [<span data-ttu-id="d3ca5-138">Automatiser BizTalk Server réglage des performances</span><span class="sxs-lookup"><span data-stu-id="d3ca5-138">Automate BizTalk Server Performance Tuning</span></span>](../core/automating-biztalk-server-performance-tuning.md)