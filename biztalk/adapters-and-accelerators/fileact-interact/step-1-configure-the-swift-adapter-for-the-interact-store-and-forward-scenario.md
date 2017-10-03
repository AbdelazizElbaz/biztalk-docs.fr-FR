---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b81599-bd26-44dc-9cf3-73868248764c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e71525c74da0f7df0769c99d443c16cc672cfbcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="40540-102">Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="40540-102">Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="40540-103">Avant de commencer cette étape, vous devez effectuer [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).</span><span class="sxs-lookup"><span data-stu-id="40540-103">Before you begin this step, you must complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).</span></span>  
  
### <a name="to-configure-the-swift-adapter"></a><span data-ttu-id="40540-104">Pour configurer l’adaptateur SWIFT</span><span class="sxs-lookup"><span data-stu-id="40540-104">To configure the SWIFT adapter</span></span>  
  
1.  <span data-ttu-id="40540-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="40540-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="40540-106">Dans l’arborescence de la console, développez Administration de BizTalk Server, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit **interagir**, pointez sur **Nouveau**, puis cliquez sur **Gestionnaire d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="40540-106">In the console tree, expand BizTalk Server Administration, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **INTERACT**, point to **New**, and then click **Send Handler**.</span></span>  
  
3.  <span data-ttu-id="40540-107">Dans le **interagir – propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **interacthost**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="40540-107">In the **INTERACT – Adapter Handler Properties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **interacthost**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="40540-108">Dans le **propriétés du Transport interagir** boîte de dialogue le **propriétés** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="40540-108">In the **INTERACT Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="40540-109">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="40540-109">**Use this**</span></span>|<span data-ttu-id="40540-110">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="40540-110">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="40540-111">**Arguments**</span><span class="sxs-lookup"><span data-stu-id="40540-111">**Arguments**</span></span>|<span data-ttu-id="40540-112">Type de l’argument suivant : – SagMessagePartner \<interagir de partenaire de Message Client créé dans les trous > **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.</span><span class="sxs-lookup"><span data-stu-id="40540-112">Type the following argument: –SagMessagePartner \<Interact Client Message Partner created in SAG> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="40540-113">**Mode de chiffrement**</span><span class="sxs-lookup"><span data-stu-id="40540-113">**Crypto Mode**</span></span>|<span data-ttu-id="40540-114">Dans la liste déroulante, sélectionnez **avancé**.</span><span class="sxs-lookup"><span data-stu-id="40540-114">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="40540-115">**LogMessageBody**</span><span class="sxs-lookup"><span data-stu-id="40540-115">**LogMessageBody**</span></span>|<span data-ttu-id="40540-116">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="40540-116">From the drop-down list, select **FALSE**.</span></span> <span data-ttu-id="40540-117">**Remarque :** si vous affectez la valeur TRUE, il conserve le corps du message dans la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="40540-117">**Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database.</span></span> <span data-ttu-id="40540-118">Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="40540-118">However, for security reasons, the message body can never be viewed in the BAM portal.</span></span>|  
    |<span data-ttu-id="40540-119">**LogMessages**</span><span class="sxs-lookup"><span data-stu-id="40540-119">**LogMessages**</span></span>|<span data-ttu-id="40540-120">Dans la liste déroulante, sélectionnez **TRUE**.</span><span class="sxs-lookup"><span data-stu-id="40540-120">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="40540-121">Ainsi, les événements de message capturées et de suivi dans le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="40540-121">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="40540-122">**Activer**</span><span class="sxs-lookup"><span data-stu-id="40540-122">**Enable**</span></span>|<span data-ttu-id="40540-123">False :</span><span class="sxs-lookup"><span data-stu-id="40540-123">False.</span></span>|  
    |<span data-ttu-id="40540-124">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="40540-124">**Password**</span></span>|<span data-ttu-id="40540-125">Tapez le mot de passe que vous utilisez pour vous connecter à des trous.</span><span class="sxs-lookup"><span data-stu-id="40540-125">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="40540-126">Pour plus d’informations, consultez l’aide d’anti-COULURE.</span><span class="sxs-lookup"><span data-stu-id="40540-126">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="40540-127">**Nom d’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="40540-127">**Username**</span></span>|<span data-ttu-id="40540-128">Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.</span><span class="sxs-lookup"><span data-stu-id="40540-128">Type the user name you use to connect to SAG.</span></span>|  
  
5.  <span data-ttu-id="40540-129">Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport interagir.</span><span class="sxs-lookup"><span data-stu-id="40540-129">Click **OK** to close the INTERACT Transport Properties dialog box.</span></span>  
  
6.  <span data-ttu-id="40540-130">Cliquez sur **OK** pour fermer l’interagir – boîte de dialogue Propriétés de gestionnaire d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="40540-130">Click **OK** to close the INTERACT – Adapter Handler Properties dialog box.</span></span>  
  
7.  <span data-ttu-id="40540-131">Dans la boîte de message, cliquez sur **OK**, puis redémarrez l’instance d’hôte interagir.</span><span class="sxs-lookup"><span data-stu-id="40540-131">In the message box, click **OK**, and then restart the InterAct host instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40540-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40540-132">See Also</span></span>  
 <span data-ttu-id="40540-133">[Interagir Store et le scénario de transfert (Push)](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="40540-133">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="40540-134">[Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="40540-134">[Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) </span></span>  
 <span data-ttu-id="40540-135">[Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="40540-135">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="40540-136">Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant</span><span class="sxs-lookup"><span data-stu-id="40540-136">Step 4: Test the InterAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)