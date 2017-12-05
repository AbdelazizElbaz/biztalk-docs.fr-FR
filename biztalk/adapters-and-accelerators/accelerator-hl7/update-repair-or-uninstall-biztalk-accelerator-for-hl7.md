---
title: "Mettre à jour, réparer ou désinstaller BizTalk Accelerator pour HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2fc84d2-1262-4a6e-ae9c-488a00ab4099
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b4fa1dba322e830114a76a0ca69134edbb1d06
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="update-repair-or-uninstall-biztalk-accelerator-for-hl7"></a><span data-ttu-id="44fd6-102">Mettre à jour, réparer ou désinstaller BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="44fd6-102">Update, repair, or uninstall BizTalk Accelerator for HL7</span></span>

<span data-ttu-id="44fd6-103">Modifier, réparer ou désinstaller le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44fd6-103">Change, repair or uninstall the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44fd6-104">Veillez à désinstaller [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] avant de désinstaller [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44fd6-104">Be sure to uninstall [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] before uninstalling [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]<span data-ttu-id="44fd6-105">ne peut pas être désinstallé si [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] n’est plus installé.</span><span class="sxs-lookup"><span data-stu-id="44fd6-105"> cannot be uninstalled if [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is no longer installed.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="44fd6-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="44fd6-106">Prerequisites</span></span>
* <span data-ttu-id="44fd6-107">Connectez-vous à l’aide d’un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="44fd6-107">Sign in using an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  

* <span data-ttu-id="44fd6-108">Ce compte d’utilisateur doit également être membre du groupe Administrateurs sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] qui stocke le BizTalk Accelerator pour HL7 données.</span><span class="sxs-lookup"><span data-stu-id="44fd6-108">This user account must also be a member of the Administrators group on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] that stores the BizTalk Accelerator for HL7 data.</span></span>  
    
## <a name="update-an-existing-installation"></a><span data-ttu-id="44fd6-109">Mettre à jour une installation existante</span><span class="sxs-lookup"><span data-stu-id="44fd6-109">Update an existing installation</span></span>

> [!NOTE]
>  <span data-ttu-id="44fd6-110">Lorsque vous modifiez votre installation de [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], le didacticiel de bout en bout ne s’exécute pas automatiquement.</span><span class="sxs-lookup"><span data-stu-id="44fd6-110">When you modify your installation of [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], the End-to-End Tutorial does not automatically run.</span></span> 
> 
> <span data-ttu-id="44fd6-111">Pour exécuter le didacticiel et vérifier que l’installation modifiée exécutées correctement, exécutez le didacticiel manuellement à partir de la  ***\<lecteur\>***  **\Program Files\Microsoft BizTalk \< version\> Accelerator pour le didacticiel de bout en HL7\SDK\End** dossier.</span><span class="sxs-lookup"><span data-stu-id="44fd6-111">To run the tutorial and verify that the modified installation executed correctly, run the tutorial manually from the ***\<drive\>*** **\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial** folder.</span></span>
  
1. <span data-ttu-id="44fd6-112">Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** en tant qu’administrateur</span><span class="sxs-lookup"><span data-stu-id="44fd6-112">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** as an administrator</span></span> 
  
2.  <span data-ttu-id="44fd6-113">Dans la page de bienvenue, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-113">On the welcome page, select **Next**.</span></span>  
  
3.  <span data-ttu-id="44fd6-114">Dans **Maintenance du programme**, sélectionnez **modifier**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-114">In **Program Maintenance**, select **Modify**, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="44fd6-115">Dans **installation personnalisée**, sélectionnez les fonctionnalités que vous souhaitez installer, désactivez les fonctionnalités vous ne souhaitez, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-115">In **Custom Setup**, select the features that you want to install, clear the features you don't want, and then select **Next**.</span></span>  
  
5.  <span data-ttu-id="44fd6-116">Dans la section Résumé, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-116">In the summary, select **Next**.</span></span>  
  
6.  <span data-ttu-id="44fd6-117">Sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-117">Select **Install**.</span></span>  
  
7. <span data-ttu-id="44fd6-118">Lorsque vous avez terminé, sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-118">When complete, select **Finish**.</span></span>  

## <a name="repair-an-existing-installation"></a><span data-ttu-id="44fd6-119">Réparer une installation existante</span><span class="sxs-lookup"><span data-stu-id="44fd6-119">Repair an existing installation</span></span>
<span data-ttu-id="44fd6-120">Le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] Assistant répare une installation en corrigeant les fichiers manquants ou endommagés, les raccourcis ou les entrées de Registre.</span><span class="sxs-lookup"><span data-stu-id="44fd6-120">The [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] Wizard repairs an installation by fixing missing or corrupt files, shortcuts, or registry entries.</span></span>  
  
1. <span data-ttu-id="44fd6-121">Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="44fd6-121">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] **setup.exe** as administrator.</span></span>  
  
