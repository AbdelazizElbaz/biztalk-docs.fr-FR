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
ms.openlocfilehash: 1affe6ebdebac515782ec9ecb82b0c6085341bfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-variables-and-operators"></a><span data-ttu-id="8ad75-102">Opérateurs et Variables XLANG-s</span><span class="sxs-lookup"><span data-stu-id="8ad75-102">XLANG-s Variables and Operators</span></span>
<span data-ttu-id="8ad75-103">Cette section traite des variables et opérateurs utilisés en langage XLANG/s.</span><span class="sxs-lookup"><span data-stu-id="8ad75-103">This section discusses the variables and operators used in the XLANG/s language.</span></span>  
  
## <a name="xlangs-variables"></a><span data-ttu-id="8ad75-104">Variables XLANG/s</span><span class="sxs-lookup"><span data-stu-id="8ad75-104">XLANG/s Variables</span></span>  
 <span data-ttu-id="8ad75-105">Les variables représentent des emplacements de stockage.</span><span class="sxs-lookup"><span data-stu-id="8ad75-105">Variables represent storage locations.</span></span> <span data-ttu-id="8ad75-106">Chaque variable a un certain type qui détermine les valeurs qu'elle peut stocker.</span><span class="sxs-lookup"><span data-stu-id="8ad75-106">Every variable has a type that determines what values can be stored in that variable.</span></span> <span data-ttu-id="8ad75-107">XLANG/s est de type sécurisé, et son compilateur garantit que le type des valeurs stockées dans les variables est toujours approprié.</span><span class="sxs-lookup"><span data-stu-id="8ad75-107">XLANG/s is type-safe, and its compiler guarantees that values stored in variables are always of the appropriate type.</span></span> <span data-ttu-id="8ad75-108">XLANG/s prend en charge les types de variables suivants :</span><span class="sxs-lookup"><span data-stu-id="8ad75-108">XLANG/s supports the following variable types:</span></span>  
  
-   <span data-ttu-id="8ad75-109">Messages</span><span class="sxs-lookup"><span data-stu-id="8ad75-109">Messages</span></span>  
  
-   <span data-ttu-id="8ad75-110">Ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="8ad75-110">Correlation sets</span></span>  
  
-   <span data-ttu-id="8ad75-111">Liens de service</span><span class="sxs-lookup"><span data-stu-id="8ad75-111">Service links</span></span>  
  
-   <span data-ttu-id="8ad75-112">Ports</span><span class="sxs-lookup"><span data-stu-id="8ad75-112">Ports</span></span>  
  
-   <span data-ttu-id="8ad75-113">Distinguent les types valeur intégrés : **booléenne**, **octets**, **Char**, **décimal**, **Double**,  **Int16**, **Int32**, **Int64**, **SByte**, **unique**, **chaîne**, **UInt16**, **UInt32**, et **UInt64**</span><span class="sxs-lookup"><span data-stu-id="8ad75-113">Distinguished built-in value types: **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**</span></span>  
  
-   <span data-ttu-id="8ad75-114">Objets</span><span class="sxs-lookup"><span data-stu-id="8ad75-114">Objects</span></span>  
  
-   <span data-ttu-id="8ad75-115">Types énumération</span><span class="sxs-lookup"><span data-stu-id="8ad75-115">Enumeration types</span></span>  
  
 <span data-ttu-id="8ad75-116">XLANG/s fournit une sémantique d'initialisation pour chacun des types ci-avant.</span><span class="sxs-lookup"><span data-stu-id="8ad75-116">XLANG/s provides initialization semantics for each of the preceding types.</span></span> <span data-ttu-id="8ad75-117">Cette initialisation peut être vue comme l'affectation d'une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="8ad75-117">Such initialization can be viewed as an assignment to a variable of that type.</span></span> <span data-ttu-id="8ad75-118">En langage XLANG/s, une variable doit être nettement affectée pour que sa valeur puisse être récupérée ou utilisée.</span><span class="sxs-lookup"><span data-stu-id="8ad75-118">In XLANG/s, a variable must be definitely assigned before its value can be obtained or used.</span></span>  
  
