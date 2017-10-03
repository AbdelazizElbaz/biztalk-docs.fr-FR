---
title: "Déplacement de bases de données Non-BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e548e72-db0e-4f07-a07a-8d210425dfa5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c836840fef8b49cb907e7ac039612c68c1f6fd6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="moving-non-bam-databases"></a><span data-ttu-id="4d29f-102">Déplacement de bases de données Non-BAM</span><span class="sxs-lookup"><span data-stu-id="4d29f-102">Moving Non-BAM Databases</span></span>
<span data-ttu-id="4d29f-103">Vous pouvez utiliser cette procédure pour déplacer les bases de données BizTalk Server principales vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="4d29f-103">You can use this procedure to move the primary BizTalk Server databases to another server.</span></span> <span data-ttu-id="4d29f-104">Cette même procédure peut également être utilisée pour déplacer les bases de données BizTalk Server à partir d’un serveur SQL Server local à un serveur SQL distant ou à un cluster de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4d29f-104">This same basic procedure can also be used to move the BizTalk Server databases from a local SQL Server to a remote SQL Server or to a SQL Server cluster.</span></span> <span data-ttu-id="4d29f-105">Cette section décrit comment déplacer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données qui ne sont pas lié de BAM.</span><span class="sxs-lookup"><span data-stu-id="4d29f-105">This section describes how to move the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases that are not BAM related.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d29f-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4d29f-106">In This Section</span></span>  
 <span data-ttu-id="4d29f-107">Pour déplacer le BAM non bases de données suivent les étapes décrites dans la rubrique [comment déplacer les bases de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=210646) (http://go.microsoft.com/fwlink/?LinkId=210646) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="4d29f-107">To move the non BAM databases follow the steps in the topic [How to Move the BizTalk Server Databases](http://go.microsoft.com/fwlink/?LinkId=210646) (http://go.microsoft.com/fwlink/?LinkId=210646) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] help.</span></span>  
  
 <span data-ttu-id="4d29f-108">Cette section contient également une rubrique qui décrit les procédures à suivre après avoir déplacé particulier [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.</span><span class="sxs-lookup"><span data-stu-id="4d29f-108">This section also contains a topic that describes procedures that must be followed after moving particular [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="4d29f-109">Effectuez les étapes de la rubrique en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="4d29f-109">Complete the steps in the topic as appropriate for your environment.</span></span>  
  
-   [<span data-ttu-id="4d29f-110">Considérations lors du déplacement de la base de données de suivi si la base de données MessageBox n’est pas déplacé</span><span class="sxs-lookup"><span data-stu-id="4d29f-110">Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved</span></span>](../technical-guides/before-you-move-the-tracking-database-if-messagebox-database-is-not-moving.md)