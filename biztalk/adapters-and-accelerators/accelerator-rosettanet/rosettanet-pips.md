---
title: PIP de RosettaNet | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs, clusters
- RosettaNet, PIPs
- PIPs, PIP specifications
- PIPs, segments
- PIPs, RosettaNet
- DTDs, DTD files
ms.assetid: 2f7e8db3-9ccb-403a-9fe7-58fbba3c4cb1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1980f7c5e22259dc6c09d4f2d8dba31f3ac04d61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rosettanet-pips"></a><span data-ttu-id="09aa2-102">PIP de RosettaNet</span><span class="sxs-lookup"><span data-stu-id="09aa2-102">RosettaNet PIPs</span></span>
<span data-ttu-id="09aa2-103">L’organisation RosettaNet crée et gère les processus d’Interface partenaires (PIP) pour fournir des définitions communes de processus d’entreprise pour tous les échanges de messages RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="09aa2-103">The RosettaNet organization creates and maintains Partner Interface Processes (PIPs) to provide common business-process definitions for all RosettaNet message exchanges.</span></span>  
  
 <span data-ttu-id="09aa2-104">Chaque spécification PIP fournit un fichier de définition (DTD) de type de document et un document d’indications de message.</span><span class="sxs-lookup"><span data-stu-id="09aa2-104">Each PIP specification provides a document type definition (DTD) file and a message guideline document.</span></span> <span data-ttu-id="09aa2-105">Le fichier DTD définit la structure du message de contenu de service.</span><span class="sxs-lookup"><span data-stu-id="09aa2-105">The DTD file defines the service-content message structure.</span></span> <span data-ttu-id="09aa2-106">Le document de l’indication de message, qui est un fichier HTML lisible, spécifie les contraintes au niveau de l’élément.</span><span class="sxs-lookup"><span data-stu-id="09aa2-106">The message-guideline document, which is a human-readable HTML file, specifies element-level constraints.</span></span> <span data-ttu-id="09aa2-107">Ensemble, ils fournissent une définition complète du processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="09aa2-107">Together, they provide a complete definition of the business process.</span></span>  
  
 <span data-ttu-id="09aa2-108">Pour plus d’informations sur les spécifications PIP, consultez le site Web de RosettaNet [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859).</span><span class="sxs-lookup"><span data-stu-id="09aa2-108">For more information about PIP specifications, see the RosettaNet Web site at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859).</span></span>  
  
## <a name="pip-contents"></a><span data-ttu-id="09aa2-109">Contenu PIP</span><span class="sxs-lookup"><span data-stu-id="09aa2-109">PIP Contents</span></span>  
 <span data-ttu-id="09aa2-110">Une spécification PIP effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="09aa2-110">A PIP specification does the following:</span></span>  
  
-   <span data-ttu-id="09aa2-111">Décrit le modèle de processus public il implémente</span><span class="sxs-lookup"><span data-stu-id="09aa2-111">Describes which public process pattern it implements</span></span>  
  
-   <span data-ttu-id="09aa2-112">Décrit comment configurer le processus public</span><span class="sxs-lookup"><span data-stu-id="09aa2-112">Describes how to configure the public process</span></span>  
  
-   <span data-ttu-id="09aa2-113">Fournit des références pour les documents à transmettre au sein du PIP</span><span class="sxs-lookup"><span data-stu-id="09aa2-113">Provides references to the documents to exchange within the PIP</span></span>  
  
 <span data-ttu-id="09aa2-114">Une spécification PIP inclut trois parties principales : une vue opérationnel Business (BOV), affichage du Service fonctionnel (FSV) et une vue de Framework implémentation (IFV).</span><span class="sxs-lookup"><span data-stu-id="09aa2-114">A PIP specification includes three major parts: a Business Operational View (BOV), Functional Service View (FSV), and an Implementation Framework View (IFV).</span></span> <span data-ttu-id="09aa2-115">Chacune de ces vues spécifie les contraintes au niveau de l’élément :</span><span class="sxs-lookup"><span data-stu-id="09aa2-115">Each of these views specifies element-level constraints:</span></span>  
  
