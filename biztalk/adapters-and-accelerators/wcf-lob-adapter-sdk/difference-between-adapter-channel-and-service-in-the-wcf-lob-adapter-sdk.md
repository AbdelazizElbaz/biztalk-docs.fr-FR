---
title: "Différence entre le canal de l’adaptateur et le service dans WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24d41d96-0ea1-4a97-bd45-b65afdbbd923
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e377568887d3d626e288fc47f82714b189d44b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="difference-between-adapter-channel-and-service-in-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="6473b-102">Différence entre le canal de l’adaptateur et le service dans WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="6473b-102">Difference between adapter channel and service in the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="6473b-103">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] et [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] chacun d’eux fournit un ensemble d’API qui peut être utilisé pour exposer les fonctionnalités d’application à l’utilisation des applications sur le même ordinateur ou sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="6473b-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] each provide a set of APIs that can be used to expose application functionality to consuming applications on the same computer or across a network.</span></span> <span data-ttu-id="6473b-104">Pour choisir le framework plus approprié, vous devez prendre en compte les propriétés de l’application du système cible que vous exposez, ainsi que les exigences d’entreprise pour la fonctionnalité exposée.</span><span class="sxs-lookup"><span data-stu-id="6473b-104">To choose the most appropriate framework, you must consider the properties of the target system application you are exposing as well as the business requirements for the exposed functionality.</span></span> <span data-ttu-id="6473b-105">Cette rubrique fournit des instructions qui vous permet de choisir le framework approprié.</span><span class="sxs-lookup"><span data-stu-id="6473b-105">This topic provides guidelines that you can use to choose the appropriate framework.</span></span>  
  
## <a name="when-to-write-an-adapter"></a><span data-ttu-id="6473b-106">Lorsque d’écrire un adaptateur</span><span class="sxs-lookup"><span data-stu-id="6473b-106">When to Write an Adapter</span></span>  
 <span data-ttu-id="6473b-107">Envisagez d’écrire un adaptateur à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] lorsque :</span><span class="sxs-lookup"><span data-stu-id="6473b-107">Consider writing an adapter using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] when:</span></span>  
  
-   <span data-ttu-id="6473b-108">Le système cible est un existant, non -*Web services activés* système</span><span class="sxs-lookup"><span data-stu-id="6473b-108">The target system is an existing, non-*Web services-enabled* system</span></span>  
  
-   <span data-ttu-id="6473b-109">Le système cible est dynamique et peut être amélioré avec les nouvelles opérations</span><span class="sxs-lookup"><span data-stu-id="6473b-109">The target system is dynamic and can be enhanced with new operations</span></span>  
  
-   <span data-ttu-id="6473b-110">Le système cible a une grande quantité de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6473b-110">The target system has a large amount of metadata</span></span>  
  
-   <span data-ttu-id="6473b-111">Il existe un grand nombre divers d’utilisateurs pour les données du système cible</span><span class="sxs-lookup"><span data-stu-id="6473b-111">There is a large, diverse number of users for the target system's data</span></span>  
  
-   <span data-ttu-id="6473b-112">Applications consommatrices ont besoin des fonctionnalités de découverte de métadonnées application riche</span><span class="sxs-lookup"><span data-stu-id="6473b-112">Consuming applications need rich application metadata discovery functionality</span></span>  
  
 <span data-ttu-id="6473b-113">Par exemple, si le système cible contient des centaines d’opérations de gestion des demandes de remboursement de soins de santé et les opérations sont dynamiques (ce qui signifie que les utilisateurs peuvent ajouter de nouvelles opérations qui effectuent des tâches supplémentaires), il est judicieux d’exposer cette fonctionnalité à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6473b-113">For example, if the target system contains hundreds of operations for managing health care claims, and the operations are dynamic (meaning users can add new operations that perform additional tasks), it makes sense to expose this functionality using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="6473b-114">Cela garantit que les nouvelles opérations sont détectables par les applications à l’aide de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6473b-114">This will ensure that new operations are discoverable by applications using the adapter.</span></span> <span data-ttu-id="6473b-115">Avec [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], vous devrez modifier le contrat de service, car elle est statique.</span><span class="sxs-lookup"><span data-stu-id="6473b-115">With [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], you would have to modify the service contract because it is static.</span></span>  
  
## <a name="when-to-write-a-service"></a><span data-ttu-id="6473b-116">Quand un Service d’écriture</span><span class="sxs-lookup"><span data-stu-id="6473b-116">When to Write a Service</span></span>  
 <span data-ttu-id="6473b-117">Utilisez le *modèle de Service WCF* pour créer un service lorsque :</span><span class="sxs-lookup"><span data-stu-id="6473b-117">Use the *WCF Service Model* to create a service when:</span></span>  
  
