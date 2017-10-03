---
title: "Comment créer des définitions de vocabulaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, creating
- vocabularies, definitions
ms.assetid: 6f8fc4c2-2c46-4a7d-a02f-89de0396e3e2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff9fdfc7cd444a97d1a24353c13d93460c00d4ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-vocabulary-definitions"></a><span data-ttu-id="464b7-102">Comment créer des définitions de vocabulaire</span><span class="sxs-lookup"><span data-stu-id="464b7-102">How to Create Vocabulary Definitions</span></span>
<span data-ttu-id="464b7-103">Vous pouvez utiliser l'Assistant Définition de vocabulaire pour créer des définitions de vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="464b7-103">You can use the Vocabulary Definition Wizard to create vocabulary definitions.</span></span> <span data-ttu-id="464b7-104">Vous pouvez définir une définition de vocabulaire en tant que valeur constante, plage de valeurs, ensemble de valeurs ou éléments d'un assembly .NET, d'un document XML ou d'une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="464b7-104">You can define a vocabulary definition as a constant value, a range of values, a set of values, or elements of a .NET assembly, XML document, or database table.</span></span> <span data-ttu-id="464b7-105">Si vous sélectionnez une variable publique, il y aura **obtenir** et **définir** options de la même façon que dans l’Assistant Définition de base de données et XML.</span><span class="sxs-lookup"><span data-stu-id="464b7-105">If you select a public variable, there will be **Get** and **Set** options just like in Database and XML definition wizard.</span></span>  
  
 <span data-ttu-id="464b7-106">Vous pouvez également créer une définition de vocabulaire en sélectionnant un fait à partir d’un des trois onglets : par exemple, une colonne de base de données, un nœud XML ou un membre d’une classe .NET, en faisant glisser le fait sur pour le **vocabulaires** onglet, et sa suppression à une version non publiée d’un vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="464b7-106">Alternatively, you can create a new vocabulary definition by selecting a fact from one of the three tabs—for example, a database column, an XML node, or a member of a .NET class—dragging the fact over to the **Vocabularies** tab, and dropping it to an unpublished version of a vocabulary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="464b7-107">Vous ne pouvez pas ajouter une définition de vocabulaire à une version de vocabulaire qui a été publiée.</span><span class="sxs-lookup"><span data-stu-id="464b7-107">You cannot add a vocabulary definition to a vocabulary version that has been published.</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-constant-value"></a><span data-ttu-id="464b7-108">Pour définir une définition de vocabulaire en tant que valeur constante</span><span class="sxs-lookup"><span data-stu-id="464b7-108">To define a vocabulary definition as a constant value</span></span>  
  
1.  <span data-ttu-id="464b7-109">Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="464b7-109">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-110">Vous pouvez également faire glisser des éléments à partir d’autres onglets de l’Explorateur de faits : schémas XML, des bases de données et des Classes .NET</span><span class="sxs-lookup"><span data-stu-id="464b7-110">You can also drag and drop items from other tabs of Fact Explorer: XML Schemas, Databases and .NET Classes</span></span>  
  
2.  <span data-ttu-id="464b7-111">Dans l’Assistant Définition de vocabulaire, sélectionnez **valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-111">In the Vocabulary Definition Wizard, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="464b7-112">Modifiez le nom et la description de la définition.</span><span class="sxs-lookup"><span data-stu-id="464b7-112">Edit the definition name and definition description.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-113">La longueur maximale d'un nom complet de définition est de 512 caractères.</span><span class="sxs-lookup"><span data-stu-id="464b7-113">The maximum length for a definition display name is 512 characters.</span></span>  
  
4.  <span data-ttu-id="464b7-114">Sélectionnez **valeur constante**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-114">Select **Constant Value**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="464b7-115">Dans la liste déroulante des types de systèmes disponibles, sélectionnez un type de définition.</span><span class="sxs-lookup"><span data-stu-id="464b7-115">Select a definition type from the drop-down list of available system types.</span></span>  
  
6.  <span data-ttu-id="464b7-116">Modifiez le nom d’affichage et la valeur, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-116">Edit the display name and value, and then click **Finish**.</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-range-of-values"></a><span data-ttu-id="464b7-117">Pour définir une définition de vocabulaire en tant que plage de valeurs</span><span class="sxs-lookup"><span data-stu-id="464b7-117">To define a vocabulary definition as a range of values</span></span>  
  
