---
title: SendMail | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- SMTP adapters
ms.assetid: a0258619-b195-4c8a-8326-77add6e6f04d
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2fce9c39fad76ad0e621fb4773cc39efc3488cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendmail"></a><span data-ttu-id="31fcc-102">SendMail</span><span class="sxs-lookup"><span data-stu-id="31fcc-102">SendMail</span></span>
<span data-ttu-id="31fcc-103">L'exemple SendMail montre comment utiliser l'adaptateur SMTP (Simple Mail Transfer Protocol) pour envoyer des messages électroniques à partir d'une orchestration Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31fcc-103">The SendMail sample demonstrates how you can use the Simple Mail Transfer Protocol (SMTP) adapter to send e-mail messages from within a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span> <span data-ttu-id="31fcc-104">Les informations dynamiques utilisées pour envoyer les messages électroniques sont extraites d'un message XML à l'aide de la fonctionnalité de promotion de propriétés.</span><span class="sxs-lookup"><span data-stu-id="31fcc-104">Dynamic information used to send the e-mail messages is retrieved from an XML message using property promotion functionality.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="31fcc-105">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="31fcc-105">What This Sample Does</span></span>  
 <span data-ttu-id="31fcc-106">Cet exemple envoie un message électronique à l'aide d'informations obtenues à partir des propriétés promues à partir d'un message de bon de commande (PO) XML entrant, en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="31fcc-106">This sample sends an e-mail message using information obtained from properties promoted out of an incoming XML purchase order (PO) message, using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="31fcc-107">L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] extrait un message de PO XML entrant.</span><span class="sxs-lookup"><span data-stu-id="31fcc-107">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration retrieves an input XML PO message.</span></span>  
  
2.  <span data-ttu-id="31fcc-108">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration promeut le **PONumber** et **messagerie** propriétés pour faciliter l’accès à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="31fcc-108">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration promotes the **PONumber** and **Email** properties for easier access in the future.</span></span>  
  
3.  <span data-ttu-id="31fcc-109">L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les valeurs des propriétés promues pour définir l'adresse de destination du port d'envoi dynamique et l'objet du message électronique.</span><span class="sxs-lookup"><span data-stu-id="31fcc-109">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration uses the values of the promoted properties to set the destination address of the dynamic send port and to set the subject of the e-mail message.</span></span>  
  
4.  <span data-ttu-id="31fcc-110">L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie le message électronique construit via l'adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="31fcc-110">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration sends the constructed e-mail message through the SMTP adapter.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="31fcc-111">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="31fcc-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="31fcc-112">\<*Exemples de chemin d’accès*> \AdaptersUsage\SendMail\\</span><span class="sxs-lookup"><span data-stu-id="31fcc-112">\<*Samples Path*>\AdaptersUsage\SendMail\\</span></span>  
  
 <span data-ttu-id="31fcc-113">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="31fcc-113">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="31fcc-114">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="31fcc-114">File(s)</span></span>|<span data-ttu-id="31fcc-115"> Description</span><span class="sxs-lookup"><span data-stu-id="31fcc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31fcc-116">AssemblyInfo.cs, SendMail.btproj, SendMail.sln</span><span class="sxs-lookup"><span data-stu-id="31fcc-116">AssemblyInfo.cs, SendMail.btproj, SendMail.sln</span></span>|<span data-ttu-id="31fcc-117">Fournit des fichiers d'informations de projet, de solution et d'assembly pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="31fcc-117">Provides project, solution, and assembly information files for this sample.</span></span>|  
