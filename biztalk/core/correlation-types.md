---
title: "Types de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, correlation types
- correlation types, correlation sets
- correlation types
- validating, correlation types
- correlation types, about correlation types
- correlation types, validating
ms.assetid: 1aa5ca5c-c37d-4091-9f5d-331a6b202d4e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3da5fad8cb4edc1d6a528f481616b4f10efb71d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlation-types"></a><span data-ttu-id="c8b56-102">Types de corrélations</span><span class="sxs-lookup"><span data-stu-id="c8b56-102">Correlation Types</span></span>
<span data-ttu-id="c8b56-103">Chaque ensemble de corrélations est basé sur un **type de corrélation**, qui est simplement une liste de propriétés.</span><span class="sxs-lookup"><span data-stu-id="c8b56-103">Each correlation set is based on a **correlation type**, which is simply a list of properties.</span></span> <span data-ttu-id="c8b56-104">Ces propriétés peuvent être relatives aux données contenues dans le message lui-même, ou au contexte qui décrit le système ou les messages non associés aux données transmises dans le message.</span><span class="sxs-lookup"><span data-stu-id="c8b56-104">These properties might be data properties, which are found in the message itself, or context properties, which describe details of the system or messages that are unrelated to the data being conveyed in the message.</span></span>  
  
 <span data-ttu-id="c8b56-105">Vous pouvez utiliser un type de corrélation dans plus d'un ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="c8b56-105">You can use a correlation type in more than one correlation set.</span></span> <span data-ttu-id="c8b56-106">Si vous avez besoin de corréler différentes valeurs de propriétés dans un type de corrélation, vous devez créer un nouvel ensemble de corrélations ; chaque ensemble de corrélations ne peut être initialisé qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="c8b56-106">If you need to correlate on different values for the properties in a correlation type, you must create a new correlation set—each correlation set can be initialized only once.</span></span>  
  
 <span data-ttu-id="c8b56-107">Vous pouvez promouvoir des propriétés dans un schéma de propriété afin de déclarer que certaines propriétés dans un message sont accessibles à votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="c8b56-107">You can promote properties in a property schema to declare that certain properties in a message are accessible to your orchestration.</span></span> <span data-ttu-id="c8b56-108">Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c8b56-108">For more information, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c8b56-109">Ne définissez pas la propriété définie par le système **BTS. CorrelationToken** qui est associé à chaque message.</span><span class="sxs-lookup"><span data-stu-id="c8b56-109">Do not set the system-defined property **BTS.CorrelationToken** that is associated with each message.</span></span> <span data-ttu-id="c8b56-110">Elle est utilisée par le moteur pour la corrélation des messages, et la modifier pourrait faire perdre des messages à votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="c8b56-110">This is used by the engine in correlating messages, and setting it could result in your orchestration losing messages.</span></span>  
  
## <a name="validating-message-correlation-on-send-actions"></a><span data-ttu-id="c8b56-111">Validation de la corrélation des messages dans les actions Envoi</span><span class="sxs-lookup"><span data-stu-id="c8b56-111">Validating Message Correlation on Send Actions</span></span>  
 <span data-ttu-id="c8b56-112">Vous pouvez valider les propriétés d'un message que vous envoyez depuis votre orchestration pour vous assurer qu'il reflète les propriétés de son ensemble de corrélations.</span><span class="sxs-lookup"><span data-stu-id="c8b56-112">You can validate the properties of a message that you send from your orchestration to ensure that it reflects the properties in its correlation set.</span></span> <span data-ttu-id="c8b56-113">Cette validation est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c8b56-113">By default, this validation is disabled.</span></span> <span data-ttu-id="c8b56-114">Pour plus d’informations sur comment l’activer, consultez [Validation d’exécution pour le moteur d’Orchestration](../core/runtime-validation-for-the-orchestration-engine.md).</span><span class="sxs-lookup"><span data-stu-id="c8b56-114">For information on how to enable it, see [Runtime Validation for the Orchestration Engine](../core/runtime-validation-for-the-orchestration-engine.md).</span></span>