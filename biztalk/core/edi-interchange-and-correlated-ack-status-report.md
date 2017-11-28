---
title: "Échange EDI et état ACK corrélé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a112cc3d-d34c-4652-a8ee-3355a31d4a03
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5f4268badf9907eb90b090abe34a8355b3ab8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-interchange-and-correlated-ack-status-report"></a><span data-ttu-id="9432e-102">Rapport d'échange EDI et d'état de l'accusé de réception corrélé</span><span class="sxs-lookup"><span data-stu-id="9432e-102">EDI Interchange and Correlated ACK Status Report</span></span>
<span data-ttu-id="9432e-103">Ce rapport affiche les échanges EDI traités par les pipelines d'envoi et de réception EDI, ainsi que les accusés de réception corrélés à ces échanges.</span><span class="sxs-lookup"><span data-stu-id="9432e-103">This report shows all EDI interchanges that are processed by the EDI send and receive pipelines, and the acknowledgment correlated to those interchanges.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="9432e-104">Champs du rapport État</span><span class="sxs-lookup"><span data-stu-id="9432e-104">Fields in the Status Report</span></span>  
 <span data-ttu-id="9432e-105">Le rapport Échange EDI et état ACK corrélé indique les informations suivantes relatives aux échanges reçus ou envoyés et aux accusés de réception qui leur sont corrélés :</span><span class="sxs-lookup"><span data-stu-id="9432e-105">The EDI Interchange and Correlated ACK Status Report displays the following information for the received or sent interchanges and the acknowledgments that are correlated to them:</span></span>  
  
-   <span data-ttu-id="9432e-106">Tiers expéditeur</span><span class="sxs-lookup"><span data-stu-id="9432e-106">Sender Party</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9432e-107">Le tiers expéditeur est déterminé comme suit :</span><span class="sxs-lookup"><span data-stu-id="9432e-107">The sender party will be determined as follows:</span></span>  
    >   
    >  -   <span data-ttu-id="9432e-108">Si le nom du tiers dans l'échange correspond au nom configuré dans les propriétés EDI d'un tiers, le nom configuré s'affiche.</span><span class="sxs-lookup"><span data-stu-id="9432e-108">If the party name in the interchange matches the name configured in the EDI Properties for a party, then the configured name is displayed.</span></span>  
    > -   <span data-ttu-id="9432e-109">Si le nom du tiers dans l'échange ne correspond à aucune des propriétés EDI configurées pour les tiers existants, le nom du tiers spécifié dans l'échange s'affiche.</span><span class="sxs-lookup"><span data-stu-id="9432e-109">If the party name in the interchange does not match any of the configured EDI Properties for existing parties, the party name specified in the interchange is displayed.</span></span>  
  
-   <span data-ttu-id="9432e-110">Tiers récepteur</span><span class="sxs-lookup"><span data-stu-id="9432e-110">Receiver Party</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9432e-111">Le nom du tiers récepteur est déterminé comme suit :</span><span class="sxs-lookup"><span data-stu-id="9432e-111">The receiver party name will be determined as follows:</span></span>  
    >   
    >  -   <span data-ttu-id="9432e-112">Si le nom du tiers dans l'échange correspond au nom configuré dans les propriétés EDI d'un tiers, le nom configuré s'affiche.</span><span class="sxs-lookup"><span data-stu-id="9432e-112">If the party name in the interchange matches the name configured in the EDI Properties for a party, then the configured name is displayed.</span></span>  
    > -   <span data-ttu-id="9432e-113">Si le nom du tiers dans l'échange ne correspond à aucune des propriétés EDI configurées pour les tiers existants, le nom du tiers spécifié dans l'échange s'affiche.</span><span class="sxs-lookup"><span data-stu-id="9432e-113">If the party name in the interchange does not match any of the configured EDI Properties for existing parties, the party name specified in the interchange is displayed.</span></span>  
  
-   <span data-ttu-id="9432e-114">ID de contrôle</span><span class="sxs-lookup"><span data-stu-id="9432e-114">Control ID</span></span>  
  
-   <span data-ttu-id="9432e-115">Sens</span><span class="sxs-lookup"><span data-stu-id="9432e-115">Direction</span></span>  
  
-   <span data-ttu-id="9432e-116">date/heure de l'échange ;</span><span class="sxs-lookup"><span data-stu-id="9432e-116">Interchange Date Time</span></span>  
  
-   <span data-ttu-id="9432e-117">Type de codage EDI</span><span class="sxs-lookup"><span data-stu-id="9432e-117">EDI encoding type</span></span>  
  
-   <span data-ttu-id="9432e-118">État de l'échange</span><span class="sxs-lookup"><span data-stu-id="9432e-118">Interchange Status</span></span>  
  
