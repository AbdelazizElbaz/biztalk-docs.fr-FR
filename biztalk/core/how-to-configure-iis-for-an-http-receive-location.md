---
title: "Configuration d’IIS pour l’emplacement de réception HTTP | Documents Microsoft"
description: "Créer l’application de réception HTTP BTS dans IIS et de tester les paramètres de pool d’applications dans BizTalk Server"
ms.custom: 
ms.date: 10/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e09768d6616a33a4900995f3dd3225fa34318b3c
ms.sourcegitcommit: 75d35f6f230f0846c29a4b146c6d5b074e60b13c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="configure-iis-for-an-http-receive-location"></a><span data-ttu-id="97a3a-103">Configuration d’IIS pour l’emplacement de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="97a3a-103">Configure IIS for an HTTP Receive Location</span></span>
<span data-ttu-id="97a3a-104">Utilisations de l’emplacement de réception HTTP une application dans Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="97a3a-104">The HTTP receive location uses an application within Internet Information Services (IIS).</span></span> <span data-ttu-id="97a3a-105">Emplacement dans les services IIS de réception de cette rubrique répertorie les étapes pour activer le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="97a3a-105">This topic lists the steps to enable the HTTP receive location within IIS.</span></span> 

<span data-ttu-id="97a3a-106">Selon votre système d’exploitation, les étapes de configuration de l’application IIS peuvent varier.</span><span class="sxs-lookup"><span data-stu-id="97a3a-106">Depending on your operating system, the steps to configure the IIS application may vary.</span></span> <span data-ttu-id="97a3a-107">Utilisez ces étapes comme guide, comme l’interface utilisateur peut être différent sur votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="97a3a-107">Use these steps as a guide, as the user interface may be different on your OS.</span></span>
  
## <a name="32-bit-vs-64-bit"></a><span data-ttu-id="97a3a-108">éditions 32 bits et 64 bits</span><span class="sxs-lookup"><span data-stu-id="97a3a-108">32-bit vs 64-bit</span></span>

<span data-ttu-id="97a3a-109">Emplacement utilise le BTSHTTPReceive.dll de réception HTTP.</span><span class="sxs-lookup"><span data-stu-id="97a3a-109">An HTTP receive location uses the BTSHTTPReceive.dll.</span></span> <span data-ttu-id="97a3a-110">Il existe une version 32 bits et une version 64 bits de la DLL.</span><span class="sxs-lookup"><span data-stu-id="97a3a-110">There is a 32-bit and a 64-bit version of the DLL.</span></span> <span data-ttu-id="97a3a-111">Vous choisissez la version que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="97a3a-111">You choose which version you want to use.</span></span> <span data-ttu-id="97a3a-112">processus 64 bits ont plus de mémoire disponible, par conséquent, si vous traitez des messages plus volumineux, la version 64 bits peut être préférable.</span><span class="sxs-lookup"><span data-stu-id="97a3a-112">64-bit processes have more available memory, so if you process larger messages, then the 64-bit version may be best.</span></span> 

<span data-ttu-id="97a3a-113">**emplacement d’installation 32 bits**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive*.</span><span class="sxs-lookup"><span data-stu-id="97a3a-113">**32-bit install location**: *Program Files (x86)\Microsoft BizTalk Server\HttpReceive*.</span></span>
<span data-ttu-id="97a3a-114">**emplacement d’installation 64 bits**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive64*</span><span class="sxs-lookup"><span data-stu-id="97a3a-114">**64-bit install location**: *Program Files (x86)\Microsoft BizTalk Server\HttpReceive64*</span></span>

<span data-ttu-id="97a3a-115">Pour exécuter la version 64 bits du HTTP adaptateur de réception en mode natif de 64 bits, ouvrez une invite de commandes et exécuter les scripts suivants :</span><span class="sxs-lookup"><span data-stu-id="97a3a-115">To run the 64-bit version of the HTTP receive adapter in 64-bit native mode,  open a command prompt, and execute the following scripts:</span></span>  

1. <span data-ttu-id="97a3a-116">Type :`cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`</span><span class="sxs-lookup"><span data-stu-id="97a3a-116">Type: `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`</span></span>  

