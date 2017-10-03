---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour PeopleSoft Enterprise pour écrire des données vers PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837dd4db-576d-41c1-9fe8-e1e46861270b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9c4c0714c28f426ccfaa2799bd16463124e6e52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-peoplesoft-enterprise-to-write-data-to-peoplesoft-enterprise"></a><span data-ttu-id="512b7-102">Didacticiel : écriture de données vers PeopleSoft Enterprise à l'aide de l'adaptateur BizTalk pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="512b7-102">Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Write Data to PeopleSoft Enterprise</span></span>
<span data-ttu-id="512b7-103">L'adaptateur BizTalk pour PeopleSoft Enterprise permet d'écrire des données dans un système PeopleSoft à l'aide des informations reçues d'un partenaire commercial ou d'une application interne.</span><span class="sxs-lookup"><span data-stu-id="512b7-103">The BizTalk Adapter for PeopleSoft Enterprise can be used to write data to a PeopleSoft System with information received from a trading partner or internal application.</span></span> <span data-ttu-id="512b7-104">Cette procédure pas à pas décrit un exemple de Kit de développement logiciel (SDK) qui illustre ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="512b7-104">This walkthrough describes an SDK sample that illustrates this functionality.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="512b7-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="512b7-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="512b7-106">La plateforme Java 2 doit être installée sur la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur BizTalk pour PeopleSoft Enterprise est exécuté.</span><span class="sxs-lookup"><span data-stu-id="512b7-106">The Java 2 Platform must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.</span></span>  
  
-   <span data-ttu-id="512b7-107">Le fichier JAR de l’adaptateur d’objet Java PeopleSoft, **psjoa.jar** doivent être copiés vers un dossier qui est accessible à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] que l’adaptateur BizTalk pour PeopleSoft Enterprise est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="512b7-107">The PeopleSoft Java Object Adapter JAR file, **psjoa.jar** should be copied to a folder that is accessible to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.</span></span>  
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="512b7-108"> doit être installé sur la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur BizTalk pour PeopleSoft Enterprise est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="512b7-108"> must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="512b7-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="512b7-109">What This Sample Does</span></span>  
 <span data-ttu-id="512b7-110">Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour PeopleSoft Enterprise pour créer un enregistrement dans le système PeopleSoft pour les données dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="512b7-110">This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for PeopleSoft Enterprise to create a record in the PeopleSoft system from the data in the XML file.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="512b7-111">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="512b7-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="512b7-112">Cet exemple a été conçu dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et créé pour illustrer les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour PeopleSoft Enterprise avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="512b7-112">This sample was designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and was created to illustrate basic functionality using the BizTalk Adapter for PeopleSoft Enterprise with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="512b7-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="512b7-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="512b7-114">L'exemple se trouve dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="512b7-114">The sample is located in the following folder:</span></span>  
  
 <span data-ttu-id="512b7-115">\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftOneWaySend</span><span class="sxs-lookup"><span data-stu-id="512b7-115">\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftOneWaySend</span></span>  
  
 <span data-ttu-id="512b7-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="512b7-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="512b7-117">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="512b7-117">**Runtime Project Filename**</span></span>|<span data-ttu-id="512b7-118">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="512b7-118">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="512b7-119">OneWaySend.btproj,</span><span class="sxs-lookup"><span data-stu-id="512b7-119">OneWaySend.btproj,</span></span><br /><br /> <span data-ttu-id="512b7-120">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="512b7-120">OneWaySend.sln</span></span>|<span data-ttu-id="512b7-121">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="512b7-121">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="512b7-122">LOCATIONService.xsd,</span><span class="sxs-lookup"><span data-stu-id="512b7-122">LOCATIONService.xsd,</span></span><br /><br /> <span data-ttu-id="512b7-123">LOCATIONService_1.xsd,</span><span class="sxs-lookup"><span data-stu-id="512b7-123">LOCATIONService_1.xsd,</span></span><br /><br /> <span data-ttu-id="512b7-124">LOCATIONService_2.xsd</span><span class="sxs-lookup"><span data-stu-id="512b7-124">LOCATIONService_2.xsd</span></span>|<span data-ttu-id="512b7-125">Fichiers de schéma de l'application.</span><span class="sxs-lookup"><span data-stu-id="512b7-125">Schema files for the application.</span></span> <span data-ttu-id="512b7-126">**Remarque :** les fichiers de schéma de l’adaptateur dans le projet ont été créés à l’aide de la **Assistant Ajouter les métadonnées de l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="512b7-126">**Note:**  The adapter schema files in the project were originally created using the **Add Adapter Metadata Wizard**.</span></span> <span data-ttu-id="512b7-127">Pour plus d'informations sur l'Assistant Ajouter les métadonnées de l'adaptateur, consultez la rubrique « Ajout de métadonnées d'adaptateur à un projet BizTalk » de la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="512b7-127">For more information on the Add Adapter Metadata Wizard see the topic "How to Add Adapter Metadata to a BizTalk Project" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>|  
