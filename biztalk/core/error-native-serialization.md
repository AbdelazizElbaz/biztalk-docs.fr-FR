---
title: "Erreur : sérialisation Native | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.nativeSerialize
ms.assetid: 48f8d460-83a0-44ce-af9b-086fcad36cb8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0d4a842a3f9a10703fb47bf21edb01ab92bd93c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---native-serialization"></a><span data-ttu-id="e8265-102">Erreur : sérialisation Native</span><span class="sxs-lookup"><span data-stu-id="e8265-102">Error - Native Serialization</span></span>
<span data-ttu-id="e8265-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="e8265-103">**Error Code**</span></span>  
  
 <span data-ttu-id="e8265-104">btm1048</span><span class="sxs-lookup"><span data-stu-id="e8265-104">btm1048</span></span>  
  
 <span data-ttu-id="e8265-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="e8265-105">**Explanation**</span></span>  
  
 <span data-ttu-id="e8265-106">Erreur de sérialisation lors de la tentative de conversion du message de l'instance de sortie XML généré par le mappage au format natif indiqué par le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="e8265-106">The indicated serialization error was encountered when attempting to convert the XML output instance message produced by the map into the native format specified by the destination schema.</span></span>  
  
 <span data-ttu-id="e8265-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="e8265-107">**User Action**</span></span>  
  
 <span data-ttu-id="e8265-108">En fonction de l'erreur indiquée, corrigez les transformations spécifiées dans le mappage ou le schéma de destination, ou bien les deux.</span><span class="sxs-lookup"><span data-stu-id="e8265-108">Based on the indicated serialization error, make the appropriate corrections to either the transformations specified in the map, or to the destination schema, or to both.</span></span> <span data-ttu-id="e8265-109">Il peut être utile ouvrir le schéma de destination dans l’Éditeur BizTalk et utiliser le **valider le schéma**, **valider l’Instance**, et **générer l’Instance** commandes disponibles lorsque vous cliquez sur un schéma dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="e8265-109">It may be helpful to open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands available when you right-click a schema in Solution Explorer.</span></span>