---
title: "Dépannage des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, troubleshooting
- troubleshooting, acknowledgements
ms.assetid: faed356e-f5fc-4920-a9f9-82eca0ad7d67
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecbbb22498cfd3d451c0b8c75c8e6f4502c2364d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-acknowledgments"></a><span data-ttu-id="6de66-102">Dépannage des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="6de66-102">Troubleshooting Acknowledgments</span></span>
<span data-ttu-id="6de66-103">Traite des problèmes liés à [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="6de66-103">Addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] acknowledgments.</span></span>  
  
## <a name="acknowledgments-are-not-generated"></a><span data-ttu-id="6de66-104">Accusés de réception ne sont pas générés.</span><span class="sxs-lookup"><span data-stu-id="6de66-104">Acknowledgments are not generated</span></span>  
 <span data-ttu-id="6de66-105">Il existe plusieurs causes possibles pour les accusés de réception (ACK) n’a été généré ou reçu.</span><span class="sxs-lookup"><span data-stu-id="6de66-105">There are several potential causes for acknowledgments (ACKs) not being generated or received.</span></span> <span data-ttu-id="6de66-106">Passez en revue la liste suivante des problèmes potentiels.</span><span class="sxs-lookup"><span data-stu-id="6de66-106">Review the following list of potential problems.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6de66-107">Symptôme</span><span class="sxs-lookup"><span data-stu-id="6de66-107">Symptom</span></span>  
 <span data-ttu-id="6de66-108">Accusés de réception ne sont pas générés lorsque vous mettez à jour les informations du tiers dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Explorer de Configuration pour générer des accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="6de66-108">Acknowledgments are not generated when you update party information in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer to generate acknowledgments.</span></span>  
  
<span data-ttu-id="6de66-109">**Cause possible** : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] met en cache et actualise les informations de configuration de tiers toutes les 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="6de66-109">**Possible cause** : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] caches and refreshes party configuration information every 15 minutes.</span></span>  
  
<span data-ttu-id="6de66-110">**Résolution** : attendez au moins 15 minutes pour le cache actualiser ou redémarrer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour les modifications prennent effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="6de66-110">**Resolution** : Wait for at least 15 minutes for the cache to refresh, or restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for changes to take effect immediately.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6de66-111">Symptôme</span><span class="sxs-lookup"><span data-stu-id="6de66-111">Symptom</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="6de66-112">ne génère pas d’accusés de réception et les erreurs d’événement apparaissent dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="6de66-112"> does not generate ACKs and event errors appear in the event log.</span></span>  
  
<span data-ttu-id="6de66-113">**Cause possible** : un accusé de réception ne peut pas être généré lorsqu’un lot dans / lots message contient un champ FHS11 vide.</span><span class="sxs-lookup"><span data-stu-id="6de66-113">**Possible cause** : An ACK cannot be generated when a batch in/batch out message contains an empty FHS11 field.</span></span>  
  
<span data-ttu-id="6de66-114">**Résolution** : Assurez-vous que vos messages ont un champ FHS11 correctement mis en forme et rempli.</span><span class="sxs-lookup"><span data-stu-id="6de66-114">**Resolution** : Ensure that your messages have a correctly formatted and populated FHS11 field.</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6de66-115">Symptôme</span><span class="sxs-lookup"><span data-stu-id="6de66-115">Symptom</span></span>  
 <span data-ttu-id="6de66-116">Votre application ne peut pas générer ou recevoir un accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="6de66-116">Your application cannot generate or receive an ACK.</span></span>  
  
<span data-ttu-id="6de66-117">**Cause possible** : empêchent des informations incorrectes dans le champ MSH3 de votre message [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] d’envoyer le message aux accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="6de66-117">**Possible cause** : Incorrect information in the MSH3 field of your message prevents [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] from sending the message ACKs.</span></span>  
  
<span data-ttu-id="6de66-118">**Résolution** : Assurez-vous que vos messages ont un champ MSH3 correctement mis en forme et rempli.</span><span class="sxs-lookup"><span data-stu-id="6de66-118">**Resolution** : Ensure that your messages have a correctly formatted and populated MSH3 field.</span></span>  
  