2.  <span data-ttu-id="44fd6-122">Dans la page de bienvenue, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-122">On the welcome page, select **Next**.</span></span>  
  
3.  <span data-ttu-id="44fd6-123">Dans **Maintenance du programme**, sélectionnez **réparation**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-123">In **Program Maintenance**, select **Repair**, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="44fd6-124">Dans **compte de Service de journalisation**, entrez de nouveau le compte d’utilisateur, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-124">In **Logging Service Account**, re-enter the user account, and then select **OK**.</span></span>  
  
4.  <span data-ttu-id="44fd6-125">Si vous y êtes invité **le nom du compte a été accordé d’ouverture de session en tant que service droit**, puis sélectionnez **OK** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="44fd6-125">If prompted **The account name has been granted logon as a service right**, then select **OK** to continue.</span></span>  
  
5.  <span data-ttu-id="44fd6-126">Lorsque vous êtes prêt à réparer, sélectionnez **installer**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-126">When ready to repair, select **Install**.</span></span>  
  
6. <span data-ttu-id="44fd6-127">Lorsque terminée, sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-127">When completed, select **Finish**.</span></span> 

  
## <a name="uninstall-btahl7"></a><span data-ttu-id="44fd6-128">Désinstaller BTAHL7</span><span class="sxs-lookup"><span data-stu-id="44fd6-128">Uninstall BTAHL7</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="44fd6-129">S’il existe un emplacement de réception ou un port d’envoi à l’aide du type de transport MLLP, le programme d’installation BTAHL7 ne supprime pas l’adaptateur MLLP lors de la désinstallation de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="44fd6-129">If there is a receive location or send port using the MLLP transport type, the BTAHL7 setup does not remove the MLLP adapter during the uninstall of BTAHL7.</span></span> <span data-ttu-id="44fd6-130">Avant de désinstaller, supprimer tous les emplacements de réception ou envoient ports utilisant le transport MLLP.</span><span class="sxs-lookup"><span data-stu-id="44fd6-130">Before you uninstall, remove all receive locations or send ports using the MLLP transport.</span></span> <span data-ttu-id="44fd6-131">Ou bien, modifiez le type de transport à partir de MLLP à un autre type.</span><span class="sxs-lookup"><span data-stu-id="44fd6-131">Or, change the transport type from MLLP to another type.</span></span> <span data-ttu-id="44fd6-132">Ensuite, la désinstallation supprime l’adaptateur MLLP.</span><span class="sxs-lookup"><span data-stu-id="44fd6-132">Then, the uninstall will remove the MLLP adapter.</span></span>  
      
1.  <span data-ttu-id="44fd6-133">Ouvrez **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-133">Open **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="44fd6-134">Sélectionnez [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], puis sélectionnez **désinstallation**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-134">Select [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], and then select **Uninstall**.</span></span>  
  
4.  <span data-ttu-id="44fd6-135">Sélectionnez **Oui** si vous êtes invité à confirmer.</span><span class="sxs-lookup"><span data-stu-id="44fd6-135">Select **Yes** if asked to confirm.</span></span> 
  
5.  <span data-ttu-id="44fd6-136">Lorsque terminée, sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="44fd6-136">When completed, select **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44fd6-137">BTAHL7 ne désinstalle pas automatiquement [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artefacts et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="44fd6-137">BTAHL7 does not automatically uninstall [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artifacts and assemblies.</span></span>  
  

  
## <a name="troubleshooting-installation-issues"></a><span data-ttu-id="44fd6-138">Résolution des problèmes d’Installation</span><span class="sxs-lookup"><span data-stu-id="44fd6-138">Troubleshooting Installation Issues</span></span>  
 <span data-ttu-id="44fd6-139">Si le serveur est incapable de vérifier si l’utilisateur est un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] administrateur, désinstallation de BTAHL7 retourne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="44fd6-139">If the server is unable to validate whether the user is a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrator, uninstalling BTAHL7 returns the following error:</span></span> 
 
 `Fatal error during uninstallation`  
  
<span data-ttu-id="44fd6-140">Pour poursuivre la désinstallation, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="44fd6-140">To continue with uninstallation, do the following:</span></span>  
  
1.  <span data-ttu-id="44fd6-141">Connectez-vous au serveur en tant qu’administrateur local.</span><span class="sxs-lookup"><span data-stu-id="44fd6-141">Sign in to the server as a local administrator.</span></span>  
  
2.  <span data-ttu-id="44fd6-142">Désinstallez [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44fd6-142">Uninstall [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="44fd6-143">Désinstallez [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44fd6-143">Uninstall [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44fd6-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44fd6-144">See Also</span></span>  
[<span data-ttu-id="44fd6-145">Installer ou mettre à niveau Microsoft BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="44fd6-145">Install or upgrade Microsoft BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)