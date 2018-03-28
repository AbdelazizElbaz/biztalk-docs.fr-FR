---
title: Résoudre les problèmes et les problèmes connus avec l’accélérateur BizTalk du RosettaNet (BTARN) installé sur BizTalk Server | Documents Microsoft »
description: Recommandations pour l’installation de SQL, le compte de service pour les instances d’hôte et les erreurs connues avec l’installation de BTARN dans BizTalk Server
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdca89c1a7a4ed3834103776f9f28c8631c5de0a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-the-installation-and-see-the-known-install-issues"></a><span data-ttu-id="df1eb-103">Résoudre les problèmes de l’installation et de voir les problèmes d’installation connus</span><span class="sxs-lookup"><span data-stu-id="df1eb-103">Troubleshoot the installation and see the known install issues</span></span>

  
## <a name="do-not-install-sql-server-on-the-domain-controller-computer"></a><span data-ttu-id="df1eb-104">N'installez pas SQL Server sur l'ordinateur du contrôleur de domaine</span><span class="sxs-lookup"><span data-stu-id="df1eb-104">Do not install SQL Server on the domain controller computer</span></span>  
 <span data-ttu-id="df1eb-105">Si vous installez SQL Server sur le même ordinateur que votre ordinateur de contrôleur de domaine, il retourne le message d’erreur suivant quand il tente de créer les ports d’envoi SQL :</span><span class="sxs-lookup"><span data-stu-id="df1eb-105">If you install SQL Server on the same computer as your domain controller computer, it returns the following error message when it is trying to create the SQL send ports:</span></span>  
  
```
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500.  
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500  

```
  
> [!IMPORTANT]
>  <span data-ttu-id="df1eb-106">N’installez pas SQL Server sur l’ordinateur de contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="df1eb-106">Do not install SQL Server on the domain controller computer.</span></span>  
  
## <a name="service-account-for-the-application-pools-must-be-the-same-as-the-service-account-for-the-isolated-host-and-host-instances"></a><span data-ttu-id="df1eb-107">Le compte de service pour les pools d'applications doit être le même que le compte de service pour les instances de l'hôte et de l'hôte isolé</span><span class="sxs-lookup"><span data-stu-id="df1eb-107">Service account for the application pools must be the same as the service account for the Isolated Host and Host instances</span></span>  
 <span data-ttu-id="df1eb-108">Si le compte de service défini pour les pools d’applications BTARN est différent du compte de l’hôte isolé, BTARN ne traite pas correctement les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="df1eb-108">If the service account set for the BTARN application pools is different from the Isolated Host account, BTARN does not process incoming messages correctly.</span></span> <span data-ttu-id="df1eb-109">Lorsque la page .aspx de réception appelle le pipeline, le pipeline n’a pas accès aux certificats appropriés.</span><span class="sxs-lookup"><span data-stu-id="df1eb-109">When the receive .aspx page calls the pipeline, the pipeline does not have access to the appropriate certificates.</span></span> <span data-ttu-id="df1eb-110">Par conséquent, il ne déchiffrer le message entrant ni valider la signature.</span><span class="sxs-lookup"><span data-stu-id="df1eb-110">Therefore, it does not decrypt the incoming message or validate the signature.</span></span> <span data-ttu-id="df1eb-111">En outre, il ne pourrez pas accéder à la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="df1eb-111">Also, it won't be able to access the MessageBox database.</span></span>  
  

## <a name="known-install-issues"></a><span data-ttu-id="df1eb-112">Problèmes d’installation connus</span><span class="sxs-lookup"><span data-stu-id="df1eb-112">Known install issues</span></span>

  
### <a name="btarn-http-front-end-feature-configuration-fails"></a><span data-ttu-id="df1eb-113">Échec de la configuration de la fonctionnalité de fin avant de BTARN HTTP</span><span class="sxs-lookup"><span data-stu-id="df1eb-113">BTARN HTTP Front End Feature configuration fails</span></span>  
 <span data-ttu-id="df1eb-114">**Problème**</span><span class="sxs-lookup"><span data-stu-id="df1eb-114">**Problem**</span></span>  
  
 <span data-ttu-id="df1eb-115">Si vous effectuez une installation personnalisée pour installer uniquement la fonction frontale HTTP BTARN, la configuration BTARN peut échouer une fois l'installation terminée en affichant le message suivant :</span><span class="sxs-lookup"><span data-stu-id="df1eb-115">If you perform a custom installation to install only the BTARN HTTP Front End feature, BTARN configuration may fail with the following error after setup has completed:</span></span> 

