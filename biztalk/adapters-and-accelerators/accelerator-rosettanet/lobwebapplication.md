---
title: LOBWebApplication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, LOBWebApplication
- ASPX pages, LOBWebApplication utility
- virtual servers
- ASPX pages, submitting actions
- LOBWebApplication
- ASPX pages, response messages
- LOBWebApplication utility
ms.assetid: 2d578efd-72a9-4621-9274-30792bf94b6c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9be49eab2560cc9e9eab5a29456a27f92760e5d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="lobwebapplication"></a><span data-ttu-id="2f9a4-102">LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2f9a4-102">LOBWebApplication</span></span>
<span data-ttu-id="2f9a4-103">Vous utilisez l’utilitaire LOBWebApplication pour envoyer un message d’action ou d’une réponse à partir d’une page ASPX à un partenaire commercial, en simulant une application Web line-of-business.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-103">You use the LOBWebApplication utility to submit an action or response message from an ASPX page to a trading partner, simulating an actual line-of-business Web application.</span></span>  
  
 <span data-ttu-id="2f9a4-104">Une fois que vous avez configuré la page ASPX, vous la page de démarrage et entrez les paramètres pour un message : l’accueil et les organisations partenaires ; l’ID d’instance ; version et code PIP et la catégorie du message.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-104">After you have set up the ASPX page, you start the page, and enter the parameters for a message: the home and partner organizations; the PIP code, version, and instance ID; and the message category.</span></span> <span data-ttu-id="2f9a4-105">Vous pouvez ensuite modifier le contenu du service et envoyer le message.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-105">You can then modify the service content, and submit the message.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="2f9a4-106">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="2f9a4-106">Location in SDK</span></span>  
 <span data-ttu-id="2f9a4-107">\<*lecteur*\>\Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\SDK\LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2f9a4-107">\<*drive*\>\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication</span></span>  
  
## <a name="adding-a-virtual-server-for-lobwebapplication"></a><span data-ttu-id="2f9a4-108">Ajout d’un serveur virtuel pour LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2f9a4-108">Adding a Virtual Server for LOBWebApplication</span></span>  
  
#### <a name="to-add-a-virtual-server"></a><span data-ttu-id="2f9a4-109">Pour ajouter un serveur virtuel</span><span class="sxs-lookup"><span data-stu-id="2f9a4-109">To add a virtual server</span></span>  
  
1.  <span data-ttu-id="2f9a4-110">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-110">Click **Start**, point to **AllPrograms**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="2f9a4-111">Dans le Gestionnaire des Services IIS, développez  **\<nom de l’ordinateur\> (ordinateur local)**, développez **Sites Web**, puis cliquez sur **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-111">In Information Services Manager, expand **\<Computer name\> (local computer)**, expand **Web Sites**, and then right-click **Default Web Site**.</span></span>  
  
3.  <span data-ttu-id="2f9a4-112">Pointez sur **nouveau**, puis cliquez sur **répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-112">Point to **New**, and then click **Virtual Directory**.</span></span>  
  
4.  <span data-ttu-id="2f9a4-113">Sur le **Assistant de création de répertoire virtuel** , cliquez sur **suivant**, puis tapez un alias pour le site, tel que **LOBWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-113">On the **Virtual Directory Creation Wizard** page, click **Next**, and then type an alias for the site, such as **LOBWebApplication**.</span></span>  
  
5.  <span data-ttu-id="2f9a4-114">Sur le **répertoire de contenu du Site Web** , cliquez sur **Parcourir**, atteindre \< *lecteur*\>\Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\SDK\LOBWebApplication, cliquez sur **OK**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-114">On the **Web Site Content Directory** page, click **Browse**, move to \<*drive*\>\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication, click **OK**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="2f9a4-115">Sur le **autorisations d’accès de répertoire virtuel** page, sélectionnez **en lecture** et **exécuter des scripts**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-115">On the **Virtual Directory Access Permissions** page, select **Read** and **Run scripts**, and then click **Next**.</span></span> <span data-ttu-id="2f9a4-116">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-116">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="2f9a4-117">Ajoutez l’utilisateur du compte de service qui a été utilisé pour configurer BTARN, par exemple, hostsvc, à la STS_WPG.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-117">Add the service account user that was used to configure BTARN, for example, hostsvc, to the STS_WPG.</span></span>  
  
