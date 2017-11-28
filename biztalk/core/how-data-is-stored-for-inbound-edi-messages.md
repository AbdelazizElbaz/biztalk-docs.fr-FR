---
title: "Stockage des données des Messages EDI entrants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8cbcb96-c0af-4f41-b844-f0e684a4af7c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60cc8743cd945ad231f3a42f9cbd4f0e76b418d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-data-is-stored-for-inbound-edi-messages"></a><span data-ttu-id="f89b6-102">Stockage des données des messages EDI entrants</span><span class="sxs-lookup"><span data-stu-id="f89b6-102">How Data Is Stored for Inbound EDI Messages</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f89b6-103"> effectue les opérations suivantes pour générer une entrée de rapport d'état pour un échange entrant et l'accusé de réception envoyé en réponse :</span><span class="sxs-lookup"><span data-stu-id="f89b6-103"> does the following to generate a status report entry for an inbound interchange and the acknowledgment sent in response to it:</span></span>  
  
1.  <span data-ttu-id="f89b6-104">Lorsque le pipeline de réception EDI envoie un message entrant au format XML à la base de données MessageBox, il crée les entrées suivantes dans le magasin de données de création de rapports d'état avec les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f89b6-104">When inbound message XML is sent by the EDI receive pipeline to the MessageBox, the receive pipeline creates the following entries in the status reporting data store with the following values:</span></span>  
  
    -   <span data-ttu-id="f89b6-105">une entrée de rapport d'état pour chaque échange reçu, avec l'état défini sur Accepté/Partiellement accepté/Rejeté ;</span><span class="sxs-lookup"><span data-stu-id="f89b6-105">One status report entry for each interchange received, with Status set to Accepted/Partially Accepted/Rejected</span></span>  
  
    -   <span data-ttu-id="f89b6-106">une entrée de rapport d'état pour chaque accusé de réception (d'échange) technique : un par échange, avec l'état défini sur Généré ;</span><span class="sxs-lookup"><span data-stu-id="f89b6-106">One status report entry for each technical (interchange) acknowledgment, one per interchange, with Status set to Generated</span></span>  
  
    -   <span data-ttu-id="f89b6-107">une entrée de rapport d'état pour chaque accusé de réception fonctionnel : un par groupe dans X12 et un pour tous les groupes dans EDIFACT, avec l'état défini sur Généré.</span><span class="sxs-lookup"><span data-stu-id="f89b6-107">One status report entry for each functional acknowledgment, one per group in X12 and one for all groups in EDIFACT, with Status set to Generated.</span></span>  
  
2.  <span data-ttu-id="f89b6-108">Une fois que le pipeline d'envoi EDI a envoyé les accusés de réception au partenaire commercial, il met à jour les entrées relatives à l'état des accusés de réception d'échange et fonctionnels en les définissant sur Envoyé.</span><span class="sxs-lookup"><span data-stu-id="f89b6-108">After the send pipeline has sent the acknowledgments to the trading partner, the EDI send pipeline updates the Interchange ACK status and Functional ACK status entries to Sent, as appropriate.</span></span> <span data-ttu-id="f89b6-109">Aucune modification n'est apportée à l'entrée relative à l'état de l'échange.</span><span class="sxs-lookup"><span data-stu-id="f89b6-109">No changes are made to the Interchange status entry.</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-inbound-interchanges"></a><span data-ttu-id="f89b6-110">Données stockées par le pipeline de réception pour les échanges entrants</span><span class="sxs-lookup"><span data-stu-id="f89b6-110">Data Stored by the Receive Pipeline for Inbound Interchanges</span></span>  
 <span data-ttu-id="f89b6-111">Le pipeline de réception crée un enregistrement dans le magasin de données de création de rapports d'état pour chaque échange reçu.</span><span class="sxs-lookup"><span data-stu-id="f89b6-111">The receive pipeline creates a record in the status report data store for each interchange that it receives.</span></span> <span data-ttu-id="f89b6-112">Les données stockées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f89b6-112">The data stored includes:</span></span>  
  
