---
title: "Exemples d’adaptateur SAP | Documents Microsoft"
description: "exemples d’adaptateur WCF mySAP qui peuvent être utilisés avec BizTalk Server, modèle de service WCF, modèle de canal WCF et le fournisseur de données pour SAP"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4654c458-83be-417f-ae54-5c3a8f6ab81f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d163c573003f40b2049f7e921e5edc4997b4e115
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="samples-for-the-sap-adapter"></a><span data-ttu-id="371b8-103">Exemples de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="371b8-103">Samples for the SAP adapter</span></span>
<span data-ttu-id="371b8-104">Exemples de [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] sont classés ainsi :</span><span class="sxs-lookup"><span data-stu-id="371b8-104">Samples for [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] are categorized into:</span></span>  
  
-   <span data-ttu-id="371b8-105">Les exemples [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="371b8-105">[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples</span></span>  
  
-   <span data-ttu-id="371b8-106">Exemples de modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="371b8-106">WCF service model samples</span></span>  
  
-   <span data-ttu-id="371b8-107">Exemples de modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="371b8-107">WCF channel model samples</span></span>  
  
-   <span data-ttu-id="371b8-108">Les exemples [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="371b8-108">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] samples</span></span>  

  
 <span data-ttu-id="371b8-109">Les exemples sont disponibles au [Pack adaptateurs BizTalk 2010 : exemples d’adaptateur SAP](https://www.microsoft.com/download/details.aspx?id=1314).</span><span class="sxs-lookup"><span data-stu-id="371b8-109">The samples are available at [BizTalk Adapter Pack 2010: SAP adapter samples](https://www.microsoft.com/download/details.aspx?id=1314).</span></span> 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
 <span data-ttu-id="371b8-110">La liste suivante décrit les exemples.</span><span class="sxs-lookup"><span data-stu-id="371b8-110">The following list describes the samples.</span></span>
  
## <a name="biztalk-server-samples"></a><span data-ttu-id="371b8-111">Exemples de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="371b8-111">BizTalk Server samples</span></span>  
  
|<span data-ttu-id="371b8-112">Exemple de nom de répertoire</span><span class="sxs-lookup"><span data-stu-id="371b8-112">Sample Directory Name</span></span>|<span data-ttu-id="371b8-113"> Description</span><span class="sxs-lookup"><span data-stu-id="371b8-113">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="371b8-114">IDOCSend</span><span class="sxs-lookup"><span data-stu-id="371b8-114">IDOCSend</span></span>|<span data-ttu-id="371b8-115">Montre comment envoyer un IDOC à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-115">Demonstrates how to send an IDOC to an SAP system.</span></span>|  
|<span data-ttu-id="371b8-116">ReceiveIDOC</span><span class="sxs-lookup"><span data-stu-id="371b8-116">ReceiveIDOC</span></span>|<span data-ttu-id="371b8-117">Montre comment recevoir un IDOC à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-117">Demonstrates how to receive an IDOC from an SAP system.</span></span>|  
|<span data-ttu-id="371b8-118">ReceiveIDOC_SYSREL</span><span class="sxs-lookup"><span data-stu-id="371b8-118">ReceiveIDOC_SYSREL</span></span>|<span data-ttu-id="371b8-119">Montre comment recevoir un IDOC à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-119">Demonstrates how to receive an IDOC from an SAP system.</span></span> <span data-ttu-id="371b8-120">L’IDOC reçu a le numéro de version inférieur à la SYSREL SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-120">The IDOC being received has the version number less than the SAP SYSREL.</span></span>|  
|<span data-ttu-id="371b8-121">RFCServer</span><span class="sxs-lookup"><span data-stu-id="371b8-121">RFCServer</span></span>|<span data-ttu-id="371b8-122">Montre comment recevoir un appel de serveur RFC à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-122">Demonstrates how to receive an RFC server call from the SAP system.</span></span>|  
|<span data-ttu-id="371b8-123">SAPTransaction</span><span class="sxs-lookup"><span data-stu-id="371b8-123">SAPTransaction</span></span>|<span data-ttu-id="371b8-124">Montre comment effectuer des transactions dans un système SAP à l’aide.</span><span class="sxs-lookup"><span data-stu-id="371b8-124">Demonstrates how to perform transactions in an SAP system using.</span></span>|  
|<span data-ttu-id="371b8-125">tRFCClient</span><span class="sxs-lookup"><span data-stu-id="371b8-125">tRFCClient</span></span>|<span data-ttu-id="371b8-126">Montre comment effectuer des appels de client tRFC sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-126">Demonstrates how to make tRFC client calls on an SAP system.</span></span>|  
  
## <a name="wcf-service-model-samples"></a><span data-ttu-id="371b8-127">Exemples de modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="371b8-127">WCF service model samples</span></span>   
  
|<span data-ttu-id="371b8-128">Exemple de nom de répertoire</span><span class="sxs-lookup"><span data-stu-id="371b8-128">Sample Directory Name</span></span>|<span data-ttu-id="371b8-129"> Description</span><span class="sxs-lookup"><span data-stu-id="371b8-129">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="371b8-130">SapIdocStringClientSM</span><span class="sxs-lookup"><span data-stu-id="371b8-130">SapIdocStringClientSM</span></span>|<span data-ttu-id="371b8-131">Montre comment envoyer un IDOC à un système SAP en appelant l’opération SendIdoc.</span><span class="sxs-lookup"><span data-stu-id="371b8-131">Demonstrates how to send an IDOC to an SAP system by invoking the SendIdoc operation.</span></span>|  
|<span data-ttu-id="371b8-132">SapRfcServerSM</span><span class="sxs-lookup"><span data-stu-id="371b8-132">SapRfcServerSM</span></span>|<span data-ttu-id="371b8-133">Montre comment recevoir un appel de serveur RFC à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-133">Demonstrates how to receive an RFC server call from an SAP system.</span></span>|  
|<span data-ttu-id="371b8-134">SapBapiTxClientSM</span><span class="sxs-lookup"><span data-stu-id="371b8-134">SapBapiTxClientSM</span></span>|<span data-ttu-id="371b8-135">Montre comment appeler des interfaces BAPI à l’intérieur d’une transaction sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-135">Demonstrates how to invoke BAPIs inside a transaction on an SAP system.</span></span>|  
|<span data-ttu-id="371b8-136">SapTrfcClientSM</span><span class="sxs-lookup"><span data-stu-id="371b8-136">SapTrfcClientSM</span></span>|<span data-ttu-id="371b8-137">Montre comment appeler les appels du client tRFC sur un système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-137">Demonstrates how to invoke tRFC client calls on an SAP system.</span></span>|  
  
## <a name="wcf-channel-model-samples"></a><span data-ttu-id="371b8-138">Exemples de modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="371b8-138">WCF channel model samples</span></span>  
  
|<span data-ttu-id="371b8-139">Exemple de nom de répertoire</span><span class="sxs-lookup"><span data-stu-id="371b8-139">Sample Directory Name</span></span>|<span data-ttu-id="371b8-140"> Description</span><span class="sxs-lookup"><span data-stu-id="371b8-140">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="371b8-141">SapIdocReceiveCM</span><span class="sxs-lookup"><span data-stu-id="371b8-141">SapIdocReceiveCM</span></span>|<span data-ttu-id="371b8-142">Montre comment recevoir des IDOC à partir d’un système SAP</span><span class="sxs-lookup"><span data-stu-id="371b8-142">Demonstrates how to receive IDOCs from an SAP system</span></span>|  
|<span data-ttu-id="371b8-143">SapRfcServerCM</span><span class="sxs-lookup"><span data-stu-id="371b8-143">SapRfcServerCM</span></span>|<span data-ttu-id="371b8-144">Montre comment recevoir un appel de serveur RFC à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="371b8-144">Demonstrates how to receive an RFC server call from the SAP system.</span></span>|  
  
## <a name="data-provider-for-sap-samples"></a><span data-ttu-id="371b8-145">Fournisseur de données pour obtenir des exemples SAP</span><span class="sxs-lookup"><span data-stu-id="371b8-145">Data Provider for SAP samples</span></span>  
  
|<span data-ttu-id="371b8-146">Exemple de nom de répertoire</span><span class="sxs-lookup"><span data-stu-id="371b8-146">Sample Directory Name</span></span>|<span data-ttu-id="371b8-147"> Description</span><span class="sxs-lookup"><span data-stu-id="371b8-147">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="371b8-148">SAP ado</span><span class="sxs-lookup"><span data-stu-id="371b8-148">sap ado</span></span>|<span data-ttu-id="371b8-149">Montre comment utiliser le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="371b8-149">Demonstrates how to use the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span>|  
  
 
## <a name="see-also"></a><span data-ttu-id="371b8-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="371b8-150">See Also</span></span>  
[<span data-ttu-id="371b8-151">Développer vos applications SAP</span><span class="sxs-lookup"><span data-stu-id="371b8-151">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)