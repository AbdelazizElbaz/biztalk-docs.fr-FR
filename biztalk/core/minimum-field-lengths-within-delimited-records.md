---
title: "Longueur minimale des champs dans les enregistrements délimités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24272d0d-34c8-487a-9334-683c65c159b8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d803eb311bda7c27db5a05830f7a84f9b9857e8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="minimum-field-lengths-within-delimited-records"></a><span data-ttu-id="bdf77-102">Longueur minimale des champs dans les enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="bdf77-102">Minimum Field Lengths Within Delimited Records</span></span>
<span data-ttu-id="bdf77-103">Par définition, les champs des enregistrements positionnels sont tous définis avec des longueurs spécifiques exactes.</span><span class="sxs-lookup"><span data-stu-id="bdf77-103">By definition, the fields in positional records are all defined to have specific exact lengths.</span></span> <span data-ttu-id="bdf77-104">Les champs des enregistrements délimités peuvent également être définis avec une longueur minimale.</span><span class="sxs-lookup"><span data-stu-id="bdf77-104">Fields in delimited records can also be defined to have a minimum length.</span></span> <span data-ttu-id="bdf77-105">Cette caractéristique est définie par le **[longueur minimale avec caractère de remplissage** propriété du **élément de champ** et **attribut de champ** nœuds.</span><span class="sxs-lookup"><span data-stu-id="bdf77-105">This characteristic is defined by the **[Minimum Length with Pad Character** property of **Field Element** and **Field Attribute** nodes.</span></span>  
  
 <span data-ttu-id="bdf77-106">Lorsque vous fournissez une valeur différente de zéro pour le **longueur minimale avec caractère de remplissage** propriété, l’assembleur de fichier plat détermine si le nombre de caractères de données associées au champ est inférieur à celle du paramètre de la **Longueur minimale avec caractère de remplissage** propriété, le caractère de remplissage correspondant permet de faire la différence.</span><span class="sxs-lookup"><span data-stu-id="bdf77-106">When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file assembler will determine whether the number of data characters associated with the field is smaller than the setting of the **Minimum Length with Pad Character** property, the relevant pad character will be used to make up the difference.</span></span>  
  
 <span data-ttu-id="bdf77-107">Les caractères de remplissage sont ajoutés avant ou après les caractères de données en fonction du paramètre de la **Justification** propriété pour le champ.</span><span class="sxs-lookup"><span data-stu-id="bdf77-107">The pad characters will be added before or after the data characters based on the setting of the **Justification** property for the field.</span></span> <span data-ttu-id="bdf77-108">Lorsque le **Justification** est définie sur **gauche**, tous les caractères de remplissage nécessaires pour obtenir la longueur minimale seront ajoutées après les caractères de données.</span><span class="sxs-lookup"><span data-stu-id="bdf77-108">When the **Justification** property is set to **Left**, any pad characters required to meet the minimum length will be added after the data characters.</span></span> <span data-ttu-id="bdf77-109">Lorsque le **Justification** est définie sur **droite**, tous les caractères de remplissage nécessaires pour obtenir la longueur minimale sont ajoutés avant les caractères de données.</span><span class="sxs-lookup"><span data-stu-id="bdf77-109">When the **Justification** property is set to **Right**, any pad characters required to meet the minimum length will be added before the data characters.</span></span>  
  
 <span data-ttu-id="bdf77-110">Lorsque vous fournissez une valeur différente de zéro pour le **longueur minimale avec caractère de remplissage** propriété, le désassembleur de fichier plat examine le début ou la fin (en fonction du paramètre de la **Justification** propriété) de la valeur du champ de la présence du caractère de remplissage correspondant, et le cas échéant, les caractères de remplissage seront ignorés et n’apparaissent pas dans le message XML équivalent en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="bdf77-110">When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file disassembler will examine the beginning or end (based on the setting of the **Justification** property) of the field value for the presence of the relevant pad character, and if present, the pad characters will be discarded and not appear in the equivalent XML message being constructed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf77-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdf77-111">See Also</span></span>  
-  [<span data-ttu-id="bdf77-112">Considérations relatives aux champs</span><span class="sxs-lookup"><span data-stu-id="bdf77-112">Field Considerations</span></span>](../core/field-considerations.md)   
-  <span data-ttu-id="bdf77-113">**Justification (propriété de nœud des schémas de fichier plat)** et **longueur minimale avec caractère de remplissage (propriété de nœud des schémas de fichier plat)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf77-113">**Justification (Node Property of Flat File Schemas)** and **Minimum Length with Pad Character (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>