1.  <span data-ttu-id="464b7-118">Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="464b7-118">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="464b7-119">Dans l’Assistant Définition de vocabulaire, sélectionnez **valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-119">In the Vocabulary Definition Wizard, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="464b7-120">Modifiez le nom et la description de la définition.</span><span class="sxs-lookup"><span data-stu-id="464b7-120">Edit the definition name and definition description.</span></span>  
  
4.  <span data-ttu-id="464b7-121">Sélectionnez **plage de valeurs**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-121">Select **Range of Values**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="464b7-122">Sélectionnez un type de définition dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="464b7-122">Select a definition type from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="464b7-123">Cliquez sur **plage inférieure**, puis cliquez sur **modifier** pour spécifier les valeurs de la plage inférieure.</span><span class="sxs-lookup"><span data-stu-id="464b7-123">Click **Range Low**, and then click **Edit** to specify the values for the lower range.</span></span> <span data-ttu-id="464b7-124">La boîte de dialogue de définition de paramètre s'ouvre alors.</span><span class="sxs-lookup"><span data-stu-id="464b7-124">The parameter definition dialog will be opened.</span></span>  
  
7.  <span data-ttu-id="464b7-125">Sélectionnez **utiliser une valeur constante** et entrer une valeur constante, ou sélectionnez **utiliser une définition d’un vocabulaire publié** et accédez à une définition de vocabulaire, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="464b7-125">Select **Use Constant Value** and enter a constant value, or select **Use Definition from a Published Vocabulary** and browse to a vocabulary definition, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="464b7-126">Répétez les étapes 6 et 7 pour **plage supérieure**.</span><span class="sxs-lookup"><span data-stu-id="464b7-126">Repeat steps 6 and 7 for **Range High**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-127">Le **plage supérieure** valeur doit dépasser la **plage inférieure** valeur.</span><span class="sxs-lookup"><span data-stu-id="464b7-127">The **Range High** value must exceed the **Range Low** value.</span></span>  
  
9. <span data-ttu-id="464b7-128">Tapez la chaîne de format d’affichage ou cliquez sur **par défaut** pour revenir à la chaîne de format d’affichage par défaut, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-128">Type the display format string or click **Default** to revert to the default display format string, and then click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-129">Votre format de chaîne doit inclure des index de paramètre dans des accolades, par exemple, « {0} » et « {1}"—to servent d’espaces réservés pour les paramètres de la plage haute et basse.</span><span class="sxs-lookup"><span data-stu-id="464b7-129">Your format string should include parameter indexes in curly braces—for example, "{0}" and "{1}"—to serve as placeholders for the high and low range parameters.</span></span>  
  
     <span data-ttu-id="464b7-130">![Définitions de vocabulaire](../core/media/3db84492-d6b8-4059-9d2c-a720ccc207b6.gif "3db84492-d6b8-4059-9d2c-a720ccc207b6")</span><span class="sxs-lookup"><span data-stu-id="464b7-130">![Vocabulary Definitions](../core/media/3db84492-d6b8-4059-9d2c-a720ccc207b6.gif "3db84492-d6b8-4059-9d2c-a720ccc207b6")</span></span>  
<span data-ttu-id="464b7-131">Plage de valeurs avec format de chaîne</span><span class="sxs-lookup"><span data-stu-id="464b7-131">Range of values with formatted string</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-set-of-values"></a><span data-ttu-id="464b7-132">Pour définir une définition de vocabulaire en tant qu'ensemble de valeurs</span><span class="sxs-lookup"><span data-stu-id="464b7-132">To define a vocabulary definition as a set of values</span></span>  
  
1.  <span data-ttu-id="464b7-133">Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="464b7-133">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="464b7-134">Dans l’Assistant Définition de vocabulaire, sélectionnez **valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-134">In the Vocabulary Definition Wizard, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="464b7-135">Modifiez le nom et la description de la définition.</span><span class="sxs-lookup"><span data-stu-id="464b7-135">Edit the definition name and definition description.</span></span>  
  
