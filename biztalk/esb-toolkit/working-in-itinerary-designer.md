---
title: "Travaillez dans le Concepteur d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06742cb8-f6d6-46e2-adc0-6be9a3d6a447
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf474c68d91b7648f7f0efcfe4e85e7531e4aa1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="working-in-itinerary-designer"></a><span data-ttu-id="5e079-102">Vous travaillez dans le Concepteur d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="5e079-102">Working in Itinerary Designer</span></span>
<span data-ttu-id="5e079-103">Après avoir créé un projet Microsoft Visual c#, vous pouvez créer de nouveaux modèles d’itinéraire et ajouter des itinéraires existants au projet.</span><span class="sxs-lookup"><span data-stu-id="5e079-103">After you create a Microsoft Visual C# project, you can create new itinerary models and add existing itineraries to the project.</span></span> <span data-ttu-id="5e079-104">Les étapes suivantes décrivent comment créer une nouvelle feuille de route, ajouter un modèle d’itinéraire existant ou modifier le nom d’un itinéraire.</span><span class="sxs-lookup"><span data-stu-id="5e079-104">The following steps describe how to create a new itinerary, add an existing itinerary model, or change the name of an itinerary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e079-105">Avant d’utiliser le Concepteur d’itinéraire, vous devez installer le programme d’installation de Windows Microsoft.Practices.ESB.CORE (fichier .msi) à partir de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] le dossier d’installation.</span><span class="sxs-lookup"><span data-stu-id="5e079-105">Before working with the Itinerary Designer, you must install the Microsoft.Practices.ESB.CORE Windows Installer (.msi file) from the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] install folder.</span></span> <span data-ttu-id="5e079-106">Cette étape installe les assemblys d’exécution requis dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="5e079-106">This step installs the required run-time assemblies to the global assembly cache.</span></span>  
  
## <a name="basic-operations"></a><span data-ttu-id="5e079-107">Opérations de base</span><span class="sxs-lookup"><span data-stu-id="5e079-107">Basic Operations</span></span>  

#### <a name="create-an-itinerary"></a><span data-ttu-id="5e079-108">Créer un itinéraire</span><span class="sxs-lookup"><span data-stu-id="5e079-108">Create an itinerary</span></span>  
  
1.  <span data-ttu-id="5e079-109">Dans l’Explorateur de solutions, cliquez sur le nom du projet c#, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="5e079-109">In Solution Explorer, right-click the C# project name, point to **Add**, and then click **New Itinerary**.</span></span>  
  
2.  <span data-ttu-id="5e079-110">Dans le **nom** zone située au bas de la boîte de dialogue, tapez le nom de l’itinéraire, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5e079-110">In the **Name** box at the bottom of the dialog box, type the name for the itinerary, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e079-111">La nouvelle feuille de route est créé et affiché dans le Concepteur d’itinéraire et un fichier .itinerary correspondant est créé et affiché dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="5e079-111">The new itinerary is created and displayed in Itinerary Designer, and a corresponding .itinerary file is created and displayed in Solution Explorer.</span></span>  
  
#### <a name="add-an-existing-itinerary-to-the-project"></a><span data-ttu-id="5e079-112">Ajoutez un itinéraire existant au projet</span><span class="sxs-lookup"><span data-stu-id="5e079-112">Add an existing itinerary to the project</span></span>
  
1.  <span data-ttu-id="5e079-113">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet c#, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="5e079-113">In Solution explorer, right click the C# project name, point to **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="5e079-114">Dans le **ajouter un élément existant** boîte de dialogue, accédez au répertoire qui contient la feuille de route, cliquez sur l’itinéraire, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5e079-114">In the **Add Existing Item** dialog box, navigate to the directory that contains the itinerary, click the itinerary, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e079-115">L’itinéraire est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="5e079-115">The itinerary is added to the project.</span></span>  
  
#### <a name="change-the-name-of-an-itinerary"></a><span data-ttu-id="5e079-116">Modifier le nom d’un itinéraire</span><span class="sxs-lookup"><span data-stu-id="5e079-116">Change the name of an itinerary</span></span>  
  
1.  <span data-ttu-id="5e079-117">Dans l’Explorateur de solutions, cliquez sur le fichier .itinerary que vous souhaitez renommer, puis cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="5e079-117">In Solution Explorer, right-click the .itinerary file you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="5e079-118">Tapez le nouveau nom de fichier, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="5e079-118">Type the new file name, and then press ENTER.</span></span>  
  
#### <a name="save-an-itinerary"></a><span data-ttu-id="5e079-119">Enregistrer un itinéraire</span><span class="sxs-lookup"><span data-stu-id="5e079-119">Save an itinerary</span></span>  
  
