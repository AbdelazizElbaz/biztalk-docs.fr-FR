---
title: Tutorial1 de bout en bout | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: btahl7.endtoendtutorial
helpviewer_keywords:
- end-to-end tutorial, about the tutorial
- end-to-end tutorial
- tutorials, end-to-end tutorial
ms.assetid: 90625edc-70a0-42c9-a2fb-8eeb5465d766
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90dc31ac286f8ce1e38d9a511eb319828d8ae939
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="end-to-end-tutorial"></a><span data-ttu-id="51e15-102">Didacticiel de bout en bout</span><span class="sxs-lookup"><span data-stu-id="51e15-102">End-to-End Tutorial</span></span>
<span data-ttu-id="51e15-103">Ce didacticiel contient des procédures détaillées qui décrivent la façon dont vous utilisez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour faciliter le processus d’entreprise dans un scénario d’abonné et le serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="51e15-103">This tutorial contains detailed steps that describe how you use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to facilitate business processes in a subscriber and publisher scenario.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51e15-104">Pour utiliser ce didacticiel, vous devez installer les outils de test lors de l’installation BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="51e15-104">To use this tutorial, you must install the test tools when installing BTAHL7.</span></span> <span data-ttu-id="51e15-105">Si vous avez effectué une installation par défaut pour installer BTAHL7, vous devez exécuter une installation personnalisée et installer les outils de test pour ce didacticiel fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="51e15-105">If you performed a typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly.</span></span> <span data-ttu-id="51e15-106">À la **le programme d’installation personnalisé** écran de l’installation personnalisée de BTAHL7, sélectionnez **outil de Test MLLP** à partir de la **carte** dossier, puis sélectionnez **Test Instances** à partir de la **artefacts** dossier.</span><span class="sxs-lookup"><span data-stu-id="51e15-106">At the **Custom Setup** screen of the BTAHL7 custom installation, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="51e15-107">Pour plus d’informations, consultez [installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span><span class="sxs-lookup"><span data-stu-id="51e15-107">For more information, see [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
## <a name="declarative-scenario"></a><span data-ttu-id="51e15-108">Scénario déclaratif</span><span class="sxs-lookup"><span data-stu-id="51e15-108">Declarative Scenario</span></span>  
 <span data-ttu-id="51e15-109">Ce didacticiel utilise le scénario déclaratif ou publication/abonnement.</span><span class="sxs-lookup"><span data-stu-id="51e15-109">This tutorial uses the publish/subscribe or declarative scenario.</span></span> <span data-ttu-id="51e15-110">Dans le scénario déclaratif, le flux d’activité est similaire à celui indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="51e15-110">In the declarative scenario, the flow of business is similar to that shown in the following figure.</span></span> <span data-ttu-id="51e15-111">La liste numérotée, la figure suivante décrit le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="51e15-111">The numbered list following the figure describes the workflow.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-e2e-wkflw.gif "hl7_e2e_wkflw")  
<span data-ttu-id="51e15-112">Figure montrant le flux d’entreprise pour le scénario déclaratif</span><span class="sxs-lookup"><span data-stu-id="51e15-112">Figure showing the flow of business for the declarative scenario</span></span>  
  
1.  <span data-ttu-id="51e15-113">Le flux de travail commence lorsque le serveur de publication, par exemple, une décharge d’admission et système de transfert, envoie un message à des abonnés spécifiques.</span><span class="sxs-lookup"><span data-stu-id="51e15-113">The workflow begins when the publisher, for example, an Admissions Discharge and Transfer system, sends a message to specific subscribers.</span></span> <span data-ttu-id="51e15-114">Le serveur de publication dans le flux de travail est « Tutorial_ADTSystem », et le message est appelé «**ADT ^ A103**. »</span><span class="sxs-lookup"><span data-stu-id="51e15-114">The publisher in the workflow is "Tutorial_ADTSystem", and the message is called "**ADT^A103**."</span></span>  
  
2.  <span data-ttu-id="51e15-115">Le message est routé vers le moteur d’Interface de BTAHL7, qui à son tour reçoit, traite, valide, remet en forme, puis achemine le message vers les abonnés.</span><span class="sxs-lookup"><span data-stu-id="51e15-115">The message is routed to the BTAHL7 Interface Engine, which in turn receives, processes, validates, reformats, and then routes the message to subscribers.</span></span>  
  
3.  <span data-ttu-id="51e15-116">Les abonnés dans ce scénario sont un système d’Information hôpital (Tutorial_HISystem) et un système pharmacie (Tutorial_RXSystem).</span><span class="sxs-lookup"><span data-stu-id="51e15-116">The subscribers in this scenario are a Hospital Information System (Tutorial_HISystem) and a Pharmacy System (Tutorial_RXSystem).</span></span> <span data-ttu-id="51e15-117">Ce scénario utilise les types d’adaptateur de fichier et MLLP.</span><span class="sxs-lookup"><span data-stu-id="51e15-117">This scenario uses both File and MLLP adapter types.</span></span> <span data-ttu-id="51e15-118">Le serveur de publication n'a pas besoin de connaître les abonnés et BTAHL7 correctement envoie un accusé de réception au serveur de publication après le traitement du message.</span><span class="sxs-lookup"><span data-stu-id="51e15-118">The publisher does not need to be aware of the subscribers and BTAHL7 appropriately sends an acknowledgment to the publisher after processing the message.</span></span>  
  
