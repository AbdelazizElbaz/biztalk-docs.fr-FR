---
title: "Erreur : l’Assembly externe du fonctoid script ne peut pas être appelé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.cannotInvokeExternalAssembly
ms.assetid: 30d97b05-2cbf-44a5-b219-3a5ae17fc597
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37f6df36a955f2f40da35368fd72fd2d1fcbb7b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---external-assembly-for-scripting-functoid-cannot-be-invoked"></a><span data-ttu-id="8c292-102">Erreur - Assembly externe du fonctoid script ne peut pas être appelée.</span><span class="sxs-lookup"><span data-stu-id="8c292-102">Error - External Assembly for Scripting Functoid Cannot Be Invoked</span></span>
<span data-ttu-id="8c292-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="8c292-103">**Error Code**</span></span>  
  
 <span data-ttu-id="8c292-104">btm1067</span><span class="sxs-lookup"><span data-stu-id="8c292-104">btm1067</span></span>  
  
 <span data-ttu-id="8c292-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="8c292-105">**Explanation**</span></span>  
  
 <span data-ttu-id="8c292-106">La méthode d’assembly externe qui est associée à la **script** fonctoid ne peut pas être appelé.</span><span class="sxs-lookup"><span data-stu-id="8c292-106">The external assembly method that is associated with the relevant **Scripting** functoid cannot be invoked.</span></span> <span data-ttu-id="8c292-107">Bien que cette méthode ne soit pas obligatoire pour la compilation des mappages, l'opération Test Map requiert la présence de ces assemblys externes dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="8c292-107">Although not required for map compilation, the Test Map operation requires that such external assemblies be present in the global assembly cache (GAC).</span></span> <span data-ttu-id="8c292-108">Toute opération d'exécution normale nécessite également que les assemblys externes se trouvent dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="8c292-108">Normal, run time operation also requires that external assemblies be present in the GAC.</span></span>  
  
 <span data-ttu-id="8c292-109">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="8c292-109">**User Action**</span></span>  
  
 <span data-ttu-id="8c292-110">Vérifiez que l’assembly externe correspondant au **script** fonctoid figure dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="8c292-110">Ensure that the external assembly referenced by the relevant **Scripting** functoid is in the GAC.</span></span>