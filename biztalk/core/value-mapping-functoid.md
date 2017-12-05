---
title: Fonctoid Mappage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Value Mapping functoids
- functoids, empty tags
- Concatenate functoids
ms.assetid: 3dd626fb-3bf6-4ede-9fd2-ddae5a54d178
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 038d59827a62c9f4e83879ec7cf2e0b47fd738f4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="value-mapping-functoid"></a><span data-ttu-id="502f7-102">Fonctoid Mappage</span><span class="sxs-lookup"><span data-stu-id="502f7-102">Value Mapping Functoid</span></span>
<span data-ttu-id="502f7-103">Le **mappage** fonctoid retourne la valeur de son deuxième paramètre si son premier paramètre a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="502f7-103">The **Value Mapping** functoid returns the value of its second parameter if its first parameter is true.</span></span> <span data-ttu-id="502f7-104">Un fonctoid sert souvent à modifier les attributs d'un champ en attributs d'un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="502f7-104">A common use of the functoid is to change the attributes of a field into the attributes of a record.</span></span> <span data-ttu-id="502f7-105">Pour mettre à plat une partie d’un message d’entrée en convertissant plusieurs enregistrements en un seul enregistrement, utilisez la [fonctoid Mappage des valeurs (mise à plat)](../core/value-mapping-flattening-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="502f7-105">To flatten a portion of an input message by converting multiple records into a single record, use the [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).</span></span>  
  
 <span data-ttu-id="502f7-106">La figure suivante illustre un mappage avec le **mappage** fonctoid permet de modifier les attributs d’un champ en attributs d’un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="502f7-106">The following figure shows a map with the **Value Mapping** functoid used to change the attributes of a field into the attributes of a record.</span></span>  
  
 <span data-ttu-id="502f7-107">![](../core/media/valuemappingfunctoid.gif "valuemappingfunctoid")</span><span class="sxs-lookup"><span data-stu-id="502f7-107">![](../core/media/valuemappingfunctoid.gif "valuemappingfunctoid")</span></span>  
<span data-ttu-id="502f7-108">Mappage du fonctoid Mappage des valeurs</span><span class="sxs-lookup"><span data-stu-id="502f7-108">Value Mapping Functoid Map</span></span>  
  
 <span data-ttu-id="502f7-109">Le code suivant montre un message d’instance d’entrée dans les paires de noms et valeurs sont assignées aux **nom** et **valeur** attributs.</span><span class="sxs-lookup"><span data-stu-id="502f7-109">The following code shows an input instance message in which pairs of names and values are assigned to **Name** and **Value** attributes.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherIn">  
    <Record>  
        <Field Name="WindSpeed" Value="5"/>   
        <Field Name="Temperature" Value="20" />  
    </Record>  
    <Record>  
        <Field Name="WindSpeed" Value="15" />  
        <Field Name="Temperature" Value="18" />  
    </Record>  
</ns0:Root>  
```  
  
 <span data-ttu-id="502f7-110">Le mappage précédent convertit le message en une version dans laquelle les valeurs sont affectées aux attributs avec les noms correspondants dans des enregistrements séparés.</span><span class="sxs-lookup"><span data-stu-id="502f7-110">The preceding map can convert this message into one in which the values are assigned to attributes with the corresponding names in separate records.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherOut">  
    <Record WindSpeed="5"/>  
    <Record Temperature="20"/>  
    <Record WindSpeed="15"/>  
    <Record Temperature="18"/>  
</ns0:Root>  
```  
  
 <span data-ttu-id="502f7-111">Le **égal** fonctoids testent les valeurs de la **nom** attribut.</span><span class="sxs-lookup"><span data-stu-id="502f7-111">The **Equal** functoids test the values of the **Name** attribute.</span></span> <span data-ttu-id="502f7-112">La première **égal** fonctoid teste la valeur de **nom** « windspeed ».</span><span class="sxs-lookup"><span data-stu-id="502f7-112">The first **Equal** functoid tests for the value of **Name** being "WindSpeed."</span></span> <span data-ttu-id="502f7-113">Lorsque le **nom** est « WindSpeed », la première **égal** fonctoid retourne **True**.</span><span class="sxs-lookup"><span data-stu-id="502f7-113">When the **Name** is "WindSpeed," the first **Equal** functoid returns **True**.</span></span> <span data-ttu-id="502f7-114">À son tour, ainsi le **mappage** fonctoid pour définir la valeur de la **WindSpeed** attribut dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="502f7-114">This, in turn, allows the **Value Mapping** functoid to set the value of the **WindSpeed** attribute in the output instance message.</span></span>  
  
## <a name="suppressing-the-creation-of-empty-tags"></a><span data-ttu-id="502f7-115">Suppression de la création de balises vides</span><span class="sxs-lookup"><span data-stu-id="502f7-115">Suppressing the Creation of Empty Tags</span></span>  
 <span data-ttu-id="502f7-116">Pour supprimer des balises vides, utilisez le fonctoid Mappage des valeurs pour vérifier si une balise doit être créée ou non.</span><span class="sxs-lookup"><span data-stu-id="502f7-116">To suppress empty tags, use the Value Mapping functoid to control if a tag gets created or not.</span></span> <span data-ttu-id="502f7-117">Si la valeur de la condition est true, le champ de destination sera créé, sinon, il ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="502f7-117">If the value is evaluated to true, the destination field will be created; otherwise the destination field will not be created.</span></span> <span data-ttu-id="502f7-118">Dans un scénario de bouclage, utilisez un fonctoid logique et connectez-le à l'enregistrement ou au champ de destination.</span><span class="sxs-lookup"><span data-stu-id="502f7-118">In a looping scenario, use a logical functoid and connect it to the destination record or field.</span></span> <span data-ttu-id="502f7-119">Si la condition a la valeur false, la balise ne sera pas créée.</span><span class="sxs-lookup"><span data-stu-id="502f7-119">If the condition is evaluated to false, the tag will not be created.</span></span> <span data-ttu-id="502f7-120">Pour obtenir un exemple, consultez [bouclage conditionnel](../core/conditional-looping.md).</span><span class="sxs-lookup"><span data-stu-id="502f7-120">For an example, see [Conditional Looping](../core/conditional-looping.md).</span></span>  
  
## <a name="forcing-the-creation-of-empty-tags"></a><span data-ttu-id="502f7-121">Création forcée de balises vides</span><span class="sxs-lookup"><span data-stu-id="502f7-121">Forcing the Creation of Empty Tags</span></span>  
 <span data-ttu-id="502f7-122">Pour forcer la création de balises vides, vous pouvez ajouter une valeur dans la propriété valeur du champ de destination ou de lien un **Concatenate** fonctoid pour le champ de destination.</span><span class="sxs-lookup"><span data-stu-id="502f7-122">To force empty tags to be created, you can add a value in the Value property of the destination field or link a **Concatenate** functoid to the destination field.</span></span>  <span data-ttu-id="502f7-123">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est possible de forcer la génération de balises vides en sélectionnant la «\<vide\>« valeur de la propriété de la valeur du champ de destination.</span><span class="sxs-lookup"><span data-stu-id="502f7-123">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is possible to force the generation of empty tags by selecting the "\<empty\>" value in the Value property of the destination field.</span></span> <span data-ttu-id="502f7-124">Dans ce cas, le champ sera créé avec la valeur vide.</span><span class="sxs-lookup"><span data-stu-id="502f7-124">In this case the field will be created with the empty value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502f7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="502f7-125">See Also</span></span>  
 <span data-ttu-id="502f7-126">[(Mise à plat) fonctoid Mappage](../core/value-mapping-flattening-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="502f7-126">[Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md) </span></span>  
 <span data-ttu-id="502f7-127">[Comment ajouter des fonctoids de mappage à un mappage de valeur](../core/how-to-add-value-mapping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="502f7-127">[How to Add Value Mapping Functoids to a Map](../core/how-to-add-value-mapping-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="502f7-128">Fonctoids avancés</span><span class="sxs-lookup"><span data-stu-id="502f7-128">Advanced Functoids</span></span>](../core/advanced-functoids.md)