<span data-ttu-id="5e079-120">Sur le **fichier** menu, cliquez sur **enregistrer \<nom d’itinéraire\>**.</span><span class="sxs-lookup"><span data-stu-id="5e079-120">On the **File** menu, click **Save \<itinerary name\>**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e079-121">Fichiers d’itinéraire sont enregistrés en tant que modèles DSL format XML correspondant.</span><span class="sxs-lookup"><span data-stu-id="5e079-121">Itinerary files are saved as DSL models in corresponding XML format.</span></span>  
  
#### <a name="set-itinerary-export-properties"></a><span data-ttu-id="5e079-122">Définir les propriétés de l’exportation d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="5e079-122">Set itinerary export properties</span></span>  
  
1.  <span data-ttu-id="5e079-123">Dans la fenêtre Propriétés, tapez un **nom** propriété.</span><span class="sxs-lookup"><span data-stu-id="5e079-123">In the Properties window, type a **Name** property.</span></span>  
  
2.  <span data-ttu-id="5e079-124">Dans la fenêtre Propriétés, tapez un **Version** propriété.</span><span class="sxs-lookup"><span data-stu-id="5e079-124">In the Properties window, type a **Version** property.</span></span>  
  
3.  <span data-ttu-id="5e079-125">Dans la fenêtre Propriétés, définissez la **réponse à la demande est** propriété à l’aide de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5e079-125">In the Properties window, specify the **Is Request Response** property using the drop-down list.</span></span> <span data-ttu-id="5e079-126">Définissez cette propriété sur **true** si le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] application cliente communique avec une rampe d’entrée à l’aide du modèle d’échange de messages de demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="5e079-126">Set this property to **true** if the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] client application communicates with an on-ramp using request-response message exchange pattern.</span></span>  
  
4.  <span data-ttu-id="5e079-127">Dans la fenêtre Propriétés, définissez la **exporter un Mode** propriété **par défaut** ou **Strict**.</span><span class="sxs-lookup"><span data-stu-id="5e079-127">In the Properties window, set the **Export Mode** property to **Default** or **Strict**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e079-128">Lors de la création [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinéraires à l’aide du Concepteur d’itinéraire, le **exporter un Mode** propriété peut être utilisée pour définir où le service s’exécute.</span><span class="sxs-lookup"><span data-stu-id="5e079-128">When creating [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itineraries using the Itinerary Designer, the **Export Mode** property can be used to define where the service will execute.</span></span> <span data-ttu-id="5e079-129">Définition de la **exporter un Mode** propriété **Strict** garantit que l’itinéraire service s’exécute dans son conteneur prescrite ; dans ce cas, chaque service d’itinéraire dans l’itinéraire XML a une propriété de l’étape qui Spécifie le pipeline dans laquelle le service s’exécute.</span><span class="sxs-lookup"><span data-stu-id="5e079-129">Setting the **Export Mode** property to **Strict** ensures that the itinerary service executes in its prescribed container; in this case, each itinerary service in the XML itinerary has a stage property that specifies the pipeline in which the service executes.</span></span> <span data-ttu-id="5e079-130">Si cette propriété est définie sur **par défaut**, un itinéraire compatible avec Microsoft ESB est créé, avec aucune phase spécifié, et le service d’itinéraire s’exécute dans l’ordre indiqué, mais pas nécessairement dans l’étape de pipeline que vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="5e079-130">If this property is set to **Default**, an itinerary compatible with Microsoft ESB is created, with no stage specified, and the itinerary service executes in the order prescribed, but not necessarily in the pipeline stage desired.</span></span>  
  
#### <a name="export-an-itinerary-to-a-file"></a><span data-ttu-id="5e079-131">Exporter un itinéraire vers un fichier</span><span class="sxs-lookup"><span data-stu-id="5e079-131">Export an itinerary to a file</span></span>  
  
1.  <span data-ttu-id="5e079-132">Dans la fenêtre Propriétés, cliquez sur **XML itinéraire exportateur** dans les **modèle exportateur** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5e079-132">In the Properties window, click **XML Itinerary Exporter** in the **Model Exporter** drop-down list.</span></span>  
  
2.  <span data-ttu-id="5e079-133">Dans la fenêtre Propriétés, définissez la **fichier XML de la feuille de route** à une nouvelle valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="5e079-133">In the Properties window, set the **Itinerary XML file** property to a new value.</span></span>  
  
#### <a name="export-an-itinerary-to-a-database"></a><span data-ttu-id="5e079-134">Exporter un itinéraire pour une base de données</span><span class="sxs-lookup"><span data-stu-id="5e079-134">Export an itinerary to a database</span></span>  
  
1.  <span data-ttu-id="5e079-135">Dans la fenêtre Propriétés, cliquez sur **exportateur de feuille de route de base de données** dans les **modèle exportateur** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5e079-135">In the Properties window, click **Database Itinerary Exporter** in the **Model Exporter** drop-down list.</span></span>  
  
2.  <span data-ttu-id="5e079-136">Dans la fenêtre Propriétés, définissez la **base de données de la feuille de route** chaîne de connexion de propriété pour pointer vers la base de données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="5e079-136">In the Properties window, set the **Itinerary Database** property connection string to point to the itinerary database.</span></span>  
  
