---
title: "Résoudre les problèmes de performances de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance
- performance, troubleshooting
ms.assetid: 7e8e9fec-0edf-4c67-837c-0e271b2ffe68
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9e18a2f26af993da36a13d389f2aff2ad2f60a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-performance-issues-with-the-sap-adapter"></a><span data-ttu-id="7b58f-102">Résoudre les problèmes de performances de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="7b58f-102">Troubleshoot Performance Issues with the SAP adapter</span></span>
<span data-ttu-id="7b58f-103">Cette section présente l’utilisation de techniques de dépannage pour résoudre les problèmes de performances que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b58f-103">This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span>  
  
##  <span data-ttu-id="7b58f-104"><a name="BKMK_SAPSlowdown"></a>Ralentissement ou blocage dans le débit lors de l’utilisation de l’adaptateur avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7b58f-104"><a name="BKMK_SAPSlowdown"></a> Slowdown or stall in throughput when using the adapter with BizTalk Server</span></span>  
 <span data-ttu-id="7b58f-105">**Problème**</span><span class="sxs-lookup"><span data-stu-id="7b58f-105">**Problem**</span></span>  
  
 <span data-ttu-id="7b58f-106">Lorsque vous utilisez la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le nombre de messages envoyés ou reçus par l’adaptateur de ralentissement ou est fourni à un blocage.</span><span class="sxs-lookup"><span data-stu-id="7b58f-106">When using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.</span></span>  
  
 <span data-ttu-id="7b58f-107">**Cause**</span><span class="sxs-lookup"><span data-stu-id="7b58f-107">**Cause**</span></span>  
  
 <span data-ttu-id="7b58f-108">Le **EnableBizTalkCompatibilityMode** propriété de liaison n’est pas définie sur WCF-Custom d’envoi ou port de réception dans la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7b58f-108">The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration Console.</span></span>  
  
 <span data-ttu-id="7b58f-109">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="7b58f-109">**Resolution**</span></span>  
  
 <span data-ttu-id="7b58f-110">Définir le **EnableBizTalkCompatibilityMode** liaison de propriété à True.</span><span class="sxs-lookup"><span data-stu-id="7b58f-110">Set the **EnableBizTalkCompatibilityMode** binding property to True.</span></span> <span data-ttu-id="7b58f-111">Pour plus d’informations sur cette propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="7b58f-111">For more information about this property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span> <span data-ttu-id="7b58f-112">Pour obtenir des instructions sur la façon de définir une propriété de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="7b58f-112">For instructions on how to set a binding property, see [Configure the binding properties for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).</span></span>  
  
##  <span data-ttu-id="7b58f-113"><a name="BKMK_SAPMemLeak"></a>Fuite de mémoire possible lors de l’utilisation de valeurs NULL pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="7b58f-113"><a name="BKMK_SAPMemLeak"></a> Possible memory leak when using NULL values for parameters</span></span>  
 <span data-ttu-id="7b58f-114">**Problème**</span><span class="sxs-lookup"><span data-stu-id="7b58f-114">**Problem**</span></span>  
  
 <span data-ttu-id="7b58f-115">Vous pouvez observer mémoire fuite si vous ne spécifiez pas les valeurs des paramètres d’entrée ou de table lors de l’appel des artefacts dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7b58f-115">You may observe memory leak if you do not specify values for input or table parameters while invoking artifacts in the SAP system.</span></span>  
  
 <span data-ttu-id="7b58f-116">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="7b58f-116">**Resolution**</span></span>  
  
 <span data-ttu-id="7b58f-117">Assurez-vous que vous spécifiez des valeurs pour tous les paramètres d’entrée et de table lors de l’appel d’un artefact dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="7b58f-117">Make sure you specify values for all the input and table parameters while invoking an artifact in the SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b58f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b58f-118">See Also</span></span>  
[<span data-ttu-id="7b58f-119">Résoudre les problèmes de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="7b58f-119">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)