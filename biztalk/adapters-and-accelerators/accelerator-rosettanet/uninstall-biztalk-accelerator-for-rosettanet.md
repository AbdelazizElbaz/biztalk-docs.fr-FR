---
title: "Désinstallez l’accélérateur BizTalk RosettaNet (BTARN) sur le serveur BizTalk | Documents Microsoft »"
description: "Annuler le déploiement des artefacts et annuler la configuration de BTARN pour supprimer l’accélérateur BizTalk Server"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 8d289a3705eb0c127dc4d2637c2d6ffd3c122b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="uninstall-the-rosettanet-accelerator"></a><span data-ttu-id="3ec87-103">Désinstallez l’accélérateur RosettaNet</span><span class="sxs-lookup"><span data-stu-id="3ec87-103">Uninstall the RosettaNet accelerator</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="3ec87-104">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="3ec87-104">Before you begin</span></span>
  
* <span data-ttu-id="3ec87-105">Si vous n’exécutez **Setup.exe**, le processus de désinstallation ne supprime pas les artefacts de l’analyse BAM (Business Activity), les artefacts BizTalk, les répertoires virtuels Internet Information Services (IIS) et pools d’applications.</span><span class="sxs-lookup"><span data-stu-id="3ec87-105">If you only run **Setup.exe**, the uninstall process does not remove the Business Activity Monitoring (BAM) artifacts, the BizTalk artifacts, Internet Information Services (IIS) virtual directories, and application pools.</span></span>  
  
* <span data-ttu-id="3ec87-106">Si vous avez utilisé le **bouclage** utilitaire permettant de créer des accords miroirs pour un déploiement sur un seul ordinateur, puis exécutez l’outil avec la **/désactiver <** **organisation d’accueil**  **>**  option avant de supprimer les partenaires dans le **Console d’Administration BTARN**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-106">If you used the **Loopback** utility to create mirror agreements for a single-computer deployment, then run the tool with the **/disable <** **home organization** **>** option before deleting the partners in the **BTARN Administration Console**.</span></span>  
  
* <span data-ttu-id="3ec87-107">Si ce serveur fait partie d’un déploiement sur plusieurs ordinateurs, n’exécutez pas le **BtarnClean** utilitaire ou annuler manuellement le déploiement d’assemblys BTARN.</span><span class="sxs-lookup"><span data-stu-id="3ec87-107">If this server is part of a multi-computer deployment, do not run the **BtarnClean** utility or manually undeploy the BTARN assemblies.</span></span> <span data-ttu-id="3ec87-108">La suppression des artéfacts sur un ordinateur d’arrête la fonctionnalité des autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="3ec87-108">Removing the artifacts on one computer breaks the functionality of the other computers.</span></span>  <span data-ttu-id="3ec87-109">Si vous souhaitez désinstaller BTARN sur tous les serveurs, puis exécutez le **BtarnClean** utilitaire.</span><span class="sxs-lookup"><span data-stu-id="3ec87-109">If you want to uninstall BTARN from all the servers, then run the **BtarnClean** utility.</span></span> 

  
## <a name="undeploy-the-artifacts"></a><span data-ttu-id="3ec87-110">Annuler le déploiement des artefacts</span><span class="sxs-lookup"><span data-stu-id="3ec87-110">Undeploy the artifacts</span></span>  

<span data-ttu-id="3ec87-111">Nous vous recommandons de sauvegarder des vos artefacts BAM avant l’annulation du déploiement.</span><span class="sxs-lookup"><span data-stu-id="3ec87-111">We recommend backing up your BAM artifacts before undeploying.</span></span> 

