---
title: "Comment configurer le portail BAM pour travailler sur un Cluster d’équilibrage de charge réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96c04fde-dc12-42fb-9193-aa74819fe880
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73bd5013cd2a09d240fa58b7cf5283c8d1903c69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster"></a><span data-ttu-id="641aa-102">Configuration du portail BAM de sorte qu'il fonctionne dans un cluster NLB</span><span class="sxs-lookup"><span data-stu-id="641aa-102">How to Configure the BAM Portal to Work on an NLB Cluster</span></span>
<span data-ttu-id="641aa-103">Le portail BAM peut être configuré pour fonctionner dans un cluster d'équilibrage de charge réseau.</span><span class="sxs-lookup"><span data-stu-id="641aa-103">The BAM portal can be configured to work in a network load balancing (NLB) cluster.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="641aa-104">Portail BAM *uniquement* s’exécute en mode 32 bits.</span><span class="sxs-lookup"><span data-stu-id="641aa-104">BAM Portal *only* runs in 32-bit mode.</span></span> <span data-ttu-id="641aa-105">Si IIS est installé sur un ordinateur 64 bits, vérifiez qu’ASP.NET 2.0 est activé en mode 32 bits.</span><span class="sxs-lookup"><span data-stu-id="641aa-105">If IIS is installed on a 64-bit machine, then confirm ASP.NET 2.0 is enabled in 32-bit mode.</span></span> <span data-ttu-id="641aa-106">Pour ce faire, ouvrez le Gestionnaire des services Internet, ouvrez **Pool d’applications**, sélectionnez le pool d’applications (BAMAppPool), puis cliquez sur **paramètres avancés**.</span><span class="sxs-lookup"><span data-stu-id="641aa-106">To do this, open IIS Manager, open **Application Pool**, select the application pool (BAMAppPool), and then click **Advanced Settings**.</span></span> <span data-ttu-id="641aa-107">Dans **Activer les applications 32 bits**, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="641aa-107">In **Enable 32-bit applications**, select **True**.</span></span>  
>   
>  <span data-ttu-id="641aa-108">Pour les logiciels supplémentaires requis du portail BAM, consultez [planification pour le portail BAM](../core/planning-for-the-bam-portal.md).</span><span class="sxs-lookup"><span data-stu-id="641aa-108">For additional BAM Portal requirements, see [Planning for the BAM Portal](../core/planning-for-the-bam-portal.md).</span></span>  
  
### <a name="to-prepare-to-configure-bam-portal-on-an-nlb-cluster"></a><span data-ttu-id="641aa-109">Pour préparer la configuration du portail BAM dans un cluster d'équilibrage de charge réseau</span><span class="sxs-lookup"><span data-stu-id="641aa-109">To prepare to configure BAM portal on an NLB cluster</span></span>  
  
1.  <span data-ttu-id="641aa-110">Installez et configurez le portail sur le premier ordinateur.</span><span class="sxs-lookup"><span data-stu-id="641aa-110">Install and configure the portal on the first computer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-111">Configurez le portail uniquement sur le premier ordinateur.</span><span class="sxs-lookup"><span data-stu-id="641aa-111">You only configure the portal on the first computer.</span></span> <span data-ttu-id="641aa-112">Vous avez la possibilité d'activer le portail BAM sur les autres ordinateurs du cluster, mais la configuration ne doit être effectuée que sur le premier.</span><span class="sxs-lookup"><span data-stu-id="641aa-112">You have the option of enabling the BAM portal on other the other computers in the cluster, but the configuration is done only on the first computer.</span></span>  
  
2.  <span data-ttu-id="641aa-113">Installez les composants du portail sur tous les ordinateurs à inclure dans le cluster d'équilibrage de charge réseau, puis joignez les autres ordinateurs du cluster dans le groupe BizTalk de l'ordinateur sur lequel le portail est configuré.</span><span class="sxs-lookup"><span data-stu-id="641aa-113">Install the portal components on all the computers to be included in the NLB cluster, and then join the other computers in the cluster to the BizTalk group of the computer on which the portal is configured.</span></span> <span data-ttu-id="641aa-114">Vous devez activer les groupes BizTalk et joindre le groupe approprié.</span><span class="sxs-lookup"><span data-stu-id="641aa-114">You must enable the BizTalk groups and join the appropriate group.</span></span>  
  
