---
title: Comment enregistrer les informations de suivi au fichier | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, tracking
- DebugTrackingInterceptor
- Business Rules Framework, code samples
ms.assetid: c832b763-aa08-4a0e-9086-776dccb0a6ef
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cdaae8e727cedc784ecaade83178cf50f863f99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-log-tracking-information-to-file"></a><span data-ttu-id="fccf5-102">Comment enregistrer les informations de suivi au fichier</span><span class="sxs-lookup"><span data-stu-id="fccf5-102">How to Log Tracking Information to File</span></span>
<span data-ttu-id="fccf5-103">Quand le moteur des règles d'entreprise s'exécute, il transmet les informations de suivi de l'exécution à un intercepteur.</span><span class="sxs-lookup"><span data-stu-id="fccf5-103">When the Business Rule Engine executes, it passes execution tracking information to an interceptor.</span></span> <span data-ttu-id="fccf5-104">Il est configuré pour faire appel à l'intercepteur BizTalk, qui est utilisé lors du suivi des événements de messages et des données d'instance de service.</span><span class="sxs-lookup"><span data-stu-id="fccf5-104">The engine is configured to use the BizTalk interceptor which is used when tracking message events and service instance data.</span></span> <span data-ttu-id="fccf5-105">Si vous appelez le moteur en dehors de l'orchestration BizTalk, vous pouvez transmettre l'intercepteur que vous voulez utiliser quand vous exécutez la stratégie.</span><span class="sxs-lookup"><span data-stu-id="fccf5-105">If you are calling the engine outside of BizTalk orchestration, you can pass the interceptor you want to use when you execute the policy.</span></span> <span data-ttu-id="fccf5-106">En plus de l’intercepteur BizTalk, vous pouvez également utiliser le **DebugTrackingInterceptor** pour les informations de suivi au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="fccf5-106">In addition to the BizTalk interceptor, you can also use the **DebugTrackingInterceptor** to output the tracking information to file.</span></span> <span data-ttu-id="fccf5-107">L’exemple de code suivant montre comment utiliser **DebugTrackingInterceptor**.</span><span class="sxs-lookup"><span data-stu-id="fccf5-107">The following code example demonstrates how to use **DebugTrackingInterceptor**.</span></span>  
  
```  
DebugTrackingInterceptor tracker = new DebugTrackingInterceptor("TrackingOutput.txt");  
policy.Execute(shortTermFacts,tracker);  
```