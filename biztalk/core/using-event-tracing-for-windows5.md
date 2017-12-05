---
title: "À l’aide du suivi d’événements pour Windows5 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- events, Event Tracing for Windows
- controller application
- ETW components
- consumer application
- Provider
- Event Tracing for Windows
- Event Tracing for Windows, components
- BTAPeopleSoftTrace command
ms.assetid: 330ef84b-5e2a-4b79-85a9-72271eb489d2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60a317dabd31bc1a6f37645c6b3fb2ce25d6de43
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="036de-102">À l’aide d’événements de suivi pour Windows</span><span class="sxs-lookup"><span data-stu-id="036de-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="036de-103">L'adaptateur BizTalk pour PeopleSoft Enterprise consigne les erreurs, avertissements et messages d'information dans l'Observateur d'événements Windows.</span><span class="sxs-lookup"><span data-stu-id="036de-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="036de-104">Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="036de-104">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="036de-105">Lorsqu'ETW est activé, l'outil crée un fichier *.etl pour recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="036de-105">When ETW is enabled, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="036de-106">Le fichier est au format binaire et doit être converti pour être lu.</span><span class="sxs-lookup"><span data-stu-id="036de-106">The file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="036de-107">Pour cela, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe.</span><span class="sxs-lookup"><span data-stu-id="036de-107">To do this you must have a consumer application available to interpret the \*.etl file; for example, tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="036de-108">Composants ETW</span><span class="sxs-lookup"><span data-stu-id="036de-108">ETW Components</span></span>  
 <span data-ttu-id="036de-109">Le Suivi d'événements pour Windows comporte trois composants :</span><span class="sxs-lookup"><span data-stu-id="036de-109">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="036de-110">**Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).</span><span class="sxs-lookup"><span data-stu-id="036de-110">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="036de-111">Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="036de-111">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="036de-112">Cela permet de s'assurer que les appels `BTAPeopleSoftTrace` sont en mesure de localiser tracelog.exe dans le système.</span><span class="sxs-lookup"><span data-stu-id="036de-112">This makes sure that `BTAPeopleSoftTrace` calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="036de-113">Par défaut, BTAPeopleSoftTrace recherche le chemin d'accès actuel.</span><span class="sxs-lookup"><span data-stu-id="036de-113">By default, BTAPeopleSoftTrace searches the current path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="036de-114">tracelog.exe est disponible dans le Kit de développement Microsoft (SDK) et il est compatible avec les commandes fournies par l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="036de-114">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="036de-115">Pour utiliser logman.exe, consultez la documentation de logman.</span><span class="sxs-lookup"><span data-stu-id="036de-115">To use logman.exe, see the logman documentation.</span></span>  
  
-   <span data-ttu-id="036de-116">**Application consommateur**: lit les événements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="036de-116">**Consumer application**: Reads logged events.</span></span>  
  
     <span data-ttu-id="036de-117">Pour que l'application consommateur puisse lire les événements du fichier .etl, le Suivi d'événements pour Windows doit les vider dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="036de-117">For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="036de-118">Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.</span><span class="sxs-lookup"><span data-stu-id="036de-118">Typically this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="036de-119">Pour utiliser le consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel\> = -rt.</span><span class="sxs-lookup"><span data-stu-id="036de-119">To use the consumer without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.</span></span>  
  
-   <span data-ttu-id="036de-120">**Fournisseur :** fournit l’événement.</span><span class="sxs-lookup"><span data-stu-id="036de-120">**Provider:** Provides the event.</span></span>  
  
     <span data-ttu-id="036de-121">L'adaptateur BizTalk pour PeopleSoft Enterprise dispose de cinq fournisseurs différents.</span><span class="sxs-lookup"><span data-stu-id="036de-121">BizTalk Adapter for PeopleSoft Enterprise has five different providers.</span></span> <span data-ttu-id="036de-122">Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="036de-122">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="036de-123">Pour rechercher les fournisseurs enregistrés dans le **root\WMI\EventTrace** chemin d’accès, vous pouvez utiliser des outils tels que WMI CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="036de-123">To find the registered providers in the **root\WMI\EventTrace** path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="036de-124">L'adaptateur BizTalk pour PeopleSoft Enterprise dispose de cinq fournisseurs, vous permettant ainsi de consigner plusieurs sortes de messages :</span><span class="sxs-lookup"><span data-stu-id="036de-124">BizTalk Adapter for PeopleSoft Enterprise has five providers, allowing you to log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="036de-125">**Fournisseur de journalisation de récepteur**: le \<élément Trace\> commutateur est **-récepteur**.</span><span class="sxs-lookup"><span data-stu-id="036de-125">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span>  
  
-   <span data-ttu-id="036de-126">**Fournisseur castdetails pour le récepteur**: le \<élément Trace\> commutateur est **- castDetailsReceive**.</span><span class="sxs-lookup"><span data-stu-id="036de-126">**Receiver CastDetails Provider**: The \<Trace element\> switch is **-castDetailsReceive**.</span></span>  
  
