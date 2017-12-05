---
title: Test de votre Installation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing installation
- installing, testing installation
ms.assetid: db27a75c-db7f-46ff-b8ef-2624ff18dcc8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7fc94930ba5ff0851114e36d728ee7f3ffb73ab
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="testing-your-installation"></a><span data-ttu-id="fcd1f-102">Test de votre Installation</span><span class="sxs-lookup"><span data-stu-id="fcd1f-102">Testing Your Installation</span></span>
<span data-ttu-id="fcd1f-103">Vous pouvez configurer votre [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation en exécutant manuellement le didacticiel de bout en bout ou en exécutant le programme de didacticiel de bout en bout de test.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-103">You can set up your [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation for testing either by manually running through the end-to-end tutorial or by executing the end-to-end tutorial program.</span></span> <span data-ttu-id="fcd1f-104">Pour tester le programme, cliquez sur le **lancer le didacticiel** bouton pendant l’installation ou exécutez EndToEndTutorial.exe dans C:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\ Dossier didacticiel de bout en bout (après l’exécution de configuration et installation).</span><span class="sxs-lookup"><span data-stu-id="fcd1f-104">To exercise the program, either click the **Launch Tutorial** button during setup or execute EndToEndTutorial.exe in the C:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial folder (after running installation and configuration).</span></span> <span data-ttu-id="fcd1f-105">Une de ces actions automatisées effectue les mêmes étapes que vous devez effectuer manuellement en exécutant le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-105">Either of these automated actions will perform the same setup steps that you would manually perform by running through the tutorial.</span></span> <span data-ttu-id="fcd1f-106">Le programme de didacticiel de bout en bout effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="fcd1f-106">The end-to-end tutorial program does the following:</span></span>  
  
-   <span data-ttu-id="fcd1f-107">Déploie des schémas MSH et l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fcd1f-107">Deploys MSH and ACK schemas</span></span>  
  
-   <span data-ttu-id="fcd1f-108">Déploie des schémas courants Version 2.3.1</span><span class="sxs-lookup"><span data-stu-id="fcd1f-108">Deploys Version 2.3.1 common schemas</span></span>  
  
-   <span data-ttu-id="fcd1f-109">Déploie les schémas ADT</span><span class="sxs-lookup"><span data-stu-id="fcd1f-109">Deploys ADT schemas</span></span>  
  
-   <span data-ttu-id="fcd1f-110">Crée le Tutorial_1WayReceive port de réception</span><span class="sxs-lookup"><span data-stu-id="fcd1f-110">Creates the Tutorial_1WayReceive receive port</span></span>  
  
-   <span data-ttu-id="fcd1f-111">Crée le Tutorial_MLLPReceive emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="fcd1f-111">Creates the Tutorial_MLLPReceive receive location</span></span>  
  
-   <span data-ttu-id="fcd1f-112">Crée le Tutorial_BTAHL7PickUp port de réception</span><span class="sxs-lookup"><span data-stu-id="fcd1f-112">Creates the Tutorial_BTAHL7PickUp receive port</span></span>  
  
-   <span data-ttu-id="fcd1f-113">Crée le Tutorial_FileReceiveLoc emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="fcd1f-113">Creates the Tutorial_FileReceiveLoc receive location</span></span>  
  
-   <span data-ttu-id="fcd1f-114">Crée le port d’envoi Tutorial_sendAck_ADT</span><span class="sxs-lookup"><span data-stu-id="fcd1f-114">Creates the Tutorial_sendAck_ADT send port</span></span>  
  
-   <span data-ttu-id="fcd1f-115">Crée le port d’envoi Tutorial_sendMsg_RX</span><span class="sxs-lookup"><span data-stu-id="fcd1f-115">Creates the Tutorial_sendMsg_RX send port</span></span>  
  
-   <span data-ttu-id="fcd1f-116">Crée le port d’envoi Tutorial_BTAHL7Drop</span><span class="sxs-lookup"><span data-stu-id="fcd1f-116">Creates the Tutorial_BTAHL7Drop send port</span></span>  
  
-   <span data-ttu-id="fcd1f-117">Crée le port d’envoi Tutorial_MLLPSend</span><span class="sxs-lookup"><span data-stu-id="fcd1f-117">Creates the Tutorial_MLLPSend send port</span></span>  
  
-   <span data-ttu-id="fcd1f-118">Crée le tiers Tutorial_ADTSystem</span><span class="sxs-lookup"><span data-stu-id="fcd1f-118">Creates the Tutorial_ADTSystem party</span></span>  
  
-   <span data-ttu-id="fcd1f-119">Crée le tiers Tutorial_RXSystem</span><span class="sxs-lookup"><span data-stu-id="fcd1f-119">Creates the Tutorial_RXSystem party</span></span>  
  
-   <span data-ttu-id="fcd1f-120">Crée le tiers Tutorial_HISystem</span><span class="sxs-lookup"><span data-stu-id="fcd1f-120">Creates the Tutorial_HISystem party</span></span>  
  
-   <span data-ttu-id="fcd1f-121">Redémarre le Service BizTalk</span><span class="sxs-lookup"><span data-stu-id="fcd1f-121">Restarts the BizTalk Service</span></span>  
  
 <span data-ttu-id="fcd1f-122">Si vous avez exécuté le programme de didacticiel de bout en bout, vous pouvez supprimer une instance de test pour HL7 dans un dossier prédéfini.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-122">If you have executed the end-to-end tutorial program, you can drop a test instance for HL7 in a pre-defined folder.</span></span> <span data-ttu-id="fcd1f-123">Le pipeline de réception associé au dossier récupère le message et le traite.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-123">The receive pipeline associated with the folder picks up the message and processes it.</span></span> <span data-ttu-id="fcd1f-124">Selon les filtres, un pipeline d’envoi achemine le document dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-124">Based on filters, a send pipeline routes the document to the destination folder.</span></span> <span data-ttu-id="fcd1f-125">Cette simple « aller-retour » exerce les blocs de construction de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) du moteur et confirme que votre installation.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-125">This simple "round-trip" exercises the basic building blocks of the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) engine and confirms your installation.</span></span>  
  
