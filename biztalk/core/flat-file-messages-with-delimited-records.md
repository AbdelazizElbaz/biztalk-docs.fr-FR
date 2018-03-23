---
title: Messages de fichier plat avec des enregistrements délimités | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ad7119b-4e39-43df-9dba-a04382eb6db2
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5dc9eb0253e2bfe8824f6395e1c619c23f0e551
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="flat-file-messages-with-delimited-records"></a><span data-ttu-id="b1c41-102">Messages de fichier plat avec des enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="b1c41-102">Flat File Messages with Delimited Records</span></span>
<span data-ttu-id="b1c41-103">Les enregistrements délimités d'un message d'instance de fichier plat contiennent des enregistrements imbriqués et/ou des champs individuels (éléments de données) séparés par un caractère ou un ensemble de caractères prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="b1c41-103">Delimited records within a flat file instance message contain nested records and/or individual fields (items of data) that are separated by a predefined character or set of characters.</span></span> <span data-ttu-id="b1c41-104">Les champs sont analysés selon ces délimiteurs de séparation.</span><span class="sxs-lookup"><span data-stu-id="b1c41-104">The fields are parsed according to these separating delimiters.</span></span> <span data-ttu-id="b1c41-105">Prenons l'exemple des enregistrements délimités suivants issus d'un message d'instance de fichier plat et contenant deux lignes d'un bon de commande hypothétique :</span><span class="sxs-lookup"><span data-stu-id="b1c41-105">For example, consider the following delimited records from a flat file instance message, which contain two line items from a hypothetical purchase order:</span></span>  
  
```  
  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Electric-120vac,ITEM926-AA|Baby Monitor|1|39.98|Electric-4AA|2004-01-21  
  
```  
  
 <span data-ttu-id="b1c41-106">Une définition raisonnable de cet enregistrement dans un schéma de fichier flat peut être celle-ci :</span><span class="sxs-lookup"><span data-stu-id="b1c41-106">A reasonable definition for this record in a flat file schema can be described as follows:</span></span>  
  
-   <span data-ttu-id="b1c41-107">Des éléments nommés d'un enregistrement délimité avec un délimiteur enfant (,), un préfixe de classement enfant et la balise ITEMS (en gras)</span><span class="sxs-lookup"><span data-stu-id="b1c41-107">A delimited record named items with child delimiter (,), child order prefix, and the tag ITEMS.</span></span>  
  
    -   <span data-ttu-id="b1c41-108">Élément avec un délimiteur enfant nommé d’enregistrement répété A délimités, &#124;, valeur infix de classement enfant et la balise d’élément.</span><span class="sxs-lookup"><span data-stu-id="b1c41-108">A delimited, repeating record named item with child delimiter &#124;, child order infix, and the tag ITEM.</span></span>  
  
    -   <span data-ttu-id="b1c41-109">Un élément « partNum ».</span><span class="sxs-lookup"><span data-stu-id="b1c41-109">An attribute named "partNum".</span></span>  
  
    -   <span data-ttu-id="b1c41-110">Un élément « productName ».</span><span class="sxs-lookup"><span data-stu-id="b1c41-110">An element named "productName".</span></span>  
  
    -   <span data-ttu-id="b1c41-111">Un élément « quantity ».</span><span class="sxs-lookup"><span data-stu-id="b1c41-111">An element named "quantity".</span></span>  
  
    -   <span data-ttu-id="b1c41-112">Un élément « USPrice ».</span><span class="sxs-lookup"><span data-stu-id="b1c41-112">An element named "USPrice".</span></span>  
  
    -   <span data-ttu-id="b1c41-113">Un élément « powerSource ».</span><span class="sxs-lookup"><span data-stu-id="b1c41-113">An element named "powerSource".</span></span>  
  
