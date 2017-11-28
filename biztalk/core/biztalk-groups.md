---
title: Groupes BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Management database, groups
- groups
- groups, Management database
- groups, about groups
ms.assetid: 197cbcf6-c722-4cbb-9642-3cb8a34757e2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9cd38012f0e2a7ba5f4cfcb56ae63678aacbf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-groups"></a><span data-ttu-id="e62ee-102">Groupes BizTalk</span><span class="sxs-lookup"><span data-stu-id="e62ee-102">BizTalk Groups</span></span>

## <a name="overview"></a><span data-ttu-id="e62ee-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e62ee-103">Overview</span></span>
<span data-ttu-id="e62ee-104">Le *groupe BizTalk* est une unité d’organisation qui représente généralement une entreprise, département, concentrateur ou toute autre unité d’entreprise qui nécessite une implémentation BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e62ee-104">The *BizTalk group* is a unit of organization that usually represents an enterprise, department, hub, or other business unit that requires a contained BizTalk Server implementation.</span></span> <span data-ttu-id="e62ee-105">Le groupe BizTalk entretient une relation un-à-un avec une base de données de gestion BizTalk Server (appelée base de données de configuration BizTalk Server dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="e62ee-105">The BizTalk group has a one-to-one relationship with a BizTalk Server Management database (known as the BizTalk Server Configuration database in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e62ee-106">Si les groupes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent contenir plusieurs ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peuvent être associés qu'à un seul groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e62ee-106">While [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groups may contain multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers, any given [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer may only be associated with a single [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span>  
  
 <span data-ttu-id="e62ee-107">La base de données de gestion BizTalk stocke les informations de configuration pour le groupe BizTalk et les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="e62ee-107">The BizTalk Management database stores configuration information for the BizTalk group and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in that group.</span></span> <span data-ttu-id="e62ee-108">Ces informations spécifient une partie de la logique de traitement du message pour les serveurs et les endroits où l'exécution physique de cette logique a lieu.</span><span class="sxs-lookup"><span data-stu-id="e62ee-108">This configuration information specifies part of the message-processing logic for the servers and where this logic will physically run.</span></span> <span data-ttu-id="e62ee-109">Pour plus d’informations sur la base de données de gestion BizTalk Server, consultez [bases de données BizTalk Server](../core/databases-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="e62ee-109">For more information about the BizTalk Server Management database, see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="e62ee-110">Vous devez spécifier la même base de données de gestion BizTalk Server pour chaque installation de serveur du groupe afin de pouvoir administrer chaque serveur à partir de la console Administration.</span><span class="sxs-lookup"><span data-stu-id="e62ee-110">You must specify the same BizTalk Server Management database for each server installation in the group so that you can administer each server from the administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e62ee-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e62ee-111">See Also</span></span>  
 <span data-ttu-id="e62ee-112">[Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="e62ee-112">[Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md) </span></span>  
 <span data-ttu-id="e62ee-113">[Gestion des groupes](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="e62ee-113">[Managing Groups](../core/managing-groups.md) </span></span>  
 [<span data-ttu-id="e62ee-114">Entités</span><span class="sxs-lookup"><span data-stu-id="e62ee-114">Entities</span></span>](../core/entities.md)