---
title: 'Erreur : conflit d’options de lien | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.linkOptionConflict
ms.assetid: dbad5c00-500b-4931-a54c-8b311fbfda53
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31f5829f971e524a5e4d2c0f443174c6511a6314
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---link-option-conflict"></a><span data-ttu-id="d6913-102">Erreur : conflit d’options de lien</span><span class="sxs-lookup"><span data-stu-id="d6913-102">Error - Link Option Conflict</span></span>
<span data-ttu-id="d6913-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="d6913-103">**Error Code**</span></span>  
  
 <span data-ttu-id="d6913-104">btm1022</span><span class="sxs-lookup"><span data-stu-id="d6913-104">btm1022</span></span>  
  
 <span data-ttu-id="d6913-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="d6913-105">**Explanation**</span></span>  
  
 <span data-ttu-id="d6913-106">Les nœuds indiqués dans le schéma de destination comportent des directives de compilateur contradictoires sur leurs liaisons entrantes.</span><span class="sxs-lookup"><span data-stu-id="d6913-106">The indicated nodes in the destination schema have conflicting compiler directives specified for their incoming links.</span></span>  
  
 <span data-ttu-id="d6913-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="d6913-107">**User Action**</span></span>  
  
 <span data-ttu-id="d6913-108">Sélectionnez une seule ou les deux liaisons associées aux nœuds indiqués dans le schéma de destination, puis, dans la fenêtre Propriétés de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], modifiez les directives de compilateur de sorte qu'elles soient compatibles.</span><span class="sxs-lookup"><span data-stu-id="d6913-108">Select one or both of the links leading to the indicated nodes in the destination schema and then in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, change their compiler directives so that they are compatible.</span></span>