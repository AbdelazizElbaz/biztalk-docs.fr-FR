---
title: "À l’aide du suivi d’événements pour Windows3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- provider
- Receiver Logging Provider
- Transmitter Logging Provider
- controller application
- consumer application
- BTATIBCOEMSTrace command
- Event Tracing for Windows
ms.assetid: 71954431-2015-4d50-b69e-500c883b1e04
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75b2b339c99dcf1b64368c73381d1dbe81e0fb39
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="05358-102">À l’aide d’événements de suivi pour Windows</span><span class="sxs-lookup"><span data-stu-id="05358-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="05358-103">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows.</span><span class="sxs-lookup"><span data-stu-id="05358-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="05358-104">Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="05358-104">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="05358-105">Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="05358-105">When ETW is activated, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="05358-106">Ce fichier au format binaire doit être converti pour être lu.</span><span class="sxs-lookup"><span data-stu-id="05358-106">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="05358-107">Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe.</span><span class="sxs-lookup"><span data-stu-id="05358-107">To do this, you must have a consumer application available to interpret the \*.etl file, for example, tracerpt.exe or tracedmp.exe.</span></span> <span data-ttu-id="05358-108">Par exemple, l’application tracerpt.exe convertit le \*fichier .etl dans deux fichiers texte : summary.txt et dumpfile.csv.</span><span class="sxs-lookup"><span data-stu-id="05358-108">For example, the tracerpt.exe application converts the \*.etl file into two text files: summary.txt and dumpfile.csv.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="05358-109">Composants ETW</span><span class="sxs-lookup"><span data-stu-id="05358-109">ETW Components</span></span>  
 <span data-ttu-id="05358-110">Le Suivi d'événements pour Windows comporte trois composants :</span><span class="sxs-lookup"><span data-stu-id="05358-110">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="05358-111">**Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).</span><span class="sxs-lookup"><span data-stu-id="05358-111">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="05358-112">Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="05358-112">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="05358-113">Cela permet de s’assurer que les appels BTATIBCO EMSTrace peuvent localiser tracelog.exe dans le système.</span><span class="sxs-lookup"><span data-stu-id="05358-113">This makes sure that BTATIBCO EMSTrace calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="05358-114">Par défaut, BTATIBCO EMSTrace recherche le chemin d'accès actuel.</span><span class="sxs-lookup"><span data-stu-id="05358-114">By default, BTATIBCO EMSTrace searches the current path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05358-115">tracelog.exe est disponible dans le Kit de développement logiciel Microsoft (SDK) et est compatible avec les commandes fournies par l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service.</span><span class="sxs-lookup"><span data-stu-id="05358-115">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by Microsoft BizTalk Adapter for TIBCO Enterprise Message Service.</span></span> <span data-ttu-id="05358-116">Pour utiliser logman.exe, consultez la documentation de logman.</span><span class="sxs-lookup"><span data-stu-id="05358-116">To use logman.exe, see the logman documentation.</span></span>  
  
-   <span data-ttu-id="05358-117">**Application consommateur**: lit les événements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="05358-117">**Consumer application**: Reads logged events.</span></span>  
  
     <span data-ttu-id="05358-118">Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="05358-118">For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="05358-119">Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.</span><span class="sxs-lookup"><span data-stu-id="05358-119">Typically this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="05358-120">Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel\> = -rt.</span><span class="sxs-lookup"><span data-stu-id="05358-120">To use the consumer application without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.</span></span>  
  
