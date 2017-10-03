---
title: "Annotations des champs déclencheurs HIPAA schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1389284-a2ec-44e7-a2f1-8d26f83fd31d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d3bf6d53ec95ebfc57cff646ce5658fc6b1f4a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hipaa-schema-trigger-field-annotations"></a><span data-ttu-id="879ea-102">Annotations des champs déclencheurs de schéma HIPAA</span><span class="sxs-lookup"><span data-stu-id="879ea-102">HIPAA Schema Trigger Field Annotations</span></span>
<span data-ttu-id="879ea-103">Les segments EDI contiennent souvent des valeurs du qualificateur qui modifient la signification d'un segment.</span><span class="sxs-lookup"><span data-stu-id="879ea-103">EDI segments often contain qualifier values that modify the meaning of the segment.</span></span> <span data-ttu-id="879ea-104">Par exemple, un segment N1 peut contenir un élément de qualification « BT » signifiant « Nom de facturation (bill-to) » ou « ST » pour « Nom de livraison (ship-to) ».</span><span class="sxs-lookup"><span data-stu-id="879ea-104">For example, an N1 segment can contain a qualifying element of “BT” to signify a “bill-to name,” or it may contain a qualifying element of “ST” to indicate a “ship-to name.”</span></span> <span data-ttu-id="879ea-105">Généralement, l'interprétation de ces champs est dictée par la logique d'entreprise et le Désassembleur fait correspondre toutes les instances du segment N1 avec le même enregistrement XML ; toutefois, les schémas HIPAA inclus dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] contiennent des annotations permettant au Désassembleur EDI de créer des enregistrements XML uniques sur la base de la présence d'un élément de qualification.</span><span class="sxs-lookup"><span data-stu-id="879ea-105">Normally it is left to business logic to determine how to interpret these fields and the disassembler resolves all instances of the N1 segment to the same XML record name; however, the HIPAA schemas shipped with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] contain annotations that allow the EDI disassembler to create unique XML records based on the presence of a qualifying element.</span></span>  
  
 <span data-ttu-id="879ea-106">**Implémentation du champ déclencheur**</span><span class="sxs-lookup"><span data-stu-id="879ea-106">**Trigger Field Implementation**</span></span>  
  
 <span data-ttu-id="879ea-107">Les champs déclencheurs sont implémentés en tant que paire d'attributs XML décrivant l'élément de segment et la valeur de déclenchement qui provoque la création de cet enregistrement.</span><span class="sxs-lookup"><span data-stu-id="879ea-107">Trigger fields are implemented as a pair of XML attributes that describe the segment element and the trigger value that causes this record to be created.</span></span> <span data-ttu-id="879ea-108">Le tableau suivant présente ces attributs :</span><span class="sxs-lookup"><span data-stu-id="879ea-108">The following table describes these attributes:</span></span>  
  
|<span data-ttu-id="879ea-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="879ea-109">Attribute</span></span>|<span data-ttu-id="879ea-110">Fonction</span><span class="sxs-lookup"><span data-stu-id="879ea-110">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="879ea-111">trigger_field</span><span class="sxs-lookup"><span data-stu-id="879ea-111">trigger_field</span></span>|<span data-ttu-id="879ea-112">Champ du segment dans lequel la valeur de déclenchement est recherchée.</span><span class="sxs-lookup"><span data-stu-id="879ea-112">The segment field that will be inspected for the trigger value.</span></span>|  
|<span data-ttu-id="879ea-113">trigger_value</span><span class="sxs-lookup"><span data-stu-id="879ea-113">trigger_value</span></span>|<span data-ttu-id="879ea-114">La ou les valeurs de déclenchement.</span><span class="sxs-lookup"><span data-stu-id="879ea-114">The trigger value(s).</span></span><br /><br /> <span data-ttu-id="879ea-115">Ce champ peut contenir une seule valeur ou une liste de valeurs délimitées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="879ea-115">This may contain a single value, or a space delimited list of values.</span></span>|  
  
 <span data-ttu-id="879ea-116">Le tableau suivant illustre l'annotation de déclenchement telle qu'affichée dans le schéma HIPAA, le segment EDI provoquant l'activation du déclencheur ainsi que les données XML résultant du traitement du segment.</span><span class="sxs-lookup"><span data-stu-id="879ea-116">The following table shows the trigger annotation as it would appear in the HIPAA schema, the EDI segment that will cause the trigger to activate, and the resulting XML data after processing the segment.</span></span>  
  