`Failed to create object for feature: WebApp`  
  
 <span data-ttu-id="df1eb-116">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="df1eb-116">**Resolution**</span></span>  
  
<span data-ttu-id="df1eb-117">Copier les fichiers et reconfigurer manuellement :</span><span class="sxs-lookup"><span data-stu-id="df1eb-117">Manually copy files and reconfigure:</span></span> 
  
1.  <span data-ttu-id="df1eb-118">Copiez les deux fichiers suivants à partir d’un ordinateur BizTalk Server à l’ordinateur sur lequel vous avez installé la fonction frontale HTTP BTARN :</span><span class="sxs-lookup"><span data-stu-id="df1eb-118">Copy the following two files from an BizTalk Server computer to the computer on which you installed the BTARN HTTP Front End feature:</span></span>
  
    -   <span data-ttu-id="df1eb-119">Microsoft.VC80.ATL.manifest</span><span class="sxs-lookup"><span data-stu-id="df1eb-119">Microsoft.VC80.ATL.manifest</span></span>  
  
    -   <span data-ttu-id="df1eb-120">atl80.dll</span><span class="sxs-lookup"><span data-stu-id="df1eb-120">atl80.dll</span></span>  
  
     <span data-ttu-id="df1eb-121">Si Visual Studio est installé sur le même ordinateur que BizTalk Server, le dossier source pour les deux fichiers est <*lecteur*> : \Program Files\Microsoft Visual Studio < version\>\VC\redist\x86\Microsoft.VC100.ATL .</span><span class="sxs-lookup"><span data-stu-id="df1eb-121">If Visual Studio is installed on the same computer as BizTalk Server, the source folder for the two files is <*drive*>:\Program Files\Microsoft Visual Studio <version\>\VC\redist\x86\Microsoft.VC100.ATL.</span></span>  
  
     <span data-ttu-id="df1eb-122">Si Visual Studio n’est pas installé sur le même ordinateur BizTalk Server, le dossier source pour les deux fichiers est sous <*lecteur*> : \WINDOWS\WinSxS.</span><span class="sxs-lookup"><span data-stu-id="df1eb-122">If Visual Studio is not installed on the same BizTalk Server computer, the source folder for the two files is under <*drive*>:\WINDOWS\WinSxS.</span></span>  
  
2.  <span data-ttu-id="df1eb-123">Ajoutez les fichiers copiés sur l'ordinateur sur lequel vous avez installé la fonction frontale HTTP BTARN.</span><span class="sxs-lookup"><span data-stu-id="df1eb-123">Add the copied files to the computer on which you installed BTARN HTTP Front End feature.</span></span> <span data-ttu-id="df1eb-124">Par défaut, copiez les fichiers dans <*lecteur*> : \Program Files\Microsoft BizTalk Accelerator pour RosettaNet.</span><span class="sxs-lookup"><span data-stu-id="df1eb-124">By default, copy the files to <*drive*>:\Program Files\Microsoft BizTalk Accelerator for RosettaNet.</span></span>  
  
3.  <span data-ttu-id="df1eb-125">Après avoir copié les fichiers sur l’ordinateur frontal HTTP, exécutez **Configuration.exe** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="df1eb-125">After you have copied the files to the HTTP Front End computer, run **Configuration.exe** again.</span></span>  
  
