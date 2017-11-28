---
title: Fonctoids de conversion | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0cd7abcf-f524-4e85-b8d5-d6123767490f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 192db4b03f80674f2eb90be2255a8682454bde2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conversion-functoids"></a><span data-ttu-id="e18f1-102">Fonctoids de conversion</span><span class="sxs-lookup"><span data-stu-id="e18f1-102">Conversion Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="e18f1-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e18f1-103">Overview</span></span>
<span data-ttu-id="e18f1-104">**Conversion** fonctoids sont utilisés pour effectuer une conversion entre les nombres et leurs équivalents ASCII et à convertir en base 10 numéros à leur base 8 et 16 équivalents de base.</span><span class="sxs-lookup"><span data-stu-id="e18f1-104">**Conversion** functoids are used to convert between numbers and their ASCII equivalents, and to convert base 10 numbers to their base 8 and base 16 equivalents.</span></span>  
  
 <span data-ttu-id="e18f1-105">Tous les fonctoids de conversion ne prennent qu'un seul paramètre d'entrée.</span><span class="sxs-lookup"><span data-stu-id="e18f1-105">All of the conversion functoids take a single input parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e18f1-106">En raison de modifications dans le système de type sous-jacent, les **Conversion** fonctoids dans cette version du Mappeur BizTalk produisent des résultats légèrement différents que celles produites dans les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="e18f1-106">Due to changes in the underlying type system, the **Conversion** functoids in this version of BizTalk Mapper produce slightly different results than those produced in previous versions.</span></span> <span data-ttu-id="e18f1-107">Par exemple, dans les versions précédentes du Mappeur BizTalk, une valeur d’entrée de -20 à la **hexadécimal** fonctoid a généré en sortie 0xFFEC.</span><span class="sxs-lookup"><span data-stu-id="e18f1-107">For example, in previous versions of BizTalk Mapper an input value of -20 to the **Hexadecimal** functoid resulted in an output of 0xFFEC.</span></span> <span data-ttu-id="e18f1-108">Dans cette version, cette même valeur d'entrée de -20 donne en sortie 0xFFFFFFEC.</span><span class="sxs-lookup"><span data-stu-id="e18f1-108">In this version, the same input value of -20 will result in an output of 0xFFFFFFEC.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="e18f1-109">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="e18f1-109">Available functoids</span></span>  
 <span data-ttu-id="e18f1-110">Le **Conversion** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="e18f1-110">The **Conversion** functoids are:</span></span> 

* <span data-ttu-id="e18f1-111">ASCII vers caractère</span><span class="sxs-lookup"><span data-stu-id="e18f1-111">ASCII to Character</span></span>
* <span data-ttu-id="e18f1-112">Caractère vers ASCII</span><span class="sxs-lookup"><span data-stu-id="e18f1-112">Character to ASCII</span></span>
* <span data-ttu-id="e18f1-113">Valeur hexadécimale</span><span class="sxs-lookup"><span data-stu-id="e18f1-113">Hexadecimal</span></span>
* <span data-ttu-id="e18f1-114">Octal</span><span class="sxs-lookup"><span data-stu-id="e18f1-114">Octal</span></span>

<span data-ttu-id="e18f1-115">Ces fonctoids sont décrites [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="e18f1-115">These functoids are described [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 

## <a name="see-also"></a><span data-ttu-id="e18f1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e18f1-116">See Also</span></span>  
 [<span data-ttu-id="e18f1-117">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="e18f1-117">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
