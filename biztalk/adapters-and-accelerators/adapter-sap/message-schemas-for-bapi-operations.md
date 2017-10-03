---
title: "Schémas de message pour des opérations BAPI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAPI operations, message schemas for
- BAPI operations, message structure for
- BAPI operations, message actions for
ms.assetid: ef4d88e8-f31a-4b68-a303-6885b6f8c083
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 999e60a7e2cac827031ea2a19f9482d9da0baaa6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-bapi-operations"></a><span data-ttu-id="f2030-102">Schémas de message pour des opérations BAPI</span><span class="sxs-lookup"><span data-stu-id="f2030-102">Message Schemas for BAPI Operations</span></span>
<span data-ttu-id="f2030-103">Les sections suivantes décrivent les schémas de message et les actions de message utilisées pour appeler des interfaces BAPI sur le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] en tant que méthodes d’objets métier.</span><span class="sxs-lookup"><span data-stu-id="f2030-103">The following sections describe the message schemas and message actions used to invoke BAPIs on the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as methods of business objects.</span></span> <span data-ttu-id="f2030-104">Vous pouvez également appeler des interfaces BAPI en tant qu’opérations RFC sur la carte.</span><span class="sxs-lookup"><span data-stu-id="f2030-104">You can also invoke BAPIs as RFC operations on the adapter.</span></span> <span data-ttu-id="f2030-105">Pour plus d’informations sur les messages utilisés pour appeler les RFC, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f2030-105">For more information about the messages used to invoke RFCs, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span> <span data-ttu-id="f2030-106">Quelle que soit la façon dont vous appelez un BAPI sur la carte, l’adaptateur appelle toujours BAPI comme RFC sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="f2030-106">Regardless of how you invoke a BAPI on the adapter, the adapter always invokes the BAPI as an RFC on the SAP system.</span></span> <span data-ttu-id="f2030-107">Pour une vue d’ensemble de la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge BAPI, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="f2030-107">For an overview of how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports BAPIs, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
## <a name="message-structure-for-business-object-operations"></a><span data-ttu-id="f2030-108">Structure du message pour les opérations d’objet métier</span><span class="sxs-lookup"><span data-stu-id="f2030-108">Message Structure for Business Object Operations</span></span>  
 <span data-ttu-id="f2030-109">Le tableau suivant présente les schémas de message utilisées pour appeler une commande BAPI comme une méthode d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="f2030-109">The following table shows the message schemas used to invoke a BAPI as a business object method.</span></span>  
  