4.  <span data-ttu-id="51e15-119">Le serveur de publication envoie le ADT ^ message A03 via un adaptateur MLLP unidirectionnel (Tutorial_1WayReceivePort).</span><span class="sxs-lookup"><span data-stu-id="51e15-119">The publisher sends the ADT^A03 message through a one-way MLLP adapter (Tutorial_1WayReceivePort).</span></span>  
  
5.  <span data-ttu-id="51e15-120">La destination de ce message est le moteur d’Interface BTAHL7, par conséquent, le message entrant contient un message source (MSH3 = Tutorial_ADTSystem) et un message de destination (MSH5 = BTAHL7InterfaceEngine).</span><span class="sxs-lookup"><span data-stu-id="51e15-120">The destination of this message is the BTAHL7 Interface Engine, so the incoming message contains a source message (MSH3 = Tutorial_ADTSystem) and a destination message (MSH5 = BTAHL7InterfaceEngine).</span></span>  
  
6.  <span data-ttu-id="51e15-121">BTAHL7 génère un accusé de réception (ACK) après avoir correctement vérifié le message, puis envoie l’accusé de réception à le Tutorial_ADTSystem via l’adaptateur File.</span><span class="sxs-lookup"><span data-stu-id="51e15-121">BTAHL7 generates an acknowledgment (ACK) after appropriately validating the message, and then sends the acknowledgment to the Tutorial_ADTSystem through the File adapter.</span></span>  
  
7.  <span data-ttu-id="51e15-122">Le système Tutorial_HISystem et le système Tutorial_RXSystem s’abonner au message ADT reçu par le moteur d’Interface BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="51e15-122">The Tutorial_HISystem system and the Tutorial_RXSystem system subscribe to the ADT message received by the BTAHL7 Interface Engine.</span></span>  
  
8.  <span data-ttu-id="51e15-123">La transformation se produit lorsque vous spécifiez des valeurs pour les champs à l’aide de la **MSH carte** onglet dans l’Explorateur de Configuration BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="51e15-123">The transformation occurs when you specify values for the respective fields by using the **MSH Map** tab in BTAHL7 Configuration Explorer.</span></span>  
  
     <span data-ttu-id="51e15-124">Par exemple, la partie Tutorial_RXSystem a MSH3 = BTHL7 spécifié dans le **MSH carte** onglet. Par conséquent, le message reçu par l’abonné aura « BTAHL7 » comme valeur pour le champ MSH3.</span><span class="sxs-lookup"><span data-stu-id="51e15-124">For example, the party Tutorial_RXSystem has MSH3=BTHL7 specified in the **MSH Map** tab. Therefore, the message received by the subscriber will have "BTAHL7" as the value for the MSH3 field.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51e15-125">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="51e15-125">In this section</span></span>  
  
-   [<span data-ttu-id="51e15-126">Test de votre Installation</span><span class="sxs-lookup"><span data-stu-id="51e15-126">Testing Your Installation</span></span>](../../adapters-and-accelerators/accelerator-hl7/testing-your-installation.md)  
  
-   [<span data-ttu-id="51e15-127">Préparation à l’utilisation du didacticiel</span><span class="sxs-lookup"><span data-stu-id="51e15-127">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)  
  
-   [<span data-ttu-id="51e15-128">Étape 1 : Créer et déployer des schémas d’en-tête et d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="51e15-128">Step 1: Create and Deploy Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="51e15-129">Étape 2 : Créer des schémas courants pour v2.3.1</span><span class="sxs-lookup"><span data-stu-id="51e15-129">Step 2: Create Common Schemas for v2.3.1</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md)  
  
-   [<span data-ttu-id="51e15-130">Étape 3 : Créer et déployer un projet déclencheur d’événement (Message)</span><span class="sxs-lookup"><span data-stu-id="51e15-130">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project.md)  
  
-   [<span data-ttu-id="51e15-131">Étape 4 : Créer le Port de réception pour l’acceptation de ADT ^ A03 des Messages à partir de systèmes ADT à l’aide de l’adaptateur MLLP</span><span class="sxs-lookup"><span data-stu-id="51e15-131">Step 4: Create the Receive Port for Accepting ADT^A03 Messages from ADT Systems Using the MLLP Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-receive-port-to-accept-adt^a03-messages-from-adt-using-mllp.md)  
  
-   [<span data-ttu-id="51e15-132">Étape 5 : Créer un Port d’envoi pour remettre les accusés de réception au système ADT à l’aide de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="51e15-132">Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)  
  
-   [<span data-ttu-id="51e15-133">Étape 6 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 dans le système de réception à l’aide de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="51e15-133">Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)  
  
-   [<span data-ttu-id="51e15-134">Étape 7 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP</span><span class="sxs-lookup"><span data-stu-id="51e15-134">Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)  
  
-   [<span data-ttu-id="51e15-135">Étape 8 : Configurer les informations de tiers</span><span class="sxs-lookup"><span data-stu-id="51e15-135">Step 8: Configure Party Information</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)  
  
-   [<span data-ttu-id="51e15-136">Étape 9 : Redémarrer BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="51e15-136">Step 9: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md)  
  
-   [<span data-ttu-id="51e15-137">Étape 10 : Vérifier que le scénario de bout en bout</span><span class="sxs-lookup"><span data-stu-id="51e15-137">Step 10: Verify the End-to-End Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-end-to-end-scenario.md)

## <a name="see-also"></a><span data-ttu-id="51e15-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51e15-138">See also</span></span>
[<span data-ttu-id="51e15-139">Prise en main BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="51e15-139">Get started with the BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)