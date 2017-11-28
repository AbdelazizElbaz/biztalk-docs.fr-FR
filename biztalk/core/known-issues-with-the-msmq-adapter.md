---
title: "Problèmes connus avec l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce77cdac-79c1-4529-8f09-0fb1f87ca037
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f210d0e480a311aed0bed5d50f6a827bd6ea4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-msmq-adapter"></a><span data-ttu-id="17030-102">Problèmes connus avec l'adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="17030-102">Known Issues with the MSMQ Adapter</span></span>
<span data-ttu-id="17030-103">Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.</span><span class="sxs-lookup"><span data-stu-id="17030-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="17030-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="17030-104">Known Issues</span></span>  
  
#### <a name="msmq-adapter-receive-locations-do-not-process-documents"></a><span data-ttu-id="17030-105">Non-traitement des documents par les emplacements de réception de l'adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="17030-105">MSMQ Adapter receive locations do not process documents</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="17030-106">Problème</span><span class="sxs-lookup"><span data-stu-id="17030-106">Problem</span></span>  
 <span data-ttu-id="17030-107">Emplacements de réception de l’adaptateur MSMQ ne traitera pas les documents.</span><span class="sxs-lookup"><span data-stu-id="17030-107">MSMQ Adapter receive locations will not process documents.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="17030-108">Cause</span><span class="sxs-lookup"><span data-stu-id="17030-108">Cause</span></span>  
 <span data-ttu-id="17030-109">Si le nombre de threads disponibles est insuffisant dans la réserve de threads .NET associée à l'instance de l'hôte BizTalk sur laquelle est exécuté le gestionnaire de réception de l'adaptateur MSMQ, les emplacements de réception de ce dernier sont incapables de traiter les documents.</span><span class="sxs-lookup"><span data-stu-id="17030-109">If there are insufficient threads available in the .NET thread pool associated with the BizTalk host instance that the MSMQ adapter receive handler is running in then MSMQ Adapter receive locations are unable to process documents due to thread starvation.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="17030-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="17030-110">Resolution</span></span>  
 <span data-ttu-id="17030-111">Pour augmenter le nombre de threads disponibles dans le pool de threads .NET pour l’instance d’hôte, suivez les étapes de la **valeurs de thread CLR Hosting de l’hôte** section de la rubrique [que l’adaptateur affectent les paramètres de Configuration Performances](../core/configuration-parameters-that-affect-adapter-performance.md).</span><span class="sxs-lookup"><span data-stu-id="17030-111">To increase the number of available threads in the .NET thread pool for the host instance, follow the steps in the **CLR Hosting thread values for the host** section of the topic [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).</span></span>  
  
 <span data-ttu-id="17030-112">Étant donné que chaque MSMQ emplacement de réception qui est lié à un MSMQ réception gestionnaire requiert un thread de pool de threads .NET, définissez **MinIOThreads** et **MinWorkerThreads** à une valeur qui est supérieur ou égal à le nombre d’emplacements de réception MSMQ liés au Gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="17030-112">Because each MSMQ receive location that is bound to an MSMQ receive handler requires a thread from the .NET thread pool, set **MinIOThreads** and **MinWorkerThreads** to a value that is greater than or equal to the number of MSMQ receive locations bound to the receive handler.</span></span> <span data-ttu-id="17030-113">En conséquence, définissez la valeur de **MaxIOThreads** et **MaxWorkerThreads** et une valeur égale au nombre de MSMQ emplacements de réception liés au Gestionnaire de réception * 2 pour avoir une marge :</span><span class="sxs-lookup"><span data-stu-id="17030-113">Accordingly, set the value for **MaxIOThreads** and **MaxWorkerThreads** to a value equal to the number of MSMQ receive locations bound to the receive handler * 2 to allow for headroom:</span></span>  
  
