---
title: "L’installation des problèmes connus de lecture | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 245379f2-4048-4803-83ea-38dc23eb1a81
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6641e7974a0e1872b71794af6553d708e9619dd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="read-the-installation-known-issues"></a><span data-ttu-id="a2023-102">Lecture de l’installation des problèmes connus</span><span class="sxs-lookup"><span data-stu-id="a2023-102">Read the installation known issues</span></span>
[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]<span data-ttu-id="a2023-103">problèmes connus ont répertoriés dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="a2023-103"> have known issues listed in the following sections.</span></span>  
  
## <a name="swift-does-not-support-stress-testing-on-integration-test-bed-itb-and-swiftnet-stub-environment"></a><span data-ttu-id="a2023-104">SWIFT ne prend pas en charge les tests de Stress sur le banc d’essai intégration (ITB) et l’environnement de SWIFTNet Stub</span><span class="sxs-lookup"><span data-stu-id="a2023-104">SWIFT Does Not Support Stress Testing on Integration Test Bed (ITB) and SWIFTNet Stub Environment</span></span>  
 <span data-ttu-id="a2023-105">Le ITB ne fournit pas de contrat de niveau de Service (SLA) en termes de débit et ne peut pas garantir que les données sont complètement transmises ou cohérent.</span><span class="sxs-lookup"><span data-stu-id="a2023-105">The ITB does not provide Service Level Agreement (SLA) in terms of throughput, and cannot guarantee that data is completely transmitted or consistent.</span></span> <span data-ttu-id="a2023-106">Vous devez le test de stress du réseau de votre implémentation de la production dans l’environnement de pilote.</span><span class="sxs-lookup"><span data-stu-id="a2023-106">You should stress test your implementation on the production network in the Pilot environment.</span></span>  
  
 <span data-ttu-id="a2023-107">En outre, vous devez vous assurer que tous les nœuds (serveurs, des lignes et la bande passante) sont configurés correctement pour éviter toute perte de données.</span><span class="sxs-lookup"><span data-stu-id="a2023-107">Additionally, you must ensure that all of the nodes (server, lines, and bandwidth) are properly configured to avoid any data loss.</span></span> <span data-ttu-id="a2023-108">Voici les débits d’exemple typique :</span><span class="sxs-lookup"><span data-stu-id="a2023-108">Following are typical sample throughputs:</span></span>  
  
-   <span data-ttu-id="a2023-109">Interagir/Fileact envoyer sous ordinateur accentuée : 20 messages par minute</span><span class="sxs-lookup"><span data-stu-id="a2023-109">Interact/Fileact Send under stressed computer: 20 messages/minute</span></span>  
  
-   <span data-ttu-id="a2023-110">Interagir/Fileact recevoir sous ordinateur accentuée : 300-400 messages/minute</span><span class="sxs-lookup"><span data-stu-id="a2023-110">Interact/Fileact Receive under stressed computer: 300-400 messages/minute</span></span>  
  
 <span data-ttu-id="a2023-111">Pour plus d’informations, consultez votre documentation SWIFT.</span><span class="sxs-lookup"><span data-stu-id="a2023-111">For more information, see your SWIFT documentation.</span></span>  
  
## <a name="messages-not-pushed-when-queue-is-open"></a><span data-ttu-id="a2023-112">Messages non envoyées lors de la file d’attente est ouvert</span><span class="sxs-lookup"><span data-stu-id="a2023-112">Messages Not Pushed When Queue Is Open</span></span>  
 <span data-ttu-id="a2023-113">Lorsque vous utilisez interagir ou FileAct Store et le mode de transfert (msng), si la session avec la file d’attente est ouverte et que les messages ne sont pas envoyées, vous devez redémarrer SNLreceiver.exe.</span><span class="sxs-lookup"><span data-stu-id="a2023-113">When you are using InterAct or FileAct Store and Forward (SnF) mode, if the session with the queue is open and messages are not being pushed, then you must restart SNLreceiver.exe.</span></span> <span data-ttu-id="a2023-114">Cela permet d’éviter un problème avec SWIFT qui peut se produire occasionnellement.</span><span class="sxs-lookup"><span data-stu-id="a2023-114">This avoids an issue with SWIFT that can occur occasionally.</span></span>  
  
