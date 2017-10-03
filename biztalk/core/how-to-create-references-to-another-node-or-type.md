---
title: "Comment créer des références à un autre nœud ou Type | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c60be9ad-01a9-40e7-b43b-8c3d09bbb32f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 643f39b9a42e2566f77371096d7305f56e11a328
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-references-to-another-node-or-type"></a><span data-ttu-id="75f80-102">Créer des références à un autre nœud ou Type</span><span class="sxs-lookup"><span data-stu-id="75f80-102">Create References to Another Node or Type</span></span>
<span data-ttu-id="75f80-103">Vous pouvez utiliser des nœuds globaux pour créer des types de données, ou fragments de structure, réutilisables dont vous pouvez vous servir dans votre schéma dès lors que cette structure est appropriée.</span><span class="sxs-lookup"><span data-stu-id="75f80-103">You can use global nodes to create reusable data types—fragments of structure—that you can use throughout the schema wherever that structure is appropriate.</span></span> <span data-ttu-id="75f80-104">Vous pouvez utiliser uniquement les nœuds qui sont des enfants directs de la **schéma** nœud pour créer des types globaux.</span><span class="sxs-lookup"><span data-stu-id="75f80-104">You can only use nodes that are direct children of the **Schema** node to create global types.</span></span>  
  
 <span data-ttu-id="75f80-105">Vous pouvez également créer des références cycliques à l’aide des types de données des nœuds qui ne sont pas des descendants directs du **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="75f80-105">You can also create cyclical references using the data types of nodes that are not direct descendants of the **Schema** node.</span></span> <span data-ttu-id="75f80-106">Cela se révèle utile pour représenter des structures récursives dans des schémas.</span><span class="sxs-lookup"><span data-stu-id="75f80-106">This is useful for representing recursive structures in schemas.</span></span>  
  
 <span data-ttu-id="75f80-107">Cette rubrique fournit des instructions étape par étape concernant différents types de nœuds globaux ainsi qu'à propos de la manière d'y faire référence pour les utiliser.</span><span class="sxs-lookup"><span data-stu-id="75f80-107">This topic provides step-by-step instructions for various types of global nodes and how to refer to them to use them.</span></span>  
  
 <span data-ttu-id="75f80-108">**Création de déclarations globales**</span><span class="sxs-lookup"><span data-stu-id="75f80-108">**Creating Global Declarations**</span></span>  
  
 <span data-ttu-id="75f80-109">Vous pouvez créer des types globaux à l'aide d'enregistrements, de champs ou d'attributs.</span><span class="sxs-lookup"><span data-stu-id="75f80-109">You can create global types using records, fields or attributes.</span></span> <span data-ttu-id="75f80-110">Les types globaux créés à partir d'enregistrements ne peuvent être utilisés que dans les enregistrements. De même, les types créés à partir de champs ne peuvent être utilisés que dans les champs et les types d'attribut ne peuvent être utilisés que dans les attributs.</span><span class="sxs-lookup"><span data-stu-id="75f80-110">Global types created from records may only be used in records, types created from fields only in fields, attribute types only in attributes.</span></span> <span data-ttu-id="75f80-111">Les procédures suivantes décrivent comment définir et utiliser des déclarations globales.</span><span class="sxs-lookup"><span data-stu-id="75f80-111">The following procedures describe how to define and use global declarations.</span></span>  
  
## <a name="create-a-global-declaration-from-a-node"></a><span data-ttu-id="75f80-112">Créer une déclaration globale à partir d’un nœud</span><span class="sxs-lookup"><span data-stu-id="75f80-112">Create a global declaration from a node</span></span>  
  
1.  <span data-ttu-id="75f80-113">Sélectionnez le **enregistrement** , **attribut de champ**, ou **élément de champ** dont vous souhaitez rendre disponible globalement le type de nœud.</span><span class="sxs-lookup"><span data-stu-id="75f80-113">Select the **Record** , **Field Attribute**,or **Field Element** node whose type you want to make globally available.</span></span>  
  
2.  <span data-ttu-id="75f80-114">Dans le **propriétés** fenêtre, tapez un nom dans la **Data Structure Type** liste qui sera utilisé comme nom global pour le type complexe et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="75f80-114">In the **Properties** window, type a name in the **Data Structure Type** list that will be used as the global name for the complex type, and then press ENTER.</span></span>  
  
## <a name="create-a-globally-defined-sequence-group-node-choice-group-node-or-all-group-node"></a><span data-ttu-id="75f80-115">Créer un nœud de groupe séquence définie globalement, nœud groupe choix ou nœud groupe tous</span><span class="sxs-lookup"><span data-stu-id="75f80-115">Create a globally defined Sequence Group node, Choice Group node, or All Group node</span></span>  
  
