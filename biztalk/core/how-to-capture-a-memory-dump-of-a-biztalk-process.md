---
title: "Comment capturer une image mémoire d’un processus BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8053fcf3-b331-4245-b3c3-21290463e0c0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f87ad0f4a3eb3a49ea789d45a707bbc8b46cb4c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-biztalk-process"></a><span data-ttu-id="fcdaf-102">Capture de l'image mémoire d'un processus BizTalk</span><span class="sxs-lookup"><span data-stu-id="fcdaf-102">How to Capture a Memory Dump of a BizTalk Process</span></span>
<span data-ttu-id="fcdaf-103">Dans certaines circonstances, il peut être nécessaire de capturer l'image mémoire d'un processus exécuté sur un serveur BizTalk Server afin d'effectuer une analyse approfondie du processus.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-103">Under certain circumstances it may be necessary to capture a memory dump of a process running on a BizTalk Server to perform an in depth analysis of the process.</span></span> <span data-ttu-id="fcdaf-104">Les situations qui peuvent nécessiter l'analyse d'une image mémoire sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fcdaf-104">Situations that may require analysis of a memory dump include the following:</span></span>  
  
-   <span data-ttu-id="fcdaf-105">Un processus ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-105">When a process is unresponsive.</span></span>  
  
-   <span data-ttu-id="fcdaf-106">Un processus se bloque.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-106">When a process is crashing.</span></span>  
  
-   <span data-ttu-id="fcdaf-107">Un processus subit des fuites de mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-107">When a process leaks memory.</span></span>  
  
 <span data-ttu-id="fcdaf-108">Cette section inclut les étapes à suivre pour capturer le type approprié d'image mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-108">This section includes the steps that should be followed to capture the appropriate type of memory dump.</span></span>  
  
## <a name="installation-of-the-iis-diagnostics-toolkit"></a><span data-ttu-id="fcdaf-109">Installation de l'ensemble d'outils de diagnostic IIS</span><span class="sxs-lookup"><span data-stu-id="fcdaf-109">Installation of the IIS Diagnostics Toolkit</span></span>  
 <span data-ttu-id="fcdaf-110">Chacune des rubriques de cette section nécessite l’utilisation de la **outil** de la boîte à outils de diagnostic IIS pour capturer un vidage de mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-110">Each of the topics in this section requires the use of the **Debug Diagnostics Tool** of the IIS Diagnostics Toolkit to capture a memory dump.</span></span> <span data-ttu-id="fcdaf-111">Pour installer le **outil** de la boîte à outils de diagnostic IIS, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fcdaf-111">To install the **Debug Diagnostics Tool** of the IIS Diagnostics Toolkit follow these steps:</span></span>  
  
1.  <span data-ttu-id="fcdaf-112">Télécharger les outils de diagnostic IIS depuis [Internet Information Services des outils de Diagnostic](http://go.microsoft.com/fwlink/?LinkId=64426).</span><span class="sxs-lookup"><span data-stu-id="fcdaf-112">Download the IIS Diagnostics Toolkit from [Internet Information Services Diagnostic Tools](http://go.microsoft.com/fwlink/?LinkId=64426).</span></span>  
  
2.  <span data-ttu-id="fcdaf-113">Double-cliquez sur le **iisdiag.msi** package pour lancer le programme d’installation de IIS Diagnostics Toolkit et choisir le **personnalisé** type d’installation.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-113">Double-click the **iisdiag.msi** package to start the IIS Diagnostics Toolkit setup program and choose the **Custom** setup type.</span></span>  
  
3.  <span data-ttu-id="fcdaf-114">Dans le **installation personnalisée** boîte de dialogue, assurez-vous que l’option pour le **outil de débogage Diagnostics 1.0** est activée et suivez les étapes décrites dans le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="fcdaf-114">In the **Custom Setup** dialog, ensure that the option for the **Debug Diagnostics Tool 1.0** is enabled and complete the steps in the setup program.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fcdaf-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fcdaf-115">In This Section</span></span>  
  
-   [<span data-ttu-id="fcdaf-116">Comment capturer une image mémoire d’un processus qui ne répond pas</span><span class="sxs-lookup"><span data-stu-id="fcdaf-116">How to Capture a Memory Dump of a Process that is Non Responsive</span></span>](../core/how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive.md)  
  
-   [<span data-ttu-id="fcdaf-117">Comment capturer une image mémoire d’un processus bloqué</span><span class="sxs-lookup"><span data-stu-id="fcdaf-117">How to Capture a Memory Dump of a Process that is Crashing</span></span>](../core/how-to-capture-a-memory-dump-of-a-process-that-is-crashing.md)  
  
-   [<span data-ttu-id="fcdaf-118">Comment capturer une image mémoire d’un processus qui est une fuite de mémoire</span><span class="sxs-lookup"><span data-stu-id="fcdaf-118">How to Capture a Memory Dump of a Process that is Leaking Memory</span></span>](../core/how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory.md)  
  
-   [<span data-ttu-id="fcdaf-119">L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire</span><span class="sxs-lookup"><span data-stu-id="fcdaf-119">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)