---
title: "Élément structurel d’un Message à l’ensemble de transactions EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: caea8408-c09c-4525-a9c9-18abe4432594
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d49288e9a311c9766e61fe985b9e279a8660f4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-transaction-set-message-structural-element"></a><span data-ttu-id="27a64-102">Élément structurel d’un Message à l’ensemble de transactions EDI</span><span class="sxs-lookup"><span data-stu-id="27a64-102">EDI Transaction Set-Message Structural Element</span></span>
<span data-ttu-id="27a64-103">Le document informatisé (dans le codage X12) ou le message (dans le codage EDIFACT) contient des segments qui constituent les données de message.</span><span class="sxs-lookup"><span data-stu-id="27a64-103">The transaction set (in X12 encoding) or message (in EDIFACT encoding) contains segments that make up the message data.</span></span> <span data-ttu-id="27a64-104">Le document informatisé est constitué d'un en-tête, d'un ensemble de segments de données et d'un code de fin.</span><span class="sxs-lookup"><span data-stu-id="27a64-104">The transaction set consists of a header, a collection of data segments, and a trailer.</span></span> <span data-ttu-id="27a64-105">Toutes les informations nécessaires pour traiter la transaction sont disponibles au sein du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="27a64-105">All details that are required to process the transaction are available within the transaction set.</span></span>  
  
 <span data-ttu-id="27a64-106">Un document informatisé doit commencer par un en-tête de document informatisé ST (dans X12) ou un en-tête de message UNH (dans EDIFACT).</span><span class="sxs-lookup"><span data-stu-id="27a64-106">A transaction set must start with a ST Transaction Set Header (in X12) or a UNH Message Header (in EDIFACT).</span></span> <span data-ttu-id="27a64-107">Il doit se terminer par un code de fin de document informatisé SE (dans X12) ou un code de fin de message UNT (dans EDIFACT).</span><span class="sxs-lookup"><span data-stu-id="27a64-107">It must end with a SE Transaction Set Trailer (in X12) or a UNT Message Trailer (in EDIFACT).</span></span> <span data-ttu-id="27a64-108">Le code de fin indique le nombre de segments de données qui inclut les segments d'en-tête et de code de fin.</span><span class="sxs-lookup"><span data-stu-id="27a64-108">The trailer provides a count of the data segments that includes the header and trailer segments.</span></span>  
  
 <span data-ttu-id="27a64-109">Un document informatisé peut contenir une ou plusieurs boucles, qui sont requises pour répéter un ensemble de segments associés.</span><span class="sxs-lookup"><span data-stu-id="27a64-109">A transaction set can contain one or more loops, which are required to repeat a collection of related segments.</span></span>