---
title: "Types de réponse FIN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, response types
- deploying, schemas
- FIN Response Reconciliation, message types
- FRR, deploying schemas
- schemas, deploying
- FIN Response Reconciliation, response types
- messages, message types
- response types [FIN Response Reconciliation]
ms.assetid: a6ef2f20-08ab-40d3-a0a5-cc4048ce0987
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54c890a5e0f51207cce1897b10095a87ae438793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-types"></a><span data-ttu-id="5be1f-102">Types de réponse FIN</span><span class="sxs-lookup"><span data-stu-id="5be1f-102">FIN Response Types</span></span>
<span data-ttu-id="5be1f-103">Rapprochement de réponse FIN (FRR) rapproche les réponses à un message de FIN de SWIFT catégorie 0 à 9.</span><span class="sxs-lookup"><span data-stu-id="5be1f-103">FIN Response Reconciliation (FRR) reconciles responses to any Category 0 to 9 SWIFT FIN message.</span></span> <span data-ttu-id="5be1f-104">En réponse à un de ces messages FIN, l’application de la FIN de SWIFT toujours envoie au moins et éventuellement plusieurs, accusé de réception (ACK) ou (NAK) de l’accusé de réception négatif.</span><span class="sxs-lookup"><span data-stu-id="5be1f-104">In response to one of these FIN messages, the SWIFT FIN application always sends at least one, and possibly more than one, acknowledgment (ACK) or negative acknowledgment (NAK).</span></span> <span data-ttu-id="5be1f-105">Le tableau suivant présente les types des messages sortants et entrants (réponse) les messages traités par FRR.</span><span class="sxs-lookup"><span data-stu-id="5be1f-105">The following table shows the message types of the outbound and inbound (response) messages processed by FRR.</span></span>  
  
