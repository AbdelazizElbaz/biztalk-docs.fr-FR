---
title: Activation de la journalisation de System.Net | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eea50b9-1f46-45fc-a327-585adb4583a0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e672f2b9e7ae8b0ef3889493273660c8ef9140c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-systemnet-logging"></a>Activation de la consignation System.Net
Vous pouvez activer la journalisation pour le `System.Net` et `System.Net.Sockets` [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] espace de noms du service BTSNtSvc.exe. De cette façon, un fichier journal sera créé, qui contiendra des informations détaillées sur les problèmes rencontrés avec votre installation BizTalk Server.  
  
> [!NOTE]
>  Il s'agit d'une fonction de Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] compatible avec [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] ou une version ultérieure.  
  
 Le suivi est activé en modifiant le fichier de configuration d’application pour **BTSNtSvc.exe**, **BTSNtSvc.exe.config**. Ce fichier se trouve dans le répertoire d'installation de BizTalk Server. Si vous avez installé BizTalk Server dans son emplacement par défaut, BtsNtSvc.exe se trouve dans le répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
 Pour modifier **BTSNtSvc.exe.config**, ouvrez le fichier de configuration et collez le code ci-dessous dans le `<configuration>` élément à l’aide du bloc-notes ou votre éditeur de texte.  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="System.Net" switchValue="Verbose">  
      <listeners>  
        <add name="System.Net"/>  
      </listeners>  
    </source>  
    <source name="System.Net.Sockets" switchValue="Verbose">  
      <listeners>  
        <add name="System.Net"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="System.Net"  
          type="System Diagnostics.TextWriterTraceListener"  
          initializeData="System.Net..log"/>  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 Le fichier journal est écrite dans le même répertoire que celui qui contient BTSNtSvc.exe. Si vous avez installé à l’emplacement par défaut, il n’est écrit pour [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Interprétation du traçage réseau](http://go.microsoft.com/fwlink/?LinkId=78679)