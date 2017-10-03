---
title: "Référence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b916c55a-c84c-4008-8927-f8e584c36fe9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3e32145e2340a4d86a6893db3e9209b79c2b5e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reference"></a><span data-ttu-id="79a10-102">Référence</span><span class="sxs-lookup"><span data-stu-id="79a10-102">Reference</span></span>
<span data-ttu-id="79a10-103">Le **référence** élément peut être utilisé pour ajouter une ou plusieurs relations à une activité BAM.</span><span class="sxs-lookup"><span data-stu-id="79a10-103">The **Reference** element can be used to add one or more relationships to a BAM activity.</span></span> <span data-ttu-id="79a10-104">Cela s'avère utile lorsque vous souhaitez associer un pointeur tel qu'une clé primaire, un ID ou une URL à un message lui correspondant.</span><span class="sxs-lookup"><span data-stu-id="79a10-104">This is useful when you want to attach a pointer like a primary key, ID, or URL to a related message.</span></span> <span data-ttu-id="79a10-105">Par exemple, vous voulez peut-être stocker une référence à un lot d'expéditions d'une activité Purchase Order.</span><span class="sxs-lookup"><span data-stu-id="79a10-105">For example, you might store a reference to a Shipment Batch in a Purchase Order activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="79a10-106">Format</span><span class="sxs-lookup"><span data-stu-id="79a10-106">Format</span></span>  
 <span data-ttu-id="79a10-107">Le `Reference` élément prend en charge à la fois le **données** et **LongData** des éléments enfants qui contiennent une expression spécifiant les données à associer à l’activité BAM.</span><span class="sxs-lookup"><span data-stu-id="79a10-107">The `Reference` element supports both the **Data** and **LongData** child elements that contain an expression specifying the data to attach to the BAM activity.</span></span> <span data-ttu-id="79a10-108">Vous pouvez utiliser n’importe quelle combinaison de **données** et **LongData** pour répondre à vos exigences de suivi.</span><span class="sxs-lookup"><span data-stu-id="79a10-108">You can use any combination of **Data** and **LongData** to meet your tracking requirements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79a10-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="79a10-109">Attributes</span></span>  
  