|<span data-ttu-id="879ea-117">Annotation de déclenchement du schéma</span><span class="sxs-lookup"><span data-stu-id="879ea-117">Schema Trigger Annotation</span></span>|<span data-ttu-id="879ea-118">Segment N1 correspondant</span><span class="sxs-lookup"><span data-stu-id="879ea-118">Matching N1 Segment</span></span>|<span data-ttu-id="879ea-119">Données XML résultantes</span><span class="sxs-lookup"><span data-stu-id="879ea-119">Resulting XML Data</span></span>|  
|-------------------------------|-------------------------|------------------------|  
|`<xs:element name="TS835W1_1000A_Loop">  <xs:annotation>   <xs:appinfo>    <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayerIdentification_TS835W1_1000A/N101__EntityIdentifierCode"     trigger_value="PR" notes="Payer Identification" />    </xs:appinfo>  </xs:annotation>`|<span data-ttu-id="879ea-120">N1 * PR\*Contoso\*XV\*0000000 ~</span><span class="sxs-lookup"><span data-stu-id="879ea-120">N1*PR\*Contoso\*XV\*0000000~</span></span>|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|`<xs:element name="TS835W1_1000B_Loop">   <xs:annotation>    <xs:appinfo>     <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayeeIdentification_TS835W1_1000B/N101__EntityIdentifierCode"     trigger_value="PE" notes="Payee Identification" />    </xs:appinfo>   </xs:annotation>`|<span data-ttu-id="879ea-121">N1 * PE\*Fabrikam\*FI\*9999999 ~</span><span class="sxs-lookup"><span data-stu-id="879ea-121">N1*PE\*Fabrikam\*FI\*9999999~</span></span>|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
 <span data-ttu-id="879ea-122">**Traitement du désassembleur EDI des champs déclencheurs**</span><span class="sxs-lookup"><span data-stu-id="879ea-122">**EDI Disassembler Processing of Trigger Fields**</span></span>  
  
 <span data-ttu-id="879ea-123">Lors de la réception d’une transaction HIPAA définie, si le désassembleur EDI rencontre un segment qui contient un champ déclencheur, il utilise les informations de déclencheur pour générer un enregistrement XML spécifique à la combinaison segment / déclencheur.</span><span class="sxs-lookup"><span data-stu-id="879ea-123">When receiving a HIPAA transaction set, if the EDI disassembler encounters a segment that contains a trigger field, it uses the trigger information to generate an XML record specific to the segment and trigger combination.</span></span> <span data-ttu-id="879ea-124">Par exemple, dans les données EDI suivantes, deux segments N1 possèdent des valeurs distinctes pour N101, PR et PE.</span><span class="sxs-lookup"><span data-stu-id="879ea-124">For example, in the following EDI data, there are two N1 segments that have different values for N101, PR and PE:</span></span>  
  
