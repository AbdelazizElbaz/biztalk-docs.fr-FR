---
title: "Procédure de Pipelines de réception pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, setting
- setting receive pipelines
- pipelines, setting
ms.assetid: d40e0225-0313-4e9b-8d92-464870aabf71
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dd29852ab41af0d5b1f4ed0d184c158a23b5ae7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-receive-pipelines-for-tibco-rendezvous"></a><span data-ttu-id="7fac3-102">Configuration des pipelines de réception pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="7fac3-102">How to Set Receive Pipelines for TIBCO Rendezvous</span></span>
<span data-ttu-id="7fac3-103">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert la définition du gestionnaire de réception et du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="7fac3-103">Microsoft BizTalk Adapter for TIBCO Rendezvous requires that you set the receive handler and receive pipeline.</span></span>  
  
### <a name="to-set-the-pipeline"></a><span data-ttu-id="7fac3-104">Pour définir le pipeline</span><span class="sxs-lookup"><span data-stu-id="7fac3-104">To set the pipeline</span></span>  
  
1.  <span data-ttu-id="7fac3-105">Définir le **Gestionnaire de réception** à **BizTalkServerIsolatedHost** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="7fac3-105">Set the **Receive Handler** to **BizTalkServerIsolatedHost** in the list.</span></span>  
  
2.  <span data-ttu-id="7fac3-106">Définir le **Pipeline de réception** à **XMLReceive** ou tout pipeline équivalent.</span><span class="sxs-lookup"><span data-stu-id="7fac3-106">Set the **Receive Pipeline** to **XMLReceive** or any equivalent pipeline.</span></span>  
  
3.  <span data-ttu-id="7fac3-107">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7fac3-107">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fac3-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fac3-108">See Also</span></span>  
 [<span data-ttu-id="7fac3-109">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="7fac3-109">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)