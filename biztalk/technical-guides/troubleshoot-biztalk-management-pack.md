---
title: "Résolution des problèmes du Pack d’administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 676fd891-ee7f-49fc-a6d7-204dc6f2f382
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506e65565e841b4f601dc1cb8dcef64a0aeb7956
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting"></a><span data-ttu-id="d59d4-102">Dépannage</span><span class="sxs-lookup"><span data-stu-id="d59d4-102">Troubleshooting</span></span>
<span data-ttu-id="d59d4-103">Il existe un certain nombre d’actions que vous pouvez prendre pour résoudre les problèmes de pack d’administration BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="d59d4-103">There are a number of actions that you can take to troubleshoot BizTalk Server management pack issues:</span></span>  
  
-   <span data-ttu-id="d59d4-104">Assurez-vous qu’Operations Manager est correctement installé.</span><span class="sxs-lookup"><span data-stu-id="d59d4-104">Ensure that Operations Manager is installed properly.</span></span>  
  
-   <span data-ttu-id="d59d4-105">Assurez-vous que les paramètres de configuration Operations Manager sont définies correctement.</span><span class="sxs-lookup"><span data-stu-id="d59d4-105">Ensure that Operations Manager configuration settings are set properly.</span></span>  
  
-   <span data-ttu-id="d59d4-106">Vérifiez que l’importation du Pack d’administration est terminée et réussie.</span><span class="sxs-lookup"><span data-stu-id="d59d4-106">Verify that your import of the Management Pack is complete and successful.</span></span>  
  
-   <span data-ttu-id="d59d4-107">Assurez-vous que toutes les entités pertinentes sont activées, notamment les règles et analyses.</span><span class="sxs-lookup"><span data-stu-id="d59d4-107">Ensure that all relevant entities are enabled, such as rules and monitors.</span></span>  
  
-   <span data-ttu-id="d59d4-108">Assurez-vous que les groupes d’ordinateurs sont renseignées avec les ordinateurs appropriés.</span><span class="sxs-lookup"><span data-stu-id="d59d4-108">Ensure that the computer groups are populated with the correct computers.</span></span> <span data-ttu-id="d59d4-109">Vous pouvez utiliser la **création** mode **groupes** nœud dans la console pour effectuer cette vérification.</span><span class="sxs-lookup"><span data-stu-id="d59d4-109">You can use the **Authoring** mode **Groups** node in the console to perform this inspection.</span></span>  
  
-   <span data-ttu-id="d59d4-110">Assurez-vous que tous les agents SCOM sont intègres.</span><span class="sxs-lookup"><span data-stu-id="d59d4-110">Ensure that all the SCOM agents are healthy.</span></span>  
  
-   <span data-ttu-id="d59d4-111">Assurez-vous que l’intervalle de pulsation est correctement défini et que les règles sont propagées à l’ordinateur de l’agent Operations Manager 2007 R2/2012.</span><span class="sxs-lookup"><span data-stu-id="d59d4-111">Ensure that the heartbeat interval is set properly and that the rules are propagated to the Operations Manager 2007 R2/2012 agent computer.</span></span>  
  
-   <span data-ttu-id="d59d4-112">Assurez-vous que tous les compteurs de performance sont correctement installés.</span><span class="sxs-lookup"><span data-stu-id="d59d4-112">Ensure that all performance counters are properly installed.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="d59d4-113">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="d59d4-113">Known Issues</span></span>
<span data-ttu-id="d59d4-114">Le tableau suivant répertorie tous les problèmes connus avec la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack pour Operations Manager.</span><span class="sxs-lookup"><span data-stu-id="d59d4-114">The following table lists all the known issues with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack for Operations Manager.</span></span>  
  
