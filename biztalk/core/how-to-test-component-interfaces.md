---
title: Comment tester des Interfaces de composant | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing component interfaces
- component interfaces, testing
ms.assetid: d637f76d-170d-4543-a2b2-a4ac4001386b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be50521e5c4421d8ac8902bcf7a414d734c3b9f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-component-interfaces"></a><span data-ttu-id="ff195-102">Test des interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="ff195-102">How to Test Component Interfaces</span></span>
<span data-ttu-id="ff195-103">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise fait appel aux métadonnées et aux interfaces de composant PeopleSoft ; il permet donc de traiter de nouvelles interfaces de composant ou des interfaces de composant modifiées.</span><span class="sxs-lookup"><span data-stu-id="ff195-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft metadata and component interfaces; therefore, it can handle new or modified component interfaces.</span></span> <span data-ttu-id="ff195-104">L'adaptateur n'émet aucune hypothèse à propos des interfaces de composant à l'exception du fait qu'elles sont logiques et valides.</span><span class="sxs-lookup"><span data-stu-id="ff195-104">The adapter makes no assumptions about component interfaces except that they are logical and valid.</span></span> <span data-ttu-id="ff195-105">Ainsi, chaque interface de composant doit être testée avant qu'elle puisse être utilisée comme source pour l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ff195-105">Therefore, each component interface must be tested before it is used as a source for the adapter.</span></span>  
  
 <span data-ttu-id="ff195-106">Si un utilisateur ou une mise à niveau PeopleSoft apporte des modifications à l'application sous-jacente et que ces modifications invalident une interface de composant, l'utilisateur doit réparer celle-ci avant que l'adaptateur puisse l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="ff195-106">If changes are made to the underlying application by the user or by a PeopleSoft upgrade, and the changes invalidate a component interface, the user must repair the invalid component interface before the adapter uses it.</span></span>  
  
### <a name="to-test-a-component-interface"></a><span data-ttu-id="ff195-107">Pour tester une interface de composant</span><span class="sxs-lookup"><span data-stu-id="ff195-107">To test a component interface</span></span>  
  
1.  <span data-ttu-id="ff195-108">Dans le Concepteur d’applications, sur le **outils** menu, cliquez sur **tester une Interface de composant**.</span><span class="sxs-lookup"><span data-stu-id="ff195-108">In Application Designer, on the **Tools** menu, click **Test Component Interface**.</span></span>  
  
     ![](../core/media/psadapter-54-ps-testcompinterface1.gif "PSAdapter_54_PS_TestCompInterface1")  
  
