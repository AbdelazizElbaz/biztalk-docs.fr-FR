---
title: "Fonctoids mathématiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 244fa926-a086-4398-a677-9c322e9024b2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 232098f27578e75bb925be47a202b07b6487d65d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mathematical-functoids"></a><span data-ttu-id="6ee87-102">Fonctoids mathématiques</span><span class="sxs-lookup"><span data-stu-id="6ee87-102">Mathematical Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="6ee87-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="6ee87-103">Overview</span></span>
<span data-ttu-id="6ee87-104">**Mathématiques** fonctoids sont utilisés pour effectuer diverses opérations mathématiques de base.</span><span class="sxs-lookup"><span data-stu-id="6ee87-104">**Mathematical** functoids are used to perform a variety of basic mathematical operations.</span></span>  
  
 <span data-ttu-id="6ee87-105">Le nombre de paramètres d’entrée pour le **mathématique** fonctoids varient à partir du fonctoid au fonctoid, et dans certains cas, ces fonctoids acceptent un grand nombre d’entrées.</span><span class="sxs-lookup"><span data-stu-id="6ee87-105">The number of input parameters to the **Mathematical** functoids varies from functoid to functoid, and where reasonable, these functoids accept large numbers of inputs.</span></span> <span data-ttu-id="6ee87-106">Par exemple, le **Division** fonctoid requiert exactement deux paramètres d’entrée (le dividende et le diviseur), lors de la **ajout** fonctoid accepte entre 2 et 100 paramètres d’entrée, ce qui entraîne leur somme.</span><span class="sxs-lookup"><span data-stu-id="6ee87-106">For example, the **Division** functoid requires exactly two input parameters (the dividend and the divisor), while the **Addition** functoid accepts between 2 and 100 input parameters, resulting in their sum.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ee87-107">Étant donné que Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise la fonctionnalité sous-jacente de .NET Framework, les résultats générés par certains de la **mathématique** fonctoids peuvent varier par rapport aux fonctoids équivalents dans les versions précédentes de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6ee87-107">Because Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the underlying functionality of the .NET Framework, the results produced by some of the **Mathematical** functoids may vary from the equivalent functoids in previous versions of BizTalk Server.</span></span> <span data-ttu-id="6ee87-108">Testez vos mappages minutieusement pour veiller à ce que vous obtenez les résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="6ee87-108">Test your maps thoroughly to be sure you are getting the results you expect.</span></span>  

## <a name="functoids-list"></a><span data-ttu-id="6ee87-109">Liste des fonctoids</span><span class="sxs-lookup"><span data-stu-id="6ee87-109">Functoids list</span></span>  
 <span data-ttu-id="6ee87-110">Le **mathématique** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="6ee87-110">The **Mathematical** functoids are:</span></span> 

* <span data-ttu-id="6ee87-111">Valeur absolue</span><span class="sxs-lookup"><span data-stu-id="6ee87-111">Absolute Value</span></span>
* <span data-ttu-id="6ee87-112">Addition</span><span class="sxs-lookup"><span data-stu-id="6ee87-112">Addition</span></span>
* <span data-ttu-id="6ee87-113">Division</span><span class="sxs-lookup"><span data-stu-id="6ee87-113">Division</span></span>
* <span data-ttu-id="6ee87-114">Entier</span><span class="sxs-lookup"><span data-stu-id="6ee87-114">Integer</span></span>
* <span data-ttu-id="6ee87-115">Valeur maximale</span><span class="sxs-lookup"><span data-stu-id="6ee87-115">Maximum Value</span></span>
* <span data-ttu-id="6ee87-116">Valeur minimale</span><span class="sxs-lookup"><span data-stu-id="6ee87-116">Minimum Value</span></span>
* <span data-ttu-id="6ee87-117">Modulo</span><span class="sxs-lookup"><span data-stu-id="6ee87-117">Modulo</span></span>
* <span data-ttu-id="6ee87-118">Multiplication</span><span class="sxs-lookup"><span data-stu-id="6ee87-118">Multiplication</span></span>
* <span data-ttu-id="6ee87-119">Arrondi</span><span class="sxs-lookup"><span data-stu-id="6ee87-119">Round</span></span>
* <span data-ttu-id="6ee87-120">Racine carrée</span><span class="sxs-lookup"><span data-stu-id="6ee87-120">Square Root</span></span>
* <span data-ttu-id="6ee87-121">Soustraction</span><span class="sxs-lookup"><span data-stu-id="6ee87-121">Subtraction</span></span>

<span data-ttu-id="6ee87-122">Plus d’informations sur ces fonctoids est [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="6ee87-122">More info on these functoids is [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="6ee87-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ee87-123">See Also</span></span>  
 [<span data-ttu-id="6ee87-124">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="6ee87-124">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
