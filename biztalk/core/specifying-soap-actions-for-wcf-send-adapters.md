---
title: "Spécification des Actions SOAP pour WCF des adaptateurs d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send adapters, mapping
- send adapters, WCF services
- mapping, send adapters
- mapping, WCF send adapters
ms.assetid: fa9878eb-65b5-4ccc-b727-ff7e09ba6302
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385e92f7801dc2512fbd038bd0b005d95c503e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="specifying-soap-actions-for-wcf-send-adapters"></a><span data-ttu-id="8ad68-102">Spécification des actions SOAP pour les adaptateurs d'envoi WCF</span><span class="sxs-lookup"><span data-stu-id="8ad68-102">Specifying SOAP Actions for WCF Send Adapters</span></span>
<span data-ttu-id="8ad68-103">Vous pouvez définir le **WCF. Action** propriété de contexte dans la boîte de dialogue Propriétés du transport WCF envoi carte ou dans l’orchestration **Expression** formes.</span><span class="sxs-lookup"><span data-stu-id="8ad68-103">You can set the **WCF.Action** context property in the WCF send adapter transport properties dialog box or in the orchestration **Expression** shapes.</span></span> <span data-ttu-id="8ad68-104">Si vous définissez la **WCF. Action** propriété de contexte de l’orchestration, vous devez laisser la **Action** champ vide dans la boîte de dialogue Propriétés WCF adaptateur transport pour les ports d’envoi statiques.</span><span class="sxs-lookup"><span data-stu-id="8ad68-104">If you set the **WCF.Action** context property in the orchestration, you need to leave the **Action** field blank in the WCF adapter transport properties dialog box for the static send ports.</span></span> <span data-ttu-id="8ad68-105">Si vous spécifiez également une action dans les ports d’envoi statiques, le **WCF. Action** propriété de contexte que vous définissez dans l’orchestration sera remplacée.</span><span class="sxs-lookup"><span data-stu-id="8ad68-105">If you also specify an action in the static send ports, the **WCF.Action** context property you set in the orchestration will be overridden.</span></span>  
  
 <span data-ttu-id="8ad68-106">En outre, il existe deux façons de spécifier cette propriété : le format d’action unique et le format de mappage d’action.</span><span class="sxs-lookup"><span data-stu-id="8ad68-106">Moreover, there are two ways to specify this property: the single action format and the action mapping format.</span></span> <span data-ttu-id="8ad68-107">Si vous définissez cette propriété dans le format d'action unique (par exemple, http://MyService/IMyContract/MyAction1), l'action SOAP dans la boîte de dialogue Propriétés du transport de l'adaptateur WCF pour les messages sortants est toujours définie sur la valeur spécifiée dans cette propriété.</span><span class="sxs-lookup"><span data-stu-id="8ad68-107">If you set this property in the single action format—for example, http://MyService/IMyContract/MyAction1—the SOAP action in the WCF send adapter transport properties dialog box for outgoing messages is always set to the value specified in this property.</span></span> <span data-ttu-id="8ad68-108">Vous pouvez également définir le format d’action unique dans l’orchestration **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="8ad68-108">Alternatively, you can set the single action format in the orchestration **Expression** shape.</span></span> <span data-ttu-id="8ad68-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8ad68-109">For example,</span></span>  
  
```  
OutboundMessage(WCF.Action)="http://MyService/IMyContract/MyAction1";  
```  
  
 <span data-ttu-id="8ad68-110">Si vous définissez cette propriété dans le format de mappage d’action, l’action SOAP sortante est déterminée par le **BTS. Opération** propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="8ad68-110">If you set this property in the action mapping format, the outgoing SOAP action is determined by the **BTS.Operation** context property.</span></span> <span data-ttu-id="8ad68-111">Par exemple, si cette propriété est définie au format XML suivant dans WCF envoyer la boîte de dialogue Propriétés du transport adaptateur et le **BTS. Opération** est définie sur **Operation_1** du port d’envoi dans l’orchestration, l’adaptateur d’envoi WCF utilise http://MyService/IMyContract/MyAction1 pour l’action SOAP sortante.</span><span class="sxs-lookup"><span data-stu-id="8ad68-111">For example, if this property is set to the following XML format in the WCF send adapter transport properties dialog box and the **BTS.Operation** property is set to **Operation_1** in the send port in the orchestration, the WCF send adapter uses http://MyService/IMyContract/MyAction1 for the outgoing SOAP action.</span></span>  
  
