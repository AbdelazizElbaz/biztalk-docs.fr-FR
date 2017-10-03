---
title: "Erreur : analyse Native générique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.genericNativeParsing
ms.assetid: a28a4c0f-b69b-448b-b305-3b06b4f061e4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 383c3198af290552715d51812f22c82760cb445f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---generic-native-parsing"></a><span data-ttu-id="e95bb-102">Erreur : analyse Native générique</span><span class="sxs-lookup"><span data-stu-id="e95bb-102">Error - Generic Native Parsing</span></span>
<span data-ttu-id="e95bb-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="e95bb-103">**Error Code**</span></span>  
  
 <span data-ttu-id="e95bb-104">btm1042</span><span class="sxs-lookup"><span data-stu-id="e95bb-104">btm1042</span></span>  
  
 <span data-ttu-id="e95bb-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="e95bb-105">**Explanation**</span></span>  
  
 <span data-ttu-id="e95bb-106">Le fichier de message de l'instance d'entrée natif associé à l'opération Test Map n'a pas été analysé. Une erreur d'analyse générique irrécupérable a été renvoyée.</span><span class="sxs-lookup"><span data-stu-id="e95bb-106">The native input instance message file specified for the Test Map operation could not be parsed, and generated a generic fatal parsing error.</span></span>  
  
 <span data-ttu-id="e95bb-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="e95bb-107">**User Action**</span></span>  
  
 <span data-ttu-id="e95bb-108">Si nécessaire, corrigez le schéma source associé au mappage ou le message de l'instance d'entrée natif du fichier indiqué, ou bien les deux.</span><span class="sxs-lookup"><span data-stu-id="e95bb-108">As appropriate, correct either the source schema associated with the map or the native input instance message in the specified file, or both.</span></span> <span data-ttu-id="e95bb-109">Pour identifier le problème, pensez à utiliser l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e95bb-109">Consider working within BizTalk Editor to isolate the problem.</span></span> <span data-ttu-id="e95bb-110">Le **valider le schéma** et **générer l’Instance** commandes, disponibles lorsque vous cliquez sur un schéma dans l’Explorateur de solutions, sont utiles pour la recherche d’erreurs de schéma.</span><span class="sxs-lookup"><span data-stu-id="e95bb-110">The **Validate Schema** and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, are useful for finding schema errors.</span></span>