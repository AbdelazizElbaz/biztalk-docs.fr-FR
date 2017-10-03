---
title: "Exemple de scénario d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAHL7, business example
- examples, business processes
- health care organizations, business example
- business processes, example
ms.assetid: 54bfbe45-4638-4488-bbd8-c642926a35d3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a74fafbac364469b1afdba5365c2af87cc4fa2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-business-scenario"></a><span data-ttu-id="d6ec7-102">Exemple de scénario commercial</span><span class="sxs-lookup"><span data-stu-id="d6ec7-102">Sample Business Scenario</span></span>
<span data-ttu-id="d6ec7-103">Soins de santé des processus sont souvent complexes et impliquent de nombreux systèmes.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-103">Health care processes are often complex and involve many systems.</span></span> <span data-ttu-id="d6ec7-104">Un exemple est le processus qui se produit lorsqu’un patient entre un hôpital et un médecin envoie le patient d’un laboratoire de test.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-104">An example is the process that occurs when a patient enters a hospital, and a physician sends the patient for a lab test.</span></span> <span data-ttu-id="d6ec7-105">Impliqués dans cette procédure sont cinq parties :</span><span class="sxs-lookup"><span data-stu-id="d6ec7-105">Involved in this procedure are five parties:</span></span>  
  
-   <span data-ttu-id="d6ec7-106">Le médecin</span><span class="sxs-lookup"><span data-stu-id="d6ec7-106">The attending physician</span></span>  
  
-   <span data-ttu-id="d6ec7-107">Le système d’enregistrement hôpital</span><span class="sxs-lookup"><span data-stu-id="d6ec7-107">The Hospital Registration System</span></span>  
  
-   <span data-ttu-id="d6ec7-108">Le système d’entrée de commande cliniques</span><span class="sxs-lookup"><span data-stu-id="d6ec7-108">The Clinical Order Entry System</span></span>  
  
-   <span data-ttu-id="d6ec7-109">Le système de laboratoire</span><span class="sxs-lookup"><span data-stu-id="d6ec7-109">The Laboratory System</span></span>  
  
-   <span data-ttu-id="d6ec7-110">Le système de facturation</span><span class="sxs-lookup"><span data-stu-id="d6ec7-110">The Billing System</span></span>  
  
 <span data-ttu-id="d6ec7-111">Les étapes suivantes peuvent se produire dans ce processus :</span><span class="sxs-lookup"><span data-stu-id="d6ec7-111">The following steps might occur in this process:</span></span>  
  
1.  <span data-ttu-id="d6ec7-112">La participation doctor inscrit le patient.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-112">The attending doctor registers the patient.</span></span>  
  
    1.  <span data-ttu-id="d6ec7-113">Un ADT ^ O04 message d’inscription est diffusée par le système d’enregistrement hôpital.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-113">An ADT^O04 registration message is broadcast by the Hospital Registration System.</span></span>  
  
    2.  <span data-ttu-id="d6ec7-114">Le ADT ^ O04 message est reçu par tous les services qui s’abonnent au message, y compris le système d’entrée de commande cliniques et le système de laboratoire.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-114">The ADT^O04 message is received by all departments that subscribe to the message, including the Clinical Order Entry System and the Laboratory System.</span></span>  
  
2.  <span data-ttu-id="d6ec7-115">Le médecin commandes une étude de diagnostic à partir de l’installation de laboratoire.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-115">The doctor orders a diagnostic study from the laboratory facility.</span></span>  
  
    1.  <span data-ttu-id="d6ec7-116">Un ORM ^ O01 message d’ordre est envoyé à partir du système d’entrée de commande cliniques, après la validation de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-116">An ORM^O01 order message is sent from the Clinical Order Entry System, after validation of business rules.</span></span>  
  
    2.  <span data-ttu-id="d6ec7-117">Le ORM ^ O01 message est reçu par le système de laboratoire.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-117">The ORM^O01 message is received by the Laboratory System.</span></span>  
  
3.  <span data-ttu-id="d6ec7-118">Le laboratoire reçoit la commande et renvoie une confirmation.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-118">The laboratory receives the order, and returns a confirmation.</span></span>  
  
    1.  <span data-ttu-id="d6ec7-119">Un ORR ^ message de confirmation de la commande O02 est envoyé par le système de laboratoire, indiquant que la commande peut être exécutée.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-119">An ORR^O02 order-confirmation message is sent by the Laboratory System, indicating that the order can be executed.</span></span>  
  
    2.  <span data-ttu-id="d6ec7-120">L’ORR ^ O02 message est reçu par le système d’entrée de commande cliniques.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-120">The ORR^O02 message is received by the Clinical Order Entry System.</span></span>  
  