### <a name="some-btarn-assemblies-stay-in-gac-after-uninstalling"></a><span data-ttu-id="df1eb-126">Certains assemblys BTARN demeurent dans le GAC après la désinstallation</span><span class="sxs-lookup"><span data-stu-id="df1eb-126">Some BTARN Assemblies stay in GAC after uninstalling</span></span>  
 <span data-ttu-id="df1eb-127">**Problème**</span><span class="sxs-lookup"><span data-stu-id="df1eb-127">**Problem**</span></span>  
  
 <span data-ttu-id="df1eb-128">Lorsque vous désinstallez BTARN, certains assemblys restent dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="df1eb-128">When you uninstall BTARN, some assemblies remain in the global assembly cache (GAC).</span></span>  
  
 <span data-ttu-id="df1eb-129">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="df1eb-129">**Resolution**</span></span>  
  
 <span data-ttu-id="df1eb-130">Supprimez les assemblys du GAC avant de réinstaller BTARN.</span><span class="sxs-lookup"><span data-stu-id="df1eb-130">Remove the assemblies from the GAC before reinstalling BTARN.</span></span>  
  
 <span data-ttu-id="df1eb-131">Utilisez le **BtarnClean** utilitaire à partir du SDK pour supprimer les assemblys.</span><span class="sxs-lookup"><span data-stu-id="df1eb-131">Use the **BtarnClean** utility from the SDK to remove the assemblies.</span></span> <span data-ttu-id="df1eb-132">L'utilitaire effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="df1eb-132">The utility performs the following actions:</span></span>  
  
-   <span data-ttu-id="df1eb-133">Arrête et désinscrit toutes les orchestrations BTARN.</span><span class="sxs-lookup"><span data-stu-id="df1eb-133">Stops and unenlists all the BTARN orchestrations.</span></span>  
  
-   <span data-ttu-id="df1eb-134">Arrête et supprime tous les ports associés.</span><span class="sxs-lookup"><span data-stu-id="df1eb-134">Stops and deletes all the associated ports.</span></span>  
  
-   <span data-ttu-id="df1eb-135">Annule le déploiement de tous les assemblys Microsoft.Solutions.BTARN.\*.</span><span class="sxs-lookup"><span data-stu-id="df1eb-135">Undeploys all the Microsoft.Solutions.BTARN.\* assemblies.</span></span>  
  
 <span data-ttu-id="df1eb-136">Après avoir exécuté l'utilitaire, si des assemblys demeurent dans le GAC, ouvrez l'Explorateur Windows, accédez au dossier « C:\Windows\Assembly », puis supprimez manuellement tous les assemblys en commençant par Microsoft.Solutions.BTARN.</span><span class="sxs-lookup"><span data-stu-id="df1eb-136">After running the utility, if there are assemblies remaining in the GAC, open Windows Explorer, go to the "C:\Windows\Assembly" folder, and then manually delete all assemblies starting with Microsoft.Solutions.BTARN.</span></span>  
  
### <a name="service-unavailable-error-on-64-bit-os"></a><span data-ttu-id="df1eb-137">Erreur de service non disponible sur le système d’exploitation 64 bits</span><span class="sxs-lookup"><span data-stu-id="df1eb-137">Service Unavailable error on 64-bit OS</span></span>
 <span data-ttu-id="df1eb-138">**Problème**</span><span class="sxs-lookup"><span data-stu-id="df1eb-138">**Problem**</span></span>  
  
 <span data-ttu-id="df1eb-139">Vous risquez d’obtenir un `Service Unavailable` lors de la tentative d’accès HTTP BTARN emplacement de réception sur les systèmes d’exploitation Windows 64 bits.</span><span class="sxs-lookup"><span data-stu-id="df1eb-139">You may get a `Service Unavailable` error when trying to access the BTARN HTTP receive location on 64-bit Windows operating systems.</span></span>  
  
 <span data-ttu-id="df1eb-140">**Cause**</span><span class="sxs-lookup"><span data-stu-id="df1eb-140">**Cause**</span></span>  
  
 <span data-ttu-id="df1eb-141">Ce problème peut être lié au filtre ISAPI « RPCProxy.dll ».</span><span class="sxs-lookup"><span data-stu-id="df1eb-141">This issue can be caused by the "RPCProxy.dll" ISAPI filter.</span></span>  
  
 <span data-ttu-id="df1eb-142">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="df1eb-142">**Resolution**</span></span>  
  
<span data-ttu-id="df1eb-143">Supprimer les références au filtre ISAPI du proxy RPC et redémarrer les services IIS :</span><span class="sxs-lookup"><span data-stu-id="df1eb-143">Remove references to the RPC proxy ISAPI filter and restart IIS:</span></span>
  