-   <span data-ttu-id="9432e-119">Nombre de groupes</span><span class="sxs-lookup"><span data-stu-id="9432e-119">Group Count</span></span>  
  
-   <span data-ttu-id="9432e-120">ID de port</span><span class="sxs-lookup"><span data-stu-id="9432e-120">Port ID</span></span>  
  
-   <span data-ttu-id="9432e-121">Alias du tiers expéditeur</span><span class="sxs-lookup"><span data-stu-id="9432e-121">Sender Party Alias</span></span>  
  
-   <span data-ttu-id="9432e-122">Alias du tiers récepteur</span><span class="sxs-lookup"><span data-stu-id="9432e-122">Receiver Party Alias</span></span>  
  
-   <span data-ttu-id="9432e-123">ID de corrélation du document informatisé</span><span class="sxs-lookup"><span data-stu-id="9432e-123">Transaction Set Correlation ID</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="9432e-124">Champs de l'expression de requête du rapport d'état</span><span class="sxs-lookup"><span data-stu-id="9432e-124">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="9432e-125">Vous pouvez personnaliser le rapport Échange EDI et état ACK corrélé en modifiant les champs de l'expression de requête qui détermine les données affichées.</span><span class="sxs-lookup"><span data-stu-id="9432e-125">You can customize the EDI Interchange and Correlated ACK Status Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="9432e-126">Les champs suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="9432e-126">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="9432e-127">Champ de l'expression de requête</span><span class="sxs-lookup"><span data-stu-id="9432e-127">Query Expression Field</span></span>|<span data-ttu-id="9432e-128">Opérateurs potentiels</span><span class="sxs-lookup"><span data-stu-id="9432e-128">Potential Operators</span></span>|<span data-ttu-id="9432e-129">Valeurs potentielles</span><span class="sxs-lookup"><span data-stu-id="9432e-129">Potential Values</span></span>|<span data-ttu-id="9432e-130">Inclus par défaut ?</span><span class="sxs-lookup"><span data-stu-id="9432e-130">Included By Default?</span></span>|  
|<span data-ttu-id="9432e-131">Rechercher</span><span class="sxs-lookup"><span data-stu-id="9432e-131">Search for</span></span>|<span data-ttu-id="9432e-132">Égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-132">Equals</span></span>|<span data-ttu-id="9432e-133">État de l'échange/de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="9432e-133">Interchange/ACK Status</span></span>|<span data-ttu-id="9432e-134">Oui (requis)</span><span class="sxs-lookup"><span data-stu-id="9432e-134">Yes (required)</span></span>|  
|<span data-ttu-id="9432e-135">État</span><span class="sxs-lookup"><span data-stu-id="9432e-135">Status</span></span>|<span data-ttu-id="9432e-136">Égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-136">Equals</span></span><br /><br /> <span data-ttu-id="9432e-137">Différent de</span><span class="sxs-lookup"><span data-stu-id="9432e-137">Not Equals</span></span>|<span data-ttu-id="9432e-138">Accepté</span><span class="sxs-lookup"><span data-stu-id="9432e-138">Accepted</span></span><br /><br /> <span data-ttu-id="9432e-139">Accepté avec erreurs</span><span class="sxs-lookup"><span data-stu-id="9432e-139">Accepted with Errors</span></span><br /><br /> <span data-ttu-id="9432e-140">Envoyé</span><span class="sxs-lookup"><span data-stu-id="9432e-140">Sent</span></span><br /><br /> <span data-ttu-id="9432e-141">Tous</span><span class="sxs-lookup"><span data-stu-id="9432e-141">All</span></span><br /><br /> <span data-ttu-id="9432e-142">Accusé de réception attendu</span><span class="sxs-lookup"><span data-stu-id="9432e-142">Ack Expected</span></span><br /><br /> <span data-ttu-id="9432e-143">Accusé de réception non attendu</span><span class="sxs-lookup"><span data-stu-id="9432e-143">Ack Not Expected</span></span><br /><br /> <span data-ttu-id="9432e-144">Rejeté</span><span class="sxs-lookup"><span data-stu-id="9432e-144">Rejected</span></span><br /><br /> <span data-ttu-id="9432e-145">(Ces valeurs sont définies ci-dessous.)</span><span class="sxs-lookup"><span data-stu-id="9432e-145">(These values are defined below.)</span></span>|<span data-ttu-id="9432e-146">Oui</span><span class="sxs-lookup"><span data-stu-id="9432e-146">Yes</span></span>|  
|<span data-ttu-id="9432e-147">date/heure de l'échange ;</span><span class="sxs-lookup"><span data-stu-id="9432e-147">Interchange Date Time</span></span>|<span data-ttu-id="9432e-148">Inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-148">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="9432e-149">Supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-149">Greater Than or Equals</span></span>|<span data-ttu-id="9432e-150">Date/heure spécifique</span><span class="sxs-lookup"><span data-stu-id="9432e-150">Specific Date Time</span></span><br /><br /> <span data-ttu-id="9432e-151">aujourd'hui</span><span class="sxs-lookup"><span data-stu-id="9432e-151">Today</span></span><br /><br /> <span data-ttu-id="9432e-152">Aujourd'hui - 1</span><span class="sxs-lookup"><span data-stu-id="9432e-152">Today - 1</span></span>|<span data-ttu-id="9432e-153">Oui</span><span class="sxs-lookup"><span data-stu-id="9432e-153">Yes</span></span><br /><br /> <span data-ttu-id="9432e-154">Remarque : peut être inclus plusieurs fois dans l'expression de requête.</span><span class="sxs-lookup"><span data-stu-id="9432e-154">Note: Can be included more than once in the query expression.</span></span>|  
|<span data-ttu-id="9432e-155">Résultats (nb maximal)</span><span class="sxs-lookup"><span data-stu-id="9432e-155">Maximum Matches</span></span>|<span data-ttu-id="9432e-156">Égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-156">Equals</span></span>|<span data-ttu-id="9432e-157">Entier (valeur par défaut 50)</span><span class="sxs-lookup"><span data-stu-id="9432e-157">Integer (default of 50)</span></span>|<span data-ttu-id="9432e-158">Oui</span><span class="sxs-lookup"><span data-stu-id="9432e-158">Yes</span></span>|  
|<span data-ttu-id="9432e-159">ID de contrôle</span><span class="sxs-lookup"><span data-stu-id="9432e-159">Control ID</span></span>|<span data-ttu-id="9432e-160">Égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-160">Equals</span></span>|<span data-ttu-id="9432e-161">ID de contrôle de l'échange</span><span class="sxs-lookup"><span data-stu-id="9432e-161">Interchange Control ID</span></span>|<span data-ttu-id="9432e-162">Non</span><span class="sxs-lookup"><span data-stu-id="9432e-162">No</span></span>|  
|<span data-ttu-id="9432e-163">Sens</span><span class="sxs-lookup"><span data-stu-id="9432e-163">Direction</span></span>|<span data-ttu-id="9432e-164">Égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-164">Equals</span></span>|<span data-ttu-id="9432e-165">Tous (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9432e-165">All (default)</span></span><br /><br /> <span data-ttu-id="9432e-166">Recevoir</span><span class="sxs-lookup"><span data-stu-id="9432e-166">Receive</span></span><br /><br /> <span data-ttu-id="9432e-167">Send</span><span class="sxs-lookup"><span data-stu-id="9432e-167">Send</span></span>|<span data-ttu-id="9432e-168">Non</span><span class="sxs-lookup"><span data-stu-id="9432e-168">No</span></span>|  
|<span data-ttu-id="9432e-169">Tiers récepteur</span><span class="sxs-lookup"><span data-stu-id="9432e-169">Receiver Party</span></span>|<span data-ttu-id="9432e-170">Égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-170">Equals</span></span>|<span data-ttu-id="9432e-171">Tous (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9432e-171">All (default)</span></span><br /><br /> <span data-ttu-id="9432e-172">Nom de tiers spécifique</span><span class="sxs-lookup"><span data-stu-id="9432e-172">Specific party name</span></span>|<span data-ttu-id="9432e-173">Non</span><span class="sxs-lookup"><span data-stu-id="9432e-173">No</span></span>|  
|<span data-ttu-id="9432e-174">Tiers expéditeur</span><span class="sxs-lookup"><span data-stu-id="9432e-174">Sender Party</span></span>|<span data-ttu-id="9432e-175">Égal à</span><span class="sxs-lookup"><span data-stu-id="9432e-175">Equals</span></span>|<span data-ttu-id="9432e-176">Tous (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9432e-176">All (default)</span></span><br /><br /> <span data-ttu-id="9432e-177">Nom de tiers spécifique</span><span class="sxs-lookup"><span data-stu-id="9432e-177">Specific party name</span></span>|<span data-ttu-id="9432e-178">Non</span><span class="sxs-lookup"><span data-stu-id="9432e-178">No</span></span>|  
  
## <a name="status-definitions"></a><span data-ttu-id="9432e-179">Définitions d'état</span><span class="sxs-lookup"><span data-stu-id="9432e-179">Status Definitions</span></span>  
 <span data-ttu-id="9432e-180">Les valeurs d'état utilisées dans les rapports d'état EDI ont les définitions suivantes :</span><span class="sxs-lookup"><span data-stu-id="9432e-180">The status values used in EDI status reports have the following definitions:</span></span>  
  
-   <span data-ttu-id="9432e-181">Accepté : échange valide.</span><span class="sxs-lookup"><span data-stu-id="9432e-181">Accepted: Valid interchange</span></span>  
  
-   <span data-ttu-id="9432e-182">Accepté avec erreurs : des erreurs ont été notées dans les segments.</span><span class="sxs-lookup"><span data-stu-id="9432e-182">Accepted with Errors: Errors were noted in segments</span></span>  
  
-   <span data-ttu-id="9432e-183">Envoyé : l'échange a été envoyé avec succès.</span><span class="sxs-lookup"><span data-stu-id="9432e-183">Sent: The interchange was sent successfully</span></span>  
  
-   <span data-ttu-id="9432e-184">Tout : affiche un message avec toute autre valeur.</span><span class="sxs-lookup"><span data-stu-id="9432e-184">All: Display a message with any of the other values</span></span>  
  
-   <span data-ttu-id="9432e-185">Accusé de réception attendu</span><span class="sxs-lookup"><span data-stu-id="9432e-185">Ack Expected</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9432e-186">Le champ État de l'échange dans le rapport d'état État de l'échange et détails de l'accusé de réception sera défini à Accusé de réception attendu pour un message sortant lorsque le message est envoyé si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attend un accusé de réception technique.</span><span class="sxs-lookup"><span data-stu-id="9432e-186">The Interchange Status field in the Interchange Status and ACK Details status report will be set to "Ack Expected" for an outbound message when the message is sent if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] expects a technical acknowledgment.</span></span> <span data-ttu-id="9432e-187">Cela se produit si le **TA1 attendu** propriété est définie dans **accusés de réception** page d’onglet d’accord unidirectionnel. L'état passe à Accepté lorsque l'accusé de réception technique est reçu et validé.</span><span class="sxs-lookup"><span data-stu-id="9432e-187">This occurs if the **TA1 Expected** property is set in **Acknowledgements** page for the one-way agreement tab. The status will be changed to “Accepted” when the technical acknowledgment has been received and validated.</span></span> <span data-ttu-id="9432e-188">Notez que cela se produit uniquement pour un accusé de réception technique, et non pas pour un accusé de réception fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="9432e-188">Note that this only occurs for a technical acknowledgment, not a functional acknowledgment.</span></span>  
  
-   <span data-ttu-id="9432e-189">Accusé de réception non attendu</span><span class="sxs-lookup"><span data-stu-id="9432e-189">Ack Not Expected</span></span>  
  
-   <span data-ttu-id="9432e-190">Rejeté : l'échange n'est pas valide en raison d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="9432e-190">Rejected: The interchange was invalid due to errors.</span></span>  
  
## <a name="additional-reports-displayed-from-this-report"></a><span data-ttu-id="9432e-191">Rapports supplémentaires affichés à partir de ce rapport</span><span class="sxs-lookup"><span data-stu-id="9432e-191">Additional Reports Displayed from This Report</span></span>  
 <span data-ttu-id="9432e-192">Vous pouvez afficher les rapports d'état supplémentaires suivants pour un document informatisé affiché dans le rapport Détails du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="9432e-192">You can display the following additional status reports for a transaction set shown in the Transaction Set Details report.</span></span> <span data-ttu-id="9432e-193">Pour accéder aux rapports, cliquez avec le bouton droit sur un échange ou un accusé de réception figurant dans le rapport Échange EDI et état ACK corrélé, puis cliquez sur la commande appropriée :</span><span class="sxs-lookup"><span data-stu-id="9432e-193">You access the reports by right-clicking an interchange or acknowledgment listed in the EDI Interchange and Correlated ACK Status report, and then clicking the appropriate command:</span></span>  
  
-   [<span data-ttu-id="9432e-194">État de l’échange et rapport d’état de détails de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="9432e-194">Interchange Status and ACK Details Status Report</span></span>](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [<span data-ttu-id="9432e-195">Rapport d’état détails transaction</span><span class="sxs-lookup"><span data-stu-id="9432e-195">Transaction Set Details Status Report</span></span>](../core/transaction-set-details-status-report.md)  
  
## <a name="next-steps"></a><span data-ttu-id="9432e-196">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9432e-196">Next steps</span></span>
  
-   [<span data-ttu-id="9432e-197">État de l’échange et rapport d’état de détails de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="9432e-197">Interchange Status and ACK Details Status Report</span></span>](../core/interchange-status-and-ack-details-status-report.md)  
  
-   [<span data-ttu-id="9432e-198">Rapport d’état détails transaction</span><span class="sxs-lookup"><span data-stu-id="9432e-198">Transaction Set Details Status Report</span></span>](../core/transaction-set-details-status-report.md)  
  
-   [<span data-ttu-id="9432e-199">Rapport d’état du contenu du Message EDI</span><span class="sxs-lookup"><span data-stu-id="9432e-199">EDI Message Content Status Report</span></span>](../core/edi-message-content-status-report.md)  
  