|<span data-ttu-id="79a10-110">Nom de l'attribut</span><span class="sxs-lookup"><span data-stu-id="79a10-110">Attribute name</span></span>|<span data-ttu-id="79a10-111"> Description</span><span class="sxs-lookup"><span data-stu-id="79a10-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="79a10-112">Nom</span><span class="sxs-lookup"><span data-stu-id="79a10-112">Name</span></span>|<span data-ttu-id="79a10-113">Nom de la relation à associer à l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="79a10-113">Name of the relationship that will be attached to the BAM activity.</span></span>|  
|<span data-ttu-id="79a10-114">Type</span><span class="sxs-lookup"><span data-stu-id="79a10-114">Type</span></span>|<span data-ttu-id="79a10-115">Chaîne arbitraire spécifiant le type de relation à associer à l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="79a10-115">Arbitrary string specifying the type of relationship that will be attached to the BAM activity.</span></span> <span data-ttu-id="79a10-116">Les chaînes arbitraires et les types BAM prédéfinis suivants sont pris en charge :</span><span class="sxs-lookup"><span data-stu-id="79a10-116">Both arbitrary strings and the following predefined BAM types are supported:</span></span><br /><br /> <span data-ttu-id="79a10-117">-BizTalkService</span><span class="sxs-lookup"><span data-stu-id="79a10-117">-   BizTalkService</span></span><br /><span data-ttu-id="79a10-118">-MessageID</span><span class="sxs-lookup"><span data-stu-id="79a10-118">-   MessageID</span></span><br /><span data-ttu-id="79a10-119">-Activité</span><span class="sxs-lookup"><span data-stu-id="79a10-119">-   Activity</span></span><br /><span data-ttu-id="79a10-120">-DocumentUrl</span><span class="sxs-lookup"><span data-stu-id="79a10-120">-   DocumentUrl</span></span><br /><span data-ttu-id="79a10-121">-InstanceID</span><span class="sxs-lookup"><span data-stu-id="79a10-121">-   InstanceID</span></span><br /><br /> <span data-ttu-id="79a10-122">Pour plus d’informations sur les types de référence BAM prédéfinis, consultez [propriétés de la référence](http://go.microsoft.com/fwlink/?LinkId=119601).</span><span class="sxs-lookup"><span data-stu-id="79a10-122">For more information on predefined BAM reference types, see [Reference Properties](http://go.microsoft.com/fwlink/?LinkId=119601).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79a10-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="79a10-123">Child Elements</span></span>  
  
|<span data-ttu-id="79a10-124">État de l'exécution</span><span class="sxs-lookup"><span data-stu-id="79a10-124">Execution status</span></span>|<span data-ttu-id="79a10-125"> Description</span><span class="sxs-lookup"><span data-stu-id="79a10-125">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="79a10-126">data</span><span class="sxs-lookup"><span data-stu-id="79a10-126">Data</span></span>|<span data-ttu-id="79a10-127">Indique le mode d'extraction des données de chaîne (jusqu'à 128 caractères) qui seront associées à l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="79a10-127">Specifies how to extract string data up to 128 characters that will be attached to the BAM activity.</span></span>|  
|<span data-ttu-id="79a10-128">LongData</span><span class="sxs-lookup"><span data-stu-id="79a10-128">LongData</span></span>|<span data-ttu-id="79a10-129">Indique le mode d'extraction des données de chaîne longue arbitraire qui seront associées à l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="79a10-129">Specifies how to extract arbitrarily long string data that will be attached to the BAM activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="79a10-130">A `Reference` élément peut combiner un ou plusieurs **données** et **LongData** des éléments enfants en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="79a10-130">A `Reference` element can combine one or more **Data** and **LongData** child elements as needed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79a10-131">Notes</span><span class="sxs-lookup"><span data-stu-id="79a10-131">Remarks</span></span>  
 <span data-ttu-id="79a10-132">Les opérations communes suivantes ne sont pas autorisées dans les expressions Reference :</span><span class="sxs-lookup"><span data-stu-id="79a10-132">The following common operations are not allowed in Reference expressions:</span></span>  
  
-   <span data-ttu-id="79a10-133">And</span><span class="sxs-lookup"><span data-stu-id="79a10-133">And</span></span>  
  
-   <span data-ttu-id="79a10-134">Égal à</span><span class="sxs-lookup"><span data-stu-id="79a10-134">Equals</span></span>  
  
## <a name="example"></a><span data-ttu-id="79a10-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="79a10-135">Example</span></span>  
 <span data-ttu-id="79a10-136">Dans l'exemple suivant, une référence intitulée « Related Document » du type « DocumentUrl » est créée à l'aide de l'opération `GetUserData` pour un workflow.</span><span class="sxs-lookup"><span data-stu-id="79a10-136">In the following sample, a reference named "Related Document" of type "DocumentUrl" is created using `GetUserData` for a workflow.</span></span> <span data-ttu-id="79a10-137">Compte tenu que la longueur attendue des données utilisateur doit être inférieure à 1 024 caractères, l'élément `Data` est utilisé pour contenir l'élément `Expression`.</span><span class="sxs-lookup"><span data-stu-id="79a10-137">Because the user data is expected to be fewer than 1024 characters in length, the `Data` element is used to contain the `Expression` element.</span></span>  
  
```  
<ic:Reference Name="Related Document" Type="DocumentUrl">  
  <ic:Data>  
    <ic:Expression>  
      <wf:Operation Name="GetUserData" />  
    </ic:Expression>  
  </ic:Data>  
</ic:Reference>  
```  
  
 <span data-ttu-id="79a10-138">Le **référence** élément prend en charge un mélange de `Data` et `LongData` éléments.</span><span class="sxs-lookup"><span data-stu-id="79a10-138">The **Reference** element supports a mix of `Data` and `LongData` elements.</span></span> <span data-ttu-id="79a10-139">Dans l'exemple suivant, les champs relatifs au nom du pays et aux remarques d'un bon de commande sont récupérés à partir d'un service WCF, puis ils sont écrits dans la relation « Long and Short Data » comme le type « MyType ».</span><span class="sxs-lookup"><span data-stu-id="79a10-139">In the following sample, the country name and note fields from a purchase order are retrieved from a WCF service and written to the relationship "Long and Short Data" as type "MyType".</span></span> <span data-ttu-id="79a10-140">Étant donné que la longueur prise en charge dans le champ de remarques est supérieure à 1 024 caractères, l'expression est intégrée à un élément `LongData`.</span><span class="sxs-lookup"><span data-stu-id="79a10-140">Because the note field supports more than 1024 characters, the expression is enclosed in a `LongData` element.</span></span>  
  
```  
<ic:Reference Name="Long and Short Data" Type="MyType">  
  <ic:Data>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Country: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Country</wcf:Argument>  
      </wcf:Operation>  
       <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:Data>  
  <ic:LongData>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Note: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Note</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:LongData>  
</ic:Reference>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79a10-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79a10-141">See Also</span></span>  
 <span data-ttu-id="79a10-142">[Élément OnEvent de l’intercepteur](../core/interceptor-onevent-element.md) </span><span class="sxs-lookup"><span data-stu-id="79a10-142">[Interceptor OnEvent Element](../core/interceptor-onevent-element.md) </span></span>  
 [<span data-ttu-id="79a10-143">Méthode EventStream.AddRelatedActivity</span><span class="sxs-lookup"><span data-stu-id="79a10-143">EventStream.AddRelatedActivity Method</span></span>](http://go.microsoft.com/fwlink/?LinkId=119602)