---
redirect_url: /biztalk/core/troubleshooting-tibco-rendezvous/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: cce9ad685bc4b0bc8a0d97e0645573c5e2db1cf5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="a1004-101">À l’aide d’événements de suivi pour Windows</span><span class="sxs-lookup"><span data-stu-id="a1004-101">Using Event Tracing for Windows</span></span>
<span data-ttu-id="a1004-102">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous consigne des messages d'erreur, d'avertissement et d'informations dans l'Observateur d'événements Windows.</span><span class="sxs-lookup"><span data-stu-id="a1004-102">Microsoft BizTalk Adapter for TIBCO Rendezvous logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="a1004-103">Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="a1004-103">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="a1004-104">Lorsqu'il est activé, cet outil crée un fichier *.etl pour recevoir les messages.</span><span class="sxs-lookup"><span data-stu-id="a1004-104">When ETW is activated, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="a1004-105">Ce fichier au format binaire doit être converti pour être lu.</span><span class="sxs-lookup"><span data-stu-id="a1004-105">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="a1004-106">Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, tracerpt.exe ou tracedmp.exe.</span><span class="sxs-lookup"><span data-stu-id="a1004-106">To do this, you must have a consumer application available to interpret the \*.etl file, for example, tracerpt.exe or tracedmp.exe.</span></span> <span data-ttu-id="a1004-107">Par exemple, l’application tracerpt.exe convertira la \*fichier .etl dans deux fichiers texte : summary.txt et dumpfile.csv.</span><span class="sxs-lookup"><span data-stu-id="a1004-107">For example, the tracerpt.exe application will convert the \*.etl file into two text files: summary.txt and dumpfile.csv.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="a1004-108">Composants ETW</span><span class="sxs-lookup"><span data-stu-id="a1004-108">ETW Components</span></span>  
 <span data-ttu-id="a1004-109">Le Suivi d'événements pour Windows comporte trois composants :</span><span class="sxs-lookup"><span data-stu-id="a1004-109">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="a1004-110">**Application de contrôleur**: active et désactive un fournisseur (par exemple, tracelog.exe ou logman.exe).</span><span class="sxs-lookup"><span data-stu-id="a1004-110">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="a1004-111">Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="a1004-111">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="a1004-112">Cela permet de s’assurer que les appels BTATIBCO RendezvousTrace peuvent localiser tracelog.exe dans le système.</span><span class="sxs-lookup"><span data-stu-id="a1004-112">This makes sure that BTATIBCO RendezvousTrace calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="a1004-113">Par défaut, BTATIBCO RendezvousTrace recherche le chemin d'accès actuel.</span><span class="sxs-lookup"><span data-stu-id="a1004-113">By default, BTATIBCO RendezvousTrace searches the current path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1004-114">tracelog.exe est disponible dans le Kit de développement logiciel Microsoft (SDK) et est compatible avec les commandes fournies par l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="a1004-114">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by Microsoft BizTalk Adapter for TIBCO Rendezvous.</span></span> <span data-ttu-id="a1004-115">Pour utiliser logman.exe, consultez la documentation de logman.</span><span class="sxs-lookup"><span data-stu-id="a1004-115">To use logman.exe, see the logman documentation.</span></span>  
  
-   <span data-ttu-id="a1004-116">**Application consommateur**: lit les événements enregistrés.</span><span class="sxs-lookup"><span data-stu-id="a1004-116">**Consumer application**: Reads logged events.</span></span>  
  
     <span data-ttu-id="a1004-117">Pour que l'application consommateur puisse lire les événements dans le fichier .etl, l'outil Suivi d'événements pour Windows doit les vider dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="a1004-117">For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="a1004-118">Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.</span><span class="sxs-lookup"><span data-stu-id="a1004-118">Typically this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="a1004-119">Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, \<en temps réel\> = -rt.</span><span class="sxs-lookup"><span data-stu-id="a1004-119">To use the consumer application without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.</span></span>  
  
-   <span data-ttu-id="a1004-120">**Fournisseur**: fournit l’événement.</span><span class="sxs-lookup"><span data-stu-id="a1004-120">**Provider**: Provides the event.</span></span>  
  
     <span data-ttu-id="a1004-121">L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs distincts,</span><span class="sxs-lookup"><span data-stu-id="a1004-121">BizTalk Adapter for TIBCO Rendezvous includes three different providers.</span></span> <span data-ttu-id="a1004-122">Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="a1004-122">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="a1004-123">Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.</span><span class="sxs-lookup"><span data-stu-id="a1004-123">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="a1004-124">L'adaptateur BizTalk pour TIBCO Rendezvous inclut trois fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="a1004-124">BizTalk Adapter for TIBCO Rendezvous has three providers.</span></span> <span data-ttu-id="a1004-125">Vous pouvez ainsi consigner différents types de messages :</span><span class="sxs-lookup"><span data-stu-id="a1004-125">This lets you log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="a1004-126">**Fournisseur de journalisation de récepteur**: le \<élément Trace\> commutateur est **-récepteur**.</span><span class="sxs-lookup"><span data-stu-id="a1004-126">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span>  
  
