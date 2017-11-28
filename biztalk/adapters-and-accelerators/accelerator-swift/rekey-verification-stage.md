---
title: "La phase de vérification de recomposition | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rekey verification
- stages, rekey verification
ms.assetid: 8a2880b6-bb25-4af5-9f51-d0b090ca38c8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9fe163a8351b0edc904f81d77a7ea341de13df6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rekey-verification-stage"></a><span data-ttu-id="0ddc2-102">Recomposition la phase de vérification</span><span class="sxs-lookup"><span data-stu-id="0ddc2-102">Rekey Verification Stage</span></span>
<span data-ttu-id="0ddc2-103">Quand une vérification recomposition étape se produit dans le flux de travail de réparation de message, une copie du message d’origine est conservée par Message réparer et New Submission et une copie exacte du message est envoyée à la boîte de réception ses recomposition vérification.</span><span class="sxs-lookup"><span data-stu-id="0ddc2-103">When a Rekey Verification stage occurs in the message repair workflow, a copy of the original message is maintained by Message Repair and New Submission and an exact copy of the message is sent to the verifier's inbox for rekey verification.</span></span> <span data-ttu-id="0ddc2-104">Dans la vérification de changement de clé, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair et New Submission efface les champs spécifiés pour rentrée manuelle.</span><span class="sxs-lookup"><span data-stu-id="0ddc2-104">In rekey verification, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair and New Submission clears specified fields for manual re-entry.</span></span>  
  
 <span data-ttu-id="0ddc2-105">Ce concept est expliqué plus en détail la [sécurité du Runtime serveur](../../adapters-and-accelerators/accelerator-swift/server-runtime-security.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="0ddc2-105">This concept is explained further in the [Server Runtime Security](../../adapters-and-accelerators/accelerator-swift/server-runtime-security.md) topic.</span></span> <span data-ttu-id="0ddc2-106">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur participe à la phase de vérification de recomposition doit manuellement entrer à nouveau dans les champs effacés, via le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran, les valeurs qui correspondent exactement à ceux du message d’origine (à partir de l’étape de la création ou de la réparation).</span><span class="sxs-lookup"><span data-stu-id="0ddc2-106">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user participating in the Rekey Verification stage must manually re-enter into the cleared fields, through the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, values that exactly match those in the original message (from either the Create or Repair stage).</span></span> <span data-ttu-id="0ddc2-107">Le vérificateur signe le message avec un certificat valide, puis envoie le message.</span><span class="sxs-lookup"><span data-stu-id="0ddc2-107">The verifier then signs the message with a valid certificate and submits the message.</span></span>  
  
 <span data-ttu-id="0ddc2-108">Si les valeurs des champs rekeyed ne correspondent pas exactement les champs de message d’origine, le Message Repair et New Submission réinitialise l’étape dans le flux de travail et renvoie le message à la boîte de réception du réparateur.</span><span class="sxs-lookup"><span data-stu-id="0ddc2-108">If the values of the rekeyed fields do not match the original message fields exactly, Message Repair and New Submission resets the stage in the workflow and sends the message back to the repairer's inbox.</span></span> <span data-ttu-id="0ddc2-109">Il valide également la signature du vérificateur qui régénérée les champs.</span><span class="sxs-lookup"><span data-stu-id="0ddc2-109">It also validates the signature of the verifier who rekeyed the fields.</span></span> <span data-ttu-id="0ddc2-110">Si le vérificateur n’est pas validé, il envoie le message à la boîte de réception de la vérification.</span><span class="sxs-lookup"><span data-stu-id="0ddc2-110">If the verifier is not validated, it sends the message back to the verifier's inbox.</span></span>