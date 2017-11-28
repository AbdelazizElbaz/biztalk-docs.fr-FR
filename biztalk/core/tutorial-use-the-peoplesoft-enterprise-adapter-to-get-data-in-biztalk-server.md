---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour PeopleSoft Enterprise pour récupérer des données à partir de PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c173fa4c-911e-4fa3-813f-e8f36b0049a5
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 823bd5739ac58d8b63f79ee15102cf44f3d82c7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-peoplesoft-enterprise-to-retrieve-data-from-peoplesoft-enterprise"></a><span data-ttu-id="845ba-102">Didacticiel : extraction de données vers PeopleSoft Enterprise à l'aide de l'adaptateur BizTalk de PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="845ba-102">Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Retrieve Data from PeopleSoft Enterprise</span></span>
<span data-ttu-id="845ba-103">L'adaptateur BizTalk pour PeopleSoft Enterprise permet d'exécuter une requête sur un système PeopleSoft et de renvoyer les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="845ba-103">The BizTalk Adapter for PeopleSoft Enterprise can be used to execute a query against a PeopleSoft system and return the results of the query.</span></span> <span data-ttu-id="845ba-104">Cette procédure pas à pas décrit un exemple de Kit de développement logiciel (SDK) qui illustre ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="845ba-104">This walkthrough describes an SDK sample that illustrates this functionality.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="845ba-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="845ba-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="845ba-106">La plateforme Java 2 doit être installée sur la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur BizTalk pour PeopleSoft Enterprise Geis est exécuté.</span><span class="sxs-lookup"><span data-stu-id="845ba-106">The Java 2 Platform must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise Geis running on.</span></span>  
  
-   <span data-ttu-id="845ba-107">Le fichier JAR de l’adaptateur d’objet Java PeopleSoft, **psjoa.jar** doivent être copiés vers un dossier qui est accessible à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] que l’adaptateur BizTalk pour PeopleSoft Enterprise est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="845ba-107">The PeopleSoft Java Object Adapter JAR file, **psjoa.jar** should be copied to a folder that is accessible to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.</span></span>  
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="845ba-108"> doit être installé sur la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur BizTalk pour PeopleSoft Enterprise est exécuté afin de créer et de déployer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="845ba-108"> must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="845ba-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="845ba-109">What This Sample Does</span></span>  
 <span data-ttu-id="845ba-110">Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour PeopleSoft Enterprise pour exécuter une requête dans le système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="845ba-110">This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for PeopleSoft Enterprise to execute a query against a PeopleSoft system.</span></span> <span data-ttu-id="845ba-111">Le résultat de la requête est écrit dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="845ba-111">The result of the query is written to an XML file.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="845ba-112">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="845ba-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="845ba-113">Cet exemple a été conçu dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et créé pour illustrer les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour PeopleSoft Enterprise avec une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="845ba-113">This sample was designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and was created to illustrate basic functionality using the BizTalk Adapter for PeopleSoft Enterprise with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="845ba-114">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="845ba-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="845ba-115">L'exemple se trouve dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="845ba-115">The sample is located in the following folder:</span></span>  
  
 <span data-ttu-id="845ba-116">\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftTwoWaySend</span><span class="sxs-lookup"><span data-stu-id="845ba-116">\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftTwoWaySend</span></span>  
  
 <span data-ttu-id="845ba-117">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="845ba-117">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="845ba-118">**Nom de fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="845ba-118">**Runtime Project Filename**</span></span>|<span data-ttu-id="845ba-119">**Description du fichier de projet d’exécution**</span><span class="sxs-lookup"><span data-stu-id="845ba-119">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="845ba-120">TwoWaySend.btproj,</span><span class="sxs-lookup"><span data-stu-id="845ba-120">TwoWaySend.btproj,</span></span><br /><br /> <span data-ttu-id="845ba-121">TwoWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="845ba-121">TwoWaySend.sln</span></span>|<span data-ttu-id="845ba-122">Fichiers de projet et de solution de l'application.</span><span class="sxs-lookup"><span data-stu-id="845ba-122">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="845ba-123">LOCATIONService.xsd,</span><span class="sxs-lookup"><span data-stu-id="845ba-123">LOCATIONService.xsd,</span></span><br /><br /> <span data-ttu-id="845ba-124">LOCATIONService_1.xsd,</span><span class="sxs-lookup"><span data-stu-id="845ba-124">LOCATIONService_1.xsd,</span></span><br /><br /> <span data-ttu-id="845ba-125">LOCATIONService_2.xsd</span><span class="sxs-lookup"><span data-stu-id="845ba-125">LOCATIONService_2.xsd</span></span>|<span data-ttu-id="845ba-126">Fichiers de schéma de l'application.</span><span class="sxs-lookup"><span data-stu-id="845ba-126">Schema files for the application.</span></span> <span data-ttu-id="845ba-127">**Remarque :** les fichiers de schéma de l’adaptateur dans le projet ont été créés à l’aide de la **Assistant Ajouter les métadonnées de l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="845ba-127">**Note:**  The adapter schema files in the project were originally created using the **Add Adapter Metadata Wizard**.</span></span> <span data-ttu-id="845ba-128">Pour plus d'informations sur l'Assistant Ajouter les métadonnées de l'adaptateur, consultez la rubrique « Ajout de métadonnées d'adaptateur à un projet BizTalk » de la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="845ba-128">For more information on the Add Adapter Metadata Wizard see the topic "How to Add Adapter Metadata to a BizTalk Project" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>|  