2. <span data-ttu-id="97a3a-117">Type :`C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`</span><span class="sxs-lookup"><span data-stu-id="97a3a-117">Type: `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97a3a-118">Toute configuration IIS menant au partage du même processus par SOAP et HTTP est non valide.</span><span class="sxs-lookup"><span data-stu-id="97a3a-118">Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid.</span></span> <span data-ttu-id="97a3a-119">Vous ne pouvez utiliser qu'un seul récepteur isolé par processus.</span><span class="sxs-lookup"><span data-stu-id="97a3a-119">You can have only one isolated receiver per process.</span></span>  
  
##  <a name="configure-the-iis-application"></a><span data-ttu-id="97a3a-120">Configurer l’application IIS</span><span class="sxs-lookup"><span data-stu-id="97a3a-120">Configure the IIS application</span></span>
  
1.  <span data-ttu-id="97a3a-121">Ouvrez **Internet Information Services** (ouvrir **le Gestionnaire de serveur**, sélectionnez **outils**, puis sélectionnez **Gestionnaire des Services Internet**).</span><span class="sxs-lookup"><span data-stu-id="97a3a-121">Open **Internet Information Services** (open **Server Manager**, select **Tools**, and select **Internet Information Services Manager**).</span></span> 
  
2.  <span data-ttu-id="97a3a-122">Dans IIS, sélectionnez le nom de votre serveur.</span><span class="sxs-lookup"><span data-stu-id="97a3a-122">In IIS, select your server name.</span></span> <span data-ttu-id="97a3a-123">Dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-123">In the **Features View**, double-click **Handler Mappings**.</span></span> <span data-ttu-id="97a3a-124">Dans le volet Actions, sélectionnez **ajouter un mappage de scripts**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-124">In the Actions pane, select **Add Script Map**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97a3a-125">Lorsque vous configurez le mappage du script au niveau du serveur web-, le mappage s’applique à tous les sites web.</span><span class="sxs-lookup"><span data-stu-id="97a3a-125">When you configure the script mapping at the web server-level, the mapping applies to all web sites.</span></span> <span data-ttu-id="97a3a-126">Si vous souhaitez limiter le mappage vers un site Web spécifique ou d’un dossier virtuel, sélectionnez ce site web ou un dossier et puis ajoutez le mappage de script.</span><span class="sxs-lookup"><span data-stu-id="97a3a-126">If you want to restrict the mapping to a specific Web site or virtual folder, select that web site or folder, and then add the script map.</span></span>  
  
3.  <span data-ttu-id="97a3a-127">Dans **ajouter un mappage de scripts**, sélectionnez **chemin d’accès de la demande**et le type `BtsHttpReceive.dll`.</span><span class="sxs-lookup"><span data-stu-id="97a3a-127">In **Add Script Map**, select **Request path**, and type `BtsHttpReceive.dll`.</span></span>  
  
4.  <span data-ttu-id="97a3a-128">Dans **exécutable**, sélectionnez les points de suspension (**...** ), puis accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span><span class="sxs-lookup"><span data-stu-id="97a3a-128">In **Executable**, select the ellipsis (**…**), and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span></span> <span data-ttu-id="97a3a-129">Sélectionnez **BtsHttpReceive.dll**, puis sélectionnez **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-129">Select **BtsHttpReceive.dll**, and then select **Open**.</span></span>  
  
5.  <span data-ttu-id="97a3a-130">Dans **nom**, entrez `BizTalk HTTP Receive`, puis sélectionnez **Restrictions des demandes**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-130">In **Name**, enter `BizTalk HTTP Receive`, and then select **Request Restrictions**.</span></span> <span data-ttu-id="97a3a-131">Dans la fenêtre :</span><span class="sxs-lookup"><span data-stu-id="97a3a-131">In this window:</span></span>
  
    1. <span data-ttu-id="97a3a-132">Dans **verbes**, sélectionnez **un des verbes suivants**, puis entrez `POST`.</span><span class="sxs-lookup"><span data-stu-id="97a3a-132">In **Verbs**, select **One of the following verbs**, and enter `POST`.</span></span>  
  
    2. <span data-ttu-id="97a3a-133">Dans **accès**, sélectionnez **Script**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-133">In **Access**, select **Script**, and then select **OK**.</span></span>  
  
    3. <span data-ttu-id="97a3a-134">Lorsque vous êtes invité à autoriser l’extension ISAPI, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-134">When prompted to allow the ISAPI extension, select **Yes**.</span></span>  
  
6. <span data-ttu-id="97a3a-135">Créer un nouveau pool d’applications (avec le bouton droit **Pools d’applications**, sélectionnez **ajouter le pool d’applications**).</span><span class="sxs-lookup"><span data-stu-id="97a3a-135">Create a new application pool (right-click **Application Pools**, select **Add application pool**).</span></span> <span data-ttu-id="97a3a-136">**Nom** votre pool d’applications (telles que `BTSHTTPReceive`), sélectionnez **.NET Framework v4.0.30319**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-136">**Name** your application pool (such as `BTSHTTPReceive`), select **NET Framework v4.0.30319**, and select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97a3a-137">Le numéro de version .NET peut varier selon la version de .NET Framework installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="97a3a-137">The .NET version number may vary depending on the version of .NET Framework installed on the computer.</span></span>  
  
     <span data-ttu-id="97a3a-138">Le pool d’applications est répertorié.</span><span class="sxs-lookup"><span data-stu-id="97a3a-138">The new application pool is listed.</span></span>  
  
7. <span data-ttu-id="97a3a-139">Sélectionnez votre nouveau pool d’applications, puis ouvrez le **paramètres avancés** (**Actions** volet).</span><span class="sxs-lookup"><span data-stu-id="97a3a-139">Select your new application pool, and open the **Advanced Settings** (**Actions** pane).</span></span> <span data-ttu-id="97a3a-140">Dans la fenêtre :</span><span class="sxs-lookup"><span data-stu-id="97a3a-140">In this window:</span></span>

    - <span data-ttu-id="97a3a-141">**Activer l’Application 32 bits**: la valeur **True** si vous avez choisi de 32 bits **BtsHttpReceive.dll**</span><span class="sxs-lookup"><span data-stu-id="97a3a-141">**Enable 32-Bit Application**: Set to **True** if you chose the 32-bit **BtsHttpReceive.dll**</span></span>
    - <span data-ttu-id="97a3a-142">**Modèle de processus** section, **identité**: sélectionnez les points de suspension (**...** ), sélectionnez **compte personnalisé**, puis **définir** à un compte qui est membre de la **utilisateurs d’hôtes BizTalk isolés** et **IIS_WPG** groupes.</span><span class="sxs-lookup"><span data-stu-id="97a3a-142">**Process Model** section, **Identity**: Select the ellipsis (**…**), select **Custom account**, and then **Set** it to an account that is a member of the **BizTalk Isolated Host Users** and **IIS_WPG** groups.</span></span> <span data-ttu-id="97a3a-143">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-143">Select **OK**.</span></span> 
  
8. <span data-ttu-id="97a3a-144">Ajoutez une nouvelle application pour le site web (avec le bouton droit le **Site Web par défaut**, sélectionnez **ajouter une Application**).</span><span class="sxs-lookup"><span data-stu-id="97a3a-144">Add a new application to the web site (right-click the **Default Web Site**, select **Add Application**).</span></span> <span data-ttu-id="97a3a-145">Dans la fenêtre :</span><span class="sxs-lookup"><span data-stu-id="97a3a-145">In this window:</span></span>
  
    1. <span data-ttu-id="97a3a-146">**Alias** : entrez un alias que vous associez à l’application (tel que `BTS HTTP Receive`, puis **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-146">**Alias** : Enter an alias that you associate with the application (such as `BTS HTTP Receive`, and then **Select**.</span></span>  
    2. <span data-ttu-id="97a3a-147">Sélectionnez le nouveau pool d’applications que vous venez créé, puis **OK**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-147">Select the new application pool you just created, and then select **OK**.</span></span>  
    3. <span data-ttu-id="97a3a-148">**Chemin d’accès physique**: sélectionnez les points de suspension (**...** ), puis accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span><span class="sxs-lookup"><span data-stu-id="97a3a-148">**Physical path**: Select the ellipsis (**…**), and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span></span>  
    4. <span data-ttu-id="97a3a-149">**Paramètres de test** vérifier aucun message d’erreur dans le **tester la connexion** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="97a3a-149">**Test Settings** to verify there are no errors in the **Test Connection** dialog box.</span></span> <span data-ttu-id="97a3a-150">**Fermer**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-150">**Close**, and then select **OK**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="97a3a-151">Si les paramètres de Test renvoie un avertissement, l’identité du pool d’applications est absent des autorisations pour un dossier ou accès à un groupe.</span><span class="sxs-lookup"><span data-stu-id="97a3a-151">If Test Settings returns a warning, the identity of the application pool may be missing permissions to a folder, or access to a group.</span></span> <span data-ttu-id="97a3a-152">En tant qu’étape de dépannage, sélectionnez **connecter en tant que**, entrez la **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="97a3a-152">As a troubleshooting step, select **Connect As**, enter the **User name** and **Password** for a user account that is a member of the Administrators group.</span></span> 

9. <span data-ttu-id="97a3a-153">La nouvelle application s’affiche est répertorié sous **Sites Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="97a3a-153">The new application appears is listed under **Default Web Sites**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a3a-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97a3a-154">See Also</span></span>  
 [<span data-ttu-id="97a3a-155">Pour configurer les emplacement de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="97a3a-155">How to Configure an HTTP Receive Location</span></span>](../core/how-to-configure-an-http-receive-location.md)
