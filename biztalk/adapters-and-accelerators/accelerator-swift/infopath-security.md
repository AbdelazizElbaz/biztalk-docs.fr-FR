---
title: "InfoPath sécurité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, InfoPath forms
- InfoPath forms, security
ms.assetid: 6ed7b5cc-9801-45a5-8fdb-e5d56dd36435
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ec5478af7c404840bf1c5c80be5520e405bd26a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="infopath-security"></a><span data-ttu-id="7fd17-102">Sécurité d’InfoPath</span><span class="sxs-lookup"><span data-stu-id="7fd17-102">InfoPath Security</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="7fd17-103">[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 utilise des Signatures XML pour vous permettre de signer numériquement un formulaire à l’aide d’un certificat numérique.</span><span class="sxs-lookup"><span data-stu-id="7fd17-103"> [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 uses XML Signatures to let you digitally sign a form using a digital certificate.</span></span> <span data-ttu-id="7fd17-104">Les Signatures XML définit une norme pour les signatures numériques basé sur XML que vous utilisez pour vous aider à sécuriser les données contenues dans les documents XML.</span><span class="sxs-lookup"><span data-stu-id="7fd17-104">XML Signatures defines a standard for XML-based digital signatures that you use to help secure the data contained in XML documents.</span></span> <span data-ttu-id="7fd17-105">Les Signatures XML est une norme régie par le World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="7fd17-105">XML Signatures is a standard governed by the World Wide Web Consortium (W3C).</span></span>  
  
 <span data-ttu-id="7fd17-106">Une signature numérique est un cachet électronique et sécurisé de l’authentification d’une macro ou un document.</span><span class="sxs-lookup"><span data-stu-id="7fd17-106">A digital signature is an electronic, encryption-based, secure stamp of authentication on a macro or document.</span></span> <span data-ttu-id="7fd17-107">Lors de la signature numérique d’un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire, l’instance XML par le formulaire est « estampillée » avec une signature numérique (signature public résumé des données de clé et signé est écrite dans un nœud dédié dans le code XML).</span><span class="sxs-lookup"><span data-stu-id="7fd17-107">When digitally signing an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, the XML instance entered through the form is "stamped" with a digital signature (the signature public key and signed data digest is written to a dedicated node in the XML).</span></span> <span data-ttu-id="7fd17-108">Cette signature confirme que le document XML du signataire et qu’il n’a pas été modifié.</span><span class="sxs-lookup"><span data-stu-id="7fd17-108">This signature confirms that the XML document originated from the signer and has not been altered.</span></span> [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]<span data-ttu-id="7fd17-109">Fournit la signature vérifiable, non répudiée, signature partielle, cosigning et contresignant prise en charge améliorée de signature numérique.</span><span class="sxs-lookup"><span data-stu-id="7fd17-109"> provides verifiable, non-repudiable signing, partial signing, cosigning and countersigning through enhanced digital signature support.</span></span>  
  
 <span data-ttu-id="7fd17-110">Les solutions SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms générés avec l’utilitaire FormGenerator fournie par A4SWIFT utilisent la méthode countersigning de la signature numérique pour vous permettre de signatures de countersigners pour être empilées les unes sur les autres.</span><span class="sxs-lookup"><span data-stu-id="7fd17-110">The SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms generated with the FormGenerator utility provided by A4SWIFT use the countersigning method of digital signing to let signatures of countersigners to be stacked on top of each other.</span></span> <span data-ttu-id="7fd17-111">Cette pile signature countersigning modélise le processus humains de création ou modification d’un message SWIFT, incluant le message révisé et approuvé par un ou plusieurs réviseurs et les approbateurs et enfin envoyer ce message uniquement une fois toutes les étapes dans un flux de travail ont approuvé.</span><span class="sxs-lookup"><span data-stu-id="7fd17-111">This countersigning signature stack models the human-oriented process of creating or editing a SWIFT message, having the message reviewed and approved by one or more reviewers and approvers, and finally submitting that message only after all stages in a workflow have signed off.</span></span>  
  
 <span data-ttu-id="7fd17-112">Réparateurs, les réviseurs ou les approbateurs signer le message qu’ils approuvent ou rejettent.</span><span class="sxs-lookup"><span data-stu-id="7fd17-112">Repairers, reviewers, or approvers sign the message regardless of whether they approve or reject it.</span></span> <span data-ttu-id="7fd17-113">La signature signifie l’authenticité de la réponse et ne signifie pas nécessairement une décision « acceptée ».</span><span class="sxs-lookup"><span data-stu-id="7fd17-113">The signature signifies authenticity of the response and does not necessarily signify an "accepted" decision.</span></span>  
  
 <span data-ttu-id="7fd17-114">Lorsque la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire est envoyé, il vérifie les messages de validité et que l’utilisateur de la signature du formulaire est le bon rôle.</span><span class="sxs-lookup"><span data-stu-id="7fd17-114">When the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form is submitted, it checks messages for validity and that the user signing the form is in the correct role.</span></span>  
  
 <span data-ttu-id="7fd17-115">Si le message est rejeté à tout moment dans un flux de travail (en plus de réparation), le message est envoyé à la phase de réparation.</span><span class="sxs-lookup"><span data-stu-id="7fd17-115">If the message is rejected at any stage in a workflow (besides repair), the message is sent back to the repair stage.</span></span> <span data-ttu-id="7fd17-116">Si le message est rejeté au stade réparateur ou créateur, Message Repair et New Submission envoie le message à l’instance d’orchestration Message Repair et New Submission avec propriétés spécifiques de marquer le message comme étant rejeté.</span><span class="sxs-lookup"><span data-stu-id="7fd17-116">If the message is rejected at the repairer or creator stage, Message Repair and New Submission sends the message back to the Message Repair and New Submission orchestration instance with specific properties marking the message as rejected.</span></span>  
  
 <span data-ttu-id="7fd17-117">Cette section décrit la façon dont Message Repair et New Submission gère les signatures numériques basées sur les fonctionnalités définies pour un rôle.</span><span class="sxs-lookup"><span data-stu-id="7fd17-117">This section describes how Message Repair and New Submission handles the digital signatures based on the capabilities defined for a role.</span></span> <span data-ttu-id="7fd17-118">La combinaison de rôle et la fonction est appelée une « phase » dans le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="7fd17-118">The role and capability combination is called a "stage" in the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fd17-119">Le rôle « créer » est limité à un créateur d’unique entre tous les services.</span><span class="sxs-lookup"><span data-stu-id="7fd17-119">The "create" role is limited to a single creator across all departments.</span></span>  
  
 <span data-ttu-id="7fd17-120">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="7fd17-120">This section contains:</span></span>  
  
-   [<span data-ttu-id="7fd17-121">Création et la réparation des étapes</span><span class="sxs-lookup"><span data-stu-id="7fd17-121">Create and Repair Stages</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-and-repairing-stages.md)  
  
-   [<span data-ttu-id="7fd17-122">Recomposition la phase de vérification</span><span class="sxs-lookup"><span data-stu-id="7fd17-122">Rekey Verification Stage</span></span>](../../adapters-and-accelerators/accelerator-swift/rekey-verification-stage.md)  
  
-   [<span data-ttu-id="7fd17-123">Étape d’approbation</span><span class="sxs-lookup"><span data-stu-id="7fd17-123">Approval Stage</span></span>](../../adapters-and-accelerators/accelerator-swift/approval-stage.md)  
  
-   [<span data-ttu-id="7fd17-124">Distribuer des certificats numériques</span><span class="sxs-lookup"><span data-stu-id="7fd17-124">Distributing Digital Certificates</span></span>](../../adapters-and-accelerators/accelerator-swift/distributing-digital-certificates.md)