4.  <span data-ttu-id="464b7-136">Sélectionnez **ensemble de valeurs**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-136">Select **Set of Values**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="464b7-137">Entrez le type de la définition et son nom complet.</span><span class="sxs-lookup"><span data-stu-id="464b7-137">Enter the definition type and display name.</span></span>  
  
6.  <span data-ttu-id="464b7-138">Pour ajouter un membre à l’ensemble, sélectionnez **utiliser une valeur constante** et entrer une valeur constante, ou sélectionnez **utiliser une définition d’un vocabulaire publié** et accédez à une définition de vocabulaire, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="464b7-138">To add a member to the set, select **Use Constant Value** and enter a constant value, or select **Use Definition from a Published Vocabulary** and browse to a vocabulary definition, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="464b7-139">Recommencez l'étape 6 avec n'importe quelle combinaison de constantes ou de définitions de vocabulaire, pour tous les éléments que vous souhaitez inclure dans votre ensemble.</span><span class="sxs-lookup"><span data-stu-id="464b7-139">Repeat step 6, with any combination of constants or vocabulary definitions, for as many items as you want to include in your set.</span></span>  
  
8.  <span data-ttu-id="464b7-140">Pour déplacer un membre dans l’ordre relatif de l’ensemble, sélectionnez-le, puis **des** ou **vers le bas**.</span><span class="sxs-lookup"><span data-stu-id="464b7-140">To move a member within the relative order of the set, select it and then click **Up** or **Down**.</span></span>  
  
9. <span data-ttu-id="464b7-141">Pour supprimer un membre de l’ensemble, sélectionnez-le, puis **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-141">To remove a member from the set, select it and then click **Remove**.</span></span>  
  
10. <span data-ttu-id="464b7-142">Lorsque vous avez terminé votre jeu, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-142">When you have completed your set, click **Finish**.</span></span>  
  
     <span data-ttu-id="464b7-143">![Définitions de vocabulaire](../core/media/461d0d70-52ed-4f43-927d-3efb1fbfb934.gif "461d0d70-52ed-4f43-927d-3efb1fbfb934")</span><span class="sxs-lookup"><span data-stu-id="464b7-143">![Vocabulary Definitions](../core/media/461d0d70-52ed-4f43-927d-3efb1fbfb934.gif "461d0d70-52ed-4f43-927d-3efb1fbfb934")</span></span>  
<span data-ttu-id="464b7-144">Ensemble de valeurs</span><span class="sxs-lookup"><span data-stu-id="464b7-144">Set of values</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-a-net-class-or-class-member"></a><span data-ttu-id="464b7-145">Pour définir une définition de vocabulaire en tant que classe .Net ou que membre de classe</span><span class="sxs-lookup"><span data-stu-id="464b7-145">To define a vocabulary definition as a .NET class or class member</span></span>  
  
1.  <span data-ttu-id="464b7-146">Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="464b7-146">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="464b7-147">Dans l’Assistant Définition de vocabulaire, sélectionnez **classe .NET ou membre de classe**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-147">In the Vocabulary Definition Wizard, select **.NET Class or Class Member**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="464b7-148">Modifier la **nom de la définition** et **Description** champs.</span><span class="sxs-lookup"><span data-stu-id="464b7-148">Edit the **Definition Name** and **Description** fields.</span></span>  
  
4.  <span data-ttu-id="464b7-149">Cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="464b7-149">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="464b7-150">Dans le **assemblys .NET** boîte de dialogue, sélectionnez un assembly, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="464b7-150">In the **.NET Assemblies** dialog box, select an assembly, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-151">Les assemblys doivent se trouver dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="464b7-151">The assemblies have to be in the global assembly cache (GAC).</span></span> <span data-ttu-id="464b7-152">L’éditeur des règles d’entreprise charge un assembly .NET lorsque vous recherchez l’assembly .NET dans le **l’Explorateur de faits** fenêtre ou dans le **classe .NET ou définition de membre de classe** page de la **vocabulaire Définition** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="464b7-152">The business rule composer loads a .NET assembly when you browse for the .NET assembly in the **Facts Explorer** window or in the **.NET Class or Class Member Definition** page of the **Vocabulary Definition** window.</span></span>  <span data-ttu-id="464b7-153">Si vous mettez à jour l'assembly dans le GAC, fermez l'Éditeur des règles d'entreprise et redémarrez-le afin de charger l'assembly .NET mis à jour.</span><span class="sxs-lookup"><span data-stu-id="464b7-153">If you update the assembly in the GAC, close the business rule composer and restart it to load the updated .NET assembly.</span></span> <span data-ttu-id="464b7-154">L'actualisation n'est en effet pas automatique.</span><span class="sxs-lookup"><span data-stu-id="464b7-154">The business rule composer does not refresh the assembly automatically.</span></span>  
  
