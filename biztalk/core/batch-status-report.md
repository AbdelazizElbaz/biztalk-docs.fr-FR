---
title: "Rapport d’état du lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dad016-e7bb-45cd-b36a-a9c83d073501
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c033f58432c8ae5a2d87b87b56223b8f64a7201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-status-report"></a><span data-ttu-id="73a15-102">Rapport État du lot</span><span class="sxs-lookup"><span data-stu-id="73a15-102">Batch Status Report</span></span>
<span data-ttu-id="73a15-103">Ce rapport affiche l'activité des instances de l'orchestration de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="73a15-103">This report shows the activity of instances of the batching orchestration.</span></span> <span data-ttu-id="73a15-104">Chaque ligne du rapport indique l'état des lots en cours de traitement par une instance de l'orchestration de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="73a15-104">Each row in the report indicates the status of the batches being processed by a single instance of the batching orchestration.</span></span>  
  
 <span data-ttu-id="73a15-105">L'état des lots conservés n'est pas signalé dans le rapport État du lot, mais dans le rapport État de l'échange/de l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="73a15-105">The status of preserved batches is not reported in the Batch Status Report, but is reported in the Interchange/ACK Status report.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="73a15-106">Champs du rapport État</span><span class="sxs-lookup"><span data-stu-id="73a15-106">Fields in the Status Report</span></span>  
 <span data-ttu-id="73a15-107">Le rapport État du lot affiche les informations suivantes pour les échanges reçus par lot :</span><span class="sxs-lookup"><span data-stu-id="73a15-107">The Batch Status Report displays the following information for batched interchanges:</span></span>  
  
-   <span data-ttu-id="73a15-108">état du lot ;</span><span class="sxs-lookup"><span data-stu-id="73a15-108">Batch Status</span></span>  
  
-   <span data-ttu-id="73a15-109">Nom du lot</span><span class="sxs-lookup"><span data-stu-id="73a15-109">Batch Name</span></span>  
  
-   <span data-ttu-id="73a15-110">nom du tiers de destination ;</span><span class="sxs-lookup"><span data-stu-id="73a15-110">Destination Party Name</span></span>  
  
-   <span data-ttu-id="73a15-111">heure de l'activation ;</span><span class="sxs-lookup"><span data-stu-id="73a15-111">Activation Time</span></span>  
  
-   <span data-ttu-id="73a15-112">nombre d'occurrences dans le lot ;</span><span class="sxs-lookup"><span data-stu-id="73a15-112">Batch Occurrence</span></span>  
  
-   <span data-ttu-id="73a15-113">type de codage EDI ;</span><span class="sxs-lookup"><span data-stu-id="73a15-113">EDI Encoding Type</span></span>  
  
-   <span data-ttu-id="73a15-114">type de lot ;</span><span class="sxs-lookup"><span data-stu-id="73a15-114">Batch Type</span></span>  
  
-   <span data-ttu-id="73a15-115">cible du lot ;</span><span class="sxs-lookup"><span data-stu-id="73a15-115">Batch Target</span></span>  
  
-   <span data-ttu-id="73a15-116">Nombre d’éléments de lot : le nombre d’éléments par lots ont été accumulé par l’instance d’orchestration de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="73a15-116">Batch Element Count: how many batch elements have been accumulated by the batching orchestration instance</span></span>  
  
-   <span data-ttu-id="73a15-117">nombre d'éléments rejetés ;</span><span class="sxs-lookup"><span data-stu-id="73a15-117">Rejected Elements Count</span></span>  
  
-   <span data-ttu-id="73a15-118">Action la plus récente : Peut être lot activé, déclenchement planifié, déclenchement basé sur le nombre, déclenchement du remplacement manuel, lot terminé/arrêter version, élément ajouté ou déclenchement externe</span><span class="sxs-lookup"><span data-stu-id="73a15-118">Latest Action: Can be Batch Activated, Scheduled Release, Count Based Release, Manual Override Release, Batch Terminated/Stop Release, Element Added, or External Release</span></span>  
  
-   <span data-ttu-id="73a15-119">Numéro de contrôle d’échange</span><span class="sxs-lookup"><span data-stu-id="73a15-119">Interchange Control Number</span></span>  
  
-   <span data-ttu-id="73a15-120">date/heure de l'échange ;</span><span class="sxs-lookup"><span data-stu-id="73a15-120">Interchange Date Time</span></span>  
  
