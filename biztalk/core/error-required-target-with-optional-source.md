---
title: 'Erreur : cible obligatoire avec Source facultative | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.reqdTargetWithOptionalSource
ms.assetid: 3f342011-4577-4682-8324-8296615d5194
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76dd96f61766a475db6385e306bc64bc36db4fcf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---required-target-with-optional-source"></a><span data-ttu-id="f16c0-102">Erreur : cible obligatoire avec Source facultative</span><span class="sxs-lookup"><span data-stu-id="f16c0-102">Error - Required Target with Optional Source</span></span>
<span data-ttu-id="f16c0-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="f16c0-103">**Error Code**</span></span>  
  
 <span data-ttu-id="f16c0-104">btm1001</span><span class="sxs-lookup"><span data-stu-id="f16c0-104">btm1001</span></span>  
  
 <span data-ttu-id="f16c0-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="f16c0-105">**Explanation**</span></span>  
  
 <span data-ttu-id="f16c0-106">Les données du nœud requis indiqué dans le schéma de destination proviennent d'un nœud facultatif du schéma source.</span><span class="sxs-lookup"><span data-stu-id="f16c0-106">The data for the indicated required node in the destination schema comes from an optional node in the source schema.</span></span> <span data-ttu-id="f16c0-107">Par conséquent, il se peut que le mappage de certains messages de l'instance valides échoue.</span><span class="sxs-lookup"><span data-stu-id="f16c0-107">Therefore, there may be valid instance messages for which mapping will fail.</span></span>  
  
 <span data-ttu-id="f16c0-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f16c0-108">**User Action**</span></span>  
  
 <span data-ttu-id="f16c0-109">Confirmez les caractéristiques facultatives et obligatoires des nœuds source et de destination spécifiés et vérifiez que celles-ci soient compatibles.</span><span class="sxs-lookup"><span data-stu-id="f16c0-109">Confirm the optional and required characteristics of the specified source and destination nodes, respectively, and consider making these characteristics match.</span></span>