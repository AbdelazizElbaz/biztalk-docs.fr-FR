---
title: "Comment créer des Interfaces de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating component interfaces
- component interfaces, creating
ms.assetid: 9def053a-cbf6-4b34-b2e8-b2d03bffc5fe
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86ee68edba66b05d3c2541dd9c41cc074bd790b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-component-interfaces"></a><span data-ttu-id="9ed8f-102">Création des interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="9ed8f-102">How to Create Component Interfaces</span></span>
<span data-ttu-id="9ed8f-103">Vous créez des interfaces de composant à l'aide du Concepteur d'applications PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-103">You create component interfaces using the PeopleSoft Application Designer.</span></span> <span data-ttu-id="9ed8f-104">Pour plus d'informations sur celui-ci, consultez la documentation de PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-104">(For more information about Application Designer, see the PeopleSoft Enterprise documentation.)</span></span>  
  
 <span data-ttu-id="9ed8f-105">Vous pouvez ajouter des propriétés à partir des enregistrements de la vue du composant.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-105">You can add properties from the records in the component view.</span></span> <span data-ttu-id="9ed8f-106">Dans l'interface de composant, vous pouvez supprimer une propriété que vous ne souhaitez pas exposer.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-106">In the component interface, you can delete a property that you do not want to expose.</span></span> <span data-ttu-id="9ed8f-107">Vous pouvez renommer une propriété en double-cliquant dessus pour entrer un nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-107">You can rename properties by clicking the property and then clicking again until you can type a new name.</span></span> <span data-ttu-id="9ed8f-108">Si vous renommez une propriété, vous pouvez la référencer dans l'interface de composant uniquement par le nouveau nom, et non par le nom de composant sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-108">If you rename a property, you can reference it in the component interface only by the new name, not by the underlying component name.</span></span>  
  
 <span data-ttu-id="9ed8f-109">Plusieurs icônes peuvent être présentes en regard des propriétés.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-109">Properties may have various icons adjacent to them.</span></span> <span data-ttu-id="9ed8f-110">Par exemple, EMPLID possède une icône qui indique qu'il s'agit d'un champ de clé de l'enregistrement sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-110">For example, EMPLID has an icon that indicates that it is a key field from the underlying record.</span></span> <span data-ttu-id="9ed8f-111">NAME possède une icône qui indique qu'il s'agit d'un champ de clé de remplacement de l'enregistrement sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-111">NAME has an icon that indicates that it is an alternate key field from the underlying record.</span></span> <span data-ttu-id="9ed8f-112">(Pour obtenir une liste complète des icônes de propriétés, consultez la documentation PeopleBooks.)</span><span class="sxs-lookup"><span data-stu-id="9ed8f-112">(For a complete list of property icons, see the PeopleBooks documentation.)</span></span>  
  
### <a name="creating-a-new-component-interface"></a><span data-ttu-id="9ed8f-113">Création d'une interface de composant</span><span class="sxs-lookup"><span data-stu-id="9ed8f-113">Creating a new component interface</span></span>  
  
1.  <span data-ttu-id="9ed8f-114">Ouvrez le concepteur d'applications PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-114">Open the PeopleSoft Application Designer.</span></span>  
  
2.  <span data-ttu-id="9ed8f-115">Dans le menu **Fichier** , cliquez sur **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-115">On the **File** menu, click **New**.</span></span>  
  
     ![](../core/media/psadapter-42-ps-new-compinterface.gif "PSAdapter_42_PS_New_CompInterface")  
  
3.  <span data-ttu-id="9ed8f-116">Dans le **nouveau** boîte de dialogue, sélectionnez **Interface de composant**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-116">In the **New** dialog box, select **Component Interface**, and then click **OK**.</span></span>  
  
     ![](../core/media/psadapter-43-ps-selectsourcecomp.gif "PSAdapter_43_PS_SelectSourceComp")  
  
4.  <span data-ttu-id="9ed8f-117">Dans le **sélectionner le composant Source pour l’Interface de composant** fenêtre, sélectionnez le composant à utiliser comme base pour l’interface de composant, puis cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-117">In the **Select Source Component for Component Interface** window, select the component to use as a basis for the component interface, and then click **Select**.</span></span>  
  
     ![](../core/media/psadapter-44-ps-appdesigner1.gif "PSAdapter_44_PS_AppDesigner1")  
  
    > [!NOTE]
    >  <span data-ttu-id="9ed8f-118">Si l'interface de composant est volumineuse, exposez les propriétés du composant manuellement.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-118">If the component interface is large, expose the component properties manually.</span></span>  
  
5.  <span data-ttu-id="9ed8f-119">Dans le **Concepteur d’applications** boîte de dialogue zone, choisissez une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="9ed8f-119">In the **Application Designer** dialog box, choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="9ed8f-120">Cliquez sur **non** pour créer l’interface de composant sans afficher les propriétés et d’exposer les propriétés du composant manuellement.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-120">Click **No** to create the component interface without displaying properties and to expose component properties manually.</span></span>  
  
         <span data-ttu-id="9ed8f-121">a.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-121">a.</span></span> <span data-ttu-id="9ed8f-122">Faites glisser les champs appropriés dans le volet gauche vers le volet droit.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-122">Drag the relevant fields from the left pane to the right pane.</span></span>  
  
         <span data-ttu-id="9ed8f-123">b.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-123">b.</span></span> <span data-ttu-id="9ed8f-124">Pour sélectionner diverses fonctions à effectuer, avec le bouton droit soit sur le volet droit ou gauche, selon le volet est actif.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-124">To select various functions to perform, right-click either the right or left pane, depending on which pane is active.</span></span>  
  
         <span data-ttu-id="9ed8f-125">Pour obtenir une liste complète des fonctions, consultez la documentation PeopleBooks.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-125">For a complete list of functions, see the PeopleBooks documentation.</span></span>  
  
    -   <span data-ttu-id="9ed8f-126">Cliquez sur **Oui** pour créer l’interface de composant et afficher les propriétés de l’interface de composant sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="9ed8f-126">Click **Yes** to create the component interface and display the properties of the underlying component interface.</span></span>  
  
         ![](../core/media/psadapter-45-ps-appdesigner2.gif "PSAdapter_45_PS_AppDesigner2")  
  
## <a name="see-also"></a><span data-ttu-id="9ed8f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ed8f-127">See Also</span></span>  
 <span data-ttu-id="9ed8f-128">[Méthodes standard dans les Interfaces de composant](../core/standard-methods-in-component-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="9ed8f-128">[Standard Methods in Component Interfaces](../core/standard-methods-in-component-interfaces.md) </span></span>  
 <span data-ttu-id="9ed8f-129">[Annexe c : à l’aide des Interfaces de composant](../core/appendix-c-using-component-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="9ed8f-129">[Appendix C: Using Component Interfaces](../core/appendix-c-using-component-interfaces.md) </span></span>  
 [<span data-ttu-id="9ed8f-130">Annexe a : méthodes d’Interface de composant</span><span class="sxs-lookup"><span data-stu-id="9ed8f-130">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)