## <a name="acknowledgments-are-suspended-or-not-routed-to-the-send-party"></a><span data-ttu-id="6de66-119">Accusés de réception sont suspendus ou pas routés vers le tiers d’envoi</span><span class="sxs-lookup"><span data-stu-id="6de66-119">Acknowledgments are suspended or not routed to the send party</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6de66-120">Symptôme</span><span class="sxs-lookup"><span data-stu-id="6de66-120">Symptom</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="6de66-121">envoie des messages à une carte bidirectionnelle sans génération d’accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="6de66-121"> sends messages to a two-way adapter without generating acknowledgments.</span></span>  
  
<span data-ttu-id="6de66-122">**Cause possible** : l’abonnement de message n’est pas configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="6de66-122">**Possible cause** : The message subscription is not configured correctly.</span></span>  
  
<span data-ttu-id="6de66-123">**Résolution** : Assurez-vous que les abonnements aux messages soient présent et configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="6de66-123">**Resolution** : Ensure that message subscriptions are present and configured correctly.</span></span>  
  
## <a name="suspended-acknowledgments"></a><span data-ttu-id="6de66-124">Accusés de réception suspendus</span><span class="sxs-lookup"><span data-stu-id="6de66-124">Suspended acknowledgments</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6de66-125">Symptôme</span><span class="sxs-lookup"><span data-stu-id="6de66-125">Symptom</span></span>  
 <span data-ttu-id="6de66-126">Accusés de réception sont suspendus avec le message d’erreur « Délimiteur figurant dans le champ » lorsque vous avez configuré le tiers pour que l’encodage de caractères contenant les caractères de délimitation telles que @-! $.</span><span class="sxs-lookup"><span data-stu-id="6de66-126">Acknowledgments are suspended with the error message "Delimiter found in the field" when you have configured the party to have encoding characters containing delimiter characters such as @-!$.</span></span>  
  
<span data-ttu-id="6de66-127">**Cause possible** : le message contient des caractères tels que le point (.) ou un trait d’union (-).</span><span class="sxs-lookup"><span data-stu-id="6de66-127">**Possible cause** : The message contains characters such as a period (.) or a hyphen (-).</span></span> <span data-ttu-id="6de66-128">Lors de la génération les accusés de réception, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] inclut «. » et «- » pour la valeur d’horodateur.</span><span class="sxs-lookup"><span data-stu-id="6de66-128">When generating the ACKs, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] includes "." and "-" for the timestamp value.</span></span>  
  
<span data-ttu-id="6de66-129">**Résolution** : désactiver la validation dans le pipeline d’envoi afin d’éviter ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="6de66-129">**Resolution** : Disable validation in the send pipeline to avoid these errors.</span></span>  
  
## <a name="biztalk-server-generates-an-error-about-missing-ack-when-using-2-way-mllp-adapter"></a><span data-ttu-id="6de66-130">BizTalk Server génère une erreur manquants de l’accusé de réception lors de l’utilisation de l’adaptateur MLLP à 2 facteurs</span><span class="sxs-lookup"><span data-stu-id="6de66-130">BizTalk Server generates an error about missing ACK when using 2-way MLLP adapter</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="6de66-131">Symptôme</span><span class="sxs-lookup"><span data-stu-id="6de66-131">Symptom</span></span>  
 <span data-ttu-id="6de66-132">Vous obtenez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="6de66-132">You get the following or similar error in the Event Log:</span></span>  
  
 <span data-ttu-id="6de66-133">« Impossible de recevoir l’accusé de réception à partir du réseau en raison d’une erreur « Exception de HRESULT : 0xC0C01662 « »</span><span class="sxs-lookup"><span data-stu-id="6de66-133">"Unable to receive ACK from network due to error "Exception from HRESULT: 0xC0C01662""</span></span>  
  
<span data-ttu-id="6de66-134">**Cause possible** : à l’aide de 1-méthode de réception et le port d’envoi bidirectionnel 2, c’est le cas BizTalk n’a pas d’un port de réception correspondant pour renvoyer le message reçu à partir du port d’envoi bidirectionnel 2.</span><span class="sxs-lookup"><span data-stu-id="6de66-134">**Possible cause** : You are using 1-way receive and 2-way send port, so BizTalk does not have a corresponding Receive port to return the message received from the 2-way Send port.</span></span>  
  
<span data-ttu-id="6de66-135">**Résolution** : il s’agit par conception, et vous pouvez ignorer le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6de66-135">**Resolution** : This is by design, and you can ignore the error message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de66-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6de66-136">See Also</span></span>  
[<span data-ttu-id="6de66-137">Problèmes connus et dépannage dans HL7</span><span class="sxs-lookup"><span data-stu-id="6de66-137">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)