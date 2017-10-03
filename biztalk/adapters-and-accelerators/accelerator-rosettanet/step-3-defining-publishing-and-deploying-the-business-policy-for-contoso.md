---
title: "Étape 3 : Définition, publication et déploiement de la stratégie d’entreprise pour Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, deploying
- policies, publishing
- private process tutorial, creating policies
- policies, creating
ms.assetid: 529b16d8-226b-4046-a95d-64162ebd59a3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbdd1133145aada8b1a1abf0ccdde25547b7fed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-defining-publishing-and-deploying-the-business-policy-for-contoso"></a><span data-ttu-id="d2256-102">Étape 3 : Définition, la publication et le déploiement de la stratégie d’entreprise pour Contoso</span><span class="sxs-lookup"><span data-stu-id="d2256-102">Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso</span></span>
<span data-ttu-id="d2256-103">Dans cette étape, vous créez une stratégie d’entreprise qui réserve une quantité définie d’unités pour chaque produit Contoso fabrique à utiliser en cas d’urgence.</span><span class="sxs-lookup"><span data-stu-id="d2256-103">In this step, you create a business policy that reserves a set quantity of units for each product that Contoso manufactures to be used in case of an emergency.</span></span>  
  
### <a name="to-add-a-new-policy"></a><span data-ttu-id="d2256-104">Pour ajouter une nouvelle stratégie</span><span class="sxs-lookup"><span data-stu-id="d2256-104">To add a new policy</span></span>  
  
1.  <span data-ttu-id="d2256-105">Dans l’éditeur des règles d’entreprise, dans le volet Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="d2256-105">In the Business Rule Composer, in the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
2.  <span data-ttu-id="d2256-106">Nommez la nouvelle stratégie **3A2PriceAvailabilityPolicy**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="d2256-106">Name the new policy **3A2PriceAvailabilityPolicy**, and then press **Enter**.</span></span>  
  
### <a name="to-add-a-policy-rule-to-enforce-the-emergency-quantity-needs"></a><span data-ttu-id="d2256-107">Pour ajouter une règle de stratégie afin d’appliquer la quantité d’urgence doit</span><span class="sxs-lookup"><span data-stu-id="d2256-107">To add a policy rule to enforce the emergency quantity needs</span></span>  
  
1.  <span data-ttu-id="d2256-108">Avec le bouton droit **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityPolicy**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="d2256-108">Right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Add New Rule**.</span></span>  
  
2.  <span data-ttu-id="d2256-109">Nommez la règle **règle fournir d’urgence - quantité épuisé**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="d2256-109">Name the rule **Emergency Supply Rule - Quantity Exhausted**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="d2256-110">Dans l’éditeur des règles d’entreprise, dans le volet droit, cliquez sur **Conditions** sous le volet IF, pointez sur **prédicats**, puis cliquez sur le **inférieur ou égal** prédicat.</span><span class="sxs-lookup"><span data-stu-id="d2256-110">In the Business Rule Composer, in the right pane, right-click **Conditions** under the IF pane, point to **Predicates**, and then click the **Less than equal** predicate.</span></span>  
  
4.  <span data-ttu-id="d2256-111">Dans le volet Explorateur de faits, développez **vocabulaires**, développez **3A2PriceAvailabilityVocabulary**, développez **Version 1.0 - publiée**, sélectionnez **quantité Disponible**et faites-le glisser vers le `argument1` espace réservé sur l’aire de compositeur.</span><span class="sxs-lookup"><span data-stu-id="d2256-111">In the Facts Explorer pane, expand **Vocabularies**, expand **3A2PriceAvailabilityVocabulary**, expand **Version 1.0 - Published**, select **Quantity Available**, and drag it onto the `argument1` placeholder on the composer surface.</span></span>  
  
5.  <span data-ttu-id="d2256-112">Répétez l’étape 4 en faisant glisser **quantité d’urgence nécessaire** sur la `argument2` espace réservé.</span><span class="sxs-lookup"><span data-stu-id="d2256-112">Repeat step 4 by dragging **Emergency Quantity Needed** onto the `argument2` placeholder.</span></span>  
  
6.  <span data-ttu-id="d2256-113">Sélectionnez **Final quantité disponible**et faites-le glisser sur **Actions** dans le volet THEN.</span><span class="sxs-lookup"><span data-stu-id="d2256-113">Select **Final Quantity Available**, and then drag it onto **Actions** in the THEN pane.</span></span>  
  
### <a name="to-add-a-policy-to-revise-the-number-available-field-in-the-response"></a><span data-ttu-id="d2256-114">Pour ajouter une stratégie pour modifier le champ nombre disponibles dans la réponse</span><span class="sxs-lookup"><span data-stu-id="d2256-114">To add a policy to revise the Number Available field in the response</span></span>  
  