2.  <span data-ttu-id="ff195-109">Dans le **testeur d’Interface de composant** boîte de dialogue zone, l’interface de composant de test en utilisant l’une méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ff195-109">In the **Component Interface Tester** dialog box, test the component interface by using one the following methods.</span></span> <span data-ttu-id="ff195-110">Après avoir terminé d'apporter des modifications, cliquez avec le bouton droit sur le premier élément dans le volet.</span><span class="sxs-lookup"><span data-stu-id="ff195-110">After you finish making changes, right-click the top item in the pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ff195-111">Si besoin, cliquez sur la boîte de dialogue pour l'amener au premier plan.</span><span class="sxs-lookup"><span data-stu-id="ff195-111">If required, click the dialog box to bring it to the foreground.</span></span>  
  
    -   <span data-ttu-id="ff195-112">Pour tester l’interface de composant à l’aide de la méthode Find, cliquez sur **trouver**.</span><span class="sxs-lookup"><span data-stu-id="ff195-112">To test the component interface using the Find method, click **Find**.</span></span>  
  
         <span data-ttu-id="ff195-113">Le **testeur d’Interface de composant - résultats de la recherche** boîte de dialogue s’ouvre, affichant toutes les entrées possibles pour le composant sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="ff195-113">The **Component Interface Tester - Find Results** dialog box opens, displaying all the possible entries for the underlying component.</span></span> <span data-ttu-id="ff195-114">Si le nombre d'entrées est supérieur à 300, un message s'affiche.</span><span class="sxs-lookup"><span data-stu-id="ff195-114">If there are more than 300 entries, a message appears.</span></span>  
  
         <span data-ttu-id="ff195-115">a.</span><span class="sxs-lookup"><span data-stu-id="ff195-115">a.</span></span> <span data-ttu-id="ff195-116">Dans le volet gauche de la **résultats de la recherche** boîte de dialogue, sélectionnez un champ.</span><span class="sxs-lookup"><span data-stu-id="ff195-116">In the left pane of the **Find Results** dialog box, select a field.</span></span>  
  
         <span data-ttu-id="ff195-117">b.</span><span class="sxs-lookup"><span data-stu-id="ff195-117">b.</span></span> <span data-ttu-id="ff195-118">Pour afficher les données pertinentes pour le champ concerné, cliquez sur **sélectionnés**.</span><span class="sxs-lookup"><span data-stu-id="ff195-118">To display the relevant data for that particular field, click **Get Selected**.</span></span>  
  
         <span data-ttu-id="ff195-119">L'écran suivant s'affiche.</span><span class="sxs-lookup"><span data-stu-id="ff195-119">The following screen appears.</span></span>  
  
         ![](../core/media/psadapter-55-ps-testcompinterface2.gif "PSAdapter_55_PS_TestCompInterface2")  
  
         <span data-ttu-id="ff195-120">Si les paramètres de sécurité l'autorisent, vous pouvez modifier les valeurs des champs individuels.</span><span class="sxs-lookup"><span data-stu-id="ff195-120">If the security settings allow, you can change the values in the individual fields.</span></span>  
  
         <span data-ttu-id="ff195-121">La boîte de dialogue suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="ff195-121">The following dialog box opens.</span></span>  
  
         ![](../core/media/psadapter-56-ps-testcompinterface3.gif "PSAdapter_56_PS_TestCompInterface3")  
  
    -   <span data-ttu-id="ff195-122">Pour tester l’interface de composant à l’aide de la `Get` méthode :</span><span class="sxs-lookup"><span data-stu-id="ff195-122">To test the component interface using the `Get` method:</span></span>  
  
         <span data-ttu-id="ff195-123">a.</span><span class="sxs-lookup"><span data-stu-id="ff195-123">a.</span></span> <span data-ttu-id="ff195-124">Entrez l’ou les clés existante.</span><span class="sxs-lookup"><span data-stu-id="ff195-124">Enter the existing key(s).</span></span>  
  
         <span data-ttu-id="ff195-125">b.</span><span class="sxs-lookup"><span data-stu-id="ff195-125">b.</span></span> <span data-ttu-id="ff195-126">Cliquez sur **obtenir existant**.</span><span class="sxs-lookup"><span data-stu-id="ff195-126">Click **Get Existing**.</span></span>  
  
         <span data-ttu-id="ff195-127">Cette action a pour effet de renvoyer les propriétés exposées qui correspondent à la clé que vous avez entrée.</span><span class="sxs-lookup"><span data-stu-id="ff195-127">This returns the exposed properties for the key that you entered.</span></span>  
  
         <span data-ttu-id="ff195-128">Vous pouvez modifier les valeurs si **mettre à jour les accès** a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="ff195-128">You can change values if **Update access** was specified.</span></span>  
  
         <span data-ttu-id="ff195-129">Vous pouvez également tester l'interface de composant à l'aide de la méthode `Create`.</span><span class="sxs-lookup"><span data-stu-id="ff195-129">Alternatively, you can test using the `Create` method.</span></span>  
  
         ![](../core/media/psadapter-57-ps-testcompinterface4.gif "PSAdapter_57_PS_TestCompInterface4")  
  
    -   <span data-ttu-id="ff195-130">Pour tester l’interface de composant à l’aide de la `Create` méthode :</span><span class="sxs-lookup"><span data-stu-id="ff195-130">To test the component interface using the `Create` method:</span></span>  
  
         <span data-ttu-id="ff195-131">a.</span><span class="sxs-lookup"><span data-stu-id="ff195-131">a.</span></span> <span data-ttu-id="ff195-132">Entrez toutes les valeurs de clés requises.</span><span class="sxs-lookup"><span data-stu-id="ff195-132">Enter all required key values.</span></span>  
  
         <span data-ttu-id="ff195-133">b.</span><span class="sxs-lookup"><span data-stu-id="ff195-133">b.</span></span> <span data-ttu-id="ff195-134">Cliquez sur **créer de nouveaux**.</span><span class="sxs-lookup"><span data-stu-id="ff195-134">Click **Create New**.</span></span>  
  
         <span data-ttu-id="ff195-135">Lorsque vous entrez des valeurs valides dans **créer des clés**, un volet qui affiche les données JOBCODE s’ouvre après que le nom de la Table est développé avec les données par défaut en place.</span><span class="sxs-lookup"><span data-stu-id="ff195-135">When you enter valid values in **Create keys**, a pane that displays the JOBCODE data opens after the Table name is expanded with default data in place.</span></span>  
  
         <span data-ttu-id="ff195-136">Vous pouvez maintenant modifier des champs.</span><span class="sxs-lookup"><span data-stu-id="ff195-136">You can change fields now.</span></span>  
  
         ![](../core/media/psadapter-58-ps-testcompinterface5.gif "PSAdapter_58_PS_TestCompInterface5")  
  
         <span data-ttu-id="ff195-137">Les modifications sont validées en fonction de la logique d'entreprise sous-jacente du composant.</span><span class="sxs-lookup"><span data-stu-id="ff195-137">Changes are validated against the component's underlying business logic.</span></span>  
  
3.  <span data-ttu-id="ff195-138">Pour enregistrer vos modifications, cliquez sur le **enregistrer** icône.</span><span class="sxs-lookup"><span data-stu-id="ff195-138">To save your changes, click the **Save** icon.</span></span>  
  
     <span data-ttu-id="ff195-139">Les clés qui ont été utilisées pour créer l'enregistrement peuvent être utilisées avec la méthode Get pour afficher des données.</span><span class="sxs-lookup"><span data-stu-id="ff195-139">The keys used to create the record can be used with the Get method for viewing data.</span></span> <span data-ttu-id="ff195-140">Les données qui ont été ajoutées peuvent être affichées dans le composant PeopleSoft, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ff195-140">The data that was added can be viewed in the PeopleSoft Component as shown in the following example.</span></span>  
  
     ![](../core/media/psadapter-59-ps-testcompinterface6.gif "PSAdapter_59_PS_TestCompInterface6")  
  
     <span data-ttu-id="ff195-141">**Date d’effet** est une des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="ff195-141">**Effective Date** is one of the default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff195-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff195-142">See Also</span></span>  
 <span data-ttu-id="ff195-143">[Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md) </span><span class="sxs-lookup"><span data-stu-id="ff195-143">[Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md) </span></span>  
 [<span data-ttu-id="ff195-144">Annexe c : à l’aide des Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="ff195-144">Appendix C: Using Component Interfaces</span></span>](../core/appendix-c-using-component-interfaces.md)