-   <span data-ttu-id="73a15-121">taille du lot (en nombre de caractères) (n'est pas affichée par défaut).</span><span class="sxs-lookup"><span data-stu-id="73a15-121">Batch Size (in characters) (not displayed by default)</span></span>  
  
## <a name="view-related-interchanges-status-reports"></a><span data-ttu-id="73a15-122">Affichage des rapports État de l'échange associés</span><span class="sxs-lookup"><span data-stu-id="73a15-122">View Related Interchanges Status Reports</span></span>  
 <span data-ttu-id="73a15-123">Si vous cliquez avec le bouton droit sur un échange ou un accusé de réception répertorié dans le rapport État du lot, vous pouvez afficher les détails des échanges associés au lot.</span><span class="sxs-lookup"><span data-stu-id="73a15-123">If you right-click an interchange or acknowledgment listed in the Batch Status Report, you can display details about the interchanges related to the batch.</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="73a15-124">Champs de l'expression de requête du rapport d'état</span><span class="sxs-lookup"><span data-stu-id="73a15-124">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="73a15-125">Vous pouvez personnaliser le rapport État du lot en modifiant les champs de l'expression de requête qui détermine les données affichées.</span><span class="sxs-lookup"><span data-stu-id="73a15-125">You can customize the Batch Status Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="73a15-126">Les champs suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="73a15-126">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="73a15-127">Champ de l'expression de requête</span><span class="sxs-lookup"><span data-stu-id="73a15-127">Query Expression Field</span></span>|<span data-ttu-id="73a15-128">Opérateurs potentiels</span><span class="sxs-lookup"><span data-stu-id="73a15-128">Potential Operators</span></span>|<span data-ttu-id="73a15-129">Valeurs potentielles</span><span class="sxs-lookup"><span data-stu-id="73a15-129">Potential Values</span></span>|<span data-ttu-id="73a15-130">Inclus par défaut ?</span><span class="sxs-lookup"><span data-stu-id="73a15-130">Included By Default?</span></span>|  
|<span data-ttu-id="73a15-131">Rechercher</span><span class="sxs-lookup"><span data-stu-id="73a15-131">Search for</span></span>|<span data-ttu-id="73a15-132">Égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-132">Equals</span></span>|<span data-ttu-id="73a15-133">état du lot ;</span><span class="sxs-lookup"><span data-stu-id="73a15-133">Batch Status</span></span>|<span data-ttu-id="73a15-134">Oui (requis)</span><span class="sxs-lookup"><span data-stu-id="73a15-134">Yes (required)</span></span>|  
|<span data-ttu-id="73a15-135">état du lot ;</span><span class="sxs-lookup"><span data-stu-id="73a15-135">Batch Status</span></span>|<span data-ttu-id="73a15-136">Égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-136">Equals</span></span><br /><br /> <span data-ttu-id="73a15-137">Différent de</span><span class="sxs-lookup"><span data-stu-id="73a15-137">Not Equals</span></span>|<span data-ttu-id="73a15-138">Défini par : L’instance de lot est configurée mais heure de début est postérieur à l’heure de la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="73a15-138">Defined: The batch instance is configured but the start date time is later than the current date time.</span></span><br /><br /> <span data-ttu-id="73a15-139">Actif (par défaut) : l’instance du lot est configurée et collecte des jeux de transactions pour un lot.</span><span class="sxs-lookup"><span data-stu-id="73a15-139">Active (default): The batch instance is configured and is collecting transaction sets for a batch.</span></span> <span data-ttu-id="73a15-140">L'heure de début est antérieure à l'heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="73a15-140">The start date time is earlier than the current date time.</span></span><br /><br /> <span data-ttu-id="73a15-141">Publié : Les critères de déclenchement ont été satisfaits et le lot a été envoyé, ou que l’orchestration de traitement par lots a été arrêtée avant que les messages soient traités.</span><span class="sxs-lookup"><span data-stu-id="73a15-141">Released: The release criteria has been met, and the batch has been sent, or that the batch orchestration was stopped before any messages were processed.</span></span><br /><br /> <span data-ttu-id="73a15-142">Terminé : Les critères de déclenchement a été remplie, mais le lot n’a pas été envoyé.</span><span class="sxs-lookup"><span data-stu-id="73a15-142">Completed: The release criteria has been met, but the batch has not been sent.</span></span><br /><br /> <span data-ttu-id="73a15-143">All : Afficher n’importe quelle instance de lot dans un de ces États.</span><span class="sxs-lookup"><span data-stu-id="73a15-143">All: Display any batch instance that is in one of the above states.</span></span>|<span data-ttu-id="73a15-144">Oui</span><span class="sxs-lookup"><span data-stu-id="73a15-144">Yes</span></span>|  
|<span data-ttu-id="73a15-145">Résultats (nb maximal)</span><span class="sxs-lookup"><span data-stu-id="73a15-145">Maximum Matches</span></span>|<span data-ttu-id="73a15-146">Égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-146">Equals</span></span>|<span data-ttu-id="73a15-147">Entier (valeur par défaut 50)</span><span class="sxs-lookup"><span data-stu-id="73a15-147">Integer (default of 50)</span></span>|<span data-ttu-id="73a15-148">Oui</span><span class="sxs-lookup"><span data-stu-id="73a15-148">Yes</span></span>|  
|<span data-ttu-id="73a15-149">Date et heure d'activation</span><span class="sxs-lookup"><span data-stu-id="73a15-149">Activation Date Time</span></span>|<span data-ttu-id="73a15-150">Inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-150">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="73a15-151">Supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-151">Greater Than or Equals</span></span>|<span data-ttu-id="73a15-152">Date heure</span><span class="sxs-lookup"><span data-stu-id="73a15-152">Date Time</span></span><br /><br /> <span data-ttu-id="73a15-153">aujourd'hui</span><span class="sxs-lookup"><span data-stu-id="73a15-153">Today</span></span><br /><br /> <span data-ttu-id="73a15-154">Aujourd'hui - 5</span><span class="sxs-lookup"><span data-stu-id="73a15-154">Today - 5</span></span>|<span data-ttu-id="73a15-155">Non</span><span class="sxs-lookup"><span data-stu-id="73a15-155">No</span></span><br /><br /> <span data-ttu-id="73a15-156">Remarque : peut être inclus plusieurs fois dans l'expression de requête.</span><span class="sxs-lookup"><span data-stu-id="73a15-156">Note: Can be included more than once in the query expression.</span></span>|  
|<span data-ttu-id="73a15-157">Nom du lot</span><span class="sxs-lookup"><span data-stu-id="73a15-157">Batch Name</span></span>|<span data-ttu-id="73a15-158">Égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-158">Equals</span></span>|<span data-ttu-id="73a15-159">Tous (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="73a15-159">All (Default)</span></span><br /><br /> <span data-ttu-id="73a15-160">Nom de lot spécifique</span><span class="sxs-lookup"><span data-stu-id="73a15-160">Specific batch name</span></span>|<span data-ttu-id="73a15-161">Non</span><span class="sxs-lookup"><span data-stu-id="73a15-161">No</span></span>|  
|<span data-ttu-id="73a15-162">Tiers de destination</span><span class="sxs-lookup"><span data-stu-id="73a15-162">Destination Party</span></span>|<span data-ttu-id="73a15-163">Égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-163">Equals</span></span>|<span data-ttu-id="73a15-164">Tous (par défaut)</span><span class="sxs-lookup"><span data-stu-id="73a15-164">All (default)</span></span><br /><br /> <span data-ttu-id="73a15-165">Nom de tiers spécifique</span><span class="sxs-lookup"><span data-stu-id="73a15-165">Specific party name</span></span>|<span data-ttu-id="73a15-166">Non</span><span class="sxs-lookup"><span data-stu-id="73a15-166">No</span></span>|  
|<span data-ttu-id="73a15-167">Type de codage EDI</span><span class="sxs-lookup"><span data-stu-id="73a15-167">EDI encoding type</span></span>|<span data-ttu-id="73a15-168">Égal à</span><span class="sxs-lookup"><span data-stu-id="73a15-168">Equals</span></span>|<span data-ttu-id="73a15-169">X12</span><span class="sxs-lookup"><span data-stu-id="73a15-169">X12</span></span><br /><br /> <span data-ttu-id="73a15-170">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="73a15-170">EDIFACT</span></span><br /><br /> <span data-ttu-id="73a15-171">Tous (par défaut)</span><span class="sxs-lookup"><span data-stu-id="73a15-171">All (default)</span></span>|<span data-ttu-id="73a15-172">Non</span><span class="sxs-lookup"><span data-stu-id="73a15-172">No</span></span>|  
  
