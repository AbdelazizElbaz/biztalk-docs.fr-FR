---
title: "Configurer le traitement par lot pour améliorer les performances de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65589925-af94-45f1-b501-37c21618b2cf
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dbee8e5b238af0a6dc7f15d54b85d85e0c4b26c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching-to-improve-adapter-performance"></a><span data-ttu-id="676e0-102">Configurer le traitement par lot pour améliorer les performances de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="676e0-102">Configuring Batching to Improve Adapter Performance</span></span>
<span data-ttu-id="676e0-103">La façon dont un adaptateur traite un lot peut avoir un impact significatif sur les performances.</span><span class="sxs-lookup"><span data-stu-id="676e0-103">The way an adapter processes a batch can have a significant effect on performance.</span></span> <span data-ttu-id="676e0-104">Un délai fixe étant associé à chaque transaction, vous devez faire en sorte de limiter le nombre de transactions en les combinant dans un lot unique.</span><span class="sxs-lookup"><span data-stu-id="676e0-104">Because there is a fixed delay associated with each transaction, you should try to minimize the number of transactions by combining more than one operation into a single batch.</span></span>  
  
 <span data-ttu-id="676e0-105">Si vous envoyez des messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par lots, ne pas limiter la taille de lot basée uniquement sur le nombre de messages.</span><span class="sxs-lookup"><span data-stu-id="676e0-105">If you are submitting messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in batches, do not limit the batch size based only on the message count.</span></span> <span data-ttu-id="676e0-106">Par exemple, si la taille de lot est deux et que l’adaptateur obtient quatre messages de taille de 4 Ko, 8 Ko, 1 Mo et 5 Mo respectivement, le premier lot sera de taille 12 Ko et le deuxième lot sera de 6 Mo.</span><span class="sxs-lookup"><span data-stu-id="676e0-106">For example, if the batch size is two and the adapter gets four messages of size 4 KB, 8 KB, 1 MB, and 5 MB respectively, the first batch will be of size 12 KB, and the second batch will be of size 6 MB.</span></span> <span data-ttu-id="676e0-107">Le moteur de messagerie BizTalk traitant tous les messages d'un lot unique de manière séquentielle, le deuxième lot dans cet exemple sera traité beaucoup plus lentement que le premier.</span><span class="sxs-lookup"><span data-stu-id="676e0-107">Because the BizTalk Messaging Engine processes all messages in a single batch sequentially, the second batch in this example will be processed much more slowly than the first batch.</span></span> <span data-ttu-id="676e0-108">L’effet est le débit réduit.</span><span class="sxs-lookup"><span data-stu-id="676e0-108">The effect of this is reduced throughput.</span></span>  
  
 <span data-ttu-id="676e0-109">Pour gérer ce problème, nous vous recommandons de ce lot vous selon le nombre de messages et le nombre total d’octets dans le lot (autrement dit, taille de lot en octets).</span><span class="sxs-lookup"><span data-stu-id="676e0-109">To handle this problem, we recommend that you batch based on both the message count and the total number of bytes in the batch (that is, batch size in bytes).</span></span> <span data-ttu-id="676e0-110">Il n’existe aucun nombre optimal pour le nombre total d’octets.</span><span class="sxs-lookup"><span data-stu-id="676e0-110">There is no optimal number for total bytes.</span></span> <span data-ttu-id="676e0-111">Toutefois, dans un scénario de traitement normal, si la taille de lot dépasse 1 Mo, vous allez commencer rencontrer de débit et accès concurrentiel médiocre.</span><span class="sxs-lookup"><span data-stu-id="676e0-111">However, in a normal processing scenario, if the batch size exceeds 1 MB, you will start encountering poor concurrency and throughput.</span></span>  
  
 <span data-ttu-id="676e0-112">Adaptateurs traitent généralement les messages de taille variable dans l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="676e0-112">Adapters generally process messages of varying size in the production environment.</span></span> <span data-ttu-id="676e0-113">Les tailles des messages entrants sont susceptibles de varier considérablement.</span><span class="sxs-lookup"><span data-stu-id="676e0-113">The sizes of incoming messages are likely to vary significantly.</span></span> <span data-ttu-id="676e0-114">Par conséquent, toujours utiliser octets de nombre et le nombre total de messages pour générer le lot.</span><span class="sxs-lookup"><span data-stu-id="676e0-114">As a result, always use message count and total bytes to build the batch.</span></span>