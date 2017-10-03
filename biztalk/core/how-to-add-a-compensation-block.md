---
title: "L’ajout d’un bloc de Compensation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compensations, compensation blocks
- compensation blocks, adding
ms.assetid: 1bdeed92-3144-44ef-ad0d-1c6976f46a36
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dec4f4dd01c2bbf522dfff44ec8aaf0c2f5e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-compensation-block"></a><span data-ttu-id="a1112-102">Ajout d'un bloc de compensation</span><span class="sxs-lookup"><span data-stu-id="a1112-102">How to Add a Compensation Block</span></span>
<span data-ttu-id="a1112-103">Si vous n'ajoutez pas votre propre compensation, le moteur d'exécution effectue une compensation par défaut qui appelle les compensations de toutes les transactions imbriquées au sein de la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="a1112-103">If you do not add your own compensation, the runtime engine performs a default compensation that invokes the compensations of any nested transactions within the current transaction.</span></span> <span data-ttu-id="a1112-104">Il appelle d'abord la compensation de la transaction terminée la plus récente, puis remonte jusqu'à-ce que toutes les transactions imbriquées aient été compensées.</span><span class="sxs-lookup"><span data-stu-id="a1112-104">It first invokes the compensation of the most recently completed transaction, and works backward until all nested transactions have been compensated.</span></span>  
  
 <span data-ttu-id="a1112-105">Cela est vrai même lorsque votre compensation a lieu à l’intérieur d’une forme boucle : les compensations seront exécutées dans l’ordre inverse.</span><span class="sxs-lookup"><span data-stu-id="a1112-105">This holds true even when your compensation takes place inside a Loop shape: the compensations will be run in reverse order.</span></span> <span data-ttu-id="a1112-106">La compensation de la dernière itération de la boucle sera la première appelée, puis la compensation de l'itération précédente sera appelée, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="a1112-106">First, the compensation for the last iteration of the loop will be invoked, then the compensation for the previous iteration, and so on.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a1112-107">Vu que les données doivent être conservées dans la mémoire physique pour que la compensation fonctionne, l'utilisation de compensations dans une boucle peut affecter les performances, ce qui peut poser problème dans le cas d'un nombre important d'itérations.</span><span class="sxs-lookup"><span data-stu-id="a1112-107">Because data is persisted to physical memory for compensation to work, using compensations inside a loop might affect performance, which might be an issue given a large number of iterations.</span></span>  
  
 <span data-ttu-id="a1112-108">Si l'ordre par défaut ne convient pas à vos besoins, vous pouvez écrire votre propre gestionnaire de compensation qui appellera explicitement les gestionnaires de compensation des étendues imbriquées dans l'ordre de votre choix.</span><span class="sxs-lookup"><span data-stu-id="a1112-108">If the default ordering does not fit your requirements, you can write your own compensation handler to explicitly call the compensation handlers of the nested scopes in the order you specify.</span></span>  
  
### <a name="to-add-a-compensation-block"></a><span data-ttu-id="a1112-109">Pour ajouter un bloc de compensation</span><span class="sxs-lookup"><span data-stu-id="a1112-109">To add a Compensation Block</span></span>  
  
1.  <span data-ttu-id="a1112-110">Avec le bouton droit le **étendue** forme de la transaction à laquelle vous souhaitez ajouter un **bloc de Compensation**, puis cliquez sur **nouveau bloc de Compensation**.</span><span class="sxs-lookup"><span data-stu-id="a1112-110">Right-click the **Scope** shape for the transaction to which you want to add a **Compensation Block**, and then click **New Compensation Block**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1112-111">Pour ajouter un **bloc de Compensation** à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur **Atomique** ou **longue**.</span><span class="sxs-lookup"><span data-stu-id="a1112-111">To add a **Compensation Block** to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **Atomic** or **Long Running**.</span></span>  
  
     <span data-ttu-id="a1112-112">A **bloc de Compensation** est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="a1112-112">A **Compensation Block** is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="a1112-113">À l’intérieur de la **bloc de Compensation** forme, ajouter des formes pour créer le processus d’annulation d’une transaction validée.</span><span class="sxs-lookup"><span data-stu-id="a1112-113">Inside the **Compensation Block** shape, add shapes to create the process for undoing a committed transaction.</span></span>