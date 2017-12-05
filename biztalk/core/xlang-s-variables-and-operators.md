---
title: "Opérateurs et Variables XLANG-s | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02512789-2cb9-4ba9-aa78-e59b248e6b24
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c1773b7af3ec029026ee884e6c1161e27a3c330
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="xlang-s-variables-and-operators"></a><span data-ttu-id="1efca-102">Opérateurs et Variables XLANG-s</span><span class="sxs-lookup"><span data-stu-id="1efca-102">XLANG-s Variables and Operators</span></span>
<span data-ttu-id="1efca-103">Cette section traite des variables et opérateurs utilisés en langage XLANG/s.</span><span class="sxs-lookup"><span data-stu-id="1efca-103">This section discusses the variables and operators used in the XLANG/s language.</span></span>  
  
## <a name="xlangs-variables"></a><span data-ttu-id="1efca-104">Variables XLANG/s</span><span class="sxs-lookup"><span data-stu-id="1efca-104">XLANG/s Variables</span></span>  
 <span data-ttu-id="1efca-105">Les variables représentent des emplacements de stockage.</span><span class="sxs-lookup"><span data-stu-id="1efca-105">Variables represent storage locations.</span></span> <span data-ttu-id="1efca-106">Chaque variable a un certain type qui détermine les valeurs qu'elle peut stocker.</span><span class="sxs-lookup"><span data-stu-id="1efca-106">Every variable has a type that determines what values can be stored in that variable.</span></span> <span data-ttu-id="1efca-107">XLANG/s est de type sécurisé, et son compilateur garantit que le type des valeurs stockées dans les variables est toujours approprié.</span><span class="sxs-lookup"><span data-stu-id="1efca-107">XLANG/s is type-safe, and its compiler guarantees that values stored in variables are always of the appropriate type.</span></span> <span data-ttu-id="1efca-108">XLANG/s prend en charge les types de variables suivants :</span><span class="sxs-lookup"><span data-stu-id="1efca-108">XLANG/s supports the following variable types:</span></span>  
  
-   <span data-ttu-id="1efca-109">Messages</span><span class="sxs-lookup"><span data-stu-id="1efca-109">Messages</span></span>  
  
-   <span data-ttu-id="1efca-110">Ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="1efca-110">Correlation sets</span></span>  
  
-   <span data-ttu-id="1efca-111">Liens de service</span><span class="sxs-lookup"><span data-stu-id="1efca-111">Service links</span></span>  
  
-   <span data-ttu-id="1efca-112">Ports</span><span class="sxs-lookup"><span data-stu-id="1efca-112">Ports</span></span>  
  
-   <span data-ttu-id="1efca-113">Distinguent les types valeur intégrés : **booléenne**, **octets**, **Char**, **décimal**, **Double**,  **Int16**, **Int32**, **Int64**, **SByte**, **unique**, **chaîne**, **UInt16**, **UInt32**, et **UInt64**</span><span class="sxs-lookup"><span data-stu-id="1efca-113">Distinguished built-in value types: **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**</span></span>  
  
-   <span data-ttu-id="1efca-114">Objets</span><span class="sxs-lookup"><span data-stu-id="1efca-114">Objects</span></span>  
  
-   <span data-ttu-id="1efca-115">Types énumération</span><span class="sxs-lookup"><span data-stu-id="1efca-115">Enumeration types</span></span>  
  
 <span data-ttu-id="1efca-116">XLANG/s fournit une sémantique d'initialisation pour chacun des types ci-avant.</span><span class="sxs-lookup"><span data-stu-id="1efca-116">XLANG/s provides initialization semantics for each of the preceding types.</span></span> <span data-ttu-id="1efca-117">Cette initialisation peut être vue comme l'affectation d'une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="1efca-117">Such initialization can be viewed as an assignment to a variable of that type.</span></span> <span data-ttu-id="1efca-118">En langage XLANG/s, une variable doit être nettement affectée pour que sa valeur puisse être récupérée ou utilisée.</span><span class="sxs-lookup"><span data-stu-id="1efca-118">In XLANG/s, a variable must be definitely assigned before its value can be obtained or used.</span></span>  
  
