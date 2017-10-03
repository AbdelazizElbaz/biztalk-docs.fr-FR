---
title: Compensation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compensations, errors
- compensations
- errors, compensations
- compensations, about compensations
- compensations, atomic transactions
- atomic transactions, compensations
- transactions, compensations
ms.assetid: 0a80dd16-fd35-4f45-95b7-52bb9df80cbb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c572638ea6212c3fb79e6b239aa8ffbe713c3c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="compensation"></a><span data-ttu-id="d238d-102">Compensation</span><span class="sxs-lookup"><span data-stu-id="d238d-102">Compensation</span></span>
<span data-ttu-id="d238d-103">Si une erreur se produit et que vous avez besoin d'annuler ou d'inverser les effets d'une transaction validée avec succès, vous pouvez le faire en ajoutant un code de compensation à votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="d238d-103">If an error occurs and you need to undo or reverse the effects of a successfully committed transaction, you can do so by adding compensation code to your orchestration.</span></span>  
  
 <span data-ttu-id="d238d-104">La compensation peut être appelée une fois toutes les actions de la transaction effectuées avec succès.</span><span class="sxs-lookup"><span data-stu-id="d238d-104">The compensation can be invoked after the transaction has completed its actions successfully.</span></span> <span data-ttu-id="d238d-105">À ce stade, l'état de l'orchestration est connu, et les informations relatives à cet état sont disponibles dans le code de la compensation, ce qui signifie que vous pouvez écrire un code qui agira de manière appropriée en fonction de l'état de l'orchestration lorsque la transaction est validée.</span><span class="sxs-lookup"><span data-stu-id="d238d-105">At that point, the state of the orchestration is known, and state information is available to the code in the compensation, which means that you can write code to act appropriately depending on the state of the orchestration when the transaction commits.</span></span>  
  
 <span data-ttu-id="d238d-106">Les compensations sont également possibles pour les transactions atomiques.</span><span class="sxs-lookup"><span data-stu-id="d238d-106">Compensations can also be provided on atomic transactions.</span></span> <span data-ttu-id="d238d-107">Ces compensations ne peuvent être appelées qu'une fois la transaction atomique validée.</span><span class="sxs-lookup"><span data-stu-id="d238d-107">These compensations can only be called after the atomic transaction commits.</span></span> <span data-ttu-id="d238d-108">Vous devez écrire un code pour annuler ou inverser le déroulement de l'exécution normale de la compensation.</span><span class="sxs-lookup"><span data-stu-id="d238d-108">You need to write code to undo or reverse the path of the normal execution in the compensation.</span></span>  
  
 <span data-ttu-id="d238d-109">Le bloc de compensation est flexible ; il peut contenir toute autre forme, y compris une autre étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="d238d-109">The compensation block is flexible; it can contain any other shape, including another transaction scope.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d238d-110">Vous ne pouvez utiliser une compensation qu'une seule fois par étendue.</span><span class="sxs-lookup"><span data-stu-id="d238d-110">You can do a compensation only once on a given scope.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d238d-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d238d-111">In This Section</span></span>  
  
-   [<span data-ttu-id="d238d-112">Comment configurer la forme compenser</span><span class="sxs-lookup"><span data-stu-id="d238d-112">How to Configure the Compensate Shape</span></span>](../core/how-to-configure-the-compensate-shape.md)  
  
-   [<span data-ttu-id="d238d-113">L’ajout d’une Compensation personnalisée à une Orchestration</span><span class="sxs-lookup"><span data-stu-id="d238d-113">How to Add Custom Compensation to an Orchestration</span></span>](../core/how-to-add-custom-compensation-to-an-orchestration.md)  
  
-   [<span data-ttu-id="d238d-114">L’ajout d’un bloc de Compensation</span><span class="sxs-lookup"><span data-stu-id="d238d-114">How to Add a Compensation Block</span></span>](../core/how-to-add-a-compensation-block.md)