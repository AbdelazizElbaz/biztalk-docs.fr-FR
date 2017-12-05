---
title: "Résoudre les problèmes de TIBCO Rendezvous | Documents Microsoft"
description: "Utiliser le suivi d’événements Windows pour troubl = esdhoot l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b7bc3ab-16fa-4e91-8730-9431473b2fb4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18ae8d599b67a1a572021cae0ebc9bfc64992a9b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-tibco-rendezvous"></a><span data-ttu-id="33517-103">Résoudre les problèmes de TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="33517-103">Troubleshoot TIBCO Rendezvous</span></span>
  
## <a name="use-event-tracing-for-windows"></a><span data-ttu-id="33517-104">Utiliser le suivi d’événements pour Windows</span><span class="sxs-lookup"><span data-stu-id="33517-104">Use Event Tracing for Windows</span></span>
<span data-ttu-id="33517-105">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows.</span><span class="sxs-lookup"><span data-stu-id="33517-105">Microsoft BizTalk Adapter for TIBCO Rendezvous logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="33517-106">Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="33517-106">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="33517-107">Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="33517-107">When ETW is activated, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="33517-108">Ce fichier au format binaire doit être converti pour être lu.</span><span class="sxs-lookup"><span data-stu-id="33517-108">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="33517-109">Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe.</span><span class="sxs-lookup"><span data-stu-id="33517-109">To do this, you must have a consumer application available to interpret the \*.etl file, for example, tracerpt.exe or tracedmp.exe.</span></span> <span data-ttu-id="33517-110">Par exemple, l’application tracerpt.exe convertira la \*fichier .etl dans deux fichiers texte : summary.txt et dumpfile.csv.</span><span class="sxs-lookup"><span data-stu-id="33517-110">For example, the tracerpt.exe application will convert the \*.etl file into two text files: summary.txt and dumpfile.csv.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="33517-111">Composants ETW</span><span class="sxs-lookup"><span data-stu-id="33517-111">ETW Components</span></span>  
 <span data-ttu-id="33517-112">Le Suivi d'événements pour Windows comporte trois composants :</span><span class="sxs-lookup"><span data-stu-id="33517-112">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="33517-113">**Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).</span><span class="sxs-lookup"><span data-stu-id="33517-113">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="33517-114">Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="33517-114">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="33517-115">Cela permet de s’assurer que les appels BTATIBCO RendezvousTrace peuvent localiser tracelog.exe dans le système.</span><span class="sxs-lookup"><span data-stu-id="33517-115">This makes sure that BTATIBCO RendezvousTrace calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="33517-116">Par défaut, BTATIBCO RendezvousTrace recherche le chemin d'accès actuel.</span><span class="sxs-lookup"><span data-stu-id="33517-116">By default, BTATIBCO RendezvousTrace searches the current path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33517-117">tracelog.exe est disponible dans le Kit de développement logiciel Microsoft (SDK) et est compatible avec les commandes fournies par l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="33517-117">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by Microsoft BizTalk Adapter for TIBCO Rendezvous.</span></span> <span data-ttu-id="33517-118">Pour utiliser logman.exe, consultez la documentation de logman.</span><span class="sxs-lookup"><span data-stu-id="33517-118">To use logman.exe, see the logman documentation.</span></span>  
  
-   <span data-ttu-id="33517-119">**Application consommateur**: lit les événements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="33517-119">**Consumer application**: Reads logged events.</span></span>  
  
     <span data-ttu-id="33517-120">Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="33517-120">For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="33517-121">Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.</span><span class="sxs-lookup"><span data-stu-id="33517-121">Typically this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="33517-122">Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel\> = -rt.</span><span class="sxs-lookup"><span data-stu-id="33517-122">To use the consumer application without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.</span></span>  
  
-   <span data-ttu-id="33517-123">**Fournisseur**: fournit l’événement.</span><span class="sxs-lookup"><span data-stu-id="33517-123">**Provider**: Provides the event.</span></span>  
  
     <span data-ttu-id="33517-124">L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs distincts,</span><span class="sxs-lookup"><span data-stu-id="33517-124">BizTalk Adapter for TIBCO Rendezvous includes three different providers.</span></span> <span data-ttu-id="33517-125">Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="33517-125">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="33517-126">Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="33517-126">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="33517-127">L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="33517-127">BizTalk Adapter for TIBCO Rendezvous has three providers.</span></span> <span data-ttu-id="33517-128">Vous pouvez ainsi consigner différents types de messages :</span><span class="sxs-lookup"><span data-stu-id="33517-128">This lets you log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="33517-129">**Fournisseur de journalisation de récepteur**: le \<élément Trace\> commutateur est **-récepteur**.</span><span class="sxs-lookup"><span data-stu-id="33517-129">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span>  
  