6.  <span data-ttu-id="464b7-155">Développez le nœud de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="464b7-155">Expand the assembly node.</span></span>  
  
7.  <span data-ttu-id="464b7-156">Sélectionnez une classe ou développez une classe et sélectionnez un membre de classe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="464b7-156">Select a class, or expand a class and select a class member, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="464b7-157">Cliquez sur **suivant**et spécifiez le nom complet.</span><span class="sxs-lookup"><span data-stu-id="464b7-157">Click **Next**, and specify the display name.</span></span>  
  
     <span data-ttu-id="464b7-158">Pour plus d'informations, voir la section « Pour spécifier le format d'affichage d'une définition de vocabulaire à l'aide de paramètres » plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="464b7-158">For more information, see "To specify the display format of a vocabulary definition by using parameters" later in this topic.</span></span>  
  
9. <span data-ttu-id="464b7-159">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-159">Click **Finish**.</span></span>  
  
     <span data-ttu-id="464b7-160">![Définitions de vocabulaire](../core/media/4259101f-26dd-488f-81c0-f8d225e4016e.gif "4259101f-26dd-488f-81c0-f8d225e4016e")</span><span class="sxs-lookup"><span data-stu-id="464b7-160">![Vocabulary Definitions](../core/media/4259101f-26dd-488f-81c0-f8d225e4016e.gif "4259101f-26dd-488f-81c0-f8d225e4016e")</span></span>  
<span data-ttu-id="464b7-161">Définition de vocabulaire d'objets .NET</span><span class="sxs-lookup"><span data-stu-id="464b7-161">Net object vocabulary definition</span></span>  
  
### <a name="to-define-a-vocabulary-definition-as-an-xml-document-element-or-attribute"></a><span data-ttu-id="464b7-162">Pour définir une définition de vocabulaire en tant qu'élément ou attribut de document XML</span><span class="sxs-lookup"><span data-stu-id="464b7-162">To define a vocabulary definition as an XML document element or attribute</span></span>  
  
1.  <span data-ttu-id="464b7-163">Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="464b7-163">Right-click the vocabulary version, and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="464b7-164">Dans l’Assistant Définition de vocabulaire, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-164">In the Vocabulary Definition Wizard, select **XML Document Element or Attribute**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="464b7-165">Tapez un nom de définition et une description de la définition.</span><span class="sxs-lookup"><span data-stu-id="464b7-165">Type a definition name and a definition description.</span></span>  
  
4.  <span data-ttu-id="464b7-166">Cliquez sur **Parcourir** pour localiser un fichier de schéma et de spécifier un attribut ou élément de document.</span><span class="sxs-lookup"><span data-stu-id="464b7-166">Click **Browse** to locate a schema file and specify a document element or attribute.</span></span>  
  
5.  <span data-ttu-id="464b7-167">Dans la liste déroulante, sélectionnez un type compatible avec celui de l'élément ou de l'attribut du schéma.</span><span class="sxs-lookup"><span data-stu-id="464b7-167">From the drop-down list, select a type that is compatible with the type of the element or attribute in the schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-168">Si aucun cast valide ne peut être effectué vers ou à partir du type spécifié dans le type de l'élément ou de l'attribut du document, un message d'erreur s'affichera lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="464b7-168">If a valid cast cannot be done to or from the specified type to the type of the document element or attribute, you will get an error at run time.</span></span>  
  
6.  <span data-ttu-id="464b7-169">Sélectionnez un type d'opération selon que vous souhaitez obtenir la valeur de l'élément ou de l'attribut, ou définir sa valeur.</span><span class="sxs-lookup"><span data-stu-id="464b7-169">Select an operation type to indicate whether you plan to get the value of the element or attribute, or to set its value.</span></span>  
  
