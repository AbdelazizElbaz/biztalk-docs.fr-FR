---
title: "Exemple Hello World2 de règles d’entreprise (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: 2a88a2a0-8cb6-4373-8441-0ab04345a477
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48d92d3de6b4ef6b4d541d7f64e0d483feb9c30f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-hello-world2-biztalk-server-sample"></a><span data-ttu-id="951f6-102">Exemple Hello World2 de règles d’entreprise (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="951f6-102">Business Rules Hello World2 (BizTalk Server Sample)</span></span>
<span data-ttu-id="951f6-103">L’exemple d’entreprise règles « Hello World2 » étend l’exemple de Business règles « Hello world1 » en montrant comment vers la version, publier et déployer l’ensemble pour le magasin de règles SQL partagé et l’exécution de la stratégie à l’aide de règles XML le **stratégie** objet fourni par l’infrastructure des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="951f6-103">The Business Rules Hello World2 sample extends the Business Rules Hello World1 sample by demonstrating how to version, publish, and deploy the XML rule set to the shared SQL rule store, and how to run the policy using the **Policy** object provided by the Business Rules Framework.</span></span> <span data-ttu-id="951f6-104">L'exemple illustre également les stratégies de mise à jour dynamiques en action.</span><span class="sxs-lookup"><span data-stu-id="951f6-104">The sample also demonstrates dynamic policy updates in action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="951f6-105">Il est basé sur l'hypothèse que l'utilisateur a installé le service de mise à jour du moteur des règles et les composants des règles d'entreprise (situés sous le nœud « Logiciels supplémentaires ») durant l'installation du produit.</span><span class="sxs-lookup"><span data-stu-id="951f6-105">This sample assumes that the user has installed the Rule Engine Update Service and Business Rules Components (located under the "Additional Software" node) during installation of the product.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="951f6-106">Vous utilisez **stratégie** objets pour intégrer le moteur de règles dans une application autonome.</span><span class="sxs-lookup"><span data-stu-id="951f6-106">You use **Policy** objects to integrate the rule engine into any stand-alone application.</span></span> <span data-ttu-id="951f6-107">Le **stratégie** objet est l’abstraction gérés via la règle de plusieurs instances du moteur, les jeux sont extraits et instanciés à partir du magasin SQL partagé, et les stratégies mises à jour sont extraites et publiées à l’hébergement de règles application.</span><span class="sxs-lookup"><span data-stu-id="951f6-107">The **Policy** object is the abstraction through which multiple rule engine instances are managed, rule sets are retrieved and instantiated from the shared SQL store, and updates to the policies are retrieved and published to the hosting application.</span></span>  
  
 <span data-ttu-id="951f6-108">Pour plus d’informations de base sur l’ensemble défini et des exemples de règles faits créés par cet exemple, consultez [entreprise règles « Hello world1 »](../core/business-rules-hello-world1-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="951f6-108">For basic information about the rule set defined, and sample facts constructed by this sample, see [Business Rules Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="951f6-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="951f6-109">What This Sample Does</span></span>  
 <span data-ttu-id="951f6-110">Cet exemple crée un fichier exécutable qui effectue la séquence d'étapes suivante :</span><span class="sxs-lookup"><span data-stu-id="951f6-110">This sample creates an executable that performs the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="951f6-111">Appelle la méthode **CreateRuleset** pour générer l’ensemble de règles décrit dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="951f6-111">Calls the method **CreateRuleset** to build the rule set described in the Remarks section.</span></span>  
  
2.  <span data-ttu-id="951f6-112">Appelle la méthode **SaveToFile** pour montrer l’enregistrement d’un ensemble de règles dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="951f6-112">Calls the method **SaveToFile** to demonstrate saving a rule set to a file.</span></span>  
  
3.  <span data-ttu-id="951f6-113">Appelle la méthode **LoadFromFile** pour montrer le chargement à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="951f6-113">Calls the method **LoadFromFile** to demonstrate loading a rule set from a file.</span></span>  
  
4.  <span data-ttu-id="951f6-114">Déploie l'ensemble de règles dans un magasin de règles SQL partagé.</span><span class="sxs-lookup"><span data-stu-id="951f6-114">Deploys the rule set to a shared SQL rule store.</span></span>  
  
5.  <span data-ttu-id="951f6-115">Exécute l’ensemble à l’aide de règles une **stratégie** de l’objet et en utilisant le même ensemble d’exemples de faits utilisées dans l’entreprise règles « Hello world1 » d’exemple.</span><span class="sxs-lookup"><span data-stu-id="951f6-115">Runs the rule set by using a **Policy** object, and by using the same set of sample facts used in the Business Rules Hello World1 sample.</span></span>  
  
6.  <span data-ttu-id="951f6-116">Temps de pause, ce qui vous permet de modifier la règle de définie le fichier **SampleRuleStore.xml** d’une manière spécifique.</span><span class="sxs-lookup"><span data-stu-id="951f6-116">Pauses, enabling you to modify the rule set file **SampleRuleStore.xml** in a specific way.</span></span>  
  
7.  <span data-ttu-id="951f6-117">Exécute l’ensemble à l’aide de règles une **stratégie** de l’objet, la règle modifiée maintenant définir et à nouveau avec le même jeu d’exemples de faits utilisées dans l’entreprise règles « Hello world1 » exemple.</span><span class="sxs-lookup"><span data-stu-id="951f6-117">Runs the rule set again using a **Policy** object, the now modified rule set, and again with the same set of sample facts used in the Business Rules Hello World1 sample.</span></span>  
  
8.  <span data-ttu-id="951f6-118">Effectue un nettoyage en supprimant le fichier de l'ensemble de règles et les enregistrements de l'ensemble de règles déployé pour préparer les exécutions suivantes de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="951f6-118">Cleans up by deleting the rule set file and the deployed rule set records in preparation for subsequent running of the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="951f6-119">Pour obtenir des informations importantes sur tous les exemples dans ce SDK, consultez [exemples](../core/samples-in-the-sdk.md).</span><span class="sxs-lookup"><span data-stu-id="951f6-119">For important information about all samples in this SDK, see [Samples](../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="951f6-120">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="951f6-120">Where to Find This Sample</span></span>  
 <span data-ttu-id="951f6-121">*\<Exemples de chemin d’accès >*\Business Rules\Business règles Hello World2\\</span><span class="sxs-lookup"><span data-stu-id="951f6-121">*\<Samples Path>*\Business Rules\Business Rules Hello World2\\</span></span>  
  
 <span data-ttu-id="951f6-122">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="951f6-122">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="951f6-123">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="951f6-123">File(s)</span></span>|<span data-ttu-id="951f6-124"> Description</span><span class="sxs-lookup"><span data-stu-id="951f6-124">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="951f6-125">App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld2.csproj, BusinessRulesHelloWorld2.sln</span><span class="sxs-lookup"><span data-stu-id="951f6-125">App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld2.csproj, BusinessRulesHelloWorld2.sln</span></span>|<span data-ttu-id="951f6-126">Projet, solution et fichiers associés pour la portion de cet exemple qui crée, enregistre, charge, déploie et exécute un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="951f6-126">Project, solution, and related files for the portion of this sample that creates, saves, loads, deploys, and executes a rule set.</span></span>|  
|<span data-ttu-id="951f6-127">HelloWorld2.cs</span><span class="sxs-lookup"><span data-stu-id="951f6-127">HelloWorld2.cs</span></span>|<span data-ttu-id="951f6-128">Les fichier Visual c# qui contient des méthodes servant à montrer la création d’une règle définir, l’enregistrement d’un ensemble de règles à un fichier, son chargement à partir d’un fichier de déploiement de la règle à un magasin de règles partagé Microsoft SQL Server, et ensuite la règle en cours d’exécution définies à l’aide un **stratégie**objet.</span><span class="sxs-lookup"><span data-stu-id="951f6-128">Visual C# file that contains methods to demonstrate creating a rule set, saving a rule set to a file, loading a rule set from a file, deploying the rule set to a shared Microsoft SQL Server rule store, and then running the rule set by using a **Policy** object.</span></span>|  
|<span data-ttu-id="951f6-129">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="951f6-129">Cleanup.bat</span></span>|<span data-ttu-id="951f6-130">Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="951f6-130">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="951f6-131">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="951f6-131">Removes send and receive ports.</span></span> <span data-ttu-id="951f6-132">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="951f6-132">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="951f6-133">SampleDocumentInstance.xml</span><span class="sxs-lookup"><span data-stu-id="951f6-133">SampleDocumentInstance.xml</span></span>|<span data-ttu-id="951f6-134">Exemple de fichier d'entrée conforme au schéma défini dans le fichier SampleSchema.xsd.</span><span class="sxs-lookup"><span data-stu-id="951f6-134">Sample input file that conforms to the schema defined in the file SampleSchema.xsd.</span></span>|  
|<span data-ttu-id="951f6-135">SampleSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="951f6-135">SampleSchema.xsd</span></span>|<span data-ttu-id="951f6-136">Fichier de schéma qui définit un schéma unique avec un élément référencé par l'ensemble de règles créé dans le fichier Visual C# Class1.cs.</span><span class="sxs-lookup"><span data-stu-id="951f6-136">Schema file that defines a simple schema with an element referenced by the rule set created in the Visual C# file Class1.cs.</span></span>|  
|<span data-ttu-id="951f6-137">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="951f6-137">Setup.bat</span></span>|<span data-ttu-id="951f6-138">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="951f6-138">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="951f6-139">Dans le dossier \HelloWorld2Library :</span><span class="sxs-lookup"><span data-stu-id="951f6-139">In the \HelloWorld2Library folder:</span></span><br /><br /> <span data-ttu-id="951f6-140">AssemblyInfo.cs, HelloWorld2Library.csproj, HelloWorld2Library.sln</span><span class="sxs-lookup"><span data-stu-id="951f6-140">AssemblyInfo.cs, HelloWorld2Library.csproj, HelloWorld2Library.sln</span></span>|<span data-ttu-id="951f6-141">Projet, solution et fichiers associés pour la portion de cet exemple qui fournit la classe définissant les objets référencés par l'ensemble de règles créé.</span><span class="sxs-lookup"><span data-stu-id="951f6-141">Project, solution, and related files for the portion of this sample that provides the class that defines the objects referenced by the created rule set.</span></span>|  
|<span data-ttu-id="951f6-142">Dans le dossier \HelloWorld2Library :</span><span class="sxs-lookup"><span data-stu-id="951f6-142">In the \HelloWorld2Library folder:</span></span><br /><br /> <span data-ttu-id="951f6-143">HelloWorld2LibraryClass.cs</span><span class="sxs-lookup"><span data-stu-id="951f6-143">HelloWorld2LibraryClass.cs</span></span>|<span data-ttu-id="951f6-144">Les fichiers Visual c# qui contient la propriété référencée dans le **IF** partie de la règle créée et la méthode qui peut être appelée dans le **puis** partie de la règle créée.</span><span class="sxs-lookup"><span data-stu-id="951f6-144">Visual C# file that contains the property referenced in the **IF** portion of the created rule, and the method that may be called in the **THEN** portion of the created rule.</span></span>|  
  
### <a name="to-build-and-initialize-the-business-rules-hello-world2-sample"></a><span data-ttu-id="951f6-145">Pour créer et initialiser l'exemple de règles d'entreprise « Hello World2 »</span><span class="sxs-lookup"><span data-stu-id="951f6-145">To build and initialize the Business Rules Hello World2 sample</span></span>  
  
1.  <span data-ttu-id="951f6-146">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="951f6-146">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="951f6-147">*\<Exemples de chemin d’accès >*\Business Rules\Business règles Hello World2\\</span><span class="sxs-lookup"><span data-stu-id="951f6-147">*\<Samples Path>*\Business Rules\Business Rules Hello World2\\</span></span>  
  
2.  <span data-ttu-id="951f6-148">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="951f6-148">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="951f6-149">Compilation et déploiement des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="951f6-149">Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="951f6-150">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="951f6-150">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="951f6-151">Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="951f6-151">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="951f6-152">Celle-ci permet de signer les assemblys obtenus.</span><span class="sxs-lookup"><span data-stu-id="951f6-152">Use this key pair to sign the resulting assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="951f6-153">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="951f6-153">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="951f6-154">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="951f6-154">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
### <a name="to-run-the-business-rules-hello-world2-sample"></a><span data-ttu-id="951f6-155">Pour exécuter l'exemple de règles d'entreprise « Hello World2 »</span><span class="sxs-lookup"><span data-stu-id="951f6-155">To run the Business Rules Hello World2 sample</span></span>  
  
1.  <span data-ttu-id="951f6-156">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="951f6-156">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="951f6-157">*\<Exemples de chemin d’accès >*\Business Rules\Business règles Hello World2\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="951f6-157">*\<Samples Path>*\Business Rules\Business Rules Hello World2\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="951f6-158">Dans la fenêtre de commande, tapez le nom du fichier pour cet exemple (**BusinessRulesHelloWorld2.exe**), puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="951f6-158">In the command window, type the name of the file for this sample (**BusinessRulesHelloWorld2.exe**), and then press ENTER.</span></span>  
  
## <a name="hello-world2-output"></a><span data-ttu-id="951f6-159">Sortie de l'exemple « Hello World2 »</span><span class="sxs-lookup"><span data-stu-id="951f6-159">Hello World2 Output</span></span>  
 <span data-ttu-id="951f6-160">Selon la nature de l’ensemble de règles créé, décrit dans la section commentaires du [entreprise règles « Hello world1 »](../core/business-rules-hello-world1-biztalk-server-sample.md), si vous exécutez cet exemple avec l’exemple d’entrée de fichier fourni SampleDocumentInstance.xml, ce qui a une valeur d’un (1) définie pour son **ID** élément, vous verrez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="951f6-160">Based on the nature of the created rule set, described in the Comments section of [Business Rules Hello World1](../core/business-rules-hello-world1-biztalk-server-sample.md), if you run this sample with the provided sample input file SampleDocumentInstance.xml, which has a value of one (1) defined for its **ID** element, you will see the following output:</span></span>  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Deploying the ruleset ...  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...  
Grabbing the policy ...  
Executing the policy...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
The major version of the policy was: 1  
The minor version of the policy was: 0  
Press the ENTER to continue after updating the policy...  
```  
  
> [!NOTE]
>  <span data-ttu-id="951f6-161">La sortie en gras est la sortie produite par l’exemple d’objet métier défini par les fichiers dans le **HelloWorld2Library** que la règle de définie les références de dossier.</span><span class="sxs-lookup"><span data-stu-id="951f6-161">The output shown in bold is the output produced by the sample business object, defined by the files in the **HelloWorld2Library** folder that the rule set references.</span></span> <span data-ttu-id="951f6-162">À ce stade, l'application reste en attente dans cet état.</span><span class="sxs-lookup"><span data-stu-id="951f6-162">At this point, the application is left waiting in this state.</span></span>  
  
 <span data-ttu-id="951f6-163">La partie suivant de l'exécution de l'exemple implique l'utilisation de l'Éditeur de règles d'entreprise pour modifier ces dernières.</span><span class="sxs-lookup"><span data-stu-id="951f6-163">The next part of running the sample involves using the Business Rules Composer to change the business rules.</span></span>  
  
#### <a name="to-use-the-business-rules-composer-to-change-the-business-rules"></a><span data-ttu-id="951f6-164">Utiliser l'Éditeur de règles d'entreprise afin de modifier les règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="951f6-164">To use the Business Rules Composer to change the business rules</span></span>  
  
1.  <span data-ttu-id="951f6-165">Pour ouvrir l’éditeur des règles d’entreprise, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="951f6-165">To open the Business Rules Composer, click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Composer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="951f6-166">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="951f6-166">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="951f6-167">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="951f6-167">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="951f6-168">Si une boîte de dialogue SQL Server sur l’ordinateur exécutant SQL Server, cliquez sur **OK** pour se connecter au magasin de règles.</span><span class="sxs-lookup"><span data-stu-id="951f6-168">If a SQL Server dialog box appears on the computer running SQL Server, click **OK** to connect to the rule store.</span></span>  
  
3.  <span data-ttu-id="951f6-169">Dans **l’Explorateur de stratégies**, ci-dessous la **SampleRuleSet** nœud, cliquez sur le noeud **Version 1.0 – Deployed**, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="951f6-169">In **Policy Explorer**, below the **SampleRuleSet** node, right-click the node **Version 1.0 – Deployed**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="951f6-170">Avec le bouton droit **SampleRuleSet**, puis cliquez sur **Coller (Version de stratégie)**.</span><span class="sxs-lookup"><span data-stu-id="951f6-170">Right-click **SampleRuleSet**, and then click **Paste (Policy Version)**.</span></span>  
  
5.  <span data-ttu-id="951f6-171">Vous pouvez modifier la condition et l'action de la règle en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="951f6-171">You can change the rule condition and action to meet your needs.</span></span> <span data-ttu-id="951f6-172">Pour cette procédure, cliquez sur **rule1** dans **Version 1.1 (non enregistrée)**.</span><span class="sxs-lookup"><span data-stu-id="951f6-172">For this procedure, click **rule1** in **Version 1.1 (not saved)**.</span></span> <span data-ttu-id="951f6-173">Dans le volet droit, cliquez sur **Conditions**, puis cliquez sur **ajouter le NOT logique**.</span><span class="sxs-lookup"><span data-stu-id="951f6-173">In the right pane, right-click **Conditions**, and then click **Add Logical NOT**.</span></span> <span data-ttu-id="951f6-174">Ajout d’un **NOT logique** opération **n’est pas égal** pour le prédicat équivaut à utiliser une **égal** prédicat.</span><span class="sxs-lookup"><span data-stu-id="951f6-174">Adding a **Logical NOT** operation to **Not Equal** to predicate is equivalent to using an **Equal** predicate.</span></span>  
  
6.  <span data-ttu-id="951f6-175">Cliquez sur le noeud **Version 1.1 (non enregistrée)**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="951f6-175">Right-click the node **Version 1.1(not saved)**, and then click **Save**.</span></span> <span data-ttu-id="951f6-176">Cliquez sur Nouveau, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="951f6-176">Right-click again, and then click **Publish**.</span></span> <span data-ttu-id="951f6-177">Avec le bouton droit une troisième fois, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="951f6-177">Right-click a third time and click **Deploy**.</span></span>  
  
7.  <span data-ttu-id="951f6-178">Dans la fenêtre de commande en pause vous demandant d'appuyer sur une touche pour continuer après la mise à jour de la stratégie, appuyez sur une touche.</span><span class="sxs-lookup"><span data-stu-id="951f6-178">In the paused command window asking you to press any key to continue after updating the policy, press any key.</span></span>  
  
 <span data-ttu-id="951f6-179">La sortie (en supposant que vous ayez modifié la règle en ajoutant un Not logique) du fichier exécutable BusinessRulesHelloWorld2.exe continue comme suit :</span><span class="sxs-lookup"><span data-stu-id="951f6-179">Output (assuming you changed the rule by adding a logical Not) from the executable file BusinessRulesHelloWorld2.exe continues as follows:</span></span>  
  
```  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...         
Grabbing the policy ...         
Executing the policy...         
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5         
The major version of the policy was: 1         
The minor version of the policy was: 1         
Press ENTER to continue after updating the policy...         
```  
  
 <span data-ttu-id="951f6-180">Notez la façon dont la sortie a changé :</span><span class="sxs-lookup"><span data-stu-id="951f6-180">Notice how the output has changed:</span></span>  
  
-   <span data-ttu-id="951f6-181">La ligne de sortie dans la méthode **MySampleMethod** ne s’imprime une fois maintenant, pour l’instance de la **MySampleBusinessObject** classe pour laquelle le **MyValue** propriété est égale à 1 , au lieu de la règle précédente imprimer lorsque la **MyValue** propriété n’est pas égale à 1.</span><span class="sxs-lookup"><span data-stu-id="951f6-181">The output line in the method **MySampleMethod** only prints once now, for the instance of the **MySampleBusinessObject** class for which the **MyValue** property is equal to 1, rather than the previous rule of printing when the **MyValue** property is not equal to 1.</span></span>  
  
-   <span data-ttu-id="951f6-182">Le numéro de version mineure de la stratégie est désormais 1.</span><span class="sxs-lookup"><span data-stu-id="951f6-182">The minor version number of the policy is now 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951f6-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="951f6-183">See Also</span></span>  
 [<span data-ttu-id="951f6-184">Règles d’entreprise (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="951f6-184">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)