1.  <span data-ttu-id="d2256-115">Avec le bouton droit **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityPolicy**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="d2256-115">Right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Add New Rule**.</span></span>  
  
2.  <span data-ttu-id="d2256-116">Nommez la nouvelle règle **d’urgence fournir règle - quantité disponible**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="d2256-116">Name the new rule **Emergency Supply Rule - Quantity Available**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="d2256-117">Dans l’éditeur des règles d’entreprise, dans le volet droit, cliquez droit **Conditions** sous le volet IF, pointez sur **prédicats**, puis cliquez sur le **supérieur** prédicat.</span><span class="sxs-lookup"><span data-stu-id="d2256-117">In the Business Rule Composer, in the right pane, right click **Conditions** under the IF pane, point to **Predicates**, and then click the **Greater than** predicate.</span></span>  
  
4.  <span data-ttu-id="d2256-118">Dans le volet Explorateur de faits, développez **vocabulaires**, développez **3A2PriceAvailabilityVocabulary**, développez **Version 1.0 - publiée**, sélectionnez **quantité Disponible**et faites-le glisser sur le `argument1` espace réservé sur l’aire de compositeur.</span><span class="sxs-lookup"><span data-stu-id="d2256-118">In the Facts Explorer pane, expand **Vocabularies**, expand **3A2PriceAvailabilityVocabulary**, expand **Version 1.0 - Published**, select **Quantity Available**, and then drag it onto the `argument1` placeholder on the composer surface.</span></span>  
  
5.  <span data-ttu-id="d2256-119">Répétez cette étape même en faisant glisser **quantité d’urgence nécessaire** sur la `argument2` espace réservé.</span><span class="sxs-lookup"><span data-stu-id="d2256-119">Repeat that same step by dragging **Emergency Quantity Needed** onto the `argument2` placeholder.</span></span>  
  
6.  <span data-ttu-id="d2256-120">Sélectionnez **Final quantité disponible**et faites-le glisser sur **Actions** dans le volet THEN.</span><span class="sxs-lookup"><span data-stu-id="d2256-120">Select **Final Quantity Available**, and then drag it onto **Actions** in the THEN pane.</span></span>  
  
7.  <span data-ttu-id="d2256-121">Dans le volet Explorateur de faits, développez **Version 1.0 - publiée** sous **fonctions**et faites glisser le `Subtract` de fonction sur le **0** argument suivant pour  **Dernière quantité disponible** dans le volet THEN.</span><span class="sxs-lookup"><span data-stu-id="d2256-121">In the Facts Explorer pane, expand **Version 1.0 - Published** under **Functions**, and drag the `Subtract` function onto the **0** argument next to **Final Quantity Available** in the THEN pane.</span></span>  
  
8.  <span data-ttu-id="d2256-122">Faites glisser **quantité disponible** (sous **3A2PriceAvailabilityVocabulary**) et déposez-le sur le `value1` espace réservé dans le volet THEN.</span><span class="sxs-lookup"><span data-stu-id="d2256-122">Drag **Quantity Available** (under **3A2PriceAvailabilityVocabulary**) and drop it on the `value1` placeholder in the THEN pane.</span></span>  
  
9. <span data-ttu-id="d2256-123">Faites glisser **quantité d’urgence nécessaire**et déposez-la sur la `value2` espace réservé dans le volet THEN.</span><span class="sxs-lookup"><span data-stu-id="d2256-123">Drag **Emergency Quantity Needed**, and drop it on the `value2` placeholder in the THEN pane.</span></span>  
  
### <a name="to-save-publish-and-deploy-the-business-policy"></a><span data-ttu-id="d2256-124">Pour enregistrer, publier et déployer la stratégie d’entreprise</span><span class="sxs-lookup"><span data-stu-id="d2256-124">To save, publish, and deploy the business policy</span></span>  
  
1.  <span data-ttu-id="d2256-125">Dans le volet Explorateur de stratégies, cliquez sur **Version 1.0 (non enregistrée)** sous **3A2PriceAvailabilityPolicy**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="d2256-125">In the Policy Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Save**.</span></span>  
  
2.  <span data-ttu-id="d2256-126">Cliquez sur ce même nœud, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="d2256-126">Right-click that same node, and then click **Publish**.</span></span>  
  
3.  <span data-ttu-id="d2256-127">Cliquez sur ce même nœud, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="d2256-127">Right-click that same node, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2256-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2256-128">See Also</span></span>  
 [<span data-ttu-id="d2256-129">Étape 4 : Création du projet de HeaderHelper</span><span class="sxs-lookup"><span data-stu-id="d2256-129">Step 4: Creating the HeaderHelper Project</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md)