---
title: "Mise à niveau de BizTalk Accelerator pour HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91b6747f-e560-4cf8-99b5-af0d150599bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4df85c965943f2f2c916fef6b558f98caf2175f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="upgrade-biztalk-accelerator-for-hl7"></a><span data-ttu-id="305eb-102">Mise à niveau de BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="305eb-102">Upgrade BizTalk Accelerator for HL7</span></span>
<span data-ttu-id="305eb-103">Vue d’ensemble de la [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="305eb-103">Overview of the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] upgrade process.</span></span> 
  
<a name="BKMK_BeforeUpgrade"></a>   
## <a name="before-you-upgrade"></a><span data-ttu-id="305eb-104">Avant la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="305eb-104">Before you upgrade</span></span>  
  
-   <span data-ttu-id="305eb-105">L’utilisateur qui exécute la mise à niveau doit être membre du groupe Administrateurs de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="305eb-105">The user running the upgrade must be a member of the BizTalk Administrators group.</span></span>  
  
-   <span data-ttu-id="305eb-106">Le service SQL Server (MSSQLSERVER) doit être en cours d’exécution lorsque vous effectuez une mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="305eb-106">The SQL Server (MSSQLSERVER) service must be running when you perform an upgrade.</span></span>  
  
-   <span data-ttu-id="305eb-107">N’exécutez pas une installation sans assistance pour mettre à niveau.</span><span class="sxs-lookup"><span data-stu-id="305eb-107">Do not run a silent installation to upgrade.</span></span>  
  
-   <span data-ttu-id="305eb-108">Lorsque vous mettez à niveau, le programme d’installation migre existants [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] informations de configuration à une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="305eb-108">When you upgrade, the setup program migrates the existing [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] configuration information to the newer version.</span></span>  
  
-   <span data-ttu-id="305eb-109">Lorsque vous mettez à niveau, les clés de Registre et les bases de données sont automatiquement sauvegardés.</span><span class="sxs-lookup"><span data-stu-id="305eb-109">When you upgrade, the registry keys and databases are automatically backed up.</span></span>  
  
-   <span data-ttu-id="305eb-110">Les fichiers dans le  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator pour HL7 dossier sont mises à jour.</span><span class="sxs-lookup"><span data-stu-id="305eb-110">The files in the *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7 folder are updated.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="305eb-111">La mise à niveau ne crée pas un nouveau dossier pour les fichiers mis à niveau, et il modifie le nom du dossier existant.</span><span class="sxs-lookup"><span data-stu-id="305eb-111">The upgrade does not create a new folder for the upgraded files, nor does it change the name of the existing folder.</span></span>  
  
<a name="BKMK_UpgradePaths"></a>   
## <a name="supported-upgrade-paths"></a><span data-ttu-id="305eb-112">Chemins de mise à niveau pris en charge</span><span class="sxs-lookup"><span data-stu-id="305eb-112">Supported Upgrade Paths</span></span>  
 <span data-ttu-id="305eb-113">Le tableau suivant répertorie la prise en charge [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] versions qui peuvent être mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="305eb-113">The following table lists the supported [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] versions that can be upgraded.</span></span> <span data-ttu-id="305eb-114">« Oui » signifie que le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version peut être mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="305eb-114">“Yes” means the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version can be upgraded.</span></span> <span data-ttu-id="305eb-115">« Non » signifie que le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version ne peut pas être mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="305eb-115">“No” means the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version cannot be upgraded.</span></span> <span data-ttu-id="305eb-116">Si le [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version n’est pas répertoriée, cette version ne peut pas être mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="305eb-116">If the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] version is not listed, that version cannot be upgraded.</span></span>  

||[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]|[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]|<span data-ttu-id="305eb-117">BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="305eb-117">BizTalk Server 2013</span></span>|
|---|---|---|---|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="305eb-118"> 2013</span><span class="sxs-lookup"><span data-stu-id="305eb-118"> 2013</span></span>|<span data-ttu-id="305eb-119">Oui</span><span class="sxs-lookup"><span data-stu-id="305eb-119">Yes</span></span>|<span data-ttu-id="305eb-120">Oui</span><span class="sxs-lookup"><span data-stu-id="305eb-120">Yes</span></span>|<span data-ttu-id="305eb-121">Non</span><span class="sxs-lookup"><span data-stu-id="305eb-121">No</span></span>|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="305eb-122"> 2010</span><span class="sxs-lookup"><span data-stu-id="305eb-122"> 2010</span></span>|<span data-ttu-id="305eb-123">Non</span><span class="sxs-lookup"><span data-stu-id="305eb-123">No</span></span>|<span data-ttu-id="305eb-124">Oui</span><span class="sxs-lookup"><span data-stu-id="305eb-124">Yes</span></span>|<span data-ttu-id="305eb-125">Oui</span><span class="sxs-lookup"><span data-stu-id="305eb-125">Yes</span></span>|  