-   <span data-ttu-id="33517-130">Utilisez **-récepteur** pour récupérer tous les messages du journal qui ont été reçus par l’adaptateur lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="33517-130">Use **-receiver** to get any messages from the log that were received by the adapter at runtime.</span></span>  
  
-   <span data-ttu-id="33517-131">**Fournisseur de journalisation de l’émetteur**: le \<élément Trace\> commutateur est **-émetteur**.</span><span class="sxs-lookup"><span data-stu-id="33517-131">**Transmitter Logging Provider**: the \<Trace element\> switch is **-transmitter**.</span></span>  
  
     <span data-ttu-id="33517-132">Utilisez **-émetteur** pour récupérer tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="33517-132">Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="33517-133">**Fournisseur de journalisation de gestion —**le \<élément Trace\> commutateur est **-gestion**.</span><span class="sxs-lookup"><span data-stu-id="33517-133">**Management Logging Provider—**the \<Trace element\> switch is **-management**.</span></span>  
  
     <span data-ttu-id="33517-134">Utilisez **-gestion**pour récupérer tous les messages du journal qui ont été générés pendant la navigation du système du serveur.</span><span class="sxs-lookup"><span data-stu-id="33517-134">Use **-management**to get any messages from the log that were generated during browsing of the server system.</span></span>  
  
## <a name="btatibcorvtrace-command"></a><span data-ttu-id="33517-135">Commande BTATIBCORVTrace</span><span class="sxs-lookup"><span data-stu-id="33517-135">BTATIBCORVTrace Command</span></span>  
 <span data-ttu-id="33517-136">Pour utiliser ETW, exécutez l’adaptateur BizTalk pour commande TIBCO Rendezvous (btatibcbtatibcorvtrace.cmd).</span><span class="sxs-lookup"><span data-stu-id="33517-136">To use ETW, run the BizTalk Adapter for TIBCO Rendezvous command, BTATIBCORVTrace.cmd.</span></span> <span data-ttu-id="33517-137">Utilisez-la comme suit :</span><span class="sxs-lookup"><span data-stu-id="33517-137">You use this command as follows:</span></span>  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="33517-138">Où :  **\<élément Trace\>**  (obligatoire) est le type de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="33517-138">Where: **\<Trace element\>** (required) is the kind of provider.</span></span>  
  
 <span data-ttu-id="33517-139">Les options associées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="33517-139">Its options are as follows:</span></span>  
  
-   <span data-ttu-id="33517-140">**-émetteur**</span><span class="sxs-lookup"><span data-stu-id="33517-140">**-transmitter**</span></span>  
  
-   <span data-ttu-id="33517-141">**-récepteur**</span><span class="sxs-lookup"><span data-stu-id="33517-141">**-receiver**</span></span>  
  
-   <span data-ttu-id="33517-142">**-gestion**</span><span class="sxs-lookup"><span data-stu-id="33517-142">**-management**</span></span>  
  
-   <span data-ttu-id="33517-143">**-start, - stop**: activer ou désactiver le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="33517-143">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="33517-144">**-cir \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="33517-144">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="33517-145">**-cir** est un fichier circulaire.</span><span class="sxs-lookup"><span data-stu-id="33517-145">**-cir** is a circular file.</span></span> <span data-ttu-id="33517-146">**\<Mo\>**: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="33517-146">**\<MB\>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="33517-147">**-seq \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="33517-147">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="33517-148">**-seq** est un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="33517-148">**-seq** is a sequential file.</span></span> <span data-ttu-id="33517-149">**\<Mo\>**: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="33517-149">**\<MB\>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="33517-150">**-rt**: définir le mode temps réel sur.</span><span class="sxs-lookup"><span data-stu-id="33517-150">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="33517-151">**Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).</span><span class="sxs-lookup"><span data-stu-id="33517-151">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="33517-152">Exemple :</span><span class="sxs-lookup"><span data-stu-id="33517-152">For example:</span></span>  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
## <a name="see-more"></a><span data-ttu-id="33517-153">Voir plus d’informations</span><span class="sxs-lookup"><span data-stu-id="33517-153">See more</span></span>
[<span data-ttu-id="33517-154">Gérer les exceptions</span><span class="sxs-lookup"><span data-stu-id="33517-154">Handle exceptions</span></span>](../core/using-biztalk-server-exception-handling4.md)  
[<span data-ttu-id="33517-155">Sécurité</span><span class="sxs-lookup"><span data-stu-id="33517-155">Security</span></span>](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)  
[<span data-ttu-id="33517-156">Architecture</span><span class="sxs-lookup"><span data-stu-id="33517-156">Architecture</span></span>](../core/architecture-of-biztalk-adapter-for-tibco-rendezvous.md)