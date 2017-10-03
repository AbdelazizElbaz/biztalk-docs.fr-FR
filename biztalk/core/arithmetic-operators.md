---
title: "Opérateurs arithmétiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d73e153c-aac1-4cea-92d8-af4a1bea6e6a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b3d66a990437929176835228efa1a74a5fa8683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="arithmetic-operators"></a><span data-ttu-id="7b288-102">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="7b288-102">Arithmetic Operators</span></span>
<span data-ttu-id="7b288-103">L'infrastructure des règles d'entreprise prend en charge l'utilisation des opérateurs d'addition, de soustraction, de multiplication, de division et de reste (modulo) lors de la création des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7b288-103">The Business Rules Framework supports using the addition, subtraction, multiplication, division, and remainder (modulo) operators in creating business rules.</span></span> <span data-ttu-id="7b288-104">Le tableau suivant décrit ces opérateurs arithmétiques.</span><span class="sxs-lookup"><span data-stu-id="7b288-104">The following table describes the arithmetic operators.</span></span>  
  
|<span data-ttu-id="7b288-105">Opérateur arithmétique</span><span class="sxs-lookup"><span data-stu-id="7b288-105">Arithmetic operator</span></span>|<span data-ttu-id="7b288-106"> Description</span><span class="sxs-lookup"><span data-stu-id="7b288-106">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="7b288-107">**Ajouter**</span><span class="sxs-lookup"><span data-stu-id="7b288-107">**Add**</span></span>|<span data-ttu-id="7b288-108">Représente l'opérateur d'addition (arg1 ajouté à arg2).</span><span class="sxs-lookup"><span data-stu-id="7b288-108">Represents the addition operator (arg1 added to arg2).</span></span>|  
|<span data-ttu-id="7b288-109">**Soustraction**</span><span class="sxs-lookup"><span data-stu-id="7b288-109">**Subtract**</span></span>|<span data-ttu-id="7b288-110">Représente l'opérateur de soustraction (arg1 soustrait de arg2).</span><span class="sxs-lookup"><span data-stu-id="7b288-110">Represents the subtraction operator (arg1 subtracted from arg2).</span></span>|  
|<span data-ttu-id="7b288-111">**Multiplier**</span><span class="sxs-lookup"><span data-stu-id="7b288-111">**Multiply**</span></span>|<span data-ttu-id="7b288-112">Représente l'opérateur de multiplication (arg1 multiplié par arg2).</span><span class="sxs-lookup"><span data-stu-id="7b288-112">Represents the multiplication operator (arg1 multiplied by arg2).</span></span>|  
|<span data-ttu-id="7b288-113">**Divide**</span><span class="sxs-lookup"><span data-stu-id="7b288-113">**Divide**</span></span>|<span data-ttu-id="7b288-114">Représente l'opérateur de division (arg1 divisé par arg2).</span><span class="sxs-lookup"><span data-stu-id="7b288-114">Represents the division operator (arg1 divided by arg2).</span></span>|  
|<span data-ttu-id="7b288-115">**Reste**</span><span class="sxs-lookup"><span data-stu-id="7b288-115">**Remainder**</span></span>|<span data-ttu-id="7b288-116">Représente l'opérateur de reste (arg1 modulo arg2).</span><span class="sxs-lookup"><span data-stu-id="7b288-116">Represents the remainder operator (arg1 modulo arg2).</span></span>|  
  
 <span data-ttu-id="7b288-117">Lorsque les opérandes sont de types différents, la promotion numérique automatique a lieu avec la conversion du plus petit type d'opérande en le plus grand type d'opérande.</span><span class="sxs-lookup"><span data-stu-id="7b288-117">When operands are of different types, automatic numeric promotion occurs with the smaller operand type being converted to the larger operand type.</span></span> <span data-ttu-id="7b288-118">Par exemple, si le **ajouter** opérateur est utilisé avec le premier opérande de **int** type et le deuxième opérande de **long** type, le type du premier opérande est converti en **long** avant d’effectuer la **ajouter** opération.</span><span class="sxs-lookup"><span data-stu-id="7b288-118">For example, if the **Add** operator is used with the first operand of **int** type and the second operand of **long** type, the type of the first operand is converted to **long** before performing the **Add** operation.</span></span> <span data-ttu-id="7b288-119">Le moteur de règles prend également en charge la double promotion si les deux opérandes peuvent être promus vers un type commun.</span><span class="sxs-lookup"><span data-stu-id="7b288-119">The rule engine also supports double promotion if both the operands can be promoted to a common type.</span></span> <span data-ttu-id="7b288-120">Par exemple, si le **ajouter** opérateur est utilisé avec le premier opérande de **int** type et le deuxième opérande de **uint** type, les types des deux opérandes sont convertis en **long** avant d’effectuer la **ajouter** opération.</span><span class="sxs-lookup"><span data-stu-id="7b288-120">For example, if the **Add** operator is used with the first operand of **int** type and the second operand of **uint** type, the types of both operands are converted to **long** before performing the **Add** operation.</span></span>  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a><span data-ttu-id="7b288-121">Pour utiliser un opérateur logique dans une règle d'entreprise</span><span class="sxs-lookup"><span data-stu-id="7b288-121">To use a logical operator in a business rule</span></span>  
 <span data-ttu-id="7b288-122">Procédez comme suit pour utiliser un opérateur logique dans une règle d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7b288-122">Use the following procedure to use a logical operator in a business rule.</span></span>  
  
1.  <span data-ttu-id="7b288-123">Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.</span><span class="sxs-lookup"><span data-stu-id="7b288-123">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
2.  <span data-ttu-id="7b288-124">Développez **vocabulaires**, développez **fonctions**, développez **Version 1.0 - publiée**, puis faites glisser le **ajouter/soustraire/Multiplier/diviser/reste** au volet Conditions/Actions du volet.</span><span class="sxs-lookup"><span data-stu-id="7b288-124">Expand **Vocabularies**, expand **Functions**, expand **Version 1.0 - Published**, and then drag the **Add/Subtract/Multiply/Divide/Remainder** to the Conditions pane/Actions pane.</span></span>  
  
3.  <span data-ttu-id="7b288-125">Spécifiez les valeurs des opérateurs de gauche et de droite.</span><span class="sxs-lookup"><span data-stu-id="7b288-125">Specify values for left and right operators.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b288-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b288-126">See Also</span></span>  
 [<span data-ttu-id="7b288-127">Opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="7b288-127">Logical Operators</span></span>](../core/logical-operators.md)