---
title: "Élément OnEvent de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d684ac8e-61bc-410b-97a2-6fd3549e0d97
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6fb70b2536dbf5db5b0abc03bc194de154b4317
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-onevent-element"></a><span data-ttu-id="e2f6b-102">Élément OnEvent de l'intercepteur</span><span class="sxs-lookup"><span data-stu-id="e2f6b-102">Interceptor OnEvent Element</span></span>
<span data-ttu-id="e2f6b-103">Le **OnEvent** élément décrit un événement réel qui est mappé à l’activité BAM associée.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-103">The **OnEvent** element describes one real event that is mapped to the enclosing BAM activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="e2f6b-104">Format</span><span class="sxs-lookup"><span data-stu-id="e2f6b-104">Format</span></span>  
 <span data-ttu-id="e2f6b-105">L'élément `OnEvent` contient des éléments enfants qui spécifient un filtre d'événements, l'ID de corrélation et, de manière facultative, les données à mettre à jour, les données de référence et un jeton de liaison.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-105">The `OnEvent` element contains child elements that specify an event filter, the correlation ID and optionally which data to update, reference data, and a continuation token.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2f6b-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="e2f6b-106">Attributes</span></span>  
  
|<span data-ttu-id="e2f6b-107">Nom de l'attribut</span><span class="sxs-lookup"><span data-stu-id="e2f6b-107">Attribute name</span></span>|<span data-ttu-id="e2f6b-108"> Description</span><span class="sxs-lookup"><span data-stu-id="e2f6b-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e2f6b-109">Nom</span><span class="sxs-lookup"><span data-stu-id="e2f6b-109">Name</span></span>|<span data-ttu-id="e2f6b-110">Nom défini par l'utilisateur pour cet événement.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-110">User-defined name for this event.</span></span>|  
|<span data-ttu-id="e2f6b-111">Source</span><span class="sxs-lookup"><span data-stu-id="e2f6b-111">Source</span></span>|<span data-ttu-id="e2f6b-112">Nom de l’événement source tel qu’il apparaît dans un **EventSource** élément.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-112">Name of the event source as it appears in an **EventSource** element.</span></span>|  
|<span data-ttu-id="e2f6b-113">IsBegin</span><span class="sxs-lookup"><span data-stu-id="e2f6b-113">IsBegin</span></span>|<span data-ttu-id="e2f6b-114">Valeur booléenne indiquant si l'événement représente le début d'une nouvelle activité BAM (`true`) ou non (`false`).</span><span class="sxs-lookup"><span data-stu-id="e2f6b-114">Boolean value indicating whether the event is the beginning of a new BAM activity (`true`) or not (`false`).</span></span>|  
|<span data-ttu-id="e2f6b-115">IsEnd</span><span class="sxs-lookup"><span data-stu-id="e2f6b-115">IsEnd</span></span>|<span data-ttu-id="e2f6b-116">Valeur booléenne indiquant si l'événement représente la fin d'une activité BAM (`true`) ou non (`false`).</span><span class="sxs-lookup"><span data-stu-id="e2f6b-116">Boolean value indicating whether the event is the end of a BAM activity (`true`) or not (`false`).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2f6b-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e2f6b-117">Child Elements</span></span>  
  