1.  <span data-ttu-id="75f80-116">Sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le nœud groupe globalement défini.</span><span class="sxs-lookup"><span data-stu-id="75f80-116">Select the **Record** node into which you want to insert the globally defined group node.</span></span>  
  
2.  <span data-ttu-id="75f80-117">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe séquence**, **groupe choix**, ou **toutes les Groupe**, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="75f80-117">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sequence Group**, **Choice Group**, or **All Group**, as appropriate.</span></span>  
  
3.  <span data-ttu-id="75f80-118">Créez une structure dans le groupe nouvellement inséré.</span><span class="sxs-lookup"><span data-stu-id="75f80-118">Create a structure in the newly inserted group.</span></span> <span data-ttu-id="75f80-119">Par exemple, insérez **enregistrement** ou **élément de champ** nœuds pour exprimer la structure des données dans le nœud de groupe.</span><span class="sxs-lookup"><span data-stu-id="75f80-119">For example, insert **Record** or **Field Element** nodes to express the structure of the data within the group node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75f80-120">Groupe de séquences, **groupe choix**, et **groupe tous** nœuds peuvent uniquement contenir des nœuds qui correspondent à des éléments XML et par conséquent pas contenir **attribut de champ** nœuds.</span><span class="sxs-lookup"><span data-stu-id="75f80-120">Sequence Group, **Choice Group**, and **All Group** nodes can only contain nodes that correspond to XML elements and therefore cannot contain **Field Attribute** nodes.</span></span>  
  
4.  <span data-ttu-id="75f80-121">Sélectionnez le nœud de groupe inséré à l'étape 2.</span><span class="sxs-lookup"><span data-stu-id="75f80-121">Select the group node inserted in step 2.</span></span>  
  
5.  <span data-ttu-id="75f80-122">Dans la fenêtre Propriétés, cliquez sur **référence du groupe**, tapez un nom dans le champ valeur, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="75f80-122">In the Properties window, click **Group Reference**, type a name into the value field, and then press ENTER.</span></span>  
  
     <span data-ttu-id="75f80-123">En fournissant un nom dans la **référence du groupe** propriété, vous avez défini globalement le nœud de groupe, après laquelle vous pouvez associer d’autres nœuds de groupe avec ce type globalement défini (structure).</span><span class="sxs-lookup"><span data-stu-id="75f80-123">By providing a name in the **Group Reference** property, you have globally defined group node, after which you can associate other group nodes with this globally defined type (structure).</span></span>  
  
## <a name="create-a-globally-defined-attribute-group-node"></a><span data-ttu-id="75f80-124">Créer un nœud groupe attribut globalement défini</span><span class="sxs-lookup"><span data-stu-id="75f80-124">Create a globally defined Attribute Group node</span></span>  
  
1.  <span data-ttu-id="75f80-125">Sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer globalement défini **groupe d’attributs** nœud.</span><span class="sxs-lookup"><span data-stu-id="75f80-125">Select the **Record** node into which you want to insert the globally defined **Attribute Group** node.</span></span>  
  
2.  <span data-ttu-id="75f80-126">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe d’attributs**.</span><span class="sxs-lookup"><span data-stu-id="75f80-126">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Attribute Group**.</span></span>  
  
     <span data-ttu-id="75f80-127">Cette opération ajoute une **groupe d’attributs** à la fin des nœuds enfants du nœud de **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="75f80-127">This adds an **Attribute Group** node to the end of the child nodes in the selected **Record** node.</span></span>  
  
3.  <span data-ttu-id="75f80-128">Ajouter les **attribut de champ** ou **groupe d’attributs** nœuds à votre **groupe d’attributs**.</span><span class="sxs-lookup"><span data-stu-id="75f80-128">Add the appropriate **Field Attribute** or **Attribute Group** nodes to your **Attribute Group**.</span></span>  
  
4.  <span data-ttu-id="75f80-129">Si vous le souhaitez, si vous souhaitez renommer le **groupe d’attributs** nœud, sélectionnez le **groupe d’attributs** nœud et modifier son **référence du groupe** propriété à un nouveau nom de votre choix.</span><span class="sxs-lookup"><span data-stu-id="75f80-129">Optionally, if you want to rename the **Attribute Group** node, select the **Attribute Group** node and change its **Group Reference** property to a new name of your choosing.</span></span>  
  
     <span data-ttu-id="75f80-130">Les groupes d'attributs sont toujours globaux et référencés à partir de leur point d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="75f80-130">Attribute groups are always global and referenced from their point of use.</span></span>  
  
## <a name="use-a-type-or-group-that-has-been-globally-defined"></a><span data-ttu-id="75f80-131">Utiliser un type ou un groupe qui a été globalement défini</span><span class="sxs-lookup"><span data-stu-id="75f80-131">Use a type or group that has been globally defined</span></span>  
  
