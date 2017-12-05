---
title: "Configuration du système Source | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722dd52c-1eea-453c-9a36-9b8d9cf19350
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73f5d785c20d1390ae811d737e9169951e0270e7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-the-source-system"></a><span data-ttu-id="c95e1-102">Configuration du système Source</span><span class="sxs-lookup"><span data-stu-id="c95e1-102">Configuring the Source System</span></span>
<span data-ttu-id="c95e1-103">Dans le cadre de la copie des journaux de BizTalk Server, il n’a pas d’importance si le système source se trouve sur un seul [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance ou si elle est réparti entre plusieurs instances hébergées dans un cluster Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c95e1-103">For the purposes of BizTalk Server log shipping, it does not matter if the source system is located on a single [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance or if it is distributed among multiple instances hosted in a Windows Server cluster.</span></span> <span data-ttu-id="c95e1-104">Il n’y a pas de considérations supplémentaires autres que celles nécessaires à l’exécution du travail de sauvegarde de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c95e1-104">There are no additional considerations other than those required to successfully run the Backup BizTalk Server job.</span></span> <span data-ttu-id="c95e1-105">Pour configurer cette tâche, consultez [comment configurer le travail de sauvegarde de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154072) (http://go.microsoft.com/fwlink/?LinkID=154072) dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c95e1-105">To configure this job, see [How to Configure the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkID=154072) (http://go.microsoft.com/fwlink/?LinkID=154072) in BizTalk Server Help.</span></span> <span data-ttu-id="c95e1-106">Après avoir configuré le travail de sauvegarde de BizTalk Server, passez à la rubrique [comment configurer le système de Destination](../technical-guides/how-to-configure-the-destination-system.md).</span><span class="sxs-lookup"><span data-stu-id="c95e1-106">After you have configured the Backup BizTalk Server Job, proceed to the topic [How to Configure the Destination System](../technical-guides/how-to-configure-the-destination-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95e1-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c95e1-107">See Also</span></span>  
 [<span data-ttu-id="c95e1-108">Configuration de la copie des journaux de transaction BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c95e1-108">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)