3.  <span data-ttu-id="641aa-115">Sélectionnez la base de données de gestion BizTalk configurée pour l'ordinateur sur lequel le portail est installé.</span><span class="sxs-lookup"><span data-stu-id="641aa-115">Select the BizTalk Management database configured for the computer on which the portal is installed.</span></span>  
  
4.  <span data-ttu-id="641aa-116">Créez le cluster d'équilibrage de charge réseau.</span><span class="sxs-lookup"><span data-stu-id="641aa-116">Create the NLB cluster.</span></span> <span data-ttu-id="641aa-117">Pour plus d’informations sur la façon de créer et gérer des clusters d’équilibrage de la charge réseau, consultez « Créer et gérer charger Clusters d’équilibrage réseau » à [http://go.microsoft.com/fwlink/?LinkId=56206](http://go.microsoft.com/fwlink/?LinkId=56206).</span><span class="sxs-lookup"><span data-stu-id="641aa-117">For more information about how to create and manage network load balancing clusters, see "Create and Manage Network Load Balancing Clusters" at [http://go.microsoft.com/fwlink/?LinkId=56206](http://go.microsoft.com/fwlink/?LinkId=56206).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-118">Vous devez vérifier que le cluster d'équilibrage de charge réseau fonctionne correctement hors du contexte de BizTalk Server avant de poursuivre.</span><span class="sxs-lookup"><span data-stu-id="641aa-118">You should confirm that your NLB cluster is working properly outside of the BizTalk Server context before continuing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-119">Pour configurer l'équilibrage de la charge réseau au niveau du matériel, consultez la documentation de votre fournisseur de matériel.</span><span class="sxs-lookup"><span data-stu-id="641aa-119">To set up hardware-based NLB, refer to your hardware provider's documentation.</span></span>  
  
### <a name="to-update-the-bam-configuration-to-reflect-the-location-of-the-cluster"></a><span data-ttu-id="641aa-120">Pour mettre à jour la configuration de l'analyse BAM afin de prendre en compte l'emplacement du cluster</span><span class="sxs-lookup"><span data-stu-id="641aa-120">To update the BAM configuration to reflect the location of the cluster</span></span>  
  
1.  <span data-ttu-id="641aa-121">Utilisez l'utilitaire de gestion de l'analyse BAM pour obtenir la configuration BAM actuelle.</span><span class="sxs-lookup"><span data-stu-id="641aa-121">Use the BAM Management Utility to get the current BAM configuration.</span></span> <span data-ttu-id="641aa-122">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**et le type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm get-config-filename : myconfig.Xml.</span><span class="sxs-lookup"><span data-stu-id="641aa-122">To do this, click **Start**, click **Run**, and type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm get-config -FileName:MyConfig.xml.</span></span>  
  
2.  <span data-ttu-id="641aa-123">Remplacez le nom de l'hôte local par celui du cluster d'équilibrage de charge réseau.</span><span class="sxs-lookup"><span data-stu-id="641aa-123">Replace the local host name with the name of the NLB cluster.</span></span> <span data-ttu-id="641aa-124">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\myconfig.Xml.</span><span class="sxs-lookup"><span data-stu-id="641aa-124">To do this, click **Start**, click **Run**, and type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\MyConfig.xml.</span></span>  
  