|<span data-ttu-id="d59d4-115">Problème</span><span class="sxs-lookup"><span data-stu-id="d59d4-115">Issue</span></span>|<span data-ttu-id="d59d4-116"> Description</span><span class="sxs-lookup"><span data-stu-id="d59d4-116">Description</span></span>|<span data-ttu-id="d59d4-117">Résolution</span><span class="sxs-lookup"><span data-stu-id="d59d4-117">Resolution</span></span>|  
|-----------|-----------------|----------------|  
|<span data-ttu-id="d59d4-118">Compteurs de performances liés les erreurs et avertissements après le redémarrage</span><span class="sxs-lookup"><span data-stu-id="d59d4-118">Performance counter related errors and warnings after restart</span></span>|<span data-ttu-id="d59d4-119">Vous pouvez voir les erreurs associées dans des performances et des avertissements dans le journal des événements Operations Manager après l’agent de redémarrer.</span><span class="sxs-lookup"><span data-stu-id="d59d4-119">You might see performance counter-related errors and warnings in the Operations Manager event log after agent restart.</span></span>|<span data-ttu-id="d59d4-120">Le Pack d’administration permet de récupérer après les erreurs et reprend le travail.</span><span class="sxs-lookup"><span data-stu-id="d59d4-120">The Management Pack recovers after the errors and resumes working.</span></span>|  
|<span data-ttu-id="d59d4-121">Avertissements dans le journal des événements liés à la découverte d’objets</span><span class="sxs-lookup"><span data-stu-id="d59d4-121">Objects discovery related warnings in the Operations Manager event Log</span></span>|<span data-ttu-id="d59d4-122">Lorsqu’une opération de découverte (y compris la détection de relation) ne parvient pas à trouver une instance, un avertissement est écrit dans le journal des événements Operations Manager indiquant que la valeur null a été retournée par le script de découverte.</span><span class="sxs-lookup"><span data-stu-id="d59d4-122">When a discovery (including relationship discovery) fails to find an instance, a warning is written to the Operations Manager event log stating that null was returned by the discovery script.</span></span>||  
|<span data-ttu-id="d59d4-123">Génération d’alertes dans le nœud physique dans un environnement en cluster n’est pas fiable</span><span class="sxs-lookup"><span data-stu-id="d59d4-123">Alerting in physical node in clustered environment is unreliable</span></span>|<span data-ttu-id="d59d4-124">Il existe deux problèmes connus associés à la surveillance dans les environnements en cluster :</span><span class="sxs-lookup"><span data-stu-id="d59d4-124">There are two known issues associated with monitoring in clustered environments:</span></span><br /><br /> <span data-ttu-id="d59d4-125">-Lors de la modification d’un nœud actif au mode passif, l’état d’analyse du nœud et artefacts associés ne seront pas reportée correctement dans la Console opérateur.</span><span class="sxs-lookup"><span data-stu-id="d59d4-125">-   When a node changes from active to passive, the monitoring status of the node and associated artifacts may not be reflected correctly in the Operations Console.</span></span><br /><span data-ttu-id="d59d4-126">-Dans les environnements en cluster, Operations Manager crée un nœud virtuel qui peut afficher des alertes et l’état en double.</span><span class="sxs-lookup"><span data-stu-id="d59d4-126">-   In clustered environments, the Operations Manager creates a virtual node which may display duplicate status and alerts.</span></span>|<span data-ttu-id="d59d4-127">Dans les environnements en cluster qui contient les nœuds de type actif/passif. s’appuient sur les informations d’analyse s’affichées dans le nœud virtuel uniquement.</span><span class="sxs-lookup"><span data-stu-id="d59d4-127">In clustered environments that contains active/passive nodes; rely on the monitoring information displayed in the virtual node only.</span></span> <span data-ttu-id="d59d4-128">Il s’agit, car le nœud virtuel pointe toujours vers le nœud physique qui est actif à n’importe quel point dans le temps.</span><span class="sxs-lookup"><span data-stu-id="d59d4-128">This is because the virtual node always points to the physical node that is active at any point in time.</span></span>|  
|<span data-ttu-id="d59d4-129">Relations et des moniteurs de dépendance</span><span class="sxs-lookup"><span data-stu-id="d59d4-129">Relationships and Dependency monitors</span></span>|<span data-ttu-id="d59d4-130">Voici les problèmes connus liés aux relations et des moniteurs de dépendance : cela produit généralement lorsque le Pack d’administration de BizTalk est réimporté sur un serveur donné de SCOM.</span><span class="sxs-lookup"><span data-stu-id="d59d4-130">The following are the known issues related to relationships and dependency monitors: This occurs mostly when the BizTalk Management Pack is re-imported on a given SCOM Server.</span></span> <span data-ttu-id="d59d4-131">L’utilisateur est alors requise pour commenter l’état précédent, tel qu’indiqué dans la section « Étapes pour reproduire le problème ».</span><span class="sxs-lookup"><span data-stu-id="d59d4-131">The user is then required to see comment the previous state as given in the "Steps to Reproduce the Behavior" section.</span></span><br /><br /> <span data-ttu-id="d59d4-132">-Les relations entre les artefacts BizTalk ne sont pas détectées.</span><span class="sxs-lookup"><span data-stu-id="d59d4-132">-   Relationships between BizTalk artifacts are not discovered.</span></span><br /><span data-ttu-id="d59d4-133">-Relations de dépendance ne s’affichent pas comme prévu.</span><span class="sxs-lookup"><span data-stu-id="d59d4-133">-   Dependency relationships are not displayed as expected.</span></span><br /><span data-ttu-id="d59d4-134">-Cumul de surveillance de l’état n’a pas lieu.</span><span class="sxs-lookup"><span data-stu-id="d59d4-134">-   Roll up of monitoring status does not occur.</span></span><br /><span data-ttu-id="d59d4-135">-Certains moniteurs de dépendance ne sont pas initialisées même après la détection de relation.</span><span class="sxs-lookup"><span data-stu-id="d59d4-135">-   Some dependency monitors are uninitialized even after relationship discovery.</span></span>|<span data-ttu-id="d59d4-136">Les solutions de contournement pour résoudre ces problèmes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d59d4-136">The workarounds to address these issues are as follows:</span></span><br /><br /> <ul><li><span data-ttu-id="d59d4-137">Redémarrez le Service de contrôle d’intégrité Operations Manager sur l’ordinateur de l’agent de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d59d4-137">Restart the Operations Manager Health Service on the BizTalk agent machine.</span></span> <br />     <span data-ttu-id="d59d4-138">-OU-</span><span class="sxs-lookup"><span data-stu-id="d59d4-138">-OR-</span></span></li><li><span data-ttu-id="d59d4-139">Exécuter la tâche de vidage Health Service State et Cache.</span><span class="sxs-lookup"><span data-stu-id="d59d4-139">Run the Flush Health Service State and Cache task.</span></span> <span data-ttu-id="d59d4-140">Les étapes à suivre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d59d4-140">The steps to do this are as follows:</span></span><br /><br /> <ol><li><span data-ttu-id="d59d4-141">Dans l’arborescence de navigation, sélectionnez l’état d’intégrité d’Operations Manager Agent Agent.</span><span class="sxs-lookup"><span data-stu-id="d59d4-141">In the navigation tree, select Operations Manager Agent Agent Health State.</span></span></li><li><span data-ttu-id="d59d4-142">Sélectionnez l’ordinateur qui exécute BizTalk Server dans l’état de l’Agent à partir de l’Observateur du Service de contrôle d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="d59d4-142">Select the computer that is running BizTalk Server under Agent State from Health Service Watcher.</span></span></li><li><span data-ttu-id="d59d4-143">Sélectionnez l’état de l’agent sous l’état de l’Agent.</span><span class="sxs-lookup"><span data-stu-id="d59d4-143">Select the agent state under Agent State.</span></span></li><li><span data-ttu-id="d59d4-144">Cliquez sur la tâche de vidage Health Service State et Cache dans le volet de droite.</span><span class="sxs-lookup"><span data-stu-id="d59d4-144">Click the Flush Health Service State and Cache task in the right-side panel.</span></span></li><li><span data-ttu-id="d59d4-145">Dans la tâche d’exécution - état du Service de contrôle d’intégrité vidage et la boîte de dialogue de Cache, cliquez sur Exécuter.</span><span class="sxs-lookup"><span data-stu-id="d59d4-145">In the Run Task - Flush Health Service State and Cache dialog box, click Run.</span></span></li></ol></li></ul>|  
|<span data-ttu-id="d59d4-146">Présente les incorrect d’état des ports d’envoi et les emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="d59d4-146">Displays wrong status of send ports and receive locations</span></span>|<span data-ttu-id="d59d4-147">Lorsque le service SSO est arrêté, le Pack d’administration de BizTalk Server ne pas afficher l’état correct des ports d’envoi et emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="d59d4-147">When the SSO service is down, the BizTalk Server Management Pack does not show the correct status of send ports and receive locations.</span></span>||