---
title: "Ensembles de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, inspecting
- correlation sets, about correlation sets
- correlation sets, passing as parameters
- messages, correlation sets
- correlation sets
- correlation sets, following correlation sets
- correlation sets, initializing
ms.assetid: 528dcd6c-d364-4bb8-8deb-cd4a0791867f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28d11e5e174808ca7718d5fef98b3ad079cffc18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlation-sets"></a><span data-ttu-id="94b02-102">Ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="94b02-102">Correlation Sets</span></span>
<span data-ttu-id="94b02-103">Vous pouvez réaliser une sorte de corrélation de messages avec des instances d'orchestration en définissant des ensembles de corrélations.</span><span class="sxs-lookup"><span data-stu-id="94b02-103">You can achieve this sort of correlation of messages with orchestration instances by defining correlation sets.</span></span> <span data-ttu-id="94b02-104">Un ensemble de corrélations est un ensemble de propriétés *avec des valeurs spécifiques*.</span><span class="sxs-lookup"><span data-stu-id="94b02-104">A correlation set is a set of properties *with specific values*.</span></span> <span data-ttu-id="94b02-105">Il ne s'agit pas d'un type de corrélation, qui correspond à une simple liste de propriétés.</span><span class="sxs-lookup"><span data-stu-id="94b02-105">This is different from a correlation type, which is simply a list of properties.</span></span> <span data-ttu-id="94b02-106">Si un message entrant ne dispose pas de l'ensemble de ces propriétés, avec des valeurs correspondantes pour chacune d'elles, la corrélation échoue et l'instance d'orchestration ne reçoit pas le message.</span><span class="sxs-lookup"><span data-stu-id="94b02-106">If an incoming message does not have all of these properties, with matching values for each, correlation will fail and the message will not be received by the orchestration instance.</span></span>  
  
 <span data-ttu-id="94b02-107">Les types de corrélations définissent un jeu de propriétés sur lesquelles corréler les messages.</span><span class="sxs-lookup"><span data-stu-id="94b02-107">Correlation types define a set of properties on which you will be correlating messages.</span></span> <span data-ttu-id="94b02-108">Il peut s'agir de n'importe laquelle des propriétés précédemment définies dans un schéma de propriété et déployées dans le cadre d'un projet BizTalk, y compris des propriétés « système » déployées avec les schémas GlobalPropertySchemas installés en même temps que l'installation BizTalk de base.</span><span class="sxs-lookup"><span data-stu-id="94b02-108">These can be any properties which were previously defined in a property schema and deployed with some BizTalk Project including "system" properties deployed with the GlobalPropertySchemas which is installed as part of the base BizTalk install.</span></span> <span data-ttu-id="94b02-109">Un ensemble de corrélations définit un ensemble de propriétés et de valeurs attribuées à ces propriétés qu'un message doit contenir pour être traité par une orchestration particulière.</span><span class="sxs-lookup"><span data-stu-id="94b02-109">A correlation set defines a set of properties and values for these properties that a message must contain to be processed by a particular orchestration.</span></span>  
  
 <span data-ttu-id="94b02-110">Par exemple, un type de corrélation pourrait se composer des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="94b02-110">For example, a correlation type could consist of the following properties:</span></span>  
  
|<span data-ttu-id="94b02-111">Propriété d'un type de corrélation</span><span class="sxs-lookup"><span data-stu-id="94b02-111">Correlation Type Property</span></span>|<span data-ttu-id="94b02-112">Représentation XML possible</span><span class="sxs-lookup"><span data-stu-id="94b02-112">Possible XML Representation</span></span>|  
|-------------------------------|---------------------------------|  
|<span data-ttu-id="94b02-113">Social Security number</span><span class="sxs-lookup"><span data-stu-id="94b02-113">Social Security number</span></span>|<span data-ttu-id="94b02-114">\<SSN >\</SSN ></span><span class="sxs-lookup"><span data-stu-id="94b02-114">\<SSN>\</SSN></span></span>|  
|<span data-ttu-id="94b02-115">Date of Birth</span><span class="sxs-lookup"><span data-stu-id="94b02-115">Date of Birth</span></span>|<span data-ttu-id="94b02-116">\<DOB >\</DOB ></span><span class="sxs-lookup"><span data-stu-id="94b02-116">\<DOB>\</DOB></span></span>|  
|<span data-ttu-id="94b02-117">Gender</span><span class="sxs-lookup"><span data-stu-id="94b02-117">Gender</span></span>|<span data-ttu-id="94b02-118">\<Sexe > \< /sexe ></span><span class="sxs-lookup"><span data-stu-id="94b02-118">\<Gender>\</Gender></span></span>|  
  
 <span data-ttu-id="94b02-119">Un ensemble de corrélations dérivé de ce type de corrélation pourrait se composer des propriétés et valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="94b02-119">While a correlation set derived from this correlation type could consist of the following properties and values:</span></span>  
  