7.  <span data-ttu-id="464b7-170">Si vous avez choisi de définir la valeur, cliquez sur **suivant**, puis spécifiez le format d’affichage.</span><span class="sxs-lookup"><span data-stu-id="464b7-170">If you chose to set the value, click **Next**, and then specify the display format.</span></span>  
  
8.  <span data-ttu-id="464b7-171">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-171">Click **Finish**.</span></span>  
  
     <span data-ttu-id="464b7-172">![Définitions de vocabulaire](../core/media/fd81b534-ec41-4147-b716-1e10ffc01d6f.gif "fd81b534-ec41-4147-b716-1e10ffc01d6f")</span><span class="sxs-lookup"><span data-stu-id="464b7-172">![Vocabulary Definitions](../core/media/fd81b534-ec41-4147-b716-1e10ffc01d6f.gif "fd81b534-ec41-4147-b716-1e10ffc01d6f")</span></span>  
<span data-ttu-id="464b7-173">Définition de vocabulaire XML</span><span class="sxs-lookup"><span data-stu-id="464b7-173">XML vocabulary definition</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="464b7-174">L'existence de l'élément défini et du type de document n'est jamais validée.</span><span class="sxs-lookup"><span data-stu-id="464b7-174">The existence of the defined element and the document type is never validated.</span></span> <span data-ttu-id="464b7-175">Si le document déclaré ne comporte pas l'élément, une erreur d'exécution se produira.</span><span class="sxs-lookup"><span data-stu-id="464b7-175">If the asserted document does not have the element, you will get a runtime error.</span></span> <span data-ttu-id="464b7-176">Si vous déclarez un document d'un type inconnu, il sera tout simplement ignoré.</span><span class="sxs-lookup"><span data-stu-id="464b7-176">If you assert a document with unknown document type, it will simply be ignored.</span></span>  
  
#### <a name="to-define-a-vocabulary-definition-as-a-database-table-or-database-table-column"></a><span data-ttu-id="464b7-177">Pour définir une définition de vocabulaire en tant que table de base de données ou que colonne de table de base de données</span><span class="sxs-lookup"><span data-stu-id="464b7-177">To define a vocabulary definition as a database table or database table column</span></span>  
  
1.  <span data-ttu-id="464b7-178">Avec le bouton droit de la version de vocabulaire, puis cliquez sur **ajouter une nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="464b7-178">Right-click the vocabulary version and then click **Add New Definition**.</span></span>  
  
2.  <span data-ttu-id="464b7-179">Dans l’Assistant Définition de vocabulaire, sélectionnez **Table de base de données ou la définition de colonne de Table de base de données**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="464b7-179">In the Vocabulary Definition Wizard, select **Database Table or Database Table Column Definition**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="464b7-180">Tapez un nom et une description de définition.</span><span class="sxs-lookup"><span data-stu-id="464b7-180">Type a definition name and definition description.</span></span>  
  
4.  <span data-ttu-id="464b7-181">Cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="464b7-181">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="464b7-182">Sélectionnez un ordinateur SQL Server avec lequel établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="464b7-182">Select a SQL Server computer to connect with.</span></span> <span data-ttu-id="464b7-183">Si l’ordinateur SQL Server n’est pas démarré, sélectionnez le **démarrer SQL Server s’il est arrêté** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="464b7-183">If the SQL Server computer is not currently started, select the **Start SQL Server if it is stopped** check box.</span></span>  
  
