---
title: Messages de fichier plat avec des enregistrements positionnels | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c17c25-3847-458e-a43e-0dbdc42db749
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42ad36873c5b252afb185f5e341de923942dea73
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="flat-file-messages-with-positional-records"></a><span data-ttu-id="2a547-102">Messages de fichier plat avec des enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="2a547-102">Flat File Messages with Positional Records</span></span>
<span data-ttu-id="2a547-103">Les enregistrements positionnels d'un message d'instance de fichier plat contiennent des champs individuels (éléments de données) qui ont chacun une longueur prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="2a547-103">Positional records within a flat file instance message contain individual fields (items of data) that are each of a predefined length.</span></span> <span data-ttu-id="2a547-104">Les champs sont analysés selon ces longueurs.</span><span class="sxs-lookup"><span data-stu-id="2a547-104">The fields are parsed according to these lengths.</span></span> <span data-ttu-id="2a547-105">Prenons l'exemple de l'enregistrement positionnel suivant, issu d'un message d'instance de fichier plat et qui contient une adresse de livraison (la première ligne indique le nombre de caractères réservés à chaque champ).</span><span class="sxs-lookup"><span data-stu-id="2a547-105">For example, consider the following positional record from a flat file instance message, which contains a ship to address (the first line shows the number of characters reserved for each field).</span></span>  
  
```  
123456789012345678901234567890123456789012345678901234567890123456789012345  
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952  
```  
  
 <span data-ttu-id="2a547-106">Une définition raisonnable d'un tel enregistrement dans un schéma de fichier plat peut être celle d'un enregistrement positionnel appelé shipTo contenant les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="2a547-106">A reasonable definition for this record in a flat file schema can be described as a positional record named shipTo that contains the following fields:</span></span>  
  
-   <span data-ttu-id="2a547-107">Un attribut appelé pays/région aligné à gauche, long de 10 caractères, avec un décalage de zéro caractère.</span><span class="sxs-lookup"><span data-stu-id="2a547-107">An attribute named country/region that is left-aligned, 10 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="2a547-108">Un élément appelé nom aligné à gauche, long de 20 caractères, avec un décalage de zéro caractère.</span><span class="sxs-lookup"><span data-stu-id="2a547-108">An element named name that is left-aligned, 20 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="2a547-109">Un élément appelé rue aligné à gauche, long de 20 caractères, avec un décalage de zéro caractère.</span><span class="sxs-lookup"><span data-stu-id="2a547-109">An element named street that is left-aligned, 20 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="2a547-110">Un élément appelé ville aligné à gauche, long de 15 caractères, avec un décalage de zéro caractère.</span><span class="sxs-lookup"><span data-stu-id="2a547-110">An element named city that is left-aligned, 15 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="2a547-111">Un élément appelé département aligné à gauche, long de 2 caractères, avec un décalage de zéro caractère.</span><span class="sxs-lookup"><span data-stu-id="2a547-111">An element named state that is left-aligned, 2 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="2a547-112">Un élément appelé code postal aligné à gauche, long de 5 caractères, avec un décalage d'un caractère.</span><span class="sxs-lookup"><span data-stu-id="2a547-112">An element named zip that is left-aligned, 5 characters in length, with a one character offset.</span></span>  
  
 <span data-ttu-id="2a547-113">Sur la base de ces définitions d'enregistrement et de champ, le désassembleur de fichier plat génèrera l'équivalent XML suivant de cet enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2a547-113">Given these record and field definitions, the flat file disassembler will produce the following XML equivalent of this record.</span></span>  
  
```  
<shipTo country/region="US">  
    <name>Alice Smith</name>  
    <street>123 Maple Street</street>  
    <city>Mill Valley</city>  
    <state>CA</state>  
    <zip>90952</zip>  
</shipTo>  
  
```  
  
 <span data-ttu-id="2a547-114">Il y a un certain nombre d'aspects relatifs aux enregistrements positionnels qui ont une incidence sur la manière dont l'enregistrement est analysé lors de sa réception et construit lors de son envoi. Parmi eux, citons :</span><span class="sxs-lookup"><span data-stu-id="2a547-114">There are a number of considerations related to positional records that will affect how the record is parsed when received and constructed when sent, including:</span></span>  
  
-   <span data-ttu-id="2a547-115">Le caractère utilisé pour remplir la portion inutilisée de chaque champ et connu sous le nom de caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="2a547-115">The character used to fill the unused portion of each field, known as the pad character.</span></span> <span data-ttu-id="2a547-116">Pour plus d’informations, consultez [remplissage des champs](../core/field-padding.md).</span><span class="sxs-lookup"><span data-stu-id="2a547-116">For more information, see [Field Padding](../core/field-padding.md).</span></span>  
  