|<span data-ttu-id="94b02-120">Propriété/valeur de l'ensemble de corrélations</span><span class="sxs-lookup"><span data-stu-id="94b02-120">Correlation Set Property/Value</span></span>|<span data-ttu-id="94b02-121">Représentation XML possible</span><span class="sxs-lookup"><span data-stu-id="94b02-121">Possible XML representation</span></span>|  
|-------------------------------------|---------------------------------|  
|<span data-ttu-id="94b02-122">Social Security number = 222112222</span><span class="sxs-lookup"><span data-stu-id="94b02-122">Social Security number = 222112222</span></span>|<span data-ttu-id="94b02-123">\<SSN > 222112222\</SSN ></span><span class="sxs-lookup"><span data-stu-id="94b02-123">\<SSN>222112222\</SSN></span></span>|  
|<span data-ttu-id="94b02-124">Date of Birth = “1/1/1995”</span><span class="sxs-lookup"><span data-stu-id="94b02-124">Date of Birth = “1/1/1995”</span></span>|<span data-ttu-id="94b02-125">\<DOB > « 1/1/1995 »\</DOB ></span><span class="sxs-lookup"><span data-stu-id="94b02-125">\<DOB>”1/1/1995”\</DOB></span></span>|  
|<span data-ttu-id="94b02-126">Gender = Male</span><span class="sxs-lookup"><span data-stu-id="94b02-126">Gender = Male</span></span>|<span data-ttu-id="94b02-127">\<Sexe > M \< /sexe ></span><span class="sxs-lookup"><span data-stu-id="94b02-127">\<Gender>M\</Gender></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="94b02-128">Chaque ensemble de corrélations prend en charge un maximum de trois paramètres.</span><span class="sxs-lookup"><span data-stu-id="94b02-128">Each correlation set supports a maximum of three parameters.</span></span>  
  
## <a name="initializing-correlation-sets"></a><span data-ttu-id="94b02-129">Propriété Initialisation des ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="94b02-129">Initializing Correlation Sets</span></span>  
  
-   <span data-ttu-id="94b02-130">**Ensembles de corrélations initialisés lors d’une action de réception**</span><span class="sxs-lookup"><span data-stu-id="94b02-130">**Correlation Sets initialized on a Receive action**</span></span>  
  
     <span data-ttu-id="94b02-131">Les ensembles de corrélations initialisés lors d'une action de réception définissent l'ensemble exact de propriétés devant figurer dans un message publié afin que ce dernier puisse être traité par les actions de réception correspondantes dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="94b02-131">Correlation sets initialized on a Receive action define the exact set of properties that must exist in a published message in order for it to be processed by the corresponding receive action(s) in an orchestration.</span></span> <span data-ttu-id="94b02-132">Un ensemble de corrélations initial crée un ensemble de corrélations à partir d'un type de corrélation en fonction des valeurs correspondantes d'un document.</span><span class="sxs-lookup"><span data-stu-id="94b02-132">An initializing correlation set will create a correlation set from a correlation type based on the corresponding values in a document.</span></span>  
  
-   <span data-ttu-id="94b02-133">**Ensembles de corrélations initialisés lors d’une action d’envoi**</span><span class="sxs-lookup"><span data-stu-id="94b02-133">**Correlation Sets initialized on a Send action**</span></span>  
  
     <span data-ttu-id="94b02-134">Les ensembles de corrélations initialisés lors d'une action d'envoi sont créés à partir d'un type de corrélation en fonction des valeurs correspondantes d'un document. Ils promeuvent les propriétés de corrélation dans le document sortant.</span><span class="sxs-lookup"><span data-stu-id="94b02-134">Correlation sets initialized on a Send action are created from a correlation type based upon the corresponding values in a document and promote the correlation properties in the outbound document.</span></span>  
  
