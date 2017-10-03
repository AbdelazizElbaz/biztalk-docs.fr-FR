---
title: "Les goulots d’étranglement au niveau de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55b37393-32dc-4717-bf62-48588c23dd78
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b741f1ffcd68f7a5c739731e5aa9a1db55be34c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bottlenecks-in-the-database-tier"></a><span data-ttu-id="435ec-102">Goulots d’étranglement au niveau de la base de données</span><span class="sxs-lookup"><span data-stu-id="435ec-102">Bottlenecks in the Database Tier</span></span>
<span data-ttu-id="435ec-103">Cette section explique comment identifier les goulots d’étranglement dans la base de données MessageBox de BizTalk, base de données de suivi, base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="435ec-103">This section explains how to identify bottlenecks in the BizTalk MessageBox database, Tracking database, and BAM Primary Import database.</span></span> <span data-ttu-id="435ec-104">Elle explique également comment éviter la contention de disque.</span><span class="sxs-lookup"><span data-stu-id="435ec-104">It also explains how to avoid disk contention.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="435ec-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="435ec-105">In This Section</span></span>  
  
-   [<span data-ttu-id="435ec-106">Comment identifier les goulots d’étranglement dans la MessageBox Database1</span><span class="sxs-lookup"><span data-stu-id="435ec-106">How to Identify Bottlenecks in the MessageBox Database1</span></span>](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md)  
  
-   [<span data-ttu-id="435ec-107">Comment identifier les goulots d’étranglement dans la base de données de suivi</span><span class="sxs-lookup"><span data-stu-id="435ec-107">How to Identify Bottlenecks in the Tracking Database</span></span>](../technical-guides/how-to-identify-bottlenecks-in-the-tracking-database.md)  
  
-   [<span data-ttu-id="435ec-108">Comment identifier les goulots d’étranglement dans la base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="435ec-108">How to Identify Bottlenecks in the BAM Primary Import Database</span></span>](../technical-guides/how-to-identify-bottlenecks-in-the-bam-primary-import-database.md)  
  
-   [<span data-ttu-id="435ec-109">Comment éviter Contention2 de disque</span><span class="sxs-lookup"><span data-stu-id="435ec-109">How to Avoid Disk Contention2</span></span>](../technical-guides/how-to-avoid-disk-contention2.md)