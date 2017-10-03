---
title: Les Segments de champ REPEATABLE | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- segments, repeatable fields
- QPD
- Table Row Data (RDT)
- Query Parameter Definition (QPD)
- Segments table
- RDT
ms.assetid: 4c31cb56-21e5-4918-aaf6-67e8ceddd74f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a801e39fac0e0bdf0cfb9ee88811703fd1c4373d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repeatable-field-segments"></a><span data-ttu-id="5997c-102">Segments répétitifs</span><span class="sxs-lookup"><span data-stu-id="5997c-102">Repeatable Field Segments</span></span>
<span data-ttu-id="5997c-103">La table des Segments dans la base de données HL7 Access contient une colonne pour le dernier champ de segments (ADD, r & DT et QPD) qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) définit comme repeatable (**Last_field_repeatable**  =  **True**).</span><span class="sxs-lookup"><span data-stu-id="5997c-103">The Segments table in the HL7 Access database contains a column for the last field of segments (ADD, RDT, and QPD) that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) defines as repeatable (**Last_field_repeatable** = **True**).</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="5997c-104">ne prend pas en charge les ajouter.</span><span class="sxs-lookup"><span data-stu-id="5997c-104"> does not support ADD.</span></span> <span data-ttu-id="5997c-105">Toutefois, r & DT et QPD sont présents pour interroger des tables et répondent avec des valeurs de la table.</span><span class="sxs-lookup"><span data-stu-id="5997c-105">However, both RDT and QPD are present to query tables and respond with table values.</span></span> <span data-ttu-id="5997c-106">L’exemple suivant montre comment [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] gère ces colonnes.</span><span class="sxs-lookup"><span data-stu-id="5997c-106">The following sample demonstrates how [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] handles these columns.</span></span>  
  
 <span data-ttu-id="5997c-107">Un client soumet la requête suivante et indique que le client souhaite obtenir une réponse immédiate en définissant **en priorité RCP-1-réponse** à «**I**» :</span><span class="sxs-lookup"><span data-stu-id="5997c-107">A client submits the following query and indicates that the client wants an immediate response by setting **RCP-1-Response priority** to "**I**":</span></span>  
  
```  
MSH|^&~\|PCR|Gen Hosp|PIMS||199811201400-0800||QBP^Q42^QBP_Q13|ACK9901|P|2.4||||||||  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR| |19980531|19990531|  
RCP|I|999^RD|  
RDF|3|PatientList^ST^20~PatientName^XPN^48~MedicationDispensed^ST^40~RXD.3^TS^26  
```  
  
 <span data-ttu-id="5997c-108">Le serveur répond à une minute plus tard avec le message suivant :</span><span class="sxs-lookup"><span data-stu-id="5997c-108">The server responds one minute later with the following message:</span></span>  
  
```  
MSH|^&~\|PIMS|Gen Hosp|PCR||199811201401-0800||RTB^K42^RTB_K13|8858|P|2.3||||||||  
MSA|AA|8699|  
QAK|Q010|OK|Q42^Tabular Dispense History^HL7nnn|4  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR||19980531|19990531|  
RDF|7|PatientId^CX^20~PatientName^XPN^48~OrderControlCode^ID^2~ MedicationDispensed^CE^100~DispenseDate^TS^26~QuantityDispensed^NM^20~ OrderingProvider^XCN^120  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|525440345^Verapamil Hydrochloride 120 mg TAB^NDC |199805291115-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00182196901^VERAPAMIL HCL ER TAB 180MG ER^NDC |19980821-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00172409660^BACLOFEN 10MG TABS^NDC |199809221415-0700|10|88^Semmelweis^Samuel^^^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00054384163^THEOPHYLLINE 80MG/15ML SOLN^NDC|199810121145-0700|10|99^Lister^Lenora^^^DR^MD  
```  
  
 <span data-ttu-id="5997c-109">À partir de l’exemple, vous voyez que QPD et r & DT sont personnalisé/site défini.</span><span class="sxs-lookup"><span data-stu-id="5997c-109">From the example, you see that QPD and RDT are custom/site defined.</span></span> <span data-ttu-id="5997c-110">La spécification HL7 définit les segments QPD et r & DT comme suit.</span><span class="sxs-lookup"><span data-stu-id="5997c-110">The HL7 specification defines QPD and RDT segments as follows.</span></span>  
  
