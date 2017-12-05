---
title: "Résoudre les problèmes de performances de l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance issues, troubleshooting
- troubleshooting, performance issues
ms.assetid: 2035cd2e-ce87-419b-aada-61d257671623
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba487bcd5d6d245c979dec903613465ae54f8d9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-performance-issues-with-the-oracle-database-adapter"></a><span data-ttu-id="fd216-102">Résoudre les problèmes de performances de l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="fd216-102">Troubleshoot performance issues with the Oracle Database adapter</span></span>
<span data-ttu-id="fd216-103">Cette section présente l’utilisation de techniques de dépannage pour résoudre les problèmes de performances que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd216-103">This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="fd216-104">Problème connu</span><span class="sxs-lookup"><span data-stu-id="fd216-104">Known Issue</span></span>  
 <span data-ttu-id="fd216-105">Voici le problème de performances courants que vous pouvez rencontrer en utilisant le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ainsi que sa cause probable et de la résolution.</span><span class="sxs-lookup"><span data-stu-id="fd216-105">The following is the most common performance issue you might encounter when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], along with its probable cause and resolution.</span></span>  
  
##  <a name="BKMK_Slowdown"></a><span data-ttu-id="fd216-106">Ralentissement ou blocage dans le débit lors de l’utilisation de l’adaptateur avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fd216-106">Slowdown or stall in throughput when using the adapter with BizTalk Server</span></span>  
 <span data-ttu-id="fd216-107">**Problème**</span><span class="sxs-lookup"><span data-stu-id="fd216-107">**Problem**</span></span>  
  
 <span data-ttu-id="fd216-108">Lorsque vous utilisez la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le nombre de messages envoyés ou reçus par l’adaptateur de ralentissement ou est fourni à un blocage.</span><span class="sxs-lookup"><span data-stu-id="fd216-108">When using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.</span></span>  
  
 <span data-ttu-id="fd216-109">**Cause**</span><span class="sxs-lookup"><span data-stu-id="fd216-109">**Cause**</span></span>  
  
 <span data-ttu-id="fd216-110">Le **EnableBizTalkCompatibilityMode** propriété de liaison n’est pas définie sur WCF-Custom d’envoi ou port de réception dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fd216-110">The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="fd216-111">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="fd216-111">**Resolution**</span></span>  
  
 <span data-ttu-id="fd216-112">Définir le **EnableBizTalkCompatibilityMode** liaison de propriété à True.</span><span class="sxs-lookup"><span data-stu-id="fd216-112">Set the **EnableBizTalkCompatibilityMode** binding property to True.</span></span> <span data-ttu-id="fd216-113">Pour plus d’informations sur cette propriété, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="fd216-113">For more information about this property, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span> <span data-ttu-id="fd216-114">Pour obtenir des instructions sur la façon de définir une propriété de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span><span class="sxs-lookup"><span data-stu-id="fd216-114">For instructions on how to set a binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
### <a name="possible-memory-leak-on-a-64-bit-computer-when-using-the-oracle-database-adapter-to-perform-operations-involving-float-data-type"></a><span data-ttu-id="fd216-115">Fuite de mémoire possible sur un ordinateur 64 bits lors de l’utilisation de l’adaptateur de base de données Oracle pour effectuer des opérations impliquant le type de données FLOAT</span><span class="sxs-lookup"><span data-stu-id="fd216-115">Possible memory leak on a 64-bit computer when using the Oracle database adapter to perform operations involving FLOAT data type</span></span>  
 <span data-ttu-id="fd216-116">**Problème**</span><span class="sxs-lookup"><span data-stu-id="fd216-116">**Problem**</span></span>  
  
 <span data-ttu-id="fd216-117">Vous pouvez rencontrer une fuite de mémoire lorsque vous utilisez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] sur un ordinateur 64 bits pour effectuer des opérations qui impliquent des types de données FLOAT.</span><span class="sxs-lookup"><span data-stu-id="fd216-117">You may experience a memory leak when using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on a 64-bit computer to perform operations that involve FLOAT data types.</span></span>  
  
 <span data-ttu-id="fd216-118">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="fd216-118">**Resolution**</span></span>  
  
 <span data-ttu-id="fd216-119">Installez .NET \< *version* \> (x64) sur l’ordinateur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="fd216-119">Install .NET \<*version*\> (x64) on the 64-bit computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd216-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd216-120">See Also</span></span>  
[<span data-ttu-id="fd216-121">Résoudre les problèmes d’Oracle adapter.md de base de données</span><span class="sxs-lookup"><span data-stu-id="fd216-121">Troubleshoot the Oracle Database adapter.md</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)