-   <span data-ttu-id="a1004-127">Utilisez **-récepteur** pour récupérer tous les messages du journal qui ont été reçus par l’adaptateur lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a1004-127">Use **-receiver** to get any messages from the log that were received by the adapter at runtime.</span></span>  
  
-   <span data-ttu-id="a1004-128">**Fournisseur de journalisation de l’émetteur**: le \<élément Trace\> commutateur est **-émetteur**.</span><span class="sxs-lookup"><span data-stu-id="a1004-128">**Transmitter Logging Provider**: the \<Trace element\> switch is **-transmitter**.</span></span>  
  
     <span data-ttu-id="a1004-129">Utilisez **-émetteur** pour récupérer tous les messages du journal qui ont été transmis par l’adaptateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a1004-129">Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="a1004-130">**Fournisseur de journalisation de gestion —**le \<élément Trace\> commutateur est **-gestion**.</span><span class="sxs-lookup"><span data-stu-id="a1004-130">**Management Logging Provider—**the \<Trace element\> switch is **-management**.</span></span>  
  
     <span data-ttu-id="a1004-131">Utilisez **-gestion**pour récupérer tous les messages du journal qui ont été générés pendant la navigation du système du serveur.</span><span class="sxs-lookup"><span data-stu-id="a1004-131">Use **-management**to get any messages from the log that were generated during browsing of the server system.</span></span>  
  
## <a name="btatibcorvtrace-command"></a><span data-ttu-id="a1004-132">Commande BTATIBCORVTrace</span><span class="sxs-lookup"><span data-stu-id="a1004-132">BTATIBCORVTrace Command</span></span>  
 <span data-ttu-id="a1004-133">Pour utiliser ETW, exécutez l’adaptateur BizTalk pour commande TIBCO Rendezvous (btatibcbtatibcorvtrace.cmd).</span><span class="sxs-lookup"><span data-stu-id="a1004-133">To use ETW, run the BizTalk Adapter for TIBCO Rendezvous command, BTATIBCORVTrace.cmd.</span></span> <span data-ttu-id="a1004-134">Utilisez-la comme suit :</span><span class="sxs-lookup"><span data-stu-id="a1004-134">You use this command as follows:</span></span>  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="a1004-135">Où :  **\<élément Trace\>**  (obligatoire) est le type de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a1004-135">Where: **\<Trace element\>** (required) is the kind of provider.</span></span>  
  
 <span data-ttu-id="a1004-136">Les options associées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a1004-136">Its options are as follows:</span></span>  
  
-   <span data-ttu-id="a1004-137">**-émetteur**</span><span class="sxs-lookup"><span data-stu-id="a1004-137">**-transmitter**</span></span>  
  
-   <span data-ttu-id="a1004-138">**-récepteur**</span><span class="sxs-lookup"><span data-stu-id="a1004-138">**-receiver**</span></span>  
  
-   <span data-ttu-id="a1004-139">**-gestion**</span><span class="sxs-lookup"><span data-stu-id="a1004-139">**-management**</span></span>  
  
-   <span data-ttu-id="a1004-140">**-start, - stop**: activer ou désactiver le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a1004-140">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="a1004-141">**-cir \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="a1004-141">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="a1004-142">**-cir** est un fichier circulaire.</span><span class="sxs-lookup"><span data-stu-id="a1004-142">**-cir** is a circular file.</span></span> <span data-ttu-id="a1004-143">**\<Mo\>**: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="a1004-143">**\<MB\>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="a1004-144">**-seq \<Mo\>**: taille et type de fichier.</span><span class="sxs-lookup"><span data-stu-id="a1004-144">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="a1004-145">**-seq** est un fichier séquentiel.</span><span class="sxs-lookup"><span data-stu-id="a1004-145">**-seq** is a sequential file.</span></span> <span data-ttu-id="a1004-146">**\<Mo\>**: taille en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="a1004-146">**\<MB\>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="a1004-147">**-rt**: définir le mode temps réel sur.</span><span class="sxs-lookup"><span data-stu-id="a1004-147">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="a1004-148">**Fichier journal**: nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).</span><span class="sxs-lookup"><span data-stu-id="a1004-148">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="a1004-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="a1004-149">For example:</span></span>  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1004-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1004-150">See Also</span></span>  
 [<span data-ttu-id="a1004-151">Dépannage de TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="a1004-151">Troubleshooting TIBCO Rendezvous</span></span>](../core/troubleshooting-tibco-rendezvous.md)