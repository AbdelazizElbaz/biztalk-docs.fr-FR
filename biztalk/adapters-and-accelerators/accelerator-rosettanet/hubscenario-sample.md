---
title: Exemple HubScenario | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb6990ec-aea2-4362-8573-7f737a4fc7f1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9b2770f1d14d716149025ac44cb3cdffbbb23b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hubscenario-sample"></a><span data-ttu-id="54691-102">Exemple HubScenario</span><span class="sxs-lookup"><span data-stu-id="54691-102">HubScenario Sample</span></span>
<span data-ttu-id="54691-103">L'exemple HubScenario montre comment gérer la transmission des messages dans un scénario basé sur un hub.</span><span class="sxs-lookup"><span data-stu-id="54691-103">The HubScenario sample demonstrates how to manage message transmission in a hub scenario.</span></span> <span data-ttu-id="54691-104">Il convertit un message envoyé à un hub intermédiaire en message à envoyer au destinataire final.</span><span class="sxs-lookup"><span data-stu-id="54691-104">It transforms a message sent to an intermediary hub into a message to be sent to the final recipient.</span></span>  
  
 <span data-ttu-id="54691-105">HubScenario extrait le numéro DUNS du destinataire final à partir du contenu du service.</span><span class="sxs-lookup"><span data-stu-id="54691-105">HubScenario extracts the DUNS number of the final recipient from the service content.</span></span> <span data-ttu-id="54691-106">Il gère les certificats de signature et de chiffrement, ainsi que l'URL de destination.</span><span class="sxs-lookup"><span data-stu-id="54691-106">It manages signing and encryption certificates, and the destination URL.</span></span> <span data-ttu-id="54691-107">Il génère un nouveau message pour le destinataire final.</span><span class="sxs-lookup"><span data-stu-id="54691-107">It generates a new message for the final recipient.</span></span>  
  
 <span data-ttu-id="54691-108">Cet exemple gère les messages de requête et de réponse 3A4, ainsi que les messages de requête 0C1.</span><span class="sxs-lookup"><span data-stu-id="54691-108">This sample handles 3A4 request and response messages, and 0C1 request messages.</span></span> <span data-ttu-id="54691-109">Quand vous utilisez HubScenario pour créer une application répondant à vos besoins, vous devez générer des routines pour chaque message PIP (Partner Interface Process).</span><span class="sxs-lookup"><span data-stu-id="54691-109">When you use HubScenario to create an application for your purposes, you will have to generate routines for each message Partner Interface Process (PIP).</span></span>  
  
 <span data-ttu-id="54691-110">L'exemple HubScenario inclut les projets HubHelper.cs et HubScenario.odx.</span><span class="sxs-lookup"><span data-stu-id="54691-110">The HubScenario sample includes HubHelper.cs and HubScenario.odx projects.</span></span>  
  
 <span data-ttu-id="54691-111">L'exemple HubScenario inclut également un fichier de liaison qui vous permet d'importer des liaisons pour un port de réception (MessagesToLOB_Receive_Port) et un emplacement de réception (MessagesToLOB_Receive_Location) à utiliser avec l'orchestration HubScenario.odx.</span><span class="sxs-lookup"><span data-stu-id="54691-111">The HubScenario sample also includes a binding file that you can use to import bindings for a receive port (MessagesToLOB_Receive_Port) and receive location (MessagesToLOB_Receive_Location) for use with the HubScenario.odx orchestration.</span></span> <span data-ttu-id="54691-112">Ce fichier de liaison (HubScenarioBinding.xml) se trouve dans  *\<lecteur >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version > Accelerator for RosettaNet \SDK\ HubScenario.</span><span class="sxs-lookup"><span data-stu-id="54691-112">This binding file (HubScenarioBinding.xml) is located in *\<drive>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version> Accelerator for RosettaNet \SDK\HubScenario.</span></span> <span data-ttu-id="54691-113">Utilisez la commande BTSTask pour importer les liaisons.</span><span class="sxs-lookup"><span data-stu-id="54691-113">Use the BTSTask command to import the bindings.</span></span> <span data-ttu-id="54691-114">Pour plus d’informations, consultez la rubrique « Commande ImportBindings » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="54691-114">For more information, see the "ImportBindings Command" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="54691-115">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="54691-115">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="54691-116">Dans Visual Studio, ouvrez \<lecteur > : \Program Files\Microsoft Microsoft BizTalk \<version > Accelerator pour RosettaNet\SDK\HubScenario\HubScenario.btproj.</span><span class="sxs-lookup"><span data-stu-id="54691-116">In Visual Studio, open \<drive>:\Program Files\Microsoft Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\HubScenario\HubScenario.btproj.</span></span> <span data-ttu-id="54691-117">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet HubScenario, puis cliquez sur Propriétés.</span><span class="sxs-lookup"><span data-stu-id="54691-117">In Solution Explorer, right-click the HubScenario project, and then click Properties.</span></span> <span data-ttu-id="54691-118">Dans la page de propriétés du projet HubScenario, sous l'onglet Signature, cochez la case **Signer l'assembly** , sélectionnez **HubScenario.snk** dans **Choisir un fichier de clé de nom fort** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="54691-118">In the Properties page for the HubScenario project, in the Signing tab select **Sign the assembly** checkbox, and select **HubScenario.snk** in **Choose a strong name key file** and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="54691-119">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet HubHelper, puis cliquez sur Propriétés.</span><span class="sxs-lookup"><span data-stu-id="54691-119">In Solution Explorer, right-click the HubHelper project, and then click Properties.</span></span> <span data-ttu-id="54691-120">Dans la page de propriétés du projet HubHelper, sous l'onglet Signature, cochez la case Signer l'assembly.</span><span class="sxs-lookup"><span data-stu-id="54691-120">In the Properties page for the HubHelper project, in the Signing tab check Sign the assembly checkbox.</span></span> <span data-ttu-id="54691-121">Dans le champ Choisir un fichier de clé de nom fort, sélectionnez le nouveau type **HubHelper.snk** en tant que nom de fichier de clé, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="54691-121">In Choose a strong name key file field, select new type **HubHelper.snk** as Key file name and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54691-122">Si vous n'entrez pas manuellement le fichier de clé d'assembly dans les projets HubScenario et HubHelper, les assemblys ne seront pas déployés.</span><span class="sxs-lookup"><span data-stu-id="54691-122">If you do not manually enter the assembly key file in the HubScenario and HubHelper projects, the assemblies will not deploy.</span></span>  
  