-   <span data-ttu-id="036de-127">**Fournisseur de journalisation de l’émetteur**: le \<élément Trace\> commutateur est **-émetteur**.</span><span class="sxs-lookup"><span data-stu-id="036de-127">**Transmitter Logging Provider**: The \<Trace element\> switch is **-transmitter**.</span></span>  
  
-   <span data-ttu-id="036de-128">**Fournisseur castdetails pour l’émetteur**: le \<élément Trace\> commutateur est **- castDetailsTransmit**.</span><span class="sxs-lookup"><span data-stu-id="036de-128">**Transmitter CastDetails Provider**: The \<Trace element\> switch is **-castDetailsTransmit**.</span></span>  
  
-   <span data-ttu-id="036de-129">**Fournisseur de journalisation de gestion**: le \<élément Trace\> commutateur est **-gestion**.</span><span class="sxs-lookup"><span data-stu-id="036de-129">**Management Logging Provider**: The \<Trace element\> switch is **-management**.</span></span>  
  
## <a name="btapeoplesofttrace-command"></a><span data-ttu-id="036de-130">Commande BTAPeopleSoftTrace</span><span class="sxs-lookup"><span data-stu-id="036de-130">BTAPeopleSoftTrace Command</span></span>  
 <span data-ttu-id="036de-131">Pour utiliser ETW, exécutez la commande de la carte, **BTAPeopleSoftTrace.cmd**.</span><span class="sxs-lookup"><span data-stu-id="036de-131">To use ETW, run the adapter command, **BTAPeopleSoftTrace.cmd**.</span></span> <span data-ttu-id="036de-132">Utilisez-la comme suit :</span><span class="sxs-lookup"><span data-stu-id="036de-132">You use this command as follows:</span></span>  
  
```  
BTAPeopleSoftTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTAPeopleSoftTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="036de-133">Où :</span><span class="sxs-lookup"><span data-stu-id="036de-133">Where:</span></span>  
  
-   <span data-ttu-id="036de-134">\<Élément trace\> (obligatoire) est le type de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="036de-134">\<Trace element\> (required) is the kind of provider.</span></span>  
  
     <span data-ttu-id="036de-135">Les options disponibles sont :</span><span class="sxs-lookup"><span data-stu-id="036de-135">Options are as follows:</span></span>  
  
    -   <span data-ttu-id="036de-136">**-castDetailsTransmit**</span><span class="sxs-lookup"><span data-stu-id="036de-136">**-castDetailsTransmit**</span></span>  
  
    -   <span data-ttu-id="036de-137">**-émetteur**</span><span class="sxs-lookup"><span data-stu-id="036de-137">**-transmitter**</span></span>  
  
    -   <span data-ttu-id="036de-138">**-castDetailsReceive**</span><span class="sxs-lookup"><span data-stu-id="036de-138">**-castDetailsReceive**</span></span>  
  
    -   <span data-ttu-id="036de-139">**-récepteur**</span><span class="sxs-lookup"><span data-stu-id="036de-139">**-receiver**</span></span>  
  
    -   <span data-ttu-id="036de-140">**-gestion**</span><span class="sxs-lookup"><span data-stu-id="036de-140">**-management**</span></span>  
  
    -   <span data-ttu-id="036de-141">**-start, - stop**: activer ou désactiver le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="036de-141">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="036de-142">**-cir \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="036de-142">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="036de-143">-cir signifie qu'il s'agit d'un fichier circulaire.</span><span class="sxs-lookup"><span data-stu-id="036de-143">-cir is a circular file.</span></span> <span data-ttu-id="036de-144">\<Mo\>: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="036de-144">\<MB\>: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="036de-145">**-seq \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="036de-145">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="036de-146">-seq signifie qu'il s'agit d'un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="036de-146">-seq is a sequential file.</span></span> <span data-ttu-id="036de-147">\<Mo\>: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="036de-147">\<MB\>: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="036de-148">**-rt**: définir le mode temps réel sur.</span><span class="sxs-lookup"><span data-stu-id="036de-148">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="036de-149">**Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de C:\rtlog.etl).</span><span class="sxs-lookup"><span data-stu-id="036de-149">**Logfile**: Name of the log file (C:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="036de-150">Exemple :</span><span class="sxs-lookup"><span data-stu-id="036de-150">For example:</span></span>  
  
```  
BTAPeopleSoftTrace -transmitter -start -cir 10 -rt C:\log\mylog.etl  
BTAPeopleSoftTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="036de-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="036de-151">See Also</span></span>  
 [<span data-ttu-id="036de-152">Résolution des problèmes de PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="036de-152">Troubleshooting PeopleSoft</span></span>](../core/troubleshooting-peoplesoft.md)