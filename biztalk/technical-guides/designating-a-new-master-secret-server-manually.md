---
title: "Désignation d’un nouveau serveur de secret principal manuellement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fa44143-8d29-49ba-9c71-96be2c9ded67
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b6d635312d3765c37f1ab9c2b64505698f93e5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designating-a-new-master-secret-server-manually"></a><span data-ttu-id="e443e-102">Désignation d’un nouveau serveur de secret principal manuellement</span><span class="sxs-lookup"><span data-stu-id="e443e-102">Designating a New Master Secret Server Manually</span></span>
<span data-ttu-id="e443e-103">Matériel de cluster peut être coûteux.</span><span class="sxs-lookup"><span data-stu-id="e443e-103">Cluster hardware can be expensive.</span></span> <span data-ttu-id="e443e-104">Si le coût du matériel est un problème, vous pouvez envisager de manuellement désigner un autre serveur Enterprise Single Sign-On (SSO) comme serveur de secret principal durant les scénarios de défaillance.</span><span class="sxs-lookup"><span data-stu-id="e443e-104">If hardware cost is a concern, you can consider manually designating another Enterprise Single Sign-On (SSO) server to be the master secret server during failure scenarios.</span></span> <span data-ttu-id="e443e-105">À l’aide de cette option, tout autre serveur de l’authentification unique dans le groupe de l’authentification unique peut être promue pour le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="e443e-105">Using this option, any other SSO server in the SSO group can be promoted to the master secret server.</span></span> <span data-ttu-id="e443e-106">Lorsque le masque est arrêté, vous pouvez promouvoir manuellement un des serveurs d’authentification unique pour être le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="e443e-106">When the master is down, you can manually promote one of the SSO servers to be the master secret server.</span></span> <span data-ttu-id="e443e-107">L’inconvénient majeurs de cette technique est que vous ne peut pas modifier les déploiements existants, redémarrez existants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services, ou déployer des applications BizTalk jusqu'à ce que vous promouvez un nouveau serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="e443e-107">The biggest disadvantage of this technique is that you cannot edit the existing deployments, restart the existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services, or deploy new BizTalk applications until you promote a new master secret server.</span></span>  
  
 <span data-ttu-id="e443e-108">Pour faciliter le processus transparente, vous devez implémenter un mécanisme d’analyse afin de vous allez découvrir l’échec dès que possible.</span><span class="sxs-lookup"><span data-stu-id="e443e-108">To make the process seamless, you will need to implement some monitoring mechanism so you will discover the failure as soon as possible.</span></span> <span data-ttu-id="e443e-109">Vous pouvez également automatiser le processus de promotion à l’aide d’une application de surveillance tels que System Center Operations Manager.</span><span class="sxs-lookup"><span data-stu-id="e443e-109">You can also automate the promotion process by using a monitoring application such as System Center Operations Manager.</span></span>  
  
 <span data-ttu-id="e443e-110">Pour plus d’informations sur le déplacement de manuellement le serveur de secret principal, consultez [comment déplacer le serveur de secret principal](http://go.microsoft.com/fwlink/?LinkId=156841) (http://go.microsoft.com/fwlink/?LinkId=156841) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="e443e-110">For more information about manually moving the master secret server, see [How to Move the Master Secret Server](http://go.microsoft.com/fwlink/?LinkId=156841) (http://go.microsoft.com/fwlink/?LinkId=156841) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e443e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e443e-111">See Also</span></span>  
 [<span data-ttu-id="e443e-112">Clustering du serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="e443e-112">Clustering the Master Secret Server</span></span>](../technical-guides/clustering-the-master-secret-server.md)