6.  <span data-ttu-id="464b7-184">Sélectionnez un type d'authentification.</span><span class="sxs-lookup"><span data-stu-id="464b7-184">Select an authentication type.</span></span> <span data-ttu-id="464b7-185">Si vous sélectionnez l’authentification SQL Server, tapez votre nom de connexion et un mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="464b7-185">If you select SQL Server authentication, type your logon name and password, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="464b7-186">Sélectionnez la table ou la colonne de table que vous souhaitez lier, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="464b7-186">Select the table or table column that you want to bind to, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="464b7-187">Si vous avez sélectionné une colonne de table, vous devez choisir entre obtenir sa valeur et définir sa valeur.</span><span class="sxs-lookup"><span data-stu-id="464b7-187">If you selected a table column, select whether you want to get its value or set its value.</span></span> <span data-ttu-id="464b7-188">Si vous choisissez de définir sa valeur, tapez le nom complet.</span><span class="sxs-lookup"><span data-stu-id="464b7-188">If you choose to get its value, type the display name.</span></span> <span data-ttu-id="464b7-189">Si vous choisissez de définir sa valeur, cliquez sur **suivant** pour spécifier le format d’affichage.</span><span class="sxs-lookup"><span data-stu-id="464b7-189">If you choose to set its value, click **Next** to specify the display format.</span></span>  
  
     <span data-ttu-id="464b7-190">Pour plus d'informations, voir la section « Pour spécifier le format d'affichage d'une définition de vocabulaire à l'aide de paramètres » plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="464b7-190">For more information, see "To specify the display format of a vocabulary definition by using parameters" later in this topic.</span></span>  
  
9. <span data-ttu-id="464b7-191">Si vous avez sélectionné une table, tapez un nom complet.</span><span class="sxs-lookup"><span data-stu-id="464b7-191">If you selected a table, type a display name.</span></span>  
  
10. <span data-ttu-id="464b7-192">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-192">Click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-193">Par défaut, **DataConnection** liaison est utilisée.</span><span class="sxs-lookup"><span data-stu-id="464b7-193">By default, **DataConnection** binding is used</span></span>  
  
     <span data-ttu-id="464b7-194">![Définitions de vocabulaire](../core/media/f8121306-cd73-4997-adc4-71a055dfd824.gif "f8121306-cd73-4997-adc4-71a055dfd824")</span><span class="sxs-lookup"><span data-stu-id="464b7-194">![Vocabulary Definitions](../core/media/f8121306-cd73-4997-adc4-71a055dfd824.gif "f8121306-cd73-4997-adc4-71a055dfd824")</span></span>  
<span data-ttu-id="464b7-195">Définition de vocabulaire de base de données</span><span class="sxs-lookup"><span data-stu-id="464b7-195">Database vocabulary definition</span></span>  
  
#### <a name="to-specify-the-display-format-of-a-vocabulary-definition-by-using-parameters"></a><span data-ttu-id="464b7-196">Pour spécifier le format d'affichage d'une définition de vocabulaire à l'aide de paramètres</span><span class="sxs-lookup"><span data-stu-id="464b7-196">To specify the display format of a vocabulary definition by using parameters</span></span>  
  
1.  <span data-ttu-id="464b7-197">Sélectionnez un paramètre dans la liste des **paramètres** dans l’Assistant Définition de vocabulaire, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="464b7-197">Select a parameter from the list of **Parameters** in Vocabulary Definition Wizard, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="464b7-198">Sélectionnez **utiliser une valeur constante** et entrer une valeur constante, ou sélectionnez **utiliser une définition d’un vocabulaire publié** et accédez à une définition de vocabulaire, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="464b7-198">Select **Use Constant Value** and enter a constant value, or select **Use Definition from a Published Vocabulary** and browse to a vocabulary definition, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="464b7-199">Tapez la chaîne de format d’affichage ou cliquez sur **par défaut** pour revenir à la chaîne de format d’affichage par défaut, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="464b7-199">Type the display format string or click **Default** to revert to the default display format string, and then click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="464b7-200">Votre format de chaîne doit inclure des index de paramètre dans des accolades, par exemple, « {0} » et « {1}"—to servent d’espaces réservés pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="464b7-200">Your format string should include parameter indexes in curly braces—for example, "{0}" and "{1}"—to serve as placeholders for the parameters.</span></span>  
  
     <span data-ttu-id="464b7-201">![Définitions de vocabulaire](../core/media/822f78f4-278a-4211-83ad-44032fa81f13.gif "822f78f4-278a-4211-83ad-44032fa81f13")</span><span class="sxs-lookup"><span data-stu-id="464b7-201">![Vocabulary Definitions](../core/media/822f78f4-278a-4211-83ad-44032fa81f13.gif "822f78f4-278a-4211-83ad-44032fa81f13")</span></span>  
<span data-ttu-id="464b7-202">Définition de paramètres à l'aide de paramètres</span><span class="sxs-lookup"><span data-stu-id="464b7-202">Vocabulary definition with parameters</span></span>