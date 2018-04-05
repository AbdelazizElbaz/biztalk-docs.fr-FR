---
title: 'Erreur : génération d’Instance XML générique | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.genericGenerateXmlInstance
ms.assetid: f2b42589-fd44-45d6-86e6-c2502820beee
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c859cfc775e74ab817e66dbb8b896f51458f0301
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---generic-generate-xml-instance"></a><span data-ttu-id="3e8fd-102">Erreur : génération d’Instance XML générique</span><span class="sxs-lookup"><span data-stu-id="3e8fd-102">Error - Generic Generate XML Instance</span></span>
<span data-ttu-id="3e8fd-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="3e8fd-103">**Error Code**</span></span>  
  
 <span data-ttu-id="3e8fd-104">btm1038</span><span class="sxs-lookup"><span data-stu-id="3e8fd-104">btm1038</span></span>  
  
 <span data-ttu-id="3e8fd-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="3e8fd-105">**Explanation**</span></span>  
  
 <span data-ttu-id="3e8fd-106">Le Mappeur BizTalk n'a pas été en mesure de générer un fichier de message de l'instance XML pour le schéma source du mappage.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-106">BizTalk Mapper was not able to generate an XML instance message file for the source schema of the map.</span></span> <span data-ttu-id="3e8fd-107">Par conséquent, un problème existe au niveau du schéma source associé au mappage.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-107">This suggests that there is a problem with the source schema associated with the map.</span></span>  
  
 <span data-ttu-id="3e8fd-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="3e8fd-108">**User Action**</span></span>  
  
 <span data-ttu-id="3e8fd-109">Utilisez l'Éditeur BizTalk pour ouvrir le schéma source associé au mappage et rechercher les problèmes éventuels liés au schéma source.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-109">Use BizTalk Editor to open the source schema associated with the map and begin investigating whether there are problems with the source schema.</span></span> <span data-ttu-id="3e8fd-110">En outre, le **valider le schéma** et **générer l’Instance** commandes, disponibles lorsque vous cliquez sur un schéma dans l’Explorateur de solutions, sont utiles pour la recherche d’erreurs de schéma.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-110">Also, the **Validate Schema** and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, are useful for finding schema errors.</span></span>