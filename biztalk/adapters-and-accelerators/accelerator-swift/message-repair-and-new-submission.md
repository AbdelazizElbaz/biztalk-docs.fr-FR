---
title: Message Repair et New Submission | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages
- resubmitting messages
- errors, messages
- messages, errors
- messages, resubmitting
ms.assetid: 5bc6bfa2-8210-4dd3-89bb-5455e294ca92
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bc15351848fe68d6ef54c31fc6d58c075bb1c58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission"></a><span data-ttu-id="f0380-102">Message Repair et New Submission</span><span class="sxs-lookup"><span data-stu-id="f0380-102">Message Repair and New Submission</span></span>
<span data-ttu-id="f0380-103">La fonctionnalité réparer du Message et de la nouvelle soumission de [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit un moyen de vous permet de réparer les messages de ce dernier et MX dont la validation échouent.</span><span class="sxs-lookup"><span data-stu-id="f0380-103">The Message Repair and New Submission feature of [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides a way for you to repair MT and MX messages that fail validation.</span></span> <span data-ttu-id="f0380-104">Le site SharePoint de MRSR (déployé par l’utilisateur), vous pouvez voir comment le message d’échec de la validation.</span><span class="sxs-lookup"><span data-stu-id="f0380-104">Using the MRSR SharePoint site (deployed by user), you can see how the message failed validation.</span></span> <span data-ttu-id="f0380-105">À partir du site MRSR, vous pouvez ouvrir le message dans un formulaire InfoPath qui vous permet d’identifier l’erreur, réparez le message et les soumettre de retraitement.</span><span class="sxs-lookup"><span data-stu-id="f0380-105">From MRSR site, you can open the message in an InfoPath form that enables you to identify the error, repair the message, and submit it for reprocessing.</span></span>  
  
 <span data-ttu-id="f0380-106">Message Repair et New Submission prend en charge la réparation de message basée sur le rôle.</span><span class="sxs-lookup"><span data-stu-id="f0380-106">Message Repair and New Submission supports role-based message repair.</span></span> <span data-ttu-id="f0380-107">Un flux de travail de réparation complète inclut la réparation, la vérification et approbation.</span><span class="sxs-lookup"><span data-stu-id="f0380-107">A full repair workflow includes repair, verification, and approval.</span></span> <span data-ttu-id="f0380-108">Réparation d’un flux de travail est associé à un service qui définit les rôles (ou les étapes) du flux de travail et configure un utilisateur A4SWIFT pour chaque rôle.</span><span class="sxs-lookup"><span data-stu-id="f0380-108">A repair workflow is associated with a department that defines the roles (or stages) of the workflow and configures an A4SWIFT user for each role.</span></span> <span data-ttu-id="f0380-109">Chaque rôle de réparation dispose d’une vue de site MRSR distincte adaptée au rôle.</span><span class="sxs-lookup"><span data-stu-id="f0380-109">Each repair role has a separate MRSR site view tailored to the role.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f0380-110">effectue une validation et chaque utilisateur qui A4SWIFT effectue un signe de rôle du message, à l’aide d’un certificat, pour garantir un processus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="f0380-110"> performs validation, and each A4SWIFT user performing a role signs the message, using a certificate, to ensure a secure process.</span></span>  
  
 <span data-ttu-id="f0380-111">En plus de la réparation de message, A4SWIFT vous permet d’envoyer un message à l’aide d’une version améliorée [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire.</span><span class="sxs-lookup"><span data-stu-id="f0380-111">In addition to message repair, A4SWIFT enables you to submit a new message using an enhanced [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form.</span></span> <span data-ttu-id="f0380-112">Un quatrième utilisateur A4SWIFT, un créateur exécute cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f0380-112">A fourth A4SWIFT user, a creator, performs this function.</span></span> <span data-ttu-id="f0380-113">Le processus effectue la validation et peut impliquer la réparation, la vérification et approbation rôles afin d’envoi réussi.</span><span class="sxs-lookup"><span data-stu-id="f0380-113">The process also performs validation, and can involve repair, verification, and approval roles to ensure successful submission.</span></span> <span data-ttu-id="f0380-114">A4SWIFT gère la nouvelle soumission de message via un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forment la même manière qu’elle gère un message réparé.</span><span class="sxs-lookup"><span data-stu-id="f0380-114">A4SWIFT handles new message submission through an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form the same way that it handles a repaired message.</span></span>  
  
 <span data-ttu-id="f0380-115">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="f0380-115">This section contains:</span></span>  
  
-   [<span data-ttu-id="f0380-116">Processus de réparation de message</span><span class="sxs-lookup"><span data-stu-id="f0380-116">Message Repair Process</span></span>](../../adapters-and-accelerators/accelerator-swift/message-repair-process.md)  
  
-   [<span data-ttu-id="f0380-117">Création de services et les rôles pour Message Repair et New Submission</span><span class="sxs-lookup"><span data-stu-id="f0380-117">Creating Departments and Roles for Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="f0380-118">À l’aide d’un formulaire InfoPath à réparer un Message ou envoyez un nouveau Message</span><span class="sxs-lookup"><span data-stu-id="f0380-118">Using an InfoPath Form to Repair a Message or Submit a New Message</span></span>](../../adapters-and-accelerators/accelerator-swift/using-an-infopath-form-to-repair-a-message-or-submit-a-new-message.md)  
  
-   [<span data-ttu-id="f0380-119">Traitement spécial dans le Message Repair et New Submission</span><span class="sxs-lookup"><span data-stu-id="f0380-119">Special Processing in Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="f0380-120">Réparer les Messages non analysées</span><span class="sxs-lookup"><span data-stu-id="f0380-120">Repairing Unparsed Messages</span></span>](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)  
  
-   [<span data-ttu-id="f0380-121">Nouveau traitement de Service d’envoi et de la réparation de message</span><span class="sxs-lookup"><span data-stu-id="f0380-121">Message Repair and New Submission Service Processing</span></span>](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-service-processing.md)