---
title: "Comment copier des données dans le contexte du Message en tant que champs de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fdfe475-d9b4-4cf9-898f-dbd7e719c27c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18242f30f32974cc32ab5d39a4a9c63650f27ffa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-data-to-the-message-context-as-property-fields"></a><span data-ttu-id="bfa38-102">Comment copier des données dans le contexte du Message en tant que champs de propriété</span><span class="sxs-lookup"><span data-stu-id="bfa38-102">How to Copy Data to the Message Context as Property Fields</span></span>
<span data-ttu-id="bfa38-103">Vous pouvez promouvoir une propriété comme un **champ de propriété** dans la même façon que pour promouvoir une propriété comme un **champ distinctif**, et vous pouvez également utiliser le **Promotion rapide** des fonctions aux simplifier le processus.</span><span class="sxs-lookup"><span data-stu-id="bfa38-103">You can promote a property as a **Property Field** in much the same way as promoting a property as a **Distinguished Field**, and you can also use the **Quick Promotion** feature to streamline the process.</span></span>  
  
 <span data-ttu-id="bfa38-104">Vous pouvez choisir **champ de propriété** plutôt que la promotion **champ distinctif** promotion pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="bfa38-104">You might choose **Property Field** promotion over **Distinguished Field** promotion for the following reasons:</span></span>  
  
-   <span data-ttu-id="bfa38-105">Les valeurs que vous souhaitez promouvoir sont inférieure à la limite de 255 caractères qui s’applique aux **champs de propriété**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-105">The values you want to promote are shorter than the 255 character limitation that applies to **Property Fields**.</span></span>  
  
-   <span data-ttu-id="bfa38-106">Les valeurs dont vous assurez la promotion doivent être accessibles en dehors des orchestrations, par exemple dans des pipelines ou des ports.</span><span class="sxs-lookup"><span data-stu-id="bfa38-106">You need the values that you promote to be accessible outside of orchestrations, such as within pipelines or ports.</span></span>  
  
 <span data-ttu-id="bfa38-107">Cette rubrique fournit des instructions pas à pas pour promouvoir une propriété comme un **champ de propriété** dans les deux des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="bfa38-107">This topic provides step-by-step instructions for promoting a property as a **Property Field** in both of these ways.</span></span>  
  
### <a name="to-promote-a-property-as-a-property-field-using-the-promote-properties-dialog-box"></a><span data-ttu-id="bfa38-108">Pour promouvoir une propriété en tant que champ de propriété à l'aide de la boîte de dialogue Promouvoir les propriétés</span><span class="sxs-lookup"><span data-stu-id="bfa38-108">To promote a property as a Property Field using the Promote Properties dialog box</span></span>  
  
1.  <span data-ttu-id="bfa38-109">Si nécessaire, créez un schéma de propriété approprié dans lequel vous effectuerez la promotion d'une propriété.</span><span class="sxs-lookup"><span data-stu-id="bfa38-109">If necessary, create an appropriate property schema into which you will promote a property.</span></span> <span data-ttu-id="bfa38-110">Pour obtenir des instructions pas à pas pour créer des schémas de propriété, consultez [création de schémas de propriété](../core/how-to-create-property-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="bfa38-110">For step-by-step instructions for creating property schemas, see [Creating Property Schemas](../core/how-to-create-property-schemas.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bfa38-111">Cette étape ne soit pas nécessaire si vous avez déjà créé un schéma de propriété et inséré approprié **élément de champ** nœuds en tant que nœuds enfants de la **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="bfa38-111">This step might not be necessary if you have already created a property schema and inserted the appropriate **Field Element** nodes as child nodes of the **Schema** node.</span></span>  
  
2.  <span data-ttu-id="bfa38-112">Dans l’Éditeur BizTalk, ouvrez le schéma pour lequel vous souhaitez promouvoir une ou plusieurs propriétés, puis sélectionnez le (premier) **Fieldelement**, **attribut de champ**, ou **enregistrement** nœud que vous souhaitez promouvoir en tant qu’un **champ de propriété**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-112">In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Property Field**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bfa38-113">Vous pouvez uniquement promouvoir **enregistrement** nœuds s’ils sont configurés pour qu’il contienne uniquement du contenu simple en ayant sa **Content Type** propriété **SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-113">You can only promote **Record** nodes if they are configured to contain only simple content by having its **Content Type** property set to **SimpleContent**.</span></span>  
  
3.  <span data-ttu-id="bfa38-114">Cliquez sur le nœud sélectionné, cliquez sur **promouvoir**, puis cliquez sur **afficher les Promotions**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-114">Right-click the selected node, click **Promote**, and then click **Show Promotions**.</span></span>  
  
     <span data-ttu-id="bfa38-115">Le **promouvoir les propriétés** boîte de dialogue s’ouvre avec apparaît le nœud sélectionné dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bfa38-115">The **Promote Properties** dialog box opens with the selected node showing as selected in the schema tree on the left side of the dialog box.</span></span>  
  
