---
title: "Comment identifier les goulots d’étranglement dans la base de données BizTalkDTADb | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4499bc3-d50b-4b97-b19c-93c7bcc40483
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c7463a0288733936189d3cbbb69b59b3b202419
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-biztalkdtadb-database"></a><span data-ttu-id="a074e-102">Identification des goulots d'étranglement dans la base de données BizTalkDTADb</span><span class="sxs-lookup"><span data-stu-id="a074e-102">How to Identify Bottlenecks in the BizTalkDTADb Database</span></span>
<span data-ttu-id="a074e-103">Pour identifier les goulots d'étranglement dans la base de données BizTalkDTADb, procédez de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="a074e-103">To identify bottlenecks in the BizTalkDTADb database, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="a074e-104">Vérifiez que le service de l'Agent SQL est exécuté.</span><span class="sxs-lookup"><span data-stu-id="a074e-104">Ensure that the SQL-Agent Service is running.</span></span>  
  
2.  <span data-ttu-id="a074e-105">Vérifiez que le travail d'archivage et de purge est en cours d'exécution et s'effectue correctement.</span><span class="sxs-lookup"><span data-stu-id="a074e-105">Ensure that the Archive/Purge Job is running and completing successfully.</span></span>  
  
3.  <span data-ttu-id="a074e-106">Vérifiez qu'il existe suffisamment d'espace disque disponible pour les archives DTADb et l'augmentation de la base de données.</span><span class="sxs-lookup"><span data-stu-id="a074e-106">Verify that sufficient free disk space is available for the DTADb archives and database growth.</span></span>