3.  <span data-ttu-id="54691-123">À l’invite de commandes, passez à  *\<lecteur >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version > Accelerator pour RosettaNet\SDK\HubScenario dossier.</span><span class="sxs-lookup"><span data-stu-id="54691-123">At a command prompt, move to *\<drive>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\HubScenario folder.</span></span> <span data-ttu-id="54691-124">Exécutez le fichier Setup.bat (ou sur un ordinateur 64 bits, exécutez Setupx64.bat).</span><span class="sxs-lookup"><span data-stu-id="54691-124">Run the file Setup.bat (or on a 64-bit computer, run Setupx64.bat).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="54691-125">Montre</span><span class="sxs-lookup"><span data-stu-id="54691-125">Demonstrates</span></span>  
 <span data-ttu-id="54691-126">L'orchestration HubScenario.ods montre comment effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="54691-126">The HubScenario.ods orchestration demonstrates how to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="54691-127">Reçoit le message de l'application métier.</span><span class="sxs-lookup"><span data-stu-id="54691-127">Receives the message from the line-of-business application.</span></span>  
  
2.  <span data-ttu-id="54691-128">Supprime l'élément `CDATA` du contenu du service, en retournant la chaîne XML.</span><span class="sxs-lookup"><span data-stu-id="54691-128">Removes the `CDATA` element from the service content, returning the XML string.</span></span>  
  
3.  <span data-ttu-id="54691-129">Récupère le nom du tiers de destination, ainsi que le PIPCode, le PIPInstanceID et le PIPVersion pour le message final.</span><span class="sxs-lookup"><span data-stu-id="54691-129">Retrieves the destination party name, PIPCode, PIPInstanceID, and PIPVersion for the final message.</span></span>  
  
4.  <span data-ttu-id="54691-130">Récupère le numéro DUNS du destinataire final.</span><span class="sxs-lookup"><span data-stu-id="54691-130">Retrieves the DUNS number for the final recipient.</span></span>  
  
5.  <span data-ttu-id="54691-131">Détermine la catégorie du message, puis ajoute l'élément DOCTYPE contenant une référence au schéma approprié pour le contenu du service.</span><span class="sxs-lookup"><span data-stu-id="54691-131">Determines the category of the message, and adds the DOCTYPE element that contains a reference to the appropriate schema to the service content.</span></span>  
  
6.  <span data-ttu-id="54691-132">Construit un message avec le nouveau nom du tiers de destination, ainsi que le numéro DUNS, les informations de code PIP et le contenu du service.</span><span class="sxs-lookup"><span data-stu-id="54691-132">Constructs a message with the new destination party name, DUNS number, PIP code information, and service content.</span></span>  
  
7.  <span data-ttu-id="54691-133">Envoie le message de traitement par [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54691-133">Submits the message for processing by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="54691-134">Il s'agit d'un appel à `SubmitRNIF.SubmitMessage`.</span><span class="sxs-lookup"><span data-stu-id="54691-134">This is a call to `SubmitRNIF.SubmitMessage`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54691-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54691-135">See Also</span></span>  
 <span data-ttu-id="54691-136">[Exemple de scénario basé sur un concentrateur](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="54691-136">[Sample Hub-Based Scenario](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md) </span></span>  
 [<span data-ttu-id="54691-137">Exemples d’orchestration</span><span class="sxs-lookup"><span data-stu-id="54691-137">Orchestration Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)