4.  <span data-ttu-id="bfa38-116">Dans le **promouvoir les propriétés** boîte de dialogue, sélectionnez le **champs de propriété** onglet.</span><span class="sxs-lookup"><span data-stu-id="bfa38-116">In the **Promote Properties** dialog box, select the **Property Fields** tab.</span></span>  
  
5.  <span data-ttu-id="bfa38-117">Vérifiez que le schéma de propriété dans lequel vous souhaitez promouvoir une propriété se trouve dans le **liste des schémas de propriété** dans l’onglet champs de propriété. Si c'est bien le cas, passez directement à l'étape 8.</span><span class="sxs-lookup"><span data-stu-id="bfa38-117">Confirm that the property schema into which you want to promote a property is present in the **Property Schemas List** in the Property Fields tab. If it is present, skip to step 8.</span></span>  
  
6.  <span data-ttu-id="bfa38-118">Dans le **liste des schémas de propriété** , cliquez sur le **dossier** icône.</span><span class="sxs-lookup"><span data-stu-id="bfa38-118">In the **Property Schemas List** section, click the **Folder** icon.</span></span> <span data-ttu-id="bfa38-119">Le **sélecteur de Type BizTalk** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="bfa38-119">The **BizTalk Type Picker** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="bfa38-120">Dans le **sélecteur de Type BizTalk** boîte de dialogue zone, naviguez jusqu’au schéma de propriété approprié (que vous avez créés à l’étape 1), sélectionnez-le, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-120">In the **BizTalk Type Picker** dialog box, navigate to the appropriate property schema (that you may have created in step 1), select that schema, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bfa38-121">Si vous le souhaitez, vous pouvez modifier le préfixe d’espace de noms associé au schéma de propriété en modifiant la chaîne dans les zones appropriées **préfixe** champ de colonne.</span><span class="sxs-lookup"><span data-stu-id="bfa38-121">Optionally, you can change the namespace prefix associated with the property schema by changing the string in the appropriate **Prefix** column field.</span></span>  
  
8.  <span data-ttu-id="bfa38-122">Avec le nœud à promouvoir est toujours sélectionné dans l’arborescence de schéma sur le côté gauche de la **promouvoir les propriétés** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-122">With the node to be promoted still selected in the schema tree on the left side of the **Promote Properties** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="bfa38-123">Si autorisé, le nœud sélectionné est ajouté à la fin de la **liste de champs de propriété** sur la **champs de propriété** onglet. Sinon, une zone de message fournit une explication</span><span class="sxs-lookup"><span data-stu-id="bfa38-123">If allowed, the selected node is added to the end of the **Property Fields List** on the **Property Fields** tab. If not allowed, a message box provides an explanation.</span></span> <span data-ttu-id="bfa38-124">Si non autorisée, la **ajouter** bouton n’est pas activé.</span><span class="sxs-lookup"><span data-stu-id="bfa38-124">If not allowed, the **Add** button is not enabled.</span></span>  
  
9. <span data-ttu-id="bfa38-125">Double-cliquez sur **propriété** cellule de colonne pour la ligne que vous venez d’ajouter à la **liste de champs de propriété**, puis, dans la liste déroulante, sélectionnez le **schéma de propriété** et correspondant **élément de champ** nœud dans lequel vous souhaitez promouvoir le nœud sélectionné.</span><span class="sxs-lookup"><span data-stu-id="bfa38-125">Double-click **Property** column cell for the row you just added to the **Property Fields List**, and then in the drop-down list, select the **Property Schema** and corresponding **Field Element** node into which you want to promote the selected node.</span></span> <span data-ttu-id="bfa38-126">Les valeurs de liste déroulante ont le format x : y, où X est le préfixe d’espace de noms d’un schéma de propriété dans le **liste des schémas de propriété**, et Y est le nom du nœud d’un **élément de champ** nœud ce schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="bfa38-126">Drop-down list values have the form X:Y, where X is the namespace prefix of a property schema in the **Property Schemas List**, and Y is the node name of a **Field Element** node in that property schema.</span></span>  
  
     <span data-ttu-id="bfa38-127">La valeur par défaut dans la liste déroulante est le premier schéma de propriété **(élément de champ)** nœud qui n’a pas encore été promu, triées par ordre alphabétique sur tous les schémas de propriété pertinents.</span><span class="sxs-lookup"><span data-stu-id="bfa38-127">The default value in the drop-down list is the first property schema **(Field Element)** node that has not yet been promoted, sorted alphabetically across all relevant property schemas.</span></span> <span data-ttu-id="bfa38-128">Il s'agira rarement du nœud de schéma de propriété dans lequel vous avez l'intention de promouvoir un nœud de schéma donné.</span><span class="sxs-lookup"><span data-stu-id="bfa38-128">This will rarely be the property schema node into which you intend to promote a given schema node.</span></span>  
  
