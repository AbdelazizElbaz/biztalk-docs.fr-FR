---
title: Didacticiel interrogative | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interrogative tutorial
- interrogative tutorial, about the tutorial
- tutorials, interrogative tutorial
ms.assetid: 93988429-5544-4920-821f-54f0a67bda72
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b35a5bc8ba7574df7499fef5d63a100993c4201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interrogative-tutorial"></a><span data-ttu-id="91ea9-102">Didacticiel interrogative</span><span class="sxs-lookup"><span data-stu-id="91ea9-102">Interrogative Tutorial</span></span>
<span data-ttu-id="91ea9-103">Ce didacticiel contient des procédures détaillées qui décrivent la façon dont vous utilisez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour faciliter le processus d’entreprise dans un scénario de requête/réponse.</span><span class="sxs-lookup"><span data-stu-id="91ea9-103">This tutorial contains detailed steps that describe how you use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to facilitate business processes in a Query/Response scenario.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91ea9-104">Pour utiliser ce didacticiel, vous devez installer les outils de test MLLP.</span><span class="sxs-lookup"><span data-stu-id="91ea9-104">To use this tutorial, you must install the MLLP test tools.</span></span> <span data-ttu-id="91ea9-105">Ces outils ne sont pas installés par une installation classique de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="91ea9-105">These tools are not installed by a Typical installation of BTAHL7.</span></span> <span data-ttu-id="91ea9-106">Vous devez exécuter une installation personnalisée et sélectionnez **outil de Test MLLP** à partir du dossier de l’adaptateur et **Test Instances** à partir du dossier d’artefacts.</span><span class="sxs-lookup"><span data-stu-id="91ea9-106">You must run a Custom installation and select **MLLP Test Tool** from the Adapter folder and **Test Instances** from the Artifacts folder.</span></span> <span data-ttu-id="91ea9-107">Si les outils de test sont installés, votre système doit contenir le dossier \< *lecteur*: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\MLLP utilitaires.</span><span class="sxs-lookup"><span data-stu-id="91ea9-107">If the test tools are installed, your system will contain the folder \<*drive*:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\MLLP Utilities.</span></span> <span data-ttu-id="91ea9-108">Consultez [installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span><span class="sxs-lookup"><span data-stu-id="91ea9-108">See [install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
## <a name="interrogative-scenario"></a><span data-ttu-id="91ea9-109">Scénario interrogative</span><span class="sxs-lookup"><span data-stu-id="91ea9-109">Interrogative Scenario</span></span>  
 <span data-ttu-id="91ea9-110">Ce didacticiel utilise le scénario de Interrogative ou de requête/réponse.</span><span class="sxs-lookup"><span data-stu-id="91ea9-110">This tutorial uses the Query/Response or Interrogative scenario.</span></span> <span data-ttu-id="91ea9-111">Dans ce scénario, le flux d’activité est similaire à celui indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="91ea9-111">In this scenario, the flow of business is similar to that shown in the following figure.</span></span> <span data-ttu-id="91ea9-112">La liste numérotée, la figure suivante décrit le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="91ea9-112">The numbered list following the figure describes the workflow.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-intertutorial.gif "hl7_intertutorial")  
  
1.  <span data-ttu-id="91ea9-113">Le flux de travail commence lorsqu’un système d’admission décharger et de transfert (ADT) envoie une requête à un système d’informations.</span><span class="sxs-lookup"><span data-stu-id="91ea9-113">The workflow begins when an Admissions Discharge and Transfer (ADT) system sends a query to the Hospital Information System.</span></span> <span data-ttu-id="91ea9-114">Le message HL7 utilise la «**req ^ Q01**« schéma.</span><span class="sxs-lookup"><span data-stu-id="91ea9-114">The HL7 message uses the "**QRY^Q01**" schema.</span></span> <span data-ttu-id="91ea9-115">Dans le didacticiel, l’utilitaire MllpSend simule le ADT port de réception envoie le message de requête au système informations hôpital via le ADT dans le moteur d’intégration BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="91ea9-115">In the tutorial, the MllpSend utility simulates the ADT system sending the query message to the Hospital Information System through the ADT receive port in the BTAHL7 Integration Engine.</span></span>  
  
2.  <span data-ttu-id="91ea9-116">Le moteur d’intégration BTAHL7 reçoit le message de requête à partir du système ADT et le valide.</span><span class="sxs-lookup"><span data-stu-id="91ea9-116">The BTAHL7 Integration Engine receives the query message from the ADT system and validates it.</span></span> <span data-ttu-id="91ea9-117">Ensuite, le pipeline de BTAHL7 renvoie un accusé de réception à ADT.</span><span class="sxs-lookup"><span data-stu-id="91ea9-117">Then, the BTAHL7 pipeline sends an acknowledgment back to ADT.</span></span>  
  