|<span data-ttu-id="5be1f-106">Sortant /</span><span class="sxs-lookup"><span data-stu-id="5be1f-106">Outbound/</span></span><br /><br /> <span data-ttu-id="5be1f-107">en entrée</span><span class="sxs-lookup"><span data-stu-id="5be1f-107">inbound</span></span>|<span data-ttu-id="5be1f-108">type de message</span><span class="sxs-lookup"><span data-stu-id="5be1f-108">Message type</span></span>|<span data-ttu-id="5be1f-109">État du message</span><span class="sxs-lookup"><span data-stu-id="5be1f-109">Message status</span></span>|  
|----------------------------|------------------|--------------------|  
|<span data-ttu-id="5be1f-110">Sortant</span><span class="sxs-lookup"><span data-stu-id="5be1f-110">Outbound</span></span>|<span data-ttu-id="5be1f-111">Tous les types de messages SWIFT FIN catégorie 0 à 9</span><span class="sxs-lookup"><span data-stu-id="5be1f-111">All Category 0 to 9 SWIFT FIN message types</span></span>|<span data-ttu-id="5be1f-112">Néant</span><span class="sxs-lookup"><span data-stu-id="5be1f-112">N/A</span></span>|  
|<span data-ttu-id="5be1f-113">Trafic entrant</span><span class="sxs-lookup"><span data-stu-id="5be1f-113">Inbound</span></span>|<span data-ttu-id="5be1f-114">MQ Series panoramique/NAN (au niveau du transport MQSeries l’accusé de réception/NON-RÉCEPTION)</span><span class="sxs-lookup"><span data-stu-id="5be1f-114">MQ Series PAN/NAN (MQ Series transport-level ACK/NAK)</span></span>|<span data-ttu-id="5be1f-115">Accusé de réception de transport MQSeries</span><span class="sxs-lookup"><span data-stu-id="5be1f-115">MQSeries transport acknowledgment</span></span>|  
||<span data-ttu-id="5be1f-116">MT010 (avertissement de non-remise)</span><span class="sxs-lookup"><span data-stu-id="5be1f-116">MT010 (Non-Delivery Warning)</span></span>|<span data-ttu-id="5be1f-117">SWIFT envoyé avec succès la version d’origine du message au partenaire, mais n’est pas informé que le partenaire a reçu le message.</span><span class="sxs-lookup"><span data-stu-id="5be1f-117">SWIFT successfully sent the original message to the partner, but has no indication that the partner received the message.</span></span> <span data-ttu-id="5be1f-118">Si [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit plusieurs messages d’avertissement de Non remise (NDW), il effectue une itération et attend que le prochain message attendu.</span><span class="sxs-lookup"><span data-stu-id="5be1f-118">If [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives multiple Non-Delivery Warning (NDW) messages, it loops and waits for the next expected message.</span></span>|  
||<span data-ttu-id="5be1f-119">MT011 (accusé de réception)</span><span class="sxs-lookup"><span data-stu-id="5be1f-119">MT011 (Delivery Notification)</span></span>|<span data-ttu-id="5be1f-120">SWIFT envoyé avec succès la version d’origine du message au partenaire et a reçu une indication que le partenaire a reçu le message.</span><span class="sxs-lookup"><span data-stu-id="5be1f-120">SWIFT successfully sent the original message to the partner, and received an indication that the partner received the message.</span></span>|  
||<span data-ttu-id="5be1f-121">MT012 (Notification de l’expéditeur)</span><span class="sxs-lookup"><span data-stu-id="5be1f-121">MT012 (Sender Notification)</span></span>|<span data-ttu-id="5be1f-122">SWIFT a reçu le message d’origine à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5be1f-122">SWIFT successfully received the original message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>|  
||<span data-ttu-id="5be1f-123">MT015 (DNK ou NAK retardé)</span><span class="sxs-lookup"><span data-stu-id="5be1f-123">MT015 (DNK, or Delayed NAK)</span></span>|<span data-ttu-id="5be1f-124">SWIFT n'a pas envoyé le message d’origine au partenaire.</span><span class="sxs-lookup"><span data-stu-id="5be1f-124">SWIFT has not successfully sent the original message to the partner.</span></span>|  
||<span data-ttu-id="5be1f-125">MT019 (abandon de Notification)</span><span class="sxs-lookup"><span data-stu-id="5be1f-125">MT019 (Abort Notification)</span></span>|<span data-ttu-id="5be1f-126">Interruption de la transmission de message à SWIFT.</span><span class="sxs-lookup"><span data-stu-id="5be1f-126">Message transmission aborted at SWIFT.</span></span>|  
||<span data-ttu-id="5be1f-127">MTS21_FIN_ACKNAK (accusé de réception ou un accusé de réception négatif d’un message FIN envoyé par un LT (accusé de réception/NON-RÉCEPTION))</span><span class="sxs-lookup"><span data-stu-id="5be1f-127">MTS21_FIN_ACKNAK (Acknowledgment or negative acknowledgment of a FIN message sent by an LT (ACK/NAK))</span></span>|<span data-ttu-id="5be1f-128">SWIFT avec ou sans succès a reçu le message de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5be1f-128">SWIFT successfully or unsuccessfully received the message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="5be1f-129">Ce message décrit ces deux cas.</span><span class="sxs-lookup"><span data-stu-id="5be1f-129">This message covers both of these cases.</span></span> <span data-ttu-id="5be1f-130">S’il s’agit d’un accusé de réception ou un NAK est déterminée par la valeur dans le champ 451 du message (« 0 » pour l’accusé de réception) et « 1 » pour NAK.</span><span class="sxs-lookup"><span data-stu-id="5be1f-130">Whether it is an ACK or a NAK is determined by the value in the 451 field of the message ("0" for ACK and "1" for NAK).</span></span> <span data-ttu-id="5be1f-131">Il s’agit de la première réponse remise à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5be1f-131">This will be the first response delivered back to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>|  
  
## <a name="deployment-of-schemas-for-frr"></a><span data-ttu-id="5be1f-132">Déploiement de schémas pour FRR</span><span class="sxs-lookup"><span data-stu-id="5be1f-132">Deployment of Schemas for FRR</span></span>  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="5be1f-133">le programme d’installation déploie des schémas dans FrrSchemas.dll pour tous les messages au niveau du système (comme indiqué dans le tableau ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="5be1f-133"> setup deploys schemas in FrrSchemas.dll for all system-level messages (as shown in the table above).</span></span> <span data-ttu-id="5be1f-134">L’orchestration FRR requiert ces schémas à déployer.</span><span class="sxs-lookup"><span data-stu-id="5be1f-134">The FRR orchestration requires these schemas to be deployed.</span></span> <span data-ttu-id="5be1f-135">Étant donné que [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] le programme d’installation déploie ces schémas dans FrrSchemas.dll, vous n’avez pas à et ne devez pas déployer ces schémas dans un autre projet.</span><span class="sxs-lookup"><span data-stu-id="5be1f-135">Because [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup deploys these schemas in FrrSchemas.dll, you do not have to, and must not, deploy these schemas in another project.</span></span> <span data-ttu-id="5be1f-136">Ceci génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="5be1f-136">Doing so will generate an error.</span></span>  
  
 <span data-ttu-id="5be1f-137">FRRSchemas.dll inclut les schémas suivants :</span><span class="sxs-lookup"><span data-stu-id="5be1f-137">FRRSchemas.dll includes the following schemas:</span></span>  
  
-   <span data-ttu-id="5be1f-138">TransportAck</span><span class="sxs-lookup"><span data-stu-id="5be1f-138">TransportAck</span></span>  
  
-   <span data-ttu-id="5be1f-139">MT010</span><span class="sxs-lookup"><span data-stu-id="5be1f-139">MT010</span></span>  
  
-   <span data-ttu-id="5be1f-140">MT011</span><span class="sxs-lookup"><span data-stu-id="5be1f-140">MT011</span></span>  
  
-   <span data-ttu-id="5be1f-141">MT012</span><span class="sxs-lookup"><span data-stu-id="5be1f-141">MT012</span></span>  
  
-   <span data-ttu-id="5be1f-142">MT015</span><span class="sxs-lookup"><span data-stu-id="5be1f-142">MT015</span></span>  
  
-   <span data-ttu-id="5be1f-143">MT019</span><span class="sxs-lookup"><span data-stu-id="5be1f-143">MT019</span></span>  
  
-   <span data-ttu-id="5be1f-144">MTS21_FIN_ACKNAK</span><span class="sxs-lookup"><span data-stu-id="5be1f-144">MTS21_FIN_ACKNAK</span></span>