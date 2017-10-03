---
title: "Types d’échecs de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transformation stage
- assembly stage
- errors, disassembly stage
- errors, assembly stage
- routing, errors
- errors, transformation stage
- errors, messages [HAT]
- errors, routing
- disassembly stage, errors
- messages, errors [HAT]
ms.assetid: 3a8e1c58-4b53-4439-837d-aaa233eb9158
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 466c7c21fd1a00e192307dd82384dc613b6697a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-message-failures"></a><span data-ttu-id="4f1de-102">Types d'échecs associés aux messages</span><span class="sxs-lookup"><span data-stu-id="4f1de-102">Types of Message Failures</span></span>
<span data-ttu-id="4f1de-103">Cette rubrique répertorie les différents stades auxquels un échec de message peut survenir.</span><span class="sxs-lookup"><span data-stu-id="4f1de-103">This topic lists different points where a message failure may occur.</span></span>  
  
 <span data-ttu-id="4f1de-104">**Échecs dans la phase de désassemblage**</span><span class="sxs-lookup"><span data-stu-id="4f1de-104">**Failures in the disassembly phase**</span></span>  
  
 <span data-ttu-id="4f1de-105">Le traitement peut échouer au cours de la phase de désassemblage, suite à la défaillance de l'un des composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f1de-105">Processing might also fail during the disassembly phase; that is, failure in one of the pipeline components.</span></span> <span data-ttu-id="4f1de-106">Par exemple, le déchiffrement peut échouer en raison de l'absence de certificat de chiffrement sur le serveur de traitement ou un échec d'analyse peut être dû à un problème au niveau du schéma ou du message.</span><span class="sxs-lookup"><span data-stu-id="4f1de-106">For example, decryption failed due to absence of decryption cert on the processing server, or parsing failure due to problem either in the schema or in the message.</span></span>  
  
 <span data-ttu-id="4f1de-107">**Échecs lors du routage**</span><span class="sxs-lookup"><span data-stu-id="4f1de-107">**Failures in routing**</span></span>  
  
 <span data-ttu-id="4f1de-108">Une fois que le désassemblage du message a été correctement effectué, le point de défaillance potentiel suivant est le routage, par exemple lorsque des utilisateurs activent un emplacement de réception correspondant à une orchestration et qu'ils oublient d'inscrire l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="4f1de-108">After a message disassembles successfully, the next potential failure point is routing; for example, users enable a corresponding receive location of an orchestration and forget to enlist the orchestration.</span></span> <span data-ttu-id="4f1de-109">Dans ce cas, le routage du message collecté à partir de l'emplacement de réception échoue et la base de données MessageBox génère un rapport d'échec du routage.</span><span class="sxs-lookup"><span data-stu-id="4f1de-109">In this case, the message picked up from the receive location fails routing and the MessageBox database generates a Routing Failure report.</span></span>  
  
 <span data-ttu-id="4f1de-110">Les rapports d'échec de routage sont répertoriés dans la console Administration de BizTalk Server comme des messages suspendus ne pouvant être repris.</span><span class="sxs-lookup"><span data-stu-id="4f1de-110">Routing Failure reports are listed in the BizTalk Server Administration Console as non-resumable suspended messages.</span></span> <span data-ttu-id="4f1de-111">Chaque rapport d'échec de routage contient un instantané de la propriété du message pris lors de l'échec du routage.</span><span class="sxs-lookup"><span data-stu-id="4f1de-111">Each Routing Failure report contains a message property snap shot taken when the routing failure occurred.</span></span> <span data-ttu-id="4f1de-112">Vous pouvez utiliser les informations contenues dans chaque rapport pour déterminer la raison de l'échec du routage pour le message concerné.</span><span class="sxs-lookup"><span data-stu-id="4f1de-112">You can use the information in each report to determine why routing failed for its associated message.</span></span> <span data-ttu-id="4f1de-113">Si ce message peut être repris, vous pouvez corriger le problème de routage et reprendre le message afin de poursuivre son traitement.</span><span class="sxs-lookup"><span data-stu-id="4f1de-113">If the associated message is resumable, you can correct the routing problem and resume the message so that processing continues.</span></span> <span data-ttu-id="4f1de-114">Les rapports d'échec de routage sont affichés dans la liste de résultats avec un nom de service et un type de service non renseignés.</span><span class="sxs-lookup"><span data-stu-id="4f1de-114">Routing Failure reports are listed in the results list with a blank service name and service type.</span></span> <span data-ttu-id="4f1de-115">Lorsque vous terminez une instance suspendue, le rapport de l'échec du routage associé à cette instance est automatiquement supprimé par le travail Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb exécuté toutes les minutes par défaut.</span><span class="sxs-lookup"><span data-stu-id="4f1de-115">When you terminate a suspended instance, the Routing Failure report associated with the suspended instance is automatically deleted by the Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job that runs every minute by default.</span></span> <span data-ttu-id="4f1de-116">Pour plus d’informations sur le travail Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb, voir [Structure de base de données et les travaux](../core/database-structure-and-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="4f1de-116">For more information about the Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job, see [Database Structure and Jobs](../core/database-structure-and-jobs.md).</span></span>  
  
 <span data-ttu-id="4f1de-117">**Échecs lors de la phase de transformation**</span><span class="sxs-lookup"><span data-stu-id="4f1de-117">**Failures during the transformation phase**</span></span>  
  
-   <span data-ttu-id="4f1de-118">**Messages reçus**.</span><span class="sxs-lookup"><span data-stu-id="4f1de-118">**Received Messages**.</span></span> <span data-ttu-id="4f1de-119">lorsqu'un message est reçu à partir d'un emplacement de réception, il est désassemblé (par exemple, déchiffré et analysé), il peut éventuellement être transformé en un format différent par le biais d'un mappage entrant spécifié sur un port de réception, puis il est publié dans la base de données MessageBox en vue de son routage vers une orchestration ou un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="4f1de-119">When a message is received from Receive Location, the message is disassembled (for example, decrypted and parsed), the message might optionally be transformed to a different format via an Inbound Map specified on a receive Port, and published to the MessageBox for routing to an orchestration or a Send Port.</span></span> <span data-ttu-id="4f1de-120">Dans ce cas, le traitement peut échouer au cours de la phase de transformation en raison d'un mappage entrant incorrect ou de problèmes dans le schéma ou dans le message reçu.</span><span class="sxs-lookup"><span data-stu-id="4f1de-120">In this case, processing may fail during transformation phase due to incorrect Inbound Map, or problems in the schema or in the message received.</span></span>  
  
-   <span data-ttu-id="4f1de-121">**Les Messages envoyés**.</span><span class="sxs-lookup"><span data-stu-id="4f1de-121">**Sent Messages**.</span></span> <span data-ttu-id="4f1de-122">lorsqu'un message est envoyé vers un emplacement d'envoi, un mappage sortant, configuré sur le port d'envoi, peut éventuellement transformer le message.</span><span class="sxs-lookup"><span data-stu-id="4f1de-122">When a message is to be sent to a Send Location, an Outbound Map configured on Send Port might optionally transform the message.</span></span> <span data-ttu-id="4f1de-123">Ensuite, le message transformé est assemblé et transmis à l'adaptateur pour être transféré vers l'emplacement d'envoi.</span><span class="sxs-lookup"><span data-stu-id="4f1de-123">Then the transformed message is assembled and handed to the adapter for final transmission to the Send Location.</span></span> <span data-ttu-id="4f1de-124">Dans ce cas, le traitement peut échouer au cours de la phase de transformation, du fait d'un mappage sortant incorrect ou d'un problème dans le schéma ou dans le message source.</span><span class="sxs-lookup"><span data-stu-id="4f1de-124">In this case, processing may fail during transformation phase due to incorrect Outbound Map or problem in schema or source message.</span></span>  
  
 <span data-ttu-id="4f1de-125">**Échecs dans la phase d’assemblage**</span><span class="sxs-lookup"><span data-stu-id="4f1de-125">**Failures in the message assembly phase**</span></span>  
  
 <span data-ttu-id="4f1de-126">Le traitement peut également échouer lors de la phase d'assemblage, c'est-à-dire suite à une défaillance d'un composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f1de-126">Processing can also fail during message assembly phase – in other words, failing in pipeline component.</span></span> <span data-ttu-id="4f1de-127">Une fois le message correctement assemblé, le point de défaillance potentiel suivant est la transmission à l'emplacement d'envoi. Par exemple, l'emplacement d'envoi (qui appartient au partenaire) peut être défaillant ou absent.</span><span class="sxs-lookup"><span data-stu-id="4f1de-127">After a message successfully assembles, the next potential failure point becomes transmission to Send Location; for example, the Send Location (which belongs to the partner) might be down or not exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1de-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f1de-128">See Also</span></span>  
 [<span data-ttu-id="4f1de-129">Enquête sur les échecs de messages, de Port et d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="4f1de-129">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)