-   <span data-ttu-id="09aa2-116">Le BOV spécifie la sémantique des entités de données d’entreprise et le flux du processus.</span><span class="sxs-lookup"><span data-stu-id="09aa2-116">The BOV specifies the semantics of business data entities and the business process flow.</span></span> <span data-ttu-id="09aa2-117">Il décrit le démarrage et les États de fin et les rôles de partenaire.</span><span class="sxs-lookup"><span data-stu-id="09aa2-117">It describes start and end states, and partner roles.</span></span> <span data-ttu-id="09aa2-118">Elle décrit l’interaction entre les rôles et sécurité des informations d’audit et les contrôles de processus.</span><span class="sxs-lookup"><span data-stu-id="09aa2-118">It describes the interaction between roles, and details security, audit, and process controls.</span></span> <span data-ttu-id="09aa2-119">Il spécifie les documents commerciaux et les entités de données d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="09aa2-119">It specifies the business documents and business data entities.</span></span>  
  
-   <span data-ttu-id="09aa2-120">Le FSV spécifie les interactions, les agents et les services de composants réseau.</span><span class="sxs-lookup"><span data-stu-id="09aa2-120">The FSV specifies network component services, agents, and interactions.</span></span> <span data-ttu-id="09aa2-121">Il fournit la conception du composant de réseau requise pour exécuter le processus PIP et décrit les interactions entre les composants réseau.</span><span class="sxs-lookup"><span data-stu-id="09aa2-121">It provides the network component design required to run the PIPs, and describes possible network component interactions.</span></span>  
  
-   <span data-ttu-id="09aa2-122">Le IFV spécifie les formats de message de protocole de réseau et les spécifications de communication requises pour exécuter le PIP.</span><span class="sxs-lookup"><span data-stu-id="09aa2-122">The IFV specifies the network-protocol message formats and communication requirements required to run the PIP.</span></span>  
  
## <a name="clusters-and-segments"></a><span data-ttu-id="09aa2-123">Les Segments et les clusters</span><span class="sxs-lookup"><span data-stu-id="09aa2-123">Clusters and Segments</span></span>  
 <span data-ttu-id="09aa2-124">Vous classez PIP en une fonction d’entreprise de niveau supérieur (cluster) et une sous-fonction (segment).</span><span class="sxs-lookup"><span data-stu-id="09aa2-124">You categorize PIPs by a high-level business function (cluster) and a subfunction (segment).</span></span> <span data-ttu-id="09aa2-125">Les segments et les clusters organisent les messages en catégories reconnaissables.</span><span class="sxs-lookup"><span data-stu-id="09aa2-125">Clusters and segments organize business messages into recognizable categories.</span></span> <span data-ttu-id="09aa2-126">Le tableau suivant répertorie ces segments et les clusters.</span><span class="sxs-lookup"><span data-stu-id="09aa2-126">The following table lists these clusters and segments.</span></span>  
  
