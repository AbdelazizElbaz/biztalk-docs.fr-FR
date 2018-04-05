---
title: 'Erreur : fonctoid sans lien vers le schéma de Destination de bouclage de Table | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.tableLoopingNoLinkToDestSchema
ms.assetid: cf162e6a-5c61-4adc-978b-af641db67ed2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 329e6670288f05382acf0ea014ba9ae84c4cb645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---table-looping-functoid-without-link-to-destination-schema"></a><span data-ttu-id="bd762-102">Erreur : fonctoid sans lien vers le schéma de Destination de bouclage de Table</span><span class="sxs-lookup"><span data-stu-id="bd762-102">Error - Table Looping Functoid Without Link to Destination Schema</span></span>
<span data-ttu-id="bd762-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="bd762-103">**Error Code**</span></span>  
  
 <span data-ttu-id="bd762-104">btm1077</span><span class="sxs-lookup"><span data-stu-id="bd762-104">btm1077</span></span>  
  
 <span data-ttu-id="bd762-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="bd762-105">**Explanation**</span></span>  
  
 <span data-ttu-id="bd762-106">Contrairement à la plupart des fonctoids, la **bouclage de Table** fonctoid possède plusieurs sorties.</span><span class="sxs-lookup"><span data-stu-id="bd762-106">Unlike most functoids, the **Table Looping** functoid has multiple outputs.</span></span> <span data-ttu-id="bd762-107">Toutes sauf une de ces sorties doivent être connecté en tant que le premier paramètre d’entrée pour séparer les instances de la **extracteur de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="bd762-107">All but one of these outputs must be connected as the first input parameter to separate instances of the **Table Extractor** functoid.</span></span> <span data-ttu-id="bd762-108">La sortie restante doit être connectée à un **enregistrement** nœud (avec les paramètres de périodicité appropriés) dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="bd762-108">The remaining output must be connected to a **Record** node (with appropriate recurrence settings) in the destination schema.</span></span> <span data-ttu-id="bd762-109">Cette erreur se produit lorsque ce lien de sortie une **bouclage de Table** n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="bd762-109">This error occurs when this latter output link from a **Table Looping** functoid is missing.</span></span>  
  
 <span data-ttu-id="bd762-110">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="bd762-110">**User Action**</span></span>  
  
 <span data-ttu-id="bd762-111">Faites glisser le fonctoid **bouclage de Table** enregistrement approprié **enregistrement** nœud dans le schéma de destination pour créer le lien manquant.</span><span class="sxs-lookup"><span data-stu-id="bd762-111">Drag the indicated **Table Looping** record to the appropriate **Record** node in the destination schema to create the missing link.</span></span>