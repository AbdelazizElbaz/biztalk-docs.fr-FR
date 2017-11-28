---
title: "Étape 6 (sur site) : Créer une transformation pour mapper le Message à partir de la file d’attente vers le schéma Insert | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30a55f1e-32cc-409a-a814-084026f51b35
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02b2be9659714beb4b9a52f4c2a9dd1e5b3ea47f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-on-premises-create-a-transform-to-map-the-message-from-the-queue-to-the-insert-schema"></a><span data-ttu-id="0b1b7-102">Étape 6 (sur site) : Créer une transformation pour mapper le Message à partir de la file d’attente vers le schéma Insert</span><span class="sxs-lookup"><span data-stu-id="0b1b7-102">Step 6 (On Premises): Create a Transform to Map the Message from the Queue to the Insert Schema</span></span>
<span data-ttu-id="0b1b7-103">Le message est reçu par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir de la file d’attente du Bus de Service sera le **ECommerceSalesOrder.xsd** schéma.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-103">The message that is received by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from the Service Bus Queue will be of the **ECommerceSalesOrder.xsd** schema.</span></span> <span data-ttu-id="0b1b7-104">Toutefois, pour insérer un message dans le **SalesOrder** table, le message doit être de **insérer** schéma que vous avez généré dans [étape 5 (locaux) : générer le schéma d’insertion d’un Message dans la Table SalesOrder](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md).</span><span class="sxs-lookup"><span data-stu-id="0b1b7-104">However, to insert a message into the **SalesOrder** table, the message must be of **Insert** schema that you generated in [Step 5 (On Premises): Generate the Schema for Inserting a Message inito SalesOrder Table](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md).</span></span> <span data-ttu-id="0b1b7-105">Par conséquent, dans cette rubrique, nous créons un mappage pour transformer le **ECommerceSalesOrder.xsd** schéma dans le schéma d’opération Insert.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-105">So, in this topic, we create a map to transform the **ECommerceSalesOrder.xsd** schema into the Insert operation schema.</span></span>  
  
### <a name="to-create-a-map"></a><span data-ttu-id="0b1b7-106">Pour créer un mappage</span><span class="sxs-lookup"><span data-stu-id="0b1b7-106">To create a map</span></span>  
  
1.  <span data-ttu-id="0b1b7-107">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous avez déjà créé, cliquez sur le projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you already created, right-click the project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="0b1b7-108">Dans le **un nouvel élément** boîte de dialogue, sélectionnez **carte**, entrez le nom de mappage `SalesOrder_SQL.btm`, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-108">In the **New Item** dialog box, select **Map**, enter the map name as `SalesOrder_SQL.btm`, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="0b1b7-109">Dans le mappage, pour le schéma source, sélectionnez **ECommerceSalesOrder.xsd**.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-109">In the map, for the source schema, select **ECommerceSalesOrder.xsd**.</span></span> <span data-ttu-id="0b1b7-110">Pour le schéma de destination, sélectionnez **TableOperations.SalesOrder.xsd (Insert)** schéma.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-110">For the destination schema, select **TableOperations.SalesOrder.xsd (Insert)** schema.</span></span>  
  