## <a name="xlangs-operators"></a><span data-ttu-id="8ad75-119">Opérateurs XLANG/s</span><span class="sxs-lookup"><span data-stu-id="8ad75-119">XLANG/s Operators</span></span>  
 <span data-ttu-id="8ad75-120">XLANG/s prend en charge les opérateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="8ad75-120">XLANG/s supports the following operators.</span></span> <span data-ttu-id="8ad75-121">Ils sont strictement conformes à la fonction des opérateurs correspondants en C#.</span><span class="sxs-lookup"><span data-stu-id="8ad75-121">They adhere closely to the functionality of the corresponding operators in C#.</span></span>  
  
|<span data-ttu-id="8ad75-122">Opérateur</span><span class="sxs-lookup"><span data-stu-id="8ad75-122">Operator</span></span>|<span data-ttu-id="8ad75-123"> Description</span><span class="sxs-lookup"><span data-stu-id="8ad75-123">Description</span></span>|<span data-ttu-id="8ad75-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ad75-124">Example</span></span>|  
|--------------|-----------------|-------------|  
|<span data-ttu-id="8ad75-125">checked</span><span class="sxs-lookup"><span data-stu-id="8ad75-125">checked</span></span>|<span data-ttu-id="8ad75-126">Signale une erreur de dépassement arithmétique positif</span><span class="sxs-lookup"><span data-stu-id="8ad75-126">Raises error on arithmetic overflow</span></span>|<span data-ttu-id="8ad75-127">checked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="8ad75-127">checked(x = y * 1000)</span></span>|  
|<span data-ttu-id="8ad75-128">unchecked</span><span class="sxs-lookup"><span data-stu-id="8ad75-128">unchecked</span></span>|<span data-ttu-id="8ad75-129">Ignore l'erreur de dépassement arithmétique positif</span><span class="sxs-lookup"><span data-stu-id="8ad75-129">Ignores arithmetic overflow</span></span>|<span data-ttu-id="8ad75-130">unchecked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="8ad75-130">unchecked(x = y * 1000)</span></span>|  
|<span data-ttu-id="8ad75-131">new</span><span class="sxs-lookup"><span data-stu-id="8ad75-131">new</span></span>|<span data-ttu-id="8ad75-132">Crée une instance d'une classe</span><span class="sxs-lookup"><span data-stu-id="8ad75-132">Creates an instance of a class</span></span>|<span data-ttu-id="8ad75-133">myObject = new MyClass;</span><span class="sxs-lookup"><span data-stu-id="8ad75-133">myObject = new MyClass;</span></span>|  
|<span data-ttu-id="8ad75-134">typeof</span><span class="sxs-lookup"><span data-stu-id="8ad75-134">typeof</span></span>|<span data-ttu-id="8ad75-135">Extrait un type</span><span class="sxs-lookup"><span data-stu-id="8ad75-135">Retrieves a type</span></span>|<span data-ttu-id="8ad75-136">myMapType = typeof(myMap)</span><span class="sxs-lookup"><span data-stu-id="8ad75-136">myMapType = typeof(myMap)</span></span>|  
|<span data-ttu-id="8ad75-137">succeeded</span><span class="sxs-lookup"><span data-stu-id="8ad75-137">succeeded</span></span>|<span data-ttu-id="8ad75-138">Tests de réussite d'étendue transactionnelle ou d'orchestration</span><span class="sxs-lookup"><span data-stu-id="8ad75-138">Tests for successful completion of transactional scope or orchestration</span></span>|<span data-ttu-id="8ad75-139">a réussi (\<ID de transaction enfant de l’étendue actuelle ou de service >)</span><span class="sxs-lookup"><span data-stu-id="8ad75-139">succeeded(\<transaction ID for child transaction of current scope or service>)</span></span>|  
|<span data-ttu-id="8ad75-140">existe</span><span class="sxs-lookup"><span data-stu-id="8ad75-140">exists</span></span>|<span data-ttu-id="8ad75-141">Vérifie l'existence d'une propriété de contexte de message</span><span class="sxs-lookup"><span data-stu-id="8ad75-141">Tests for the existence of a message context property</span></span>|<span data-ttu-id="8ad75-142">BTS.RetryCount exists Message_In</span><span class="sxs-lookup"><span data-stu-id="8ad75-142">BTS.RetryCount exists Message_In</span></span>|  
|+|<span data-ttu-id="8ad75-143">Plus unaire</span><span class="sxs-lookup"><span data-stu-id="8ad75-143">Unary plus</span></span>|<span data-ttu-id="8ad75-144">+(int x)</span><span class="sxs-lookup"><span data-stu-id="8ad75-144">+(int x)</span></span>|  
|-|<span data-ttu-id="8ad75-145">Moins unaire</span><span class="sxs-lookup"><span data-stu-id="8ad75-145">Unary minus</span></span>|<span data-ttu-id="8ad75-146">-(int x)</span><span class="sxs-lookup"><span data-stu-id="8ad75-146">-(int x)</span></span>|  
|<span data-ttu-id="8ad75-147">!</span><span class="sxs-lookup"><span data-stu-id="8ad75-147">!</span></span>|<span data-ttu-id="8ad75-148">Négation logique</span><span class="sxs-lookup"><span data-stu-id="8ad75-148">Logical negation</span></span>|<span data-ttu-id="8ad75-149">!myBool</span><span class="sxs-lookup"><span data-stu-id="8ad75-149">!myBool</span></span>|  
|~|<span data-ttu-id="8ad75-150">Complément de bits</span><span class="sxs-lookup"><span data-stu-id="8ad75-150">Bitwise complement</span></span>|<span data-ttu-id="8ad75-151">x = ~y</span><span class="sxs-lookup"><span data-stu-id="8ad75-151">x = ~y</span></span>|  
|<span data-ttu-id="8ad75-152">()</span><span class="sxs-lookup"><span data-stu-id="8ad75-152">()</span></span>|<span data-ttu-id="8ad75-153">Cast</span><span class="sxs-lookup"><span data-stu-id="8ad75-153">Cast</span></span>|<span data-ttu-id="8ad75-154">(bool) myInt</span><span class="sxs-lookup"><span data-stu-id="8ad75-154">(bool) myInt</span></span>|  
|*|<span data-ttu-id="8ad75-155">Multiplié</span><span class="sxs-lookup"><span data-stu-id="8ad75-155">Times</span></span>|<span data-ttu-id="8ad75-156">Poids = MyMsg.numOrders * 20</span><span class="sxs-lookup"><span data-stu-id="8ad75-156">Weight = MyMsg.numOrders * 20</span></span>|  
|/|<span data-ttu-id="8ad75-157">Divisé par</span><span class="sxs-lookup"><span data-stu-id="8ad75-157">Divided by</span></span>|<span data-ttu-id="8ad75-158">x / y</span><span class="sxs-lookup"><span data-stu-id="8ad75-158">x / y</span></span>|  
|+|<span data-ttu-id="8ad75-159">signe plus</span><span class="sxs-lookup"><span data-stu-id="8ad75-159">Plus</span></span>|<span data-ttu-id="8ad75-160">x + y</span><span class="sxs-lookup"><span data-stu-id="8ad75-160">x + y</span></span>|  
|-|<span data-ttu-id="8ad75-161">Moins</span><span class="sxs-lookup"><span data-stu-id="8ad75-161">Minus</span></span>|<span data-ttu-id="8ad75-162">x - y</span><span class="sxs-lookup"><span data-stu-id="8ad75-162">x - y</span></span>|  
|<<|<span data-ttu-id="8ad75-163">Décalage vers la gauche</span><span class="sxs-lookup"><span data-stu-id="8ad75-163">Shift left</span></span>|<span data-ttu-id="8ad75-164">x <\< 2</span><span class="sxs-lookup"><span data-stu-id="8ad75-164">x <\< 2</span></span>|  
|>>|<span data-ttu-id="8ad75-165">Décalage vers la droite</span><span class="sxs-lookup"><span data-stu-id="8ad75-165">Shift right</span></span>|<span data-ttu-id="8ad75-166">x >> 2</span><span class="sxs-lookup"><span data-stu-id="8ad75-166">x >> 2</span></span>|  
|<|<span data-ttu-id="8ad75-167">Inférieur à</span><span class="sxs-lookup"><span data-stu-id="8ad75-167">Less than</span></span>|<span data-ttu-id="8ad75-168">Si (MyMsg.numOrders \< 10)...</span><span class="sxs-lookup"><span data-stu-id="8ad75-168">If (MyMsg.numOrders \< 10)...</span></span>|  
|>|<span data-ttu-id="8ad75-169">Supérieur à</span><span class="sxs-lookup"><span data-stu-id="8ad75-169">Greater than</span></span>|<span data-ttu-id="8ad75-170">Si (MyMsg.numOrders > 10)...</span><span class="sxs-lookup"><span data-stu-id="8ad75-170">If (MyMsg.numOrders > 10)...</span></span>|  
|<=|<span data-ttu-id="8ad75-171">Inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="8ad75-171">Less than or equal to</span></span>|<span data-ttu-id="8ad75-172">Si (MyMsg.numOrders \<= 10)...</span><span class="sxs-lookup"><span data-stu-id="8ad75-172">If (MyMsg.numOrders \<= 10)...</span></span>|  
|>=|<span data-ttu-id="8ad75-173">Supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="8ad75-173">Greater than or equal to</span></span>|<span data-ttu-id="8ad75-174">Si (MyMsg.numOrders > = 10)...</span><span class="sxs-lookup"><span data-stu-id="8ad75-174">If (MyMsg.numOrders >= 10)...</span></span>|  
|==|<span data-ttu-id="8ad75-175">Égal à</span><span class="sxs-lookup"><span data-stu-id="8ad75-175">Equal to</span></span>|<span data-ttu-id="8ad75-176">If (MyMsg.numOrders == 10)...</span><span class="sxs-lookup"><span data-stu-id="8ad75-176">If (MyMsg.numOrders == 10)...</span></span>|  
|<span data-ttu-id="8ad75-177">!=</span><span class="sxs-lookup"><span data-stu-id="8ad75-177">!=</span></span>|<span data-ttu-id="8ad75-178">Différent de</span><span class="sxs-lookup"><span data-stu-id="8ad75-178">Not equal to</span></span>|<span data-ttu-id="8ad75-179">If (MyMsg.numOrders != 10)...</span><span class="sxs-lookup"><span data-stu-id="8ad75-179">If (MyMsg.numOrders != 10)...</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ad75-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad75-180">See Also</span></span>  
 <span data-ttu-id="8ad75-181">[Types de données XLANG-s](../core/xlang-s-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="8ad75-181">[XLANG-s Data Types](../core/xlang-s-data-types.md) </span></span>  
 <span data-ttu-id="8ad75-182">[Instructions XLANG-s](../core/xlang-s-statements.md) </span><span class="sxs-lookup"><span data-stu-id="8ad75-182">[XLANG-s Statements](../core/xlang-s-statements.md) </span></span>  
 <span data-ttu-id="8ad75-183">[Expressions XLANG-s](../core/xlang-s-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="8ad75-183">[XLANG-s Expressions](../core/xlang-s-expressions.md) </span></span>  
 <span data-ttu-id="8ad75-184">[Mots réservés XLANG-s](../core/xlang-s-reserved-words.md) </span><span class="sxs-lookup"><span data-stu-id="8ad75-184">[XLANG-s Reserved Words](../core/xlang-s-reserved-words.md) </span></span>  
 [<span data-ttu-id="8ad75-185">XLANG-s pour les Conversions de Type BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="8ad75-185">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)