1. <span data-ttu-id="3ec87-112">Annuler le déploiement des artéfacts BAM que vous avez déployé :</span><span class="sxs-lookup"><span data-stu-id="3ec87-112">Undeploy all the BAM artifacts that you deployed:</span></span>  
  
    1.  <span data-ttu-id="3ec87-113">À l’invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3ec87-113">At the command prompt, run the following command:</span></span>  
  
         ```cd %ProgramFiles%\\<BizTalk Server installation directory\>\Tracking```
  
    2.  <span data-ttu-id="3ec87-114">À l'invite de commande où l'interface utilisateur de suivi était installée, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3ec87-114">At the command prompt where the tracking UI was installed, run the following command:</span></span>  
  
         ```bm remove-all DefinitionFile:"%ProgramFiles%\\<installation directory\>\BAMTracking\tracking.xml"```
  
        > [!NOTE]
        >  <span data-ttu-id="3ec87-115">Pour plus d’informations sur BAM, consultez [la gestion de l’analyse BAM](../../core/managing-bam.md)</span><span class="sxs-lookup"><span data-stu-id="3ec87-115">For more information about BAM, see [Managing Business Activity Monitoring](../../core/managing-bam.md)</span></span> 
  
2.  <span data-ttu-id="3ec87-116">Sauvegardez et supprimez tous les contrats, les partenaires et les organisations de base à partir de la Console de gestion BTARN.</span><span class="sxs-lookup"><span data-stu-id="3ec87-116">Backup and delete all the agreements, partners, and home organizations from the BTARN Management Console.</span></span> <span data-ttu-id="3ec87-117">Consultez la rubrique « Gestion de la Configuration BTARN » (dans le nœud des opérations de l’aide sur BTARN) pour plus d’informations sur l’utilisation de la **BtarnConfig** utilitaire pour sauvegarder les accords et les partenaires.</span><span class="sxs-lookup"><span data-stu-id="3ec87-117">See the "Administering the BTARN Configuration" topic (in the Operations node of BTARN Help) for information about using the **BtarnConfig** utility to back up the agreements and partners.</span></span>  
  
    > [!NOTE]
    >  * <span data-ttu-id="3ec87-118">Arrêter et annuler le déploiement des artefacts BizTalk créés par BTARN à l’aide de la [BtarnClean](btarnclean.md) utilitaire.</span><span class="sxs-lookup"><span data-stu-id="3ec87-118">Stop and undeploy the BizTalk artifacts created by BTARN by using the [BtarnClean](btarnclean.md) utility.</span></span>
    >  * <span data-ttu-id="3ec87-119">Supprimer les artéfacts supplémentaires que vous avez déployé.</span><span class="sxs-lookup"><span data-stu-id="3ec87-119">Remove any additional artifacts that you deployed.</span></span> <span data-ttu-id="3ec87-120">Consultez [annulation du déploiement des Applications BizTalk](../../core/undeploying-biztalk-applications.md) .</span><span class="sxs-lookup"><span data-stu-id="3ec87-120">See [Undeploying BizTalk Applications](../../core/undeploying-biztalk-applications.md) .</span></span>
  
3.  <span data-ttu-id="3ec87-121">À partir de l’installation de BTARN, recherchez le dossier MSI\Program Files\Microsoft BizTalk Accelerator pour RosettaNet\SDK dossier.</span><span class="sxs-lookup"><span data-stu-id="3ec87-121">From the BTARN Setup, locate the MSI\Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK folder.</span></span> <span data-ttu-id="3ec87-122">Dans le dossier SDK, double-cliquez sur **BTARNClean.exe**, puis sélectionnez **Y** à se poursuivre, ou **N** pour annuler l’exécution de l’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="3ec87-122">In the SDK folder, double-click **BTARNClean.exe**, and then select **Y** to continue, or **N** to cancel running the utility.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ec87-123">Si votre serveur fait partie d’un scénario de déploiement de plusieurs ordinateurs, vous pouvez ignorer l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="3ec87-123">If your server is part of a multi-computer deployment scenario, you can skip step 3.</span></span> <span data-ttu-id="3ec87-124">Annulation du déploiement de toutes les ressources partagées, la fonctionnalité s’arrête sur les autres serveurs dans le déploiement.</span><span class="sxs-lookup"><span data-stu-id="3ec87-124">Undeploying any shared resources breaks the functionality on the other servers in the deployment.</span></span>  
  
4.  <span data-ttu-id="3ec87-125">Annulez le déploiement d'éventuels assemblys que vous aviez créés et déployés.</span><span class="sxs-lookup"><span data-stu-id="3ec87-125">Undeploy any custom assemblies that you created and deployed.</span></span>  
  
