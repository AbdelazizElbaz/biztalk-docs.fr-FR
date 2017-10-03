---
title: "À l’aide du suivi d’événements pour Windows2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- Event Tracing for Windows
ms.assetid: 88b91b74-2b2e-40e0-a3e9-1ebd6367abe8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95495448bb7b92f30911d4d33b3456fa5cef9bb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="0b328-102">À l’aide d’événements de suivi pour Windows</span><span class="sxs-lookup"><span data-stu-id="0b328-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="0b328-103">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld consigne les erreurs, avertissements et messages d'information dans l'Observateur d'événements Windows.</span><span class="sxs-lookup"><span data-stu-id="0b328-103">Microsoft BizTalk Adapter for JD Edwards OneWorld logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="0b328-104">Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d'événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="0b328-104">You can view additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="0b328-105">Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="0b328-105">When ETW is activated, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="0b328-106">Ce fichier au format binaire doit être converti pour être lu.</span><span class="sxs-lookup"><span data-stu-id="0b328-106">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="0b328-107">Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl : par exemple, tracerpt.exe ou tracedmp.exe.</span><span class="sxs-lookup"><span data-stu-id="0b328-107">To do this, you must have a consumer application available to interpret the \*.etl file: for example, tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="0b328-108">Composants ETW</span><span class="sxs-lookup"><span data-stu-id="0b328-108">ETW Components</span></span>  
 <span data-ttu-id="0b328-109">Le Suivi d'événements pour Windows comporte trois composants :</span><span class="sxs-lookup"><span data-stu-id="0b328-109">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="0b328-110">**Application de contrôleur.**</span><span class="sxs-lookup"><span data-stu-id="0b328-110">**Controller application.**</span></span> <span data-ttu-id="0b328-111">active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).</span><span class="sxs-lookup"><span data-stu-id="0b328-111">Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="0b328-112">Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="0b328-112">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="0b328-113">Cela permet de s'assurer que les appels BTAJDEdwardsOneWorldTrace sont en mesure de localiser tracelog.exe dans le système.</span><span class="sxs-lookup"><span data-stu-id="0b328-113">This ensures that BTAJDEdwardsOneWorldTrace calls can locate tracelog.exe in your system.</span></span> <span data-ttu-id="0b328-114">Par défaut, BTAJDEdwardsOneWorldTrace recherche le chemin d'accès actuel.</span><span class="sxs-lookup"><span data-stu-id="0b328-114">By default, BTAJDEdwardsOneWorldTrace searches the current path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b328-115">tracelog.exe est disponible dans le kit de développement Microsoft et il est compatible avec les commandes fournies par l'adaptateur BizTalk pour JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="0b328-115">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by BizTalk Adapter for JD Edwards OneWorld.</span></span> <span data-ttu-id="0b328-116">Pour utiliser logman.exe, consultez la documentation de logman.</span><span class="sxs-lookup"><span data-stu-id="0b328-116">To use logman.exe refer to the logman documentation.</span></span>  
  
-   <span data-ttu-id="0b328-117">**Application consommateur.**</span><span class="sxs-lookup"><span data-stu-id="0b328-117">**Consumer application.**</span></span> <span data-ttu-id="0b328-118">lit les événements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="0b328-118">Reads logged events.</span></span>  
  
     <span data-ttu-id="0b328-119">Pour que l'application consommateur puisse lire les événements du fichier .etl, le Suivi d'événements pour Windows doit les vider dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="0b328-119">For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="0b328-120">Normalement, cette opération est effectuée lorsque le contrôleur désactive le suivi.</span><span class="sxs-lookup"><span data-stu-id="0b328-120">Normally this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="0b328-121">Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel,  **\<en temps réel > = -rt**.</span><span class="sxs-lookup"><span data-stu-id="0b328-121">To use the consumer application without deactivating the trace, the controller must activate the trace with the real-time option, **\<Real time> = -rt**.</span></span>  
  
-   <span data-ttu-id="0b328-122">**Fournisseur.**</span><span class="sxs-lookup"><span data-stu-id="0b328-122">**Provider.**</span></span> <span data-ttu-id="0b328-123">fournit l'événement.</span><span class="sxs-lookup"><span data-stu-id="0b328-123">Provides the event.</span></span>  
  
 <span data-ttu-id="0b328-124">L'adaptateur BizTalk pour JD Edwards OneWorld inclut cinq fournisseurs différents.</span><span class="sxs-lookup"><span data-stu-id="0b328-124">BizTalk Adapter for JD Edwards OneWorld includes five different providers.</span></span> <span data-ttu-id="0b328-125">Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="0b328-125">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="0b328-126">Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="0b328-126">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="0b328-127">L'adaptateur BizTalk pour JD Edwards OneWorld dispose de cinq fournisseurs, vous permettant ainsi de consigner plusieurs sortes de messages :</span><span class="sxs-lookup"><span data-stu-id="0b328-127">BizTalk Adapter for JD Edwards OneWorld has five providers, allowing you to log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="0b328-128">**Fournisseur de journalisation du récepteur.**</span><span class="sxs-lookup"><span data-stu-id="0b328-128">**Receiver Logging Provider.**</span></span> <span data-ttu-id="0b328-129">Le \<Trace element > commutateur est **-récepteur**.</span><span class="sxs-lookup"><span data-stu-id="0b328-129">The \<Trace element> switch is **-receiver**.</span></span>  
  
-   <span data-ttu-id="0b328-130">**Fournisseur castdetails pour le récepteur.**</span><span class="sxs-lookup"><span data-stu-id="0b328-130">**Receiver CastDetails Provider.**</span></span> <span data-ttu-id="0b328-131">Le \<Trace element > commutateur est **- castDetailsReceive**.</span><span class="sxs-lookup"><span data-stu-id="0b328-131">The \<Trace element> switch is **-castDetailsReceive**.</span></span>  
  