3.  <span data-ttu-id="91ea9-118">Le moteur d’Interface BTAHL7 traite le message, et ensuite les itinéraires du message de requête à la destination de HIS de tiers via le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="91ea9-118">The BTAHL7 Interface Engine processes the message, and then routes the query message to the HIS destination party through the HIS send port.</span></span>  
  
4.  <span data-ttu-id="91ea9-119">Après avoir reçu l’accusé de réception de la requête d’origine, le système ADT attend une réponse.</span><span class="sxs-lookup"><span data-stu-id="91ea9-119">After receiving the acknowledgment from the original query, the ADT system waits for a response.</span></span> <span data-ttu-id="91ea9-120">L’hôpital informations système renvoient un message de réponse via le port de réception.</span><span class="sxs-lookup"><span data-stu-id="91ea9-120">The Hospital Information System sends a response message back through the HIS receive port.</span></span> <span data-ttu-id="91ea9-121">Pour ce didacticiel, l’utilitaire MllpSend simule un système d’informations du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="91ea9-121">For this tutorial, the MllpSend utility simulates the Hospital Information System sending the response message.</span></span>  
  
5.  <span data-ttu-id="91ea9-122">Le moteur d’Interface BTAHL7 traite le message de réponse et puis l’achemine au tiers de destination via le port d’envoi ADT.</span><span class="sxs-lookup"><span data-stu-id="91ea9-122">The BTAHL7 Interface Engine processes the response message and then routes it to the destination party through the ADT send port.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91ea9-123">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="91ea9-123">In this section</span></span>  
  
-   [<span data-ttu-id="91ea9-124">Préparation à l’utilisation du didacticiel</span><span class="sxs-lookup"><span data-stu-id="91ea9-124">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)  
  
-   [<span data-ttu-id="91ea9-125">Étape 1 : Créer et déployer des en-tête commun et schémas d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="91ea9-125">Step 1: Create and Deploy Common Header and Acknowledgment Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md)  
  
-   [<span data-ttu-id="91ea9-126">Étape 2 : Créer des schémas courants pour V2.4</span><span class="sxs-lookup"><span data-stu-id="91ea9-126">Step 2: Create Common Schemas for V2.4</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md)  
  
-   [<span data-ttu-id="91ea9-127">Étape 3 : Créer et déployer un projet déclencheur d’événement (Message)</span><span class="sxs-lookup"><span data-stu-id="91ea9-127">Step 3: Create and Deploy a Trigger Event (Message) Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-deploy-a-trigger-event-message-project-hl7-main.md)  
  
-   [<span data-ttu-id="91ea9-128">Étape 4 : Créer le Port de réception pour accepter les Messages de requête ADT</span><span class="sxs-lookup"><span data-stu-id="91ea9-128">Step 4: Create the Receive Port for Accepting ADT Query Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md)  
  
-   [<span data-ttu-id="91ea9-129">Étape 5 : Créer le Port de réception pour l’acceptation de ses Messages</span><span class="sxs-lookup"><span data-stu-id="91ea9-129">Step 5: Create the Receive Port for Accepting HIS Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)  
  
-   [<span data-ttu-id="91ea9-130">Étape 6 : Créer un Port d’envoi pour remettre des Messages de requête</span><span class="sxs-lookup"><span data-stu-id="91ea9-130">Step 6: Create a Send Port to Deliver Query Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-query-messages.md)  
  
-   [<span data-ttu-id="91ea9-131">Étape 7 : Créer un Port d’envoi pour remettre des Messages de réponse</span><span class="sxs-lookup"><span data-stu-id="91ea9-131">Step 7: Create a Send Port to Deliver Response Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md)  
  
-   [<span data-ttu-id="91ea9-132">Étape 8 : Configurer les informations de tiers</span><span class="sxs-lookup"><span data-stu-id="91ea9-132">Step 8: Configure Party Information</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md)  
  
-   [<span data-ttu-id="91ea9-133">Étape 9 : Redémarrer BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="91ea9-133">Step 9: Restart BizTalk Server</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server-hl7-main.md)  
  
-   [<span data-ttu-id="91ea9-134">Étape 10 : Vérifier que le scénario Interrogative</span><span class="sxs-lookup"><span data-stu-id="91ea9-134">Step 10: Verify the Interrogative Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-verify-the-interrogative-scenario.md)  

## <a name="next-step"></a><span data-ttu-id="91ea9-135">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="91ea9-135">Next step</span></span>  
 [<span data-ttu-id="91ea9-136">Préparation à l’utilisation du didacticiel</span><span class="sxs-lookup"><span data-stu-id="91ea9-136">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial-hl7-main.md)
  
## <a name="see-also"></a><span data-ttu-id="91ea9-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91ea9-137">See Also</span></span>  
[<span data-ttu-id="91ea9-138">Prise en main BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="91ea9-138">Get started with the BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)