5.  <span data-ttu-id="3ec87-126">À l’invite de commandes, accédez à \Program Files\Microsoft BizTalk Server <your version>\Tracking.</span><span class="sxs-lookup"><span data-stu-id="3ec87-126">At the command prompt, go to \Program Files\Microsoft BizTalk Server <your version>\Tracking.</span></span> <span data-ttu-id="3ec87-127">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3ec87-127">Run the following command:</span></span> 

    ```BM UNDEPLOY ALL <drive\>:\Program Files\\<installation directory\>\BAMTracking\tracking.xml```
  
## <a name="unconfigure-btarn"></a><span data-ttu-id="3ec87-128">Annuler la configuration de BTARN</span><span class="sxs-lookup"><span data-stu-id="3ec87-128">Unconfigure BTARN</span></span>
  
1.  <span data-ttu-id="3ec87-129">Recherchez et exécutez ce qui suit pour annuler la configuration de BTARN :</span><span class="sxs-lookup"><span data-stu-id="3ec87-129">Locate and run the following to unconfigure BTARN:</span></span>  
  
     <span data-ttu-id="3ec87-130">***< lecteur\>*****: \Program Files\\< répertoire d’installation\>\Configuration.exe /u** </span><span class="sxs-lookup"><span data-stu-id="3ec87-130">***<drive\>***  **:\Program Files\\<installation directory\>\Configuration.exe /u**</span></span>  
  
2.  <span data-ttu-id="3ec87-131">Dans le panneau de configuration, double-cliquez sur **Ajout / Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-131">In Control Panel, double-click **Add or Remove Programs**.</span></span>  
  
3.  <span data-ttu-id="3ec87-132">Dans le **programmes actuellement installés** , cliquez sur **Microsoft BizTalk Accelerator for RosettaNet**, puis cliquez sur **modifier/supprimer**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-132">In the **Currently installed programs** list, click **Microsoft BizTalk Accelerator for RosettaNet**, and then click **Change/Remove**.</span></span>  
  
4.  <span data-ttu-id="3ec87-133">Dans le **Maintenance du programme** boîte de dialogue, sélectionnez **supprimer**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-133">In the **Program Maintenance** dialog box, select **Remove**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="3ec87-134">Dans le **Résumé** boîte de dialogue, cliquez sur **désinstallation**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-134">In the **Summary** dialog box, click **Uninstall**.</span></span>  
  
6.  <span data-ttu-id="3ec87-135">Dans le **désinstallation terminée** boîte de dialogue, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-135">In the **Uninstall Completed** dialog box, click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ec87-136">Le processus de désinstallation ne supprime pas les bases de données BTARN (BTARNARCHIVE, BTARNCONFIG et BTARNDATA).</span><span class="sxs-lookup"><span data-stu-id="3ec87-136">The uninstallation process does not remove the BTARN databases (BTARNARCHIVE, BTARNCONFIG, and BTARNDATA).</span></span> <span data-ttu-id="3ec87-137">Vous devez les supprimer manuellement.</span><span class="sxs-lookup"><span data-stu-id="3ec87-137">You must manually remove them.</span></span>  
  
7.  <span data-ttu-id="3ec87-138">Ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-138">Open **SQL Server Management Studio**.</span></span>  
  
8.  <span data-ttu-id="3ec87-139">Dans le **se connecter au serveur** boîte de dialogue, cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-139">In the **Connect to Server** dialog box, click **Connect**.</span></span>  
  
9. <span data-ttu-id="3ec87-140">Développez le **bases de données** nœud dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="3ec87-140">Expand the **Databases** node in the left pane.</span></span> <span data-ttu-id="3ec87-141">Cliquez sur une des bases de données BTARN, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-141">Right-click one of the BTARN databases, and then click **Delete**.</span></span>  
  
10. <span data-ttu-id="3ec87-142">Dans le **supprimer un objet** boîte de dialogue, sélectionnez **fermer les connexions existantes**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ec87-142">In the **Delete Object** dialog box, select **Close Existing Connections**, and then click **OK**.</span></span>  
  