|<span data-ttu-id="845ba-129">PeopleSoftTwoWaySend.odx</span><span class="sxs-lookup"><span data-stu-id="845ba-129">PeopleSoftTwoWaySend.odx</span></span>|<span data-ttu-id="845ba-130">Orchestration utilisée par l'application.</span><span class="sxs-lookup"><span data-stu-id="845ba-130">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="845ba-131">PeopleSoftTwoWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="845ba-131">PeopleSoftTwoWaySend.snk</span></span>|<span data-ttu-id="845ba-132">Fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="845ba-132">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="845ba-133">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="845ba-133">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-peoplesoft-enterprise-adapter"></a><span data-ttu-id="845ba-134">Pour créer une instance de l'adaptateur PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="845ba-134">Create a new instance of the PeopleSoft Enterprise adapter</span></span>  
  
1.  <span data-ttu-id="845ba-135">Lancer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="845ba-135">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="845ba-136">Cliquez sur **Démarrer**, **programmes**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="845ba-136">Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="845ba-137">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="845ba-137">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="845ba-138">Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte** pour afficher les **propriétés de l’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-138">Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="845ba-139">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoft**.</span><span class="sxs-lookup"><span data-stu-id="845ba-139">Enter a value for the **Name** field, for example **PeopleSoft**.</span></span>  
  