-   <span data-ttu-id="0b328-132">**Fournisseur de journalisation d’émetteur.**</span><span class="sxs-lookup"><span data-stu-id="0b328-132">**Transmitter Logging Provider.**</span></span> <span data-ttu-id="0b328-133">Le \<Trace element > commutateur est **-émetteur**.</span><span class="sxs-lookup"><span data-stu-id="0b328-133">The \<Trace element> switch is **-transmitter**.</span></span>  
  
-   <span data-ttu-id="0b328-134">**Fournisseur castdetails pour l’émetteur.**</span><span class="sxs-lookup"><span data-stu-id="0b328-134">**Transmitter CastDetails Provider.**</span></span> <span data-ttu-id="0b328-135">Le \<Trace element > commutateur est **- castDetailsTransmit**.</span><span class="sxs-lookup"><span data-stu-id="0b328-135">The \<Trace element> switch is **-castDetailsTransmit**.</span></span>  
  
-   <span data-ttu-id="0b328-136">**Fournisseur de journalisation de gestion.**</span><span class="sxs-lookup"><span data-stu-id="0b328-136">**Management Logging Provider.**</span></span> <span data-ttu-id="0b328-137">Le \<Trace element > commutateur est **-gestion**.</span><span class="sxs-lookup"><span data-stu-id="0b328-137">The \<Trace element> switch is **-management**.</span></span>  
  
 <span data-ttu-id="0b328-138">Commande BTAJDEOneWorldTrace</span><span class="sxs-lookup"><span data-stu-id="0b328-138">BTAJDEOneWorldTrace Command</span></span>  
  
 <span data-ttu-id="0b328-139">Pour utiliser le Suivi d'événements pour Windows, exécutez la commande d'adaptateur BizTalk pour JD Edwards OneWorld, à savoir BTAJDEOneWorldTrace.cmd.</span><span class="sxs-lookup"><span data-stu-id="0b328-139">To use ETW, run the BizTalk Adapter for JD Edwards OneWorld command, BTAJDEOneWorldTrace.cmd.</span></span> <span data-ttu-id="0b328-140">Utilisez-la comme suit :</span><span class="sxs-lookup"><span data-stu-id="0b328-140">You use this command as follows:</span></span>  
  
```  
BTAJDEOneWorldTrace <Trace element> -start [-cir <MB>|   
      -seq <MB>] [-rt] logfile  
BTAJDEOneWorldTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="0b328-141">Où :</span><span class="sxs-lookup"><span data-stu-id="0b328-141">Where:</span></span>  
  
-   <span data-ttu-id="0b328-142">**\<Élément trace >** (obligatoire) est le type de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0b328-142">**\<Trace element>** (required) is the kind of provider.</span></span>  
  
-   <span data-ttu-id="0b328-143">Les options associées sont :</span><span class="sxs-lookup"><span data-stu-id="0b328-143">Its options are:</span></span>  
  
    -   <span data-ttu-id="0b328-144">**-castDetailsTransmit**</span><span class="sxs-lookup"><span data-stu-id="0b328-144">**-castDetailsTransmit**</span></span>  
  
    -   <span data-ttu-id="0b328-145">**-émetteur**</span><span class="sxs-lookup"><span data-stu-id="0b328-145">**-transmitter**</span></span>  
  
    -   <span data-ttu-id="0b328-146">**-castDetailsReceive**</span><span class="sxs-lookup"><span data-stu-id="0b328-146">**-castDetailsReceive**</span></span>  
  
    -   <span data-ttu-id="0b328-147">**-récepteur**</span><span class="sxs-lookup"><span data-stu-id="0b328-147">**-receiver**</span></span>  
  
    -   <span data-ttu-id="0b328-148">**-gestion**</span><span class="sxs-lookup"><span data-stu-id="0b328-148">**-management**</span></span>  
  
    -   <span data-ttu-id="0b328-149">**-start, - stop**: activer ou désactiver le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="0b328-149">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
    -   <span data-ttu-id="0b328-150">**-cir \<Mo >**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="0b328-150">**-cir \<MB>**: Size and kind of file.</span></span> <span data-ttu-id="0b328-151">-cir signifie qu'il s'agit d'un fichier circulaire.</span><span class="sxs-lookup"><span data-stu-id="0b328-151">-cir is a circular file.</span></span> <span data-ttu-id="0b328-152">\<Mo > : taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="0b328-152">\<MB>: Size in meg.</span></span>  
  
    -   <span data-ttu-id="0b328-153">**-seq \<Mo >**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="0b328-153">**-seq \<MB>**: Size and kind of file.</span></span> <span data-ttu-id="0b328-154">-seq signifie qu'il s'agit d'un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="0b328-154">-seq is a sequential file.</span></span> <span data-ttu-id="0b328-155">\<Mo > : taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="0b328-155">\<MB>: Size in meg.</span></span>  
  
    -   <span data-ttu-id="0b328-156">**-rt**: définir le mode temps réel sur.</span><span class="sxs-lookup"><span data-stu-id="0b328-156">**-rt**: Set the real time mode on.</span></span>  
  
    -   <span data-ttu-id="0b328-157">**Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).</span><span class="sxs-lookup"><span data-stu-id="0b328-157">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="0b328-158">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0b328-158">For example:</span></span>  
  
```  
BTAJDEOneWorldTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEOneWorldTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b328-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b328-159">See Also</span></span>  
 [<span data-ttu-id="0b328-160">Résolution des problèmes de JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="0b328-160">Troubleshooting JD Edwards OneWorld</span></span>](../core/troubleshooting-jd-edwards-oneworld.md)