## <a name="following-correlation-sets"></a><span data-ttu-id="94b02-135">Propriété Ensembles de corrélations suivants</span><span class="sxs-lookup"><span data-stu-id="94b02-135">Following Correlation Sets</span></span>  
 <span data-ttu-id="94b02-136">Les ensembles de corrélations suivants ne peuvent être liés qu'à une action d'envoi ou à une action de réception sans activation.</span><span class="sxs-lookup"><span data-stu-id="94b02-136">Following correlation sets can only be bound to a non-activating receive action or to a send action.</span></span> <span data-ttu-id="94b02-137">Ils sont indiqués par deux avec des ensembles de corrélations précédemment initialisés.</span><span class="sxs-lookup"><span data-stu-id="94b02-137">Following correlation sets are specified in tandem with previously initialized correlation sets.</span></span>  
  
-   <span data-ttu-id="94b02-138">**Ensembles de corrélations suivants liés à une action de réception**</span><span class="sxs-lookup"><span data-stu-id="94b02-138">**Following Correlation Sets bound to a Receive action**</span></span>  
  
     <span data-ttu-id="94b02-139">Les ensembles de corrélations suivants liés à une action Réception définissent le jeu de propriétés et de valeurs devant absolument figurer dans le document pour que ce dernier puisse être reçu.</span><span class="sxs-lookup"><span data-stu-id="94b02-139">Following correlation sets bound to a receive action define the set of properties and values that the document must contain to be received.</span></span>  <span data-ttu-id="94b02-140">Les actions de réception avec ensembles de corrélations suivants acceptent les documents contenant les propriétés d'un ensemble de corrélations précédemment initialisé.</span><span class="sxs-lookup"><span data-stu-id="94b02-140">Receive actions with following correlation sets accept documents that contain properties from a previously initialized correlation set.</span></span>  
  
-   <span data-ttu-id="94b02-141">**Ensembles de corrélations suivants liés à une action d’envoi**</span><span class="sxs-lookup"><span data-stu-id="94b02-141">**Following Correlation Sets bound to a Send action**</span></span>  
  
     <span data-ttu-id="94b02-142">Les ensembles de corrélations suivants liés à une action Envoi indiquent que le jeu de propriétés figurant dans l'ensemble de corrélations est promu dans le document sortant.</span><span class="sxs-lookup"><span data-stu-id="94b02-142">Following correlation sets bound to a send action dictate that the set of properties in the correlation set are promoted in the outbound document.</span></span>  
  
## <a name="inspecting-correlation-sets"></a><span data-ttu-id="94b02-143">Inspection des ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="94b02-143">Inspecting Correlation Sets</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="94b02-144"> permet d'inspecter les ensembles de corrélations.</span><span class="sxs-lookup"><span data-stu-id="94b02-144"> provides the ability to inspect correlation sets.</span></span> <span data-ttu-id="94b02-145">Vous pouvez inspecter un ensemble de corrélations dans une forme Expression à l'aide d'un code similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="94b02-145">You can inspect a correlation set in an Expression Shape using code similar to the following:</span></span>  
  
```  
MsgLen = Correlation_1(BTS.MessageLength);  
```  
  
 <span data-ttu-id="94b02-146">L’exemple ci-dessus part du principe que vous avez créé une variable nommée **MsgLen** de type **System.Int16** et que votre orchestration contienne une corrélation définir nommée **Correlation_1**.</span><span class="sxs-lookup"><span data-stu-id="94b02-146">The example above assumes that you have created a variable named **MsgLen** of type **System.Int16** and that your orchestration contains a correlation set named **Correlation_1**.</span></span> <span data-ttu-id="94b02-147">Cette possibilité d'inspection des ensembles de corrélations peut se révéler utile lorsque vous avez besoin de vérifier la valeur d'une corrélation transmise entre orchestrations.</span><span class="sxs-lookup"><span data-stu-id="94b02-147">The ability to inspect correlation sets may be useful if you need to inspect the value of a correlation that was passed to an orchestration by another orchestration.</span></span>  
  
## <a name="passing-correlation-sets-as-parameters-to-orchestrations"></a><span data-ttu-id="94b02-148">Transmission d'ensembles de corrélations aux orchestrations en tant que paramètres</span><span class="sxs-lookup"><span data-stu-id="94b02-148">Passing Correlation Sets as Parameters to Orchestrations</span></span>  
 <span data-ttu-id="94b02-149">Vous pouvez transmettre des corrélations en tant que *dans* paramètres vers d’autres orchestrations.</span><span class="sxs-lookup"><span data-stu-id="94b02-149">You can pass correlations as *in* parameters to other orchestrations.</span></span>