5.  <span data-ttu-id="845ba-140">Sélectionnez **PeopleSoft Enterprise (r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-140">Select **PeopleSoft Enterprise(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-solicit-response-biztalk-send-port"></a><span data-ttu-id="845ba-141">Pour créer un port d'envoi BizTalk de type sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="845ba-141">Create a Solicit-Response BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="845ba-142">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="845ba-142">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="845ba-143">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi statique avec sollicitation-réponse** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-143">Right-click **Send Ports** and point to **New**, **Static Solicit-Response Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="845ba-144">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftTwoWaySP**.</span><span class="sxs-lookup"><span data-stu-id="845ba-144">Enter a value for the **Name** field, for example **PeopleSoftTwoWaySP**.</span></span>  
  
4.  <span data-ttu-id="845ba-145">Sélectionnez l’adaptateur PeopleSoft dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport**boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-145">Select the PeopleSoft adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="845ba-146">Cette valeur correspond au nom spécifié lors de la création de l'adaptateur PeopleSoft Enterprise dans la console Administration.</span><span class="sxs-lookup"><span data-stu-id="845ba-146">This value is the name that was specified when the PeopleSoft Enterprise adapter was created in the Administration Console.</span></span>  
  
5.  <span data-ttu-id="845ba-147">Entrez les valeurs suivantes pour le **propriétés obligatoires de l’adaptateur**:</span><span class="sxs-lookup"><span data-stu-id="845ba-147">Enter the following values for the **Adapter Required Properties**:</span></span>  
  
    |<span data-ttu-id="845ba-148">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="845ba-148">**Property**</span></span>|<span data-ttu-id="845ba-149">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="845ba-149">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="845ba-150">Chemin d'accès au serveur de l'application</span><span class="sxs-lookup"><span data-stu-id="845ba-150">Application server path</span></span>|<span data-ttu-id="845ba-151">Emplacement de l'ordinateur et du port du serveur de PeopleSoft, par exemple //PSServer:8888</span><span class="sxs-lookup"><span data-stu-id="845ba-151">PeopleSoft Server's machine and port location, for example //PSServer:8888.</span></span> <span data-ttu-id="845ba-152">**Remarque :** si vous ne spécifiez pas un numéro de port, le port par défaut (9000) est utilisé pour l’exemple ci-dessus, vous pouvez entrer la valeur //psserver si le serveur de PeopleSoft utilise la valeur de port par défaut (9000).</span><span class="sxs-lookup"><span data-stu-id="845ba-152">**Note:**  If you do not specify a port number, the default port of 9000 is used so in the example above you could enter a value of //PSServer if the PeopleSoft Server uses the default port value of 9000.</span></span>|  
    |<span data-ttu-id="845ba-153">JAVA_HOME</span><span class="sxs-lookup"><span data-stu-id="845ba-153">JAVA_HOME</span></span>|<span data-ttu-id="845ba-154">Chemin d'accès au répertoire de base associé aux fichiers du Kit de développement logiciel de la plateforme Java 2, par exemple C:\j2sdk1.4.2_08</span><span class="sxs-lookup"><span data-stu-id="845ba-154">Path to the home directory associated with the Java 2 Platform SDK files, for example C:\j2sdk1.4.2_08</span></span>|  
    |<span data-ttu-id="845ba-155">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="845ba-155">Password</span></span>|<span data-ttu-id="845ba-156">Mot de passe de connexion au système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="845ba-156">Password used when connecting to the PeopleSoft system.</span></span>|  
    |<span data-ttu-id="845ba-157">Fichiers JAR PeopleSoft 8.x</span><span class="sxs-lookup"><span data-stu-id="845ba-157">PeopleSoft 8.x JAR files</span></span>|<span data-ttu-id="845ba-158">Emplacement du fichier JAR de l’adaptateur d’objet Java PeopleSoft, **psjoa.jar**, par exemple C:\JARS\psjoa.jar.</span><span class="sxs-lookup"><span data-stu-id="845ba-158">Location of the PeopleSoft Java Object Adapter JAR file, **psjoa.jar**, for example C:\JARS\psjoa.jar.</span></span>|  
    |<span data-ttu-id="845ba-159">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="845ba-159">User name</span></span>|<span data-ttu-id="845ba-160">Nom d'utilisateur pour la connexion au système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="845ba-160">Username for connecting to the PeopleSoft system.</span></span>|  
  
6.  <span data-ttu-id="845ba-161">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-161">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="845ba-162">Sélectionnez le **XMLTransmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="845ba-162">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown.</span></span>  
  
8.  <span data-ttu-id="845ba-163">Sélectionnez le **XMLReceive** pipeline à partir de la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-163">Select the **XMLReceive** pipeline from the list of pipelines available in the **Receive pipeline** dropdown and click **OK**.</span></span>  
  
9. <span data-ttu-id="845ba-164">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="845ba-164">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-one-way-biztalk-send-port"></a><span data-ttu-id="845ba-165">Pour créer un port d'envoi BizTalk unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="845ba-165">Create a One-Way BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="845ba-166">Créez un dossier cible destiné à l'usage du port d'envoi (par exemple, C:\Files\Out).</span><span class="sxs-lookup"><span data-stu-id="845ba-166">Create a target folder to be used by the send port, for example C:\Files\Out.</span></span>  
  
2.  <span data-ttu-id="845ba-167">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="845ba-167">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="845ba-168">Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-168">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="845ba-169">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftTwoWayFileSP**.</span><span class="sxs-lookup"><span data-stu-id="845ba-169">Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileSP**.</span></span>  
  
5.  <span data-ttu-id="845ba-170">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-170">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="845ba-171">Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de Destination** propriété et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-171">Enter the location of the folder that you created earlier for the **Destination Folder** property and click **OK**.</span></span>  
  
7.  <span data-ttu-id="845ba-172">Sélectionnez le **XMLTransmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-172">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="845ba-173">Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="845ba-173">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="845ba-174">Pour créer un port de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="845ba-174">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="845ba-175">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="845ba-175">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="845ba-176">Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel** pour afficher la boîte de dialogue Propriétés du Port de réception.</span><span class="sxs-lookup"><span data-stu-id="845ba-176">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="845ba-177">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftTwoWayFileRP**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-177">Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="845ba-178">Pour créer un emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="845ba-178">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="845ba-179">Créez un dossier à surveiller par l'emplacement de réception du fichier (par exemple, C:\Files\In).</span><span class="sxs-lookup"><span data-stu-id="845ba-179">Create a folder to be monitored by the file receive location, for example C:\Files\In.</span></span>  
  
2.  <span data-ttu-id="845ba-180">Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception** pour afficher les **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-180">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="845ba-181">Entrez une valeur pour le **nom** champ, par exemple **PeopleSoftTwoWayFileRL**.</span><span class="sxs-lookup"><span data-stu-id="845ba-181">Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="845ba-182">Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-182">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="845ba-183">Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-183">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="845ba-184">Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="845ba-184">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="845ba-185">Cliquez sur l’emplacement de réception, sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="845ba-185">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="modify-the-adapter-schema-target-namespace-property"></a><span data-ttu-id="845ba-186">Pour modifier la propriété d'espace de noms cible du schéma de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="845ba-186">Modify the Adapter schema target namespace property</span></span>  
  
1.  <span data-ttu-id="845ba-187">Lancez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et ouvrez le fichier TwoWaySend.sln.</span><span class="sxs-lookup"><span data-stu-id="845ba-187">Launch [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and open TwoWaySend.sln.</span></span> <span data-ttu-id="845ba-188">Cliquez sur **fichier**, **ouvrir**, **projet/Solution** pour afficher les **ouvrir le projet** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-188">Click **File**, **Open**, **Project/Solution** to display the **Open Project** dialog.</span></span>  
  
2.  <span data-ttu-id="845ba-189">Accédez au fichier TwoWaySend.sln, sélectionnez-le et cliquez sur **ouvrir** pour ouvrir la solution qui contient l’exemple de projet.</span><span class="sxs-lookup"><span data-stu-id="845ba-189">Browse to the TwoWaySend.sln file, click to select this file and click **Open** to open the solution that contains the sample project.</span></span>  
  
3.  <span data-ttu-id="845ba-190">Cliquez sur le **vue** menu et sélectionnez **l’Explorateur de solutions** pour afficher l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="845ba-190">Click the **View** menu and select **Solution Explorer** to display the Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="845ba-191">Double-cliquez sur le fichier LOCATIONService_1.xsd dans l'Explorateur de solutions pour l'ouvrir.</span><span class="sxs-lookup"><span data-stu-id="845ba-191">Double-click the LOCATIONService_1.xsd file in the Solution Explorer to open it.</span></span>  
  
5.  <span data-ttu-id="845ba-192">Avec le bouton droit le **schéma** nœud de locationservice_1.xsd, puis sélectionnez le **propriétés** option de menu pour afficher les propriétés pour le schéma.</span><span class="sxs-lookup"><span data-stu-id="845ba-192">Right-click the **Schema** node of LOCATIONService_1.xsd and select the **Properties** menu option to display the properties for the schema.</span></span>  
  
6.  <span data-ttu-id="845ba-193">Modifier la **cible Namespace** propriété à utiliser les valeurs appropriées pour le nom de l’adaptateur, par exemple le **cible Namespace** propriété doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="845ba-193">Edit the **Target Namespace** property to use the appropriate values for the adapter name, for example the **Target Namespace** property should read as follows:</span></span>  
  
    ```  
    http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
    ```  
  
     <span data-ttu-id="845ba-194">Où *PeopleSoft* est le nom de l’adaptateur PeopleSoft, tel qu’affiché dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="845ba-194">Where *PeopleSoft* is the name of the PeopleSoft adapter as viewed in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="845ba-195">Si la valeur configurée pour **cible Namespace** ne correspond pas à l’espace de noms spécifié dans l’instance de document d’entrée, un échec de routage se produit lorsque l’instance de document d’entrée est traitée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="845ba-195">If the configured value for **Target Namespace** does not match the namespace specified in the input document instance then a routing failure will occur when the input document instance is processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a><span data-ttu-id="845ba-196">Pour générer une instance de document à partir du schéma de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="845ba-196">Generate a document instance from the Adapter schema</span></span>  
  
1.  <span data-ttu-id="845ba-197">Double-cliquez sur **LOCATIONService_1.xsd** dans l’Explorateur de solutions pour ouvrir le fichier dans l’éditeur de schéma.</span><span class="sxs-lookup"><span data-stu-id="845ba-197">Double-click **LOCATIONService_1.xsd** in Solution Explorer to open the file in Schema Editor.</span></span>  
  
2.  <span data-ttu-id="845ba-198">Avec le bouton droit le  **\<schéma >** nœud dans l’éditeur de schéma et cliquez sur **propriétés** pour afficher les propriétés du nœud.</span><span class="sxs-lookup"><span data-stu-id="845ba-198">Right-click the **\<Schema>** node in Schema Editor and click **Properties** to display properties for the node.</span></span>  
  
3.  <span data-ttu-id="845ba-199">Sélectionnez **obtenir** dans la liste des nœuds disponibles dans le **référence de racine** zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="845ba-199">Select **Get** from the list of available nodes in the **Root Reference** dropdown box.</span></span> <span data-ttu-id="845ba-200">Cela doit être fait afin que lorsque vous générez un exemple d’instance de document, il sera générée depuis le **obtenir** nœud du schéma.</span><span class="sxs-lookup"><span data-stu-id="845ba-200">This should be done so that when you generate a sample document instance it will be generated from the **Get** node of the schema.</span></span>  
  
4.  <span data-ttu-id="845ba-201">Avec le bouton droit **LOCATIONService_1.xsd** dans l’Explorateur de solutions et cliquez sur **propriétés** pour afficher les propriétés dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="845ba-201">Right-click **LOCATIONService_1.xsd** in Solution Explorer and click **Properties** to display properties in the Properties window.</span></span>  
  
5.  <span data-ttu-id="845ba-202">Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** option.</span><span class="sxs-lookup"><span data-stu-id="845ba-202">In the Properties window, click to select the **Output Instance Filename** option.</span></span>  
  
6.  <span data-ttu-id="845ba-203">Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-203">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
7.  <span data-ttu-id="845ba-204">Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="845ba-204">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="845ba-205">Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="845ba-205">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
8.  <span data-ttu-id="845ba-206">Cliquez sur LOCATIONService_1.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="845ba-206">Right-click LOCATIONService_1.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
9. <span data-ttu-id="845ba-207">Avec le bouton droit le  **\<schéma >** nœud dans l’éditeur de schéma et cliquez sur **propriétés** pour afficher les propriétés du nœud.</span><span class="sxs-lookup"><span data-stu-id="845ba-207">Right-click the **\<Schema>** node in Schema Editor and click **Properties** to display the properties for the node.</span></span>  
  
10. <span data-ttu-id="845ba-208">Sélectionnez (**par défaut)** dans la liste des nœuds disponibles dans le **référence de racine** zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="845ba-208">Select (**Default)** from the list of available nodes in the **Root Reference** dropdown box.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="845ba-209">Pour modifier l'instance de document générée</span><span class="sxs-lookup"><span data-stu-id="845ba-209">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="845ba-210">Ouvrez l'instance de document générée dans un éditeur de texte tel que le Bloc-notes et modifiez-en le contenu de telle sorte que les données de ces champs génèrent un enregistrement existant :</span><span class="sxs-lookup"><span data-stu-id="845ba-210">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data in these fields will return an existing record:</span></span>  
  
    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
    <ns0:SETID>SHARE</ns0:SETID>  
    <ns0:LOCATION>WFKLOC</ns0:LOCATION>  
    <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="845ba-211">Dans l’exemple ci-dessus, *PeopleSoft* est un espace réservé pour le nom réel de la carte tel qu’affiché dans la Console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="845ba-211">In the example above, *PeopleSoft* is a placeholder for the actual name of the adapter as viewed in the BizTalk Administration Console.</span></span> <span data-ttu-id="845ba-212">*PARTAGE* et *WFKLOC* sont des espaces réservés pour les valeurs utilisées pour identifier un enregistrement particulier dans le système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="845ba-212">*SHARE* and *WFKLOC* are placeholders for values used to identify a particular record in the PeopleSoft system.</span></span>  
  
2.  <span data-ttu-id="845ba-213">Enregistrez l'instance de document modifiée.</span><span class="sxs-lookup"><span data-stu-id="845ba-213">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="845ba-214">création et déploiement du projet ;</span><span class="sxs-lookup"><span data-stu-id="845ba-214">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="845ba-215">Cliquez sur le projet TwoWaySend dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour afficher le Concepteur de projet pour le projet.</span><span class="sxs-lookup"><span data-stu-id="845ba-215">Right-click the TwoWaySend project in Solution Explorer and click **Properties** to display the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="845ba-216">Cliquez sur le **déploiement** onglet dans le Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="845ba-216">Click the **Deployment** tab in the Project Designer.</span></span>  
  
3.  <span data-ttu-id="845ba-217">Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="845ba-217">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="845ba-218">Cliquez sur le projet TwoWaySend dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="845ba-218">Right-click the TwoWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="845ba-219">Pour lier et inscrire l'orchestration</span><span class="sxs-lookup"><span data-stu-id="845ba-219">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="845ba-220">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="845ba-220">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="845ba-221">Cliquez sur le **Actualiser** situé dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] barre d’outils de la Console d’Administration ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="845ba-221">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console view.</span></span>  
  
3.  <span data-ttu-id="845ba-222">Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="845ba-222">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="845ba-223">Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="845ba-223">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="845ba-224">Spécifiez les valeurs appropriées pour les options de liaison, par exemple :</span><span class="sxs-lookup"><span data-stu-id="845ba-224">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="845ba-225">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="845ba-225">**Parameter**</span></span>|<span data-ttu-id="845ba-226">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="845ba-226">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="845ba-227">Hôte</span><span class="sxs-lookup"><span data-stu-id="845ba-227">Host</span></span>|<span data-ttu-id="845ba-228">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="845ba-228">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="845ba-229">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="845ba-229">FileReceivePort</span></span>|<span data-ttu-id="845ba-230">PeopleSoftTwoWayFileRP</span><span class="sxs-lookup"><span data-stu-id="845ba-230">PeopleSoftTwoWayFileRP</span></span>|  
    |<span data-ttu-id="845ba-231">PeopleSoftTwoWaySend678</span><span class="sxs-lookup"><span data-stu-id="845ba-231">PeopleSoftTwoWaySend678</span></span>|<span data-ttu-id="845ba-232">PeopleSoftTwoWaySP</span><span class="sxs-lookup"><span data-stu-id="845ba-232">PeopleSoftTwoWaySP</span></span>|  
    |<span data-ttu-id="845ba-233">ResponsePort</span><span class="sxs-lookup"><span data-stu-id="845ba-233">ResponsePort</span></span>|<span data-ttu-id="845ba-234">PeopleSoftTwoWayFileSP</span><span class="sxs-lookup"><span data-stu-id="845ba-234">PeopleSoftTwoWayFileSP</span></span>|  
  
6.  <span data-ttu-id="845ba-235">Cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="845ba-235">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="845ba-236">Démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="845ba-236">Start the orchestration</span></span>  
  
-   <span data-ttu-id="845ba-237">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="845ba-237">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="845ba-238">Pour placer une instance de document dans le dossier surveillé par l'emplacement de réception du fichier</span><span class="sxs-lookup"><span data-stu-id="845ba-238">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="845ba-239">Copiez l'instance de document créée précédemment dans le dossier surveillé par l'emplacement de réception du fichier.</span><span class="sxs-lookup"><span data-stu-id="845ba-239">Copy the document instance that was created earlier to the folder that the file receive location is configured to monitor.</span></span>  
  
#### <a name="verify-that-the-document-instance-was-processed-by-the-biztalk-adapter-for-peoplesoft-enterprise"></a><span data-ttu-id="845ba-240">Vérifiez que l'instance de document a été traitée par l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="845ba-240">Verify that the document instance was processed by the BizTalk Adapter for PeopleSoft Enterprise</span></span>  
  
-   <span data-ttu-id="845ba-241">Ouvrez le dossier utilisé par le port d'envoi du fichier et vérifiez qu'un document de sortie a été généré.</span><span class="sxs-lookup"><span data-stu-id="845ba-241">Open the folder that the file send port is configured to send to and verify that an output document was generated.</span></span> <span data-ttu-id="845ba-242">Ce fichier doit contenir les résultats de la requête traitée par l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="845ba-242">This file should contain the results of the query that was processed by the BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
 <span data-ttu-id="845ba-243">La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :</span><span class="sxs-lookup"><span data-stu-id="845ba-243">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="845ba-244">L'adaptateur FILE récupère le fichier dans le dossier et le publie dans la base de données MessageBox comme message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="845ba-244">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="845ba-245">L’orchestration s’abonne à ce message publié afin que le moteur de messagerie BizTalk Active une instance de l’orchestration et envoie le message à l’instance d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="845ba-245">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="845ba-246">L'instance d'orchestration republie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="845ba-246">The orchestration instance publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="845ba-247">Le port d'envoi de type sollicitation-réponse s'abonne à ce message publié et le moteur de messagerie BizTalk envoie le message au port d'envoi PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="845ba-247">The solicit-response send port subscribes to this published message so the BizTalk Messaging Engine sends the message to the PeopleSoft send port.</span></span>  
  
5.  <span data-ttu-id="845ba-248">Le port d'envoi remet le message à l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="845ba-248">The send port hands the message to the BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
6.  <span data-ttu-id="845ba-249">L'adaptateur BizTalk pour PeopleSoft Enterprise exécute une instruction Get sur le système PeopleSoft à l'aide des paramètres définis dans le fichier d'entrée.</span><span class="sxs-lookup"><span data-stu-id="845ba-249">The BizTalk Adapter for PeopleSoft Enterprise executes a Get statement against the PeopleSoft system using the parameters defined in the input file.</span></span>  
  
7.  <span data-ttu-id="845ba-250">L'adaptateur BizTalk pour PeopleSoft Enterprise renvoie les résultats de l'instruction Get comme message de réponse pour le port de sollicitation-réponse dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="845ba-250">The BizTalk Adapter for PeopleSoft Enterprise returns the results of the Get statement as the response message for the solicit-response port in the orchestration.</span></span>  
  
8.  <span data-ttu-id="845ba-251">L'orchestration publie l'ensemble des résultats dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="845ba-251">The orchestration publishes the result set to the MessageBox.</span></span>  
  
9. <span data-ttu-id="845ba-252">Le port d'envoi du fichier s'abonne à ce message et BizTalk envoie le message à l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="845ba-252">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  
  
10. <span data-ttu-id="845ba-253">L'adaptateur FILE écrit le message contenant l'ensemble des résultats dans le dossier de sortie désigné.</span><span class="sxs-lookup"><span data-stu-id="845ba-253">The File adapter writes the message containing the result set to the designated output folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845ba-254">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="845ba-254">See Also</span></span>  
 [<span data-ttu-id="845ba-255">Didacticiels : À l’aide de l’adaptateur BizTalk pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="845ba-255">Tutorials: Using BizTalk Adapter for PeopleSoft Enterprise</span></span>](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)