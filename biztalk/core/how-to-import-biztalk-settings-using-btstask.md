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
# <a name="use-btstask-to-import-or-export-biztalk-settings"></a>Utilisez BTSTask pour importer ou exporter des paramètres de BizTalk Server

## <a name="overview"></a>Vue d'ensemble
À l'aide de l'utilitaire de ligne de commande BTSTask, vous pouvez exporter les paramètres d'un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les importer vers un autre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], réduisant ainsi le délai global de mise en œuvre d'une solution. Ceci est particulièrement utile dans les scénarios où les administrateurs tentent d'ajuster les performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement intermédiaire et, lorsque les résultats souhaités sont atteints, ils peuvent importer les paramètres dans un environnement de production. 

Cette rubrique répertorie les étapes pour importer ou exporter les paramètres de BizTalk Server à partir d’un environnement à l’autre **BTSTask.exe**.  


## <a name="import-biztalk-settings"></a>Importer les paramètres de BizTalk 
> [!IMPORTANT]
>  Avant d'importer les paramètres de BizTalk Server à partir d'un environnement spécifique, vous devez exporter et enregistrer ceux-ci dans un fichier XML. Pour plus d’informations sur l’exportation des paramètres, consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) ou **exporter des paramètres de BizTalk à l’aide de BTSTask** (dans cette rubrique).  
  
 En important le fichier XML, vous pouvez répliquer les paramètres de BizTalk Server requis sur l'ordinateur cible. À l’aide de la **BTSTask.exe**, vous pouvez importer les paramètres de groupe, d’hôte et d’Instance de l’hôte et mapper les propriétés d’une à l’autre. Ci-après sont présentées les hypothèses nécessaires pour importer les paramètres :  
  
-   Vous pouvez importer les paramètres de BizTalk Server sur des topologies similaires.  
  
-   Vous devez pouvoir mapper les instances d'hôte source et d'hôte à leurs équivalents de destination.  
  
-   L'environnement de destination possède un matériel similaire (sinon identique) à l'environnement source. Ceci est essentiel car certains paramètres dépendent du matériel sous-jacent.  
  
### <a name="importsettings-command"></a>Commande ImportSettings 
 Vous pouvez utiliser la **ImportSettings** commande BTSTask pour importer les paramètres de BizTalk Server à partir de l’environnement source vers l’environnement de destination. Consultez [commande ImportSettings](../core/importsettings-command.md) pour des détails spécifiques.  
  
 Vous pouvez définir le mappage d'un hôte source à un hôte de destination et/ou d'une instance d'hôte source à une instance d'hôte de destination comme suit :  
  
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
  
 Dans un fichier de mappage, entrez une instance d’hôte en tant que « Nomhôte : nommachine ». Par exemple, « Host1:Server1 » signifie que l'instance de l'hôte « Host1 » s'exécute (ou est présente) sur l'ordinateur « Server1 ».  
  
 Pour entrer la source de 1 à n mappages de destination, utilisez une liste délimitée par des points-virgules. Exemple :  
  
```  
SourceHost Name="SourceHost1"   
......DestinationHosts   
............DestHost1;DestHost2;DestHost3   
....../DestinationHosts   
/SourceHost  
```  
  
 Il n'est possible de mapper que les instances d'hôte pour lesquelles le mappage d'hôte correspondant a également été créé. Si « SourceHost1 » a été mappé à « DestinationHost1 » dans les mappages de l'hôte, les (éventuelles) instances de « DestinationHost1 » ne pourront être mappées qu'aux (éventuelles) instances de « SourceHost1 ». L'assistant d'importation de l'interface utilisateur tient compte de cette contrainte. Ceci devrait être écrit de façon explicite dans le fichier de mappage.  


## <a name="export-biztalk-settings"></a>Exporter les paramètres de BizTalk  

Il existe deux façons pour exporter les paramètres de BizTalk : 

1. Utilisez le **ExportSettings** commande BTSTask pour exporter les paramètres de BizTalk Server de l’environnement source vers un fichier XML. Consultez [commande ExportSettings](../core/exportsettings-command.md) pour plus d’informations.  

2.  Dans Administration de BizTalk Server, utilisez le panneau de configuration. Consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) pour connaître les étapes.

 
> [!TIP]
>  Pour plus d’informations sur la façon dont les paramètres de BizTalk Server dans un fichier XML sont appliqués à l’environnement cible, consultez [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md). 
  
## <a name="see-also"></a>Voir aussi  
 [Automatiser BizTalk Server réglage des performances](../core/automating-biztalk-server-performance-tuning.md)