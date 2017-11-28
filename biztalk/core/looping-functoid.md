---
title: Fonctoid Bouclage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19886ccb-4642-48a4-b93e-563640ea828b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ce2b66fd796708a0e8b24ee05e3a0b043af6808
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="looping-functoid"></a><span data-ttu-id="5751c-102">Fonctoid Bouclage</span><span class="sxs-lookup"><span data-stu-id="5751c-102">Looping Functoid</span></span>

## <a name="overview--example"></a><span data-ttu-id="5751c-103">Vue d’ensemble et exemple</span><span class="sxs-lookup"><span data-stu-id="5751c-103">Overview & example</span></span>
<span data-ttu-id="5751c-104">Le **bouclage** fonctoid combine plusieurs enregistrements ou champs du schéma source en un enregistrement unique dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="5751c-104">The **Looping** functoid combines multiple records or fields in the source schema into a single record in the destination schema.</span></span>  
  
 <span data-ttu-id="5751c-105">L’illustration suivante montre un **bouclage**fonctoid utilisé dans un mappage pour combiner les adresses collectées à partir de deux enquêtes différentes en une liste d’adresses principale unique.</span><span class="sxs-lookup"><span data-stu-id="5751c-105">The following figure shows a **Looping**functoid used in a map to combine addresses collected from two different surveys into a single master address list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5751c-106">Le **bouclage** et **Value Mapping (Flattening)** fonctoids ne doivent pas être utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="5751c-106">The **Looping** and **Value Mapping (Flattening)** functoids should not be used together.</span></span> <span data-ttu-id="5751c-107">Si les deux sont utilisés ensemble, il en résulte un mappage compilé qui suppose il n’y a aucun dépendance pour les nœuds cibles situés au-dessous de bouclage source le **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="5751c-107">If both are used together, it results in a compiled map that assumed there is no source looping dependency for the target nodes that are below the **Looping** functoid.</span></span>  
  
 <span data-ttu-id="5751c-108">![Mappage illustrant l’utilisation du fonctoid Bouclage. ] (../core/media/loopingfunctoid.gif "loopingfunctoid")</span><span class="sxs-lookup"><span data-stu-id="5751c-108">![Map illustrating the use of the looping functoid.](../core/media/loopingfunctoid.gif "loopingfunctoid")</span></span>  
  
 <span data-ttu-id="5751c-109">Le **FoodSurvey** et **FlowerSurvey** des enregistrements de boucle du schéma source sont mappés sur le bouclage **adresse** enregistrement du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="5751c-109">The **FoodSurvey** and **FlowerSurvey** looping records of the source schema are mapped to the looping **Address** record of the destination schema.</span></span> <span data-ttu-id="5751c-110">Si un message d’instance d’entrée possède trois **FoodSurvey** enregistrements et deux **FlowerSurvey** enregistrements, les **bouclage**fonctoid combine pour créer cinq  **Adresse** enregistrements dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="5751c-110">If an input instance message has three **FoodSurvey** records and two **FlowerSurvey** records, the **Looping**functoid combines these to create five **Address** records in the output instance message.</span></span>  
  
 <span data-ttu-id="5751c-111">Le code suivant correspond à un exemple de message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5751c-111">The following code is a sample input instance message.</span></span>  
  
```  
<ns0:Surveys xmlns:ns0="http://LoopingFunctoid.Surveys">  
    <FoodSurvey Name="Karin Zimprich" Address="345 N 63rd St" City="Boston" State="MA" PostalCode="07485" />  
    <FoodSurvey Name="Wendy Wheeler" Address="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" />  
    <FoodSurvey Name="Florian Voss" Address="1234 Main St" City="Denver" State="CO" PostalCode="97402" />  
    <FlowerSurvey Name="Kelly Focht" Address="456 1st Ave" City="Miami" State="FL" PostalCode="81406" />  
    <FlowerSurvey Name="Jim Kim" Address="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" />  
</ns0:Surveys>  
```  
  
 <span data-ttu-id="5751c-112">Le message d’instance d’entrée produit le message d’instance de sortie suivant une fois traité par le mappage de l’illustration précédente.</span><span class="sxs-lookup"><span data-stu-id="5751c-112">This input instance message produces the following output instance message when processed by the map in the preceding figure.</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 <span data-ttu-id="5751c-113">Le **FoodSurvey** et **FlowerSurvey** les adresses de message ont été combinés.</span><span class="sxs-lookup"><span data-stu-id="5751c-113">The **FoodSurvey** and **FlowerSurvey** message addresses have been combined.</span></span> <span data-ttu-id="5751c-114">Le message combiné n'indique pas la source de chaque adresse.</span><span class="sxs-lookup"><span data-stu-id="5751c-114">The combined message does not indicate the source of each address.</span></span> <span data-ttu-id="5751c-115">Si vous souhaitez effectuer le suivi de la source, ajoutez un **Source** d’attribut pour le **adresse** enregistrement de la **MasterAddress** schéma et du mappage d’une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="5751c-115">If you want to track the source, add a **Source** attribute to the **Address** record of the **MasterAddress** schema and map a constant value.</span></span> <span data-ttu-id="5751c-116">Pour définir cette valeur, connectez le **FoodSurvey** champ au nouveau **Source** champ.</span><span class="sxs-lookup"><span data-stu-id="5751c-116">To set this value, connect the **FoodSurvey** field to the new **Source** field.</span></span> <span data-ttu-id="5751c-117">Sur la ligne de connecteur, vous devez modifier le **propriétés des liaisons** &#124; **Compilateur** &#124; **Liaisons sources** propriété « Copier le nom ».</span><span class="sxs-lookup"><span data-stu-id="5751c-117">On the connector line, modify the **Link Properties** &#124; **Compiler** &#124; **Source Links** property to "Copy name".</span></span> <span data-ttu-id="5751c-118">Répétez ce processus pour le **FlowerSurvey** champ.</span><span class="sxs-lookup"><span data-stu-id="5751c-118">Repeat this process for the **FlowerSurvey** field.</span></span> <span data-ttu-id="5751c-119">Le retraitement du message d'entrée à partir des instructions ci-dessus produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5751c-119">Reprocessing the input message from above yields the following output:</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458" Source="FoodSurvey"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" Source="FoodSurvey"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402" Source="FoodSurvey"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406" Source="FlowerSurvey"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" Source="FlowerSurvey"/>  
