---
title: "Modèle de processus de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, process flow
- ACK process model
ms.assetid: 3c6a5eef-57ef-41f7-9782-e1cbc4dd78e1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 846ecf4d8eee4eca0e8a75a3444a1478b7db5910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ack-process-model"></a><span data-ttu-id="a81aa-102">Modèle de processus de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="a81aa-102">ACK Process Model</span></span>
<span data-ttu-id="a81aa-103">La séquence d’étapes suivante décrit le modèle de processus d’accusé de réception (ACK) :</span><span class="sxs-lookup"><span data-stu-id="a81aa-103">The following sequence of steps describes the acknowledgment (ACK) process model:</span></span>  
  
1.  <span data-ttu-id="a81aa-104">Lorsque le personnel d’admission journaliser des informations de patients admission dans le système admission (ADT), le système génère un événement déclencheur.</span><span class="sxs-lookup"><span data-stu-id="a81aa-104">When the admissions personnel log patient admission information into the Admissions System (ADT), the system generates a trigger event.</span></span>  
  
2.  <span data-ttu-id="a81aa-105">Le système ADT génère un message encodé HL7 de l’inscription du Patient (ADT ^ A04) puis les remet à BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="a81aa-105">The ADT system generates an HL7-encoded Patient Registration message (ADT^A04) and delivers it to BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span></span>  
  
3.  <span data-ttu-id="a81aa-106">Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] système applique un wrapper MLLP sur le ADT ^ A04 message et l’achemine vers le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface.</span><span class="sxs-lookup"><span data-stu-id="a81aa-106">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] system applies an MLLP wrapper on the ADT^A04 message and routes it to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
    -   <span data-ttu-id="a81aa-107">Demande d’accusé de réception de « Mode d’origine » est préconfiguré</span><span class="sxs-lookup"><span data-stu-id="a81aa-107">Requirement of 'Original Mode' Acknowledgment is preconfigured</span></span>  
  
    -   <span data-ttu-id="a81aa-108">MSH 15 et 16 ont des valeurs null</span><span class="sxs-lookup"><span data-stu-id="a81aa-108">MSH 15 and 16 have null values</span></span>  
  
4.  <span data-ttu-id="a81aa-109">Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface valide le message et en cas de validation réussie, il génère le message d’accusé de réception avec l’état **MSA01 = AA**.</span><span class="sxs-lookup"><span data-stu-id="a81aa-109">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine validates the message and if successful validation occurs, it generates the ACK message with the status **MSA01 = AA**.</span></span>  
  
5.  <span data-ttu-id="a81aa-110">Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface moteur transforme le ADT ^ message A04 en plaçant avec les wrappers MLLP et de leur routage vers le système informations Lab (LIS).</span><span class="sxs-lookup"><span data-stu-id="a81aa-110">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine transforms the ADT^A04 message by enclosing it with MLLP wrappers and routing it to the Lab Information System (LIS).</span></span>  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a81aa-111">préconfigure amélioré le Mode d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="a81aa-111"> preconfigures 'Enhanced Mode' Acknowledgment</span></span>  
  
    -   <span data-ttu-id="a81aa-112">MSH 15 et 16 = AL</span><span class="sxs-lookup"><span data-stu-id="a81aa-112">MSH 15 and 16 = AL</span></span>  
  
6.  <span data-ttu-id="a81aa-113">La couche d’Interface LIS valide de l’en-tête à valider le message et de générer un accusé de réception accepter avec l’état **MSA1 = autorité de certification**.</span><span class="sxs-lookup"><span data-stu-id="a81aa-113">The LIS Interface Layer validates the header by committing the message and generating an ACCEPT ACK with the status **MSA1 = CA**.</span></span> <span data-ttu-id="a81aa-114">La couche d’interface achemine le message avec le wrapper MLLP le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface.</span><span class="sxs-lookup"><span data-stu-id="a81aa-114">The interface layer routes the message with the MLLP wrapper to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
7.  <span data-ttu-id="a81aa-115">La couche d’Interface LIS valide l’intégralité du message et génère un accusé de réception d’APPLICATION avec l’état **MSA1 = AA**.</span><span class="sxs-lookup"><span data-stu-id="a81aa-115">The LIS Interface Layer validates the entire message and generates an APPLICATION ACK with the status **MSA1 = AA**.</span></span> <span data-ttu-id="a81aa-116">La couche d’interface achemine le message avec le wrapper MLLP le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface.</span><span class="sxs-lookup"><span data-stu-id="a81aa-116">The interface layer routes the message with the MLLP wrapper to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a81aa-117">préconfigure « l’accusé de réception requis' accuse réception de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="a81aa-117"> preconfigures 'ACK Required' acknowledging the acknowledgment</span></span>  
  
    -   <span data-ttu-id="a81aa-118">MSH 15 = AL, ce qui indique que le système de réception doit accepter l’accusé de réception avec un Message d’acceptation de validation</span><span class="sxs-lookup"><span data-stu-id="a81aa-118">MSH 15 = AL, which indicates that the receiving system must acknowledge the ACK with a Commit Accept Message</span></span>  
  
8.  <span data-ttu-id="a81aa-119">La couche d’Interface de LIS remet le message à la couche Application conformément à la spécification de format.</span><span class="sxs-lookup"><span data-stu-id="a81aa-119">The LIS Interface layer delivers the message to the Application Layer in accordance with the format requirement.</span></span>  
  
9. <span data-ttu-id="a81aa-120">Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] moteur d’Interface valide de l’accusé de réception reçu à partir de la couche d’Interface LIS (à l’étape 7 ci-dessus) et qu’il répond avec un accusé de réception à la couche d’Interface LIS avec l’état **MSA1 = autorité de certification**.</span><span class="sxs-lookup"><span data-stu-id="a81aa-120">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine validates the ACK received from the LIS Interface Layer (in step 7 above) and responds with an ACK back to the LIS Interface Layer with the status **MSA1= CA**.</span></span>  
  
10. <span data-ttu-id="a81aa-121">Un utilisateur du système LIS passe en revue les informations sur les patients.</span><span class="sxs-lookup"><span data-stu-id="a81aa-121">A user of the LIS System reviews the Patient information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a81aa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a81aa-122">See Also</span></span>  
 <span data-ttu-id="a81aa-123">[Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="a81aa-123">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 [<span data-ttu-id="a81aa-124">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="a81aa-124">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)