---
title: Adaptateur transactionnel (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31a13377-cc89-4763-ad1b-508a16fc9708
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f934857103952a035159cc08678c8ce8c8e51a56
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="transactional-adapter-biztalk-server-sample"></a><span data-ttu-id="6ad71-102">Adaptateur transactionnel (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="6ad71-102">Transactional Adapter (BizTalk Server Sample)</span></span>
<span data-ttu-id="6ad71-103">L'exemple d'adaptateur transactionnel montre comment créer et utiliser une transaction Microsoft Distributed Transaction Coordinator (MSDTC) explicite sur une base de données lors du traitement d'un message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ad71-103">The Transactional Adapter sample demonstrates how to create and use an explicit Microsoft Distributed Transaction Coordinator (MSDTC) transaction against a database during processing of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="6ad71-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-104">What This Sample Does</span></span>  
 <span data-ttu-id="6ad71-105">Cet exemple contient un adaptateur de réception qui exécute une instruction SQL, à un intervalle spécifié par l'utilisateur, afin d'obtenir des données d'une base de données SQL Server à l'aide d'une transaction MSDTC.</span><span class="sxs-lookup"><span data-stu-id="6ad71-105">This sample contains a receive adapter which runs a SQL statement at a user-specified interval to obtain data from a SQL Server database using an MSDTC transaction.</span></span> <span data-ttu-id="6ad71-106">Ces données sont alors transmises à la base de données MessageBox de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sous la forme d'un message, dans le contexte de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="6ad71-106">The data is then submitted to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database in the form of a message under the context of the same transaction.</span></span>  
  
 <span data-ttu-id="6ad71-107">L'adaptateur d'envoi correspondant exécute une procédure stockée SQL spécifiée par l'utilisateur via l'entrée d'un message BizTalk dans le contexte d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="6ad71-107">The corresponding send adapter runs a user-specified SQL stored procedure using input from a BizTalk message in the context of a transaction.</span></span> <span data-ttu-id="6ad71-108">Il utilise les données spécifiques de ce message pour localiser et supprimer le message correspondant de la base de données MessageBox, sous cette même transaction.</span><span class="sxs-lookup"><span data-stu-id="6ad71-108">It uses specific data from that message to locate and delete the corresponding message from the Message Box database under that same transaction.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="6ad71-109">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="6ad71-109">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="6ad71-110">Cet exemple inclut deux projets dans sa solution.</span><span class="sxs-lookup"><span data-stu-id="6ad71-110">This sample has two projects in its solution.</span></span> <span data-ttu-id="6ad71-111">Le premier, le projet administratif (Admin), est utilisé avant l'exécution pour permettre à un utilisateur de configurer les emplacements de réception et les ports d'envoi qui utilisent cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6ad71-111">The first is the administrative project (Admin) which is used prior to runtime to allow a user to configure the receive locations and send ports that use this adapter.</span></span> <span data-ttu-id="6ad71-112">Le deuxième, le projet d'exécution (Runtime), est exécuté lorsque les adaptateurs d'envoi et de réception sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="6ad71-112">The second is the runtime project (Runtime) that runs when the send and receive adapters are executing.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="6ad71-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="6ad71-114">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="6ad71-114">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="6ad71-115">\<*Exemples de chemin d’accès*\>\Samples\AdaptersDevelopment\TransactionalAdapter.</span><span class="sxs-lookup"><span data-stu-id="6ad71-115">\<*Samples Path*\>\Samples\AdaptersDevelopment\TransactionalAdapter.</span></span> <span data-ttu-id="6ad71-116">Le projet administratif de configuration se trouve dans le dossier \Admin, et le projet d'exécution dans le dossier \Runtime.</span><span class="sxs-lookup"><span data-stu-id="6ad71-116">The administrative configuration project is located in the \Admin folder, while the runtime project exists in the \Runtime folder.</span></span>  
  
 <span data-ttu-id="6ad71-117">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="6ad71-117">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="6ad71-118">Nom du fichier de projet Admin</span><span class="sxs-lookup"><span data-stu-id="6ad71-118">Admin Project Filename</span></span>|<span data-ttu-id="6ad71-119">Description du fichier de projet Admin</span><span class="sxs-lookup"><span data-stu-id="6ad71-119">Admin Project File Description</span></span>|  
|----------------------------|------------------------------------|  
|<span data-ttu-id="6ad71-120">TransactionalAdmin.csproj</span><span class="sxs-lookup"><span data-stu-id="6ad71-120">TransactionalAdmin.csproj</span></span>|<span data-ttu-id="6ad71-121">Fichier du projet administratif de l'adaptateur utilisé pour la configuration antérieure à l'exécution</span><span class="sxs-lookup"><span data-stu-id="6ad71-121">Adapter administrative project file used for pre-runtime configuration</span></span>|  
|<span data-ttu-id="6ad71-122">TransactionalReceiveHandler.xsd</span><span class="sxs-lookup"><span data-stu-id="6ad71-122">TransactionalReceiveHandler.xsd</span></span>|<span data-ttu-id="6ad71-123">XSD pour les propriétés du gestionnaire de réception</span><span class="sxs-lookup"><span data-stu-id="6ad71-123">XSD for receive handler properties</span></span>|  
|<span data-ttu-id="6ad71-124">TransactionalReceiveLocation.xsd</span><span class="sxs-lookup"><span data-stu-id="6ad71-124">TransactionalReceiveLocation.xsd</span></span>|<span data-ttu-id="6ad71-125">XSD pour les propriétés de l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="6ad71-125">XSD for receive location properties</span></span>|  
|<span data-ttu-id="6ad71-126">TransactionalTransmitLocation.xsd</span><span class="sxs-lookup"><span data-stu-id="6ad71-126">TransactionalTransmitLocation.xsd</span></span>|<span data-ttu-id="6ad71-127">XSD pour les propriétés de l'emplacement de transmission</span><span class="sxs-lookup"><span data-stu-id="6ad71-127">XSD for transmit location properties</span></span>|  
|<span data-ttu-id="6ad71-128">TransactionalTransmitHandler.xsd</span><span class="sxs-lookup"><span data-stu-id="6ad71-128">TransactionalTransmitHandler.xsd</span></span>|<span data-ttu-id="6ad71-129">XSD pour les propriétés du gestionnaire de transmission</span><span class="sxs-lookup"><span data-stu-id="6ad71-129">XSD for transmit handler properties</span></span>|  
|<span data-ttu-id="6ad71-130">TransactionalAdapterManagement.cs</span><span class="sxs-lookup"><span data-stu-id="6ad71-130">TransactionalAdapterManagement.cs</span></span>|<span data-ttu-id="6ad71-131">Gestion de la configuration de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6ad71-131">Adapter configuration management.</span></span> <span data-ttu-id="6ad71-132">Contient GetConfigSchema qui est appelé par l'infrastructure d'adaptateurs BizTalk pour renvoyer un schéma de configuration XSD pour chacun des (quatre) types de configurations possibles qu'il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="6ad71-132">Contains GetConfigSchema which is invoked by the BizTalk Adapter Framework to return an XSD configuration schema for each of the (four) possible configuration types it supports.</span></span>|  
  
|<span data-ttu-id="6ad71-133">Nom du fichier de projet au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="6ad71-133">Runtime Project Filename</span></span>|<span data-ttu-id="6ad71-134">Description du fichier de projet au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="6ad71-134">Runtime Project File Description</span></span>|  
|------------------------------|--------------------------------------|  
|<span data-ttu-id="6ad71-135">Transactional.csproj</span><span class="sxs-lookup"><span data-stu-id="6ad71-135">Transactional.csproj</span></span>|<span data-ttu-id="6ad71-136">Fichier du projet d'exécution de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="6ad71-136">Adapter runtime project file</span></span>|  
|<span data-ttu-id="6ad71-137">TransactionalAsyncBatch.cs</span><span class="sxs-lookup"><span data-stu-id="6ad71-137">TransactionalAsyncBatch.cs</span></span>|<span data-ttu-id="6ad71-138">Implémentation asynchrone du port d'envoi de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="6ad71-138">Asynchronous implementation of the send part of the adapter</span></span>|  
|<span data-ttu-id="6ad71-139">TransactionalDeleteBatch.cs</span><span class="sxs-lookup"><span data-stu-id="6ad71-139">TransactionalDeleteBatch.cs</span></span>|<span data-ttu-id="6ad71-140">Supprime un lot de messages et valide ou abandonne une transaction</span><span class="sxs-lookup"><span data-stu-id="6ad71-140">Deletes a batch of messages and votes to commit or abort a transaction</span></span>|  
|<span data-ttu-id="6ad71-141">TransactionalProperties.cs</span><span class="sxs-lookup"><span data-stu-id="6ad71-141">TransactionalProperties.cs</span></span>|<span data-ttu-id="6ad71-142">Extrait et définit les propriétés de configuration</span><span class="sxs-lookup"><span data-stu-id="6ad71-142">Extracts and sets configuration properties</span></span>|  
|<span data-ttu-id="6ad71-143">TransactionalReceiver.cs</span><span class="sxs-lookup"><span data-stu-id="6ad71-143">TransactionalReceiver.cs</span></span>|<span data-ttu-id="6ad71-144">Crée et gère les points de terminaison de réception</span><span class="sxs-lookup"><span data-stu-id="6ad71-144">Creates and manages receive endpoints</span></span>|  
|<span data-ttu-id="6ad71-145">TransactionalReceiverEndpoint.cs</span><span class="sxs-lookup"><span data-stu-id="6ad71-145">TransactionalReceiverEndpoint.cs</span></span>|<span data-ttu-id="6ad71-146">Écoute réelle ou interrogation pour chaque emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="6ad71-146">Actual listening or polling for each receive location</span></span>|  
|<span data-ttu-id="6ad71-147">TransactionalTransmitter.cs</span><span class="sxs-lookup"><span data-stu-id="6ad71-147">TransactionalTransmitter.cs</span></span>|<span data-ttu-id="6ad71-148">Accepte un lot de messages du moteur de messagerie à transmettre</span><span class="sxs-lookup"><span data-stu-id="6ad71-148">Accepts a batch of messages from the Messaging Engine to be transmitted</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="6ad71-149">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-149">How to Use This Sample</span></span>  
 <span data-ttu-id="6ad71-150">Cet exemple est conçu comme une infrastructure que vous utilisez pour créer des adaptateurs d'envoi et de réception personnalisés à l'aide de transactions explicites.</span><span class="sxs-lookup"><span data-stu-id="6ad71-150">This sample is meant as a framework for you to use in creating custom send and receive adapters using explicit transactions.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="6ad71-151">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-151">Building and Initializing This Sample</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ad71-152">Si l'installation BizTalk est 64 bits ou si son emplacement a été modifié, les valeurs OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath doivent être modifiées en conséquence.</span><span class="sxs-lookup"><span data-stu-id="6ad71-152">If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.</span></span>  
  
#### <a name="create-a-strong-name-key-for-the-transactional-adapter-sample"></a><span data-ttu-id="6ad71-153">Créer une clé de nom fort de l’exemple d’adaptateur transactionnel</span><span class="sxs-lookup"><span data-stu-id="6ad71-153">Create a Strong Name Key for the Transactional Adapter sample</span></span>  
  
1.  <span data-ttu-id="6ad71-154">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-154">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="6ad71-155">À l'invite de commandes, tapez la commande suivante, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="6ad71-155">At the command prompt, type the following and then press enter:</span></span>  
  
    ```  
    cd \Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Runtime  
    ```  
  
3.  <span data-ttu-id="6ad71-156">À l'invite de commandes, tapez la commande suivante, puis appuyez sur Entrée :</span><span class="sxs-lookup"><span data-stu-id="6ad71-156">At the command prompt, type the following and then press enter:</span></span>  
  
    ```  
    sn –k TransactionalAdapter.snk  
    ```  
  
4.  <span data-ttu-id="6ad71-157">À l’invite de commandes, tapez **quitter**, puis appuyez sur ENTRÉE pour fermer la fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6ad71-157">At the command prompt, type **exit**, and then press enter to close the command prompt window.</span></span>  
  
#### <a name="build-the-transactional-adapter-solution"></a><span data-ttu-id="6ad71-158">Générez la Solution d’adaptateur transactionnel</span><span class="sxs-lookup"><span data-stu-id="6ad71-158">Build the Transactional Adapter Solution</span></span>  
  
1.  <span data-ttu-id="6ad71-159">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-159">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.</span></span>  
  
2.  <span data-ttu-id="6ad71-160">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter, puis double-cliquez sur **TransactionalAdapter.sln** pour ouvrir cette solution dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ad71-160">Browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter, and double-click **TransactionalAdapter.sln** to open this solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="6ad71-161">Pour générer les deux projets d’adaptateur transactionnel (Admin et Runtime) dans l’Explorateur de solutions, cliquez sur **Solution d’adaptateur transactionnel**, puis cliquez sur **reconstruire**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-161">To build both of the Transactional Adapter projects (Admin and Runtime) in Solution Explorer, right-click **Solution TransactionalAdapter**, and then click **Rebuild**.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="6ad71-162">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="6ad71-162">Running This Sample</span></span>  
  
#### <a name="register-the-transactional-adapter"></a><span data-ttu-id="6ad71-163">Inscrire l’adaptateur transactionnel</span><span class="sxs-lookup"><span data-stu-id="6ad71-163">Register the Transactional Adapter</span></span>  
  
1.  <span data-ttu-id="6ad71-164">Dans l'Explorateur Windows, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Admin.</span><span class="sxs-lookup"><span data-stu-id="6ad71-164">In Windows Explorer, navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Admin.</span></span>  
  
2.  <span data-ttu-id="6ad71-165">Pour ajouter les données de l’adaptateur transactionnel au Registre, double-cliquez sur **TransactionalAdmin.reg**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-165">To add the transactional adapter data to the registry, double-click **TransactionalAdmin.reg**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ad71-166">**TransactionalAdmin.reg** inclut des chemins codés en dur vers C:\Program Files\Microsoft BizTalk Server\\.</span><span class="sxs-lookup"><span data-stu-id="6ad71-166">**TransactionalAdmin.reg** includes hard-coded paths to C:\Program Files\Microsoft BizTalk Server\\.</span></span> <span data-ttu-id="6ad71-167">Si vous n'avez pas installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'emplacement par défaut ou si vous avez mis à niveau votre installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'une version antérieure, vous devez modifier le fichier TransactionalAdmin.reg en y indiquant les chemins d'accès appropriés.</span><span class="sxs-lookup"><span data-stu-id="6ad71-167">If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the default location or if you upgraded your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from a previous version, you must modify the file TransactionalAdmin.reg with the appropriate paths.</span></span> <span data-ttu-id="6ad71-168">Mettez à jour les chemins d'accès associés aux valeurs « InboundAssemblyPath », « OutboundAssemblyPath » et « AdapterMgmtAssemblyPath » afin qu'ils pointent vers l'emplacement correct des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6ad71-168">Update the paths associated with the "InboundAssemblyPath", "OutboundAssemblyPath", and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6ad71-169">Si vous installez BizTalk sur un ordinateur 64 bits, modifiez toutes les instances de l’entrée de Registre HKEY_CLASSES_ROOT\CLSID\ à HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ dans le **TransactionalAdmin.reg** fichier de Registre.</span><span class="sxs-lookup"><span data-stu-id="6ad71-169">If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **TransactionalAdmin.reg** registry file.</span></span>  
  
3.  <span data-ttu-id="6ad71-170">Dans le **Éditeur du Registre** boîte de dialogue, cliquez sur **Oui** à ajouter l’exemple d’adaptateur au Registre, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-170">In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6ad71-171">Pour fermer l’Explorateur Windows, cliquez sur **fichier**, puis cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-171">To close Windows Explorer, click **File**, and then click **Close**.</span></span>  
  
#### <a name="add-the-transactional-adapter-to-biztalk-server"></a><span data-ttu-id="6ad71-172">Pour ajouter l'adaptateur transactionnel à BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6ad71-172">Add the Transactional Adapter to BizTalk Server</span></span>  
  
1.  <span data-ttu-id="6ad71-173">Cliquez sur le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-173">Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6ad71-174">Dans le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le **Administration de BizTalk Server** d’arborescence, développez le **groupe BizTalk** d’arborescence, puis cliquez sur le **paramètres de plateforme** arborescence.</span><span class="sxs-lookup"><span data-stu-id="6ad71-174">In the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **BizTalk Server Administration** tree, expand the **BizTalk Group** tree, and then expand the **Platform Settings**  tree.</span></span>  
  
3.  <span data-ttu-id="6ad71-175">Avec le bouton droit **cartes**, cliquez sur **nouveau**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-175">Right-click **Adapters**, click **New**, and then click **Adapter**.</span></span>  
  
4.  <span data-ttu-id="6ad71-176">Dans le **propriétés de l’adaptateur** boîte de dialogue zone, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="6ad71-176">In the **Adapter Properties** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="6ad71-177">Utiliser</span><span class="sxs-lookup"><span data-stu-id="6ad71-177">Use this</span></span>|<span data-ttu-id="6ad71-178">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="6ad71-178">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6ad71-179">Nom</span><span class="sxs-lookup"><span data-stu-id="6ad71-179">Name</span></span>|<span data-ttu-id="6ad71-180">Type **TransactionalAdapter**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-180">Type **TransactionalAdapter**.</span></span>|  
    |<span data-ttu-id="6ad71-181">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="6ad71-181">Adapter</span></span>|<span data-ttu-id="6ad71-182">Sélectionnez **Txn** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="6ad71-182">Select **Txn** from the drop-down list.</span></span> <span data-ttu-id="6ad71-183">Cette entrée apparaît à la suite en cours d’exécution le **TransactionalAdmin.reg** fichier précédemment.</span><span class="sxs-lookup"><span data-stu-id="6ad71-183">This entry appears as a result of running the **TransactionalAdmin.reg** file previously.</span></span>|  
    |<span data-ttu-id="6ad71-184"> Description</span><span class="sxs-lookup"><span data-stu-id="6ad71-184">Description</span></span>|<span data-ttu-id="6ad71-185">Type **exemple adaptateur transactionnel**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-185">Type **Sample Transactional Adapter**.</span></span>|  
  
5.  <span data-ttu-id="6ad71-186">Cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="6ad71-186">Click **OK.**</span></span> <span data-ttu-id="6ad71-187">L'adaptateur apparaît dans la liste des adaptateurs, dans la fenêtre droite de la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6ad71-187">The adapter now appears in the list of adapters in the right window of the BizTalk Administration console.</span></span>  
  
#### <a name="create-a-receive-port-and-location-that-uses-the-adapter"></a><span data-ttu-id="6ad71-188">Pour créer un port de réception et un emplacement qui utilise l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="6ad71-188">Create a Receive Port and Location that uses the Adapter</span></span>  
  
1.  <span data-ttu-id="6ad71-189">Développez le **le groupe BizTalk [nom serveur]** nœud [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **Applications** nœud, développez **BizTalk Application 1** nœud.</span><span class="sxs-lookup"><span data-stu-id="6ad71-189">Expand the **BizTalk Group[server name]** node in [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **Applications** node, expand **BizTalk Application 1** node.</span></span>  
  
2.  <span data-ttu-id="6ad71-190">Avec le bouton droit **Ports de réception**, puis cliquez sur **nouveau**, sélectionnez **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="6ad71-190">Right-click **Receive Ports**, and then click **New**, select **One-Way Receive Port.**</span></span>  
  
3.  <span data-ttu-id="6ad71-191">Pour **nom**, entrez **TxnReceivePort1**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-191">For **Name**, enter **TxnReceivePort1**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6ad71-192">Avec le bouton droit le **emplacements de réception** nœud, cliquez sur **nouveau**, puis sélectionnez **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-192">Right-click the **Receive Locations** node, click **New**, and then select **One-Way Receive Location**.</span></span>  
  
5.  <span data-ttu-id="6ad71-193">Dans le**sélectionner un Port de réception** boîte de dialogue, sélectionnez **TxnReceivePort1**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-193">In the**Select a Receive Port** dialog box, select **TxnReceivePort1**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="6ad71-194">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, sous le **général** , entrez **TxnReceiveLocation1** pour **nom**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-194">In the **Receive Location Properties** dialog box, under the **General** tab, enter **TxnReceiveLocation1** for **Name**.</span></span> <span data-ttu-id="6ad71-195">Vérifiez le **Port de réception** étiquette affiche **TxnReceivePort1**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-195">Ensure the **Receive Port** label displays **TxnReceivePort1**.</span></span>  
  
7.  <span data-ttu-id="6ad71-196">Dans le**Type** zone, de liste déroulante dans le **Transport** frame, sélectionnez **TransactionalAdapter.**</span><span class="sxs-lookup"><span data-stu-id="6ad71-196">In the**Type** dropdown list box, in the **Transport** frame, select **TransactionalAdapter.**</span></span>  
  
8.  <span data-ttu-id="6ad71-197">Dans le **réception *** Pipeline** zone, vérifiez que **PassThruReceive** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="6ad71-197">In the **Receive****Pipeline** box, ensure **PassThruReceive** is selected.</span></span> <span data-ttu-id="6ad71-198">Conservez les paramètres par défaut pour les propriétés restantes.</span><span class="sxs-lookup"><span data-stu-id="6ad71-198">Leave the rest of the properties with their default settings.</span></span>  
  
9. <span data-ttu-id="6ad71-199">Cliquez sur le **configurer** situé en regard du **Type** zone déroulante.</span><span class="sxs-lookup"><span data-stu-id="6ad71-199">Click the **Configure** button next to the **Type** drop down box.</span></span> <span data-ttu-id="6ad71-200">Cela permet d'afficher une boîte de dialogue spécifique à cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6ad71-200">This displays a dialog specific to this adapter.</span></span> <span data-ttu-id="6ad71-201">Spécifiez les éléments suivants si nécessaire, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-201">Specify the following as you see appropriate, then click **OK**.</span></span>  
  
    |<span data-ttu-id="6ad71-202">Propriété</span><span class="sxs-lookup"><span data-stu-id="6ad71-202">Property</span></span>|<span data-ttu-id="6ad71-203">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6ad71-203">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="6ad71-204">Chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="6ad71-204">Connection String</span></span>|<span data-ttu-id="6ad71-205">Chaîne de connexion à la base de données SQL utilisée pour la connexion et l'authentification auprès de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="6ad71-205">The SQL database connection string used to connect and authenticate with the Northwind database.</span></span> <span data-ttu-id="6ad71-206">Nous exécuterons ultérieurement un script SQL qui utilisera cette base de données.</span><span class="sxs-lookup"><span data-stu-id="6ad71-206">We will later run a SQL script that will use this database.</span></span>|  
    |<span data-ttu-id="6ad71-207">Texte de la commande</span><span class="sxs-lookup"><span data-stu-id="6ad71-207">Command Text</span></span>|<span data-ttu-id="6ad71-208">Instructions SQL exécutées sur la base de données Northwind pour obtenir des données à placer dans un message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6ad71-208">The SQL statements that are executed against the Northwind database to obtain data to put into a BizTalk Message.</span></span>|  
    |<span data-ttu-id="6ad71-209">Cookie</span><span class="sxs-lookup"><span data-stu-id="6ad71-209">Cookie</span></span>|<span data-ttu-id="6ad71-210">Comprend une partie de l'URI. Entrez une valeur unique, telle que le nom de l'emplacement de réception ; par exemple, TxnReceiveLocation1.</span><span class="sxs-lookup"><span data-stu-id="6ad71-210">Comprises part of the URI so enter a unique value, such as the name of the receive location, for instance: TxnReceiveLocation1.</span></span>|  
    |<span data-ttu-id="6ad71-211">Unité intervalle d'interrogation</span><span class="sxs-lookup"><span data-stu-id="6ad71-211">Polling Interval Unit</span></span>|<span data-ttu-id="6ad71-212">Nombre d'unités de mesure de temps pour l'interrogation des données.</span><span class="sxs-lookup"><span data-stu-id="6ad71-212">The number of units of time measure for the polling of the data.</span></span> <span data-ttu-id="6ad71-213">Définissez cette propriété sur secondes.</span><span class="sxs-lookup"><span data-stu-id="6ad71-213">Set this to seconds.</span></span>|  
    |<span data-ttu-id="6ad71-214">Intervalle d’interrogation</span><span class="sxs-lookup"><span data-stu-id="6ad71-214">Polling Interval</span></span>|<span data-ttu-id="6ad71-215">Unité de mesure de temps pour l'interrogation des données.</span><span class="sxs-lookup"><span data-stu-id="6ad71-215">The unit of time measure for the polling of the data.</span></span> <span data-ttu-id="6ad71-216">Définissez cette propriété sur 15 secondes.</span><span class="sxs-lookup"><span data-stu-id="6ad71-216">Set this to 15 seconds.</span></span>|  
  
10. <span data-ttu-id="6ad71-217">Cliquez sur **OK** pour fermer la boîte de dialogue Configurer, puis **OK** à nouveau pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue pour revenir à la [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ad71-217">Click **OK** to close the Configure dialog box, then **OK** again to close the **Receive Location Properties** dialog box to return to the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
#### <a name="create-a-send-port-and-send-handler-that-use-the-adapter"></a><span data-ttu-id="6ad71-218">Pour créer un port d'envoi et un gestionnaire d'envoi qui utilisent l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="6ad71-218">Create a Send Port and Send Handler that use the Adapter</span></span>  
  
1.  <span data-ttu-id="6ad71-219">Avec la **BizTalk Application 1** toujours le nœud développé, cliquez sur **Ports d’envoi**, puis cliquez sur **nouveau**, puis sélectionnez **statique Port d’envoi unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-219">With the **BizTalk Application 1** node still expanded, right-click **Send Ports**, and then click **New**, and select **Static One-Way Send Port**.</span></span>  
  
2.  <span data-ttu-id="6ad71-220">Dans le **nom** , entrez **TxnSendPort1**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-220">In the **Name** field, enter **TxnSendPort1**.</span></span>  
  
3.  <span data-ttu-id="6ad71-221">Dans le **Transport** frame, dans le **Type** la liste déroulante, sélectionnez**TransactionalAdapter**`.`</span><span class="sxs-lookup"><span data-stu-id="6ad71-221">In the **Transport** frame, in the **Type** drop-down list, select**TransactionalAdapter**`.`</span></span>  
  
4.  <span data-ttu-id="6ad71-222">Dans le **Pipeline d’envoi** zone, vérifiez que **PassThruTransmit** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="6ad71-222">In the **Send Pipeline** box, ensure **PassThruTransmit** is selected.</span></span>  
  
5.  <span data-ttu-id="6ad71-223">Cliquez sur le **configurer** situé en regard du **transport** liste déroulante. Dans la boîte de dialogue qui s’affiche, spécifiez les éléments suivants si nécessaire, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-223">Click the **Configure** button next to the **transport** drop-down list.In the dialog that appears specify the following as you see appropriate, then click **OK**.</span></span>  
  
    |<span data-ttu-id="6ad71-224">Propriété</span><span class="sxs-lookup"><span data-stu-id="6ad71-224">Property</span></span>|<span data-ttu-id="6ad71-225">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6ad71-225">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="6ad71-226">Cookie</span><span class="sxs-lookup"><span data-stu-id="6ad71-226">Cookie</span></span>|<span data-ttu-id="6ad71-227">Comprend une partie de l’URI - Entrez une valeur unique comme le nom de l’emplacement de réception pour l’instance : **TxnSendPort1**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-227">Comprises part of the URI - Enter a unique value here such as the name of the receive location, for instance: **TxnSendPort1**.</span></span>|  
    |<span data-ttu-id="6ad71-228">Chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="6ad71-228">Connection String</span></span>|<span data-ttu-id="6ad71-229">Chaîne de connexion à la base de données SQL utilisée pour la connexion et l'authentification auprès de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="6ad71-229">The SQL database connection string used to connect and authenticate with the Northwind database.</span></span> <span data-ttu-id="6ad71-230">Il s’agira probablement le même que celui utilisé pour configurer le **TxnReceiveLocation1** emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="6ad71-230">It will most likely be the same one used to configure the **TxnReceiveLocation1** receive location.</span></span>|  
    |<span data-ttu-id="6ad71-231">Procédure stockée</span><span class="sxs-lookup"><span data-stu-id="6ad71-231">Stored Procedure</span></span>|<span data-ttu-id="6ad71-232">Le nom de procédure stockée exécuté pour interroger la base de données - **sp_txnProc**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-232">The stored procedure name that gets executed to poll the database - **sp_txnProc**.</span></span> <span data-ttu-id="6ad71-233">Le corps du message est transmis à que BizTalk de procédure stockée comme paramètre de chaîne appelé @Data.</span><span class="sxs-lookup"><span data-stu-id="6ad71-233">The body of the BizTalk message is given to that stored procedure as a string parameter called @Data.</span></span> <span data-ttu-id="6ad71-234">Par exemple, l’utilisateur dans ce cas plus tard configurera la procédure stockée avec le nom **sp_txnProc**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-234">For example, the user will in this case later configure the stored procedure with the name **sp_txnProc**.</span></span> <span data-ttu-id="6ad71-235">L'exécution de l'adaptateur exécuterait l'équivalent de cet appel à la base de données.</span><span class="sxs-lookup"><span data-stu-id="6ad71-235">The runtime of the adapter would execute the equivalent of this call to the database.</span></span><br /><br /> <span data-ttu-id="6ad71-236">EXEC sp_txnProc @Data = « le contenu du message BizTalk »</span><span class="sxs-lookup"><span data-stu-id="6ad71-236">exec sp_txnProc @Data = “the contents of the BizTalk message”</span></span>|  
  
6.  <span data-ttu-id="6ad71-237">Dans le volet de navigation gauche, cliquez sur **filtre**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-237">In the left navigation pane, click **Filter**.</span></span>  
  
7.  <span data-ttu-id="6ad71-238">Dans l'éditeur d'expression de filtre, entrez l'expression suivante pour définir un abonnement à ce port d'envoi et obtenir les messages reçus par le port de réception TxnReceivePort1.</span><span class="sxs-lookup"><span data-stu-id="6ad71-238">In the filter expression editor, enter the following expression to set up a subscription for this send port to receive any messages received by the TxnReceivePort1 receive port.</span></span>  
  
     <span data-ttu-id="6ad71-239">Entrez ces valeurs :**BTS. ReceivePortName == TxnReceivePort1**</span><span class="sxs-lookup"><span data-stu-id="6ad71-239">Enter these values:**BTS.ReceivePortName== TxnReceivePort1**</span></span>  
  
    1.  <span data-ttu-id="6ad71-240">`(property)`  **BIZTALK SERVER. ReceivePortName**</span><span class="sxs-lookup"><span data-stu-id="6ad71-240">`(property)`  **BTS.ReceivePortName**</span></span>  
  
    2.  <span data-ttu-id="6ad71-241">`(operator)`  **==**</span><span class="sxs-lookup"><span data-stu-id="6ad71-241">`(operator)`  **==**</span></span>  
  
    3.  <span data-ttu-id="6ad71-242">`(value)`  **TxnReceivePort1**</span><span class="sxs-lookup"><span data-stu-id="6ad71-242">`(value)`  **TxnReceivePort1**</span></span>  
  
8.  <span data-ttu-id="6ad71-243">Utilisez les valeurs par défaut pour le reste des propriétés de l’adaptateur et sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-243">Use the default values for the remainder of the adapter properties and select **OK**.</span></span>  
  
## <a name="run-the-sample"></a><span data-ttu-id="6ad71-244">Exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-244">Run the sample</span></span>  
  
1.  <span data-ttu-id="6ad71-245">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, sélectionnez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-245">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, select **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="6ad71-246">Dans le **se connecter au serveur** boîte de dialogue zone, assurez-vous que **Type de serveur** a la valeur **moteur de base de données**, entrez les informations d’identification pour s’authentifier auprès du serveur de base de données, puis sélectionnez  **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-246">In the **Connect to Server** dialog box, make sure **Server Type** is set to **Database Engine**, and enter credentials to authenticate to the database server, then select **Connect**.</span></span>  
  
3.  <span data-ttu-id="6ad71-247">Sélectionnez le **nouvelle requête** bouton de barre d’outils et collez le code suivant dans la nouvelle fenêtre de requête pour insérer une table de test, les données de test et un test de procédure stockée dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="6ad71-247">Select the **New Query** toolbar button and paste the following into the new query window to insert a test table, test data, and a test stored procedure into the Northwind database.</span></span> <span data-ttu-id="6ad71-248">Sélectionnez le **Execute** bouton de barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="6ad71-248">Select the **Execute** toolbar button.</span></span>  
  
    ```  
    use [Northwind]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[scratch]') and OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    drop table [dbo].[scratch]  
    GO  
    CREATE TABLE [dbo].[scratch] (  
         [id] [int] IDENTITY (1, 1) NOT NULL ,  
         [msg] [nvarchar] (4000) NOT NULL   
    ) ON [PRIMARY]  
    GO  
    GRANT SELECT , UPDATE , INSERT ON [dbo].[scratch] TO [public]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_txnProc]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
    drop procedure [dbo].[sp_txnProc]  
    GO  
    CREATE PROCEDURE [dbo].[sp_txnProc] @Data nvarchar (4000)  
    AS   
    INSERT scratch ( msg ) values ( @Data )  
    GO  
    GRANT EXECUTE ON [dbo].[sp_txnProc] TO [public]  
    GO  
    ```  
  
4.  <span data-ttu-id="6ad71-249">Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le **Ports d’envoi** nœud, sélectionnez le **TxnSendPort1** port d’envoi, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-249">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **Send Ports** node, select the **TxnSendPort1** send port, and select **Start**.</span></span>  
  
5.  <span data-ttu-id="6ad71-250">Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le **ReceiveLocations** nœud, sélectionnez le **TxnRecieveLocation1** emplacement de réception, puis sélectionnez **activer**.</span><span class="sxs-lookup"><span data-stu-id="6ad71-250">In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the **ReceiveLocations** node, select the **TxnRecieveLocation1** receive location, and then select **Enable**.</span></span>  
  
6.  <span data-ttu-id="6ad71-251">Une fois l'emplacement de réception activé, il interroge automatiquement la base de données aux intervalles définis pour obtenir des données.</span><span class="sxs-lookup"><span data-stu-id="6ad71-251">Once the receive location is enabled, it will automatically poll the database at the designated intervals for data.</span></span>  
  
## <a name="classes-or-methods-used-in-the-sample"></a><span data-ttu-id="6ad71-252">Classes ou méthodes utilisées dans l’exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-252">Classes or Methods Used in the sample</span></span>  
* <span data-ttu-id="6ad71-253">Interface IBTTransmitterBatch (COM)</span><span class="sxs-lookup"><span data-stu-id="6ad71-253">IBTTransmitterBatch Interface (COM)</span></span>
  
* <span data-ttu-id="6ad71-254">Interface IBTTransportProxy (COM)</span><span class="sxs-lookup"><span data-stu-id="6ad71-254">IBTTransportProxy Interface (COM)</span></span>

<span data-ttu-id="6ad71-255">Ces méthodes sont décrites [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="6ad71-255">These methods are described [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="6ad71-256">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ad71-256">See Also</span></span>  
 <span data-ttu-id="6ad71-257">[Exemples d’adaptateurs - développement](../core/adapter-samples-development.md) </span><span class="sxs-lookup"><span data-stu-id="6ad71-257">[Adapter Samples - Development](../core/adapter-samples-development.md) </span></span>  
 [<span data-ttu-id="6ad71-258">Inscription d’un adaptateur</span><span class="sxs-lookup"><span data-stu-id="6ad71-258">Registering an Adapter</span></span>](../core/registering-an-adapter.md)