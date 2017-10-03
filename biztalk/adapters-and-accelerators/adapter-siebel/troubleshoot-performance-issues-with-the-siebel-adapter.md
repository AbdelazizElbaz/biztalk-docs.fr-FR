---
title: "Résoudre les problèmes de performances de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance issues
- performance, troubleshooting
ms.assetid: fe413b15-f703-4148-99df-17b5be3c74c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6443dd8b96b19b3cf42f6444ba1ae6c16f2b4ee6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-performance-issues-with-the-siebel-adapter"></a><span data-ttu-id="ed2de-102">Résoudre les problèmes de performances de l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="ed2de-102">Troubleshoot Performance Issues with the Siebel adapter</span></span>
<span data-ttu-id="ed2de-103">Cette section présente l’utilisation de techniques de dépannage pour résoudre les problèmes de performances que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed2de-103">This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="ed2de-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="ed2de-104">Known Issues</span></span>  
  
###  <a name="slowdown-or-stall-in-throughput-when-using-the-adapter-with-biztalk-server"></a><span data-ttu-id="ed2de-105">Ralentissement ou blocage dans le débit lors de l’utilisation de l’adaptateur avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ed2de-105">Slowdown or stall in throughput when using the adapter with BizTalk Server</span></span>  
 <span data-ttu-id="ed2de-106">**Problème**</span><span class="sxs-lookup"><span data-stu-id="ed2de-106">**Problem**</span></span>  
  
 <span data-ttu-id="ed2de-107">Lorsque vous utilisez la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le nombre de messages envoyés ou reçus par l’adaptateur de ralentissement ou est fourni à un blocage.</span><span class="sxs-lookup"><span data-stu-id="ed2de-107">When using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.</span></span>  
  
 <span data-ttu-id="ed2de-108">**Cause**</span><span class="sxs-lookup"><span data-stu-id="ed2de-108">**Cause**</span></span>  
  
 <span data-ttu-id="ed2de-109">Le **EnableBizTalkCompatibilityMode** propriété de liaison n’est pas définie sur WCF-Custom d’envoi ou port de réception dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ed2de-109">The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="ed2de-110">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="ed2de-110">**Resolution**</span></span>  
  
 <span data-ttu-id="ed2de-111">Définir le **EnableBizTalkCompatibilityMode** liaison de propriété à True.</span><span class="sxs-lookup"><span data-stu-id="ed2de-111">Set the **EnableBizTalkCompatibilityMode** binding property to True.</span></span> <span data-ttu-id="ed2de-112">Pour plus d’informations sur cette propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ed2de-112">For more information about this property, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span> <span data-ttu-id="ed2de-113">Pour obtenir des instructions sur la façon de définir une propriété de liaison, consultez [configurer les propriétés de liaison pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="ed2de-113">For instructions on how to set a binding property, see [Configure the binding properties for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed2de-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed2de-114">See Also</span></span>  
[<span data-ttu-id="ed2de-115">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="ed2de-115">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)