|<span data-ttu-id="17030-114">Entrée DWORD</span><span class="sxs-lookup"><span data-stu-id="17030-114">DWORD Entry</span></span>|<span data-ttu-id="17030-115">Valeur recommandée</span><span class="sxs-lookup"><span data-stu-id="17030-115">Recommended value</span></span>|  
|-----------------|-----------------------|  
|<span data-ttu-id="17030-116">MaxIOThreads</span><span class="sxs-lookup"><span data-stu-id="17030-116">MaxIOThreads</span></span>|<span data-ttu-id="17030-117">Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ * 2.</span><span class="sxs-lookup"><span data-stu-id="17030-117">Number of MSMQ receive locations bound to the MSMQ adapter receive handler * 2.</span></span>|  
|<span data-ttu-id="17030-118">MaxWorkerThreads</span><span class="sxs-lookup"><span data-stu-id="17030-118">MaxWorkerThreads</span></span>|<span data-ttu-id="17030-119">Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ * 2.</span><span class="sxs-lookup"><span data-stu-id="17030-119">Number of MSMQ receive locations bound to the MSMQ adapter receive handler * 2.</span></span>|  
|<span data-ttu-id="17030-120">MinIOThreads</span><span class="sxs-lookup"><span data-stu-id="17030-120">MinIOThreads</span></span>|<span data-ttu-id="17030-121">Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="17030-121">Number of MSMQ receive locations bound to the MSMQ adapter receive handler.</span></span>|  
|<span data-ttu-id="17030-122">MinWorkerThreads</span><span class="sxs-lookup"><span data-stu-id="17030-122">MinWorkerThreads</span></span>|<span data-ttu-id="17030-123">Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="17030-123">Number of MSMQ receive locations bound to the MSMQ adapter receive handler.</span></span>|  
  
 <span data-ttu-id="17030-124">Ces valeurs recommandées ne se factorisent pas dans les threads utilisés par d'autres gestionnaires d'adaptateur ou orchestrations exécutées dans l'instance de l'hôte de sorte que les valeurs sont augmentées en conséquence.</span><span class="sxs-lookup"><span data-stu-id="17030-124">These recommended values do not factor in the threads used by other adapter handlers or orchestrations running in the host instance so the values should be increased accordingly.</span></span>  
  
#### <a name="msmq-adapter-receive-locations-shut-down-shortly-after-they-are-enabled"></a><span data-ttu-id="17030-125">Une fois activés, les emplacements de réception de l'adaptateur MSMQ ferment immédiatement</span><span class="sxs-lookup"><span data-stu-id="17030-125">MSMQ Adapter receive locations shut down shortly after they are enabled</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="17030-126">Problème</span><span class="sxs-lookup"><span data-stu-id="17030-126">Problem</span></span>  
 <span data-ttu-id="17030-127">Une fois activés, les emplacements de réception MSMQ ferment immédiatement</span><span class="sxs-lookup"><span data-stu-id="17030-127">MSMQ receive locations shut down shortly after they are enabled.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="17030-128">Cause</span><span class="sxs-lookup"><span data-stu-id="17030-128">Cause</span></span>  
 <span data-ttu-id="17030-129">Ce problème peut survenir si une instance locale du service Message Queuing qui ne fait pas partie d'un cluster n'est pas exécutée sur le même ordinateur que celui sur lequel l'instance d'hôte du gestionnaire de réception MSMQ est exécutée.</span><span class="sxs-lookup"><span data-stu-id="17030-129">This problem can occur if a local non-clustered instance of the Message Queuing service is not running on the same computer that the host instance for the MSMQ receive handler is running on.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="17030-130">Résolution</span><span class="sxs-lookup"><span data-stu-id="17030-130">Resolution</span></span>  
 <span data-ttu-id="17030-131">Démarrez le service Message Queuing sur l'ordinateur sur lequel l'instance d'hôte du gestionnaire de réception MSMQ est exécutée.</span><span class="sxs-lookup"><span data-stu-id="17030-131">Start the Message Queuing service on the computer that the host instance for the MSMQ receive handler is running on.</span></span> <span data-ttu-id="17030-132">Le gestionnaire de réception de l'adaptateur MSMQ requiert qu'une instance locale du service Message Queuing soit exécutée même si une instance mise en cluster de ce service est exécutée sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="17030-132">The MSMQ adapter receive handler requires that a local instance of the Message Queuing service is running even if a clustered instance of the Message Queuing service is running on the same computer.</span></span>  
  
