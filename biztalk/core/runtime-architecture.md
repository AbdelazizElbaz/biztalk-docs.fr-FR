---
title: Architecture de runtime | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- architecture, runtime
- runtime
ms.assetid: feff9a84-f19b-44c9-8d05-8e6015bb1ef9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e45ac745dbf6704f06f61155b3f57edfdec9e09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="runtime-architecture"></a><span data-ttu-id="9bc65-102">Architecture d'exécution</span><span class="sxs-lookup"><span data-stu-id="9bc65-102">Runtime Architecture</span></span>
<span data-ttu-id="9bc65-103">Avant de voir plus en détail les différents composants de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est important de comprendre comment ces composants s'intègrent dans l'architecture globale du produit.</span><span class="sxs-lookup"><span data-stu-id="9bc65-103">Before reviewing more detailed information about the various components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is important that you have an understanding of how the components fit into the overall architecture of the product.</span></span> <span data-ttu-id="9bc65-104">Le composant d'exécution de BizTalk Server repose sur une architecture de type « publication-abonnement », dans laquelle un message est publié au sein du système, puis réceptionné par un ou plusieurs abonnés actifs.</span><span class="sxs-lookup"><span data-stu-id="9bc65-104">The BizTalk Server runtime is built on a publish/subscribe architecture in which a message is published into the system, and then received by one or more active subscribers.</span></span> <span data-ttu-id="9bc65-105">Différentes versions de cette architecture existent, mais le modèle implémenté dans BizTalk Server est souvent appelé *en fonction du contenu de publication/abonnement*.</span><span class="sxs-lookup"><span data-stu-id="9bc65-105">Different flavors of this architecture exist, but the model implemented in BizTalk Server is often called *content-based publish/subscribe*.</span></span>  
  
 <span data-ttu-id="9bc65-106">Dans ce modèle, les abonnés définissent les messages qu'ils veulent recevoir à l'aide d'un ensemble de critères.</span><span class="sxs-lookup"><span data-stu-id="9bc65-106">In a content-based publish/subscribe model, subscribers specify the messages they want to receive using a set of criteria about the message.</span></span> <span data-ttu-id="9bc65-107">Lorsqu'il est publié, un message est analysé et envoyé à tous les abonnés actifs dont l'abonnement (défini par le biais d'expressions de filtre) correspond.</span><span class="sxs-lookup"><span data-stu-id="9bc65-107">The message is evaluated at the time it is published, and all of the active subscribers with matching subscriptions (indicated by filter expressions), receive the message.</span></span> <span data-ttu-id="9bc65-108">Dans le cas de BizTalk Server, parler de contenu peut induire en erreur, car les critères utilisés pour les abonnements ne sont pas nécessairement liés au contenu des messages, mais peuvent également se rapporter à des informations contextuelles sur le message lui-même.</span><span class="sxs-lookup"><span data-stu-id="9bc65-108">As it applies to BizTalk Server, content-based is a bit of a misnomer, however, because the criteria used to build subscriptions do not have to come from the message content, and may include contextual information about the message as well.</span></span> <span data-ttu-id="9bc65-109">Pour plus d’informations, le mécanisme d’abonnement, consultez [publier et s’abonner une Architecture](../core/publish-and-subscribe-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="9bc65-109">For details of the subscription mechanism, see [Publish and Subscribe Architecture](../core/publish-and-subscribe-architecture.md).</span></span>  
  
 <span data-ttu-id="9bc65-110">Les sections suivantes décrivent les différents composants de l'architecture d'exécution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9bc65-110">The sections that follow describe the various components of the BizTalk Server runtime architecture.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9bc65-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9bc65-111">In This Section</span></span>  
  
-   [<span data-ttu-id="9bc65-112">Le Message BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="9bc65-112">The BizTalk Server Message</span></span>](../core/the-biztalk-server-message.md)  
  
-   [<span data-ttu-id="9bc65-113">Cycle de vie d’un Message</span><span class="sxs-lookup"><span data-stu-id="9bc65-113">Lifecycle of a Message</span></span>](../core/lifecycle-of-a-message.md)  
  
-   [<span data-ttu-id="9bc65-114">Le traitement du Message</span><span class="sxs-lookup"><span data-stu-id="9bc65-114">Processing the Message</span></span>](../core/processing-the-message.md)  
  
-   [<span data-ttu-id="9bc65-115">Messages de requête-réponse</span><span class="sxs-lookup"><span data-stu-id="9bc65-115">Request-Response Messaging</span></span>](../core/request-response-messaging.md)  
  
-   [<span data-ttu-id="9bc65-116">Le moteur de messagerie</span><span class="sxs-lookup"><span data-stu-id="9bc65-116">The Messaging Engine</span></span>](../core/the-messaging-engine.md)  
  
-   [<span data-ttu-id="9bc65-117">Entités</span><span class="sxs-lookup"><span data-stu-id="9bc65-117">Entities</span></span>](../core/entities.md)  
  
-   [<span data-ttu-id="9bc65-118">Artefacts</span><span class="sxs-lookup"><span data-stu-id="9bc65-118">Artifacts</span></span>](../core/artifacts.md)  
  
-   [<span data-ttu-id="9bc65-119">Enterprise Single Sign-On (SSO)</span><span class="sxs-lookup"><span data-stu-id="9bc65-119">Enterprise Single Sign-On (SSO)</span></span>](../core/enterprise-single-sign-on-sso.md)  
  
-   [<span data-ttu-id="9bc65-120">Moteur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="9bc65-120">Business Rules Engine</span></span>](../core/business-rules-engine.md)  
  
-   [<span data-ttu-id="9bc65-121">Assemblys BizTalk</span><span class="sxs-lookup"><span data-stu-id="9bc65-121">BizTalk Assemblies</span></span>](../core/biztalk-assemblies.md)