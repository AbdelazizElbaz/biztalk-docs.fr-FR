---
title: "Mise à jour2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 770c9ebb-df3a-428f-be18-b36535352f8d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4376cae94e91f462974c626a57170b80b0117ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update"></a><span data-ttu-id="82d07-102">Update</span><span class="sxs-lookup"><span data-stu-id="82d07-102">Update</span></span>
<span data-ttu-id="82d07-103">L'élément `Update` permet d'extraire des données d'un événement et de les importer dans l'activité BAM associée.</span><span class="sxs-lookup"><span data-stu-id="82d07-103">The `Update` element is used to extract data from an event and import it into the related BAM activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="82d07-104">Format</span><span class="sxs-lookup"><span data-stu-id="82d07-104">Format</span></span>  
 <span data-ttu-id="82d07-105">Pour utiliser le `Update` élément, vous devez fournir un nom de colonne et le type et un **Expression** élément contenant un ou plusieurs **opération** les éléments qui correspondent à une valeur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="82d07-105">To use the `Update` element, you must provide both a column name and type and an **Expression** element containing one or more **Operation** elements that evaluate to a single string value.</span></span>  
  
```  
<ic:Update DataItemName="Name" Type="Type">  
  <ic:Expression>  
    <!-- one or more Operation elements -->  
  </ic:Expression>  
</ic:Update>  
```  
  
### <a name="attributes"></a><span data-ttu-id="82d07-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="82d07-106">Attributes</span></span>  
  
|<span data-ttu-id="82d07-107">Nom de l'attribut</span><span class="sxs-lookup"><span data-stu-id="82d07-107">Attribute name</span></span>|<span data-ttu-id="82d07-108"> Description</span><span class="sxs-lookup"><span data-stu-id="82d07-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="82d07-109">ColumnName</span><span class="sxs-lookup"><span data-stu-id="82d07-109">ColumnName</span></span>|<span data-ttu-id="82d07-110">Nom du point de contrôle de l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="82d07-110">BAM activity checkpoint name.</span></span> <span data-ttu-id="82d07-111">Il s'agit du point de contrôle qui est mis à jour avec les données extraites.</span><span class="sxs-lookup"><span data-stu-id="82d07-111">This is the checkpoint that will be updated with the extracted data.</span></span>|  
|<span data-ttu-id="82d07-112">Type</span><span class="sxs-lookup"><span data-stu-id="82d07-112">Type</span></span>|<span data-ttu-id="82d07-113">Type de données BAM du point de contrôle, qui doit être l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="82d07-113">BAM data type of the checkpoint; must be one of the following:</span></span><br /><br /> <span data-ttu-id="82d07-114">-NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="82d07-114">-   NVARCHAR</span></span><br /><span data-ttu-id="82d07-115">-DATETIME</span><span class="sxs-lookup"><span data-stu-id="82d07-115">-   DATETIME</span></span><br /><span data-ttu-id="82d07-116">-INT</span><span class="sxs-lookup"><span data-stu-id="82d07-116">-   INT</span></span><br /><span data-ttu-id="82d07-117">-FLOAT</span><span class="sxs-lookup"><span data-stu-id="82d07-117">-   FLOAT</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82d07-118">Notes</span><span class="sxs-lookup"><span data-stu-id="82d07-118">Remarks</span></span>  
 <span data-ttu-id="82d07-119">Les opérations suivantes ne sont pas prises en charge dans l'expression `Update` :</span><span class="sxs-lookup"><span data-stu-id="82d07-119">The following operations are not supported in the `Update` expression:</span></span>  
  
-   <span data-ttu-id="82d07-120">And</span><span class="sxs-lookup"><span data-stu-id="82d07-120">And</span></span>  
  
-   <span data-ttu-id="82d07-121">Égal à</span><span class="sxs-lookup"><span data-stu-id="82d07-121">Equals</span></span>  
  
## <a name="example"></a><span data-ttu-id="82d07-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="82d07-122">Example</span></span>  
 <span data-ttu-id="82d07-123">Dans l’exemple suivant, la **GetContextProperty** opération WF est utilisée pour récupérer le **EventTime** propriété.</span><span class="sxs-lookup"><span data-stu-id="82d07-123">In the following example, the **GetContextProperty** WF operation is used to retrieve the **EventTime** property.</span></span> <span data-ttu-id="82d07-124">Cette valeur est stockée en tant qu’un **DATETIME** type pour l’élément de données « StartOrderProcessing » pour l’activité BAM.</span><span class="sxs-lookup"><span data-stu-id="82d07-124">This value will be stored as a **DATETIME** type for the "StartOrderProcessing" data item for the BAM activity.</span></span>  
  
```  
<ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82d07-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d07-125">See Also</span></span>  
 [<span data-ttu-id="82d07-126">Élément OnEvent de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="82d07-126">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)