---
title: Fonctoids date et heure | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e2d49f5-1aaf-4e4d-8da1-e8605304dccb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ec31607ecefb417fef597b5ba700e6461c71a2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="date-and-time-functoids"></a><span data-ttu-id="08e6b-102">Fonctoids Date et heure</span><span class="sxs-lookup"><span data-stu-id="08e6b-102">Date and Time Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="08e6b-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="08e6b-103">Overview</span></span>
<span data-ttu-id="08e6b-104">**Date / heure** fonctoids peuvent être divisés en deux catégories.</span><span class="sxs-lookup"><span data-stu-id="08e6b-104">**Date / Time** functoids can be divided into two categories.</span></span> <span data-ttu-id="08e6b-105">La première catégorie contient un seul fonctoid, **ajouter des jours**, ce qui permet d’ajouter un nombre de jours spécifié à une date et une valeur d’heure.</span><span class="sxs-lookup"><span data-stu-id="08e6b-105">The first category contains a single functoid, **Add Days**, which is used to add a specified number of days to a specified date and time value.</span></span> <span data-ttu-id="08e6b-106">C'est particulièrement utile lorsqu'un champ d'un message d'instance de sortie est censé comporter une estimation de date et d’heure futures.</span><span class="sxs-lookup"><span data-stu-id="08e6b-106">This can be useful when a field in the output instance message is supposed to include a date and time estimate in the future.</span></span> <span data-ttu-id="08e6b-107">Par exemple, le **ajouter des jours** fonctoid peut être utilisé pour générer une estimation date d’expédition en fonction un delta fixe à partir de la date à laquelle une commande a été reçue.</span><span class="sxs-lookup"><span data-stu-id="08e6b-107">For example, the **Add Days** functoid can be used to generate an estimated shipping date based a fixed delta from the date that an order was received.</span></span>  
  
 <span data-ttu-id="08e6b-108">La seconde catégorie comprend tous les autres fonctoids dans le **Date et heure** catégorie.</span><span class="sxs-lookup"><span data-stu-id="08e6b-108">The second category includes all of the remaining functoids in the **Date and Time** category.</span></span> <span data-ttu-id="08e6b-109">Ils sont utilisés pour fournir un horodatage au moment de l’exécution, de sorte que la date et l'heure auxquelles la transformation du message est exécutée peuvent être intégrées au message d'instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="08e6b-109">They are used to provide a timestamp at run time, so that the date and time at which message transformation is being performed can be included in the output instance message.</span></span>  
  
 <span data-ttu-id="08e6b-110">Le **ajouter des jours** fonctoid accepte deux paramètres d’entrée, alors que le **Date**, **Date et heure**, et **temps** fonctoids n’ont aucune entrée. paramètres.</span><span class="sxs-lookup"><span data-stu-id="08e6b-110">The **Add Days** functoid accepts two input parameters, whereas the **Date**, **Date and Time**, and **Time** functoids have no input parameters.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="08e6b-111">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="08e6b-111">Available functoids</span></span>  
 <span data-ttu-id="08e6b-112">Le **Date / heure** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="08e6b-112">The **Date / Time** functoids are:</span></span> 

* <span data-ttu-id="08e6b-113">Ajouter des jours</span><span class="sxs-lookup"><span data-stu-id="08e6b-113">Add Days</span></span>
* <span data-ttu-id="08e6b-114">Date</span><span class="sxs-lookup"><span data-stu-id="08e6b-114">Date</span></span>
* <span data-ttu-id="08e6b-115">Date et heure</span><span class="sxs-lookup"><span data-stu-id="08e6b-115">Date and Time</span></span>
* <span data-ttu-id="08e6b-116">Time</span><span class="sxs-lookup"><span data-stu-id="08e6b-116">Time</span></span>

<span data-ttu-id="08e6b-117">Plus de détails sur ces fonctoids **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="08e6b-117">More details on these functoids are available **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="08e6b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08e6b-118">See Also</span></span>  
-  [<span data-ttu-id="08e6b-119">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="08e6b-119">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="08e6b-120">**Référence des fonctoids date et heure**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="08e6b-120">**Date and Time Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>