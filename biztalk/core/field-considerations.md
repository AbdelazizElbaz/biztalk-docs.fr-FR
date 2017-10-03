---
title: "Considérations de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d7f1853-60ed-49c2-a592-61bde5445d36
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 861f8d8bacb7c0110c9ccbfdf55f8f0547c79bad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-considerations"></a><span data-ttu-id="44ec7-102">Considérations relatives aux champs</span><span class="sxs-lookup"><span data-stu-id="44ec7-102">Field Considerations</span></span>
<span data-ttu-id="44ec7-103">Il existe un certain nombre de considérations vous gardez à l’esprit lorsque vous travaillez avec **Fieldelement** et **attribut de champ** nœuds au sein de vos schémas.</span><span class="sxs-lookup"><span data-stu-id="44ec7-103">There are a number of considerations that you should keep in mind when working with **Field Element** and **Field Attribute** nodes within your schemas.</span></span> <span data-ttu-id="44ec7-104">Il convient notamment d'observer des distinctions de base pour déterminer quand utiliser l'un ou l'autre de ces types de nœuds. Par ailleurs, des considérations plus spécifiques s'appliquent à la spécification de longueurs, de justification et de remplissage de champ.</span><span class="sxs-lookup"><span data-stu-id="44ec7-104">This includes the basic distinctions regarding when to use each of these nodes types, as well as more specific considerations related to the specification of field lengths, field justification, and field padding.</span></span> <span data-ttu-id="44ec7-105">Cette section contient des informations sur ces points :</span><span class="sxs-lookup"><span data-stu-id="44ec7-105">This section provides information about these considerations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44ec7-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="44ec7-106">In This Section</span></span>  
  
-   [<span data-ttu-id="44ec7-107">Nœuds élément de champ vs. Nœuds attribut de champ</span><span class="sxs-lookup"><span data-stu-id="44ec7-107">Field Element Nodes vs. Field Attribute Nodes</span></span>](../core/field-element-nodes-vs-field-attribute-nodes.md)  
  
-   [<span data-ttu-id="44ec7-108">Formats de Date et d’heure personnalisés</span><span class="sxs-lookup"><span data-stu-id="44ec7-108">Custom Date-Time Formats</span></span>](../core/custom-date-time-formats.md)  
  
-   [<span data-ttu-id="44ec7-109">Remplissage des champs</span><span class="sxs-lookup"><span data-stu-id="44ec7-109">Field Padding</span></span>](../core/field-padding.md)  
  
-   [<span data-ttu-id="44ec7-110">Justification des champs</span><span class="sxs-lookup"><span data-stu-id="44ec7-110">Field Justification</span></span>](../core/field-justification.md)  
  
-   [<span data-ttu-id="44ec7-111">Spécification des Positions de champ dans les enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="44ec7-111">Specification of Field Positions within Positional Records</span></span>](../core/specification-of-field-positions-within-positional-records.md)  
  
-   [<span data-ttu-id="44ec7-112">Longueur minimale des champs dans les enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="44ec7-112">Minimum Field Lengths Within Delimited Records</span></span>](../core/minimum-field-lengths-within-delimited-records.md)