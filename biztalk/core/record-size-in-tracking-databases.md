---
title: Taille d’enregistrement dans les bases de données de suivi | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: be7a891b-2674-49a3-a8e0-6aa11a918bf2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1f4d09d1af92ce4777f5036885d81ea7bf3e648
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="record-size-in-tracking-databases"></a><span data-ttu-id="d023e-102">Taille d'enregistrement dans les bases de données de suivis</span><span class="sxs-lookup"><span data-stu-id="d023e-102">Record Size in Tracking Databases</span></span>
<span data-ttu-id="d023e-103">Pour vous aider à planifier la configuration matérielle requise pour BizTalk, le tableau suivant indique la taille d'enregistrement prévue pour différents enregistrements d'événement dans la base de données des suivis.</span><span class="sxs-lookup"><span data-stu-id="d023e-103">To help you plan your hardware requirements for BizTalk, the following table shows the expected record size for various event records in the Tracking database.</span></span>  
  
|<span data-ttu-id="d023e-104">Type d’action</span><span class="sxs-lookup"><span data-stu-id="d023e-104">Action Type</span></span>|<span data-ttu-id="d023e-105">Taille</span><span class="sxs-lookup"><span data-stu-id="d023e-105">Size</span></span>|<span data-ttu-id="d023e-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="d023e-106">Notes</span></span>|  
|-----------------|----------|-----------|  
|<span data-ttu-id="d023e-107">Déploiement d'un service</span><span class="sxs-lookup"><span data-stu-id="d023e-107">Deploying a Service</span></span>|<span data-ttu-id="d023e-108">1864 + taille des informations symboliques</span><span class="sxs-lookup"><span data-stu-id="d023e-108">1864 + Symbolic Information Size</span></span>|<span data-ttu-id="d023e-109">Les informations symboliques dépendent de la taille de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="d023e-109">Symbolic Information depends on the size of the orchestration.</span></span> <span data-ttu-id="d023e-110">Par exemple, une orchestration qui reçoit un message et renvoie un message contenant 2 formes nécessite environ 4 000 octets.</span><span class="sxs-lookup"><span data-stu-id="d023e-110">For example, an orchestration that receives one message and sends one message out with 2 shapes in it takes approximately 4000 bytes.</span></span>|  
|<span data-ttu-id="d023e-111">Instance de service ayant démarré et abouti</span><span class="sxs-lookup"><span data-stu-id="d023e-111">Started and Successfully Completed Service Instance</span></span>|<span data-ttu-id="d023e-112">Normalement, 252 octets.</span><span class="sxs-lookup"><span data-stu-id="d023e-112">Normally 252 bytes.</span></span><br /><br /> <span data-ttu-id="d023e-113">735 octets dans les cas extrêmes.</span><span class="sxs-lookup"><span data-stu-id="d023e-113">Extreme cases, can reach 735 bytes.</span></span>||  
|<span data-ttu-id="d023e-114">Instance de service ayant démarré et échoué ou rencontré une erreur</span><span class="sxs-lookup"><span data-stu-id="d023e-114">Started and Failed/Exception Met Service Instance</span></span>|<span data-ttu-id="d023e-115">Normalement, 252 octets + informations sur l'erreur.</span><span class="sxs-lookup"><span data-stu-id="d023e-115">Normally 252 bytes + error information.</span></span><br /><br /> <span data-ttu-id="d023e-116">735 octets + les informations sur l'erreur dans les cas extrêmes.</span><span class="sxs-lookup"><span data-stu-id="d023e-116">Extreme cases can reach 735 bytes + error information.</span></span>|<span data-ttu-id="d023e-117">Les informations sur l'erreur sont les données texte renvoyées par un composant BizTalk ou utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d023e-117">Error information is the text data returned by a BizTalk or user component.</span></span> <span data-ttu-id="d023e-118">Elles peuvent nécessiter de 100 octets à 2 Ko.</span><span class="sxs-lookup"><span data-stu-id="d023e-118">Ranges from 100 bytes to 2 KB.</span></span>|  
|<span data-ttu-id="d023e-119">Début/fin d'une forme dans une orchestration</span><span class="sxs-lookup"><span data-stu-id="d023e-119">Start/End of a Shape In an Orchestration</span></span>|<span data-ttu-id="d023e-120">120 octets chacun.</span><span class="sxs-lookup"><span data-stu-id="d023e-120">120 bytes each.</span></span>||  
|<span data-ttu-id="d023e-121">Événements d'entrée/sortie de message</span><span class="sxs-lookup"><span data-stu-id="d023e-121">Message In/Out Events</span></span>|<span data-ttu-id="d023e-122">162 octets au minimum.</span><span class="sxs-lookup"><span data-stu-id="d023e-122">Minimum 162 bytes.</span></span><br /><br /> <span data-ttu-id="d023e-123">Premier affichage du message : 202 octets + propriétés du message (si un suivi est effectué).</span><span class="sxs-lookup"><span data-stu-id="d023e-123">First time message is seen it is 202 bytes + Message Property (if tracked)</span></span><br /><br /> <span data-ttu-id="d023e-124">2 930 octets dans les cas extrêmes.</span><span class="sxs-lookup"><span data-stu-id="d023e-124">Extreme cases can reach 2930 bytes.</span></span>|<span data-ttu-id="d023e-125">Si aucun suivi des propriétés des messages n'est effectué, vous pouvez compter sur une taille moyenne de 128 octets.</span><span class="sxs-lookup"><span data-stu-id="d023e-125">You can safely assume that the average is 182 bytes if there is no message property tracking.</span></span>|  
|<span data-ttu-id="d023e-126">Taille des propriétés des messages</span><span class="sxs-lookup"><span data-stu-id="d023e-126">Message Property Size</span></span>|<span data-ttu-id="d023e-127">40 à 288 octets si DTA reconnaît les propriétés de suivi.</span><span class="sxs-lookup"><span data-stu-id="d023e-127">40 to 288 bytes if DTA recognizes this tracking property.</span></span><br /><br /> <span data-ttu-id="d023e-128">Ajoutez jusqu'à 268 octets s'il s'agit du suivi initial d'une propriété.</span><span class="sxs-lookup"><span data-stu-id="d023e-128">Add up to 268 bytes for tracking the property the first time.</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="d023e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d023e-129">See Also</span></span>  
 <span data-ttu-id="d023e-130">[Quel est le suivi des messages ?](../core/what-is-message-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="d023e-130">[What is Message Tracking?](../core/what-is-message-tracking.md) </span></span>  
 [<span data-ttu-id="d023e-131">Gestion et l’Architecture de suivi</span><span class="sxs-lookup"><span data-stu-id="d023e-131">Management and Tracking Architecture</span></span>](../core/management-and-tracking-architecture.md)