<a name="BKMK_UpgradeSteps"></a>   
## <a name="upgrade-steps"></a><span data-ttu-id="305eb-126">Étapes de mise à niveau</span><span class="sxs-lookup"><span data-stu-id="305eb-126">Upgrade Steps</span></span>  
  
1.  <span data-ttu-id="305eb-127">Mettre à niveau le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="305eb-127">Upgrade the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>   
  
2.  <span data-ttu-id="305eb-128">Sauvegardez le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] bases de données et votre HL7 des schémas de message.</span><span class="sxs-lookup"><span data-stu-id="305eb-128">Back up the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] databases and your HL7 message schemas.</span></span>  
  
3.  <span data-ttu-id="305eb-129">Sauvegardez tous les fichiers sous le   ***\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour HL7** dossier que vous avez modifiés.</span><span class="sxs-lookup"><span data-stu-id="305eb-129">Back up any files under the ***\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for HL7** folder that you have changed.</span></span> <span data-ttu-id="305eb-130">Par exemple, sauvegardez les fichiers dans le Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="305eb-130">For example, back up files in the SDK.</span></span>  
  
4.  <span data-ttu-id="305eb-131">Installer la mise à jour appropriée pour votre version de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="305eb-131">Install the appropriate update for your version of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]:</span></span>  
  
    -   <span data-ttu-id="305eb-132">Si la mise à niveau à partir de BTAHL7 2010, installez **HL72010Patch.msp**.</span><span class="sxs-lookup"><span data-stu-id="305eb-132">If upgrading from BTAHL7 2010, install **HL72010Patch.msp**.</span></span>  
  
    -   <span data-ttu-id="305eb-133">Si la mise à niveau à partir de BTAHL7 2013, installez **HL72013Patch.msp**.</span><span class="sxs-lookup"><span data-stu-id="305eb-133">If upgrading from BTAHL7 2013, install **HL72013Patch.msp**.</span></span>  
    
  
5.  <span data-ttu-id="305eb-134">Exécutez le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="305eb-134">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup.</span></span> <span data-ttu-id="305eb-135">Consultez [installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span><span class="sxs-lookup"><span data-stu-id="305eb-135">See [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).</span></span>  
  
6.  <span data-ttu-id="305eb-136">Déployer la nouvelle BTAHL7V2*x*projet Common.</span><span class="sxs-lookup"><span data-stu-id="305eb-136">Deploy the new BTAHL7V2*x*Common project.</span></span>  
  
7.  <span data-ttu-id="305eb-137">Redéployer tous les autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="305eb-137">Redeploy all other assemblies.</span></span>  
  
8.  <span data-ttu-id="305eb-138">Regénérez les projets ou les assemblys qui contiennent une référence à un ou plusieurs assemblys [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="305eb-138">Rebuild any projects or assemblies that have a reference to one or more of the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] assemblies.</span></span> <span data-ttu-id="305eb-139">À l’aide de **BTSTask.exe** dans \< *lecteur*\>: \Program Files\Microsoft BizTalk Server \<version\>manuellement redéployer ces projets.</span><span class="sxs-lookup"><span data-stu-id="305eb-139">Using **BTSTask.exe** in \<*drive*\>:\Program Files\Microsoft BizTalk Server \<version\>, manually redeploy these projects.</span></span>  
  
9. <span data-ttu-id="305eb-140">Redémarrez le service [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="305eb-140">Restart the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] service.</span></span>  
  
<a name="BKMK_UpgradeMulti"></a>   
## <a name="upgrading-in-a-multi-server-environment"></a><span data-ttu-id="305eb-141">La mise à niveau dans un environnement multiserveur</span><span class="sxs-lookup"><span data-stu-id="305eb-141">Upgrading in a Multi-server Environment</span></span>  
 <span data-ttu-id="305eb-142">Dans un multi-serveur [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] environnement, de mise à niveau tous les [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s et la mise à niveau puis le [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] sur tous les serveurs.</span><span class="sxs-lookup"><span data-stu-id="305eb-142">In a multi-server [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] environment, upgrade all [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s, and then upgrade the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] on all servers.</span></span> <span data-ttu-id="305eb-143">Migrez vos serveur dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="305eb-143">Migrate your servers in the following order:</span></span>  
  
-   <span data-ttu-id="305eb-144">Le serveur hébergeant le groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="305eb-144">The server hosting the BizTalk Group</span></span>  
  
-   <span data-ttu-id="305eb-145">Chaque nœud de traitement</span><span class="sxs-lookup"><span data-stu-id="305eb-145">Each processing node</span></span>  
  
-   <span data-ttu-id="305eb-146">Le serveur du portail BAM</span><span class="sxs-lookup"><span data-stu-id="305eb-146">The BAM portal server</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305eb-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="305eb-147">See Also</span></span>  
 [<span data-ttu-id="305eb-148">Installer BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="305eb-148">Install BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)