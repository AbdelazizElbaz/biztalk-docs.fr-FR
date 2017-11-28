---
title: "Fonctoids de chaîne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d73be02-9c93-481f-81e4-39b60bcfa2df
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06bcb1d42a5e72a57765d17c18a48b6f4808d412
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="string-functoids"></a><span data-ttu-id="ae1d0-102">Fonctoids de chaîne</span><span class="sxs-lookup"><span data-stu-id="ae1d0-102">String Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="ae1d0-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ae1d0-103">Overview</span></span>
<span data-ttu-id="ae1d0-104">**Chaîne** fonctoids sont utilisées pour manipuler des chaînes dans des méthodes standard tels que les conversions en majuscules ou minuscules, concaténation de chaînes, détermination de la longueur de chaîne, des espaces et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ae1d0-104">**String** functoids are used to manipulate strings in standard ways such as conversions to all uppercase or all lowercase, string concatenation, determination of string length, white space trimming, and so on.</span></span>  
  
 <span data-ttu-id="ae1d0-105">Les fonctoids **majuscules**, **minuscules**, **taille**, **supprimer à droite de chaîne**, et **supprimer à gauche de chaîne** accepter qu’un seul paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ae1d0-105">The functoids **Uppercase**, **Lowercase**, **Size**, **String Right Trim**, and **String Left Trim** accept only one input parameter.</span></span> <span data-ttu-id="ae1d0-106">Les fonctoids **recherche de chaîne**, **gauche de la chaîne**, et **chaîne de droite** acceptent deux paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ae1d0-106">The functoids **String Find**, **String Left**, and **String Right** accept two input parameters.</span></span> <span data-ttu-id="ae1d0-107">Le **extraction de chaîne** fonctoid accepte trois entrées, alors que le **concaténation de chaînes** fonctoid accepte des paramètres d’entrée entre 1 et 100.</span><span class="sxs-lookup"><span data-stu-id="ae1d0-107">The **String Extract** functoid accepts three inputs, whereas the **String Concatenate** functoid accepts input parameters between 1 and 100.</span></span>  
  
 <span data-ttu-id="ae1d0-108">Deux **chaîne** fonctoids font référence à la position numérique d’un caractère dans une chaîne : **extraction de chaîne** et **recherche de chaîne**.</span><span class="sxs-lookup"><span data-stu-id="ae1d0-108">Two **String** functoids refer to the numeric position of a character in a string: **String Extract** and **String Find**.</span></span> <span data-ttu-id="ae1d0-109">ces fonctoids commencent à compter les positions des caractères à 1, et non à 0.</span><span class="sxs-lookup"><span data-stu-id="ae1d0-109">These functoids begin counting character positions at 1, not 0.</span></span>  
  
 <span data-ttu-id="ae1d0-110">Les deux fonctoids de suppression, de chaîne **supprimer à gauche de chaîne** et **supprimer à droite de chaîne**, supprimez tous les caractères d’espace blanc (espaces, tabulations, etc.) à partir de la gauche ou la droite (selon le cas) de la chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ae1d0-110">The two string trimming functoids, **String Left Trim** and **String Right Trim**, remove all white space characters (spaces, tabs, and so on) from the left  or right (as the case may be) of the specified string.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="ae1d0-111">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="ae1d0-111">Available functoids</span></span> 
 <span data-ttu-id="ae1d0-112">Le **chaîne** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="ae1d0-112">The **String** functoids are:</span></span> 

* <span data-ttu-id="ae1d0-113">Minuscules</span><span class="sxs-lookup"><span data-stu-id="ae1d0-113">Lowercase</span></span>
* <span data-ttu-id="ae1d0-114">Taille</span><span class="sxs-lookup"><span data-stu-id="ae1d0-114">Size</span></span>
* <span data-ttu-id="ae1d0-115">Concaténation de chaînes</span><span class="sxs-lookup"><span data-stu-id="ae1d0-115">String Concatenate</span></span>
* <span data-ttu-id="ae1d0-116">Extraction de chaîne</span><span class="sxs-lookup"><span data-stu-id="ae1d0-116">String Extract</span></span>
* <span data-ttu-id="ae1d0-117">Recherche de chaîne</span><span class="sxs-lookup"><span data-stu-id="ae1d0-117">String Find</span></span>
* <span data-ttu-id="ae1d0-118">Chaîne de gauche</span><span class="sxs-lookup"><span data-stu-id="ae1d0-118">String Left</span></span>
* <span data-ttu-id="ae1d0-119">Supprimer à gauche de la chaîne</span><span class="sxs-lookup"><span data-stu-id="ae1d0-119">String Left Trim</span></span>
* <span data-ttu-id="ae1d0-120">Chaîne de droite</span><span class="sxs-lookup"><span data-stu-id="ae1d0-120">String Right</span></span>
* <span data-ttu-id="ae1d0-121">Supprimer à droite de la chaîne</span><span class="sxs-lookup"><span data-stu-id="ae1d0-121">String Right Trim</span></span>
* <span data-ttu-id="ae1d0-122">Majuscules</span><span class="sxs-lookup"><span data-stu-id="ae1d0-122">Uppercase</span></span>

<span data-ttu-id="ae1d0-123">Plus d’informations sur ces fonctoids [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="ae1d0-123">More details on these functoids [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ae1d0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae1d0-124">See Also</span></span>  
-  [<span data-ttu-id="ae1d0-125">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="ae1d0-125">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="ae1d0-126">**Référence des fonctoids de chaîne**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="ae1d0-126">**String Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>