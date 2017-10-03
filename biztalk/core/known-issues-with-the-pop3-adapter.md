---
title: "Problèmes connus avec l’adaptateur POP3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6d621a2-4801-44fe-a266-d4c05ac82633
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc86b2ae14b04b160f7387f870615116e659b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-pop3-adapter"></a><span data-ttu-id="be36c-102">Problèmes connus avec l'adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="be36c-102">Known Issues with the POP3 Adapter</span></span>
<span data-ttu-id="be36c-103">Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.</span><span class="sxs-lookup"><span data-stu-id="be36c-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="be36c-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="be36c-104">Known Issues</span></span>  
  
#### <a name="the-pop3-adapter-fails-to-process-documents-when-running-on-a-64-bit-operating-system"></a><span data-ttu-id="be36c-105">L'adaptateur POP3 ne parvient pas à traiter des documents lorsqu'il s'exécute sur un système d'exploitation 64 bits</span><span class="sxs-lookup"><span data-stu-id="be36c-105">The POP3 Adapter fails to process documents when running on a 64 bit operating system</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="be36c-106">Problème</span><span class="sxs-lookup"><span data-stu-id="be36c-106">Problem</span></span>  
 <span data-ttu-id="be36c-107">L'adaptateur POP3 ne traitera pas de document s'il s'exécute sur un système d'exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="be36c-107">The POP3 Adapter will not process documents when running on a 64 bit operating system.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="be36c-108">Cause</span><span class="sxs-lookup"><span data-stu-id="be36c-108">Cause</span></span>  
 <span data-ttu-id="be36c-109">Le gestionnaire de l'adaptateur POP3 n'est pas en mesure d'exécuter une instance d'hôte 64 bits.</span><span class="sxs-lookup"><span data-stu-id="be36c-109">The POP3 Adapter adapter handler is unable to run in a 64 bit host instance.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="be36c-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="be36c-110">Resolution</span></span>  
 <span data-ttu-id="be36c-111">Si vous exécutez l'adaptateur POP3 sur une machine 64 bits, configurez les gestionnaires correspondants pour qu'ils s'exécutent sur un hôte 32 bits.</span><span class="sxs-lookup"><span data-stu-id="be36c-111">If you are running the POP3 Adapter on a 64 bit machine, configure the POP3 Adapter handlers to run in a 32 bit host.</span></span> <span data-ttu-id="be36c-112">Cette option se trouve dans la page Propriétés d'hôte accessible à partir de la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="be36c-112">This option is available on the Host Properties page accessible from the BizTalk Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be36c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be36c-113">See Also</span></span>  
 [<span data-ttu-id="be36c-114">Dépannage de l’adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="be36c-114">Troubleshooting the POP3 Adapter</span></span>](../core/troubleshooting-the-pop3-adapter.md)