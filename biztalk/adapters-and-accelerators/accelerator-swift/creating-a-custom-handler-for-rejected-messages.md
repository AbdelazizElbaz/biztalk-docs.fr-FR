---
title: "Création d’un gestionnaire personnalisé pour les Messages rejetés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom handlers
- Message Repair and New Submission, rejected messages
- Message Repair and New Submission, custom handlers
ms.assetid: 28d74504-6c62-427a-b75d-456fbe43ec3a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7c2f678bde1d438f352b749eed76b5aa0ab5d7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-handler-for-rejected-messages"></a><span data-ttu-id="3bcb8-102">Création d’un gestionnaire personnalisé pour les Messages rejetés</span><span class="sxs-lookup"><span data-stu-id="3bcb8-102">Creating a Custom Handler for Rejected Messages</span></span>
<span data-ttu-id="3bcb8-103">Si vous le rejetez un message à l’étape de vérification ou de l’approbation [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] retourne le message à la première étape définie pour le flux de travail (dans ce cas est toujours réparer, même si Create est la première étape dans le flux de travail).</span><span class="sxs-lookup"><span data-stu-id="3bcb8-103">If you reject a message in the verification or approval stage, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] returns the message to the first stage defined for the workflow (which in this case is always repair, even if Create is the first stage in the workflow).</span></span> <span data-ttu-id="3bcb8-104">Toutefois, si la première étape du flux de travail rejette le message, l’orchestration de réparation publie le message dans la MessageBox avec des propriétés promues indiquant que l’orchestration MrsrRepair a refusé le message.</span><span class="sxs-lookup"><span data-stu-id="3bcb8-104">However, if the first stage of the workflow rejects the message, the repair orchestration publishes the message to the MessageBox with promoted properties indicating that the MrsrRepair orchestration rejected the message.</span></span> <span data-ttu-id="3bcb8-105">Pour gérer ces messages, vous pouvez créer un gestionnaire personnalisé (orchestration) qui s’abonne à ces propriétés promues et traite les messages en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="3bcb8-105">To handle these messages, you can create a custom handler (orchestration) that subscribes to these promoted properties and processes the messages as required.</span></span>  
  
 <span data-ttu-id="3bcb8-106">Échec d’un message dans l’orchestration MrsrRepair pour plusieurs raisons.</span><span class="sxs-lookup"><span data-stu-id="3bcb8-106">A message can fail in the MrsrRepair orchestration for multiple reasons.</span></span> <span data-ttu-id="3bcb8-107">Dans ce cas, l’orchestration promeut les propriétés dans le tableau suivant et affecte ces propriétés, la valeur ou l’une des valeurs, indiquées dans la colonne de droite de la table.</span><span class="sxs-lookup"><span data-stu-id="3bcb8-107">When it does, the orchestration promotes the properties in the following table, and assigns these properties the value, or one of the values, shown in the right column of the table.</span></span>  
  
|<span data-ttu-id="3bcb8-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="3bcb8-108">Property</span></span>|<span data-ttu-id="3bcb8-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="3bcb8-109">Values</span></span>|  
|--------------|------------|  
|<span data-ttu-id="3bcb8-110">BIZTALK SERVER. Opération</span><span class="sxs-lookup"><span data-stu-id="3bcb8-110">BTS.Operation</span></span>|<span data-ttu-id="3bcb8-111">A4SWIFT_MRSRFailed</span><span class="sxs-lookup"><span data-stu-id="3bcb8-111">A4SWIFT_MRSRFailed</span></span>|  
|<span data-ttu-id="3bcb8-112">A4SWIFT_MRSRFailedReason</span><span class="sxs-lookup"><span data-stu-id="3bcb8-112">A4SWIFT_MRSRFailedReason</span></span>|<span data-ttu-id="3bcb8-113">Délai d'expiration</span><span class="sxs-lookup"><span data-stu-id="3bcb8-113">Timeout</span></span><br /><br /> <span data-ttu-id="3bcb8-114">Rejeté (signifie que le message a été rejeté par la première étape)</span><span class="sxs-lookup"><span data-stu-id="3bcb8-114">Rejected (means the message has been rejected from the first stage)</span></span><br /><br /> <span data-ttu-id="3bcb8-115">CantRepairInInfoPath</span><span class="sxs-lookup"><span data-stu-id="3bcb8-115">CantRepairInInfoPath</span></span>|  
|<span data-ttu-id="3bcb8-116">A4SWIFT_MRSRLastStage</span><span class="sxs-lookup"><span data-stu-id="3bcb8-116">A4SWIFT_MRSRLastStage</span></span>|<span data-ttu-id="3bcb8-117">\<nom de la dernière étape (rôle) le message a été dans permises ></span><span class="sxs-lookup"><span data-stu-id="3bcb8-117">\<name of last stage (role) that the message was in before failing></span></span>|  
|<span data-ttu-id="3bcb8-118">A4SWIFT_MRSRDepartment</span><span class="sxs-lookup"><span data-stu-id="3bcb8-118">A4SWIFT_MRSRDepartment</span></span>|<span data-ttu-id="3bcb8-119">\<nom du service ></span><span class="sxs-lookup"><span data-stu-id="3bcb8-119">\<name of department></span></span>|