---
title: "Comment capturer une image mémoire d’un processus qui ne répond pas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ad53376-2fab-4dee-8a6a-a44d157390f2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 520921010a8bbfd73de8c3b305a1270ca8363c46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive"></a><span data-ttu-id="70612-102">Capture de l'image mémoire d'un processus qui ne répond pas</span><span class="sxs-lookup"><span data-stu-id="70612-102">How to Capture a Memory Dump of a Process that is Non Responsive</span></span>
<span data-ttu-id="70612-103">Le processus BizTalk BTSNTSvc.exe est défini en tant que **négatif** lorsque le processus semble cesser de répondre.</span><span class="sxs-lookup"><span data-stu-id="70612-103">The BizTalk process BTSNTSvc.exe is defined as **hanging** when the process seems to stop responding.</span></span> <span data-ttu-id="70612-104">Les symptômes courants du blocage d'un processus sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="70612-104">Common symptoms of a process hang include:</span></span>  
  
-   <span data-ttu-id="70612-105">Les orchestrations semblent ne plus s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="70612-105">Orchestrations appear to stop running.</span></span>  
  
-   <span data-ttu-id="70612-106">Les messages ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="70612-106">Messages aren’t being processed.</span></span>  
  
-   <span data-ttu-id="70612-107">Des problèmes généraux de délai d'expiration apparaissent.</span><span class="sxs-lookup"><span data-stu-id="70612-107">General timeout issues occur.</span></span>  
  
-   <span data-ttu-id="70612-108">Le processus BizTalk BTSNTSvc.exe consomme une quantité anormalement élevée de cycles de processeur tel qu’affiché dans le **processus** onglet de **le Gestionnaire des tâches**.</span><span class="sxs-lookup"><span data-stu-id="70612-108">The BizTalk process BTSNTSvc.exe consumes an unusually high amount of CPU cycles as viewed in the **Processes** tab of **Task Manager**.</span></span>  
  
 <span data-ttu-id="70612-109">Pour capturer l'image mémoire d'un processus BTSNTSvc.exe bloqué, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="70612-109">To capture a memory dump of a hanging BTSNTSvc.exe process, follow these steps.</span></span>  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-hang-dump"></a><span data-ttu-id="70612-110">Pour configurer l’outil de diagnostic de débogage pour capturer un vidage de blocage</span><span class="sxs-lookup"><span data-stu-id="70612-110">To configure the Debug Diagnostics tool to capture a hang dump</span></span>  
  
1.  <span data-ttu-id="70612-111">Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.</span><span class="sxs-lookup"><span data-stu-id="70612-111">Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="70612-112">Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Configuration des règles s’affiche, cliquez sur le **Annuler** bouton.</span><span class="sxs-lookup"><span data-stu-id="70612-112">If the **Select Rule Type** dialog of the Rules Configuration Wizard is displayed, click the **Cancel** button.</span></span>  
  
3.  <span data-ttu-id="70612-113">Cliquez sur le **processus** onglet de l’outil de Diagnostic de débogage.</span><span class="sxs-lookup"><span data-stu-id="70612-113">Click the **Processes** tab of the Debug Diagnostic Tool.</span></span>  
  
4.  <span data-ttu-id="70612-114">Cliquez avec le bouton droit sur le processus BTSNTSvc.exe qui ne répond pas et sélectionnez **créer une image utilisateur complète**.</span><span class="sxs-lookup"><span data-stu-id="70612-114">Right click the unresponsive BTSNTSvc.exe process and select **Create Full Userdump**.</span></span> <span data-ttu-id="70612-115">Par défaut, une image mémoire du processus sera enregistré dans le répertoire \Program Files\IIS Resources\DebugDiag\Logs\Misc de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="70612-115">By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\Misc directory of the local computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70612-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70612-116">See Also</span></span>  
 [<span data-ttu-id="70612-117">L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire</span><span class="sxs-lookup"><span data-stu-id="70612-117">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)