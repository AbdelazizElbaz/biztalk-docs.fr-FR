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
# <a name="enabling-systemnet-logging"></a><span data-ttu-id="53b57-102">Activation de la consignation System.Net</span><span class="sxs-lookup"><span data-stu-id="53b57-102">Enabling System.Net Logging</span></span>
<span data-ttu-id="53b57-103">Vous pouvez activer la journalisation pour le `System.Net` et `System.Net.Sockets` [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] espace de noms du service BTSNtSvc.exe.</span><span class="sxs-lookup"><span data-stu-id="53b57-103">You can enable logging for the `System.Net` and `System.Net.Sockets`[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] namespace for the BTSNtSvc.exe service.</span></span> <span data-ttu-id="53b57-104">De cette façon, un fichier journal sera créé, qui contiendra des informations détaillées sur les problèmes rencontrés avec votre installation BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="53b57-104">This will cause a detailed log file to be created containing information that may help you identify issues with your BizTalk Server installation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53b57-105">Il s'agit d'une fonction de Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] compatible avec [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="53b57-105">This is a feature of the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] and will work in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] or later.</span></span>  
  
 <span data-ttu-id="53b57-106">Le suivi est activé en modifiant le fichier de configuration d’application pour **BTSNtSvc.exe**, **BTSNtSvc.exe.config**. Ce fichier se trouve dans le répertoire d'installation de BizTalk Server. Si vous avez installé BizTalk Server dans son emplacement par défaut, BtsNtSvc.exe se trouve dans le répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53b57-106">Tracing is enabled by modifying the application configuration file for **BTSNtSvc.exe**,  **BTSNtSvc.exe.config**. It can be found in the BizTalk Server installation path; if you installed BizTalk Server to the default location, BtsNtSvc.exe will be in the directory [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="53b57-107">Pour modifier **BTSNtSvc.exe.config**, ouvrez le fichier de configuration et collez le code ci-dessous dans le `<configuration>` élément à l’aide du bloc-notes ou votre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="53b57-107">To modify **BTSNtSvc.exe.config**, open the configuration file and paste the code below into the `<configuration>` element using Notepad or your favorite text editor.</span></span>  
  
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
  
 <span data-ttu-id="53b57-108">Le fichier journal est écrite dans le même répertoire que celui qui contient BTSNtSvc.exe.</span><span class="sxs-lookup"><span data-stu-id="53b57-108">The log file will be written to the same directory that contains BTSNtSvc.exe.</span></span> <span data-ttu-id="53b57-109">Si vous avez installé à l’emplacement par défaut, il n’est écrit pour [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53b57-109">If you installed to the default location, it will be written to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b57-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53b57-110">See Also</span></span>  
 [<span data-ttu-id="53b57-111">Interprétation du traçage réseau</span><span class="sxs-lookup"><span data-stu-id="53b57-111">Interpreting Network Tracing</span></span>](http://go.microsoft.com/fwlink/?LinkId=78679)