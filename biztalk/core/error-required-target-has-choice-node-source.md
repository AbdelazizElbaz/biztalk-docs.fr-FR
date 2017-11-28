---
title: "Erreur : cible obligatoire avec Source dans nœud choix | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.reqdTargetHasChoiceNodeSource
ms.assetid: 5b5af999-d100-4e5d-a959-c8b11d574d3b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91c9ad912b03bbb475efcc9eb8207a388400b43b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---required-target-has-choice-node-source"></a><span data-ttu-id="987cd-102">Erreur : cible obligatoire avec Source dans nœud choix</span><span class="sxs-lookup"><span data-stu-id="987cd-102">Error - Required Target Has Choice Node Source</span></span>
<span data-ttu-id="987cd-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="987cd-103">**Error Code**</span></span>  
  
 <span data-ttu-id="987cd-104">btm1029</span><span class="sxs-lookup"><span data-stu-id="987cd-104">btm1029</span></span>  
  
 <span data-ttu-id="987cd-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="987cd-105">**Explanation**</span></span>  
  
 <span data-ttu-id="987cd-106">Le nœud indiqué dans le schéma de destination est défini comme étant requis, mais est lié à un nœud dans le schéma source qui se trouve dans un **choix** nœud.</span><span class="sxs-lookup"><span data-stu-id="987cd-106">The indicated node in the destination schema is specified as required but is linked to a node in the source schema that is within a **Choice** node.</span></span> <span data-ttu-id="987cd-107">Compte tenu que le nœud indiqué dans le schéma source risque de ne pas apparaître dans le message de l'instance d'entrée, il se peut qu'aucune source à partir de laquelle créer le nœud requis dans le schéma de destination n'existe.</span><span class="sxs-lookup"><span data-stu-id="987cd-107">Because the indicated node in the source schema may not appear in an input instance message, there may not be a source from which to create the required node in the destination schema.</span></span>  
  
 <span data-ttu-id="987cd-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="987cd-108">**User Action**</span></span>  
  
 <span data-ttu-id="987cd-109">Si nécessaire, définissez le nœud indiqué dans le schéma de destination comme étant facultatif ou spécifiez une source différente pour le nœud indiqué dans le schéma de destination qui apparaîtra dans tous les messages de l'instance d'entrée valides.</span><span class="sxs-lookup"><span data-stu-id="987cd-109">As appropriate, either change the indicated node in the destination schema to optional, or provide a different source for the indicated node in the destination schema that must occur in all valid input instance messages.</span></span>