## <a name="qpd---query-parameter-definition"></a><span data-ttu-id="5997c-111">QPD - définition de paramètre de requête</span><span class="sxs-lookup"><span data-stu-id="5997c-111">QPD - Query Parameter Definition</span></span>  
 <span data-ttu-id="5997c-112">Le tableau suivant montre comment la spécification de HL7 définit QPD.</span><span class="sxs-lookup"><span data-stu-id="5997c-112">The following table shows how the HL7 specification defines QPD.</span></span>  
  
|<span data-ttu-id="5997c-113">SEQ</span><span class="sxs-lookup"><span data-stu-id="5997c-113">SEQ</span></span>|<span data-ttu-id="5997c-114">LEN</span><span class="sxs-lookup"><span data-stu-id="5997c-114">LEN</span></span>|<span data-ttu-id="5997c-115">TYPE DE DONNÉES</span><span class="sxs-lookup"><span data-stu-id="5997c-115">DT</span></span>|<span data-ttu-id="5997c-116">S’ABONNER</span><span class="sxs-lookup"><span data-stu-id="5997c-116">OPT</span></span>|<span data-ttu-id="5997c-117">RP / #</span><span class="sxs-lookup"><span data-stu-id="5997c-117">RP/#</span></span>|<span data-ttu-id="5997c-118">TBL #</span><span class="sxs-lookup"><span data-stu-id="5997c-118">TBL#</span></span>|<span data-ttu-id="5997c-119">ÉLÉMENT #</span><span class="sxs-lookup"><span data-stu-id="5997c-119">ITEM#</span></span>|<span data-ttu-id="5997c-120">NOM DE L’ÉLÉMENT</span><span class="sxs-lookup"><span data-stu-id="5997c-120">ELEMENT NAME</span></span>|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|<span data-ttu-id="5997c-121">1</span><span class="sxs-lookup"><span data-stu-id="5997c-121">1</span></span>|<span data-ttu-id="5997c-122">250</span><span class="sxs-lookup"><span data-stu-id="5997c-122">250</span></span>|<span data-ttu-id="5997c-123">CE</span><span class="sxs-lookup"><span data-stu-id="5997c-123">CE</span></span>|<span data-ttu-id="5997c-124">R</span><span class="sxs-lookup"><span data-stu-id="5997c-124">R</span></span>||<span data-ttu-id="5997c-125">0471</span><span class="sxs-lookup"><span data-stu-id="5997c-125">0471</span></span>|<span data-ttu-id="5997c-126">01375</span><span class="sxs-lookup"><span data-stu-id="5997c-126">01375</span></span>|<span data-ttu-id="5997c-127">Nom de requête de message</span><span class="sxs-lookup"><span data-stu-id="5997c-127">Message Query Name</span></span>|  
|<span data-ttu-id="5997c-128">2</span><span class="sxs-lookup"><span data-stu-id="5997c-128">2</span></span>|<span data-ttu-id="5997c-129">32</span><span class="sxs-lookup"><span data-stu-id="5997c-129">32</span></span>|<span data-ttu-id="5997c-130">ST</span><span class="sxs-lookup"><span data-stu-id="5997c-130">ST</span></span>|<span data-ttu-id="5997c-131">C</span><span class="sxs-lookup"><span data-stu-id="5997c-131">C</span></span>|||<span data-ttu-id="5997c-132">00696</span><span class="sxs-lookup"><span data-stu-id="5997c-132">00696</span></span>|<span data-ttu-id="5997c-133">Balise de requête</span><span class="sxs-lookup"><span data-stu-id="5997c-133">Query Tag</span></span>|  
|<span data-ttu-id="5997c-134">3-n</span><span class="sxs-lookup"><span data-stu-id="5997c-134">3-n</span></span>|<span data-ttu-id="5997c-135">256</span><span class="sxs-lookup"><span data-stu-id="5997c-135">256</span></span>|<span data-ttu-id="5997c-136">Varie</span><span class="sxs-lookup"><span data-stu-id="5997c-136">Varies</span></span>||||<span data-ttu-id="5997c-137">01435</span><span class="sxs-lookup"><span data-stu-id="5997c-137">01435</span></span>|<span data-ttu-id="5997c-138">Champs successives des paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="5997c-138">User parameters in successive fields</span></span>|  
  
