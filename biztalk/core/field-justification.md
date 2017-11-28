---
title: Justification du champ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04380208-9bfd-43cf-a279-104daea2b978
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da9209040e64380b3a7a167dd013a15232543a75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-justification"></a><span data-ttu-id="0f482-102">Justification des champs</span><span class="sxs-lookup"><span data-stu-id="0f482-102">Field Justification</span></span>

## <a name="overview"></a><span data-ttu-id="0f482-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0f482-103">Overview</span></span>
<span data-ttu-id="0f482-104">La justification des champs détermine si les caractères des données d’un champ sont placés avant (alignement à gauche) ou après (alignement à droite) les caractères de remplissage d’accompagnement.</span><span class="sxs-lookup"><span data-stu-id="0f482-104">Field justification concerns whether the data characters in a field occur before (left-aligned) or after (right-aligned) any accompanying pad characters.</span></span>  
  
 <span data-ttu-id="0f482-105">Il arrive que les caractères de données contenus dans un champ ne nécessitent pas tout l’espace consacré au champ.</span><span class="sxs-lookup"><span data-stu-id="0f482-105">Sometimes the data characters contained within a field do not require all of the space dedicated to that field.</span></span> <span data-ttu-id="0f482-106">Cela est vrai plus fréquemment dans les enregistrements positionnels, où le nombre d’octets ou de caractères consacrés à un champ est fixe, comme déterminé par le **longueur positionnelle** et **décalage de position** propriétés.</span><span class="sxs-lookup"><span data-stu-id="0f482-106">This is true most frequently in positional records, where the number of bytes or characters dedicated to a field is fixed, as determined by the **Positional Length** and **Positional Offset** properties.</span></span> <span data-ttu-id="0f482-107">Dans de tels cas, il est courant que les éléments de données soient plus petits que la longueur du champ, laissant une partie du champ inutilisée occupée par des caractères de remplissage.</span><span class="sxs-lookup"><span data-stu-id="0f482-107">It is common in such scenarios that the item of data is smaller than the field length, with the unused portion of the field being filled with pad characters.</span></span>  
  
 <span data-ttu-id="0f482-108">Tel remplissage peut également se produire dans les enregistrements délimités lorsque la valeur de la **longueur minimale avec caractère de remplissage** propriété dépasse l’espace nécessaire au stockage de l’élément de données correspondant.</span><span class="sxs-lookup"><span data-stu-id="0f482-108">Such padding can also occur in delimited records when the value of the **Minimum Length with Pad Character** property exceeds the space required to store the relevant item of data.</span></span>  
  
 <span data-ttu-id="0f482-109">Dans ces deux cas, la valeur de la **Justification** propriété (**gauche** ou **droite**) de la **élément de champ** ou **Attribut de champ** nœud détermine si les caractères de remplissage suivront les caractères de données (alignement à gauche) ou si les caractères de remplissage doit précéder les caractères de données (alignement à droite).</span><span class="sxs-lookup"><span data-stu-id="0f482-109">In both such cases, the value of the **Justification** property (**Left** or **Right**) of the relevant **Field Element** or **Field Attribute** node determines whether the pad characters will follow the data characters (left-aligned) or whether the pad characters will precede the data characters (right-aligned).</span></span>  
  
 <span data-ttu-id="0f482-110">Lorsque le désassembleur de fichier plat convertit un message d’instance de fichier plat en un message d’instance XML équivalent, la **Justification** propriété est utilisée lors de l’analyse du champ correspondant.</span><span class="sxs-lookup"><span data-stu-id="0f482-110">When the flat file disassembler is converting a flat file instance message into an equivalent XML instance message, the **Justification** property is used when parsing the corresponding field.</span></span> <span data-ttu-id="0f482-111">Lorsque l’assembleur de fichier plat convertit un message d’instance XML en un message d’instance de fichier plat équivalent, la **Justification** propriété est utilisée pour déterminer quand les caractères de remplissage associé à un champ particulier, le cas échéant, doit être ajouté au flux de données : avant ou après les caractères de données correspondante.</span><span class="sxs-lookup"><span data-stu-id="0f482-111">When the flat file assembler is converting an XML instance message into an equivalent flat file instance message, the **Justification** property is used to determine when the pad characters associated with a particular field, if any, should be added to the data stream: either before or after the corresponding data characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f482-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f482-112">See Also</span></span>  
- [<span data-ttu-id="0f482-113">Considérations relatives aux champs</span><span class="sxs-lookup"><span data-stu-id="0f482-113">Field Considerations</span></span>](../core/field-considerations.md)   
- <span data-ttu-id="0f482-114">Plus d’informations sur les propriétés suivantes [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span><span class="sxs-lookup"><span data-stu-id="0f482-114">More info on the following properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span></span>  
    - <span data-ttu-id="0f482-115">Justification (propriété de nœud des schémas de fichier plat)</span><span class="sxs-lookup"><span data-stu-id="0f482-115">Justification (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="0f482-116">Décalage de position (propriété de nœud des schémas de fichier plat)</span><span class="sxs-lookup"><span data-stu-id="0f482-116">Positional Offset (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="0f482-117">Longueur positionnelle (propriété de nœud des schémas de fichier plat)</span><span class="sxs-lookup"><span data-stu-id="0f482-117">Positional Length (Node Property of Flat File Schemas)</span></span>