## <a name="you-must-use-cdata-when-passing-characters-like--and--in-message"></a><span data-ttu-id="a2023-115">Vous devez utiliser CDATA lors de la transmission des caractères tels que « < » et « & » dans le message</span><span class="sxs-lookup"><span data-stu-id="a2023-115">You Must Use CDATA when Passing Characters like "<" and "&" in message</span></span>  
 <span data-ttu-id="a2023-116">Le terme CDATA est utilisé sur les données de texte ne doivent pas être analysées par l’analyseur XML.</span><span class="sxs-lookup"><span data-stu-id="a2023-116">The term CDATA is used about text data that should not be parsed by the XML parser.</span></span>  <span data-ttu-id="a2023-117">Caractères tels que « < » et « & » ne sont pas autorisés dans les éléments XML.</span><span class="sxs-lookup"><span data-stu-id="a2023-117">Characters like "<" and "&" are illegal in XML elements.</span></span> <span data-ttu-id="a2023-118">« < » génère une erreur, car l’analyseur l’interprète comme le début d’un nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="a2023-118">"<" will generate an error because the parser interprets it as the start of a new element.</span></span> <span data-ttu-id="a2023-119">« & » génère une erreur, car l’analyseur l’interprète comme le début d’une entité de caractère.</span><span class="sxs-lookup"><span data-stu-id="a2023-119">"&" will generate an error because the parser interprets it as the start of a character entity.</span></span> <span data-ttu-id="a2023-120">Tous les éléments à l’intérieur d’une section CDATA sont ignoré par l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="a2023-120">Everything inside a CDATA section is ignored by the parser.</span></span> <span data-ttu-id="a2023-121">Une section CDATA commence par «\<! [CDATA [ » et se termine par «]]\>»</span><span class="sxs-lookup"><span data-stu-id="a2023-121">A CDATA section starts with "\<![CDATA[" and ends with "]]\>"</span></span>  
  
## <a name="you-must-use-passthrough-pipelines-with-payload-only-mode"></a><span data-ttu-id="a2023-122">Vous devez utiliser des Pipelines Passthrough avec le Mode de charge utile uniquement</span><span class="sxs-lookup"><span data-stu-id="a2023-122">You Must Use Passthrough Pipelines with Payload-Only Mode</span></span>  
 <span data-ttu-id="a2023-123">Si vous utilisez le mode de charge utile uniquement pour l’adaptateur InterAct, vous devez utiliser des pipelines de transfert sur l’envoi et ports de réception si vous n’utilisez pas les pipelines personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a2023-123">If you are using payload-only mode for the InterAct adapter, you must use pass-through pipelines on both the send and receive ports if you are not using custom pipelines.</span></span>  
  
## <a name="multiple-security-contexts-not-created-swiftnet-stub-computer"></a><span data-ttu-id="a2023-124">Plusieurs contextes de sécurité non créés (ordinateur SWIFTNet Stub)</span><span class="sxs-lookup"><span data-stu-id="a2023-124">Multiple Security Contexts Not Created (SWIFTNet Stub Computer)</span></span>  
 <span data-ttu-id="a2023-125">Sur un ordinateur de stub SWIFTNet, plusieurs contextes de sécurité ne sont pas créés pour les ports d’envoi différents.</span><span class="sxs-lookup"><span data-stu-id="a2023-125">On a SWIFTNet stub computer, multiple security contexts are not created for different send ports.</span></span> <span data-ttu-id="a2023-126">Plusieurs contextes de sécurité sont créées sur ITB.</span><span class="sxs-lookup"><span data-stu-id="a2023-126">Multiple security contexts are created on ITB.</span></span>