## <a name="rdt---table-row-data"></a><span data-ttu-id="5997c-139">R & DT - données de ligne de Table</span><span class="sxs-lookup"><span data-stu-id="5997c-139">RDT - Table Row Data</span></span>  
 <span data-ttu-id="5997c-140">Le tableau suivant montre comment la spécification de HL7 définit r & DT.</span><span class="sxs-lookup"><span data-stu-id="5997c-140">The following table shows how the HL7 specification defines RDT.</span></span>  
  
|<span data-ttu-id="5997c-141">SEQ</span><span class="sxs-lookup"><span data-stu-id="5997c-141">SEQ</span></span>|<span data-ttu-id="5997c-142">LEN</span><span class="sxs-lookup"><span data-stu-id="5997c-142">LEN</span></span>|<span data-ttu-id="5997c-143">TYPE DE DONNÉES</span><span class="sxs-lookup"><span data-stu-id="5997c-143">DT</span></span>|<span data-ttu-id="5997c-144">S’ABONNER</span><span class="sxs-lookup"><span data-stu-id="5997c-144">OPT</span></span>|<span data-ttu-id="5997c-145">RP / #</span><span class="sxs-lookup"><span data-stu-id="5997c-145">RP/#</span></span>|<span data-ttu-id="5997c-146">TBL #</span><span class="sxs-lookup"><span data-stu-id="5997c-146">TBL#</span></span>|<span data-ttu-id="5997c-147">ÉLÉMENT #</span><span class="sxs-lookup"><span data-stu-id="5997c-147">ITEM#</span></span>|<span data-ttu-id="5997c-148">NOM DE L’ÉLÉMENT</span><span class="sxs-lookup"><span data-stu-id="5997c-148">ELEMENT NAME</span></span>|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|<span data-ttu-id="5997c-149">1-n</span><span class="sxs-lookup"><span data-stu-id="5997c-149">1-n</span></span>|<span data-ttu-id="5997c-150">Variable</span><span class="sxs-lookup"><span data-stu-id="5997c-150">Variable</span></span>|<span data-ttu-id="5997c-151">Variable</span><span class="sxs-lookup"><span data-stu-id="5997c-151">Variable</span></span>|<span data-ttu-id="5997c-152">R</span><span class="sxs-lookup"><span data-stu-id="5997c-152">R</span></span>|||<span data-ttu-id="5997c-153">00703</span><span class="sxs-lookup"><span data-stu-id="5997c-153">00703</span></span>|<span data-ttu-id="5997c-154">Valeur de colonne</span><span class="sxs-lookup"><span data-stu-id="5997c-154">Column Value</span></span>|  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="5997c-155">interprète QPD et r & DT sous forme de valeurs définie sur le site qui peuvent se répéter.</span><span class="sxs-lookup"><span data-stu-id="5997c-155"> interprets QPD and RDT as site-defined values that can repeat.</span></span> <span data-ttu-id="5997c-156">Étant donné que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne résout pas les types de données et d’autres détails, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] traite QPD.3 et RDT.1 en tant que types de données de chaîne dans les schémas.</span><span class="sxs-lookup"><span data-stu-id="5997c-156">Since [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not fix the data types and other details, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats QPD.3 and RDT.1 as String data types in the schemas.</span></span> <span data-ttu-id="5997c-157">Vous devrez peut-être modifier ces schémas en fonction de vos propres conditions de site.</span><span class="sxs-lookup"><span data-stu-id="5997c-157">You may have to modify these schemas depending on your own site conditions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5997c-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5997c-158">See Also</span></span>  
 [<span data-ttu-id="5997c-159">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="5997c-159">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)