```  
  
N1*PR*Contoso*XV*0000000~  
N3*N301__PayerAddressLine~  
N4*N401__PayerCityName*N4*N403__PayerPost**N4*N406~  
……  
N1*PE*Fabrikam*FI*9999999~  
N3*N301__PayeeAddressLine~  
N4*N401__PayeeCityName*N4*N403__PayeePost**N4*N406~  
  
```  
  
 <span data-ttu-id="879ea-125">Lors du traitement par le désassembleur EDI, les annotations du champ déclencheur présentes dans le schéma entraîne deux enregistrements XML distincts en fonction de la valeur de N101, < N1_PayerIdentification_TS835W1_1000A > et < N1_PayeeIdentification_TS835W1_1000B >, correspondant à N1 * PR et N1\*PE.</span><span class="sxs-lookup"><span data-stu-id="879ea-125">When processed by the EDI disassembler, the trigger field annotations present in the schema will result in two separate XML records based on the value of N101, <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B>, corresponding to N1*PR and N1\*PE.</span></span>  
  
 <span data-ttu-id="879ea-126">Lors de l'envoi, le Désassembleur EDI abandonne le suffixe situé après le caractère « _ » pour les champs contenant une annotation de déclenchement.</span><span class="sxs-lookup"><span data-stu-id="879ea-126">When sending, the EDI assembler will drop the suffix following the “_” character for fields that contain a trigger annotation.</span></span> <span data-ttu-id="879ea-127">Par exemple, <N1_PayerIdentification_TS835W1_1000A> et <N1_PayeeIdentification_TS835W1_1000B> sont transformés tous les deux en N1.</span><span class="sxs-lookup"><span data-stu-id="879ea-127">For example, both <N1_PayerIdentification_TS835W1_1000A> and <N1_PayeeIdentification_TS835W1_1000B> will both become N1.</span></span>  
  
 <span data-ttu-id="879ea-128">**Champs déclencheurs et Segments par défaut**</span><span class="sxs-lookup"><span data-stu-id="879ea-128">**Default Segments and Trigger Fields**</span></span>  
  
 <span data-ttu-id="879ea-129">Le tableau suivant contient des informations sur les segments et les champs déclencheurs par défaut utilisés dans les documents HIPAA inclus dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="879ea-129">The following table contains information on the default segments and trigger fields used in HIPAA documents supplied as part of [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="879ea-130">Les valeurs de déclencheur individuelles utilisées avec les champs déclencheurs peuvent varier selon les schémas.</span><span class="sxs-lookup"><span data-stu-id="879ea-130">The individual trigger values used with the trigger fields may vary between schemas.</span></span>  
  
|<span data-ttu-id="879ea-131">Segment avec déclencheur</span><span class="sxs-lookup"><span data-stu-id="879ea-131">Segment with Trigger</span></span>|<span data-ttu-id="879ea-132">Champ déclencheur</span><span class="sxs-lookup"><span data-stu-id="879ea-132">Trigger field</span></span>|  
|--------------------------|-------------------|  
|<span data-ttu-id="879ea-133">AMT</span><span class="sxs-lookup"><span data-stu-id="879ea-133">AMT</span></span>|<span data-ttu-id="879ea-134">AMT01</span><span class="sxs-lookup"><span data-stu-id="879ea-134">AMT01</span></span>|  
|<span data-ttu-id="879ea-135">CRC</span><span class="sxs-lookup"><span data-stu-id="879ea-135">CRC</span></span>|<span data-ttu-id="879ea-136">CRC01</span><span class="sxs-lookup"><span data-stu-id="879ea-136">CRC01</span></span>|  
|<span data-ttu-id="879ea-137">DTM</span><span class="sxs-lookup"><span data-stu-id="879ea-137">DTM</span></span>|<span data-ttu-id="879ea-138">DTM01</span><span class="sxs-lookup"><span data-stu-id="879ea-138">DTM01</span></span>|  
|<span data-ttu-id="879ea-139">DTP</span><span class="sxs-lookup"><span data-stu-id="879ea-139">DTP</span></span>|<span data-ttu-id="879ea-140">DTP01</span><span class="sxs-lookup"><span data-stu-id="879ea-140">DTP01</span></span>|  
|<span data-ttu-id="879ea-141">ENT</span><span class="sxs-lookup"><span data-stu-id="879ea-141">ENT</span></span>|<span data-ttu-id="879ea-142">ENT02</span><span class="sxs-lookup"><span data-stu-id="879ea-142">ENT02</span></span>|  
|<span data-ttu-id="879ea-143">HI</span><span class="sxs-lookup"><span data-stu-id="879ea-143">HI</span></span>|<span data-ttu-id="879ea-144">HI01:01</span><span class="sxs-lookup"><span data-stu-id="879ea-144">HI01:01</span></span>|  
|<span data-ttu-id="879ea-145">N1</span><span class="sxs-lookup"><span data-stu-id="879ea-145">N1</span></span>|<span data-ttu-id="879ea-146">N101</span><span class="sxs-lookup"><span data-stu-id="879ea-146">N101</span></span>|  
|<span data-ttu-id="879ea-147">NM1</span><span class="sxs-lookup"><span data-stu-id="879ea-147">NM1</span></span>|<span data-ttu-id="879ea-148">NM01</span><span class="sxs-lookup"><span data-stu-id="879ea-148">NM01</span></span>|  
|<span data-ttu-id="879ea-149">NTE</span><span class="sxs-lookup"><span data-stu-id="879ea-149">NTE</span></span>|<span data-ttu-id="879ea-150">NTE01</span><span class="sxs-lookup"><span data-stu-id="879ea-150">NTE01</span></span>|  
|<span data-ttu-id="879ea-151">REF</span><span class="sxs-lookup"><span data-stu-id="879ea-151">REF</span></span>|<span data-ttu-id="879ea-152">REF01</span><span class="sxs-lookup"><span data-stu-id="879ea-152">REF01</span></span>|  
|<span data-ttu-id="879ea-153">RMR</span><span class="sxs-lookup"><span data-stu-id="879ea-153">RMR</span></span>|<span data-ttu-id="879ea-154">RMR01</span><span class="sxs-lookup"><span data-stu-id="879ea-154">RMR01</span></span>|