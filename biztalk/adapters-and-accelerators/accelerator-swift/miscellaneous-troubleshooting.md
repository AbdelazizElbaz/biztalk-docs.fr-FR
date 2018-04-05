---
title: Résolution des problèmes divers | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 6ebc1867-b5d3-46de-b3bd-69e570ed2b2c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765b32895fa76c0c77b740b76e2e6a03f0571351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="miscellaneous-troubleshooting"></a><span data-ttu-id="c2da4-102">Résolution des problèmes divers</span><span class="sxs-lookup"><span data-stu-id="c2da4-102">Miscellaneous Troubleshooting</span></span>
## <a name="leading-zeroes-validation-is-not-performed-for-fields-that-use-the-checkleadingzeroesinelement-method-to-validate-a-field-in-the-message-validation-policy"></a><span data-ttu-id="c2da4-103">Les zéros de début validation n’est pas effectuée pour les champs qui utilisent la méthode CheckLeadingZeroesInElement pour valider un champ dans la stratégie de Validation de message.</span><span class="sxs-lookup"><span data-stu-id="c2da4-103">Leading zeroes validation is not performed for fields that use the CheckLeadingZeroesInElement method to validate a field in the message Validation Policy.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c2da4-104">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c2da4-104">Symptom</span></span>  
 <span data-ttu-id="c2da4-105">Aucune erreur de validation BRE n’est retournée si un message est envoyé avec des zéros non significatifs dans un champ, même si les zéros non significatifs ne sont pas autorisées pour le champ et de la stratégie de validation comprend une règle pour le champ qui effectue cette validation.</span><span class="sxs-lookup"><span data-stu-id="c2da4-105">No BRE validation error is returned if a message is submitted with leading zeroes in a field, even though leading zeroes are not permitted for the field and the validation policy includes a rule for the field that performs this validation.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c2da4-106">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c2da4-106">Possible Cause</span></span>  
 <span data-ttu-id="c2da4-107">Le **CheckLeadingZeroInElement** (méthode) est incluse dans une règle d’entreprise dans la stratégie de validation pour le type de message.</span><span class="sxs-lookup"><span data-stu-id="c2da4-107">The **CheckLeadingZeroInElement** method is included in a business rule in the validation policy for the message type.</span></span> <span data-ttu-id="c2da4-108">Cette méthode est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="c2da4-108">This method is deprecated.</span></span> <span data-ttu-id="c2da4-109">L’objectif de l’appel de fonction doit entraîner une validation échoue s’il existe un zéro non significatif dans l’élément fourni dans l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="c2da4-109">The purpose of the function call is to cause validation to fail if there is a leading zero in the element provided in the function call.</span></span> <span data-ttu-id="c2da4-110">Toutefois, cette méthode ne provoque pas de validation échoue, même s’il existe un zéro non significatif dans le champ.</span><span class="sxs-lookup"><span data-stu-id="c2da4-110">However, this method does not cause validation to fail, even if there is a leading zero in the field.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c2da4-111">Solution</span><span class="sxs-lookup"><span data-stu-id="c2da4-111">Solution</span></span>  
 <span data-ttu-id="c2da4-112">Si vous souhaitez vérifier les zéros non significatifs, vous devez implémenter la **CheckLeadingZero** méthode au lieu du **CheckLeadingZeroInElement** (méthode).</span><span class="sxs-lookup"><span data-stu-id="c2da4-112">If you want to check leading zeroes, you must implement the **CheckLeadingZero** method instead of the **CheckLeadingZeroInElement** method.</span></span> <span data-ttu-id="c2da4-113">**CheckLeadingZero** provoque une erreur de validation s’il existe un zéro non significatif de l’entrée de chaîne à la fonction.</span><span class="sxs-lookup"><span data-stu-id="c2da4-113">**CheckLeadingZero** causes a validation error if there is a leading zero in the string input to the function.</span></span>  
  
 <span data-ttu-id="c2da4-114">Pour implémenter le **CheckLeadingZero** (méthode), vous devez créer une méthode personnalisée qui appelle le **CheckLeadingZero** méthode à partir de la fonction personnalisée et fournit à celui-ci sous forme de chaîne, la valeur est validé pour les zéros de début.</span><span class="sxs-lookup"><span data-stu-id="c2da4-114">To implement the **CheckLeadingZero** method, you must create a custom method that invokes the **CheckLeadingZero** method from within the custom function and provides to it as a string the value to be validated for leading zeroes.</span></span> <span data-ttu-id="c2da4-115">C’est parce que **CheckLeadingZero** n’enregistre pas d’une erreur, mais simplement retourne une valeur booléenne False si la chaîne d’entrée n’est pas un champ de numéro de SWIFT valide ou si l’entrée de chaîne contient un zéro non significatif.</span><span class="sxs-lookup"><span data-stu-id="c2da4-115">This is because **CheckLeadingZero** does not log an error, but instead simply returns a Boolean False if the input string is not a valid SWIFT Number field or if the string input has a leading zero.</span></span> <span data-ttu-id="c2da4-116">Sinon, elle retourne la valeur True.</span><span class="sxs-lookup"><span data-stu-id="c2da4-116">Otherwise, it returns True.</span></span> <span data-ttu-id="c2da4-117">Votre méthode personnalisée peut ensuite enregistrent des erreurs en conséquence.</span><span class="sxs-lookup"><span data-stu-id="c2da4-117">Your custom method can then log errors accordingly.</span></span>  
  
