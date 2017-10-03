---
title: "Fonctionne de l’exemple d’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77811152-cc8e-4090-89eb-e3a402a46e5e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ff56f2f2f88d35290ffd897d107910e206ac98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-sql-adapter-sample-works"></a><span data-ttu-id="0403d-102">Fonctionne de l’exemple d’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="0403d-102">How the SQL Adapter Sample Works</span></span>
<span data-ttu-id="0403d-103">L’exemple d’adaptateur SQL fournit un itinéraire bidirectionnelle exemple configuré avec le service de routage et d’un service de messagerie de transformation.</span><span class="sxs-lookup"><span data-stu-id="0403d-103">The SQL Adapter sample provides a sample two-way itinerary configured with the routing service and a transform messaging service.</span></span>  
  
 <span data-ttu-id="0403d-104">Le service de routage est configuré avec un programme de résolution statique, qui spécifie que le message doit être routé pour exécuter une procédure stockée SQL dans la base de données GlobalBankESB nommé InsertProduct à l’aide du fournisseur de l’adaptateur WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="0403d-104">The routing service is configured with a STATIC resolver, which specifies that the message should be routed to execute a SQL stored procedure within the GlobalBankESB database named InsertProduct using the WCF-Custom adapter provider.</span></span>  
  
 <span data-ttu-id="0403d-105">Le service de transformation spécifie un mappage qui convertit le message entrant au format accepté par la procédure stockée de InsertProduct.</span><span class="sxs-lookup"><span data-stu-id="0403d-105">The transform service specifies a map that converts the incoming message to the format accepted by the InsertProduct stored procedure.</span></span>