---
title: "Nombre d’étapes de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, stages
- process management solution tutorial, processing stages
ms.assetid: 74bd9f8c-99b4-4931-a096-6c54221ab2e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f61c5c348e54ea096c921cb6fc63f0db339dbf4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-processing-stages"></a><span data-ttu-id="a8610-102">Nombre d’étapes de traitement</span><span class="sxs-lookup"><span data-stu-id="a8610-102">Number of Processing Stages</span></span>
<span data-ttu-id="a8610-103">La solution décompose le processus de commande en étapes, de sorte qu'il est possible de modifier le processus (par remplacement d'étapes) sans interrompre les commandes à long terme.</span><span class="sxs-lookup"><span data-stu-id="a8610-103">The solution separates the order process into stages, so that it is possible to modify the process (by replacing stages) without disrupting long-running orders.</span></span> <span data-ttu-id="a8610-104">Pour plus d’informations sur la façon dont le processus a été divisé en étapes, consultez « Division des processus d’entreprise » dans [certains principes de conception dans la Solution de gestion des processus métier](../core/some-design-principles-in-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="a8610-104">For more information about how the process was divided into stages, see "Dividing Business Processes" in [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).</span></span>  
  
 <span data-ttu-id="a8610-105">La version actuelle de la solution contient uniquement deux étapes de traitement.</span><span class="sxs-lookup"><span data-stu-id="a8610-105">The current version of the solution contains only two processing stages.</span></span> <span data-ttu-id="a8610-106">Elle peut toutefois en contenir plus.</span><span class="sxs-lookup"><span data-stu-id="a8610-106">It could, however, contain many more.</span></span> <span data-ttu-id="a8610-107">Un nombre d'étapes plus important implique davantage de points auxquels il est possible de créer des versions du processus et de continuer à travailler sur la dernière version d'une étape de traitement.</span><span class="sxs-lookup"><span data-stu-id="a8610-107">More stages provide more points where you can version the process and continue working on the latest version of a processing stage.</span></span> <span data-ttu-id="a8610-108">Toutefois, chaque étape implique une coordination supplémentaire des messages transitant via la base de données MessageBox, ce qui accroît le délai de traitement.</span><span class="sxs-lookup"><span data-stu-id="a8610-108">However, each stage introduces the overhead of additional coordinating messages going through the MessageBox database, which increases processing time.</span></span> <span data-ttu-id="a8610-109">Vous devez analyser les performances de la solution pour déterminer si le nombre d'étapes est excessif.</span><span class="sxs-lookup"><span data-stu-id="a8610-109">You must monitor the solution's performance to determine if the number of multiple stages is excessive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8610-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8610-110">See Also</span></span>  
 <span data-ttu-id="a8610-111">[Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="a8610-111">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="a8610-112">Logique du Gestionnaire de processus</span><span class="sxs-lookup"><span data-stu-id="a8610-112">Process Manager Logic</span></span>](../core/process-manager-logic.md)