### <a name="to-test-your-installation"></a><span data-ttu-id="fcd1f-126">Pour tester votre installation</span><span class="sxs-lookup"><span data-stu-id="fcd1f-126">To test your installation</span></span>  
  
1.  <span data-ttu-id="fcd1f-127">À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator pour le dossier de didacticiel HL7\SDK\End en bout.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-127">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial folder.</span></span>  
  
2.  <span data-ttu-id="fcd1f-128">Cliquez sur le **TutorialSampleInstance.txt** de fichiers, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-128">Right-click the **TutorialSampleInstance.txt** file, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="fcd1f-129">À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_ BTAHL7PickUp dossier.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-129">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp folder.</span></span>  
  
4.  <span data-ttu-id="fcd1f-130">Cliquez avec le bouton droit, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-130">Right-click the folder, and then click **Paste**.</span></span>  
  
5.  <span data-ttu-id="fcd1f-131">À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_ BTAHL7Drop dossier.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-131">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop folder.</span></span>  
  
     <span data-ttu-id="fcd1f-132">Vous pouvez vérifier si votre installation a réussi, si l’instance traité s’affiche dans le **Tutorial_BTAHL7Drop** dossier en tant que \< *Guid*\>.txt.</span><span class="sxs-lookup"><span data-stu-id="fcd1f-132">You can verify if your installation was successful if the processed instance appears in the **Tutorial_BTAHL7Drop** folder as \<*Guid*\>.txt.</span></span>  
  
 <span data-ttu-id="fcd1f-133">Passez à l’étape suivante, [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md).</span><span class="sxs-lookup"><span data-stu-id="fcd1f-133">Proceed to the next step, [Preparing to Use the Tutorial](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md).</span></span>