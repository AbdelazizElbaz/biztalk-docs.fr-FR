---
title: "Exemples de sortie de Trace de Test de stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, policies
- policies, testing
- testing, examples
ms.assetid: 92e1dc7f-1a8d-41a5-84b6-46d5ad9f2ef2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3678769dffa03bb77c3e86fef02998a354b1fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="policy-test-trace-output-examples"></a><span data-ttu-id="eae6a-102">Exemples de résultat du suivi du test de stratégies</span><span class="sxs-lookup"><span data-stu-id="eae6a-102">Policy Test Trace Output Examples</span></span>
<span data-ttu-id="eae6a-103">Cette section contient des exemples de résultat du test de stratégies pour différents types de faits.</span><span class="sxs-lookup"><span data-stu-id="eae6a-103">This section contains examples of the policy test output for different types of facts.</span></span>  
  
## <a name="net-class"></a><span data-ttu-id="eae6a-104">Classe .Net</span><span class="sxs-lookup"><span data-stu-id="eae6a-104">.Net Class</span></span>  
 <span data-ttu-id="eae6a-105">Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :</span><span class="sxs-lookup"><span data-stu-id="eae6a-105">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF test.get_ID > 0  
THEN <do something>  
```  
  
 <span data-ttu-id="eae6a-106">**Sortie :**</span><span class="sxs-lookup"><span data-stu-id="eae6a-106">**Output:**</span></span>  
  
 <span data-ttu-id="eae6a-107">TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/16/2004 9:50:28 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-107">RULE ENGINE TRACE for RULESET: LoanProcessing 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="eae6a-108">ACTIVITÉ DES FAITS 3/16/2004 9:50:28 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-108">FACT ACTIVITY 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="eae6a-109">Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="eae6a-109">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="eae6a-110">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-110">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-111">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-111">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-112">Type d’objet : MyTest.test</span><span class="sxs-lookup"><span data-stu-id="eae6a-112">Object Type: MyTest.test</span></span>  
  
 <span data-ttu-id="eae6a-113">Identificateur de l’Instance de l’objet : 872</span><span class="sxs-lookup"><span data-stu-id="eae6a-113">Object Instance Identifier: 872</span></span>  
  
 <span data-ttu-id="eae6a-114">TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/16/2004 9:50:28 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-114">CONDITION EVALUATION TEST (MATCH) 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="eae6a-115">Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="eae6a-115">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="eae6a-116">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-116">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-117">Expression de test : MyTest.test.get_ID > 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-117">Test Expression: MyTest.test.get_ID > 0</span></span>  
  
 <span data-ttu-id="eae6a-118">Valeur de l’opérande gauche : 100</span><span class="sxs-lookup"><span data-stu-id="eae6a-118">Left Operand Value: 100</span></span>  
  
 <span data-ttu-id="eae6a-119">Valeur de l’opérande droite : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-119">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="eae6a-120">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-120">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-121">METTRE À JOUR DE AGENDA 3/16/2004 9:50:28 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-121">AGENDA UPDATE 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="eae6a-122">Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="eae6a-122">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="eae6a-123">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-123">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-124">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-124">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-125">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-125">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-126">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-126">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-127">RÈGLE DÉCLENCHÉE 3/16/2004 9:50:28 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-127">RULE FIRED 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="eae6a-128">Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="eae6a-128">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="eae6a-129">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-129">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-130">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-130">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-131">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-131">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-132">ACTIVITÉ DES FAITS 3/16/2004 9:50:28 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-132">FACT ACTIVITY 3/16/2004 9:50:28 AM</span></span>  
  
 <span data-ttu-id="eae6a-133">Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7</span><span class="sxs-lookup"><span data-stu-id="eae6a-133">Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7</span></span>  
  
 <span data-ttu-id="eae6a-134">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-134">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-135">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-135">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-136">Type d’objet : MyTest.test</span><span class="sxs-lookup"><span data-stu-id="eae6a-136">Object Type: MyTest.test</span></span>  
  
 <span data-ttu-id="eae6a-137">Identificateur de l’Instance de l’objet : 872</span><span class="sxs-lookup"><span data-stu-id="eae6a-137">Object Instance Identifier: 872</span></span>  
  
## <a name="dataconnectiontypeddatarow"></a><span data-ttu-id="eae6a-138">DataConnection/TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="eae6a-138">DataConnection/TypedDataRow</span></span>  
 <span data-ttu-id="eae6a-139">Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :</span><span class="sxs-lookup"><span data-stu-id="eae6a-139">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 <span data-ttu-id="eae6a-140">**Sortie :**</span><span class="sxs-lookup"><span data-stu-id="eae6a-140">**Output:**</span></span>  
  
 <span data-ttu-id="eae6a-141">TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/16/2004 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-141">RULE ENGINE TRACE for RULESET: LoanProcessing 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-142">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-142">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-143">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-143">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-144">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-144">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-145">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-145">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-146">Type d’objet : DataConnection:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-146">Object Type: DataConnection:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-147">Identificateur de l’Instance de l’objet : 874</span><span class="sxs-lookup"><span data-stu-id="eae6a-147">Object Instance Identifier: 874</span></span>  
  
 <span data-ttu-id="eae6a-148">TEST D'ÉVALUATION DE LA CONDITION (CORRESPONDANCE) 3/16/2004 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-148">CONDITION EVALUATION TEST (MATCH) 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-149">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-149">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-150">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-150">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-151">Expression de test : sélectionnez * à partir de [CustInfo] où [CreditCardBalance] > 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-151">Test Expression: select * from [CustInfo] where [CreditCardBalance] > 0</span></span>  
  
 <span data-ttu-id="eae6a-152">Valeur de l'opérande gauche :</span><span class="sxs-lookup"><span data-stu-id="eae6a-152">Left Operand Value:</span></span>  
  
 <span data-ttu-id="eae6a-153">Valeur de l'opérande droit :</span><span class="sxs-lookup"><span data-stu-id="eae6a-153">Right Operand Value:</span></span>  
  
 <span data-ttu-id="eae6a-154">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-154">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-155">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-155">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-156">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-156">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-157">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-157">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-158">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-158">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-159">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-159">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-160">Identificateur de l’Instance de l’objet : 177556</span><span class="sxs-lookup"><span data-stu-id="eae6a-160">Object Instance Identifier: 177556</span></span>  
  
 <span data-ttu-id="eae6a-161">MISE À JOUR DE L'AGENDA 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-161">AGENDA UPDATE 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-162">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-162">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-163">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-163">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-164">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-164">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-165">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-165">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-166">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-166">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-167">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-167">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-168">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-168">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-169">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-169">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-170">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-170">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-171">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-171">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-172">Identificateur de l’Instance de l’objet : 177559</span><span class="sxs-lookup"><span data-stu-id="eae6a-172">Object Instance Identifier: 177559</span></span>  
  
 <span data-ttu-id="eae6a-173">MISE À JOUR DE L'AGENDA 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-173">AGENDA UPDATE 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-174">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-174">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-175">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-175">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-176">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-176">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-177">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-177">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-178">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-178">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-179">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-179">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-180">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-180">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-181">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-181">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-182">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-182">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-183">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-183">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-184">Identificateur de l’Instance de l’objet : 177558</span><span class="sxs-lookup"><span data-stu-id="eae6a-184">Object Instance Identifier: 177558</span></span>  
  
 <span data-ttu-id="eae6a-185">MISE À JOUR DE L'AGENDA 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-185">AGENDA UPDATE 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-186">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-186">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-187">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-187">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-188">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-188">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-189">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-189">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-190">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-190">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-191">RÈGLE DÉCLENCHÉE 3/16/2004 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-191">RULE FIRED 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-192">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-192">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-193">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-193">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-194">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-194">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-195">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-195">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-196">RÈGLE DÉCLENCHÉE 3/16/2004 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-196">RULE FIRED 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-197">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-197">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-198">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-198">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-199">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-199">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-200">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-200">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-201">RÈGLE DÉCLENCHÉE 3/16/2004 8:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-201">RULE FIRED 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-202">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-202">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-203">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-203">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-204">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-204">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-205">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-205">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-206">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-206">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-207">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-207">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-208">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-208">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-209">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-209">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-210">Type d’objet : DataConnection:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-210">Object Type: DataConnection:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-211">Identificateur de l’Instance de l’objet : 874</span><span class="sxs-lookup"><span data-stu-id="eae6a-211">Object Instance Identifier: 874</span></span>  
  
 <span data-ttu-id="eae6a-212">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-212">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-213">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-213">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-214">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-214">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-215">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-215">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-216">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-216">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-217">Identificateur de l’Instance de l’objet : 177559</span><span class="sxs-lookup"><span data-stu-id="eae6a-217">Object Instance Identifier: 177559</span></span>  
  
 <span data-ttu-id="eae6a-218">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-218">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-219">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-219">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-220">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-220">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-221">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-221">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-222">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-222">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-223">Identificateur de l’Instance de l’objet : 177558</span><span class="sxs-lookup"><span data-stu-id="eae6a-223">Object Instance Identifier: 177558</span></span>  
  
 <span data-ttu-id="eae6a-224">ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-224">FACT ACTIVITY 3/16/2004 8:30:16 AM</span></span>  
  
 <span data-ttu-id="eae6a-225">Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span><span class="sxs-lookup"><span data-stu-id="eae6a-225">Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83</span></span>  
  
 <span data-ttu-id="eae6a-226">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-226">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-227">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-227">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-228">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-228">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-229">Identificateur de l’Instance de l’objet : 177556</span><span class="sxs-lookup"><span data-stu-id="eae6a-229">Object Instance Identifier: 177556</span></span>  
  
 <span data-ttu-id="eae6a-230">L'exemple ci-dessous indique que trois lignes de la table CustInfo ont satisfait à la condition de la règle.</span><span class="sxs-lookup"><span data-stu-id="eae6a-230">The example above indicates that three rows in the CustInfo table met the condition in the rule.</span></span>  <span data-ttu-id="eae6a-231">Cela a entraîné la déclaration de trois TypedDataRows uniques dans le moteur ainsi qu'une mise à jour de l'agenda et un déclenchement de règle pour chaque instance.</span><span class="sxs-lookup"><span data-stu-id="eae6a-231">This caused three unique TypedDataRows to be asserted into the engine and an agenda update and rule firing to occur for each instance.</span></span>  
  
## <a name="typedatatabletypeddatarow"></a><span data-ttu-id="eae6a-232">TypeDataTable/TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="eae6a-232">TypeDataTable/TypedDataRow</span></span>  
 <span data-ttu-id="eae6a-233">Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :</span><span class="sxs-lookup"><span data-stu-id="eae6a-233">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 <span data-ttu-id="eae6a-234">**Sortie :**</span><span class="sxs-lookup"><span data-stu-id="eae6a-234">**Output:**</span></span>  
  
 <span data-ttu-id="eae6a-235">TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-235">RULE ENGINE TRACE for RULESET: LoanProcessing 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-236">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-236">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-237">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-237">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-238">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-238">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-239">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-239">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-240">Type d’objet : TypedDataTable:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-240">Object Type: TypedDataTable:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-241">Identificateur de l’Instance de l’objet : 377</span><span class="sxs-lookup"><span data-stu-id="eae6a-241">Object Instance Identifier: 377</span></span>  
  
 <span data-ttu-id="eae6a-242">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-242">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-243">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-243">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-244">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-244">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-245">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-245">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-246">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-246">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-247">Identificateur de l’Instance de l’objet : 376</span><span class="sxs-lookup"><span data-stu-id="eae6a-247">Object Instance Identifier: 376</span></span>  
  
 <span data-ttu-id="eae6a-248">TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-248">CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-249">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-249">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-250">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-250">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-251">Expression de test : TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-251">Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span></span>  
  
 <span data-ttu-id="eae6a-252">Valeur de l’opérande gauche : 500</span><span class="sxs-lookup"><span data-stu-id="eae6a-252">Left Operand Value: 500</span></span>  
  
 <span data-ttu-id="eae6a-253">Valeur de l’opérande droite : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-253">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="eae6a-254">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-254">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-255">METTRE À JOUR DE AGENDA 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-255">AGENDA UPDATE 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-256">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-256">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-257">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-257">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-258">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-258">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-259">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-259">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-260">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-260">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-261">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-261">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-262">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-262">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-263">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-263">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-264">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-264">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-265">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-265">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-266">Identificateur de l’Instance de l’objet : 375</span><span class="sxs-lookup"><span data-stu-id="eae6a-266">Object Instance Identifier: 375</span></span>  
  
 <span data-ttu-id="eae6a-267">TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-267">CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-268">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-268">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-269">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-269">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-270">Expression de test : TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-270">Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span></span>  
  
 <span data-ttu-id="eae6a-271">Valeur de l’opérande gauche : 1000</span><span class="sxs-lookup"><span data-stu-id="eae6a-271">Left Operand Value: 1000</span></span>  
  
 <span data-ttu-id="eae6a-272">Valeur de l’opérande droite : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-272">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="eae6a-273">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-273">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-274">METTRE À JOUR DE AGENDA 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-274">AGENDA UPDATE 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-275">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-275">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-276">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-276">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-277">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-277">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-278">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-278">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-279">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-279">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-280">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-280">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-281">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-281">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-282">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-282">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-283">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-283">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-284">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-284">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-285">Identificateur de l’Instance de l’objet : 374</span><span class="sxs-lookup"><span data-stu-id="eae6a-285">Object Instance Identifier: 374</span></span>  
  
 <span data-ttu-id="eae6a-286">TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-286">CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-287">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-287">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-288">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-288">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-289">Expression de test : TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-289">Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0</span></span>  
  
 <span data-ttu-id="eae6a-290">Valeur de l’opérande gauche : 35000</span><span class="sxs-lookup"><span data-stu-id="eae6a-290">Left Operand Value: 35000</span></span>  
  
 <span data-ttu-id="eae6a-291">Valeur de l’opérande droite : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-291">Right Operand Value: 0</span></span>  
  
 <span data-ttu-id="eae6a-292">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-292">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-293">METTRE À JOUR DE AGENDA 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-293">AGENDA UPDATE 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-294">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-294">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-295">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-295">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-296">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-296">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-297">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-297">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-298">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-298">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-299">RÈGLE DÉCLENCHÉE 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-299">RULE FIRED 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-300">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-300">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-301">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-301">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-302">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-302">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-303">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-303">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-304">RÈGLE DÉCLENCHÉE 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-304">RULE FIRED 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-305">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-305">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-306">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-306">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-307">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-307">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-308">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-308">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-309">RÈGLE DÉCLENCHÉE 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-309">RULE FIRED 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-310">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-310">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-311">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-311">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-312">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-312">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-313">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-313">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-314">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-314">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-315">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-315">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-316">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-316">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-317">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-317">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-318">Type d’objet : TypedDataTable:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-318">Object Type: TypedDataTable:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-319">Identificateur de l’Instance de l’objet : 377</span><span class="sxs-lookup"><span data-stu-id="eae6a-319">Object Instance Identifier: 377</span></span>  
  
 <span data-ttu-id="eae6a-320">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-320">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-321">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-321">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-322">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-322">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-323">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-323">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-324">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-324">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-325">Identificateur de l’Instance de l’objet : 375</span><span class="sxs-lookup"><span data-stu-id="eae6a-325">Object Instance Identifier: 375</span></span>  
  
 <span data-ttu-id="eae6a-326">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-326">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-327">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-327">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-328">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-328">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-329">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-329">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-330">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-330">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-331">Identificateur de l’Instance de l’objet : 374</span><span class="sxs-lookup"><span data-stu-id="eae6a-331">Object Instance Identifier: 374</span></span>  
  
 <span data-ttu-id="eae6a-332">ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-332">FACT ACTIVITY 3/17/2004 11:27:35 AM</span></span>  
  
 <span data-ttu-id="eae6a-333">Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439</span><span class="sxs-lookup"><span data-stu-id="eae6a-333">Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439</span></span>  
  
 <span data-ttu-id="eae6a-334">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-334">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-335">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-335">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-336">Type d’objet : TypedDataRow:Northwind:CustInfo</span><span class="sxs-lookup"><span data-stu-id="eae6a-336">Object Type: TypedDataRow:Northwind:CustInfo</span></span>  
  
 <span data-ttu-id="eae6a-337">Identificateur de l’Instance de l’objet : 376</span><span class="sxs-lookup"><span data-stu-id="eae6a-337">Object Instance Identifier: 376</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eae6a-338">L'exemple ci-dessus montre que TypedDataTable contenait trois lignes et que chacune était déclarée en tant que TypedDataRow.</span><span class="sxs-lookup"><span data-stu-id="eae6a-338">The example above shows that the TypedDataTable contained three rows, and each was asserted as a TypedDataRow.</span></span>  <span data-ttu-id="eae6a-339">Chacune avait la valeur True dans la condition et a provoqué l'ajout de la règle à l'agenda et son déclenchement.</span><span class="sxs-lookup"><span data-stu-id="eae6a-339">Each evaluated to True in the condition and caused the rule to be added to the agenda and fired.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="eae6a-340">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="eae6a-340">TypedXmlDocument</span></span>  
 <span data-ttu-id="eae6a-341">Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :</span><span class="sxs-lookup"><span data-stu-id="eae6a-341">Example rule "TestRule1" in policy "LoanProcessing":</span></span>  
  
```  
IF Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4  
THEN <do something>  
```  
  
 <span data-ttu-id="eae6a-342">**Sortie :**</span><span class="sxs-lookup"><span data-stu-id="eae6a-342">**Output:**</span></span>  
  
 <span data-ttu-id="eae6a-343">TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/17/2004 9:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-343">RULE ENGINE TRACE for RULESET: LoanProcessing 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-344">ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-344">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-345">Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="eae6a-345">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="eae6a-346">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-346">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-347">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-347">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-348">Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span><span class="sxs-lookup"><span data-stu-id="eae6a-348">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span></span>  
  
 <span data-ttu-id="eae6a-349">Identificateur de l’Instance de l’objet : 858</span><span class="sxs-lookup"><span data-stu-id="eae6a-349">Object Instance Identifier: 858</span></span>  
  
 <span data-ttu-id="eae6a-350">ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-350">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-351">Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="eae6a-351">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="eae6a-352">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-352">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-353">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-353">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-354">Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span><span class="sxs-lookup"><span data-stu-id="eae6a-354">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span></span>  
  
 <span data-ttu-id="eae6a-355">Identificateur de l’Instance de l’objet : 853</span><span class="sxs-lookup"><span data-stu-id="eae6a-355">Object Instance Identifier: 853</span></span>  
  
 <span data-ttu-id="eae6a-356">TEST D'ÉVALUATION DE LA CONDITION (CORRESPONDANCE) 3/17/2004 9:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-356">CONDITION EVALUATION TEST (MATCH) 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-357">Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="eae6a-357">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="eae6a-358">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-358">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-359">Expression de test : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths > = 4</span><span class="sxs-lookup"><span data-stu-id="eae6a-359">Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4</span></span>  
  
 <span data-ttu-id="eae6a-360">Valeur de l’opérande gauche : 6</span><span class="sxs-lookup"><span data-stu-id="eae6a-360">Left Operand Value: 6</span></span>  
  
 <span data-ttu-id="eae6a-361">Valeur de l’opérande droite : 4</span><span class="sxs-lookup"><span data-stu-id="eae6a-361">Right Operand Value: 4</span></span>  
  
 <span data-ttu-id="eae6a-362">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-362">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-363">MISE À JOUR DE L'AGENDA 3/17/2004 9:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-363">AGENDA UPDATE 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-364">Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="eae6a-364">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="eae6a-365">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-365">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-366">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-366">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-367">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-367">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-368">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-368">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-369">RÈGLE DÉCLENCHÉE 3/17/2004 9:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-369">RULE FIRED 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-370">Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="eae6a-370">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="eae6a-371">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-371">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-372">Nom de règle : TestRule1</span><span class="sxs-lookup"><span data-stu-id="eae6a-372">Rule Name: TestRule1</span></span>  
  
 <span data-ttu-id="eae6a-373">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-373">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-374">ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-374">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-375">Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="eae6a-375">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="eae6a-376">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-376">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-377">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-377">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-378">Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span><span class="sxs-lookup"><span data-stu-id="eae6a-378">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case</span></span>  
  
 <span data-ttu-id="eae6a-379">Identificateur de l’Instance de l’objet : 858</span><span class="sxs-lookup"><span data-stu-id="eae6a-379">Object Instance Identifier: 858</span></span>  
  
 <span data-ttu-id="eae6a-380">ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM</span><span class="sxs-lookup"><span data-stu-id="eae6a-380">FACT ACTIVITY 3/17/2004 9:23:05 AM</span></span>  
  
 <span data-ttu-id="eae6a-381">Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span><span class="sxs-lookup"><span data-stu-id="eae6a-381">Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b</span></span>  
  
 <span data-ttu-id="eae6a-382">Nom du groupe de règles : LoanProcessing</span><span class="sxs-lookup"><span data-stu-id="eae6a-382">Ruleset Name: LoanProcessing</span></span>  
  
 <span data-ttu-id="eae6a-383">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-383">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-384">Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span><span class="sxs-lookup"><span data-stu-id="eae6a-384">Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType</span></span>  
  
 <span data-ttu-id="eae6a-385">Identificateur de l’Instance de l’objet : 853</span><span class="sxs-lookup"><span data-stu-id="eae6a-385">Object Instance Identifier: 853</span></span>  
  
 <span data-ttu-id="eae6a-386">Cet exemple montre qu’un **TypedXmlDocument** a été déclaré dans le moteur avec un type de document de « Microsoft.Samples.BizTalk.LoansProcessor.Case ».</span><span class="sxs-lookup"><span data-stu-id="eae6a-386">This example shows that a **TypedXmlDocument** was asserted into the engine with a document type of "Microsoft.Samples.BizTalk.LoansProcessor.Case".</span></span>  <span data-ttu-id="eae6a-387">Sur la base du sélecteur XPath défini dans la règle, le moteur a alors créé et déclaré un TypedXmlDocument enfant de type « Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType » basé sur le type du document et la chaîne du sélecteur.</span><span class="sxs-lookup"><span data-stu-id="eae6a-387">Based on the XPath selector defined in the rule, the engine then created and asserted a child TypedXmlDocument with type  "Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType" based on the document type and selector string.</span></span>  
  
 <span data-ttu-id="eae6a-388">Ce TypedXmlDocument enfant ayant la valeur True dans la condition, cela a provoqué la mise à jour de l'agenda et le déclenchement de la règle.</span><span class="sxs-lookup"><span data-stu-id="eae6a-388">This child TypedXmlDocument evaluated to True in the condition, causing an agenda update and rule firing.</span></span>  <span data-ttu-id="eae6a-389">Le parent et enfant **TypedXmlDocument**du ont alors été retirés.</span><span class="sxs-lookup"><span data-stu-id="eae6a-389">The parent and child **TypedXmlDocument**'s were then retracted.</span></span>  
  
## <a name="update-function"></a><span data-ttu-id="eae6a-390">Fonction Mise à jour</span><span class="sxs-lookup"><span data-stu-id="eae6a-390">Update Function</span></span>  
 <span data-ttu-id="eae6a-391">Exemple de stratégie « Order »</span><span class="sxs-lookup"><span data-stu-id="eae6a-391">Example policy "Order"</span></span>  
  
 <span data-ttu-id="eae6a-392">**Règle « InventoryCheck »**</span><span class="sxs-lookup"><span data-stu-id="eae6a-392">**"InventoryCheck" Rule**</span></span>  
  
```  
IF Inventory.AllocateInventory == True  
THEN Order.inventoryAvailable == True  
   Update(Order)  