1.  <span data-ttu-id="75f80-132">Sélectionnez le nœud pour lequel vous souhaitez utiliser un type globalement défini.</span><span class="sxs-lookup"><span data-stu-id="75f80-132">Select the node for which you want to use a globally defined type.</span></span>  
  
2.  <span data-ttu-id="75f80-133">Dans la fenêtre Propriétés, sélectionnez le type globalement défini dans la liste déroulante pour le **Data Structure Type** propriété (**enregistrement** nœuds), **Type de données** (depropriété **Élément de champ** et **attribut de champ** nœuds), ou **référence du groupe** (**groupe séquence**, **le groupe choix**, **Groupe tous**, et **groupe d’attributs** nœuds).</span><span class="sxs-lookup"><span data-stu-id="75f80-133">In the Properties window, select the globally defined type from the drop-down list for the **Data Structure Type** property (**Record** nodes), **Data Type** property (**Field Element** and **Field Attribute** nodes), or **Group Reference** (**Sequence Group**, **Choice Group**, **All Group**, and **Attribute Group** nodes).</span></span> <span data-ttu-id="75f80-134">Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="75f80-134">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="75f80-135">Les changements apportés ultérieurement au type ou groupe globalement défini peuvent être effectués dans tous les emplacements de schéma où il apparaît.</span><span class="sxs-lookup"><span data-stu-id="75f80-135">Subsequent changes to the globally defined type or group can be made in any of the schema locations in which it appears.</span></span> <span data-ttu-id="75f80-136">Ces modifications seront appliquées à tous ces emplacements au fur et à mesure que vous les apporterez dans l'emplacement unique arbitraire.</span><span class="sxs-lookup"><span data-stu-id="75f80-136">These changes will be applied in all such locations as you make them in the single, arbitrary location.</span></span>  
  
 <span data-ttu-id="75f80-137">Une fois que vous avez créé une déclaration globale, vous êtes dans l'impossibilité de la supprimer en une seule étape.</span><span class="sxs-lookup"><span data-stu-id="75f80-137">After you have created a global declaration, you cannot delete it in a single step.</span></span> <span data-ttu-id="75f80-138">Toutefois, vous pouvez la supprimer à l’aide de la **les types de données globaux nettoyage** boîte de dialogue lorsque le schéma est enregistré, à l’aide de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="75f80-138">However, you can delete it by using the **Cleanup Global DataTypes** dialog box when the schema is saved, using the following procedure.</span></span>  
  
## <a name="delete-a-global-declaration"></a><span data-ttu-id="75f80-139">Supprimer une déclaration globale</span><span class="sxs-lookup"><span data-stu-id="75f80-139">Delete a global declaration</span></span>  
  
