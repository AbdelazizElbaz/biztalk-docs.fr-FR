---
title: Installer le FileAct et interagir adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf387d59-373b-4151-9dfd-30c511978862
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a3beccd6179bcb4526ba41f4f41a7923f5f966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-fileact-and-interact-adapter"></a><span data-ttu-id="8dc71-102">Installer le FileAct et interagir de carte</span><span class="sxs-lookup"><span data-stu-id="8dc71-102">Install the FileAct and InterAct Adapter</span></span>
<span data-ttu-id="8dc71-103">Cette section fournit des instructions pour installer [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] – pour SWIFT.</span><span class="sxs-lookup"><span data-stu-id="8dc71-103">This section provides instructions to install [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] – for SWIFT.</span></span> <span data-ttu-id="8dc71-104">Avant d’installer les adaptateurs, vous devez installer les logiciels requis.</span><span class="sxs-lookup"><span data-stu-id="8dc71-104">Before you install the adapters, you must install the prerequisite software.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8dc71-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8dc71-105">Prerequisites</span></span>  

* <span data-ttu-id="8dc71-106">Connectez-vous avec un compte qui est membre du groupe Administrateurs local et membre du groupe Administrateurs de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8dc71-106">Sign in with an account that is member of the local administrators group, and a member of the BizTalk Server Administrators group</span></span>
  
## <a name="step-1-install-biztalk-server-and-configure-bam"></a><span data-ttu-id="8dc71-107">Étape 1 : Installez BizTalk Server et configurer l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="8dc71-107">Step 1: Install BizTalk Server and configure BAM</span></span>

1. <span data-ttu-id="8dc71-108">Installer [BizTalk Server 2016](../../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md), ou [BizTalk Server 2013 R2 / 2013](../../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md)et d’installer l’analyse BAM (Business Activity).</span><span class="sxs-lookup"><span data-stu-id="8dc71-108">Install [BizTalk Server 2016](../../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md), or [BizTalk Server 2013 R2 / 2013](../../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md), and install Business Activity Monitoring (BAM).</span></span>

2. <span data-ttu-id="8dc71-109">Configurer [BizTalk Server](../../install-and-config-guides/configure-biztalk-server.md)et configurer l’analyse BAM (Business Activity).</span><span class="sxs-lookup"><span data-stu-id="8dc71-109">Configure [BizTalk Server](../../install-and-config-guides/configure-biztalk-server.md), and configure Business Activity Monitoring (BAM).</span></span>
  
3. <span data-ttu-id="8dc71-110">Assurez-vous que vous avez suffisamment des privilèges de sécurité pour accéder à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8dc71-110">Make sure you have enough security privileges to access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="8dc71-111">[Les droits de sécurité minimaux pour BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) est un bon point de départ.</span><span class="sxs-lookup"><span data-stu-id="8dc71-111">[Minimum Security Rights for BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) is a great resource.</span></span>
  
## <a name="step-2-install-biztalk-accelerator-for-swift-a4swift"></a><span data-ttu-id="8dc71-112">Étape 2 : Installer BizTalk Accelerator pour SWIFT (A4SWIFT)</span><span class="sxs-lookup"><span data-stu-id="8dc71-112">Step 2: Install BizTalk Accelerator for SWIFT (A4SWIFT)</span></span>  

<span data-ttu-id="8dc71-113">Installer et configurer le [BizTalk Accelerator pour SWIFT](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md).</span><span class="sxs-lookup"><span data-stu-id="8dc71-113">Install and configure the [BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md).</span></span>

  
## <a name="step-3-install-swiftalliance-gateway-sag"></a><span data-ttu-id="8dc71-114">Étape 3 : Installer SWIFTAlliance passerelle (trous)</span><span class="sxs-lookup"><span data-stu-id="8dc71-114">Step 3: Install SWIFTAlliance Gateway (SAG)</span></span>  
 <span data-ttu-id="8dc71-115">Avant d’installer les adaptateurs FileAct et InterAct, créez les partenaires de Message anti-COULURE, Points de terminaison et des règles de routage et tester la connectivité de trous sur l’ordinateur sur lequel vous installez les adaptateurs FileAct et InterAct.</span><span class="sxs-lookup"><span data-stu-id="8dc71-115">Before you install the FileAct and InterAct adapters, create the SAG Message Partners, End Points, and Routing Rules, and test the SAG connectivity on the computer where you install the FileAct and InterAct adapters.</span></span>