-   <span data-ttu-id="6473b-118">Le système cible est statique et a un ensemble fixe d’opérations</span><span class="sxs-lookup"><span data-stu-id="6473b-118">The target system is static and has a fixed set of operations</span></span>  
  
-   <span data-ttu-id="6473b-119">Le système cible a peu ou pas de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6473b-119">The target system has little or no metadata</span></span>  
  
-   <span data-ttu-id="6473b-120">Les développeurs de service ont connaissance de l’application doit être exposée</span><span class="sxs-lookup"><span data-stu-id="6473b-120">Service developers have detailed knowledge of the application to be exposed</span></span>  
  
-   <span data-ttu-id="6473b-121">Une nouvelle application est exposée.</span><span class="sxs-lookup"><span data-stu-id="6473b-121">A brand new application is being exposed</span></span>  
  
-   <span data-ttu-id="6473b-122">Vous créez des adaptateurs de transport générique</span><span class="sxs-lookup"><span data-stu-id="6473b-122">You are creating generic transport adapters</span></span>  
  
 <span data-ttu-id="6473b-123">Par exemple, si le système cible contient 20 opérations pour la gestion des équipes sportives, vous pouvez exposer les opérations comme un contrat statique à l’aide de [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6473b-123">For example, if the target system contains 20 operations for managing sports teams, you can expose the operations as a static contract using [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span> <span data-ttu-id="6473b-124">En procédant ainsi, vous évitez d’implémenter les fonctionnalités de métadonnées inutiles et vous pouvez réduire potentiellement des temps de développement.</span><span class="sxs-lookup"><span data-stu-id="6473b-124">By doing so, you avoid implementing unnecessary metadata features and you can potentially minimize development time.</span></span>  
  
## <a name="when-to-write-a-channel"></a><span data-ttu-id="6473b-125">Lorsque d’écrire un canal</span><span class="sxs-lookup"><span data-stu-id="6473b-125">When to Write a Channel</span></span>  
 <span data-ttu-id="6473b-126">Utilisez le *modèle de canal WCF* pour créer un canal lorsque :</span><span class="sxs-lookup"><span data-stu-id="6473b-126">Use the *WCF Channel Model* to create a channel when:</span></span>  
  
-   <span data-ttu-id="6473b-127">Création d’un protocole de câble.</span><span class="sxs-lookup"><span data-stu-id="6473b-127">Creating a wire protocol.</span></span> <span data-ttu-id="6473b-128">Exemples de protocoles de transmission de protocole WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="6473b-128">Examples of wire protocols include WS-ReliableMessaging Protocol.</span></span>  
  
-   <span data-ttu-id="6473b-129">Envoyer/recevoir des messages WCF via un transport autre que ceux qui sont inclus dans WCF (TCP, HTTP, canaux nommés, MSMQ et PeerChannel).</span><span class="sxs-lookup"><span data-stu-id="6473b-129">Send/receive WCF messages over a transport other than ones that are included in WCF (TCP, HTTP, Named Pipes, MSMQ and PeerChannel).</span></span> <span data-ttu-id="6473b-130">Par exemple, vous pouvez écrire un transport UDP, TIBCO ou un transport de messagerie Service JMS (Java).</span><span class="sxs-lookup"><span data-stu-id="6473b-130">For example, you can write a UDP transport, TIBCO, or a Java Messaging Service (JMS) transport.</span></span>  
  
-   <span data-ttu-id="6473b-131">Intégration avec un système qui n’est pas exposé comme un service Web.</span><span class="sxs-lookup"><span data-stu-id="6473b-131">Integrating with a system that is not exposed as a Web service.</span></span>  <span data-ttu-id="6473b-132">Dans ce cas, votre transport agit comme un adaptateur adaptation des messages WCF au format de message du système existant ou d’API, ce qui permet un client WCF pour communiquer directement avec le système existant.</span><span class="sxs-lookup"><span data-stu-id="6473b-132">In this case your transport acts as an adapter adapting WCF messages to the existing system's message format or API allowing a WCF client to talk directly to the existing system.</span></span> <span data-ttu-id="6473b-133">Ceci est le transport TCP amélioration des Services Web (WSE) 3.0.</span><span class="sxs-lookup"><span data-stu-id="6473b-133">An example of this is the Web Services Enhancement (WSE) 3.0 TCP transport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6473b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6473b-134">See Also</span></span>  
 <span data-ttu-id="6473b-135">[Planifier et concevoir un adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span><span class="sxs-lookup"><span data-stu-id="6473b-135">[Plan and design an adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span></span>  
 [<span data-ttu-id="6473b-136">Comprendre le système métier avec le SDK de l’adaptateur WCF LOB</span><span class="sxs-lookup"><span data-stu-id="6473b-136">Understand the LOB system with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)