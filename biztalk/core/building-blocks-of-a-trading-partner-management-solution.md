---
title: "Solution de gestion de blocs de construction d’un commercial partenaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0dabb562-7065-44b8-a26f-658d70b126eb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3415d6beec0097b05c68d7a73a320317704dc5ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="building-blocks-of-a-trading-partner-management-solution"></a><span data-ttu-id="c92b7-102">Blocs de construction d'une solution de gestion des partenaires commerciaux</span><span class="sxs-lookup"><span data-stu-id="c92b7-102">Building Blocks of a Trading Partner Management Solution</span></span>
## <a name="overview"></a><span data-ttu-id="c92b7-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c92b7-103">Overview</span></span>
<span data-ttu-id="c92b7-104">L'un des principaux atouts de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est de permettre aux utilisateurs d'activer la communication interentreprise avec leurs partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="c92b7-104">One of the core value propositions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to empower customers to enable business-to-business (B2B) communication with their business partners.</span></span> <span data-ttu-id="c92b7-105">Pour répondre à de tels besoins, les entreprises doivent modéliser, stocker et gérer des informations sur les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c92b7-105">To fulfill such business needs, enterprises need to model, store, and manage information about:</span></span>  
  
-   <span data-ttu-id="c92b7-106">les partenaires et leurs activités ;</span><span class="sxs-lookup"><span data-stu-id="c92b7-106">Partners and their businesses</span></span>  
  
-   <span data-ttu-id="c92b7-107">les règles de l'accord avec les partenaires (protocoles de codage des messages (normes EDI), protocoles de transport à utiliser (AS2), etc.).</span><span class="sxs-lookup"><span data-stu-id="c92b7-107">Rules of engagement with the partners – These include details such as which message encoding protocol to use (EDI standards), which transport protocol to use (AS2), etc.</span></span>  
  
 <span data-ttu-id="c92b7-108">Alors que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] continue à prendre en charge EDI et AS2, il ajoute les concepts fondamentaux autour de la gestion et de stocker des informations sur les partenaires et leurs activités.</span><span class="sxs-lookup"><span data-stu-id="c92b7-108">While [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] continues to provide support for EDI and AS2, it adds to the fundamental concepts around how to manage and store information about partners and their business.</span></span> <span data-ttu-id="c92b7-109">Normes EDI, messagerie AS2 et les concepts de rassembler constituent les blocs de construction d’une communication B2B ou d’une solution de gestion des partenaires commerciaux (GPC).</span><span class="sxs-lookup"><span data-stu-id="c92b7-109">EDI standards, AS2 messaging, and the concepts put together form the building blocks of a B2B communication or a Trading Partner Management (TPM) solution.</span></span> <span data-ttu-id="c92b7-110">Cette section fournit des explications détaillées sur ces concepts.</span><span class="sxs-lookup"><span data-stu-id="c92b7-110">This section provides detailed explanation about these concepts.</span></span> 
 
 <span data-ttu-id="c92b7-111">Pour plus d’informations sur la façon [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge EDI et AS2, consultez :</span><span class="sxs-lookup"><span data-stu-id="c92b7-111">For information about how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports EDI and AS2, see:</span></span>
 
 - [<span data-ttu-id="c92b7-112">Fonctionnalité EDI BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c92b7-112">BizTalk Server EDI functionality</span></span>](../core/biztalk-server-edi-functionality.md)
 - [<span data-ttu-id="c92b7-113">Fonctionnalités AS2 de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c92b7-113">BizTalk Server AS2 functionality</span></span>](../core/biztalk-server-as2-functionality.md)
  
## <a name="in-this-section"></a><span data-ttu-id="c92b7-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c92b7-114">In This Section</span></span>  
  
-   [<span data-ttu-id="c92b7-115">Partenaires commerciaux et les profils d’entreprise</span><span class="sxs-lookup"><span data-stu-id="c92b7-115">Trading partners and business profiles</span></span>](../core/trading-partners-and-business-profiles.md)
  
-   [<span data-ttu-id="c92b7-116">Paramètres de protocole</span><span class="sxs-lookup"><span data-stu-id="c92b7-116">Protocol settings</span></span>](../core/protocol-settings.md)  
  
-   [<span data-ttu-id="c92b7-117">Accord de partenariat commercial</span><span class="sxs-lookup"><span data-stu-id="c92b7-117">Trading partner agreement</span></span>](../core/trading-partner-agreement.md)  
  
-   [<span data-ttu-id="c92b7-118">Vue d’ensemble : définition d’un commercial de solution de gestion des partenaires</span><span class="sxs-lookup"><span data-stu-id="c92b7-118">Putting it all together: Defining a trading partner management solution</span></span>](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="c92b7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c92b7-119">See Also</span></span>  
 [<span data-ttu-id="c92b7-120">Gestion des partenaires commerciaux à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c92b7-120">Trading Partner Management Using BizTalk Server</span></span>](../core/trading-partner-management-using-biztalk-server.md)