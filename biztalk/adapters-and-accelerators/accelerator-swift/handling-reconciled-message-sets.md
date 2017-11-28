---
title: "La gestion des ensembles de messages rapprochées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAA
- messages, reconciled sets
ms.assetid: 05cd0cf6-f0fd-4cbe-83c6-1ed5f2da8822
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fc9f35f9381f82df90acb92e9536bbd967901a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-reconciled-message-sets"></a><span data-ttu-id="4f357-102">Gestion des ensembles de messages de rapprochement</span><span class="sxs-lookup"><span data-stu-id="4f357-102">Handling Reconciled Message Sets</span></span>
<span data-ttu-id="4f357-103">Lorsque SAA renvoie une réponse à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] enregistre la réponse dans la MessageBox et correspond à la réponse ou les réponses au message d’origine.</span><span class="sxs-lookup"><span data-stu-id="4f357-103">When SAA returns a response to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] records the response in the MessageBox, and matches the response or responses to the original message.</span></span> <span data-ttu-id="4f357-104">Vous pouvez implémenter le comportement d’application personnalisée à l’aide de ces informations.</span><span class="sxs-lookup"><span data-stu-id="4f357-104">You can implement custom application behavior using this information.</span></span> <span data-ttu-id="4f357-105">Pour ce faire, développer des gestionnaires personnalisés qui implémentent les réactions de client spécifiques aux jeux de message rapprochées/réponse.</span><span class="sxs-lookup"><span data-stu-id="4f357-105">To do so, develop custom handlers that implement customer-specific reactions to reconciled message/response sets.</span></span> <span data-ttu-id="4f357-106">Vous pouvez créer des gestionnaires personnalisés qui effectuent les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f357-106">You can create custom handlers that do the following:</span></span>  
  
-   <span data-ttu-id="4f357-107">Traiter les messages FRR a mis en corrélation avec un message MTS21_FIN_ACKNAK-accusé de réception négatif, ce qui indique que SWIFT n’a pas reçu correctement le message à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f357-107">Process messages that FRR has correlated with a MTS21_FIN_ACKNAK negative-acknowledgment message, which indicates that SWIFT did not successfully receive the message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="4f357-108">Cela peut permettre un réparateur résoudre le message et le renvoyer à SAA et le réseau SWIFT, ce qui, après la réparation, espère sera en mesure de recevoir le message avec succès.</span><span class="sxs-lookup"><span data-stu-id="4f357-108">This can enable a repairer to fix the message and re-send it to SAA and the SWIFT network, which after the repair will hopefully be able to receive the message successfully.</span></span> <span data-ttu-id="4f357-109">Pour plus d’informations sur cette solution, consultez [FRR NAK Gestionnaire exemple](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4f357-109">For more information about this solution, see [FRR NAK Handler Sample](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).</span></span>  
  
-   <span data-ttu-id="4f357-110">Supprimer les jeux de réponse de message publiés par l’orchestration dans un dossier de fichiers avec des noms de fichier unique qui indique les relations entre les messages dans le jeu.</span><span class="sxs-lookup"><span data-stu-id="4f357-110">Drop message-response sets published by the orchestration into a file folder with unique file names indicating the relationships of the messages in the set.</span></span> <span data-ttu-id="4f357-111">Vous pouvez ensuite effectuer une logique métier sur ces messages.</span><span class="sxs-lookup"><span data-stu-id="4f357-111">You can then perform business logic on these messages.</span></span>  
  
-   <span data-ttu-id="4f357-112">Traiter les messages expiré.</span><span class="sxs-lookup"><span data-stu-id="4f357-112">Process timed-out messages.</span></span>  
  
-   <span data-ttu-id="4f357-113">Enregistrez les résultats de la transmission du message et supprime ensuite les messages réels.</span><span class="sxs-lookup"><span data-stu-id="4f357-113">Log the results of message transmission and then discard the actual messages.</span></span>