|<span data-ttu-id="e2f6b-118">État de l'exécution</span><span class="sxs-lookup"><span data-stu-id="e2f6b-118">Execution status</span></span>|<span data-ttu-id="e2f6b-119"> Description</span><span class="sxs-lookup"><span data-stu-id="e2f6b-119">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e2f6b-120">Filtrer</span><span class="sxs-lookup"><span data-stu-id="e2f6b-120">Filter</span></span>|<span data-ttu-id="e2f6b-121">Fournit une méthode permettant de restreindre l'événement à des critères spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-121">Provides a way to limit the event to specific criteria.</span></span>|  
|<span data-ttu-id="e2f6b-122">CorrelationID</span><span class="sxs-lookup"><span data-stu-id="e2f6b-122">CorrelationID</span></span>|<span data-ttu-id="e2f6b-123">Indique l'ID de corrélation (l'ID de l'instance d'activité).</span><span class="sxs-lookup"><span data-stu-id="e2f6b-123">Specifies the correlation ID (the activity instance ID).</span></span>|  
|<span data-ttu-id="e2f6b-124">ContinuationToken</span><span class="sxs-lookup"><span data-stu-id="e2f6b-124">ContinuationToken</span></span>|<span data-ttu-id="e2f6b-125">Spécifie le jeton de liaison, c'est-à-dire un ID de corrélation utilisé par des événements futurs qui contribueront à la même instance d'activité.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-125">Specifies the continuation token, a correlation ID that is used by future events that will contribute to the same activity instance.</span></span>|  
|<span data-ttu-id="e2f6b-126">Update</span><span class="sxs-lookup"><span data-stu-id="e2f6b-126">Update</span></span>|<span data-ttu-id="e2f6b-127">Spécifie les données à extraire de l'événement et à importer dans l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-127">Specifies the data to extract from the event and import into the BAM activity.</span></span>|  
|<span data-ttu-id="e2f6b-128">Référence</span><span class="sxs-lookup"><span data-stu-id="e2f6b-128">Reference</span></span>|<span data-ttu-id="e2f6b-129">Ajoute une relation à une activité BAM.</span><span class="sxs-lookup"><span data-stu-id="e2f6b-129">Adds a relationship to a BAM activity.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2f6b-130">Notes</span><span class="sxs-lookup"><span data-stu-id="e2f6b-130">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2f6b-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2f6b-131">Example</span></span>  
 <span data-ttu-id="e2f6b-132">L’exemple suivant montre une manière classique **OnEvent** bloc pour WF :</span><span class="sxs-lookup"><span data-stu-id="e2f6b-132">The following example shows a typical **OnEvent** block for WF:</span></span>  
  
```  
<ic:OnEvent Name="BeginAct" IsBegin="true" Source="ResWF">  
  <ic:Filter>  
    <ic:Expression>  
      <wf:Operation Name="GetActivityName"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <wf:Operation Name="GetActivityEvent"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Closed</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <ic:Operation Name="And"/>  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>InstanceId</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>EventTime</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  <ic:Update DataItemName="FoodItem" Type="NVARCHAR">  
    <ic:Expression>  
      <wf:Operation Name="GetWorkflowProperty">  
        <wf:Argument>foodItem</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
 <span data-ttu-id="e2f6b-133">Cet exemple présente un standard **OnEvent** bloc pour le service WCF :</span><span class="sxs-lookup"><span data-stu-id="e2f6b-133">This example shows a typical **OnEvent** block for WCF service:</span></span>  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="AuthorizationRequestService" Source="ESCreditCardService">  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals"/>  
      <wcf:Operation Name="GetOperationName" />  
      <ic:Operation Name="Constant">  
        <ic:Argument>AuthorizeWithDataContract</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals" />  
      <ic:Operation Name ="And" />  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="Name" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:FirstName</wcf:Argument>  
      </wcf:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:LastName</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name ="Concatenate"/>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="e2f6b-134">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e2f6b-134">In This Section</span></span>  
  
-   [<span data-ttu-id="e2f6b-135">Filter</span><span class="sxs-lookup"><span data-stu-id="e2f6b-135">Filter</span></span>](../core/filter.md)  
  
-   [<span data-ttu-id="e2f6b-136">ID de corrélation</span><span class="sxs-lookup"><span data-stu-id="e2f6b-136">CorrelationID</span></span>](../core/correlationid.md)  
  
-   [<span data-ttu-id="e2f6b-137">ContinuationToken</span><span class="sxs-lookup"><span data-stu-id="e2f6b-137">ContinuationToken</span></span>](../core/continuationtoken.md)  
  
-   [<span data-ttu-id="e2f6b-138">Référence</span><span class="sxs-lookup"><span data-stu-id="e2f6b-138">Reference</span></span>](../core/reference.md)  
  
-   [<span data-ttu-id="e2f6b-139">Update</span><span class="sxs-lookup"><span data-stu-id="e2f6b-139">Update</span></span>](../core/update2.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2f6b-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2f6b-140">See Also</span></span>  
 [<span data-ttu-id="e2f6b-141">Structure d’un fichier de Configuration de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="e2f6b-141">Structure of an Interceptor Configuration File</span></span>](../core/structure-of-an-interceptor-configuration-file.md)