1.  <span data-ttu-id="df1eb-144">Dans le Gestionnaire des Services Internet (IIS), cliquez sur **Sites Web**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="df1eb-144">In Internet Information Services (IIS) Manager, right-click **Web Sites**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="df1eb-145">Dans le **propriétés du Site Web** boîte de dialogue, cliquez sur le **filtres ISAPI** onglet, supprimez **Proxy RPC** filtrer, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="df1eb-145">In the **Web Site Properties** dialog box, click the **ISAPI filters** tab, remove **RPC Proxy** filter, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="df1eb-146">Redémarrez IIS.</span><span class="sxs-lookup"><span data-stu-id="df1eb-146">Restart IIS.</span></span>  
  
4.  <span data-ttu-id="df1eb-147">Après avoir redémarré IIS, essayez d’accéder à http://localhost.</span><span class="sxs-lookup"><span data-stu-id="df1eb-147">After you have restarted IIS, try accessing http://localhost.</span></span> <span data-ttu-id="df1eb-148">Vous devrez recevoir le message 400 du navigateur Internet.</span><span class="sxs-lookup"><span data-stu-id="df1eb-148">You should get the 400 message back from the Internet browser.</span></span>  
  
### <a name="sql-server-mixed-mode-not-supported"></a><span data-ttu-id="df1eb-149">SQL Server en Mode mixte non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="df1eb-149">SQL Server Mixed Mode not supported</span></span>  
<span data-ttu-id="df1eb-150">BTARN ne prend pas en charge SQL Server en mode mixte.</span><span class="sxs-lookup"><span data-stu-id="df1eb-150">BTARN does not support SQL Server in mixed mode.</span></span>  
  
### <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample"></a><span data-ttu-id="df1eb-151">Exécutez setupx64.bat pour configurer la double action PIPAutomation exemple d’orchestration</span><span class="sxs-lookup"><span data-stu-id="df1eb-151">Run setupx64.bat to set up the double action PIPAutomation orchestration sample</span></span> 

<span data-ttu-id="df1eb-152">Exécutez setupx64.bat dans \Program Files\Microsoft BizTalk Accelerator pour le dossier RosettaNet\SDK\PIPAutomation\DoubleAction installer l’exemple d’Orchestration Double Action PIPAutomation.</span><span class="sxs-lookup"><span data-stu-id="df1eb-152">Run setupx64.bat in \Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction folder to set up the Double Action PIPAutomation Orchestration sample.</span></span>
  
### <a name="download-the-btarn-setup-file-from-the-web-to-a-temp-folder"></a><span data-ttu-id="df1eb-153">Télécharger le fichier d'installation BTARN du Web vers un dossier temporaire</span><span class="sxs-lookup"><span data-stu-id="df1eb-153">Download the BTARN Setup File from the Web to a Temp Folder</span></span>  
 <span data-ttu-id="df1eb-154">**Problème**</span><span class="sxs-lookup"><span data-stu-id="df1eb-154">**Problem**</span></span>  
  
 <span data-ttu-id="df1eb-155">Si vous téléchargez le fichier exécutable à partir du Web à extraction automatique de BTARN et l’enregistrer dans le dossier racine de BizTalk Server, lorsque vous essayez d’exécuter le fichier exécutable, BizTalk **Assistant** s’exécute, au lieu de l’Assistant Installation de BTARN.</span><span class="sxs-lookup"><span data-stu-id="df1eb-155">If you download the BTARN self-extracting executable file from the Web, and save it to the BizTalk Server root folder, when you attempt to run the executable, the BizTalk **Setup Wizard** runs, instead of the BTARN Setup wizard.</span></span>  
  
 <span data-ttu-id="df1eb-156">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="df1eb-156">**Resolution**</span></span>  
  
 <span data-ttu-id="df1eb-157">Téléchargez le fichier exécutable à extraction automatique de BTARN et enregistrez le fichier dans un dossier temporaire.</span><span class="sxs-lookup"><span data-stu-id="df1eb-157">Download the BTARN self-extracting executable, and save the file to a temp folder.</span></span>