8.  <span data-ttu-id="2f9a4-118">Supprimez tous les fichiers C:\WINDOWS\Microsoft.NET\Framework\v2.0.\Temporary ASP.NET Files.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-118">Delete all files from C:\WINDOWS\Microsoft.NET\Framework\v2.0.\Temporary ASP.NET Files.</span></span> <span data-ttu-id="2f9a4-119">Vous devrez peut-être exécuter le programme iisreset pour déverrouiller les fichiers avant de les supprimer.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-119">You may have to run the iisreset program to unlock the files before you can delete them.</span></span>  
  
9. <span data-ttu-id="2f9a4-120">Dans le Gestionnaire des services Internet, définissez LOBWebApplication pour s’exécuter sous le BTARNHTTPReceivePool du Pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-120">In IIS Manager, set the LOBWebApplication to run under the Application Pool BTARNHTTPReceivePool.</span></span>  
  
10. <span data-ttu-id="2f9a4-121">Dans le Gestionnaire des services Internet, dans la section Propriétés de sécurité de répertoire de l’utilitaire LOBWebApplication, désactivez l’option pour le répertoire virtuel exécuter en tant qu’utilisateur anonyme.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-121">In IIS Manager, in the Directory Security Properties section for the LOBWebApplication utility, disable the option for the virtual directory to run as anonymous.</span></span>  
  
## <a name="building-lobwebapplication"></a><span data-ttu-id="2f9a4-122">Construction LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2f9a4-122">Building LOBWebApplication</span></span>  
  
#### <a name="to-build-lobwebapplication"></a><span data-ttu-id="2f9a4-123">Pour générer des LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="2f9a4-123">To build LOBWebApplication</span></span>  
  
1.  <span data-ttu-id="2f9a4-124">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-124">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2f9a4-125">Sur le **fichier**, pointez sur **ouvrir**, puis cliquez sur **ouvrir une Solution**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-125">On the **File**, point to **Open**, and then click **Open Solution**.</span></span>  
  
3.  <span data-ttu-id="2f9a4-126">Déplacer vers \< *lecteur*\>\Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\SDK\LOBWebApplication, sélectionnez **LOBWebApplication.sln**, puis cliquez sur  **Ouvrez**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-126">Move to \<*drive*\>\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\LOBWebApplication, select **LOBWebApplication.sln**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2f9a4-127">Si vous n’avez pas ajouté un serveur virtuel de LOBWebApplication, la solution ne s’ouvre pas correctement dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f9a4-127">If you have not added a virtual server for LOBWebApplication, the solution will not open correctly in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="2f9a4-128">Avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-128">Right-click **References**, and then click **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="2f9a4-129">Dans le **ajouter une référence** boîte de dialogue, cliquez sur **Parcourir**, atteindre \< *lecteur*\>: \Program Files\Microsoft BizTalk 2013 Accelerator pour RosettaNet\Bin, sélectionnez les fichiers Microsoft.Solutions.BTARN.ConfigurationManager.dll et Microsoft.Solutions.BTARN.Shared.dll, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-129">In the **Add Reference** dialog box, click **Browse**, move to \<*drive*\>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Bin, select the Microsoft.Solutions.BTARN.ConfigurationManager.dll and Microsoft.Solutions.BTARN.Shared.dll files, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="2f9a4-130">Avec le bouton droit **LOBWebApplication**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-130">Right-click **LOBWebApplication**, and then click **Build**.</span></span>  
  
## <a name="running-lobwebapplication"></a><span data-ttu-id="2f9a4-131">LOBWebApplication en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="2f9a4-131">Running LOBWebApplication</span></span>  
  