```  
BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<Operation Name="Operation_1" Action="http://MyService/IMyContract/MyAction1" />  
<Operation Name="Operation_2" Action="http://MyService/IMyContract/MyAction2" />  
<Operation Name="Operation_3" Action="http://MyService/IMyContract/MyAction3" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="8ad68-112">Spécification du mappage d’action pour **WCF. Action** dans un **Expression** forme n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8ad68-112">Specifying action mapping for **WCF.Action** in an **Expression** shape is not supported.</span></span> <span data-ttu-id="8ad68-113">Vous devez spécifier le mappage d'action dans la boîte de dialogue Propriétés du transport WCF.</span><span class="sxs-lookup"><span data-stu-id="8ad68-113">You need to specify the action mapping in the WCF transport properties dialog box.</span></span> <span data-ttu-id="8ad68-114">Ensuite, l’adaptateur WCF recherche l’action SOAP à l’aide de la **BTS. Opération** la propriété de contexte, l’orchestration définit le nom de l’opération sur le port sur lequel le message est envoyé.</span><span class="sxs-lookup"><span data-stu-id="8ad68-114">Then the WCF adapter will look up the SOAP action by using the **BTS.Operation** context property, which the orchestration sets to the name of the operation on the port where the message is sent.</span></span>  
  
 <span data-ttu-id="8ad68-115">Si les messages sortants sont acheminés avec le routage basé sur le contenu (CBR) où le **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** propriété n’est pas définie, les adaptateurs d’envoi WCF définira le mappage d’action entier chaîne à l’action des messages WCF sortants.</span><span class="sxs-lookup"><span data-stu-id="8ad68-115">If outgoing messages are routed with content-based routing (CBR) where the **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** property is not set, WCF send adapters will set the whole action mapping string to the action of the outgoing WCF messages.</span></span> <span data-ttu-id="8ad68-116">Pour contourner ce problème, vous pouvez effectuer une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8ad68-116">To work around this, you can do one of the following:</span></span>  
  
-   <span data-ttu-id="8ad68-117">définir le champ Action sur le port d'envoi sur http://MyService/IMyContract/MyAction1 ;</span><span class="sxs-lookup"><span data-stu-id="8ad68-117">Set the action field on the send port to http://MyService/IMyContract/MyAction1.</span></span>  
  
-   <span data-ttu-id="8ad68-118">Définir le **BTS. Opération** propriété de contexte dans un pipeline.</span><span class="sxs-lookup"><span data-stu-id="8ad68-118">Set the **BTS.Operation** context property in a pipeline.</span></span> <span data-ttu-id="8ad68-119">Par exemple, définir la valeur de **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** sur Operation1.</span><span class="sxs-lookup"><span data-stu-id="8ad68-119">For example, set the value of **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** to Operation1.</span></span>  
  
-   <span data-ttu-id="8ad68-120">laisser vierge le champ Action et utiliser l'action du message entrant à la place.</span><span class="sxs-lookup"><span data-stu-id="8ad68-120">Leave the action field blank and use the action from the incoming message instead.</span></span>  
  
 <span data-ttu-id="8ad68-121">Vous pouvez également utiliser l'Assistant Consommation de service WCF BizTalk pour utiliser les services WCF avec l'action unique ou le mappage d'action.</span><span class="sxs-lookup"><span data-stu-id="8ad68-121">You can also use the BizTalk WCF Service Consuming Wizard to consume the WCF services with single action or action mapping.</span></span> <span data-ttu-id="8ad68-122">Pour plus d’informations, consultez [l’utilisation de l’Assistant de consommation de Service WCF BizTalk pour utiliser un Service WCF](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md).</span><span class="sxs-lookup"><span data-stu-id="8ad68-122">For more details, see [How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad68-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad68-123">See Also</span></span>  
 [<span data-ttu-id="8ad68-124">Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="8ad68-124">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)