4.  <span data-ttu-id="d6ec7-121">À la fin des tests, le laboratoire envoie les résultats pour le médecin et d’autres services.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-121">On completion of the tests, the laboratory sends the results to the doctor and other departments.</span></span>  
  
    1.  <span data-ttu-id="d6ec7-122">Un ORU ^ message des résultats des tests de R01 est envoyé à partir du système de laboratoire.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-122">An ORU^R01 test-results message is sent from the Laboratory System.</span></span>  
  
    2.  <span data-ttu-id="d6ec7-123">L’ORU ^ R01 message est reçu par le système d’entrée de commande cliniques et le système de facturation.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-123">The ORU^R01 message is received by the Clinical Order Entry System and the Billing System.</span></span>  
  
    3.  <span data-ttu-id="d6ec7-124">Le moteur de l’Interface envoie un message électronique au médecin, qui reçoit les résultats de laboratoire sur son PDA sans fil.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-124">The Interface Engine sends out an e-mail message to the doctor, who receives the lab results on his wireless PDA.</span></span>  
  
## <a name="the-btahl7-solution"></a><span data-ttu-id="d6ec7-125">La Solution BTAHL7</span><span class="sxs-lookup"><span data-stu-id="d6ec7-125">The BTAHL7 Solution</span></span>  
 <span data-ttu-id="d6ec7-126">L’exemple de scénario d’entreprise présentée ci-dessus est un exemple d’un système de soins de santé besoins d’intégration.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-126">The sample business scenario outlined above is an example of a health care system that needs integration.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="d6ec7-127">[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) fournit une solution pour ce scénario qui propose les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6ec7-127">[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) provides a solution for this scenario that features the following functionality:</span></span>  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d6ec7-128">s’intègre tous les systèmes impliqués dans une disposition « hub and spoke ».</span><span class="sxs-lookup"><span data-stu-id="d6ec7-128"> integrates all of the systems involved in a hub-and-spoke arrangement.</span></span> <span data-ttu-id="d6ec7-129">Chaque système communique directement avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6ec7-129">Each system communicates directly with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d6ec7-130">Ils n’ont pas à communiquer directement entre eux.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-130">They do not have to communicate directly to each other.</span></span>  
  
2.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="d6ec7-131">gère les messages encodés HL7 en mode natif.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-131"> handles HL7-encoded messages natively.</span></span> <span data-ttu-id="d6ec7-132">Aucun codage personnalisé n’est requise.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-132">No custom coding is required.</span></span>  
  
3.  <span data-ttu-id="d6ec7-133">Le ADT ^ O04 message d’inscription est diffusé à tous les systèmes qui y abonner.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-133">The ADT^O04 registration message is broadcast to all systems that subscribe to it.</span></span> <span data-ttu-id="d6ec7-134">Le modèle de messagerie éditeur-abonné pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] garantit la souplesse de configuration et gestion de la liste des systèmes d’abonnement au message.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-134">The publisher-subscriber messaging model for [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides flexibility in setting up and maintaining the list of systems subscribing to the message.</span></span> <span data-ttu-id="d6ec7-135">Vous pouvez ajouter des systèmes ou les supprimer à partir de la liste des abonnements sans affecter le reste du système.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-135">You can add systems to or delete them from the subscription list without affecting the rest of the system.</span></span>  
  
4.  <span data-ttu-id="d6ec7-136">La règle d’entreprise permet de valider le ORM ^ message de commande O01 permettre être modifiée de manière dynamique sans affecter le reste du système.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-136">The business rule used to validate the ORM^O01 order message can be changed dynamically without affecting the rest of the system.</span></span>  
  
5.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="d6ec7-137">peut être configuré pour générer automatiquement le ORR ^ message de confirmation de commande (ACK) O02.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-137"> can be configured to automatically generate the ORR^O02 order-confirmation (ACK) message.</span></span>  
  
6.  <span data-ttu-id="d6ec7-138">Si nécessaire, vous pouvez traiter par lot des messages avec d’autres utilisateurs pour l’envoi et les traiter dès réception à partir d’un lot.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-138">If necessary, you can batch any of the messages with others for sending, and process them on receipt from within the batch.</span></span>  
  
7.  <span data-ttu-id="d6ec7-139">Vous pouvez valider tous les messages dans le moteur et par rapport à la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]des schémas X 2 publié par l’organisation HL7.</span><span class="sxs-lookup"><span data-stu-id="d6ec7-139">You can validate all messages in the engine and against the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2X schemas published by the HL7 organization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ec7-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6ec7-140">See Also</span></span>  
 [<span data-ttu-id="d6ec7-141">Comment BizTalk Server résout les besoins de l’entreprise</span><span class="sxs-lookup"><span data-stu-id="d6ec7-141">How BizTalk Server Solves the Business Need</span></span>](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)