#### <a name="sc-tool-causes-error-when-attempting-to-stop-service-for-host-instance"></a><span data-ttu-id="17030-133">L'outil SC provoque une erreur lors de la tentative d'arrêt du service pour l'instance de l'hôte</span><span class="sxs-lookup"><span data-stu-id="17030-133">SC tool causes error when attempting to stop service for host instance</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="17030-134">Problème</span><span class="sxs-lookup"><span data-stu-id="17030-134">Problem</span></span>  
 <span data-ttu-id="17030-135">Lorsque vous tentez d'utiliser l'outil SC (Sc.exe) pour fermer le service de l'instance d'hôte BizTalk, vous pouvez recevoir un message d'erreur semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="17030-135">When you try to use the SC tool (Sc.exe) to shut down the service for the BizTalk host instance, you may receive an error message that resembles the following:</span></span>  
  
 <span data-ttu-id="17030-136">**ControlService n’a pas pu 1053 :**</span><span class="sxs-lookup"><span data-stu-id="17030-136">**ControlService FAILED 1053:**</span></span>  
  
 <span data-ttu-id="17030-137">**Le service n’a pas répondu à la demande de démarrage ou de contrôle en temps voulu.**</span><span class="sxs-lookup"><span data-stu-id="17030-137">**The service did not respond to the start or control request in a timely fashion.**</span></span>  
  
 <span data-ttu-id="17030-138">Après avoir reçu ce message d'erreur, le service de l'instance d'hôte BizTalk est arrêté.</span><span class="sxs-lookup"><span data-stu-id="17030-138">After you receive this error message, the service for the BizTalk host instance is stopped.</span></span> <span data-ttu-id="17030-139">Cependant, au moins deux minutes peuvent être nécessaires à l'outil SC pour arrêter le service.</span><span class="sxs-lookup"><span data-stu-id="17030-139">However, the SC tool may need two minutes or more to shut down the service.</span></span>  
  
 <span data-ttu-id="17030-140">Ce problème se produit lorsqu'un emplacement de réception de Microsoft Message Queuing est activé dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17030-140">This problem occurs when a Microsoft Message Queuing receive location is enabled in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="17030-141">En outre, un message d'erreur semblable à ce qui suit peut être consigné dans le journal système :</span><span class="sxs-lookup"><span data-stu-id="17030-141">Additionally, an error message that resembles the following may be logged in the System log:</span></span>  
  
 <span data-ttu-id="17030-142">**Type d’événement : erreur**</span><span class="sxs-lookup"><span data-stu-id="17030-142">**Event Type: Error**</span></span>  
  
 <span data-ttu-id="17030-143">**Source d’événement : Gestionnaire de contrôle de Service**</span><span class="sxs-lookup"><span data-stu-id="17030-143">**Event Source: Service Control Manager**</span></span>  
  
 <span data-ttu-id="17030-144">**Catégorie d’événement : aucun**</span><span class="sxs-lookup"><span data-stu-id="17030-144">**Event Category: None**</span></span>  
  
 <span data-ttu-id="17030-145">**ID d’événement : 7011**</span><span class="sxs-lookup"><span data-stu-id="17030-145">**Event ID: 7011**</span></span>  
  
 <span data-ttu-id="17030-146">**Description :**</span><span class="sxs-lookup"><span data-stu-id="17030-146">**Description:**</span></span>  
  
 <span data-ttu-id="17030-147">**Délai d’attente (30 000 millisecondes) attend une réponse de transaction à partir du service BTSSvc$ BizTalkServerApplication.**</span><span class="sxs-lookup"><span data-stu-id="17030-147">**Timeout (30000 milliseconds) waiting for a transaction response from the BTSSvc$BizTalkServerApplication service.**</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="17030-148">Résolution</span><span class="sxs-lookup"><span data-stu-id="17030-148">Resolution</span></span>  
 <span data-ttu-id="17030-149">Un correctif pris en charge est disponible auprès de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="17030-149">A supported hotfix is now available from Microsoft.</span></span> <span data-ttu-id="17030-150">Il permet toutefois de corriger uniquement le problème décrit dans cet article.</span><span class="sxs-lookup"><span data-stu-id="17030-150">However, this hotfix is intended to correct only the problem that is described in this article.</span></span> <span data-ttu-id="17030-151">Appliquez ce correctif logiciel uniquement aux systèmes confrontés à ce problème spécifique.</span><span class="sxs-lookup"><span data-stu-id="17030-151">Apply this hotfix only to systems that are experiencing this specific problem.</span></span> <span data-ttu-id="17030-152">Il se peut que ce correctif soit de nouveau testé ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="17030-152">This hotfix might receive additional testing.</span></span> <span data-ttu-id="17030-153">Toutefois, si ce problème ne vous affecte pas trop, il est recommandé de patienter avant d'installer le prochain Service Pack qui inclura ce correctif.</span><span class="sxs-lookup"><span data-stu-id="17030-153">Therefore, if you are not severely affected by this problem, we recommend that you wait for the next service pack that contains this hotfix.</span></span>  
  
 <span data-ttu-id="17030-154">Pour obtenir le correctif et résoudre ce problème, envoyez une demande au service clientèle en ligne de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="17030-154">To resolve this problem, submit a request to Microsoft Online Customer Services to obtain the hotfix.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17030-155">Si d'autres problèmes surviennent ou si un dépannage est nécessaire, il est possible que vous deviez créer une demande de service distincte.</span><span class="sxs-lookup"><span data-stu-id="17030-155">If additional issues occur or any troubleshooting is required, you might have to create a separate service request.</span></span> <span data-ttu-id="17030-156">Les frais de dépannage habituels s'appliquent aux questions et problèmes de prise en charge supplémentaires qui ne correspondent pas à ce correctif.</span><span class="sxs-lookup"><span data-stu-id="17030-156">The usual support costs will apply to additional support questions and issues that do not qualify for this specific hotfix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17030-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17030-157">See Also</span></span>  
 [<span data-ttu-id="17030-158">Dépannage de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="17030-158">Troubleshooting the MSMQ Adapter</span></span>](../core/troubleshooting-the-msmq-adapter.md)