## <a name="an-error-is-returned-by-the-message-validation-policy-if-the-swift-number-field-has-a-leading-zero"></a><span data-ttu-id="c2da4-118">Une erreur est retournée par la stratégie de validation de message si le champ de numéro de SWIFT a un zéro non significatif</span><span class="sxs-lookup"><span data-stu-id="c2da4-118">An error is returned by the message validation policy if the SWIFT Number field has a leading zero</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c2da4-119">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c2da4-119">Symptom</span></span>  
 <span data-ttu-id="c2da4-120">Une erreur de validation BRE est retournée si un message est envoyé avec des zéros non significatifs dans un champ de même si le début des zéros sont autorisées pour le champ.</span><span class="sxs-lookup"><span data-stu-id="c2da4-120">A BRE validation error is returned if a message is submitted with leading zeroes in a field even though leading zeroes are permitted for the field.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c2da4-121">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c2da4-121">Possible Cause</span></span>  
 <span data-ttu-id="c2da4-122">Cela peut se produire si une des méthodes suivantes est utilisée pour valider un champ de numéro de SWIFT dans la règle concernée, généralement à la partie de l’Action de la règle.</span><span class="sxs-lookup"><span data-stu-id="c2da4-122">This can occur if one of the following methods is used to validate a SWIFT Number field in the rule concerned, usually in the Action part of the rule.</span></span> <span data-ttu-id="c2da4-123">Cela peut se produire dans un champ Quantité, taux, prix ou la quantité.</span><span class="sxs-lookup"><span data-stu-id="c2da4-123">This may occur in an Amount, Rate, Price, or Quantity field.</span></span>  
  
-   <span data-ttu-id="c2da4-124">**CheckCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="c2da4-124">**CheckCurrencyAmount**</span></span>  
  
-   <span data-ttu-id="c2da4-125">**CheckValidAmount**</span><span class="sxs-lookup"><span data-stu-id="c2da4-125">**CheckValidAmount**</span></span>  
  
-   <span data-ttu-id="c2da4-126">**CheckValidCurrencyAndPriceCode**</span><span class="sxs-lookup"><span data-stu-id="c2da4-126">**CheckValidCurrencyAndPriceCode**</span></span>  
  
-   <span data-ttu-id="c2da4-127">**CheckValidSignCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="c2da4-127">**CheckValidSignCurrencyAmount**</span></span>  
  
-   <span data-ttu-id="c2da4-128">**CheckValidSignDateCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="c2da4-128">**CheckValidSignDateCurrencyAmount**</span></span>  
  
-   <span data-ttu-id="c2da4-129">**CheckValidSignRate**</span><span class="sxs-lookup"><span data-stu-id="c2da4-129">**CheckValidSignRate**</span></span>  
  
-   <span data-ttu-id="c2da4-130">**IsValidTransactionDetailsCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="c2da4-130">**IsValidTransactionDetailsCurrencyAmount**</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c2da4-131">Solution</span><span class="sxs-lookup"><span data-stu-id="c2da4-131">Solution</span></span>  
 <span data-ttu-id="c2da4-132">Si une des méthodes dans la liste ci-dessus, à l’exception de **CheckValidSignRate**, est utilisé dans la règle de la stratégie de Validation, activer des zéros non significatifs, comme décrit dans [prise en charge des zéros non significatifs dans les Validations de champ Quantité](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md).</span><span class="sxs-lookup"><span data-stu-id="c2da4-132">If any of the methods in the list above, except for **CheckValidSignRate**, is used in the rule in the Validation policy, enable leading zeros as described in [Supporting Leading Zeros in Amount Field Validations](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md).</span></span>  
  
 <span data-ttu-id="c2da4-133">Si le **CheckValidSignRate** méthode est utilisée dans la règle qui a retourné l’erreur, la seule façon pour prendre en charge les zéros non significatifs consiste à supprimer cette règle de la stratégie de Validation.</span><span class="sxs-lookup"><span data-stu-id="c2da4-133">If the **CheckValidSignRate** method is used in the rule that returned this error, the only way to support leading zeroes is to remove this rule from the Validation policy.</span></span> <span data-ttu-id="c2da4-134">Suivez les étapes ci-dessous pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="c2da4-134">Follow the steps below to accomplish this:</span></span>  
  