|<span data-ttu-id="31fcc-118">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="31fcc-118">Cleanup.bat</span></span>|<span data-ttu-id="31fcc-119">Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="31fcc-119">Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="31fcc-120">PropertySchema.xsd, PurchaseOrder.xsd</span><span class="sxs-lookup"><span data-stu-id="31fcc-120">PropertySchema.xsd, PurchaseOrder.xsd</span></span>|<span data-ttu-id="31fcc-121">Fournit des schémas respectivement pour les propriétés que vous voulez promouvoir et pour le message de PO XML.</span><span class="sxs-lookup"><span data-stu-id="31fcc-121">Provides schemas for the properties that you want to promote, and for the XML PO message, respectively.</span></span>|  
|<span data-ttu-id="31fcc-122">ReceiveSend.odx</span><span class="sxs-lookup"><span data-stu-id="31fcc-122">ReceiveSend.odx</span></span>|<span data-ttu-id="31fcc-123">Fournit une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui traite le message de PO XML entrant et envoie un message électronique sur la base des informations figurant dans le message reçu.</span><span class="sxs-lookup"><span data-stu-id="31fcc-123">Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that processes the incoming XML PO message and sends an e-mail message based on information in the message.</span></span>|  
|<span data-ttu-id="31fcc-124">SendMailInput.xml</span><span class="sxs-lookup"><span data-stu-id="31fcc-124">SendMailInput.xml</span></span>|<span data-ttu-id="31fcc-125">Contient un exemple de fichier d'entrée avec un bon de commande spécifié à l'aide de XML.</span><span class="sxs-lookup"><span data-stu-id="31fcc-125">Contains a sample input file with a PO specified using XML.</span></span>|  
|<span data-ttu-id="31fcc-126">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="31fcc-126">Setup.bat</span></span>|<span data-ttu-id="31fcc-127">Crée et initialise l'exemple.</span><span class="sxs-lookup"><span data-stu-id="31fcc-127">Builds and initializes this sample.</span></span> <span data-ttu-id="31fcc-128">**Remarque :** ce fichier d’installation crée et lie les ports, et ainsi de suite, à l’aide d’un mécanisme autre que la majeure partie de l’installation de fichiers pour les exemples du Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="31fcc-128">**Note:**  This setup file creates and binds ports, and so on, using a different mechanism than most of the setup files for the SDK samples.</span></span> <span data-ttu-id="31fcc-129">Il ne nécessite pas de fichier .xml compagnon.</span><span class="sxs-lookup"><span data-stu-id="31fcc-129">It does not require a companion .xml file.</span></span>|  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="31fcc-130">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="31fcc-130">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="31fcc-131">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="31fcc-131">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="31fcc-132">\<*Exemples de chemin d’accès*> \AdaptersUsage\SendMail</span><span class="sxs-lookup"><span data-stu-id="31fcc-132">\<*Samples Path*>\AdaptersUsage\SendMail</span></span>  
  
2.  <span data-ttu-id="31fcc-133">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="31fcc-133">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="31fcc-134">Crée le dossier d'entrée suivant pour cet exemple :</span><span class="sxs-lookup"><span data-stu-id="31fcc-134">Creates the following input folder for this sample:</span></span>  
  
         <span data-ttu-id="31fcc-135">\<*Exemples de chemin d’accès*> \AdaptersUsage\SendMail\In</span><span class="sxs-lookup"><span data-stu-id="31fcc-135">\<*Samples Path*>\AdaptersUsage\SendMail\In</span></span>  
  
    -   <span data-ttu-id="31fcc-136">compilation du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="31fcc-136">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="31fcc-137">Démarre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31fcc-137">Starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="31fcc-138">Avant de tenter d'exécuter cet exemple, vous devez confirmer que BizTalk n'a signalé aucune erreur durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="31fcc-138">You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="31fcc-139">Si vous choisissez d'ouvrir et de créer le projet dans cet exemple sans exécuter le fichier Setup.bat, vous devez d'abord créer une paire de clés de nom fort en utilisant l'utilitaire .NET Framework Strong Name Utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="31fcc-139">If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="31fcc-140">Utilisez cette paire de clés pour signer l'assembly obtenu.</span><span class="sxs-lookup"><span data-stu-id="31fcc-140">Use this key pair to sign the resulting assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="31fcc-141">Pour annuler les modifications apportées par Setup.bat, exécutez le fichier Cleanup.bat et supprimez tous recevant, précédés de SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail de ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="31fcc-141">To undo changes made by Setup.bat, run Cleanup.bat and delete all receive and send ports prefixed with SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail.</span></span> <span data-ttu-id="31fcc-142">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="31fcc-142">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
3.  <span data-ttu-id="31fcc-143">Dans le **Administration de BizTalk Server** de la console, localisez le port de réception préfixé par SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail.</span><span class="sxs-lookup"><span data-stu-id="31fcc-143">In the **BizTalk Server Administration** console, locate the receive port prefixed by SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail.</span></span> <span data-ttu-id="31fcc-144">Mettre à jour l’emplacement de réception pour ce port de réception pointer vers un répertoire sur votre système de fichiers à utiliser comme emplacement d’entrée.</span><span class="sxs-lookup"><span data-stu-id="31fcc-144">Update the receive location for this receive port to point to a directory on your file system to use as the input location.</span></span>  
  
