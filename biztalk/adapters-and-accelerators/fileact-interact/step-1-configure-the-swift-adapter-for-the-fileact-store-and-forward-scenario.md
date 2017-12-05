---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18653322-b748-4954-93f7-9a7a39e406f8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e2883bb75667d2ad2518a4b8bf0c2a90be79ec8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="5cac2-102">Étape 1 : Configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="5cac2-102">Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="5cac2-103">Complète [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) avant de commencer cette étape.</span><span class="sxs-lookup"><span data-stu-id="5cac2-103">Complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) before you begin this step.</span></span>
  
## <a name="configure-the-swift-adapter"></a><span data-ttu-id="5cac2-104">Configurez la carte SWIFT</span><span class="sxs-lookup"><span data-stu-id="5cac2-104">Configure the SWIFT adapter</span></span>  
  
1.  <span data-ttu-id="5cac2-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5cac2-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5cac2-106">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit  **FILEACT**, pointez sur **nouveau**, puis cliquez sur **Gestionnaire d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="5cac2-106">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **FILEACT**, point to **New**, and then click **Send Handler**.</span></span>  
  
3.  <span data-ttu-id="5cac2-107">Dans le **FILEACT – carte HandlerProperties** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **fileacthost**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5cac2-107">In the **FILEACT – Adapter HandlerProperties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **fileacthost**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5cac2-108">Dans le **propriétés du Transport FILEACT** boîte de dialogue le **propriétés** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5cac2-108">In the **FILEACT Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="5cac2-109">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="5cac2-109">**Use this**</span></span>|<span data-ttu-id="5cac2-110">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="5cac2-110">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="5cac2-111">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="5cac2-111">**Arguments**</span></span>|<span data-ttu-id="5cac2-112">Type de l’argument suivant : - SagMessagePartner \<Fileact Client Message partenaire créé dans les trous\> **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.</span><span class="sxs-lookup"><span data-stu-id="5cac2-112">Type the following argument: -SagMessagePartner \<Fileact Client Message Partner created in SAG\> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="5cac2-113">**Mode de chiffrement**</span><span class="sxs-lookup"><span data-stu-id="5cac2-113">**Crypto Mode**</span></span>|<span data-ttu-id="5cac2-114">Dans la liste déroulante, sélectionnez **avancé**.</span><span class="sxs-lookup"><span data-stu-id="5cac2-114">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="5cac2-115">**FACryptoMode**</span><span class="sxs-lookup"><span data-stu-id="5cac2-115">**FACryptoMode**</span></span>|<span data-ttu-id="5cac2-116">Dans la liste déroulante, sélectionnez **avancé**.</span><span class="sxs-lookup"><span data-stu-id="5cac2-116">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="5cac2-117">**LogMessages**</span><span class="sxs-lookup"><span data-stu-id="5cac2-117">**LogMessages**</span></span>|<span data-ttu-id="5cac2-118">Dans la liste déroulante, sélectionnez **TRUE**.</span><span class="sxs-lookup"><span data-stu-id="5cac2-118">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="5cac2-119">Ainsi, les événements de message capturées et de suivi dans le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="5cac2-119">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="5cac2-120">**Activer**</span><span class="sxs-lookup"><span data-stu-id="5cac2-120">**Enable**</span></span>|<span data-ttu-id="5cac2-121">False</span><span class="sxs-lookup"><span data-stu-id="5cac2-121">False</span></span>|  
    |<span data-ttu-id="5cac2-122">**Fin de l’événement**</span><span class="sxs-lookup"><span data-stu-id="5cac2-122">**Event end-point**</span></span>|<span data-ttu-id="5cac2-123">Tapez le point de terminaison trous approprié.</span><span class="sxs-lookup"><span data-stu-id="5cac2-123">Type the appropriate SAG end-point.</span></span>|  
    |<span data-ttu-id="5cac2-124">**PhysicalFolderName**</span><span class="sxs-lookup"><span data-stu-id="5cac2-124">**PhysicalFolderName**</span></span>|<span data-ttu-id="5cac2-125">Tapez le nom du dossier sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="5cac2-125">Type the name of the folder on the server.</span></span> <span data-ttu-id="5cac2-126">Par exemple, C:\Fileact\ServerLocation.</span><span class="sxs-lookup"><span data-stu-id="5cac2-126">For example, C:\Fileact\ServerLocation.</span></span>|  
    |<span data-ttu-id="5cac2-127">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="5cac2-127">**PollingInterval**</span></span>|<span data-ttu-id="5cac2-128">Tapez l’intervalle approprié (en secondes) après lequel l’adaptateur vérifie pour l’état du transfert de fichiers.</span><span class="sxs-lookup"><span data-stu-id="5cac2-128">Type the appropriate interval (in seconds) after which the adapter checks for the status of file transfer.</span></span>|  
    |<span data-ttu-id="5cac2-129">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="5cac2-129">**Password**</span></span>|<span data-ttu-id="5cac2-130">Tapez le mot de passe que vous utilisez pour vous connecter à des trous.</span><span class="sxs-lookup"><span data-stu-id="5cac2-130">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="5cac2-131">Pour plus d’informations, consultez l’aide d’anti-COULURE.</span><span class="sxs-lookup"><span data-stu-id="5cac2-131">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="5cac2-132">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="5cac2-132">**User Name**</span></span>|<span data-ttu-id="5cac2-133">Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.</span><span class="sxs-lookup"><span data-stu-id="5cac2-133">Type the user name you use to connect to SAG.</span></span>|  
  
5.  <span data-ttu-id="5cac2-134">Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport FILEACT.</span><span class="sxs-lookup"><span data-stu-id="5cac2-134">Click **OK** to close the FILEACT Transport Properties dialog box.</span></span>  
  
6.  <span data-ttu-id="5cac2-135">Cliquez sur **OK** pour fermer la FILEACT – boîte de dialogue Propriétés de gestionnaire d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="5cac2-135">Click **OK** to close the FILEACT – Adapter Handler Properties dialog box.</span></span>  
  
7.  <span data-ttu-id="5cac2-136">Dans la boîte de Message, cliquez sur **OK**, puis redémarrez l’instance d’hôte FileAct.</span><span class="sxs-lookup"><span data-stu-id="5cac2-136">In the Message box, click **OK**, and then restart the FileAct host instance.</span></span>  
  
## <a name="complete-steps"></a><span data-ttu-id="5cac2-137">Étapes à suivre</span><span class="sxs-lookup"><span data-stu-id="5cac2-137">Complete steps</span></span>
 <span data-ttu-id="5cac2-138">[Scénario de transfert et de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="5cac2-138">[FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="5cac2-139">[Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="5cac2-139">[Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md) </span></span>  
 <span data-ttu-id="5cac2-140">[Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="5cac2-140">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="5cac2-141">Étape 4 : Tester le scénario de stockage et de redirection FileAct de bout en bout</span><span class="sxs-lookup"><span data-stu-id="5cac2-141">Step 4: Test FileAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)