1.  <span data-ttu-id="c2da4-135">Dans l’éditeur des règles d’entreprise, cliquez sur le **Version** nœud pour la stratégie déployée qui contient une règle à l’aide de la **CheckValidSignRate** (méthode).</span><span class="sxs-lookup"><span data-stu-id="c2da4-135">In Business Rule Composer, right-click the **Version** node for the deployed policy that contains a rule using the **CheckValidSignRate** method.</span></span> <span data-ttu-id="c2da4-136">Cliquez sur **Annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="c2da4-136">Click **Undeploy**.</span></span>  
  
2.  <span data-ttu-id="c2da4-137">Cliquez sur le **Version** nœud pour la même stratégie, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="c2da4-137">Right-click the **Version** node for the same policy, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="c2da4-138">Cliquez sur le **Validation_Policy** nœud pour la même stratégie, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="c2da4-138">Right-click the **Validation_Policy** node for the same policy, and then click **Paste**.</span></span>  
  
4.  <span data-ttu-id="c2da4-139">Développez la nouvelle version non enregistrée de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="c2da4-139">Expand the new unsaved version of the policy.</span></span> <span data-ttu-id="c2da4-140">Avec le bouton droit de la règle qui a le **CheckValidSignRate** appel de méthode, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="c2da4-140">Right-click the rule that has the **CheckValidSignRate** method call, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="c2da4-141">Avec le bouton de la stratégie de non enregistrées new **Version** nœud, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="c2da4-141">Right-click the policy's new unsaved **Version** node, and then click **Save**.</span></span> <span data-ttu-id="c2da4-142">Cliquez sur le même nœud, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="c2da4-142">Right-click the same node, and then click **Publish**.</span></span> <span data-ttu-id="c2da4-143">Cliquez sur le même nœud, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="c2da4-143">Right-click the same node, and then click **Deploy**.</span></span>  
  
## <a name="a4swift-database-requires-archiving"></a><span data-ttu-id="c2da4-144">Base de données A4SWIFT requiert l’archivage</span><span class="sxs-lookup"><span data-stu-id="c2da4-144">A4SWIFT database requires archiving</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c2da4-145">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c2da4-145">Symptom</span></span>  
 <span data-ttu-id="c2da4-146">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données est trop importante.</span><span class="sxs-lookup"><span data-stu-id="c2da4-146">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database is growing too large.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c2da4-147">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c2da4-147">Possible Cause</span></span>  
 <span data-ttu-id="c2da4-148">La table d’historique dans les [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données n’est pas automatiquement archivé.</span><span class="sxs-lookup"><span data-stu-id="c2da4-148">The History table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database is not automatically archived.</span></span> <span data-ttu-id="c2da4-149">Cette table stocke des données sur le message repair et nouvelle soumission, y compris les personnes qui ont effectué les tâches et les données sur les processus d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c2da4-149">This table stores data about message repair and new submission, including who performed which tasks and data about orchestration processes.</span></span> <span data-ttu-id="c2da4-150">Cette table continue à croître à mesure que vous effectuez des opérations d’envoi et de la réparation de message.</span><span class="sxs-lookup"><span data-stu-id="c2da4-150">This table will continue to grow as you perform message repair and new submission operations.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c2da4-151">Solution</span><span class="sxs-lookup"><span data-stu-id="c2da4-151">Solution</span></span>  
 <span data-ttu-id="c2da4-152">Pour limiter la croissance de la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] de base de données, d’archiver régulièrement les données en dehors de la table d’historique, à l’aide de vos procédures d’archivage de standard.</span><span class="sxs-lookup"><span data-stu-id="c2da4-152">To limit growth of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, routinely archive data out of the History table, using your standard archiving procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2da4-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2da4-153">See Also</span></span>  
 [<span data-ttu-id="c2da4-154">Résolution des problèmes : Problèmes et résolutions</span><span class="sxs-lookup"><span data-stu-id="c2da4-154">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)