10. <span data-ttu-id="bfa38-129">Vous pouvez sélectionner pour la promotion des nœuds supplémentaires dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue en cliquant sur **ajouter** et puis effectuez l’étape 9 après chaque sélection.</span><span class="sxs-lookup"><span data-stu-id="bfa38-129">You can select additional nodes for promotion in the schema tree on the left side of the dialog box, clicking **Add** and then performing step 9 after each selection.</span></span>  
  
11. <span data-ttu-id="bfa38-130">Lorsque vous avez terminé, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-130">When complete, click **OK**.</span></span>  
  
     <span data-ttu-id="bfa38-131">Les nœuds que vous avez sélectionné pour promouvoir sont désormais **champs de propriété** et sont associés à un particulier **élément de champ** nœud dans un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="bfa38-131">The nodes that you selected to promote are now **Property Fields** and are associated with a particular **Field Element** node in a property schema.</span></span>  
  
### <a name="to-promote-a-property-as-a-property-field-using-the-quick-promotion-command"></a><span data-ttu-id="bfa38-132">Pour promouvoir une propriété en tant que champ de propriété à l'aide de l'option Promotion rapide</span><span class="sxs-lookup"><span data-stu-id="bfa38-132">To promote a property as a Property Field using the Quick Promotion command</span></span>  
  
1.  <span data-ttu-id="bfa38-133">Dans l’Éditeur BizTalk, ouvrez le schéma pour lequel vous souhaitez promouvoir une ou plusieurs propriétés, puis sélectionnez le (premier) **Fieldelement**, **attribut de champ**, ou **enregistrement** nœud que vous souhaitez promouvoir en tant qu’un **champ de propriété**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-133">In BizTalk Editor, open the schema for which you want to promote one or more properties, and then select the (first) **Field Element**, **Field Attribute**, or **Record** node that you want to promote as a **Property Field**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bfa38-134">Vous pouvez uniquement promouvoir **enregistrement** nœuds s’ils sont configurés pour qu’il contienne uniquement du contenu simple en ayant sa **Content Type** propriété **SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-134">You can only promote **Record** nodes if they are configured to contain only simple content by having its **Content Type** property set to **SimpleContent**.</span></span>  
  
2.  <span data-ttu-id="bfa38-135">Cliquez sur le nœud sélectionné, cliquez sur **promouvoir**, puis cliquez sur **Promotion rapide**.</span><span class="sxs-lookup"><span data-stu-id="bfa38-135">Right-click the selected node, click **Promote**, and then click **Quick Promotion**.</span></span>  
  
     <span data-ttu-id="bfa38-136">Si le schéma de propriété par défaut, comme défini par le **nom de schéma de propriété par défaut** propriété sur le **Pages de propriétés** pour le schéma pertinent, n’existe pas, vous devez cliquer sur **OK**dans la boîte de dialogue de confirmation pour créer le schéma de propriété par défaut et le configurer avec une **élément de champ** nœud pour prendre en compte votre promotion de propriétés.</span><span class="sxs-lookup"><span data-stu-id="bfa38-136">If the default property schema, as defined by the **Default Property Schema Name** property on the **Property Pages** for the relevant schema, does not exist, you must click **OK** in the confirmation dialog to create the default property schema and configure it with an appropriate **Field Element** node to accommodate your property promotion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfa38-137">Vous pouvez afficher et gérer les propriétés promues à l’aide de la **Promotions rapides** fonctionnalité en ouvrant le **promouvoir les propriétés** boîte de dialogue, puis cliquez sur le **champs de propriété** onglet. Pour obtenir des instructions pour l’ouverture du **promouvoir les propriétés** boîte de dialogue, consultez [ouverture de la boîte de dialogue promouvoir les propriétés](../core/how-to-open-the-promote-properties-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="bfa38-137">You can view and manage properties promoted using the **Quick Promotions** feature by opening the **Promote Properties** dialog box and then clicking the **Property Fields** tab. For step-by-step instructions for opening the **Promote Properties** dialog box, see [Opening the Promote Properties Dialog Box](../core/how-to-open-the-promote-properties-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa38-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfa38-138">See Also</span></span>  
 <span data-ttu-id="bfa38-139">[Promotion des propriétés](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bfa38-139">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 <span data-ttu-id="bfa38-140">[Comment créer des schémas de propriété](../core/how-to-create-property-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="bfa38-140">[How to Create Property Schemas](../core/how-to-create-property-schemas.md) </span></span>  
 [<span data-ttu-id="bfa38-141">Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle</span><span class="sxs-lookup"><span data-stu-id="bfa38-141">Ways to Use Message Content to Control Message Processing</span></span>](../core/ways-to-use-message-content-to-control-message-processing.md)