-   <span data-ttu-id="f89b6-113">Type d'enregistrement = état de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-113">Record Type = Interchange Status</span></span>  
  
-   <span data-ttu-id="f89b6-114">Direction de l'échange = réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-114">Interchange Direction = Receive</span></span>  
  
-   <span data-ttu-id="f89b6-115">Récepteur de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-115">Interchange Receiver = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-116">Expéditeur de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-116">Interchange Sender = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-117">Date de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-117">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-118">Heure de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-118">Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-119">ID de contrôle de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-119">Interchange Control ID = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-120">État de l'échange = Données de mise à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-120">Interchange Status: Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-121">Nombre de groupes d'un échange = données mises à jour (dans EDIFACT, les groupes sont facultatifs ; s'ils sont absents, la valeur définie est Non applicable)</span><span class="sxs-lookup"><span data-stu-id="f89b6-121">Count of Groups in Interchange = Update Data (In EDIFACT Groups are optional and if not present, valued as ‘Not Applicable’)</span></span>  
  
-   <span data-ttu-id="f89b6-122">ID du port de réception de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-122">Interchange Receive Port ID = Update Data</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-technical-acknowledgment-generated-in-response-to-an-inbound-interchange"></a><span data-ttu-id="f89b6-123">Données stockées par le pipeline de réception pour chaque accusé de réception technique généré en réponse à un échange entrant</span><span class="sxs-lookup"><span data-stu-id="f89b6-123">Data Stored by the Receive Pipeline for Each Technical Acknowledgment Generated in Response to an Inbound Interchange</span></span>  
 <span data-ttu-id="f89b6-124">Le pipeline d'envoi crée un enregistrement dans le magasin de données de création de rapports d'état pour chaque accusé de réception technique envoyé.</span><span class="sxs-lookup"><span data-stu-id="f89b6-124">The send pipeline creates a record in the status report data store for each technical acknowledgment that it sends.</span></span> <span data-ttu-id="f89b6-125">L'accusé de réception technique est TA1 pour X12 et le message CONTRL avec uniquement le segment UCI pour EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="f89b6-125">The technical acknowledgement is the TA1 for X12 and the CONTRL message with only the UCI Segment for EDIFACT.</span></span> <span data-ttu-id="f89b6-126">La plupart des données requises pour l'entrée sont disponibles dans les segments de code de fin et d'en-tête de l'échange (ISA/IEA ou UNB/UNZ).</span><span class="sxs-lookup"><span data-stu-id="f89b6-126">Most data required for the entry is available from the interchange header/trailer segments (ISA/IEA or UNB/UNZ).</span></span> <span data-ttu-id="f89b6-127">Les autres données sont disponibles dans les propriétés du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f89b6-127">Other data is available from send port properties.</span></span> <span data-ttu-id="f89b6-128">Les données stockées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f89b6-128">The data stored includes:</span></span>  
  
-   <span data-ttu-id="f89b6-129">Type d'enregistrement = état de l'échange/de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-129">Record Type = Interchange ACK Status</span></span>  
  
-   <span data-ttu-id="f89b6-130">Direction de l'accusé de réception d'échange = réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-130">Interchange ACK Direction = Receive</span></span>  
  
-   <span data-ttu-id="f89b6-131">Récepteur de l'échange = données mises à jour (requises à des fins de corrélation)</span><span class="sxs-lookup"><span data-stu-id="f89b6-131">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="f89b6-132">Expéditeur de l'échange = données mises à jour (requises à des fins de corrélation)</span><span class="sxs-lookup"><span data-stu-id="f89b6-132">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="f89b6-133">Date de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-133">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-134">ID de contrôle de l'échange = données mises à jour (requises à des fins de corrélation)</span><span class="sxs-lookup"><span data-stu-id="f89b6-134">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="f89b6-135">État de l’accusé de réception de l’échange = \< attendu ou non Applicable >.</span><span class="sxs-lookup"><span data-stu-id="f89b6-135">Interchange ACK Status = \< Expected or Not Applicable>.</span></span> <span data-ttu-id="f89b6-136">Si l'accusé de réception technique est configuré ou qu'une valeur lui est attribuée dans l'échange entrant, l'état est défini sur Attendu.</span><span class="sxs-lookup"><span data-stu-id="f89b6-136">If the technical ACK is configured or valued in the incoming interchange, status = Expected.</span></span> <span data-ttu-id="f89b6-137">Sinon, il est défini sur Non applicable.</span><span class="sxs-lookup"><span data-stu-id="f89b6-137">Otherwise, status = Not Applicable.</span></span>  
  
-   <span data-ttu-id="f89b6-138">ID de contrôle de l’accusé de réception de l’échange = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-138">Interchange ACK Control ID= \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-139">Date de l’accusé de réception de l’échange = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-139">Interchange ACK Date = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-140">Heure de l’accusé de réception de l’échange = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-140">Interchange ACK Time = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-141">L’accusé de réception/Code d’Action = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-141">ACK/Action Code = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-142">Code de Note de l’accusé de réception = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-142">ACK Note Code = \<not valued></span></span>  
  
## <a name="data-updated-by-the-send-pipeline-for-each-technical-acknowledgment-generated-in-response-to-inbound-interchanges"></a><span data-ttu-id="f89b6-143">Données mises à jour par le pipeline d'envoi pour chaque accusé de réception technique généré en réponse aux échanges entrants</span><span class="sxs-lookup"><span data-stu-id="f89b6-143">Data Updated by the Send Pipeline for Each Technical Acknowledgment Generated in Response to Inbound Interchanges</span></span>  
 <span data-ttu-id="f89b6-144">Pour chaque accusé de réception technique qu'il envoie, le pipeline d'envoi met à jour l'entrée de rapport d'état pour chaque échange reçu corrélé.</span><span class="sxs-lookup"><span data-stu-id="f89b6-144">For each technical acknowledgment that the send pipeline sends, it updates the status report entry for the correlated received interchange.</span></span> <span data-ttu-id="f89b6-145">La source des données sont les enveloppes d'échange créées par le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f89b6-145">The source for the data will be the Interchange envelopes created by the Send Pipeline.</span></span>  
  
 <span data-ttu-id="f89b6-146">L'Assembleur EDI recherche les enregistrements dans le magasin de données à l'aide des données des segments UCI et TA1 de l'accusé de réception entrant, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f89b6-146">The EDI Assembler locates records in the data store using data in the UCI and TA1 Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="f89b6-147">Champs de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-147">Fields in ACK</span></span>|<span data-ttu-id="f89b6-148">Champs du magasin de données</span><span class="sxs-lookup"><span data-stu-id="f89b6-148">Fields in Data store</span></span>|<span data-ttu-id="f89b6-149">Commentaire</span><span class="sxs-lookup"><span data-stu-id="f89b6-149">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="f89b6-150">ID de l'expéditeur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-150">Interchange Sender ID</span></span>|<span data-ttu-id="f89b6-151">Récepteur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-151">Interchange Receiver</span></span>|-|  
|<span data-ttu-id="f89b6-152">ID du récepteur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-152">Interchange Receiver ID</span></span>|<span data-ttu-id="f89b6-153">Expéditeur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-153">Interchange Sender</span></span>|-|  
|-|<span data-ttu-id="f89b6-154">Date de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-154">Interchange Date</span></span>|-|  
|<span data-ttu-id="f89b6-155">Numéro de contrôle d’échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-155">Interchange Control Number</span></span>|<span data-ttu-id="f89b6-156">ID de contrôle de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-156">Interchange Control ID</span></span>|-|  
|-|<span data-ttu-id="f89b6-157">Direction de l'échange = réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-157">Interchange Direction = Receive</span></span>|<span data-ttu-id="f89b6-158">Requis dans les scénarios incluant des échanges conservés à des fins d'unicité</span><span class="sxs-lookup"><span data-stu-id="f89b6-158">Required in preserved interchange scenario for uniqueness</span></span>|  
|<span data-ttu-id="f89b6-159">Type d'enregistrement</span><span class="sxs-lookup"><span data-stu-id="f89b6-159">Record Type</span></span>|<span data-ttu-id="f89b6-160">État de l’accusé de réception de l’échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-160">Interchange ACK Status</span></span>|-|  
  
 <span data-ttu-id="f89b6-161">Les données stockées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f89b6-161">The data stored includes:</span></span>  
  
-   <span data-ttu-id="f89b6-162">Type d'enregistrement = état de l'échange/de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-162">Record Type = Interchange ACK Status</span></span>  
  
-   <span data-ttu-id="f89b6-163">Direction de l'accusé de réception d'échange = envoi - données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-163">Interchange ACK Direction = Send- Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-164">État de l'échange/de l'accusé de réception = Traité ou Envoyé - Données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-164">Interchange ACK Status = Processed or Sent – Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-165">Récepteur de l'échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-165">Interchange Receiver = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-166">Expéditeur de l'échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-166">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-167">Date de l'échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-167">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-168">ID de contrôle de l'échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-168">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-169">ID de contrôle de l'accusé de réception de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-169">Interchange ACK Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-170">Date de l'accusé de réception de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-170">Interchange ACK Date = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-171">Heure de l'accusé de réception de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-171">Interchange ACK Time = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-172">Accusé de réception/code d'action = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-172">ACK/Action Code = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-173">Code de note de l'accusé de réception = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-173">ACK Note Code = Existing Data</span></span>  
  
## <a name="data-stored-by-the-receive-pipeline-for-each-functional-acknowledgment-generated-in-response-to-an-inbound-interchange"></a><span data-ttu-id="f89b6-174">Données stockées par le pipeline de réception pour chaque accusé de réception fonctionnel généré en réponse à un échange entrant</span><span class="sxs-lookup"><span data-stu-id="f89b6-174">Data Stored by the Receive Pipeline for Each Functional Acknowledgment Generated in Response to an Inbound Interchange</span></span>  
 <span data-ttu-id="f89b6-175">Le pipeline d'envoi crée un enregistrement dans le magasin de données de création de rapports d'état pour chaque accusé de réception fonctionnel envoyé.</span><span class="sxs-lookup"><span data-stu-id="f89b6-175">The send pipeline creates a record in the status report data store for each functional acknowledgment that it sends.</span></span> <span data-ttu-id="f89b6-176">Le pipeline d'envoi crée un enregistrement de chaque accusé de réception fonctionnel envoyé (en réponse à un échange reçu) dans le magasin de données de création de rapports d'état.</span><span class="sxs-lookup"><span data-stu-id="f89b6-176">The send pipeline creates a record of each functional acknowledgment sent (in response to an interchange received) in the status report data store.</span></span> <span data-ttu-id="f89b6-177">Si aucun groupe n'est présent dans EDIFACT, un seul accusé de réception fonctionnel est créé.</span><span class="sxs-lookup"><span data-stu-id="f89b6-177">If no group is present in EDIFACT, one functional ACK will still be created.</span></span> <span data-ttu-id="f89b6-178">L'entrée de rapport d'état de l'accusé de réception fonctionnel est renseignée à partir du code de fin et de l'en-tête du groupe fonctionnel (GS/GE ou UNG/UNE).</span><span class="sxs-lookup"><span data-stu-id="f89b6-178">The functional ACK status report entry will be populated from the functional group header/trailer (GS/GE or UNG/UNE).</span></span> <span data-ttu-id="f89b6-179">L'accusé de réception technique est 997 pour X12 et le message CONTRL complet pour EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="f89b6-179">The technical acknowledge is the 997 for X12 and the full CONTRL message for EDIFACT.</span></span> <span data-ttu-id="f89b6-180">Les données stockées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f89b6-180">The data stored includes:</span></span>  
  
-   <span data-ttu-id="f89b6-181">Type d'enregistrement = état de l'accusé de réception fonctionnel</span><span class="sxs-lookup"><span data-stu-id="f89b6-181">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="f89b6-182">Direction de l'accusé de réception fonctionnel = réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-182">Functional ACK Direction = Receive</span></span>  
  
-   <span data-ttu-id="f89b6-183">État de l’accusé de réception fonctionnel = \< attendu ou non Applicable >.</span><span class="sxs-lookup"><span data-stu-id="f89b6-183">Functional ACK Status = \< Expected or Not Applicable>.</span></span> <span data-ttu-id="f89b6-184">Si l'onglet d'accusé de réception fonctionnel dans le Gestionnaire d'accords partenaires est sélectionné, l'état est défini sur Attendu.</span><span class="sxs-lookup"><span data-stu-id="f89b6-184">If the functional acknowledgment tab in PAM is selected, status will set to Expected.</span></span> <span data-ttu-id="f89b6-185">Dans le cas contraire, l’état est défini à non Applicable.</span><span class="sxs-lookup"><span data-stu-id="f89b6-185">Otherwise, status will be set to Not Applicable.</span></span>  
  
-   <span data-ttu-id="f89b6-186">Récepteur de l'échange = données mises à jour (requises à des fins de corrélation)</span><span class="sxs-lookup"><span data-stu-id="f89b6-186">Interchange Receiver = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="f89b6-187">Expéditeur de l'échange = données mises à jour (requises à des fins de corrélation)</span><span class="sxs-lookup"><span data-stu-id="f89b6-187">Interchange Sender = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="f89b6-188">Date de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-188">Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-189">ID de contrôle de l'échange = données mises à jour (requises à des fins de corrélation)</span><span class="sxs-lookup"><span data-stu-id="f89b6-189">Interchange Control ID = Update Data (required for correlation)</span></span>  
  
-   <span data-ttu-id="f89b6-190">Numéro de contrôle du groupe = données mises à jour (requises à des fins de corrélation.</span><span class="sxs-lookup"><span data-stu-id="f89b6-190">Group Control Number = Update Data (required for correlation.</span></span> <span data-ttu-id="f89b6-191">Dans EDIFACT, si aucun segment de groupe n'est présent, ce champ est renseigné à l'aide de UNH.1)</span><span class="sxs-lookup"><span data-stu-id="f89b6-191">In EDIFACT if no group segments present this field is valued using UNH.1)</span></span>  
  
-   <span data-ttu-id="f89b6-192">Code de l'ID fonctionnel = données mises à jour (aucune valeur dans EDIFACT si aucun groupe n'est présent)</span><span class="sxs-lookup"><span data-stu-id="f89b6-192">Functional ID Code = Update Data (not valued in EDIFACT if group is not present)</span></span>  
  