```  
  
 <span data-ttu-id="eae6a-393">**Règle « Ship »**</span><span class="sxs-lookup"><span data-stu-id="eae6a-393">**"Ship" Rule**</span></span>  
  
```  
IF Order.inventoryAvailable == True  
THEN Shipment.ShipOrder  
```  
  
 <span data-ttu-id="eae6a-394">**Sortie :**</span><span class="sxs-lookup"><span data-stu-id="eae6a-394">**Output:**</span></span>  
  
 <span data-ttu-id="eae6a-395">TRACE du moteur de règles pour le groupe de règles : commande 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-395">RULE ENGINE TRACE for RULESET: Order 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-396">ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-396">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-397">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-397">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-398">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-398">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-399">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-399">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-400">Type d’objet : TestClasses.Order</span><span class="sxs-lookup"><span data-stu-id="eae6a-400">Object Type: TestClasses.Order</span></span>  
  
 <span data-ttu-id="eae6a-401">Identificateur de l’Instance de l’objet : 448</span><span class="sxs-lookup"><span data-stu-id="eae6a-401">Object Instance Identifier: 448</span></span>  
  
 <span data-ttu-id="eae6a-402">TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-402">CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-403">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-403">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-404">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-404">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-405">Expression de test : TestClasses.Order.inventoryAvailable == True</span><span class="sxs-lookup"><span data-stu-id="eae6a-405">Test Expression: TestClasses.Order.inventoryAvailable == True</span></span>  
  
 <span data-ttu-id="eae6a-406">Valeur de l’opérande gauche : null</span><span class="sxs-lookup"><span data-stu-id="eae6a-406">Left Operand Value: null</span></span>  
  
 <span data-ttu-id="eae6a-407">Valeur de l’opérande droite : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-407">Right Operand Value: True</span></span>  
  
 <span data-ttu-id="eae6a-408">Résultat de test : False</span><span class="sxs-lookup"><span data-stu-id="eae6a-408">Test Result: False</span></span>  
  
 <span data-ttu-id="eae6a-409">ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-409">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-410">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-410">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-411">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-411">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-412">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-412">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-413">Type d’objet : TestClasses.Shipment</span><span class="sxs-lookup"><span data-stu-id="eae6a-413">Object Type: TestClasses.Shipment</span></span>  
  
 <span data-ttu-id="eae6a-414">Identificateur de l’Instance de l’objet : 447</span><span class="sxs-lookup"><span data-stu-id="eae6a-414">Object Instance Identifier: 447</span></span>  
  
 <span data-ttu-id="eae6a-415">ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-415">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-416">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-416">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-417">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-417">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-418">Opération : Assert</span><span class="sxs-lookup"><span data-stu-id="eae6a-418">Operation: Assert</span></span>  
  
 <span data-ttu-id="eae6a-419">Type d’objet : TestClasses.Inventory</span><span class="sxs-lookup"><span data-stu-id="eae6a-419">Object Type: TestClasses.Inventory</span></span>  
  
 <span data-ttu-id="eae6a-420">Identificateur de l’Instance de l’objet : 446</span><span class="sxs-lookup"><span data-stu-id="eae6a-420">Object Instance Identifier: 446</span></span>  
  
 <span data-ttu-id="eae6a-421">TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-421">CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-422">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-422">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-423">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-423">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-424">Expression de test : TestClasses.Inventory.AllocateInventory == True</span><span class="sxs-lookup"><span data-stu-id="eae6a-424">Test Expression: TestClasses.Inventory.AllocateInventory == True</span></span>  
  
 <span data-ttu-id="eae6a-425">Valeur de l’opérande gauche : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-425">Left Operand Value: True</span></span>  
  
 <span data-ttu-id="eae6a-426">Valeur de l’opérande droite : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-426">Right Operand Value: True</span></span>  
  
 <span data-ttu-id="eae6a-427">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-427">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-428">METTRE À JOUR DE AGENDA 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-428">AGENDA UPDATE 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-429">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-429">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-430">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-430">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-431">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-431">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-432">Nom de règle : InventoryCheck</span><span class="sxs-lookup"><span data-stu-id="eae6a-432">Rule Name: InventoryCheck</span></span>  
  
 <span data-ttu-id="eae6a-433">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-433">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-434">RÈGLE DÉCLENCHÉE 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-434">RULE FIRED 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-435">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-435">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-436">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-436">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-437">Nom de règle : InventoryCheck</span><span class="sxs-lookup"><span data-stu-id="eae6a-437">Rule Name: InventoryCheck</span></span>  
  
 <span data-ttu-id="eae6a-438">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-438">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-439">ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-439">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-440">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-440">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-441">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-441">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-442">Opération : mise à jour</span><span class="sxs-lookup"><span data-stu-id="eae6a-442">Operation: Update</span></span>  
  
 <span data-ttu-id="eae6a-443">Type d’objet : TestClasses.Order</span><span class="sxs-lookup"><span data-stu-id="eae6a-443">Object Type: TestClasses.Order</span></span>  
  
 <span data-ttu-id="eae6a-444">Identificateur de l’Instance de l’objet : 448</span><span class="sxs-lookup"><span data-stu-id="eae6a-444">Object Instance Identifier: 448</span></span>  
  
 <span data-ttu-id="eae6a-445">TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-445">CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-446">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-446">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-447">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-447">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-448">Expression de test : TestClasses.Order.inventoryAvailable == True</span><span class="sxs-lookup"><span data-stu-id="eae6a-448">Test Expression: TestClasses.Order.inventoryAvailable == True</span></span>  
  
 <span data-ttu-id="eae6a-449">Valeur de l’opérande gauche : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-449">Left Operand Value: True</span></span>  
  
 <span data-ttu-id="eae6a-450">Valeur de l’opérande droite : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-450">Right Operand Value: True</span></span>  
  
 <span data-ttu-id="eae6a-451">Résultat de test : True</span><span class="sxs-lookup"><span data-stu-id="eae6a-451">Test Result: True</span></span>  
  
 <span data-ttu-id="eae6a-452">METTRE À JOUR DE AGENDA 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-452">AGENDA UPDATE 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-453">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-453">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-454">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-454">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-455">Opération : ajouter</span><span class="sxs-lookup"><span data-stu-id="eae6a-455">Operation: Add</span></span>  
  
 <span data-ttu-id="eae6a-456">Nom de règle : expédition</span><span class="sxs-lookup"><span data-stu-id="eae6a-456">Rule Name: Ship</span></span>  
  
 <span data-ttu-id="eae6a-457">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-457">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-458">RÈGLE DÉCLENCHÉE 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-458">RULE FIRED 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-459">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-459">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-460">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-460">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-461">Nom de règle : expédition</span><span class="sxs-lookup"><span data-stu-id="eae6a-461">Rule Name: Ship</span></span>  
  
 <span data-ttu-id="eae6a-462">Critères de résolution de conflit : 0</span><span class="sxs-lookup"><span data-stu-id="eae6a-462">Conflict Resolution Criteria: 0</span></span>  
  
 <span data-ttu-id="eae6a-463">ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-463">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-464">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-464">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-465">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-465">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-466">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-466">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-467">Type d’objet : TestClasses.Order</span><span class="sxs-lookup"><span data-stu-id="eae6a-467">Object Type: TestClasses.Order</span></span>  
  
 <span data-ttu-id="eae6a-468">Identificateur de l’Instance de l’objet : 448</span><span class="sxs-lookup"><span data-stu-id="eae6a-468">Object Instance Identifier: 448</span></span>  
  
 <span data-ttu-id="eae6a-469">ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-469">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-470">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-470">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-471">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-471">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-472">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-472">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-473">Type d’objet : TestClasses.Shipment</span><span class="sxs-lookup"><span data-stu-id="eae6a-473">Object Type: TestClasses.Shipment</span></span>  
  
 <span data-ttu-id="eae6a-474">Identificateur de l’Instance de l’objet : 447</span><span class="sxs-lookup"><span data-stu-id="eae6a-474">Object Instance Identifier: 447</span></span>  
  
 <span data-ttu-id="eae6a-475">ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00</span><span class="sxs-lookup"><span data-stu-id="eae6a-475">FACT ACTIVITY 3/17/2004 10:31:17 AM</span></span>  
  
 <span data-ttu-id="eae6a-476">Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span><span class="sxs-lookup"><span data-stu-id="eae6a-476">Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72</span></span>  
  
 <span data-ttu-id="eae6a-477">Nom du groupe de règles : ordre</span><span class="sxs-lookup"><span data-stu-id="eae6a-477">Ruleset Name: Order</span></span>  
  
 <span data-ttu-id="eae6a-478">Opération : retrait</span><span class="sxs-lookup"><span data-stu-id="eae6a-478">Operation: Retract</span></span>  
  
 <span data-ttu-id="eae6a-479">Type d’objet : TestClasses.Inventory</span><span class="sxs-lookup"><span data-stu-id="eae6a-479">Object Type: TestClasses.Inventory</span></span>  
  
 <span data-ttu-id="eae6a-480">Identificateur de l’Instance de l’objet : 446</span><span class="sxs-lookup"><span data-stu-id="eae6a-480">Object Instance Identifier: 446</span></span>  
  
 <span data-ttu-id="eae6a-481">Dans cet exemple, la condition associée à la règle Ship a la valeur False la première fois qu'elle est vérifiée.</span><span class="sxs-lookup"><span data-stu-id="eae6a-481">In this example, the condition associated with the Ship rule evaluates to False the first time it is checked.</span></span>  <span data-ttu-id="eae6a-482">Cependant, lorsque la règle InventoryCheck se déclenche, le champ inventoryAvailable de l'Order est modifié et une commande de mise à jour est émise sur le moteur pour l'objet Order.</span><span class="sxs-lookup"><span data-stu-id="eae6a-482">However, when the InventoryCheck rule fires, the inventoryAvailable field on the Order is changed and an Update command is issued on the engine for the Order object.</span></span>  <span data-ttu-id="eae6a-483">Cela provoque la réévaluation de la règle Ship.</span><span class="sxs-lookup"><span data-stu-id="eae6a-483">This causes the Ship rule to be reevaluated.</span></span>  <span data-ttu-id="eae6a-484">Cette fois, la condition prend la valeur True et la règle Ship se déclenche.</span><span class="sxs-lookup"><span data-stu-id="eae6a-484">This time the condition evaluates to true and the Ship rule fires.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eae6a-485">Si vos règles ne sont pas écrites correctement, le chaînage avant avec la fonction Mise à jour risque d'entraîner une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="eae6a-485">If your rules are written incorrectly, forward chaining with the Update function may cause an infinite loop.</span></span>  <span data-ttu-id="eae6a-486">Lorsque vous testerez la stratégie dans l'Éditeur des règles d'entreprise, vous recevrez dans ce cas un message d'erreur indiquant que le moteur de règles a détecté une boucle d'exécution.</span><span class="sxs-lookup"><span data-stu-id="eae6a-486">If this occurs, you will receive an error message when testing the policy in the Business Rule Composer with the text "The rule engine detected an execution loop."</span></span>