4.  <span data-ttu-id="31fcc-145">À l’aide d’un programme tel que le bloc-notes, modifiez le fichier SendMailInput.xml afin que le **messagerie** élément spécifie une adresse électronique à laquelle vous souhaitez recevoir le message électronique généré par cet exemple.</span><span class="sxs-lookup"><span data-stu-id="31fcc-145">Using a program such as Notepad, modify the file SendMailInput.xml so that the **Email** element specifies a legitimate e-mail address at which you want to receive the e-mail message generated by this sample.</span></span>  
  
5.  <span data-ttu-id="31fcc-146">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="31fcc-146">Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
6.  <span data-ttu-id="31fcc-147">Dans le **Administration de BizTalk Server** de la console, développez l’arborescence du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="31fcc-147">In the **BizTalk Server Administration** console, expand the BizTalk Group tree.</span></span>  
  
7.  <span data-ttu-id="31fcc-148">Développez le **paramètres de plateforme** arborescence dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="31fcc-148">Expand the **Platform Settings** tree in the left pane.</span></span>  
  
8.  <span data-ttu-id="31fcc-149">Développez le **cartes** dossier, cliquez sur le **SMTP** nœud, puis double-cliquez sur la ligne de l’adaptateur SMTP dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="31fcc-149">Expand the **Adapters** folder, click the **SMTP** node, and then double-click the SMTP adapter row in the right pane.</span></span>  
  
9. <span data-ttu-id="31fcc-150">Dans le **SMTP - propriétés du Gestionnaire d’adaptateur** boîte de dialogue, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="31fcc-150">In the **SMTP - Adapter Handler Properties** dialog box, click **Properties**.</span></span>  
  
10. <span data-ttu-id="31fcc-151">Dans le **propriétés du Transport SMTP** boîte de dialogue le **propriétés** onglet, entrez les valeurs appropriées pour le **nom du serveur SMTP** et **à partir de (courrier électronique adresse)** propriétés, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="31fcc-151">In the **SMTP Transport Properties** dialog box, on the **Properties** tab, provide appropriate values for the **SMTP server name** and **From (e-mail address)** properties, and then click **OK**.</span></span>  
  
     <span data-ttu-id="31fcc-152">Ces valeurs seront utilisées pour créer l'adresse électronique De pour tous les messages électroniques envoyés via cet adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="31fcc-152">These values will be used to construct the From e-mail address for any e-mail messages sent through this SMTP adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31fcc-153">Si vous devez vous authentifier auprès de votre serveur SMTP, vous devez veiller à ce que l'adresse électronique De appartienne au même compte que celui que vous utilisez pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="31fcc-153">If you need to authenticate with your SMTP server, you must ensure that the From e-mail address belongs to the same account that you use for authentication.</span></span>  
  
11. <span data-ttu-id="31fcc-154">Arrêtez, puis redémarrez le service BizTalk (BizTalkServerApplication) de façon à ce que l'orchestration adopte ces modifications.</span><span class="sxs-lookup"><span data-stu-id="31fcc-154">Stop and then restart the BizTalk service (BizTalkServerApplication) so that the orchestration will adopt these changes.</span></span>  
  
### <a name="to-run-this-sample"></a><span data-ttu-id="31fcc-155">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="31fcc-155">To run this sample</span></span>  
  
1.  <span data-ttu-id="31fcc-156">Placez une copie du fichier modifié SendMailInput.xml dans le dossier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="31fcc-156">Put a copy of the modified file SendMailInput.xml into the input folder.</span></span>  
  
2.  <span data-ttu-id="31fcc-157">Observez l'arrivée d'un message électronique à l'adresse spécifiée au cours de la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="31fcc-157">Observe the arrival of an e-mail message to the e-mail address you specified in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fcc-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31fcc-158">See Also</span></span>  
 [<span data-ttu-id="31fcc-159">Exemples d’adaptateurs - utilisation</span><span class="sxs-lookup"><span data-stu-id="31fcc-159">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)