|<span data-ttu-id="512b7-128">PeopleSoftOneWaySend.odx</span><span class="sxs-lookup"><span data-stu-id="512b7-128">PeopleSoftOneWaySend.odx</span></span>|<span data-ttu-id="512b7-129">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="512b7-129">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="512b7-130">PeopleSoftOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="512b7-130">PeopleSoftOneWaySend.snk</span></span>|<span data-ttu-id="512b7-131">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="512b7-131">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="512b7-132">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="512b7-132">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-peoplesoft-enterprise-adapter"></a><span data-ttu-id="512b7-133">Pour créer une instance de l'adaptateur PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="512b7-133">Create a new instance of the PeopleSoft Enterprise adapter</span></span>  
  
1.  <span data-ttu-id="512b7-134">Lancer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="512b7-134">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="512b7-135">Cliquez sur **Démarrer**, **tous les programmes**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="512b7-135">Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="512b7-136">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.</span><span class="sxs-lookup"><span data-stu-id="512b7-136">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="512b7-137">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...**</span><span class="sxs-lookup"><span data-stu-id="512b7-137">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="512b7-138">Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-138">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="512b7-139">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoft**.</span><span class="sxs-lookup"><span data-stu-id="512b7-139">Enter a value for the **Name** field, for example **PeopleSoft**.</span></span>  
  
