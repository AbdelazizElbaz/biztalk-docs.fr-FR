---
title: "À l’aide du suivi d’événements pour Windows4 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- BTAJDEEnterpriseOneTrace command
- Event Tracing for Windows
ms.assetid: 5f07d317-5ae2-4d1e-a343-941f3079dc4b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c7614ae4f6470427a77815338767b04f07aaa73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="bf7a5-102">À l’aide d’événements de suivi pour Windows</span><span class="sxs-lookup"><span data-stu-id="bf7a5-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="bf7a5-103">L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="bf7a5-104">Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d'événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="bf7a5-104">You can view additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="bf7a5-105">Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-105">When ETW is activated, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="bf7a5-106">Ce fichier au format binaire doit être converti pour être lu.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-106">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="bf7a5-107">Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.ex.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-107">To do this, you must have a consumer application available to interpret the \*.etl file; for example, tracerpt.exe or tracedmp.ex.</span></span> <span data-ttu-id="bf7a5-108">L’application tracept.exe convertit le \*.etl dans deux fichiers texte : summary.txt et dumpfile.csv.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-108">The tracept.exe application converts the \*.etl into two text files: summary.txt and dumpfile.csv.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="bf7a5-109">Composants ETW</span><span class="sxs-lookup"><span data-stu-id="bf7a5-109">ETW Components</span></span>  
 <span data-ttu-id="bf7a5-110">Le Suivi d'événements pour Windows comporte trois composants :</span><span class="sxs-lookup"><span data-stu-id="bf7a5-110">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="bf7a5-111">**Application de contrôleur**.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-111">**Controller application**.</span></span> <span data-ttu-id="bf7a5-112">active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).</span><span class="sxs-lookup"><span data-stu-id="bf7a5-112">Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="bf7a5-113">Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-113">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="bf7a5-114">Cela garantit que les appels BTAJDEEnterpriseOneTrace peuvent localiser tracelog.exe dans votre système.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-114">This ensures that BTAJDEEnterpriseOneTrace calls can locate tracelog.exe in your system.</span></span> <span data-ttu-id="bf7a5-115">Par défaut, BTAJDEEnterpriseOneTrace recherche le chemin d'accès actuel.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-115">By default, BTAJDEEnterpriseOneTrace searches the current path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf7a5-116">tracelog.exe est disponible dans le Kit de développement logiciel (SDK) Microsoft et est compatible avec les commandes fournies par l'adaptateur BizTalk pour JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-116">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by  BizTalk Adapter  for JD Edwards EnterpriseOne.</span></span> <span data-ttu-id="bf7a5-117">Pour utiliser logman.exe, consultez la documentation de logman.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-117">To use logman.exe, refer to the logman documentation.</span></span>  
  
-   <span data-ttu-id="bf7a5-118">**Application consommateur**.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-118">**Consumer application**.</span></span> <span data-ttu-id="bf7a5-119">lit les événements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-119">Reads logged events.</span></span> <span data-ttu-id="bf7a5-120">Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-120">For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="bf7a5-121">Normalement, cette opération est effectuée lorsque le contrôleur désactive le suivi.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-121">Normally this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="bf7a5-122">Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel,  **\<en temps réel > = -rt**.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-122">To use the consumer application without deactivating the trace, the controller must activate the trace with the real-time option, **\<Real time> = -rt**.</span></span>  
  
-   <span data-ttu-id="bf7a5-123">**Fournisseur**.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-123">**Provider**.</span></span> <span data-ttu-id="bf7a5-124">utilisé pour fournir l'événement.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-124">Used to provide the event.</span></span> <span data-ttu-id="bf7a5-125">L'adaptateur BizTalk pour JD Edwards EnterpriseOne inclut trois fournisseurs distincts,</span><span class="sxs-lookup"><span data-stu-id="bf7a5-125">BizTalk Adapter for JD Edwards EnterpriseOne includes three different providers.</span></span> <span data-ttu-id="bf7a5-126">Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="bf7a5-126">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="bf7a5-127">Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-127">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="bf7a5-128">L'adaptateur BizTalk pour JD Edwards EnterpriseOne inclut trois fournisseurs, ce qui permet de consigner plusieurs types de messages :</span><span class="sxs-lookup"><span data-stu-id="bf7a5-128">BizTalk Adapter  for JD Edwards EnterpriseOne contains three providers, allowing you to log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="bf7a5-129">**Fournisseur de journalisation de récepteur**: le \<Trace element > commutateur est **-récepteur**.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-129">**Receiver Logging Provider**: The \<Trace element> switch is **-receiver**.</span></span> <span data-ttu-id="bf7a5-130">Utilisez **-récepteur** pour récupérer tous les messages du journal qui ont été reçus par l’adaptateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-130">Use **-receiver** to get any messages from the log that were received by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="bf7a5-131">**Fournisseur de journalisation de l’émetteur**: le \<Trace element > commutateur est **-émetteur**.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-131">**Transmitter Logging Provider**: The \<Trace element> switch is **-transmitter**.</span></span> <span data-ttu-id="bf7a5-132">Utilisez **-émetteur** pour récupérer tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-132">Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="bf7a5-133">**Fournisseur de journalisation de gestion**: le \<Trace element > commutateur est **-gestion** utilisez **-gestion** pour récupérer tous les messages du journal qui ont été générés pendant la navigation du système du serveur.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-133">**Management Logging Provider**: The \<Trace element> switch is **-management** Use **-management** to get any messages from the log that were generated during browsing of the server system.</span></span>  
  