3.  <span data-ttu-id="0b1b7-111">Mappez directement les nœuds suivants dans les schémas source et de destination :</span><span class="sxs-lookup"><span data-stu-id="0b1b7-111">Directly map the following nodes in the source and destination schemas:</span></span>  
  
    |<span data-ttu-id="0b1b7-112">Schéma source</span><span class="sxs-lookup"><span data-stu-id="0b1b7-112">Source Schema</span></span>|<span data-ttu-id="0b1b7-113">Schéma de destination</span><span class="sxs-lookup"><span data-stu-id="0b1b7-113">Destination Schema</span></span>|  
    |-------------------|------------------------|  
    |<span data-ttu-id="0b1b7-114">CompanyCode</span><span class="sxs-lookup"><span data-stu-id="0b1b7-114">CompanyCode</span></span>|<span data-ttu-id="0b1b7-115">CompanyCode</span><span class="sxs-lookup"><span data-stu-id="0b1b7-115">CompanyCode</span></span>|  
    |<span data-ttu-id="0b1b7-116">PartId</span><span class="sxs-lookup"><span data-stu-id="0b1b7-116">PartId</span></span>|<span data-ttu-id="0b1b7-117">PartNum</span><span class="sxs-lookup"><span data-stu-id="0b1b7-117">PartNum</span></span>|  
    |<span data-ttu-id="0b1b7-118">Quantité</span><span class="sxs-lookup"><span data-stu-id="0b1b7-118">Quantity</span></span>|<span data-ttu-id="0b1b7-119">Qty</span><span class="sxs-lookup"><span data-stu-id="0b1b7-119">Qty</span></span>|  
    |<span data-ttu-id="0b1b7-120">AskPrice</span><span class="sxs-lookup"><span data-stu-id="0b1b7-120">AskPrice</span></span>|<span data-ttu-id="0b1b7-121">UnitAskPrice</span><span class="sxs-lookup"><span data-stu-id="0b1b7-121">UnitAskPrice</span></span>|  
    |<span data-ttu-id="0b1b7-122">Commentaires</span><span class="sxs-lookup"><span data-stu-id="0b1b7-122">Comments</span></span>|<span data-ttu-id="0b1b7-123">CustomerComments</span><span class="sxs-lookup"><span data-stu-id="0b1b7-123">CustomerComments</span></span>|  
  
4.  <span data-ttu-id="0b1b7-124">Utilisez le **Date et heure** fonctoid pour mapper les valeurs pour le **DateRequested** et **ShipDate** éléments du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-124">Use the **Date and Time** functoid to map values to the **DateRequested** and **ShipDate** elements in the destination schema.</span></span> <span data-ttu-id="0b1b7-125">Ces nœuds ne sont pas mappés sur les nœuds respectifs du schéma source.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-125">These nodes are not mapped to the respective nodes in the source schema.</span></span> <span data-ttu-id="0b1b7-126">Au lieu de cela, la date et l’heure est transmise à ces nœuds à l’aide du **Date et heure** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-126">Instead, the current date and time is passed on to these nodes by using the **Date and Time** functoid.</span></span>  
  
    1.  <span data-ttu-id="0b1b7-127">Faites glisser et déposez un **Date et heure** fonctoid à partir de la boîte à outils vers la surface du mappeur.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-127">Drag and drop a **Date and Time** functoid from toolbox to the mapper surface.</span></span>  
  
    2.  <span data-ttu-id="0b1b7-128">Connectez le fonctoid à la **DateRequested** élément dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-128">Connect the functoid to the **DateRequested** element in the destination schema.</span></span>  
  
    3.  <span data-ttu-id="0b1b7-129">Faites glisser une autre **Date et heure** fonctoid et connectez-la à la **ShipDate** élément dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-129">Drag and drop another **Date and Time** functoid and connect it to the **ShipDate** element in the destination schema.</span></span>  
  