<span data-ttu-id="8dc71-116">Consultez [https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway](https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway) pour plus d’informations sur la passerelle SWIFTAlliance.</span><span class="sxs-lookup"><span data-stu-id="8dc71-116">See [https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway](https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway) for specific details on the SWIFTAlliance Gateway.</span></span>  

## <a name="step-4-install-the-biztalk-fileact-and-interact-adapters"></a><span data-ttu-id="8dc71-117">Étape 4 : Installer les adaptateurs BizTalk FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="8dc71-117">Step 4: Install the BizTalk FileAct and InterAct adapters</span></span>  
  
1. <span data-ttu-id="8dc71-118">Exécutez le **Setup.exe** en tant qu’administrateur pour démarrer l’installation.</span><span class="sxs-lookup"><span data-stu-id="8dc71-118">Run the **Setup.exe** as administrator to start the installation.</span></span>  
  
2.  <span data-ttu-id="8dc71-119">Sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="8dc71-119">Select **Install**.</span></span>  
  
3.  <span data-ttu-id="8dc71-120">Entrez votre nom d’utilisateur et le nom de l’organisation, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8dc71-120">Enter your user name and organization name, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="8dc71-121">**Accepter** le contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="8dc71-121">**Accept** the license agreement.</span></span>
  
5.  <span data-ttu-id="8dc71-122">Sur le **Options d’Installation** page, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8dc71-122">On the **Installation Options** page, do one of the following:</span></span>  
  
    -   <span data-ttu-id="8dc71-123">Sélectionnez le **Complete** option pour installer tous les composants de la FileAct et interagir de cartes.</span><span class="sxs-lookup"><span data-stu-id="8dc71-123">Select the **Complete** option to install all components of the FileAct and InterAct adapters.</span></span>  
  
    -   <span data-ttu-id="8dc71-124">Sélectionnez le **personnalisé** permet de choisir les composants à installer.</span><span class="sxs-lookup"><span data-stu-id="8dc71-124">Select the **Custom** option to choose which components to install.</span></span>  
  
     <span data-ttu-id="8dc71-125">Vérifiez l’emplacement d’installation, ou sélectionnez **Parcourir** pour sélectionner un autre emplacement d’installation.</span><span class="sxs-lookup"><span data-stu-id="8dc71-125">Verify the installation location, or select **Browse** to select a different installation location.</span></span> <span data-ttu-id="8dc71-126">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="8dc71-126">Select **Next**.</span></span>  
  
6.  <span data-ttu-id="8dc71-127">Sur le **Résumé** page, sélectionnez **installer** pour installer les composants répertoriés.</span><span class="sxs-lookup"><span data-stu-id="8dc71-127">On the **Summary** page, select **Install** to install the listed components.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dc71-128">Lorsque **exécuter l’Assistant Configuration** est activée (valeur par défaut), le **Microsoft BizTalk FileAct et Configuration de l’adaptateur interagir** Assistant s’exécute automatiquement lorsque vous sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="8dc71-128">When **Run Configuration Wizard** is selected (the default), the **Microsoft BizTalk FileAct and InterAct Adapter Configuration** wizard runs automatically when you select **Finish**.</span></span>  
  
7. <span data-ttu-id="8dc71-129">Lors de l’installation terminée, sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="8dc71-129">When the installation completes, select **Finish**.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="8dc71-130">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8dc71-130">Next steps</span></span>

[<span data-ttu-id="8dc71-131">Configurer l’adaptateur FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="8dc71-131">Configure the FileAct and InterAct adapter</span></span>](../../adapters-and-accelerators/fileact-interact/configure-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="8dc71-132">Messages exemple interagir et FileAct</span><span class="sxs-lookup"><span data-stu-id="8dc71-132">Sample InterAct and FileAct messages</span></span>](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)  
[<span data-ttu-id="8dc71-133">Désinstaller ou réparer l’adaptateur FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="8dc71-133">Uninstall or repair the FileAct and InterAct adapter</span></span>](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[<span data-ttu-id="8dc71-134">Lecture de l’installation des problèmes connus</span><span class="sxs-lookup"><span data-stu-id="8dc71-134">Read the installation known issues</span></span>](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
  
## <a name="see-also"></a><span data-ttu-id="8dc71-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dc71-135">See Also</span></span>  
[<span data-ttu-id="8dc71-136">Mise en route avec les adaptateurs FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="8dc71-136">Getting started with the FileAct and InterAct adapters</span></span>](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)  
[<span data-ttu-id="8dc71-137">Comprendre l’architecture de l’adaptateur FileAct et InterAct</span><span class="sxs-lookup"><span data-stu-id="8dc71-137">Understanding FileAct and InterAct adapter architecture</span></span>](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)