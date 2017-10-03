---
title: Processus publics | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public processes, orchestrations
- business processes, public processes
- public processes, trading partners
- BTARN, public processes
- orchestrations, public-process orchestrations
- public processes
- trading partners, public processes
- public processes, about public processes
ms.assetid: 5ccc7449-5741-4d49-beb6-567bcd93f679
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6634a5d5871deac48fad1defbd79fae8f5f384ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="public-processes"></a><span data-ttu-id="490ac-102">Processus publics</span><span class="sxs-lookup"><span data-stu-id="490ac-102">Public Processes</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="490ac-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implémente le processus d’entreprise qui impliquent l’intégration avec des partenaires en tant que processus publics commerciaux.</span><span class="sxs-lookup"><span data-stu-id="490ac-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implements business processes that involve integration with trading partners as public processes.</span></span> <span data-ttu-id="490ac-104">Il met en œuvre des processus d’entreprise qui sont internes à une organisation en tant que processus privés.</span><span class="sxs-lookup"><span data-stu-id="490ac-104">It implements business processes that are internal to an organization as private processes.</span></span> <span data-ttu-id="490ac-105">À l’aide de processus publics et privés isole les Framework RNIF (RosettaNet Implementation) gérer (dans le processus public) à partir du traitement du service de contenu et l’intégration de serveur principal (dans le processus privé).</span><span class="sxs-lookup"><span data-stu-id="490ac-105">Using public and private processes isolates RosettaNet Implementation Framework (RNIF) handling (in the public process) from the service content processing and back-end integration (in the private process).</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="490ac-106">implémente les processus publics comme longue des orchestrations BizTalk.</span><span class="sxs-lookup"><span data-stu-id="490ac-106"> implements public processes as long-running BizTalk orchestrations.</span></span> <span data-ttu-id="490ac-107">Une orchestration de processus publics s'exécute côté initiateur, et une autre côté répondeur.</span><span class="sxs-lookup"><span data-stu-id="490ac-107">One public-process orchestration runs on the initiator side and one on the responder side.</span></span> <span data-ttu-id="490ac-108">Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation fournit des versions de l’initiateur et le répondeur orchestrations de processus publics pour RNIF 1.1 et RNIF 2.01.</span><span class="sxs-lookup"><span data-stu-id="490ac-108">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program provides versions of the initiator and responder public-process orchestrations for both RNIF 1.1 and RNIF 2.01.</span></span>  
  
 <span data-ttu-id="490ac-109">Ces orchestrations de processus publics implémentent tous les processus RNIF.</span><span class="sxs-lookup"><span data-stu-id="490ac-109">These public-process orchestrations implement all RNIF processes.</span></span> <span data-ttu-id="490ac-110">Les processus publics masquent la complexité de la spécification RNIF du reste des composants.</span><span class="sxs-lookup"><span data-stu-id="490ac-110">Public processes hide the complexity of RNIF from the rest of the components.</span></span> <span data-ttu-id="490ac-111">Outre l’application du flux de messages RNIF conforme, le processus public détermine les paramètres de suivi par défaut et fournit des informations d’état de processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="490ac-111">Besides enforcing the RNIF-compliant message flow, the public process also determines default-tracking settings and provides process state information at run time.</span></span> <span data-ttu-id="490ac-112">Il ne traite pas le contenu de service d’un message.</span><span class="sxs-lookup"><span data-stu-id="490ac-112">It does not process the service content of a message.</span></span> <span data-ttu-id="490ac-113">Le processus privé pour cela.</span><span class="sxs-lookup"><span data-stu-id="490ac-113">The private process does this.</span></span>  
  
 <span data-ttu-id="490ac-114">Chaque accord de partenariat commercial fait référence à un seul processus public pour lancer ou de répondre aux actions de processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="490ac-114">Each trading partner agreement references a single public process to initiate or respond to Partner Interface Process (PIP) actions.</span></span> <span data-ttu-id="490ac-115">Toutefois, les processus publics sont indépendantes du PIP.</span><span class="sxs-lookup"><span data-stu-id="490ac-115">However, the public processes are PIP-agnostic.</span></span>  
  
 <span data-ttu-id="490ac-116">Les spécifications de RosettaNet déterminent la conception du processus public.</span><span class="sxs-lookup"><span data-stu-id="490ac-116">The RosettaNet specifications dictate the design of the public process.</span></span> <span data-ttu-id="490ac-117">Il est recommandé de ne pas modifier un processus public.</span><span class="sxs-lookup"><span data-stu-id="490ac-117">It is recommended that you do not modify a public process.</span></span> <span data-ttu-id="490ac-118">L’orchestration de processus publics est créée et signé.</span><span class="sxs-lookup"><span data-stu-id="490ac-118">The public-process orchestration is versioned and signed.</span></span> <span data-ttu-id="490ac-119">Si vous modifiez un processus public, il ne pourra plus être compatibles RNIF.</span><span class="sxs-lookup"><span data-stu-id="490ac-119">If you modify a public process, it will no longer be RNIF-compliant.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="490ac-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="490ac-120">In This Section</span></span>  
  
-   [<span data-ttu-id="490ac-121">Processus Public d’initiateur</span><span class="sxs-lookup"><span data-stu-id="490ac-121">Initiator Public Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)  
  
-   [<span data-ttu-id="490ac-122">Processus Public de répondeur</span><span class="sxs-lookup"><span data-stu-id="490ac-122">Responder Public Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)