#### <a name="to-run-lobwebapplication-and-submit-a-message"></a><span data-ttu-id="2f9a4-132">Pour exécuter LOBWebApplication et envoyer un message</span><span class="sxs-lookup"><span data-stu-id="2f9a4-132">To run LOBWebApplication and submit a message</span></span>  
  
1.  <span data-ttu-id="2f9a4-133">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, puis cliquez sur **Internet Explorer**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-133">Click **Start**, point to **All Programs**, and then click **Internet Explorer**.</span></span>  
  
2.  <span data-ttu-id="2f9a4-134">Dans Internet Explorer, dans le **adresse** zone, tapez http://localhost/LOBWebApplication, puis cliquez sur **accédez**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-134">In Internet Explorer, in the **Address** box, type http://localhost/LOBWebApplication, and then click **Go**.</span></span>  
  
3.  <span data-ttu-id="2f9a4-135">Dans le **envoyer un Message** boîte de dialogue, tapez l’organisation d’origine, l’organisation partenaire, le code PIP, la version PIP, l’ID d’Instance PIP et la catégorie du message.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-135">In the **Submit Message** dialog box, type the home organization, the partner organization, the PIP code, the PIP version, the PIP Instance ID, and the message category.</span></span>  
  
4.  <span data-ttu-id="2f9a4-136">Modifiez le contenu de service en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-136">Modify the service content as needed.</span></span>  
  
5.  <span data-ttu-id="2f9a4-137">Cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-137">Click **Submit**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f9a4-138">Notes</span><span class="sxs-lookup"><span data-stu-id="2f9a4-138">Remarks</span></span>  
 <span data-ttu-id="2f9a4-139">L’utilitaire LOBWebApplication génère une instance du message à partir du PIP spécifié et insère le contenu du service à partir de l’instance de message généré dans la page ASPX.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-139">The LOBWebApplication utility generates an instance of the message from the specified PIP, and enters service content from the generated message instance into the ASPX page.</span></span> <span data-ttu-id="2f9a4-140">Pour ce faire, l’utilitaire utilise la même technique qu’il utilise pour générer une instance de message bien formée directement à partir d’une adresse PIP.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-140">To do this, the utility uses the same technique that it uses to generate a well-formed message instance directly from a PIP.</span></span> <span data-ttu-id="2f9a4-141">Pour plus d’informations, consultez [création d’une Instance de Message bien formée à partir d’une adresse PIP](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-well-formed-message-instance-from-a-pip.md).</span><span class="sxs-lookup"><span data-stu-id="2f9a4-141">For more information, see [Creating a Well-Formed Message Instance from a PIP](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-well-formed-message-instance-from-a-pip.md).</span></span> <span data-ttu-id="2f9a4-142">Vous pouvez remplir n’importe quel champ du contenu de service dans la page ASPX avec des données réelles pour générer une instance de message réel.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-142">You can populate any field of the service content in the ASPX page with actual data to generate an actual message instance.</span></span>  
  
 <span data-ttu-id="2f9a4-143">Vous utilisez l’utilitaire LOBWebApplication pour simuler une application Web de métier-envoi d’un message.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-143">You use the LOBWebApplication utility to simulate a line-of-business Web application submitting a message.</span></span> <span data-ttu-id="2f9a4-144">Vous utilisez l’utilitaire LOBApplication pour simuler une application de bureau métier-envoi d’un message.</span><span class="sxs-lookup"><span data-stu-id="2f9a4-144">You use the LOBApplication utility to simulate a line-of-business desktop application submitting a message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9a4-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f9a4-145">See Also</span></span>  
 <span data-ttu-id="2f9a4-146">[Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span><span class="sxs-lookup"><span data-stu-id="2f9a4-146">[Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span></span>  
 [<span data-ttu-id="2f9a4-147">LOBApplication</span><span class="sxs-lookup"><span data-stu-id="2f9a4-147">LOBApplication</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/lobapplication.md)