|<span data-ttu-id="f2030-110">Opération</span><span class="sxs-lookup"><span data-stu-id="f2030-110">Operation</span></span>|<span data-ttu-id="f2030-111">Structure XML</span><span class="sxs-lookup"><span data-stu-id="f2030-111">XML Structure</span></span>|<span data-ttu-id="f2030-112"> Description</span><span class="sxs-lookup"><span data-stu-id="f2030-112">Description</span></span>|  
|---------------|-------------------|-----------------|  
|<span data-ttu-id="f2030-113">[BUSOBJ_METHOD]</span><span class="sxs-lookup"><span data-stu-id="f2030-113">[BUSOBJ_METHOD]</span></span>|`<[BUSOBJ_METHOD] xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]>`|<span data-ttu-id="f2030-114">Appeler une méthode d’objet métier sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="f2030-114">Invoke a business object method on an SAP system.</span></span><br /><br /> <span data-ttu-id="f2030-115">Importation, la modification et les paramètres table sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f2030-115">Import, changing, and table parameters are supported.</span></span>|  
|<span data-ttu-id="f2030-116">[BUSOBJ_METHOD] Réponse</span><span class="sxs-lookup"><span data-stu-id="f2030-116">[BUSOBJ_METHOD] Response</span></span>|`<[BUSOBJ_METHOD]Response xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]Response>`|<span data-ttu-id="f2030-117">Réponse de méthode d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="f2030-117">Business object method response.</span></span><br /><br /> <span data-ttu-id="f2030-118">Exporter, modifier, et les paramètres table sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f2030-118">Export, changing, and table parameters are supported.</span></span><br /><br /> <span data-ttu-id="f2030-119">**Remarque** par défaut, les paramètres de la table ne sont pas signalées dans le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="f2030-119">**Note** By default, table parameters are not surfaced in the response message.</span></span> <span data-ttu-id="f2030-120">Si vous avez besoin des paramètres de la table dans le message de réponse, vous devez passer les paramètres de table vide dans le message de demande.</span><span class="sxs-lookup"><span data-stu-id="f2030-120">If you require table parameters in response message, you must pass empty table parameters in the request message.</span></span>|  
  
 <span data-ttu-id="f2030-121">[VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.</span><span class="sxs-lookup"><span data-stu-id="f2030-121">[VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.</span></span>  
  
 <span data-ttu-id="f2030-122">[BUSOBJ_METHOD] = le nom d’une méthode d’objet métier ; par exemple, CREATEFROMDAT2.</span><span class="sxs-lookup"><span data-stu-id="f2030-122">[BUSOBJ_METHOD] = The name of a business object method; for example, CREATEFROMDAT2.</span></span>  
  
 <span data-ttu-id="f2030-123">[IN_PARAM_NAME] = le nom d’un paramètre d’importation BAPI.</span><span class="sxs-lookup"><span data-stu-id="f2030-123">[IN_PARAM_NAME] =The name of a BAPI import parameter.</span></span>  
  
 <span data-ttu-id="f2030-124">[OUT_PARAM_NAME] = le nom d’un paramètre d’exportation BAPI.</span><span class="sxs-lookup"><span data-stu-id="f2030-124">[OUT_PARAM_NAME] = The name of a BAPI export parameter.</span></span>  
  
 <span data-ttu-id="f2030-125">[INOUT_PARAM_NAME] = le nom d’une commande BAPI la modification du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f2030-125">[INOUT_PARAM_NAME] = The name of a BAPI changing parameter.</span></span>  
  
 <span data-ttu-id="f2030-126">[TABLE_PARAM_NAME] = nom du paramètre de table BAPI.</span><span class="sxs-lookup"><span data-stu-id="f2030-126">[TABLE_PARAM_NAME] = The name of a BAPI table parameter.</span></span>  
  
 <span data-ttu-id="f2030-127">[STRUCT_PARAM_NAME] = le nom d’un paramètre de structure BAPI.</span><span class="sxs-lookup"><span data-stu-id="f2030-127">[STRUCT_PARAM_NAME] = The name of a BAPI structure parameter.</span></span>  
  
## <a name="message-actions-for-business-object-operations"></a><span data-ttu-id="f2030-128">Actions de message pour les opérations d’objet métier</span><span class="sxs-lookup"><span data-stu-id="f2030-128">Message Actions for Business Object Operations</span></span>  
 <span data-ttu-id="f2030-129">Le tableau suivant répertorie les actions de message qui sont utilisées pour appeler des interfaces BAPI en tant que méthodes d’objet métier.</span><span class="sxs-lookup"><span data-stu-id="f2030-129">The following table shows the message actions that are used to invoke BAPIs as business object methods.</span></span>  
  
|<span data-ttu-id="f2030-130">Opération</span><span class="sxs-lookup"><span data-stu-id="f2030-130">Operation</span></span>|<span data-ttu-id="f2030-131">Action du message</span><span class="sxs-lookup"><span data-stu-id="f2030-131">Message Action</span></span>|<span data-ttu-id="f2030-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2030-132">Example</span></span>|  
|---------------|--------------------|-------------|  
|<span data-ttu-id="f2030-133">[BUSOBJ_METHOD]</span><span class="sxs-lookup"><span data-stu-id="f2030-133">[BUSOBJ_METHOD]</span></span>|<span data-ttu-id="f2030-134">[VERSION] /Bapi/ [BUSOBJ_NAME] / [BUSOBJ_METHOD] / [BAPI_RFC_NAME]</span><span class="sxs-lookup"><span data-stu-id="f2030-134">[VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]</span></span>|<span data-ttu-id="f2030-135">http://Microsoft.LobServices.SAP/2007/03/BAPI/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2</span><span class="sxs-lookup"><span data-stu-id="f2030-135">http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2</span></span>|  
|<span data-ttu-id="f2030-136">[BUSOBJ_METHOD] Réponse</span><span class="sxs-lookup"><span data-stu-id="f2030-136">[BUSOBJ_METHOD] Response</span></span>|<span data-ttu-id="f2030-137">[VERSION] /Bapi/ [BUSOBJ_NAME] / [BUSOBJ_METHOD] / [BAPI_RFC_NAME] / réponse</span><span class="sxs-lookup"><span data-stu-id="f2030-137">[VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]/response</span></span>|<span data-ttu-id="f2030-138">http://Microsoft.LobServices.SAP/2007/03/BAPI/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2/Response</span><span class="sxs-lookup"><span data-stu-id="f2030-138">http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2/response</span></span>|  
  
 <span data-ttu-id="f2030-139">[VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.</span><span class="sxs-lookup"><span data-stu-id="f2030-139">[VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.</span></span>  
  
 <span data-ttu-id="f2030-140">[BUSOBJ_NAME] = nom de l’objet métier ; par exemple, BUS2032.</span><span class="sxs-lookup"><span data-stu-id="f2030-140">[BUSOBJ_NAME] = The name of the business object; for example, BUS2032.</span></span>  
  
 <span data-ttu-id="f2030-141">[BUSOBJ_METHOD] = la méthode de l’objet métier ; par exemple, CREATEFROMDAT2.</span><span class="sxs-lookup"><span data-stu-id="f2030-141">[BUSOBJ_METHOD] = The method of the business object; for example, CREATEFROMDAT2.</span></span>  
  
 <span data-ttu-id="f2030-142">[BAPI_RFC_NAME] = nom de la RFC pour BAPI ; par exemple, BAPI_SALESORDER_CREATEFROMDAT2.</span><span class="sxs-lookup"><span data-stu-id="f2030-142">[BAPI_RFC_NAME] = The RFC name for the BAPI; for example, BAPI_SALESORDER_CREATEFROMDAT2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2030-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2030-143">See Also</span></span>  
 [<span data-ttu-id="f2030-144">Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="f2030-144">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)