---
title: "Comment définir des étiquettes et commentaires sur plusieurs liens et fonctoids | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b554a19-2bd4-4dbc-b5cb-567b98c07024
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65bcb25fae52da46bbea1679e3b4e215720782d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-label-and-comment-on-multiple-links-and-functoids"></a><span data-ttu-id="f9a98-102">Comment définir les étiquettes et commentaires pour plusieurs liens et fonctoids</span><span class="sxs-lookup"><span data-stu-id="f9a98-102">How to Set Label and Comment on Multiple Links and Functoids</span></span>
<span data-ttu-id="f9a98-103">Vous pouvez définir une étiquette et/ou un commentaire communs pour plusieurs fonctoids et/ou liens.</span><span class="sxs-lookup"><span data-stu-id="f9a98-103">You can set a common label and/or a comment for multiple functoids and/or links.</span></span> <span data-ttu-id="f9a98-104">Cette rubrique décrit en détail le déroulement de cette opération.</span><span class="sxs-lookup"><span data-stu-id="f9a98-104">This topic provides details about how to perform this operation.</span></span>  
  
 <span data-ttu-id="f9a98-105">Pour plus d’informations sur la façon de sélectionner plusieurs fonctoids et/ou liens, consultez [comment sélectionner plusieurs liens et fonctoids](../core/how-to-select-multiple-links-and-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="f9a98-105">For information about how to select multiple functoid(s) and/or link(s), see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
 <span data-ttu-id="f9a98-106">Après avoir sélectionné plusieurs fonctoids et/ou liens, vous pouvez effectuer l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9a98-106">After selecting multiple functoid(s) and/or link(s), you can do any of the following:</span></span>  
  
-   <span data-ttu-id="f9a98-107">Définir une étiquette commune pour les liens sélectionnés</span><span class="sxs-lookup"><span data-stu-id="f9a98-107">Set a common label for selected links.</span></span>  
  
-   <span data-ttu-id="f9a98-108">Définir une étiquette et/ou un commentaire communs pour les fonctoids sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="f9a98-108">Set a common label and/or comment for the selected functoids.</span></span>  
  
-   <span data-ttu-id="f9a98-109">Définir une étiquette commune pour les fonctoids et les liens sélectionnés</span><span class="sxs-lookup"><span data-stu-id="f9a98-109">Set a common label for the selected functoids and links.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9a98-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f9a98-110">Prerequisites</span></span>  
 <span data-ttu-id="f9a98-111">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f9a98-111">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="to-set-a-common-label-for-selected-links"></a><span data-ttu-id="f9a98-112">Définition d'une étiquette commune pour les liens sélectionnés</span><span class="sxs-lookup"><span data-stu-id="f9a98-112">To set a common label for selected links</span></span>  
 <span data-ttu-id="f9a98-113">La définition d'une étiquette commune à plusieurs liens est une opération atomique,</span><span class="sxs-lookup"><span data-stu-id="f9a98-113">Setting a common label on multiple links is one atomic operation.</span></span> <span data-ttu-id="f9a98-114">Vous pouvez annuler ou rétablir cette opération.</span><span class="sxs-lookup"><span data-stu-id="f9a98-114">You can undo or redo this operation.</span></span>  
  
 <span data-ttu-id="f9a98-115">Pour définir une étiquette commune pour les liens sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="f9a98-115">To set a common label for the selected links:</span></span>  
  
1.  <span data-ttu-id="f9a98-116">Sur la page de grille du mappeur, sélectionnez les liens souhaités.</span><span class="sxs-lookup"><span data-stu-id="f9a98-116">On the Mapper grid page, select the desired links.</span></span>  
  
2.  <span data-ttu-id="f9a98-117">Dans le **propriétés** fenêtre, entrez une étiquette appropriée dans le **étiquette** propriété.</span><span class="sxs-lookup"><span data-stu-id="f9a98-117">In the **Properties** window, enter a suitable label in the **Label** property.</span></span>  
  
## <a name="to-set-a-common-label-andor-comment-for-selected-functoids"></a><span data-ttu-id="f9a98-118">Définition d'une étiquette et/ou d'un commentaire communs pour les fonctoids sélectionnés</span><span class="sxs-lookup"><span data-stu-id="f9a98-118">To set a common label and/or comment for selected functoids</span></span>  
 <span data-ttu-id="f9a98-119">La définition d'une étiquette commune et celle d'un commentaire commun pour les fonctoids sélectionnés représentent deux opérations atomiques distinctes,</span><span class="sxs-lookup"><span data-stu-id="f9a98-119">Setting a common label and setting a common comment for the selected functoids are two different atomic operations.</span></span> <span data-ttu-id="f9a98-120">que vous pouvez annuler ou rétablir sans le moindre problème.</span><span class="sxs-lookup"><span data-stu-id="f9a98-120">You can undo or redo these operations.</span></span>  
  
 <span data-ttu-id="f9a98-121">Pour définir une étiquette/un commentaire commun(e) pour les fonctoids sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="f9a98-121">To set a common label/comment for the selected functoids:</span></span>  
  
1.  <span data-ttu-id="f9a98-122">Sur la page de grille du mappeur, sélectionnez les fonctoids souhaités.</span><span class="sxs-lookup"><span data-stu-id="f9a98-122">On the Mapper grid page, select the desired functoids.</span></span>  
  
2.  <span data-ttu-id="f9a98-123">Dans le **propriétés** fenêtre, entrez une étiquette et/ou un commentaire dans le **étiquette** et **commentaires** propriétés.</span><span class="sxs-lookup"><span data-stu-id="f9a98-123">In the **Properties** window, enter a suitable label and/or comment in the **Label** and **Comments** properties.</span></span>  
  
## <a name="to-set-a-common-label-for-selected-functoids-and-links"></a><span data-ttu-id="f9a98-124">Définition d'une étiquette commune pour les liens et les fonctoids sélectionnés</span><span class="sxs-lookup"><span data-stu-id="f9a98-124">To set a common label for selected functoids and links</span></span>  
 <span data-ttu-id="f9a98-125">Vous pouvez définir une étiquette commune pour les liens et les fonctoids sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="f9a98-125">You can set a common label for the selected functoids and links.</span></span> <span data-ttu-id="f9a98-126">**Étiquette** est la seule propriété qui est commune aux fonctoids et liens.</span><span class="sxs-lookup"><span data-stu-id="f9a98-126">**Label** is the only property which is common to both functoids and links.</span></span> <span data-ttu-id="f9a98-127">Vous pouvez annuler ou rétablir cette opération.</span><span class="sxs-lookup"><span data-stu-id="f9a98-127">You can undo or redo this operation.</span></span>  
  
 <span data-ttu-id="f9a98-128">Pour définir une étiquette commune pour les liens et fonctoids sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="f9a98-128">To set a common label for the selected functoids and links:</span></span>  
  
1.  <span data-ttu-id="f9a98-129">Sur la page de grille du mappeur, sélectionnez les fonctoids et liens souhaités.</span><span class="sxs-lookup"><span data-stu-id="f9a98-129">On the Mapper grid page, select the desired functoids and links.</span></span>  
  
2.  <span data-ttu-id="f9a98-130">Dans le **propriétés** fenêtre, entrez une étiquette appropriée dans le **étiquette** propriété.</span><span class="sxs-lookup"><span data-stu-id="f9a98-130">In the **Properties** window, enter a suitable label in the **Label** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a98-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9a98-131">See Also</span></span>  
 [<span data-ttu-id="f9a98-132">À l’aide de liens pour spécifier l’enregistrement et les mappages de champs</span><span class="sxs-lookup"><span data-stu-id="f9a98-132">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)