-   <span data-ttu-id="05358-121">**Fournisseur**: fournit l’événement.</span><span class="sxs-lookup"><span data-stu-id="05358-121">**Provider**: Provides the event.</span></span>  
  
     <span data-ttu-id="05358-122">L'adaptateur BizTalk pour TIBCO Enterprise Message Service inclut trois fournisseurs distincts,</span><span class="sxs-lookup"><span data-stu-id="05358-122">BizTalk Adapter for TIBCO Enterprise Message Service includes three different providers.</span></span> <span data-ttu-id="05358-123">Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="05358-123">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="05358-124">Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="05358-124">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="05358-125">L'adaptateur BizTalk pour TIBCO Enterprise Message Service inclut des fournisseurs qui permettent de consigner plusieurs types de messages :</span><span class="sxs-lookup"><span data-stu-id="05358-125">BizTalk Adapter for TIBCO Enterprise Message Service has providers that enable you to log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="05358-126">**Fournisseur de journalisation de récepteur**: le \<élément Trace\> commutateur est **-récepteur**.</span><span class="sxs-lookup"><span data-stu-id="05358-126">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span>  
  
     <span data-ttu-id="05358-127">Utilisez **-récepteur** pour obtenir tous les messages du journal qui ont été reçus par l’adaptateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="05358-127">Use **-receiver** to obtain any messages from the log that were received by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="05358-128">**Fournisseur de journalisation de l’émetteur**: le \<élément Trace\> commutateur est **-émetteur**.</span><span class="sxs-lookup"><span data-stu-id="05358-128">**Transmitter Logging Provider**: the \<Trace element\> switch is **-transmitter**.</span></span>  
  
     <span data-ttu-id="05358-129">Utilisez **-émetteur**pour obtenir tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="05358-129">Use **-transmitter**to obtain any messages from the log that were transmitted by the adapter at run time.</span></span>  
  
### <a name="btatibcoemstrace-command"></a><span data-ttu-id="05358-130">Commande BTATIBCOEMSTrace</span><span class="sxs-lookup"><span data-stu-id="05358-130">BTATIBCOEMSTrace Command</span></span>  
 <span data-ttu-id="05358-131">Pour utiliser ETW, exécutez l’adaptateur BizTalk pour commande TIBCO Enterprise Message Service (btatibcoemstrace.cmd).</span><span class="sxs-lookup"><span data-stu-id="05358-131">To use ETW, run the BizTalk Adapter for TIBCO Enterprise Message Service command, BTATIBCOEMSTrace.cmd.</span></span> <span data-ttu-id="05358-132">Utilisez-la comme suit :</span><span class="sxs-lookup"><span data-stu-id="05358-132">You use this command as follows:</span></span>  
  
```  
BTATIBCOEMSTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTA TIBCOEMSTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="05358-133">Où :</span><span class="sxs-lookup"><span data-stu-id="05358-133">Where:</span></span>  
  
-   <span data-ttu-id="05358-134">**\<Élément trace\>**  (obligatoire) est le type de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="05358-134">**\<Trace element\>** (required) is the kind of provider.</span></span>  
  
 <span data-ttu-id="05358-135">Les options associées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="05358-135">Its options are as follows:</span></span>  
  
-   <span data-ttu-id="05358-136">**-émetteur**</span><span class="sxs-lookup"><span data-stu-id="05358-136">**-transmitter**</span></span>  
  
-   <span data-ttu-id="05358-137">**-récepteur**</span><span class="sxs-lookup"><span data-stu-id="05358-137">**-receiver**</span></span>  
  
-   <span data-ttu-id="05358-138">**-start, - stop**: activer ou désactiver le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="05358-138">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="05358-139">**-cir \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="05358-139">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="05358-140">**-cir** est un fichier circulaire.</span><span class="sxs-lookup"><span data-stu-id="05358-140">**-cir** is a circular file.</span></span> <span data-ttu-id="05358-141">**\<Mo\>**: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="05358-141">**\<MB\>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="05358-142">**-seq \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="05358-142">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="05358-143">**-seq** est un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="05358-143">**-seq** is a sequential file.</span></span> <span data-ttu-id="05358-144">**\<Mo\>**: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="05358-144">**\<MB\>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="05358-145">**-rt**: définir le mode temps réel sur.</span><span class="sxs-lookup"><span data-stu-id="05358-145">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="05358-146">**Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).</span><span class="sxs-lookup"><span data-stu-id="05358-146">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="05358-147">Exemple :</span><span class="sxs-lookup"><span data-stu-id="05358-147">For example:</span></span>  
  
```  
BTATIBCOEMSTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCOEMSTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="05358-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05358-148">See Also</span></span>  
 [<span data-ttu-id="05358-149">Dépannage de TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="05358-149">Troubleshooting TIBCO Enterprise Message Service</span></span>](../core/troubleshooting-tibco-enterprise-message-service.md)