## <a name="xlangs-operators"></a><span data-ttu-id="1efca-119">Opérateurs XLANG/s</span><span class="sxs-lookup"><span data-stu-id="1efca-119">XLANG/s Operators</span></span>  
 <span data-ttu-id="1efca-120">XLANG/s prend en charge les opérateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="1efca-120">XLANG/s supports the following operators.</span></span> <span data-ttu-id="1efca-121">Ils sont strictement conformes à la fonction des opérateurs correspondants en C#.</span><span class="sxs-lookup"><span data-stu-id="1efca-121">They adhere closely to the functionality of the corresponding operators in C#.</span></span>  
  
|<span data-ttu-id="1efca-122">Opérateur</span><span class="sxs-lookup"><span data-stu-id="1efca-122">Operator</span></span>|<span data-ttu-id="1efca-123"> Description</span><span class="sxs-lookup"><span data-stu-id="1efca-123">Description</span></span>|<span data-ttu-id="1efca-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="1efca-124">Example</span></span>|  
|--------------|-----------------|-------------|  
|<span data-ttu-id="1efca-125">checked</span><span class="sxs-lookup"><span data-stu-id="1efca-125">checked</span></span>|<span data-ttu-id="1efca-126">Signale une erreur de dépassement arithmétique positif</span><span class="sxs-lookup"><span data-stu-id="1efca-126">Raises error on arithmetic overflow</span></span>|<span data-ttu-id="1efca-127">checked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="1efca-127">checked(x = y * 1000)</span></span>|  
|<span data-ttu-id="1efca-128">unchecked</span><span class="sxs-lookup"><span data-stu-id="1efca-128">unchecked</span></span>|<span data-ttu-id="1efca-129">Ignore l'erreur de dépassement arithmétique positif</span><span class="sxs-lookup"><span data-stu-id="1efca-129">Ignores arithmetic overflow</span></span>|<span data-ttu-id="1efca-130">unchecked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="1efca-130">unchecked(x = y * 1000)</span></span>|  
|<span data-ttu-id="1efca-131">new</span><span class="sxs-lookup"><span data-stu-id="1efca-131">new</span></span>|<span data-ttu-id="1efca-132">Crée une instance d'une classe</span><span class="sxs-lookup"><span data-stu-id="1efca-132">Creates an instance of a class</span></span>|<span data-ttu-id="1efca-133">myObject = new MyClass;</span><span class="sxs-lookup"><span data-stu-id="1efca-133">myObject = new MyClass;</span></span>|  
|<span data-ttu-id="1efca-134">typeof</span><span class="sxs-lookup"><span data-stu-id="1efca-134">typeof</span></span>|<span data-ttu-id="1efca-135">Extrait un type</span><span class="sxs-lookup"><span data-stu-id="1efca-135">Retrieves a type</span></span>|<span data-ttu-id="1efca-136">myMapType = typeof(myMap)</span><span class="sxs-lookup"><span data-stu-id="1efca-136">myMapType = typeof(myMap)</span></span>|  
|<span data-ttu-id="1efca-137">succeeded</span><span class="sxs-lookup"><span data-stu-id="1efca-137">succeeded</span></span>|<span data-ttu-id="1efca-138">Tests de réussite d'étendue transactionnelle ou d'orchestration</span><span class="sxs-lookup"><span data-stu-id="1efca-138">Tests for successful completion of transactional scope or orchestration</span></span>|<span data-ttu-id="1efca-139">a réussi (\<ID de transaction enfant de l’étendue actuelle ou service\>)</span><span class="sxs-lookup"><span data-stu-id="1efca-139">succeeded(\<transaction ID for child transaction of current scope or service\>)</span></span>|  
|<span data-ttu-id="1efca-140">existe</span><span class="sxs-lookup"><span data-stu-id="1efca-140">exists</span></span>|<span data-ttu-id="1efca-141">Vérifie l'existence d'une propriété de contexte de message</span><span class="sxs-lookup"><span data-stu-id="1efca-141">Tests for the existence of a message context property</span></span>|<span data-ttu-id="1efca-142">BTS.RetryCount exists Message_In</span><span class="sxs-lookup"><span data-stu-id="1efca-142">BTS.RetryCount exists Message_In</span></span>|  
|+|<span data-ttu-id="1efca-143">Plus unaire</span><span class="sxs-lookup"><span data-stu-id="1efca-143">Unary plus</span></span>|<span data-ttu-id="1efca-144">+(int x)</span><span class="sxs-lookup"><span data-stu-id="1efca-144">+(int x)</span></span>|  
|-|<span data-ttu-id="1efca-145">Moins unaire</span><span class="sxs-lookup"><span data-stu-id="1efca-145">Unary minus</span></span>|<span data-ttu-id="1efca-146">-(int x)</span><span class="sxs-lookup"><span data-stu-id="1efca-146">-(int x)</span></span>|  
|<span data-ttu-id="1efca-147">!</span><span class="sxs-lookup"><span data-stu-id="1efca-147">!</span></span>|<span data-ttu-id="1efca-148">Négation logique</span><span class="sxs-lookup"><span data-stu-id="1efca-148">Logical negation</span></span>|<span data-ttu-id="1efca-149">!myBool</span><span class="sxs-lookup"><span data-stu-id="1efca-149">!myBool</span></span>|  
|~|<span data-ttu-id="1efca-150">Complément de bits</span><span class="sxs-lookup"><span data-stu-id="1efca-150">Bitwise complement</span></span>|<span data-ttu-id="1efca-151">x = ~y</span><span class="sxs-lookup"><span data-stu-id="1efca-151">x = ~y</span></span>|  
|<span data-ttu-id="1efca-152">()</span><span class="sxs-lookup"><span data-stu-id="1efca-152">()</span></span>|<span data-ttu-id="1efca-153">Cast</span><span class="sxs-lookup"><span data-stu-id="1efca-153">Cast</span></span>|<span data-ttu-id="1efca-154">(bool) myInt</span><span class="sxs-lookup"><span data-stu-id="1efca-154">(bool) myInt</span></span>|  
|*|<span data-ttu-id="1efca-155">Multiplié</span><span class="sxs-lookup"><span data-stu-id="1efca-155">Times</span></span>|<span data-ttu-id="1efca-156">Poids = MyMsg.numOrders * 20</span><span class="sxs-lookup"><span data-stu-id="1efca-156">Weight = MyMsg.numOrders * 20</span></span>|  
|/|<span data-ttu-id="1efca-157">Divisé par</span><span class="sxs-lookup"><span data-stu-id="1efca-157">Divided by</span></span>|<span data-ttu-id="1efca-158">x / y</span><span class="sxs-lookup"><span data-stu-id="1efca-158">x / y</span></span>|  
|+|<span data-ttu-id="1efca-159">signe plus</span><span class="sxs-lookup"><span data-stu-id="1efca-159">Plus</span></span>|<span data-ttu-id="1efca-160">x + y</span><span class="sxs-lookup"><span data-stu-id="1efca-160">x + y</span></span>|  
|-|<span data-ttu-id="1efca-161">Moins</span><span class="sxs-lookup"><span data-stu-id="1efca-161">Minus</span></span>|<span data-ttu-id="1efca-162">x - y</span><span class="sxs-lookup"><span data-stu-id="1efca-162">x - y</span></span>|  
|<<|<span data-ttu-id="1efca-163">Décalage vers la gauche</span><span class="sxs-lookup"><span data-stu-id="1efca-163">Shift left</span></span>|<span data-ttu-id="1efca-164">x << 2</span><span class="sxs-lookup"><span data-stu-id="1efca-164">x << 2</span></span>|  
|>>|<span data-ttu-id="1efca-165">Décalage vers la droite</span><span class="sxs-lookup"><span data-stu-id="1efca-165">Shift right</span></span>|<span data-ttu-id="1efca-166">x >> 2</span><span class="sxs-lookup"><span data-stu-id="1efca-166">x >> 2</span></span>|  
|<|<span data-ttu-id="1efca-167">Inférieur à</span><span class="sxs-lookup"><span data-stu-id="1efca-167">Less than</span></span>|<span data-ttu-id="1efca-168">If (MyMsg.numOrders < 10)...</span><span class="sxs-lookup"><span data-stu-id="1efca-168">If (MyMsg.numOrders < 10)...</span></span>|  
|>|<span data-ttu-id="1efca-169">Supérieur à</span><span class="sxs-lookup"><span data-stu-id="1efca-169">Greater than</span></span>|<span data-ttu-id="1efca-170">Si (MyMsg.numOrders > 10)...</span><span class="sxs-lookup"><span data-stu-id="1efca-170">If (MyMsg.numOrders > 10)...</span></span>|  
|<=|<span data-ttu-id="1efca-171">Inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="1efca-171">Less than or equal to</span></span>|<span data-ttu-id="1efca-172">If (MyMsg.numOrders <= 10)...</span><span class="sxs-lookup"><span data-stu-id="1efca-172">If (MyMsg.numOrders <= 10)...</span></span>|  
|>=|<span data-ttu-id="1efca-173">Supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="1efca-173">Greater than or equal to</span></span>|<span data-ttu-id="1efca-174">Si (MyMsg.numOrders > = 10)...</span><span class="sxs-lookup"><span data-stu-id="1efca-174">If (MyMsg.numOrders >= 10)...</span></span>|  
|==|<span data-ttu-id="1efca-175">Égal à</span><span class="sxs-lookup"><span data-stu-id="1efca-175">Equal to</span></span>|<span data-ttu-id="1efca-176">If (MyMsg.numOrders == 10)...</span><span class="sxs-lookup"><span data-stu-id="1efca-176">If (MyMsg.numOrders == 10)...</span></span>|  
|<span data-ttu-id="1efca-177">!=</span><span class="sxs-lookup"><span data-stu-id="1efca-177">!=</span></span>|<span data-ttu-id="1efca-178">Différent de</span><span class="sxs-lookup"><span data-stu-id="1efca-178">Not equal to</span></span>|<span data-ttu-id="1efca-179">If (MyMsg.numOrders != 10)...</span><span class="sxs-lookup"><span data-stu-id="1efca-179">If (MyMsg.numOrders != 10)...</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1efca-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1efca-180">See Also</span></span>  
 <span data-ttu-id="1efca-181">[Types de données XLANG-s](../core/xlang-s-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1efca-181">[XLANG-s Data Types](../core/xlang-s-data-types.md) </span></span>  
 <span data-ttu-id="1efca-182">[Instructions XLANG-s](../core/xlang-s-statements.md) </span><span class="sxs-lookup"><span data-stu-id="1efca-182">[XLANG-s Statements](../core/xlang-s-statements.md) </span></span>  
 <span data-ttu-id="1efca-183">[Expressions XLANG-s](../core/xlang-s-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="1efca-183">[XLANG-s Expressions](../core/xlang-s-expressions.md) </span></span>  
 <span data-ttu-id="1efca-184">[Mots réservés XLANG-s](../core/xlang-s-reserved-words.md) </span><span class="sxs-lookup"><span data-stu-id="1efca-184">[XLANG-s Reserved Words](../core/xlang-s-reserved-words.md) </span></span>  
 [<span data-ttu-id="1efca-185">Conversions de types XLANG/s en BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="1efca-185">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)