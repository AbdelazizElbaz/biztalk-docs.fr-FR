---
title: "Comment identifier les goulots d’étranglement dans la base de données BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6814c0df-3ce1-44f8-8e63-af6e23336c6d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8fa54379d6d314993ac33b7d6395f061e48849d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-bam-database"></a><span data-ttu-id="c7775-102">Identification des goulots d'étranglement dans la base de données de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="c7775-102">How to Identify Bottlenecks in the BAM Database</span></span>
<span data-ttu-id="c7775-103">Pour identifier les goulots d'étranglement dans la base de données de l'analyse BAM, procédez de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="c7775-103">To identify bottlenecks in the BAM database, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="c7775-104">Assurez-vous que le nombre d'instances actives n'augmente pas excessivement.</span><span class="sxs-lookup"><span data-stu-id="c7775-104">Ensure that the Active Instances count is not climbing.</span></span>  
  
2.  <span data-ttu-id="c7775-105">Vérifiez que le service de l'Agent SQL est exécuté.</span><span class="sxs-lookup"><span data-stu-id="c7775-105">Ensure that the SQL-Agent Service is running.</span></span>  
  
3.  <span data-ttu-id="c7775-106">Si l'analyse OLAP est configurée, vérifiez que la tâche BAM_AN_ job est exécutée à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="c7775-106">If OLAP Analysis is configured ensure that the BAM_AN_ job is running at periodic intervals.</span></span>  
  
4.  <span data-ttu-id="c7775-107">Vérifiez que la tâche BAM_DM_ (maintenance des données) est planifiée à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="c7775-107">Ensure that BAM_DM_ (Data Maintenance) job is scheduled to run at periodic intervals.</span></span>