|<span data-ttu-id="09aa2-127">Clusters</span><span class="sxs-lookup"><span data-stu-id="09aa2-127">Clusters</span></span>|<span data-ttu-id="09aa2-128">Segments</span><span class="sxs-lookup"><span data-stu-id="09aa2-128">Segments</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="09aa2-129">0 : prise en charge de RosettaNet</span><span class="sxs-lookup"><span data-stu-id="09aa2-129">0: RosettaNet Support</span></span>|<span data-ttu-id="09aa2-130">0 : administration</span><span class="sxs-lookup"><span data-stu-id="09aa2-130">0A: Administrative</span></span><br /><br /> <span data-ttu-id="09aa2-131">0C : test</span><span class="sxs-lookup"><span data-stu-id="09aa2-131">0C: Testing</span></span>|  
|<span data-ttu-id="09aa2-132">1 : partenaires produit et Service, consultez</span><span class="sxs-lookup"><span data-stu-id="09aa2-132">1: Partner Product & Service Review</span></span>|<span data-ttu-id="09aa2-133">1 a : examen du partenaire</span><span class="sxs-lookup"><span data-stu-id="09aa2-133">1A: Partner Review</span></span><br /><br /> <span data-ttu-id="09aa2-134">1 b : produit et Service, consultez</span><span class="sxs-lookup"><span data-stu-id="09aa2-134">1B: Product & Service Review</span></span>|  
|<span data-ttu-id="09aa2-135">2 : informations de produit</span><span class="sxs-lookup"><span data-stu-id="09aa2-135">2: Product Information</span></span>|<span data-ttu-id="09aa2-136">2 a : préparation pour la Distribution</span><span class="sxs-lookup"><span data-stu-id="09aa2-136">2A: Preparation for Distribution</span></span><br /><br /> <span data-ttu-id="09aa2-137">2 b : Notification de modification de produit</span><span class="sxs-lookup"><span data-stu-id="09aa2-137">2B: Product Change Notification</span></span><br /><br /> <span data-ttu-id="09aa2-138">2C : les informations de conception de produit</span><span class="sxs-lookup"><span data-stu-id="09aa2-138">2C: Product Design Information</span></span><br /><br /> <span data-ttu-id="09aa2-139">2D : conception collaboratif et l’ingénierie</span><span class="sxs-lookup"><span data-stu-id="09aa2-139">2D: Collaborative Design & Engineering</span></span>|  
|<span data-ttu-id="09aa2-140">3 : gestion des commandes</span><span class="sxs-lookup"><span data-stu-id="09aa2-140">3: Order Management</span></span>|<span data-ttu-id="09aa2-141">3 a : devis & de saisie de commande</span><span class="sxs-lookup"><span data-stu-id="09aa2-141">3A: Quote & Order Entry</span></span><br /><br /> <span data-ttu-id="09aa2-142">3 b : transport et Distribution</span><span class="sxs-lookup"><span data-stu-id="09aa2-142">3B: Transportation & Distribution</span></span><br /><br /> <span data-ttu-id="09aa2-143">3c : retourne & Finance</span><span class="sxs-lookup"><span data-stu-id="09aa2-143">3C: Returns & Finance</span></span><br /><br /> <span data-ttu-id="09aa2-144">3D : Configuration du produit</span><span class="sxs-lookup"><span data-stu-id="09aa2-144">3D: Product Configuration</span></span>|  
|<span data-ttu-id="09aa2-145">4 : gestion des stocks</span><span class="sxs-lookup"><span data-stu-id="09aa2-145">4: Inventory Management</span></span>|<span data-ttu-id="09aa2-146">4 a : prévision collaboration</span><span class="sxs-lookup"><span data-stu-id="09aa2-146">4A: Collaborative Forecasting</span></span><br /><br /> <span data-ttu-id="09aa2-147">4 b : Allocation de stock</span><span class="sxs-lookup"><span data-stu-id="09aa2-147">4B: Inventory Allocation</span></span><br /><br /> <span data-ttu-id="09aa2-148">4c : les rapports d’inventaire</span><span class="sxs-lookup"><span data-stu-id="09aa2-148">4C: Inventory Reporting</span></span><br /><br /> <span data-ttu-id="09aa2-149">4D : demande de réapprovisionnement de stock</span><span class="sxs-lookup"><span data-stu-id="09aa2-149">4D: Inventory Replenishment</span></span><br /><br /> <span data-ttu-id="09aa2-150">4e : déclaration des ventes</span><span class="sxs-lookup"><span data-stu-id="09aa2-150">4E: Sales Reporting</span></span><br /><br /> <span data-ttu-id="09aa2-151">4f : Protection de prix</span><span class="sxs-lookup"><span data-stu-id="09aa2-151">4F: Price Protection</span></span>|  
|<span data-ttu-id="09aa2-152">5 : gestion des informations marketing</span><span class="sxs-lookup"><span data-stu-id="09aa2-152">5: Marketing Information Management</span></span>|<span data-ttu-id="09aa2-153">5 a : opportunité gestion des prospects</span><span class="sxs-lookup"><span data-stu-id="09aa2-153">5A: Lead Opportunity Management</span></span><br /><br /> <span data-ttu-id="09aa2-154">5 b : gestion de la campagne Marketing</span><span class="sxs-lookup"><span data-stu-id="09aa2-154">5B: Marketing Campaign Management</span></span>|  
|<span data-ttu-id="09aa2-155">6 : prise en charge et Service</span><span class="sxs-lookup"><span data-stu-id="09aa2-155">6: Service and Support</span></span>|<span data-ttu-id="09aa2-156">6 a : fournir et d’administrer des garanties, Packages de Service et de contrat de Services</span><span class="sxs-lookup"><span data-stu-id="09aa2-156">6A: Provide and Administer Warranties, Service Packages, and Contract Services</span></span><br /><br /> <span data-ttu-id="09aa2-157">6 b : fournir et d’administrer la gestion des actifs (fusionnée avec 6 a)</span><span class="sxs-lookup"><span data-stu-id="09aa2-157">6B: Provide and Administer Asset Management (Merged with 6A)</span></span><br /><br /> <span data-ttu-id="09aa2-158">6C : assistance technique et gestion des services</span><span class="sxs-lookup"><span data-stu-id="09aa2-158">6C: Technical Support and Service Management</span></span>|  
|<span data-ttu-id="09aa2-159">7 : de fabrication</span><span class="sxs-lookup"><span data-stu-id="09aa2-159">7: Manufacturing</span></span>|<span data-ttu-id="09aa2-160">7 a : transfert de conception</span><span class="sxs-lookup"><span data-stu-id="09aa2-160">7A: Design Transfer</span></span><br /><br /> <span data-ttu-id="09aa2-161">7 b : gérer WO de fabrication et les travaux en cours</span><span class="sxs-lookup"><span data-stu-id="09aa2-161">7B: Manage Manufacturing WO & WIP</span></span><br /><br /> <span data-ttu-id="09aa2-162">7C : distribuer les informations d’édition</span><span class="sxs-lookup"><span data-stu-id="09aa2-162">7C: Distribute Manufacturing Information</span></span>|  
  
 <span data-ttu-id="09aa2-163">Chaque segment inclut un numéro de message spécifique PIP.</span><span class="sxs-lookup"><span data-stu-id="09aa2-163">Each segment includes a number of specific message PIPs.</span></span> <span data-ttu-id="09aa2-164">Par exemple, le PIP 3 a 4 est une partie du cluster de gestion des commandes (Cluster 3) et du segment apostrophe et Saisie des commandes (un Segment de Cluster 3).</span><span class="sxs-lookup"><span data-stu-id="09aa2-164">For example, the 3A4 PIP is a part of the Order Management cluster (Cluster 3) and the Quote and Order Entry segment (Segment A of Cluster 3).</span></span> <span data-ttu-id="09aa2-165">Ce segment inclut les autres processus PIP messages connexes, comme suit :</span><span class="sxs-lookup"><span data-stu-id="09aa2-165">This segment includes other related message PIPs, as follows:</span></span>  
  
 <span data-ttu-id="09aa2-166">Cluster 3 : Gestion des commandes</span><span class="sxs-lookup"><span data-stu-id="09aa2-166">Cluster 3: Order Management</span></span>  
  