### <a name="btajdeenterpriseonetrace-command"></a><span data-ttu-id="bf7a5-134">Commande BTAJDEEnterpriseOneTrace</span><span class="sxs-lookup"><span data-stu-id="bf7a5-134">BTAJDEEnterpriseOneTrace Command</span></span>  
 <span data-ttu-id="bf7a5-135">Pour utiliser ETW, exécutez l’adaptateur BizTalk pour JD Edwards EnterpriseOne commande, **BTAJDEEnterpriseOneTrace.cmd**.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-135">To use ETW, run the BizTalk Adapter for JD Edwards EnterpriseOne command, **BTAJDEEnterpriseOneTrace.cmd**.</span></span> <span data-ttu-id="bf7a5-136">Utilisez-la comme suit :</span><span class="sxs-lookup"><span data-stu-id="bf7a5-136">You use this command as follows:</span></span>  
  
```  
BTAJDEEnterpriseOneTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTAJDEEnterpriseOneTrace <Trace element> -stop  
  
```  
  
 <span data-ttu-id="bf7a5-137">Où :  **\<Trace element >** (obligatoire) est le type de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-137">Where: **\<Trace element>** (required) is the kind of provider.</span></span>  
  
 <span data-ttu-id="bf7a5-138">Les options associées sont :</span><span class="sxs-lookup"><span data-stu-id="bf7a5-138">Its options are:</span></span>  
  
-   <span data-ttu-id="bf7a5-139">**-émetteur**</span><span class="sxs-lookup"><span data-stu-id="bf7a5-139">**-transmitter**</span></span>  
  
-   <span data-ttu-id="bf7a5-140">**-récepteur**</span><span class="sxs-lookup"><span data-stu-id="bf7a5-140">**-receiver**</span></span>  
  
-   <span data-ttu-id="bf7a5-141">**-gestion**</span><span class="sxs-lookup"><span data-stu-id="bf7a5-141">**-management**</span></span>  
  
-   <span data-ttu-id="bf7a5-142">**-start, - stop**: activer ou désactiver le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-142">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="bf7a5-143">**-cir \<Mo >**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-143">**-cir \<MB>**: Size and kind of file.</span></span> <span data-ttu-id="bf7a5-144">-cir signifie qu'il s'agit d'un fichier circulaire.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-144">-cir is a circular file.</span></span> <span data-ttu-id="bf7a5-145">\<Mo > : taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-145">\<MB>: Size in meg.</span></span>  
  
-   <span data-ttu-id="bf7a5-146">**-seq \<Mo >**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-146">**-seq \<MB>**: Size and kind of file.</span></span> <span data-ttu-id="bf7a5-147">-seq signifie qu'il s'agit d'un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-147">-seq is a sequential file.</span></span> <span data-ttu-id="bf7a5-148">\<Mo > : taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-148">\<MB>: Size in meg.</span></span>  
  
-   <span data-ttu-id="bf7a5-149">**-rt**: définir le mode temps réel sur.</span><span class="sxs-lookup"><span data-stu-id="bf7a5-149">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="bf7a5-150">**Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).</span><span class="sxs-lookup"><span data-stu-id="bf7a5-150">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="bf7a5-151">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bf7a5-151">For example:</span></span>  
  
```  
BTAJDEEnterpriseOneTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEEnterpriseOneTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf7a5-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf7a5-152">See Also</span></span>  
 [<span data-ttu-id="bf7a5-153">Résolution des problèmes de JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="bf7a5-153">Troubleshooting JD Edwards EnterpriseOne</span></span>](../core/troubleshooting-jd-edwards-enterpriseone.md)