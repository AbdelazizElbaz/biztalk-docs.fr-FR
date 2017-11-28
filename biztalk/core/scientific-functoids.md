---
title: Fonctoids scientifiques | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0311b7dc-1955-45af-b858-681faccc939b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b23f65ecede9082ec93041ddab45fa92029851a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scientific-functoids"></a><span data-ttu-id="9dfde-102">Fonctoids scientifiques</span><span class="sxs-lookup"><span data-stu-id="9dfde-102">Scientific Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="9dfde-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="9dfde-103">Overview</span></span>
<span data-ttu-id="9dfde-104">**Scientifique** fonctoids sont utilisés pour effectuer des calculs exponentiels, logarithmiques et trigonométriques standard diverses.</span><span class="sxs-lookup"><span data-stu-id="9dfde-104">**Scientific** functoids are used to perform a variety of standard trigonometric, logarithmic, and exponential calculations.</span></span>  
  
 <span data-ttu-id="9dfde-105">À l’exception de la **fonctoid Logarithme** et **X ^ Y** fonctoids, qui exigent deux paramètres d’entrée, la **scientifique** fonctoids tous les acceptent un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="9dfde-105">With the exception of the **Base-Specified Logarithm** and **X^Y** functoids, which each take two input parameters, the **Scientific** functoids all take a single parameter.</span></span>  
  
 <span data-ttu-id="9dfde-106">Les quatre fonctions trigonométriques **scientifique** fonctoids (**Arc tangente**, **cosinus**, **sinus**, et **tangente**) tous les utiliseront radians au lieu de degrés comme unité pour leur entrée pertinente ou les paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="9dfde-106">The four trigonometric **Scientific** functoids (**Arc Tangent**, **Cosine**, **Sine**, and **Tangent**) all use radians rather than degrees as the units for their relevant input or output parameters.</span></span> <span data-ttu-id="9dfde-107">Un radian est une unité de mesure des angles, de sorte qu’il existe 2π radians dans un cercle.</span><span class="sxs-lookup"><span data-stu-id="9dfde-107">A radian is a unit of measure of angles, such that there are 2π radians in a circle.</span></span> <span data-ttu-id="9dfde-108">Il en résulte que :</span><span class="sxs-lookup"><span data-stu-id="9dfde-108">It follows that:</span></span>  
  
-   <span data-ttu-id="9dfde-109">2π radians équivalent à 360 degrés</span><span class="sxs-lookup"><span data-stu-id="9dfde-109">2π radians equals 360 degrees</span></span>  
  
-   <span data-ttu-id="9dfde-110">1 radian = 180/π degrés</span><span class="sxs-lookup"><span data-stu-id="9dfde-110">1 radian = 180/π degrees</span></span>  
  
-   <span data-ttu-id="9dfde-111">1 degré = π/180 radians</span><span class="sxs-lookup"><span data-stu-id="9dfde-111">1 degree = π/180 radians</span></span>  
  
 <span data-ttu-id="9dfde-112">Si vos messages d’instance d’entrée ou de sortie utilisent des degrés comme unité de mesure des angles, vous devez utiliser un **mathématique** fonctoid en conjonction avec un trigonométrique **scientifique** fonctoid obtenir un résultat correct.</span><span class="sxs-lookup"><span data-stu-id="9dfde-112">If your input or output instance messages use degrees as their unit of measure for angles, you will need to use a **Mathematical** functoid in conjunction with a trigonometric **Scientific** functoid to achieve the correct result.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="9dfde-113">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="9dfde-113">Available functoids</span></span>  
 <span data-ttu-id="9dfde-114">Le **scientifique** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="9dfde-114">The **Scientific** functoids are:</span></span> 

* <span data-ttu-id="9dfde-115">10^n</span><span class="sxs-lookup"><span data-stu-id="9dfde-115">10^n</span></span>
* <span data-ttu-id="9dfde-116">Arc tangente</span><span class="sxs-lookup"><span data-stu-id="9dfde-116">Arc Tangent</span></span>
* <span data-ttu-id="9dfde-117">Logarithme spécifié à partir de la base</span><span class="sxs-lookup"><span data-stu-id="9dfde-117">Base-Specified Logarithm</span></span>
* <span data-ttu-id="9dfde-118">Logarithme commun</span><span class="sxs-lookup"><span data-stu-id="9dfde-118">Common Logarithm</span></span>
* <span data-ttu-id="9dfde-119">Cosinus</span><span class="sxs-lookup"><span data-stu-id="9dfde-119">Cosine</span></span>
* <span data-ttu-id="9dfde-120">Fonction exponentielle naturelle</span><span class="sxs-lookup"><span data-stu-id="9dfde-120">Natural Exponential Function</span></span>
* <span data-ttu-id="9dfde-121">Logarithme naturel</span><span class="sxs-lookup"><span data-stu-id="9dfde-121">Natural Logarithm</span></span>
* <span data-ttu-id="9dfde-122">Sinus</span><span class="sxs-lookup"><span data-stu-id="9dfde-122">Sine</span></span>
* <span data-ttu-id="9dfde-123">Tangente</span><span class="sxs-lookup"><span data-stu-id="9dfde-123">Tangent</span></span>
* <span data-ttu-id="9dfde-124">X^Y</span><span class="sxs-lookup"><span data-stu-id="9dfde-124">X^Y</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9dfde-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dfde-125">See Also</span></span>  
-  [<span data-ttu-id="9dfde-126">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="9dfde-126">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="9dfde-127">**Référence des fonctoids scientifiques**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="9dfde-127">**Scientific Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>