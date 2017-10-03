---
title: "Modes de Message d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message modes, ACK messages
- messages, acknowledgements
- acknowledgements, message modes
- ACK message modes
ms.assetid: ab4a9470-dab2-46d4-8d0a-54dc12f2fa90
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 122f0851005c7d8abba6c1739ae86a1d65d89625
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ack-message-modes"></a><span data-ttu-id="e31cb-102">Modes d’accusé de réception du Message</span><span class="sxs-lookup"><span data-stu-id="e31cb-102">ACK Message Modes</span></span>
<span data-ttu-id="e31cb-103">Pour les messages d’accusé de réception (ACK), [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) détermine le mode d’accusé de réception et les valeurs à utiliser pour remplir les champs MSH15 et MSH16 de l’accusé de réception que vous souhaitez générer.</span><span class="sxs-lookup"><span data-stu-id="e31cb-103">For acknowledgment (ACK) messages, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) determines the acknowledgment mode and values to use for populating MSH15 and MSH16 fields of the ACK you want to generate.</span></span> <span data-ttu-id="e31cb-104">Ces valeurs sont présentes dans la configuration de la gestion des partenaires commerciaux (GPC).</span><span class="sxs-lookup"><span data-stu-id="e31cb-104">These values are present in the Trading Partner Management (TPM) configuration.</span></span> <span data-ttu-id="e31cb-105">Les valeurs suivantes sont possibles pour le mode de l’accusé de réception :</span><span class="sxs-lookup"><span data-stu-id="e31cb-105">The following values are possible for ACK mode:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e31cb-106">Dans la liste suivante, la spécification de HL7 mandate éléments 1 à 3 et qu’ils contiennent des valeurs MSH15 et MSH16.</span><span class="sxs-lookup"><span data-stu-id="e31cb-106">In the following list, the HL7 specification mandates items 1 through 3 and that they contain MSH15 and MSH16 values.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="e31cb-107">définit l’élément 4 pour indiquer qu’un accusé de réception ne doit pas être généré.</span><span class="sxs-lookup"><span data-stu-id="e31cb-107"> defines item 4 to signify that an acknowledgment should not be generated.</span></span>  
  
1.  <span data-ttu-id="e31cb-108">Original - il s’agit d’un accusé de réception après la validation de l’en-tête et corps.</span><span class="sxs-lookup"><span data-stu-id="e31cb-108">Original - One ACK sent after validating the header and body.</span></span> <span data-ttu-id="e31cb-109">Ce mode implique la validation du schéma.</span><span class="sxs-lookup"><span data-stu-id="e31cb-109">This mode involves schema validation.</span></span>  
  
2.  <span data-ttu-id="e31cb-110">Étendu - deux messages d’accusé de réception envoyés :</span><span class="sxs-lookup"><span data-stu-id="e31cb-110">Enhanced - Two ACK messages sent:</span></span>  
  
    -   <span data-ttu-id="e31cb-111">Accepter l’accusé de réception – le système de réception envoie ce type d’accusé de réception après la validation de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="e31cb-111">Accept ACK – The receiving system sends this type of ACK after validation of the header.</span></span> <span data-ttu-id="e31cb-112">Cet accusé de réception signale à l’application d’origine que le message est validé dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="e31cb-112">This ACK signals to the initiating application that the message is committed to the database.</span></span>  
  
    -   <span data-ttu-id="e31cb-113">Système de réception de l’accusé de réception-l’application envoie ce type d’accusé de réception après la validation de message complet, y compris l’en-tête et le corps.</span><span class="sxs-lookup"><span data-stu-id="e31cb-113">Application ACK- The receiving system sends this type of ACK after complete message validation, including the header and the body.</span></span>  
  
3.  <span data-ttu-id="e31cb-114">-Deux accusés de réception des messages différés envoyés.</span><span class="sxs-lookup"><span data-stu-id="e31cb-114">Deferred - Two ACK messages sent.</span></span>  
  
    -   <span data-ttu-id="e31cb-115">Mode d’origine : Le système de réception envoie ce type d’accusé de réception après la validation de l’en-tête et corps.</span><span class="sxs-lookup"><span data-stu-id="e31cb-115">Original Mode: The receiving system sends this type of ACK after validation of the header and body.</span></span> <span data-ttu-id="e31cb-116">Ce mode implique la validation du schéma.</span><span class="sxs-lookup"><span data-stu-id="e31cb-116">This mode involves schema validation.</span></span>  
  
    -   <span data-ttu-id="e31cb-117">Mode différé : L’application métier-accuse réception du message après son traitement.</span><span class="sxs-lookup"><span data-stu-id="e31cb-117">Deferred Mode: The line-of-business application acknowledges the message after processing it.</span></span> <span data-ttu-id="e31cb-118">L’application transmet le message différé à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], qui la traite comme un message autonome, puis les remet à la destination.</span><span class="sxs-lookup"><span data-stu-id="e31cb-118">The application delivers the deferred message to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], which process it as a stand-alone message and delivers it to the destination.</span></span>  
  
4.  <span data-ttu-id="e31cb-119">Static - un en cas de réussite ou d’échec de l’accusé de réception envoyé.</span><span class="sxs-lookup"><span data-stu-id="e31cb-119">Static - An on success or on failure ACK sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31cb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e31cb-120">See Also</span></span>  
 <span data-ttu-id="e31cb-121">[Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="e31cb-121">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="e31cb-122">[Guide de programmation](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span><span class="sxs-lookup"><span data-stu-id="e31cb-122">[Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span></span>  
 <span data-ttu-id="e31cb-123">[Modèle de processus de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md) </span><span class="sxs-lookup"><span data-stu-id="e31cb-123">[ACK Process Model](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md) </span></span>  
 [<span data-ttu-id="e31cb-124">Accusés de réception statiques</span><span class="sxs-lookup"><span data-stu-id="e31cb-124">Static Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/static-acknowledgments.md)