-   <span data-ttu-id="f89b6-193">Nombre de documents informatisés = données (dans EDIFACT, ceci est mappé à UNE.1 si des segments UNG/UNE sont présents ou à UNZ.1 si aucun segment de groupe n'est présent)</span><span class="sxs-lookup"><span data-stu-id="f89b6-193">Count of Transaction Sets = Data (in EDIFACT this is mapped to UNE.1 while UNG/UNE are present or UNZ.1 if no group segments are present)</span></span>  
  
-   <span data-ttu-id="f89b6-194">ID de contrôle de l’échange de l’accusé de réception fonctionnel = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-194">Functional ACK Interchange Control ID= \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-195">Date de l’échange de l’accusé de réception fonctionnel = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-195">Functional ACK Interchange Date = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-196">Heure de l’échange des accusés de réception fonctionnel = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-196">Functional ACK Interchange Time = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-197">Nombre de documents informatisés remis = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-197">Count of Transaction Sets Delivered = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-198">Nombre de documents informatisés acceptés = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-198">Count of Transaction Sets Accepted = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-199">L’accusé de réception/Code d’Action = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-199">ACK/Action Code = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-200">Syntaxe de l’erreur/Code d’erreur = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-200">Error/Syntax Error Code  = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-201">X12 supplémentaires Code d’erreur l’accusé de réception 2 = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-201">Additional X12 ACK Error Code 2 = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-202">X12 supplémentaires l’accusé de réception Code d’erreur 3 = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-202">Additional X12 ACK Error Code 3 = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-203">X12 supplémentaires l’accusé de réception Code d’erreur 4 = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-203">Additional X12 ACK Error Code 4 = \<not valued></span></span>  
  
-   <span data-ttu-id="f89b6-204">X12 supplémentaires l’accusé de réception Code d’erreur 5 = \<aucune valeur ></span><span class="sxs-lookup"><span data-stu-id="f89b6-204">Additional X12 ACK Error Code 5 = \<not valued></span></span>  
  
## <a name="data-updated-by-the-send-pipeline-for-each-functional-acknowledgment-generated-in-response-to-inbound-interchanges"></a><span data-ttu-id="f89b6-205">Données mises à jour par le pipeline d'envoi pour chaque accusé de réception fonctionnel généré en réponse aux échanges entrants</span><span class="sxs-lookup"><span data-stu-id="f89b6-205">Data Updated by the Send Pipeline for Each Functional Acknowledgment Generated in Response to Inbound Interchanges</span></span>  
 <span data-ttu-id="f89b6-206">Pour chaque accusé de réception fonctionnel qu'il envoie, le pipeline d'envoi met à jour l'entrée de rapport d'état pour chaque échange reçu corrélé.</span><span class="sxs-lookup"><span data-stu-id="f89b6-206">For each functional acknowledgment that the send pipeline sends, it updates the status report entry for the correlated received interchange.</span></span> <span data-ttu-id="f89b6-207">La source des données sont les enveloppes d'échange créées par le pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f89b6-207">The source for the data will be the Interchange envelopes created by the Send Pipeline.</span></span>  
  
 <span data-ttu-id="f89b6-208">L'Assembleur EDI recherche les enregistrements dans le magasin de données à l'aide des données de l'échange et des segments de l'en-tête de groupe de l'accusé de réception entrant, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f89b6-208">The EDI Assembler locates records in the data store using data in the Interchange and Group Header Segments of the incoming acknowledgment, as follows:</span></span>  
  
|<span data-ttu-id="f89b6-209">Champs de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-209">Fields in ACK</span></span>|<span data-ttu-id="f89b6-210">Champs du magasin de données</span><span class="sxs-lookup"><span data-stu-id="f89b6-210">Fields in Data store</span></span>|<span data-ttu-id="f89b6-211">Commentaire</span><span class="sxs-lookup"><span data-stu-id="f89b6-211">Comment</span></span>|  
|-------------------|--------------------------|-------------|  
|<span data-ttu-id="f89b6-212">ID de l'expéditeur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-212">Interchange Sender ID</span></span>|<span data-ttu-id="f89b6-213">Récepteur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-213">Interchange Receiver</span></span>|-|  
|<span data-ttu-id="f89b6-214">ID du récepteur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-214">Interchange Receiver ID</span></span>|<span data-ttu-id="f89b6-215">Expéditeur de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-215">Interchange Sender</span></span>|-|  
|<span data-ttu-id="f89b6-216">Date de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-216">Interchange Date</span></span>|<span data-ttu-id="f89b6-217">Date de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-217">Interchange Date</span></span>|-|  
|<span data-ttu-id="f89b6-218">Numéro de contrôle d’échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-218">Interchange Control Number</span></span>|<span data-ttu-id="f89b6-219">ID de contrôle de l'échange</span><span class="sxs-lookup"><span data-stu-id="f89b6-219">Interchange Control ID</span></span>|-|  
|<span data-ttu-id="f89b6-220">Numéro de contrôle du groupe</span><span class="sxs-lookup"><span data-stu-id="f89b6-220">Group Control Number</span></span>|<span data-ttu-id="f89b6-221">Numéro de contrôle du groupe</span><span class="sxs-lookup"><span data-stu-id="f89b6-221">Group Control Number</span></span>|<span data-ttu-id="f89b6-222">Facultatif dans EDIFACT</span><span class="sxs-lookup"><span data-stu-id="f89b6-222">Optional in EDIFACT</span></span>|  
|-|<span data-ttu-id="f89b6-223">Direction de l'échange = réception</span><span class="sxs-lookup"><span data-stu-id="f89b6-223">Interchange Direction = Receive</span></span>|<span data-ttu-id="f89b6-224">Requis dans les scénarios incluant des échanges conservés à des fins d'unicité</span><span class="sxs-lookup"><span data-stu-id="f89b6-224">Required in preserved interchange scenario for uniqueness</span></span>|  
|<span data-ttu-id="f89b6-225">Type d'enregistrement</span><span class="sxs-lookup"><span data-stu-id="f89b6-225">Record Type</span></span>|<span data-ttu-id="f89b6-226">État de l'accusé de réception fonctionnel</span><span class="sxs-lookup"><span data-stu-id="f89b6-226">Functional ACK Status</span></span>|-|  
  
 <span data-ttu-id="f89b6-227">Les données stockées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f89b6-227">The data stored includes:</span></span>  
  
-   <span data-ttu-id="f89b6-228">Type d'enregistrement = état de l'accusé de réception fonctionnel</span><span class="sxs-lookup"><span data-stu-id="f89b6-228">Record Type = Functional ACK Status</span></span>  
  
-   <span data-ttu-id="f89b6-229">Direction de l'accusé de réception fonctionnel = envoi - données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-229">Functional ACK Direction = Send – Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-230">État de l'accusé de réception fonctionnel = Envoyé/Traité - Données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-230">Functional ACK Status = Sent/Processed – Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-231">Récepteur de l’échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-231">Interchange Receiver =  Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-232">Expéditeur de l'échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-232">Interchange Sender = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-233">Date de l'échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-233">Interchange Date = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-234">ID de contrôle de l'échange = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-234">Interchange Control ID = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-235">Numéro de contrôle du groupe = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-235">Group Control Number = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-236">Code de l'ID fonctionnel = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-236">Functional ID Code = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-237">Nombre de documents informatisés = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-237">Count of Transaction Sets = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-238">Accusé de réception fonctionnel pour l'ID de contrôle de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-238">Functional ACK Interchange Control ID= Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-239">Accusé de réception fonctionnel pour la date de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-239">Functional ACK Interchange Date = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-240">Accusé de réception fonctionnel pour l'heure de l'échange = données mises à jour</span><span class="sxs-lookup"><span data-stu-id="f89b6-240">Functional ACK Interchange Time = Update Data</span></span>  
  
-   <span data-ttu-id="f89b6-241">Nombre de documents informatisés reçus = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-241">Count of Transaction Sets Received = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-242">Nombre de documents informatisés acceptés = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-242">Count of Transaction Sets Accepted = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-243">Accusé de réception/code d'action = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-243">ACK/Action Code = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-244">Erreur/code d'erreur de syntaxe = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-244">Error/Syntax Error Code  = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-245">Code d'erreur 2 de l'accusé de réception X12 supplémentaire = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-245">Additional X12 ACK Error Code 2 = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-246">X12 supplémentaires Code d’erreur de l’accusé de réception 3 = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-246">Additional X12 ACK Error Code 3 = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-247">X12 supplémentaires Code d’erreur de l’accusé de réception 4 = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-247">Additional X12 ACK Error Code 4 = Existing Data</span></span>  
  
-   <span data-ttu-id="f89b6-248">X12 supplémentaires Code d’erreur de l’accusé de réception 5 = données existantes</span><span class="sxs-lookup"><span data-stu-id="f89b6-248">Additional X12 ACK Error Code 5 = Existing Data</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89b6-249">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f89b6-249">See Also</span></span>  
 <span data-ttu-id="f89b6-250">[Stockage des données pour les rapports d’état AS2 et EDI](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="f89b6-250">[How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="f89b6-251">Stockage des données pour les Messages EDI sortants</span><span class="sxs-lookup"><span data-stu-id="f89b6-251">How Data Is Stored for Outbound EDI Messages</span></span>](../core/how-data-is-stored-for-outbound-edi-messages.md)