5.  <span data-ttu-id="512b7-140">Sélectionnez **PeopleSoft Enterprise (r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="512b7-140">Select **PeopleSoft Enterprise(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-send-port"></a><span data-ttu-id="512b7-141">Pour créer un port d'envoi BizTalk</span><span class="sxs-lookup"><span data-stu-id="512b7-141">Create a BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="512b7-142">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="512b7-142">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="512b7-143">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-143">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="512b7-144">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftOneWaySP**.</span><span class="sxs-lookup"><span data-stu-id="512b7-144">Enter a value for the **Name** field, for example **PeopleSoftOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="512b7-145">Sélectionnez l’adaptateur PeopleSoft dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport**boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-145">Select the PeopleSoft adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="512b7-146">Cette valeur correspond au nom spécifié lors de la création de l'adaptateur PeopleSoft Enterprise dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="512b7-146">This value is the name that was specified when the PeopleSoft Enterprise adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="512b7-147">Entrez les valeurs suivantes pour le **propriétés obligatoires de l’adaptateur**:</span><span class="sxs-lookup"><span data-stu-id="512b7-147">Enter the following values for the **Adapter Required Properties**:</span></span>  
  
    |<span data-ttu-id="512b7-148">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="512b7-148">**Property**</span></span>|<span data-ttu-id="512b7-149">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="512b7-149">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="512b7-150">Chemin d'accès au serveur de l'application</span><span class="sxs-lookup"><span data-stu-id="512b7-150">Application server path</span></span>|<span data-ttu-id="512b7-151">Emplacement de l'ordinateur et du port du serveur de PeopleSoft, par exemple //PSServer:8888</span><span class="sxs-lookup"><span data-stu-id="512b7-151">PeopleSoft Server's machine and port location, for example //PSServer:8888.</span></span> <span data-ttu-id="512b7-152">**Remarque :** si vous ne spécifiez pas un numéro de port, le port par défaut (9000) est utilisé pour l’exemple ci-dessus, vous pouvez entrer la valeur //psserver si le serveur de PeopleSoft utilise la valeur de port par défaut (9000).</span><span class="sxs-lookup"><span data-stu-id="512b7-152">**Note:**  If you do not specify a port number, the default port of 9000 is used so in the example above you could enter a value of //PSServer if the PeopleSoft Server uses the default port value of 9000.</span></span>|  
    |<span data-ttu-id="512b7-153">JAVA_HOME</span><span class="sxs-lookup"><span data-stu-id="512b7-153">JAVA_HOME</span></span>|<span data-ttu-id="512b7-154">Chemin d'accès au répertoire de base associé aux fichiers du Kit de développement logiciel de la plateforme Java 2, par exemple C:\j2sdk1.4.2_08</span><span class="sxs-lookup"><span data-stu-id="512b7-154">Path to the home directory associated with the Java 2 Platform SDK files, for example C:\j2sdk1.4.2_08</span></span>|  
    |<span data-ttu-id="512b7-155">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="512b7-155">Password</span></span>|<span data-ttu-id="512b7-156">Mot de passe de connexion au système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="512b7-156">Password used when connecting to the PeopleSoft system.</span></span>|  
    |<span data-ttu-id="512b7-157">Fichiers JAR PeopleSoft 8.x</span><span class="sxs-lookup"><span data-stu-id="512b7-157">PeopleSoft 8.x JAR files</span></span>|<span data-ttu-id="512b7-158">Emplacement du fichier JAR de l’adaptateur d’objet Java PeopleSoft, **psjoa.jar**, par exemple C:\JARS\psjoa.jar.</span><span class="sxs-lookup"><span data-stu-id="512b7-158">Location of the PeopleSoft Java Object Adapter JAR file, **psjoa.jar**, for example C:\JARS\psjoa.jar.</span></span>|  
    |<span data-ttu-id="512b7-159">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="512b7-159">User name</span></span>|<span data-ttu-id="512b7-160">Nom d'utilisateur pour la connexion au système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="512b7-160">Username for connecting to the PeopleSoft system.</span></span>|  
  
6.  <span data-ttu-id="512b7-161">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="512b7-161">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="512b7-162">Sélectionnez le **XML Transmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="512b7-162">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="512b7-163">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="512b7-163">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="512b7-164">Pour créer un port de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="512b7-164">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="512b7-165">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="512b7-165">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="512b7-166">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel** pour afficher la boîte de dialogue Propriétés du Port de réception.</span><span class="sxs-lookup"><span data-stu-id="512b7-166">Right-click the Receive Ports folder and then click **New**, **One-way Receive Port** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="512b7-167">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftOneWayFileRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="512b7-167">Enter a value for the **Name** field, for example **PeopleSoftOneWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="512b7-168">Pour créer un emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="512b7-168">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="512b7-169">Créez un dossier à surveiller par l'emplacement de réception du fichier (par exemple, C:\Filesource).</span><span class="sxs-lookup"><span data-stu-id="512b7-169">Create a folder to be monitored by the file receive location, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="512b7-170">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception** pour afficher les **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-170">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="512b7-171">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftOneWayFileRL**.</span><span class="sxs-lookup"><span data-stu-id="512b7-171">Enter a value for the **Name** field, for example **PeopleSoftOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="512b7-172">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-172">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="512b7-173">Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="512b7-173">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="512b7-174">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="512b7-174">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="512b7-175">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="512b7-175">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="modify-the-adapter-schema-target-namespace-property"></a><span data-ttu-id="512b7-176">Pour modifier la propriété d'espace de noms cible du schéma de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="512b7-176">Modify the Adapter schema target namespace property</span></span>  
  
1.  <span data-ttu-id="512b7-177">Lancez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et ouvrez le fichier OneWaySend.sln.</span><span class="sxs-lookup"><span data-stu-id="512b7-177">Launch [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and open OneWaySend.sln.</span></span> <span data-ttu-id="512b7-178">Cliquez sur **fichier**, **ouvrir**, **projet/Solution...**</span><span class="sxs-lookup"><span data-stu-id="512b7-178">Click **File**, **Open**, **Project/Solution…**</span></span> <span data-ttu-id="512b7-179">Pour afficher le **ouvrir le projet** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-179">to display the **Open Project** dialog.</span></span>  
  
2.  <span data-ttu-id="512b7-180">Accédez au fichier OneWaySend.sln, sélectionnez-le et cliquez sur **ouvrir** pour ouvrir la solution qui contient l’exemple de projet.</span><span class="sxs-lookup"><span data-stu-id="512b7-180">Browse to the OneWaySend.sln file, click to select this file and click **Open** to open the solution that contains the sample project.</span></span>  
  
3.  <span data-ttu-id="512b7-181">Cliquez sur le **vue** menu et sélectionnez **l’Explorateur de solutions** pour afficher l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="512b7-181">Click the **View** menu and select **Solution Explorer** to display the Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="512b7-182">Double-cliquez sur le fichier LOCATIONService_1.xsd dans l'Explorateur de solutions pour l'ouvrir.</span><span class="sxs-lookup"><span data-stu-id="512b7-182">Double-click the LOCATIONService_1.xsd file in the Solution Explorer to open it.</span></span>  
  
5.  <span data-ttu-id="512b7-183">Avec le bouton droit le **schéma** nœud de locationservice_1.xsd, puis sélectionnez le **propriétés** option de menu pour afficher les propriétés pour le schéma.</span><span class="sxs-lookup"><span data-stu-id="512b7-183">Right-click the **Schema** node of LOCATIONService_1.xsd and select the **Properties** menu option to display the properties for the schema.</span></span>  
  
6.  <span data-ttu-id="512b7-184">Modifier la **cible Namespace** propriété à utiliser les valeurs appropriées pour le nom de l’adaptateur, par exemple le **cible Namespace** propriété doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="512b7-184">Edit the **Target Namespace** property to use the appropriate values for the adapter name, for example the **Target Namespace** property should read as follows:</span></span>  
  
    ```  
    http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
    ```  
  
     <span data-ttu-id="512b7-185">Où *PeopleSoft* est le nom de l’adaptateur PeopleSoft, tel qu’affiché dans la Console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="512b7-185">Where *PeopleSoft* is the name of the PeopleSoft adapter as viewed in the BizTalk Administration Console.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="512b7-186">Si la valeur configurée pour **cible Namespace** ne correspond pas à l’espace de noms spécifié dans l’instance de document d’entrée, un échec de routage se produit lorsque l’instance de document d’entrée est traitée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="512b7-186">If the configured value for **Target Namespace** does not match the namespace specified in the input document instance then a routing failure will occur when the input document instance is processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a><span data-ttu-id="512b7-187">Pour générer une instance de document à partir du schéma de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="512b7-187">Generate a document instance from the Adapter schema</span></span>  
  
1.  <span data-ttu-id="512b7-188">Double-cliquez sur **LOCATIONService_1.xsd** dans l’Explorateur de solutions pour ouvrir le fichier dans l’éditeur de schéma.</span><span class="sxs-lookup"><span data-stu-id="512b7-188">Double-click **LOCATIONService_1.xsd** in the Solution Explorer to open the file in the Schema Editor.</span></span>  
  
2.  <span data-ttu-id="512b7-189">Avec le bouton droit le  **\<schéma >** nœud dans l’éditeur de schéma, puis cliquez sur **propriétés** pour afficher les propriétés du nœud.</span><span class="sxs-lookup"><span data-stu-id="512b7-189">Right-click the **\<Schema>** node in the Schema Editor, and click **Properties** to display the properties for the node.</span></span>  
  
3.  <span data-ttu-id="512b7-190">Sélectionnez **CreateEx** dans la liste des nœuds disponibles dans le **référence de racine** zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="512b7-190">Select **CreateEx** from the list of available nodes in the **Root Reference** dropdown box.</span></span> <span data-ttu-id="512b7-191">Cela doit être fait afin que lorsque vous générez un exemple d’instance de document, il sera générée depuis le **CreateEx** nœud du schéma.</span><span class="sxs-lookup"><span data-stu-id="512b7-191">This should be done so that when you generate a sample document instance it will be generated from the **CreateEx** node of the schema.</span></span>  
  
4.  <span data-ttu-id="512b7-192">Cliquez sur LOCATIONService_1.xsd dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="512b7-192">Right-click LOCATIONService_1.xsd in Solution Explorer and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="512b7-193">Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** sous le **général** section.</span><span class="sxs-lookup"><span data-stu-id="512b7-193">In the Properties window, click to select the **Output Instance Filename** option under the **General** section.</span></span>  
  
6.  <span data-ttu-id="512b7-194">Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-194">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
7.  <span data-ttu-id="512b7-195">Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="512b7-195">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="512b7-196">Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="512b7-196">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
8.  <span data-ttu-id="512b7-197">Cliquez sur LOCATIONService_1.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="512b7-197">Right-click LOCATIONService_1.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
9. <span data-ttu-id="512b7-198">Avec le bouton droit le  **\<schéma >** nœud dans l’éditeur de schéma, puis cliquez sur **propriétés** pour afficher les propriétés du nœud.</span><span class="sxs-lookup"><span data-stu-id="512b7-198">Right-click the **\<Schema>** node in the Schema Editor, and click **Properties** to display the properties for the node.</span></span>  
  
10. <span data-ttu-id="512b7-199">Sélectionnez (**par défaut)** dans la liste des nœuds disponibles dans le **référence de racine** zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="512b7-199">Select (**Default)** from the list of available nodes in the **Root Reference** dropdown box.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="512b7-200">Pour modifier l'instance de document générée</span><span class="sxs-lookup"><span data-stu-id="512b7-200">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="512b7-201">Ouvrez l'instance de document générée dans un éditeur de texte tel que le Bloc-notes et modifiez le contenu de telle sorte que les données de ces champs génèrent un enregistrement unique dans le système PeopleSoft : par exemple, le fichier XML ci-dessous décrit les champs d'un enregistrement qui définit un emplacement :</span><span class="sxs-lookup"><span data-stu-id="512b7-201">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data in these fields will generate a unique record in the PeopleSoft system, for example the XML file below describes the fields in a record that define a location:</span></span>  
  
    ```  
    <ns0:CreateEx xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>9991</ns0:LOCATION>  
      <ns0:interactiveMode>true</ns0:interactiveMode>  
       <ns0:properties>  
        <ns0:LOCATION_TBL_sequence>  
          <ns0:LOCATION_TBL>  
            <ns0:COUNTRY>USA</ns0:COUNTRY>  
            <ns0:DESCR>Adapter Test</ns0:DESCR>  
            <ns0:EFFDT>2006-05-31</ns0:EFFDT>  
            <ns0:EFF_STATUS>A</ns0:EFF_STATUS>  
            <ns0:SETID>SHARE</ns0:SETID>  
          </ns0:LOCATION_TBL>  
        </ns0:LOCATION_TBL_sequence>  
      </ns0:properties>  
    </ns0:CreateEx>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="512b7-202">Dans l’exemple ci-dessus, *PeopleSoft* est un espace réservé pour le nom réel de la carte tel qu’affiché dans la Console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="512b7-202">In the example above, *PeopleSoft* is a placeholder for the actual name of the adapter as viewed in the BizTalk Administration Console.</span></span>  
  
2.  <span data-ttu-id="512b7-203">Enregistrez l'instance de document modifiée.</span><span class="sxs-lookup"><span data-stu-id="512b7-203">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="512b7-204">création et déploiement du projet ;</span><span class="sxs-lookup"><span data-stu-id="512b7-204">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="512b7-205">Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="512b7-205">Right-click the OneWaySend project in Solution Explorer and click **Properties** to launch the Project Designer.</span></span>  
  
2.  <span data-ttu-id="512b7-206">Cliquez sur le **déploiement** onglet.</span><span class="sxs-lookup"><span data-stu-id="512b7-206">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="512b7-207">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="512b7-207">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="512b7-208">Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="512b7-208">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="512b7-209">Pour lier et inscrire l'orchestration</span><span class="sxs-lookup"><span data-stu-id="512b7-209">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="512b7-210">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="512b7-210">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="512b7-211">Cliquez sur le **Actualiser** bouton dans la barre d’outils MMC ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="512b7-211">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console view.</span></span>  
  
3.  <span data-ttu-id="512b7-212">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="512b7-212">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="512b7-213">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="512b7-213">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="512b7-214">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="512b7-214">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="512b7-215">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="512b7-215">**Parameter**</span></span>|<span data-ttu-id="512b7-216">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="512b7-216">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="512b7-217">Hôte</span><span class="sxs-lookup"><span data-stu-id="512b7-217">Host</span></span>|<span data-ttu-id="512b7-218">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="512b7-218">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="512b7-219">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="512b7-219">FileReceivePort</span></span>|<span data-ttu-id="512b7-220">PeopleSoftOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="512b7-220">PeopleSoftOneWayFileRP</span></span>|  
    |<span data-ttu-id="512b7-221">PeopleSoftOneWaySendPort</span><span class="sxs-lookup"><span data-stu-id="512b7-221">PeopleSoftOneWaySendPort</span></span>|<span data-ttu-id="512b7-222">PeopleSoftOneWaySP</span><span class="sxs-lookup"><span data-stu-id="512b7-222">PeopleSoftOneWaySP</span></span>|  
  
6.  <span data-ttu-id="512b7-223">Cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="512b7-223">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="512b7-224">Démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="512b7-224">Start the orchestration</span></span>  
  
-   <span data-ttu-id="512b7-225">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="512b7-225">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="512b7-226">Pour placer une instance de document dans le dossier surveillé par l'emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="512b7-226">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="512b7-227">Copiez l'instance de document créée précédemment dans le dossier surveillé par l'emplacement de réception du fichier.</span><span class="sxs-lookup"><span data-stu-id="512b7-227">Copy the document instance that was created earlier to the folder that the file receive location is configured to monitor.</span></span>  
  
#### <a name="verify-that-the-peoplesoft-system-is-updated"></a><span data-ttu-id="512b7-228">Pour vérifier la mise à jour du système PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="512b7-228">Verify that the PeopleSoft system is updated</span></span>  
  
-   <span data-ttu-id="512b7-229">Utilisez l'interface Web PeopleSoft pour vérifier que l'enregistrement a été créé à partir des données du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="512b7-229">Use the PeopleSoft web interface to verify that the record was created from the data in the XML file.</span></span>  
  
 <span data-ttu-id="512b7-230">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="512b7-230">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="512b7-231">L'adaptateur FILE récupère le fichier dans le dossier et le publie dans la base de données MessageBox comme message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="512b7-231">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="512b7-232">L'orchestration s'abonne à ce message publié et le moteur de messagerie BizTalk active une instance de l'orchestration avant d'envoyer le message à l'instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="512b7-232">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="512b7-233">L'instance d'orchestration traite le message à l'aide de la logique spécifiée dans l'orchestration, puis republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="512b7-233">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="512b7-234">Le port d'envoi PeopleSoft s'abonne à ce message publié et le moteur de messagerie BizTalk envoie le message au port d'envoi PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="512b7-234">The PeopleSoft send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the PeopleSoft send port.</span></span>  
  
5.  <span data-ttu-id="512b7-235">Le port d'envoi remet le message à l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="512b7-235">The send port hands the message to the BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
6.  <span data-ttu-id="512b7-236">L'adaptateur BizTalk pour PeopleSoft Enterprise appelle la méthode CreateEx pour créer un enregistrement à l'aide des données du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="512b7-236">The BizTalk Adapter for PeopleSoft Enterprise invokes the CreateEx method to create a record using the data in the XML file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512b7-237">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="512b7-237">See Also</span></span>  
 [<span data-ttu-id="512b7-238">Didacticiels : À l’aide de l’adaptateur BizTalk pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="512b7-238">Tutorials: Using BizTalk Adapter for PeopleSoft Enterprise</span></span>](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)