-   <span data-ttu-id="b1c41-114">Un élément facultatif « shipDate ».</span><span class="sxs-lookup"><span data-stu-id="b1c41-114">An optional element named "shipDate".</span></span>  
  
 <span data-ttu-id="b1c41-115">Sur la base de ces définitions d'enregistrement et de champ, le désassembleur de fichier plat produit l'équivalent XML de ces enregistrements.</span><span class="sxs-lookup"><span data-stu-id="b1c41-115">Given these record and field definitions, the flat file disassembler produces the following XML equivalent of these records.</span></span>  
  
```  
  
<items>  
    <item partNum="872-AA">  
        <productName>Lawnmower</productName>  
        <quantity>1</quantity>  
        <USPrice>148.95</USPrice>  
        <powerSource>Electric-120vac</powerSource>  
    </item>  
    <item partNum="926-AA">  
        <productName>Baby Monitor</productName>  
        <quantity>1</quantity>  
        <USPrice>39.98</USPrice>  
        <powerSource>Electric-4AA</powerSource>  
        <shipDate>2004-01-21</shipDate>  
    </item>  
</items>  
  
```  
  
 <span data-ttu-id="b1c41-116">Il y a un certain nombre d'aspects relatifs aux enregistrements délimités qui ont une incidence sur la manière dont l'enregistrement est analysé lors de sa réception et construit lors de son envoi. Parmi eux, citons :</span><span class="sxs-lookup"><span data-stu-id="b1c41-116">There are a number of considerations related to delimited records that will affect how the record is parsed when received and constructed when sent, including:</span></span>  
  
-   <span data-ttu-id="b1c41-117">Le ou les caractères utilisés pour substituer l'interprétation des délimiteurs de manière à ce qu'ils soient traités comme faisant partie des données.</span><span class="sxs-lookup"><span data-stu-id="b1c41-117">The character or characters used to override the interpretation of delimiters so that they are treated as part of the data.</span></span> <span data-ttu-id="b1c41-118">Pour plus d’informations, consultez [comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).</span><span class="sxs-lookup"><span data-stu-id="b1c41-118">For more information, see [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).</span></span>  
  
-   <span data-ttu-id="b1c41-119">Une balise optionnelle au début de l'enregistrement, utilisée pour le distinguer d'autres enregistrements similaires.</span><span class="sxs-lookup"><span data-stu-id="b1c41-119">An optional tag at the beginning of the record, used to distinguish the record from other similar records.</span></span> <span data-ttu-id="b1c41-120">Pour plus d’informations, consultez [gestion des balises dans les enregistrements délimités](../core/tag-handling-in-delimited-records.md).</span><span class="sxs-lookup"><span data-stu-id="b1c41-120">For more information, see [Tag Handling in Delimited Records](../core/tag-handling-in-delimited-records.md).</span></span>  
  
-   <span data-ttu-id="b1c41-121">Comment les données sont justifiées dans les champs à longueur minimum, relativement aux caractères de remplissage les accompagnant.</span><span class="sxs-lookup"><span data-stu-id="b1c41-121">How data is justified within fields with minimum lengths, relative to the accompanying pad characters.</span></span> <span data-ttu-id="b1c41-122">Pour plus d’informations, consultez [remplissage des champs](../core/field-padding.md), [Justification des champs](../core/field-justification.md), et [Minimum champ longueurs dans les enregistrements délimités](../core/minimum-field-lengths-within-delimited-records.md).</span><span class="sxs-lookup"><span data-stu-id="b1c41-122">For more information, see [Field Padding](../core/field-padding.md), [Field Justification](../core/field-justification.md), and [Minimum Field Lengths Within Delimited Records](../core/minimum-field-lengths-within-delimited-records.md).</span></span>  
  