-   <span data-ttu-id="2a547-117">Une balise optionnelle se trouvant dans l'enregistrement et utilisée pour le distinguer d'autres enregistrements similaires.</span><span class="sxs-lookup"><span data-stu-id="2a547-117">An optional tag within the record, used to distinguish the record from other similar records.</span></span> <span data-ttu-id="2a547-118">Les balises sont généralement placées au début des enregistrements mais peuvent très bien trouver place à n'importe quel autre endroit des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="2a547-118">Tags usually occur at the beginning of the record but allowable anywhere within it.</span></span> <span data-ttu-id="2a547-119">Pour plus d’informations, consultez [gestion des balises dans les enregistrements positionnels](../core/tag-handling-in-positional-records.md).</span><span class="sxs-lookup"><span data-stu-id="2a547-119">For more information, see [Tag Handling in Positional Records](../core/tag-handling-in-positional-records.md).</span></span> <span data-ttu-id="2a547-120">Il est possible de définir si les enregistrements positionnels doivent comporter ou non une balise, mais une fois la décision prise, elle doit être respectée.</span><span class="sxs-lookup"><span data-stu-id="2a547-120">Positional records can be defined to have a tag or not have a tag, but once defined, the tag must be present or not, based on the definition.</span></span>  
  
-   <span data-ttu-id="2a547-121">Comment les données sont justifiées dans un champ de longueur fixe, par rapport aux caractères de remplissage accompagnant.</span><span class="sxs-lookup"><span data-stu-id="2a547-121">How data is justified within a fixed length field, relative to the accompanying pad characters.</span></span> <span data-ttu-id="2a547-122">Pour plus d’informations, consultez [Justification des champs](../core/field-justification.md).</span><span class="sxs-lookup"><span data-stu-id="2a547-122">For more information, see [Field Justification](../core/field-justification.md).</span></span>  
  
-   <span data-ttu-id="2a547-123">Enregistrements positionnels imbriqués dans d'autres enregistrements positionnels ou délimités.</span><span class="sxs-lookup"><span data-stu-id="2a547-123">Positional records nested within other positional or delimited records.</span></span> <span data-ttu-id="2a547-124">Pour plus d’informations, consultez [enregistrements positionnels imbriqués](../core/nested-positional-records.md).</span><span class="sxs-lookup"><span data-stu-id="2a547-124">For more information, see [Nested Positional Records](../core/nested-positional-records.md).</span></span>  
  
-   <span data-ttu-id="2a547-125">Enregistrements positionnels dotés de longueurs de champ spécifiées sous la forme d'un nombre spécifique d'octets et non d'un nombre spécifique de caractères.</span><span class="sxs-lookup"><span data-stu-id="2a547-125">Positional records with field lengths specified as a specific number of bytes rather than a specific number of characters.</span></span> <span data-ttu-id="2a547-126">Pour plus d’informations, consultez [comptage des positions en octets](../core/position-counting-in-bytes.md).</span><span class="sxs-lookup"><span data-stu-id="2a547-126">For more information, see [Position Counting in Bytes](../core/position-counting-in-bytes.md).</span></span>  
  
 <span data-ttu-id="2a547-127">Pour vous aider à mieux comprendre comment fonctionnent les fichiers plats positionnels, consultez les exemples dans les dossiers FlatFileReceive et FlatFileSend dans \Program Files\Microsoft BizTalk Server\SDK\Samples\Pipelines\AssemblerDisassembler\\.</span><span class="sxs-lookup"><span data-stu-id="2a547-127">To help you better understand how to work with positional flat files, see the samples in the FlatFileReceive and FlatFileSend folders located at \Program Files\Microsoft BizTalk Server\SDK\Samples\Pipelines\AssemblerDisassembler\\.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a547-128">Si votre fichier plat contient des enregistrements délimités et positionnels, vous devez définir le **Structure** propriété du nœud racine à **délimité** et **Structure** propriété de secondaire des nœuds d’enregistrement soit **délimité** ou **positionnel** selon le cas.</span><span class="sxs-lookup"><span data-stu-id="2a547-128">If your flat file contains both delimited and positional records, you must set the **Structure** property of the root node to **Delimited** and the **Structure** property of subordinate record nodes to either **Delimited** or **Positional** as appropriate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a547-129">Les champs des enregistrements positionnels sont limités à 50 000 000 caractères.</span><span class="sxs-lookup"><span data-stu-id="2a547-129">Fields in positional records have a limit of 50000000 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a547-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a547-130">See Also</span></span>  
 <span data-ttu-id="2a547-131">[Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="2a547-131">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 [<span data-ttu-id="2a547-132">Comment créer des schémas pour les Messages de fichier plat</span><span class="sxs-lookup"><span data-stu-id="2a547-132">How to Create Schemas for Flat File Messages</span></span>](../core/how-to-create-schemas-for-flat-file-messages.md)