1.  <span data-ttu-id="75f80-140">Supprimez tous les nœuds dans lesquels ce type ou ce groupe global est utilisé, ou spécifiez un autre type ou groupe à utiliser dans tous ces nœuds, ou combinez ces deux opérations.</span><span class="sxs-lookup"><span data-stu-id="75f80-140">Delete all of the nodes where this global type or group is used, or specify a different type or group to be used in all of those nodes, or some combination thereof.</span></span> <span data-ttu-id="75f80-141">Pour obtenir des instructions pour la suppression d’un nœud, consultez [suppression de nœuds](../core/how-to-delete-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="75f80-141">For step-by-step instructions for deleting a node, see [Deleting Nodes](../core/how-to-delete-nodes.md).</span></span>  
  
2.  <span data-ttu-id="75f80-142">Lors de l’enregistrement de la spécification, la **les types de données globaux nettoyage** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="75f80-142">Upon saving your specification, the **Cleanup Global DataTypes** dialog box appears.</span></span> <span data-ttu-id="75f80-143">Sélectionnez la déclaration globale que vous souhaitez supprimer complètement de votre spécification, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="75f80-143">Select the global declaration you want to completely delete from your specification, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75f80-144">Le **les types de données globaux nettoyage** boîte de dialogue s’affiche chaque fois que vous enregistrez un schéma avec les types de données inutilisé.</span><span class="sxs-lookup"><span data-stu-id="75f80-144">The **Cleanup Global DataTypes** dialog box appears every time you save a schema with unused data types.</span></span> <span data-ttu-id="75f80-145">Si cette boîte de dialogue n'apparaît pas, c'est soit que tous les types de données sont utilisés quelque part dans le schéma, soit que le schéma n'a pas été modifié depuis son ouverture, auquel cas il contient peut-être encore des types de données non utilisés précédemment conservés.</span><span class="sxs-lookup"><span data-stu-id="75f80-145">If this dialog box does not appear, either all data types are used somewhere in the schema or the schema has not been modified since it was opened (in the latter case, it might still contain unused data types that were previously retained.</span></span>  
  
## <a name="create-cyclical-references-to-another-node"></a><span data-ttu-id="75f80-146">Créer des références cycliques à un autre nœud</span><span class="sxs-lookup"><span data-stu-id="75f80-146">Create Cyclical References to Another Node</span></span>  
 <span data-ttu-id="75f80-147">Vous pouvez créer des références cycliques à un nœud pour représenter des éléments récursifs de schéma.</span><span class="sxs-lookup"><span data-stu-id="75f80-147">You can create cyclical references to a node to represent recursive schema elements.</span></span> <span data-ttu-id="75f80-148">Pour ce faire, vous devez créer un nœud dont le type est défini par un enregistrement associé.</span><span class="sxs-lookup"><span data-stu-id="75f80-148">You do this by creating a node whose type is defined by an enclosing record.</span></span> <span data-ttu-id="75f80-149">Imaginez par exemple un message d'instance intégré dans un nombre arbitraire d'enveloppes partageant la même structure.</span><span class="sxs-lookup"><span data-stu-id="75f80-149">For example, consider an instance message that is wrapped in an arbitrary number of envelopes having the same structure.</span></span> <span data-ttu-id="75f80-150">À l'aide de références cycliques, vous pouvez créer un schéma définissant de tels messages d'instance.</span><span class="sxs-lookup"><span data-stu-id="75f80-150">Using cyclical references, you can create a schema that defines such instance messages.</span></span>  
  
### <a name="create-a-cyclical-reference"></a><span data-ttu-id="75f80-151">Créer une référence cyclique</span><span class="sxs-lookup"><span data-stu-id="75f80-151">Create a cyclical reference</span></span>  
  
1.  <span data-ttu-id="75f80-152">Sélectionnez un **enregistrement** nœud pour lequel vous voulez créer une référence récursive.</span><span class="sxs-lookup"><span data-stu-id="75f80-152">Select a **Record** node for which you want to create a recursive reference.</span></span> <span data-ttu-id="75f80-153">Il s'agit du nœud représentant la partie supérieure de la structure récursive.</span><span class="sxs-lookup"><span data-stu-id="75f80-153">This is the node representing the top of the recursive structure.</span></span>  
  
2.  <span data-ttu-id="75f80-154">Dans la fenêtre Propriétés, vérifiez que le **Data Structure Type** a une valeur.</span><span class="sxs-lookup"><span data-stu-id="75f80-154">In the Properties window, verify that the **Data Structure Type** has a value.</span></span>  
  
     <span data-ttu-id="75f80-155">Vérifier que le **enregistrement** nœud dispose d’un jeu nommé type associé est nécessaire, car les structures récursives sont définies lorsqu’un type contient lui-même.</span><span class="sxs-lookup"><span data-stu-id="75f80-155">Verifying that the **Record** node has a named type associated with it is necessary because recursive structures are defined when a type contains itself.</span></span> <span data-ttu-id="75f80-156">Les types ne peuvent se contenir eux-mêmes que via une utilisation imbriquée de types globaux nommés.</span><span class="sxs-lookup"><span data-stu-id="75f80-156">Types can only contain themselves through nested use of named global types.</span></span>  
  
3.  <span data-ttu-id="75f80-157">Sélectionnez un enfant **enregistrement** nœud enfant ou insérez un **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="75f80-157">Select a child **Record** node or insert a child **Record** node.</span></span>  
  
4.  <span data-ttu-id="75f80-158">Pour l’enfant **enregistrement** nœud, dans la fenêtre Propriétés, dans le **Data Structure Type** , sélectionnez la structure de données identifiée à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="75f80-158">For the child **Record** node, in the Properties window, in the **Data Structure Type** list, select the data structure identified in step 2.</span></span>  
  
> [!IMPORTANT]
>  - <span data-ttu-id="75f80-159">Le **Min Occurs** propriété du nœud répété doit être définie sur zéro (**0**).</span><span class="sxs-lookup"><span data-stu-id="75f80-159">The **Min Occurs** property for the repeating node must be set to zero (**0**).</span></span> <span data-ttu-id="75f80-160">Sa définition sur un (**1**) provoque une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="75f80-160">Setting it to one (**1**) causes an infinite loop.</span></span>  
>
>  - <span data-ttu-id="75f80-161">Si vous importez un schéma qui contient un élément récursif, l'Éditeur BizTalk ne vérifie pas automatiquement que ce dernier est valide.</span><span class="sxs-lookup"><span data-stu-id="75f80-161">If you import a schema that contains a recursive element, BizTalk Editor does not automatically check to ensure that the recursive element is valid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f80-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75f80-162">See Also</span></span>  
 [<span data-ttu-id="75f80-163">Gestion des nœuds dans un schéma</span><span class="sxs-lookup"><span data-stu-id="75f80-163">Managing the Nodes Within a Schema</span></span>](../core/managing-the-nodes-within-a-schema.md)