-   <span data-ttu-id="b1c41-123">Les enregistrements positionnels imbriqués dans d'autres enregistrements délimités.</span><span class="sxs-lookup"><span data-stu-id="b1c41-123">Positional records nested within other delimited records.</span></span> <span data-ttu-id="b1c41-124">Pour plus d’informations, consultez [enregistrements imbriqués positionnels et délimités](../core/nested-positional-and-delimited-records.md).</span><span class="sxs-lookup"><span data-stu-id="b1c41-124">For more information, see [Nested Positional and Delimited Records](../core/nested-positional-and-delimited-records.md).</span></span>  
  
-   <span data-ttu-id="b1c41-125">Comment les données sont justifiées dans un champ de longueur fixe, relativement aux caractères de remplissage les accompagnant.</span><span class="sxs-lookup"><span data-stu-id="b1c41-125">How data is justified within a fixed length field, relative to its accompanying pad characters.</span></span> <span data-ttu-id="b1c41-126">Pour plus d’informations, consultez [Justification des champs](../core/field-justification.md).</span><span class="sxs-lookup"><span data-stu-id="b1c41-126">For more information, see [Field Justification](../core/field-justification.md).</span></span>  
  
-   <span data-ttu-id="b1c41-127">Les considérations ayant trait au positionnement des délimiteurs relativement aux données qu'ils délimitent.</span><span class="sxs-lookup"><span data-stu-id="b1c41-127">Considerations concerning the positioning of delimiters relate to the data that they delimit.</span></span> <span data-ttu-id="b1c41-128">Pour plus d’informations, consultez [considérations d’ordre enfant](../core/child-order-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="b1c41-128">For more information, see [Child Order Considerations](../core/child-order-considerations.md).</span></span>  
  
-   <span data-ttu-id="b1c41-129">La préservation et la suppression de délimiteurs lors de la réception ou de l'envoi des messages de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="b1c41-129">Preservation and suppression of delimiters when flat file messages are received and sent.</span></span> <span data-ttu-id="b1c41-130">Pour plus d’informations, consultez [délimiteur préservation et Suppression de](../core/delimiter-preservation-and-suppression.md).</span><span class="sxs-lookup"><span data-stu-id="b1c41-130">For more information, see [Delimiter Preservation and Suppression](../core/delimiter-preservation-and-suppression.md).</span></span>  
  
 <span data-ttu-id="b1c41-131">Pour vous aider à mieux comprendre comment fonctionnent les fichiers plats délimités, consultez les exemples dans les dossiers FlatFileReceive et FlatFileSend dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Pipelines\AssemblerDisassembler\\.</span><span class="sxs-lookup"><span data-stu-id="b1c41-131">To help you better understand how to work with delimited flat files, see the samples in the FlatFileReceive and FlatFileSend folders located at [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Pipelines\AssemblerDisassembler\\.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1c41-132">Si votre fichier plat contient des enregistrements délimités et positionnels, vous devez définir le **Structure** propriété du nœud racine à **délimité** et **Structure** propriété de secondaire des nœuds d’enregistrement soit **délimité** ou **positionnel** selon le cas.</span><span class="sxs-lookup"><span data-stu-id="b1c41-132">If your flat file contains both delimited and positional records, you must set the **Structure** property of the root node to **Delimited** and the **Structure** property of subordinate record nodes to either **Delimited** or **Positional** as appropriate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1c41-133">Les champs délimités des fichiers plats sont limités à 50 000 000 caractères.</span><span class="sxs-lookup"><span data-stu-id="b1c41-133">Delimited fields in flat files have a limit of 50000000 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c41-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1c41-134">See Also</span></span>  
 <span data-ttu-id="b1c41-135">[Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="b1c41-135">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 <span data-ttu-id="b1c41-136">[Comment créer des schémas pour les Messages de fichier plat](../core/how-to-create-schemas-for-flat-file-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b1c41-136">[How to Create Schemas for Flat File Messages](../core/how-to-create-schemas-for-flat-file-messages.md) </span></span>  
 [<span data-ttu-id="b1c41-137">Migration des enregistrements de fichier plat</span><span class="sxs-lookup"><span data-stu-id="b1c41-137">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)