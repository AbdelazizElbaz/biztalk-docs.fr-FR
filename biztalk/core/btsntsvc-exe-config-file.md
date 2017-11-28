---
title: Fichier BTSNTSvc.exe.config | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2bb89a7-4fff-4ccf-a0a7-20ca610f2ddf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 303924e2aaf8304388a18d2ffe70d99fdc69acd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btsntsvcexeconfig-file"></a><span data-ttu-id="07ad5-102">Fichier BTSNTSvc.exe.config</span><span class="sxs-lookup"><span data-stu-id="07ad5-102">BTSNTSvc.exe.config File</span></span>
<span data-ttu-id="07ad5-103">Les propriétés de mise en file d’attente et leur valeur par défaut peuvent être configurées dans le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] ou dans le code XML du fichier de configuration de BizTalk (BTSNTSvc.exe.config ou BTSNTSvc64.exe.config).</span><span class="sxs-lookup"><span data-stu-id="07ad5-103">Dehydration properties and their default values are configurable in [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] or as XML in the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config).</span></span> <span data-ttu-id="07ad5-104">Les valeurs contenues dans le fichier de configuration de BizTalk sont appliquées en premier.</span><span class="sxs-lookup"><span data-stu-id="07ad5-104">The values in the BizTalk configuration file are applied first.</span></span> <span data-ttu-id="07ad5-105">Les paramètres du [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] sont ensuite appliqués.</span><span class="sxs-lookup"><span data-stu-id="07ad5-105">Then, the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] settings are applied.</span></span> <span data-ttu-id="07ad5-106">Les propriétés de mise en attente sont lues lorsque toutes les instances de l’hôte contenant une orchestration démarrent.</span><span class="sxs-lookup"><span data-stu-id="07ad5-106">The dehydration properties are read when all host instances containing an orchestration start.</span></span>  
  
 <span data-ttu-id="07ad5-107">Cette rubrique décrit le fichier de configuration de BizTalk (BTSNTSvc.exe.config ou BTSNTSvc64.exe.config).</span><span class="sxs-lookup"><span data-stu-id="07ad5-107">This topic focuses on the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config).</span></span> <span data-ttu-id="07ad5-108">De nombreuses propriétés de mise en file d’attente ne sont pas répertoriées.</span><span class="sxs-lookup"><span data-stu-id="07ad5-108">Many dehydration properties are not listed.</span></span> <span data-ttu-id="07ad5-109">Ces propriétés et leurs valeurs par défaut sont toujours appliquées, même si elles ne sont pas explicitement spécifiées dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="07ad5-109">These properties and their default values are still applied, even if they are not explicitly specified in the configuration file.</span></span>  
  
 <span data-ttu-id="07ad5-110">Pour modifier les valeurs par défaut, vous devez les ajouter explicitement dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="07ad5-110">To change the default values, you must explicitly add them to your configuration file.</span></span> <span data-ttu-id="07ad5-111">Pour plus d’informations sur la façon de modifier le comportement de mise en attente par défaut, consultez [comment modifier les paramètres de limitation d’Orchestration](../core/how-to-modify-orchestration-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="07ad5-111">For information about how to change the default dehydration behavior, see [How to Modify Orchestration Throttling Settings](../core/how-to-modify-orchestration-throttling-settings.md).</span></span> <span data-ttu-id="07ad5-112">Pour plus d’informations sur la limitation de mémoire d’orchestration, consultez [comment modifier les paramètres de limitation de la mémoire de Orchestration](../core/how-to-modify-orchestration-memory-throttling-settings.md).</span><span class="sxs-lookup"><span data-stu-id="07ad5-112">For information about orchestration memory throttling, see [How to Modify Orchestration Memory Throttling Settings](../core/how-to-modify-orchestration-memory-throttling-settings.md).</span></span>  
  
 <span data-ttu-id="07ad5-113">Le contenu du fichier BTSNTSvc.exe.config est présenté ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="07ad5-113">Following is the contents of the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="07ad5-114">Ce fichier se trouve toujours dans le même répertoire que le fichier BTSNTSvc.exe, qui figure généralement à l'emplacement C:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07ad5-114">This file is always located in the same directory as the BTSNTSvc.exe file, which is usually C:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
```  
<?xml version="1.0" ?>  
<configuration>  
       <configSections>  
              <section name="xlangs" type="Microsoft.XLANGs.BizTalk.CrossProcess.XmlSerializationConfigurationSectionHandler, Microsoft.XLANGs.BizTalk.CrossProcess" />  
       </configSections>  
       <runtime>  
              <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
                     <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking" />  
              </assemblyBinding>  
       </runtime>  
       <xlangs>  
              <Configuration>  
                     <Dehydration MaxThreshold="1800" MinThreshold="1" ConstantThreshold="-1">  
                            <VirtualMemoryThrottlingCriteria OptimalUsage="900" MaximalUsage="1300" IsActive="true" />  
                            <PrivateMemoryThrottlingCriteria OptimalUsage="50" MaximalUsage="350" IsActive="true" />  
                            <PhysicalMemoryThrottlingCriteria OptimalUsage="50" MaximalUsage="350" IsActive="false" />  
                     </Dehydration>  
              </Configuration>  
       </xlangs>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07ad5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07ad5-115">See Also</span></span>  
 [<span data-ttu-id="07ad5-116">À l’aide du Panneau de configuration de BizTalk Server réglage des performances</span><span class="sxs-lookup"><span data-stu-id="07ad5-116">Using Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)