5.  <span data-ttu-id="0b1b7-130">Mappez les nœuds suivants dans les schémas source et de destination à l’aide un **concaténation de chaînes** fonctoid :</span><span class="sxs-lookup"><span data-stu-id="0b1b7-130">Map the following nodes in the source and destination schemas using a **String Concatenate** functoid:</span></span>  
  
    |<span data-ttu-id="0b1b7-131">Schéma source</span><span class="sxs-lookup"><span data-stu-id="0b1b7-131">Source Schema</span></span>|<span data-ttu-id="0b1b7-132">Schéma de destination</span><span class="sxs-lookup"><span data-stu-id="0b1b7-132">Destination Schema</span></span>|  
    |-------------------|------------------------|  
    |<span data-ttu-id="0b1b7-133">Adresse\Ligne1</span><span class="sxs-lookup"><span data-stu-id="0b1b7-133">Address\Line1</span></span>|<span data-ttu-id="0b1b7-134">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-134">SellToAddress</span></span><br /><br /> <span data-ttu-id="0b1b7-135">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-135">BillToAddress</span></span>|  
    |<span data-ttu-id="0b1b7-136">Adresse\Ligne2</span><span class="sxs-lookup"><span data-stu-id="0b1b7-136">Address\Line2</span></span>|<span data-ttu-id="0b1b7-137">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-137">SellToAddress</span></span><br /><br /> <span data-ttu-id="0b1b7-138">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-138">BillToAddress</span></span>|  
    |<span data-ttu-id="0b1b7-139">Adresse\Ville</span><span class="sxs-lookup"><span data-stu-id="0b1b7-139">Address\City</span></span>|<span data-ttu-id="0b1b7-140">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-140">SellToAddress</span></span><br /><br /> <span data-ttu-id="0b1b7-141">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-141">BillToAddress</span></span>|  
    |<span data-ttu-id="0b1b7-142">Adresse\Département</span><span class="sxs-lookup"><span data-stu-id="0b1b7-142">Address\State</span></span>|<span data-ttu-id="0b1b7-143">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-143">SellToAddress</span></span><br /><br /> <span data-ttu-id="0b1b7-144">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-144">BillToAddress</span></span>|  
    |<span data-ttu-id="0b1b7-145">Adresse\Pays</span><span class="sxs-lookup"><span data-stu-id="0b1b7-145">Address\Country</span></span>|<span data-ttu-id="0b1b7-146">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-146">SellToAddress</span></span><br /><br /> <span data-ttu-id="0b1b7-147">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-147">BillToAddress</span></span>|  
    |<span data-ttu-id="0b1b7-148">Adresse\CodePostal</span><span class="sxs-lookup"><span data-stu-id="0b1b7-148">Address\ZipCode</span></span>|<span data-ttu-id="0b1b7-149">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-149">SellToAddress</span></span><br /><br /> <span data-ttu-id="0b1b7-150">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="0b1b7-150">BillToAddress</span></span>|  
    |<span data-ttu-id="0b1b7-151">Contact\Prénom</span><span class="sxs-lookup"><span data-stu-id="0b1b7-151">Contact\FirstName</span></span>|<span data-ttu-id="0b1b7-152">PartnerContact</span><span class="sxs-lookup"><span data-stu-id="0b1b7-152">PartnerContact</span></span>|  
    |<span data-ttu-id="0b1b7-153">Contact\NomFamille</span><span class="sxs-lookup"><span data-stu-id="0b1b7-153">Contact\LastName</span></span>||  
  
     <span data-ttu-id="0b1b7-154">Effectuez les étapes suivantes pour chaque ensemble de mappage de concaténation de chaîne :</span><span class="sxs-lookup"><span data-stu-id="0b1b7-154">Perform the following steps for each of the string concatenation mapping sets:</span></span>  
  
    1.  <span data-ttu-id="0b1b7-155">Faites glisser et déposez un **concaténation de chaînes** fonctoid à partir de la boîte à outils vers la surface du mappeur.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-155">Drag and drop a **String Concatenate** functoid from toolbox to the mapper surface.</span></span>  
  
    2.  <span data-ttu-id="0b1b7-156">Ajoutez chaque élément de l’arborescence source en tant qu’entrée à la **concaténation de chaînes** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-156">Add each element from the source tree as an input to the **String Concatenate** functoid.</span></span>  
  
    3.  <span data-ttu-id="0b1b7-157">Faites glisser et configurez la sortie de la **concaténation de chaînes** fonctoid à l’élément dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="0b1b7-157">Drag and configure the output of the **String Concatenate** functoid to the element in the destination schema.</span></span>  
  
         <span data-ttu-id="0b1b7-158">Le mappage terminé ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="0b1b7-158">The completed map resembles the following:</span></span>  
  
         <span data-ttu-id="0b1b7-159">![Mappage pour transformer des schémas](../core/media/bts2010r2-tut1-map.jpg "BTS2010R2_Tut1_Map")</span><span class="sxs-lookup"><span data-stu-id="0b1b7-159">![Map to transform schemas](../core/media/bts2010r2-tut1-map.jpg "BTS2010R2_Tut1_Map")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1b7-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b1b7-160">See Also</span></span>  
 [<span data-ttu-id="0b1b7-161">Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="0b1b7-161">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)