</ns0:MasterAddresses>  
```  

## <a name="relationships-with-nodes"></a><span data-ttu-id="5751c-120">Relations avec les nœuds</span><span class="sxs-lookup"><span data-stu-id="5751c-120">Relationships with nodes</span></span>

 <span data-ttu-id="5751c-121">Relations entre les nœuds affectent le comportement de la **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="5751c-121">Relationships among nodes affect the behavior of the **Looping** functoid.</span></span> <span data-ttu-id="5751c-122">Par exemple, liaison d’un nœud enfant et son parent dans le schéma source vers le **bouclage** fonctoid empêche le nœud de destination la création.</span><span class="sxs-lookup"><span data-stu-id="5751c-122">For example, linking both a child node and its parent in the source schema to the **Looping** functoid prevents the destination node from being created.</span></span>  
  
 <span data-ttu-id="5751c-123">Les fonctoids sont également affectés par les relations entre des nœuds sources.</span><span class="sxs-lookup"><span data-stu-id="5751c-123">Functoids are also affected by the relationships among source nodes.</span></span> <span data-ttu-id="5751c-124">La connexion d’un fonctoid à des champs enfants non frères de nœuds sources du **bouclage** fonctoid peut produire des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="5751c-124">Connecting a functoid to non-sibling child fields of source nodes of the **Looping** functoid may produce unexpected results.</span></span> <span data-ttu-id="5751c-125">Par exemple, à l’aide de la **concaténation de chaînes** fonctoid pour combiner les **FoodSurvey** champ nom et **FlowerSurvey** champ d’adresse dans le champ nom de l’adresse **MasterAddress** génère le message d’instance de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="5751c-125">For example, using the **String Concatenate** functoid to combine the **FoodSurvey** Name field and **FlowerSurvey** Address field into the Address Name field in **MasterAddress** would produce the following output instance message:</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 <span data-ttu-id="5751c-126">Notez comment la **nom** champ est manquant pour **FoodSurvey** source des messages mais n’est présente pour **FlowerSurvey** messages source.</span><span class="sxs-lookup"><span data-stu-id="5751c-126">Notice how the **Name** field is missing for **FoodSurvey** source messages but is present for **FlowerSurvey** source messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5751c-127">La connexion d’un fonctoid à des champs enfants des nœuds de source de la **bouclage** fonctoid peut produire des résultats inattendus si les nœuds de la source ne sont pas frères.</span><span class="sxs-lookup"><span data-stu-id="5751c-127">Connecting a functoid to child fields of source nodes of the **Looping** functoid may produce unexpected results if the source nodes are not siblings.</span></span>  
  
 <span data-ttu-id="5751c-128">Le **bouclage** fonctoid est une construction puissante que vous pouvez utiliser pour créer des bouclages conditionnels et mapper des schémas à des catalogues.</span><span class="sxs-lookup"><span data-stu-id="5751c-128">The **Looping** functoid is a powerful construct that you can use to create conditional loops and to map schemas to catalogs.</span></span> <span data-ttu-id="5751c-129">Il existe également des effets de chevauchement **bouclage** chemins d’accès de fonctoid vous devez prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="5751c-129">There are also some effects of overlapping **Looping** functoid paths you need to take into account.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5751c-130">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5751c-130">Next steps</span></span>
  
-   [<span data-ttu-id="5751c-131">Bouclage conditionnel</span><span class="sxs-lookup"><span data-stu-id="5751c-131">Conditional Looping</span></span>](../core/conditional-looping.md)  
  
-   [<span data-ttu-id="5751c-132">Schéma plat au catalogue</span><span class="sxs-lookup"><span data-stu-id="5751c-132">Flat Schema to Catalog</span></span>](../core/flat-schema-to-catalog.md)  
  
-   [<span data-ttu-id="5751c-133">Chemins de bouclage</span><span class="sxs-lookup"><span data-stu-id="5751c-133">Loop Paths</span></span>](../core/loop-paths.md)  
  
## <a name="see-also"></a><span data-ttu-id="5751c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5751c-134">See Also</span></span>  
 <span data-ttu-id="5751c-135">**Référence du fonctoid de bouclage de table**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5751c-135">**Table Looping Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>