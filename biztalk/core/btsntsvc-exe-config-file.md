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
# <a name="btsntsvcexeconfig-file"></a>Fichier BTSNTSvc.exe.config
Les propriétés de mise en file d’attente et leur valeur par défaut peuvent être configurées dans le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] ou dans le code XML du fichier de configuration de BizTalk (BTSNTSvc.exe.config ou BTSNTSvc64.exe.config). Les valeurs contenues dans le fichier de configuration de BizTalk sont appliquées en premier. Les paramètres du [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] sont ensuite appliqués. Les propriétés de mise en attente sont lues lorsque toutes les instances de l’hôte contenant une orchestration démarrent.  
  
 Cette rubrique décrit le fichier de configuration de BizTalk (BTSNTSvc.exe.config ou BTSNTSvc64.exe.config). De nombreuses propriétés de mise en file d’attente ne sont pas répertoriées. Ces propriétés et leurs valeurs par défaut sont toujours appliquées, même si elles ne sont pas explicitement spécifiées dans le fichier de configuration.  
  
 Pour modifier les valeurs par défaut, vous devez les ajouter explicitement dans le fichier de configuration. Pour plus d’informations sur la façon de modifier le comportement de mise en attente par défaut, consultez [comment modifier les paramètres de limitation d’Orchestration](../core/how-to-modify-orchestration-throttling-settings.md). Pour plus d’informations sur la limitation de mémoire d’orchestration, consultez [comment modifier les paramètres de limitation de la mémoire de Orchestration](../core/how-to-modify-orchestration-memory-throttling-settings.md).  
  
 Le contenu du fichier BTSNTSvc.exe.config est présenté ci-dessous. Ce fichier se trouve toujours dans le même répertoire que le fichier BTSNTSvc.exe, qui figure généralement à l'emplacement C:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)