-   <span data-ttu-id="09aa2-167">Segment A: devis et de saisie de commande</span><span class="sxs-lookup"><span data-stu-id="09aa2-167">Segment A: Quote and Order Entry</span></span>  
  
    -   <span data-ttu-id="09aa2-168">PIP 3A1 : demande de devis</span><span class="sxs-lookup"><span data-stu-id="09aa2-168">PIP 3A1: Request Quote</span></span>  
  
    -   <span data-ttu-id="09aa2-169">PIP 3A2 : demande de prix et disponibilité</span><span class="sxs-lookup"><span data-stu-id="09aa2-169">PIP 3A2: Request Price and Availability</span></span>  
  
    -   <span data-ttu-id="09aa2-170">PIP 3A3 : demande de transfert de panier d’achat</span><span class="sxs-lookup"><span data-stu-id="09aa2-170">PIP 3A3: Request Shopping Cart Transfer</span></span>  
  
    -   <span data-ttu-id="09aa2-171">3 a 4 PIP : gérer le bon de commande</span><span class="sxs-lookup"><span data-stu-id="09aa2-171">PIP 3A4: Manage Purchase Order</span></span>  
  
    -   <span data-ttu-id="09aa2-172">PIP 3A5 : état de la commande de requête</span><span class="sxs-lookup"><span data-stu-id="09aa2-172">PIP 3A5: Query Order Status</span></span>  
  
    -   <span data-ttu-id="09aa2-173">PIP 3A6 : distribuer l’état de la commande</span><span class="sxs-lookup"><span data-stu-id="09aa2-173">PIP 3A6: Distribute Order Status</span></span>  
  
    -   <span data-ttu-id="09aa2-174">…</span><span class="sxs-lookup"><span data-stu-id="09aa2-174">…</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09aa2-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09aa2-175">See Also</span></span>  
 <span data-ttu-id="09aa2-176">[RosettaNet et CIDX normes de messagerie](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md) </span><span class="sxs-lookup"><span data-stu-id="09aa2-176">[RosettaNet and CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md) </span></span>  
 [<span data-ttu-id="09aa2-177">Norme RNIF</span><span class="sxs-lookup"><span data-stu-id="09aa2-177">RNIF Standard</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)