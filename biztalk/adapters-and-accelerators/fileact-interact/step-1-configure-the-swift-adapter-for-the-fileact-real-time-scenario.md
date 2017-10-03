---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afc52c63-9f83-4e90-9269-e90834b792bf
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb671d0d4425cd935efd7f13aba0e39fd400e17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario"></a><span data-ttu-id="a1886-102">Étape 1 : Configurer l’adaptateur SWIFT pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="a1886-102">Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="a1886-103">Avant de commencer cette étape, vous devez effectuer [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).</span><span class="sxs-lookup"><span data-stu-id="a1886-103">Before you begin this step, you must complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).</span></span>  
  
### <a name="to-configure-the-swift-adapter"></a><span data-ttu-id="a1886-104">Pour configurer l’adaptateur SWIFT</span><span class="sxs-lookup"><span data-stu-id="a1886-104">To configure the SWIFT adapter</span></span>  
  
1.  <span data-ttu-id="a1886-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a1886-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a1886-106">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit  **FILEACT**, pointez sur **nouveau**, puis cliquez sur **Gestionnaire d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="a1886-106">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **FILEACT**, point to **New**, and then click **Send Handler**.</span></span>  
  
3.  <span data-ttu-id="a1886-107">Dans le **FILEACT – propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **fileacthost**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a1886-107">In the **FILEACT – Adapter Handler Properties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **fileacthost**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a1886-108">Dans le **propriétés du Transport FILEACT** boîte de dialogue le **propriétés** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a1886-108">In the **FILEACT Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="a1886-109">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="a1886-109">**Use this**</span></span>|<span data-ttu-id="a1886-110">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="a1886-110">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a1886-111">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="a1886-111">**Arguments**</span></span>|<span data-ttu-id="a1886-112">Type de l’argument suivant : - SagMessagePartner \<Fileact Client Message partenaire créé dans les trous > **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.</span><span class="sxs-lookup"><span data-stu-id="a1886-112">Type the following argument: -SagMessagePartner \<Fileact Client Message Partner created in SAG> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="a1886-113">**Mode de chiffrement**</span><span class="sxs-lookup"><span data-stu-id="a1886-113">**Crypto Mode**</span></span>|<span data-ttu-id="a1886-114">Dans la liste déroulante, sélectionnez **avancé**.</span><span class="sxs-lookup"><span data-stu-id="a1886-114">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="a1886-115">**FACryptoMode**</span><span class="sxs-lookup"><span data-stu-id="a1886-115">**FACryptoMode**</span></span>|<span data-ttu-id="a1886-116">Dans la liste déroulante, sélectionnez **avancé**.</span><span class="sxs-lookup"><span data-stu-id="a1886-116">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="a1886-117">**LogMessages**</span><span class="sxs-lookup"><span data-stu-id="a1886-117">**LogMessages**</span></span>|<span data-ttu-id="a1886-118">Dans la liste déroulante, sélectionnez **TRUE**.</span><span class="sxs-lookup"><span data-stu-id="a1886-118">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="a1886-119">Ainsi, les événements de message capturées et de suivi dans le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="a1886-119">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="a1886-120">**Activer**</span><span class="sxs-lookup"><span data-stu-id="a1886-120">**Enable**</span></span>|<span data-ttu-id="a1886-121">False</span><span class="sxs-lookup"><span data-stu-id="a1886-121">False</span></span>|  
    |<span data-ttu-id="a1886-122">**Fin de l’événement**</span><span class="sxs-lookup"><span data-stu-id="a1886-122">**Event end-point**</span></span>|<span data-ttu-id="a1886-123">Tapez le point de terminaison trous approprié.</span><span class="sxs-lookup"><span data-stu-id="a1886-123">Type the appropriate SAG end-point.</span></span>|  
    |<span data-ttu-id="a1886-124">**PhysicalFolderName**</span><span class="sxs-lookup"><span data-stu-id="a1886-124">**PhysicalFolderName**</span></span>|<span data-ttu-id="a1886-125">Tapez le nom du dossier sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="a1886-125">Type the name of the folder on the server.</span></span> <span data-ttu-id="a1886-126">Par exemple, C:\Fileact\ServerLocation.</span><span class="sxs-lookup"><span data-stu-id="a1886-126">For example, C:\Fileact\ServerLocation.</span></span>|  
    |<span data-ttu-id="a1886-127">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="a1886-127">**PollingInterval**</span></span>|<span data-ttu-id="a1886-128">Tapez l’intervalle approprié (en secondes) après lequel l’adaptateur vérifie pour l’état du transfert de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a1886-128">Type the appropriate interval (in seconds) after which the adapter checks for the status of file transfer.</span></span>|  
    |<span data-ttu-id="a1886-129">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="a1886-129">**Password**</span></span>|<span data-ttu-id="a1886-130">Tapez le mot de passe que vous utilisez pour vous connecter à des trous.</span><span class="sxs-lookup"><span data-stu-id="a1886-130">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="a1886-131">Pour plus d’informations, consultez l’aide d’anti-COULURE.</span><span class="sxs-lookup"><span data-stu-id="a1886-131">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="a1886-132">**Nom d’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="a1886-132">**Username**</span></span>|<span data-ttu-id="a1886-133">Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.</span><span class="sxs-lookup"><span data-stu-id="a1886-133">Type the user name you use to connect to SAG.</span></span>|  
  
5.  <span data-ttu-id="a1886-134">Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport FILEACT.</span><span class="sxs-lookup"><span data-stu-id="a1886-134">Click **OK** to close the FILEACT Transport Properties dialog box.</span></span>  
  
6.  <span data-ttu-id="a1886-135">Cliquez sur **OK** pour fermer la FILEACT – boîte de dialogue Propriétés de gestionnaire d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a1886-135">Click **OK** to close the FILEACT – Adapter Handler Properties dialog box.</span></span>  
  
7.  <span data-ttu-id="a1886-136">Dans la boîte de message, cliquez sur **OK**, puis redémarrez l’instance d’hôte FileAct.</span><span class="sxs-lookup"><span data-stu-id="a1886-136">In the message box, click **OK**, and then restart the FileAct host instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1886-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1886-137">See Also</span></span>  
 <span data-ttu-id="a1886-138">[Scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a1886-138">[FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="a1886-139">[Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a1886-139">[Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="a1886-140">[Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a1886-140">[Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="a1886-141">Étape 4 : Tester le scénario de bout en bout FileAct en temps réel</span><span class="sxs-lookup"><span data-stu-id="a1886-141">Step 4: Test FileAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)