3.  <span data-ttu-id="641aa-125">Pour l'équilibrage de la charge réseau au niveau du matériel uniquement, vérifiez que le fichier de configuration est paramétré comme suit :</span><span class="sxs-lookup"><span data-stu-id="641aa-125">For hardware-based NLB only, verify the configuration file has the following:</span></span>  
  
    ```  
    <GlobalProperty Name="BAMVRoot">  
    http://<NLB IP Address>:portname/BAM</GlobalProperty>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-126">Les étapes 4 et 5 sont facultatives lors de la mise à jour de la configuration BAM avec l'équilibrage de la charge réseau au niveau du matériel.</span><span class="sxs-lookup"><span data-stu-id="641aa-126">Steps 4 and 5 are not necessary when updating the BAM configuration on hardware-based NLB.</span></span>  
  
4.  <span data-ttu-id="641aa-127">Modifiez la ligne suivante pour la faire pointer vers le cluster d'équilibrage de charge réseau en remplaçant le nom de l'ordinateur (machinename) par celui du cluster :</span><span class="sxs-lookup"><span data-stu-id="641aa-127">Modify the following line to point to the NLB cluster by replacing the computer name (machinename) with the cluster name:</span></span>  
  
    ```  
    <GlobalProperty Name=" BAMVRoot">  http://machinename:portname/BAM  
    </GlobalProperty>   
    ```  
  
5.  <span data-ttu-id="641aa-128">Enregistrez la nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="641aa-128">Save the new configuration.</span></span> <span data-ttu-id="641aa-129">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**et le type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm update-config-filename : myconfig.Xml.</span><span class="sxs-lookup"><span data-stu-id="641aa-129">To do this, click **Start**, click **Run**, and type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm update-config -FileName:MyConfig.xml.</span></span>  
  
### <a name="to-edit-the-bam-portal-webconfig-file-to-change-the-bammanagementservice-and-queryservice-urls-to-point-to-the-nlb-server-name-note-this-procedure-is-not-necessary-for-hardware-based-nlb"></a><span data-ttu-id="641aa-130">Pour modifier le fichier web.config du portail BAM afin que les URL de BAMmanagementService et de QueryService pointent vers le nom du serveur d'équilibrage de charge réseau.</span><span class="sxs-lookup"><span data-stu-id="641aa-130">To edit the BAM portal web.config file to change the BAMmanagementService and QueryService URLs to point to the NLB server name.</span></span> <span data-ttu-id="641aa-131">Remarque : Cette procédure n’est pas nécessaire pour l’équilibrage de charge basé sur le matériel réseau.</span><span class="sxs-lookup"><span data-stu-id="641aa-131">Note: This procedure is not necessary for hardware-based NLB.</span></span>  
  
1.  <span data-ttu-id="641aa-132">Ouvrez le fichier web.config à l’aide du bloc-notes en cliquant sur **Démarrer**, puis sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, puis en cliquant sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="641aa-132">Open the web.config file using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="641aa-133">Modifiez le nom de l'ordinateur (machinename) et celui du port dans les deux lignes suivantes pour qu'ils pointent vers le nom du cluster :</span><span class="sxs-lookup"><span data-stu-id="641aa-133">Modify the following computer name (machinename) and the port name in the following two lines to point to the name of name of the cluster:</span></span>  
  
    ```  
    <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
    <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />   
    ```  
  
3.  <span data-ttu-id="641aa-134">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="641aa-134">Save the file.</span></span> <span data-ttu-id="641aa-135">Pour ce faire, cliquez sur **fichier**, puis cliquez sur **enregistrer** dans la barre de menus du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="641aa-135">To do this, click **File**, and then click **Save** on the Notepad menu bar.</span></span>  
  
### <a name="to-configure-each-additional-computer-in-the-cluster"></a><span data-ttu-id="641aa-136">Pour configurer les ordinateurs supplémentaires dans le cluster</span><span class="sxs-lookup"><span data-stu-id="641aa-136">To configure each additional computer in the cluster</span></span>  
  
1.  <span data-ttu-id="641aa-137">Copiez le fichier web.config dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal de chaque ordinateur du cluster.</span><span class="sxs-lookup"><span data-stu-id="641aa-137">Copy the web.config file to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal folder on each additional computer in the cluster.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-138">Dans les étapes suivantes toutes les références à la **Program Files** sera **Program Files (x86)** pour les ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="641aa-138">In the following steps all references to the **Program Files** folder will be **Program Files (x86)** for 64 bit computers.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="641aa-139">Dans les étapes suivantes, lorsque vous créez les répertoires virtuels, assurez-vous qu'ils possèdent les mêmes paramètres que les trois répertoires virtuels BAM créés par la configuration de BizTalk Server sur le premier ordinateur.</span><span class="sxs-lookup"><span data-stu-id="641aa-139">In the following steps, when you are creating the virtual directories, check to make sure they have the exact settings as the three BAM virtual directories created by the BizTalk Server Configuration on first computer.</span></span> <span data-ttu-id="641aa-140">Confirmez les chemins d'accès, la version ASP.NET, les autorisations sur les répertoires et le pool d'applications.</span><span class="sxs-lookup"><span data-stu-id="641aa-140">Confirm your file paths, the ASP.NET version, your directory permissions, and application pool.</span></span>  <span data-ttu-id="641aa-141">Pour exécuter BAMAppPool sur l'ordinateur que vous configurez, utilisez le même compte de service de domaine que celui utilisé lors de la configuration du premier ordinateur.</span><span class="sxs-lookup"><span data-stu-id="641aa-141">Use the same domain service account to run the BAMAppPool on the computer you are setting up as you used when setting up the first computer.</span></span> <span data-ttu-id="641aa-142">Vérifiez que BAMAppPool est exécuté sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="641aa-142">Make sure the BAMAppPool is running on all of the computers.</span></span> <span data-ttu-id="641aa-143">Vous devez copier deux fichiers web.config.</span><span class="sxs-lookup"><span data-stu-id="641aa-143">There are two web.config files you must copy.</span></span>  
    >   
    >  <span data-ttu-id="641aa-144">Outre le fichier web.config enregistré dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal, vous devez copier les fichiers web.config se trouvant dans les dossiers [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService et [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMQueryService dans les mêmes dossiers sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="641aa-144">In addition to the web.config file [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal, you must copy the web.config file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService and [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMQueryService to the same folders on this computer.</span></span>  
  
2.  <span data-ttu-id="641aa-145">Pour l'équilibrage de la charge réseau au niveau du matériel uniquement, modifiez le nom de l'ordinateur (machinename) et celui du port dans les deux lignes suivantes pour qu'ils pointent vers le nom du cluster :</span><span class="sxs-lookup"><span data-stu-id="641aa-145">For hardware-based NLB only, modify the following computer name (machinename) and the port name in the following two lines to point to the name of name of the cluster:</span></span>  
  
    ```  
    <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
    <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />  
    ```  
  
3.  <span data-ttu-id="641aa-146">Créer un pool d’applications appelé BAMAppPool.</span><span class="sxs-lookup"><span data-stu-id="641aa-146">Create an application pool called BAMAppPool.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-147">Le chemin d’accès de répertoire pour les répertoires virtuels doit être % InstallationFolder%/BamPortal, % InstallationFolder%/BamPortal/BAMManagementService et % InstallationFolder%/BamPortal/BAMQueryService.</span><span class="sxs-lookup"><span data-stu-id="641aa-147">The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService, and %InstallationFolder%/BamPortal/BAMQueryService.</span></span>  
  
4.  <span data-ttu-id="641aa-148">Créez un répertoire virtuel appelé BAM sous le site Web par défaut.</span><span class="sxs-lookup"><span data-stu-id="641aa-148">Create a virtual directory under the Default Website called BAM.</span></span>  
  
5.  <span data-ttu-id="641aa-149">Remplacez le pool d'applications du répertoire virtuel BAM par le pool BAMAppPool.</span><span class="sxs-lookup"><span data-stu-id="641aa-149">Change the application pool of BAM virtual directory to BAMAppPool.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-150">Le chemin d'accès aux répertoires virtuels doit être le suivant : %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService et %InstallationFolder%/BamPortal/BAMQueryService.</span><span class="sxs-lookup"><span data-stu-id="641aa-150">The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService and %InstallationFolder%/BamPortal/BAMQueryService.</span></span>  
  
6.  <span data-ttu-id="641aa-151">Créez un répertoire virtuel appelé BAMManagementService sous BAM.</span><span class="sxs-lookup"><span data-stu-id="641aa-151">Create a virtual directory called BAMManagementService under BAM.</span></span>  
  
7.  <span data-ttu-id="641aa-152">Remplacez le pool d'applications de BAMManagementService par le pool BAMAppPool.</span><span class="sxs-lookup"><span data-stu-id="641aa-152">Change the application pool of BAMManagementService to BAMAppPool.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-153">Le chemin d’accès de répertoire pour les répertoires virtuels doit être % InstallationFolder%/BamPortal, % InstallationFolder%/BamPortal/BAMManagementService et % InstallationFolder%/BamPortal/BAMQueryService.</span><span class="sxs-lookup"><span data-stu-id="641aa-153">The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService, and %InstallationFolder%/BamPortal/BAMQueryService.</span></span>  
  
8.  <span data-ttu-id="641aa-154">Créez un répertoire virtuel appelé BAMQueryService sous BAM.</span><span class="sxs-lookup"><span data-stu-id="641aa-154">Create a virtual directory called BAMQueryService under BAM.</span></span>  
  
9. <span data-ttu-id="641aa-155">Remplacez le pool d'applications de BAMQueryService par le pool BAMAppPool.</span><span class="sxs-lookup"><span data-stu-id="641aa-155">Change the application pool of BAMQueryService to BAMAppPool.</span></span>  
  
10. <span data-ttu-id="641aa-156">Pour modifier la version de l’analyse BAM, BAMMANAGEMENTSERVICE et BAMQUERYSERVICE définir la version des Applications pour .NET Framework 4, utilisez le INETMGR, situé sur l’onglet Propriétés ASP, du répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="641aa-156">Use the INETMGR, located on the virtual directory Properites ASP NET Tab, to change the version for BAM, BAMMANAGEMENTSERVICE, and BAMQUERYSERVICE to set the version of the Applications to .NET Framework 4.</span></span>  
  
11. <span data-ttu-id="641aa-157">Exécutez aspnet_setreg.exe -k:"SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\identity" -u:BAMWebServiceAccount -p:Password.</span><span class="sxs-lookup"><span data-stu-id="641aa-157">Run aspnet_setreg.exe -k:"SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\identity" -u:BAMWebServiceAccount  -p:Password.</span></span>  <span data-ttu-id="641aa-158">Le compte spécifié ici est le compte d'utilisateur de service Web de gestion BAM.</span><span class="sxs-lookup"><span data-stu-id="641aa-158">The account specified here is the BAM Management Web Service User account.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="641aa-159">Portail BAM *uniquement* s’exécute en mode 32 bits.</span><span class="sxs-lookup"><span data-stu-id="641aa-159">BAM Portal *only* runs in 32-bit mode.</span></span> <span data-ttu-id="641aa-160">Si IIS est installé sur un ordinateur 64 bits, ASP.NET 2.0 doit être activé en mode 32 bits.</span><span class="sxs-lookup"><span data-stu-id="641aa-160">If IIS is installed on a 64-bit machine, ASP.NET 2.0 must be enabled in 32-bit mode.</span></span> <span data-ttu-id="641aa-161">Pour ce faire, ouvrez le Gestionnaire des services Internet, ouvrez **Pool d’applications**, sélectionnez le pool d’applications (BAMAppPool), puis cliquez sur **paramètres avancés**.</span><span class="sxs-lookup"><span data-stu-id="641aa-161">To do this, open IIS Manager, open **Application Pool**, select the application pool (BAMAppPool), and then click **Advanced Settings**.</span></span> <span data-ttu-id="641aa-162">Dans **Activer les applications 32 bits**, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="641aa-162">In **Enable 32-bit applications**, select **True**.</span></span>  
    >   
    >  <span data-ttu-id="641aa-163">[Planification pour le portail BAM](../core/planning-for-the-bam-portal.md) répertorie les considérations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="641aa-163">[Planning for the BAM Portal](../core/planning-for-the-bam-portal.md) lists additional requirements.</span></span>  
  
12. <span data-ttu-id="641aa-164">Définissez les listes de contrôle d'accès (ACL) en lecture pour les utilisateurs AppPool sur WebServices en exécutant SubInACL (outil de ligne de commande permettant aux administrateurs d'obtenir des informations de sécurité sur des fichiers), des clés de Registre et des services, et de transmettre ces informations d'un utilisateur à l'autre, d'un groupe local ou global à l'autre ou d'un domaine à l'autre.</span><span class="sxs-lookup"><span data-stu-id="641aa-164">Set the read ACLs for the AppPool user on WebServices by running SubInACL, a command-line tool that enables administrators to obtain security information about files, registry keys, and services, and to transfer this information from user to user, from local or global group to group, and from domain to domain.</span></span>  
  
13. <span data-ttu-id="641aa-165">Télécharger l’outil SubInAcl à [http://go.microsoft.com/fwlink/?LinkId=61990](http://go.microsoft.com/fwlink/?LinkId=61990).</span><span class="sxs-lookup"><span data-stu-id="641aa-165">Download SubInAcl from [http://go.microsoft.com/fwlink/?LinkId=61990](http://go.microsoft.com/fwlink/?LinkId=61990).</span></span>  
  
14. <span data-ttu-id="641aa-166">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="641aa-166">Open a command prompt.</span></span> <span data-ttu-id="641aa-167">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="641aa-167">To do this, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
15. <span data-ttu-id="641aa-168">Tapez la commande suivante à l’invite de commandes : subinacl.exe /subkeyreg « HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices » « / accorder = Service réseau = R »</span><span class="sxs-lookup"><span data-stu-id="641aa-168">Type the following at the command prompt: subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices" "/grant=Network Service=R"</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-169">L’objectif de cette commande doit accorder le Pool d’applications BAM utilisateur un accès en lecture à la clé de Registre SOFTWAREMicrosoftBizTalk Server3.0BAMWebServicesidentity.</span><span class="sxs-lookup"><span data-stu-id="641aa-169">The purpose of this command is to grant the BAM Application Pool user read access to the SOFTWAREMicrosoftBizTalk Server3.0BAMWebServicesidentity registry key.</span></span> <span data-ttu-id="641aa-170">Cet exemple utilise le pool « Network Service » puisqu'il s'agit du pool utilisé par défaut par IIS.</span><span class="sxs-lookup"><span data-stu-id="641aa-170">The example uses Network Service since it is the default used by IIS for Application Pool.</span></span> <span data-ttu-id="641aa-171">Si vous n'employez pas les paramètres IIS par défaut, vous devez vous servir de l'utilisateur du pool d'applications que votre déploiement utilise.</span><span class="sxs-lookup"><span data-stu-id="641aa-171">If you do not use the default IIS settings, you should substitute the application pool user that your deployment uses.</span></span>  
  
16. <span data-ttu-id="641aa-172">Tapez la commande suivante à l’invite de commandes : subinacl.exe /keyreg « HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3. 0 » « / accorder =\<BAM WebService Account > »</span><span class="sxs-lookup"><span data-stu-id="641aa-172">Type the following at the command prompt: subinacl.exe /keyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0" "/grant=\<BAM WebService Account>”</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-173">L'objet de cette commande est d'accorder à l'utilisateur du service Web de gestion BAM un accès en lecture de la clé de Registre SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\Identity.</span><span class="sxs-lookup"><span data-stu-id="641aa-173">The purpose of this command is to grant the BAM Management Web Service User account read access to the SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\Identity registry key.</span></span>  
  
17. <span data-ttu-id="641aa-174">Vérifiez que l'identité sous laquelle le pool d'applications BAM et le service Web de gestion BAM sont exécutés dispose d'un accès en lecture à la clé ASPNET_SETREG.</span><span class="sxs-lookup"><span data-stu-id="641aa-174">Verify that the identity that the application pool that the BAMManagement Web service runs under has read access to the ASPNET_SETREG key.</span></span>  
  
18. <span data-ttu-id="641aa-175">Utilisez l'outil d'administration de la console Gestion de l'ordinateur pour ajouter l'utilisateur du service Web de gestion BAM et le compte de l'utilisateur du pool d'applications BAM au groupe Internet Information Services Worker Process (IIS_WPG) et au groupe SharePoint Services (STS_WPG).</span><span class="sxs-lookup"><span data-stu-id="641aa-175">Use the Computer Management administrator tool to add the BAM Management Web service user and the BAM application pool user account to the IIS Worker Process Group (IIS_WPG) and SharePoint services group (STS_WPG).</span></span>  
  
19. <span data-ttu-id="641aa-176">Définir les autorisations sur les dossiers temporaires ASP.NET pour le pool d’applications et les utilisateurs du service Web : c:\windows\system32\cacls « %windir%\Microsoft.NET\Framework\ v2.0. \<numéro de version > \Temporary ASP.NET Files » /T /E /G \<BAM WebService Account > : F</span><span class="sxs-lookup"><span data-stu-id="641aa-176">Set the permissions on the temporary ASP.NET folders for the applications pool and Web service users: c:\windows\system32\cacls "%windir%\Microsoft.NET\Framework\ v2.0.\<min version number>\Temporary ASP.NET Files" /T /E /G \<BAM WebService Account>:F</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="641aa-177">Vous devez accorder l'accès à la fois au compte d'utilisateur de service Web de gestion BAM et au compte d'utilisateur du pool d'applications BAM.</span><span class="sxs-lookup"><span data-stu-id="641aa-177">You grant access to both the BAM Management Web Service User account and the BAM App Pool User account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="641aa-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="641aa-178">See Also</span></span>  
 [<span data-ttu-id="641aa-179">Gestion du portail BAM</span><span class="sxs-lookup"><span data-stu-id="641aa-179">Managing the BAM Portal</span></span>](../core/managing-the-bam-portal.md)