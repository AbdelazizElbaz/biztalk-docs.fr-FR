---
title: "Modification d’un PIP existant dans RNPIPs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RNPIPs
- modifying, PIPs
- PIPs, modifying
- assemblies, RNPIPs
ms.assetid: f2ed25c4-1979-4691-9315-e7568e7cca8b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7aa00b1a029092247d3c4ce935edfd88f4344a95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="modifying-an-existing-pip-in-rnpips"></a><span data-ttu-id="f5b1a-102">Modification d’un PIP existant dans RNPIPs</span><span class="sxs-lookup"><span data-stu-id="f5b1a-102">Modifying an Existing PIP in RNPIPs</span></span>
<span data-ttu-id="f5b1a-103">Cette rubrique décrit comment modifier et redéployer l’un des schémas de processus PIP (Partner Interface) installés par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-103">This topic describes how to change and re-deploy one of the Partner Interface Process (PIP) schemas installed by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] setup.</span></span> <span data-ttu-id="f5b1a-104">Vous déployez le schéma dans le cadre de l'assembly RNPIPs.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-104">You deploy the schema as part of the RNPIPs assembly.</span></span>  
  
### <a name="to-modify-an-existing-pip-in-rnpips"></a><span data-ttu-id="f5b1a-105">Pour modifier un PIP existant dans RNPIPs</span><span class="sxs-lookup"><span data-stu-id="f5b1a-105">To modify an existing PIP in RNPIPs</span></span>  
  
1.  <span data-ttu-id="f5b1a-106">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-106">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="f5b1a-107">Recherchez le \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator pour le dossier du Générateur de RosettaNet\SDK\Utilities\Schema.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-107">Locate the \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\Utilities\Schema Generator folder.</span></span>  
  
3.  <span data-ttu-id="f5b1a-108">À l'invite de commandes, tapez **CScript InstallDTD.vbs**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-108">At the command prompt, type **CScript InstallDTD.vbs**, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5b1a-109">Vous ne devez effectuer les étapes 1 et 2 une fois après l’installation de [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5b1a-109">You only have to do steps 1 and 2 one time after you install [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
4.  <span data-ttu-id="f5b1a-110">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-110">Start **Microsoft Visual Studio 2012**.</span></span>  
  
5.  <span data-ttu-id="f5b1a-111">Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-111">In the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
6.  <span data-ttu-id="f5b1a-112">Dans le **ouvrir le projet** boîte de dialogue, accédez à \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas, puis sélectionnez  **RNPIPs.btproj**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-112">In the **Open Project** dialog box, move to \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\Schemas, and then select **RNPIPs.btproj**.</span></span>  
  
7.  <span data-ttu-id="f5b1a-113">Dans le menu **Affichage** , cliquez sur **Explorateur BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-113">In the **View** menu, click **BizTalk Explorer**.</span></span> <span data-ttu-id="f5b1a-114">Développez **Assemblys**, puis cliquez avec le bouton droit sur **Microsoft.Solutions.BTARN.Schemas.RNPIPs(3.3.0.0)**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-114">Expand **Assemblies**, and then right-click **Microsoft.Solutions.BTARN.Schemas.RNPIPs(3.3.0.0)**.</span></span> <span data-ttu-id="f5b1a-115">Cliquez sur **Annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-115">Click **Undeploy**.</span></span>  
  
8.  <span data-ttu-id="f5b1a-116">Démarrez une **invite de commandes Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-116">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
9. <span data-ttu-id="f5b1a-117">Accédez à l'emplacement entré à l'étape 6. À l'invite de commandes, tapez **sn -k RNPIPs.snk**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-117">Move to the location entered in step 6, at the command prompt, type **sn -k RNPIPs.snk**, and then press **Enter**.</span></span>  
  
10. <span data-ttu-id="f5b1a-118">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **RNPIPs**, cliquez sur **Propriétés**, sur **Propriétés communes**, puis sur **Assembly.**</span><span class="sxs-lookup"><span data-stu-id="f5b1a-118">In Solution Explorer, right-click **RNPIPs**, click **Properties**, click **Common Properties**, and then click **Assembly.**</span></span>  
  
11. <span data-ttu-id="f5b1a-119">Dans le volet droit, faites défiler jusqu'à **Nom fort**. Dans la section **Fichier de clé de l'assembly** , cliquez sur le bouton de sélection (...) et accédez à l'emplacement entré à l'étape 6. À l'invite de commandes, tapez **RNPIPs.snk**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-119">In the right pane, scroll down to **Strong Name**, in the **Assembly Key File** section, click the ellipsis button (...) button, go to the location entered in step 6, at the command prompt, type **RNPIPs.snk**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="f5b1a-120">Dans la boîte de dialogue **Pages de propriétés** , cliquez sur **Propriétés de configuration**, sur **Déploiement**, sur **Redéployer**, sélectionnez `True`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-120">In the **Property Pages** dialog box, click **Configuration Properties**, click **Deployment**, click **Redeploy**, select `True`, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="f5b1a-121">Modifiez tous les schémas existants dans RNPIPs, en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-121">Edit any of the existing schemas in RNPIPs, as required.</span></span>  
  
14. <span data-ttu-id="f5b1a-122">Cliquez sur **Fichier**, puis sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-122">Click **File**, and then click **Save**.</span></span>  
  
15. <span data-ttu-id="f5b1a-123">Cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-123">Right-click the project name, and then click **Build**.</span></span>  
  
16. <span data-ttu-id="f5b1a-124">Cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-124">Right-click the project name, and then click **Deploy**.</span></span>  
  
17. <span data-ttu-id="f5b1a-125">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-125">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
18. <span data-ttu-id="f5b1a-126">Dans la Console Administration de BizTalk, développez **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, puis développez **hôtes**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-126">In BizTalk Administration Console, expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, and then expand **Hosts**.</span></span>  
  
19. <span data-ttu-id="f5b1a-127">Dans le volet droit, cliquez avec le bouton droit sur le nom de l'hôte, puis cliquez sur **Arrêter**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-127">In the right pane, right-click the name of the host, and then click **Stop**.</span></span> <span data-ttu-id="f5b1a-128">Une fois le service arrêté, cliquez avec le bouton droit sur le nom de l'hôte, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="f5b1a-128">After the service has stopped, right-click the name of the host, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b1a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5b1a-129">See Also</span></span>  
 <span data-ttu-id="f5b1a-130">[Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span><span class="sxs-lookup"><span data-stu-id="f5b1a-130">[Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md) </span></span>  
 [<span data-ttu-id="f5b1a-131">Vous incorporez un nouveau Partner Interface Process</span><span class="sxs-lookup"><span data-stu-id="f5b1a-131">Incorporating a New Partner Interface Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)