3.  <span data-ttu-id="5e079-137">Dans la fenêtre Propriétés, définissez la **état de la feuille de route** propriété **publié** ou **déployées**.</span><span class="sxs-lookup"><span data-stu-id="5e079-137">In the Properties window, set the **Itinerary Status** property to **Published** or **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e079-138">Lorsqu’un itinéraire est exporté vers une base de données avec **état de la feuille de route** la valeur **publié**, l’itinéraire se ne pas effet pour la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exécution jusqu'à ce que lorsque la propriété est définie à  **Déployé**.</span><span class="sxs-lookup"><span data-stu-id="5e079-138">When an itinerary is exported to a database with **Itinerary Status** set to **Published**, the itinerary will not become effective for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] run time until after the property is set to **Deployed**.</span></span>  
  
## <a name="security-operations"></a><span data-ttu-id="5e079-139">Opérations de sécurité</span><span class="sxs-lookup"><span data-stu-id="5e079-139">Security Operations</span></span>  
 <span data-ttu-id="5e079-140">À l’aide du Concepteur d’itinéraire, vous pouvez protéger des informations sensibles, telles que les mots de passe et autres informations d’identification stockées dans un [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] d’itinéraire, en chiffrant ces informations à l’aide de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="5e079-140">By using the Itinerary Designer, you can protect sensitive information, such as passwords and other credentials stored in a [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary, by encrypting this information using X.509 certificates.</span></span>  
  
#### <a name="select-the-x509-certificate-for-an-itinerary"></a><span data-ttu-id="5e079-141">Sélectionnez le certificat X.509 pour un itinéraire</span><span class="sxs-lookup"><span data-stu-id="5e079-141">Select the X.509 certificate for an itinerary</span></span>  
  
1.  <span data-ttu-id="5e079-142">Dans la fenêtre Propriétés de concepteur d’itinéraire, développez le **le certificat de chiffrement** propriété, puis cliquez sur le **magasin** liste déroulante, puis sélectionnez le **CurrentUser**ou **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="5e079-142">In the Itinerary Designer Properties window, expand the **Encryption Certificate** property, and then click the **Store Location** drop-down list, and select the **CurrentUser** or **LocalMachine**.</span></span> <span data-ttu-id="5e079-143">Cela associe le magasin de certificats X.509 à l’utilisateur actuel ou l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5e079-143">This associates the X.509 certificate store with the current user or the local computer.</span></span>  
  
2.  <span data-ttu-id="5e079-144">Dans la fenêtre Propriétés, cliquez sur le **nom du magasin** liste déroulante et sélectionnez la valeur qui correspond à votre magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="5e079-144">In the Properties window, click the **Store Name** drop-down list and select the value which corresponds to your certificate store.</span></span>  
  
3.  <span data-ttu-id="5e079-145">Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (...) en regard de la propriété du certificat de chiffrement, puis sélectionnez le **certificat X.509** dans les **sélectionner un certificat** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5e079-145">In the Properties window, click the ellipsis button (...) next to the Encryption Certificate property, and then select the **X.509 certificate** in the **Select Certificate** dialog box.</span></span>  
  
#### <a name="remove-the-x509-certificate-from-an-itinerary"></a><span data-ttu-id="5e079-146">Supprimer le certificat X.509 à partir d’un itinéraire</span><span class="sxs-lookup"><span data-stu-id="5e079-146">Remove the X.509 certificate from an itinerary</span></span>  
  
-   <span data-ttu-id="5e079-147">Dans la fenêtre Propriétés de concepteur d’itinéraire, développez le **le certificat de chiffrement** propriété et définissez la **magasin** propriété sur une autre valeur.</span><span class="sxs-lookup"><span data-stu-id="5e079-147">In the Itinerary Designer Properties window, expand the **Encryption Certificate** property, and then set the **Store Location** property to a different value.</span></span> <span data-ttu-id="5e079-148">Il dissocie l’ancien certificat avec la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] modèle d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="5e079-148">This disassociates the old certificate with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary model.</span></span>  
  
#### <a name="disable-the-x509-certificate-validation"></a><span data-ttu-id="5e079-149">Désactiver la validation du certificat X.509</span><span class="sxs-lookup"><span data-stu-id="5e079-149">Disable the X.509 certificate validation</span></span>  
  
<span data-ttu-id="5e079-150">Dans l’Éditeur du Registre, accédez à la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**, puis définissez le **RequireX509Certificate** valeur de propriété  **false**.</span><span class="sxs-lookup"><span data-stu-id="5e079-150">In the Registry Editor, go to the subkey **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**, and then set the **RequireX509Certificate** property value to **false**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e079-151">Si vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] sur un système d’exploitation qui prend en charge 64 bits, la sous-clé est **HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**.</span><span class="sxs-lookup"><span data-stu-id="5e079-151">If you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] on an operating system that has 64-bit support, the subkey is **HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**.</span></span>