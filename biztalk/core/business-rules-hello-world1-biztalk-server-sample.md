---
title: "Hello World1 de règles d’entreprise (exemple BizTalk Server) | Documents Microsoft"
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
ms.assetid: 0623ad20-96cc-430e-bb36-35431a5d17ee
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7231fd0d2aba7298127534eb43f1bf3c8c453b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-hello-world1-biztalk-server-sample"></a><span data-ttu-id="49d70-102">Hello World1 de règles d’entreprise (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="49d70-102">Business Rules Hello World1 (BizTalk Server Sample)</span></span>
<span data-ttu-id="49d70-103">L'exemple de règles d'entreprise « Hello World1 » montre comment créer un ensemble de règles BizTalk, l'enregistrer dans un fichier (SampleRuleSet.xml), le charger et l'exécuter sur la base d'un exemple d'ensemble de faits.</span><span class="sxs-lookup"><span data-stu-id="49d70-103">The Business Rules Hello World1 sample demonstrates how to create a BizTalk rule set, save it to a file (SampleRuleSet.xml), load it, and run it based on a sample set of facts.</span></span> <span data-ttu-id="49d70-104">L'exemple d'ensemble de règles contient une seule règle impliquant un élément XML, ainsi que des objets .NET (propriétés et membres) en tant que termes dans la définition de règle.</span><span class="sxs-lookup"><span data-stu-id="49d70-104">The sample rule set contains a simple rule that involves an XML element, and .NET-based objects (properties and members) as terms in rule definition.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="49d70-105">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="49d70-105">What This Sample Does</span></span>  
 <span data-ttu-id="49d70-106">Cet exemple crée un fichier exécutable qui effectue la séquence d'étapes suivante :</span><span class="sxs-lookup"><span data-stu-id="49d70-106">This sample creates an executable that performs the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="49d70-107">Appelle la méthode **CreateRuleset** pour générer l’ensemble de règles décrit dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="49d70-107">Calls the method **CreateRuleset** to build the rule set described in the Remarks section.</span></span>  
  
2.  <span data-ttu-id="49d70-108">Appelle la méthode **SaveToFile** pour montrer l’enregistrement d’un ensemble de règles dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="49d70-108">Calls the method **SaveToFile** to demonstrate saving a rule set to a file.</span></span>  
  
3.  <span data-ttu-id="49d70-109">Appelle la méthode **LoadFromFile** pour montrer le chargement à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="49d70-109">Calls the method **LoadFromFile** to demonstrate loading a rule set from a file.</span></span>  
  
4.  <span data-ttu-id="49d70-110">Crée les exemples de faits sur lesquels exécuter l'ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="49d70-110">Constructs sample facts against which to run the rule set.</span></span>  
  
5.  <span data-ttu-id="49d70-111">Exécute l'ensemble de règles sur les exemples de faits et génère une sortie écran.</span><span class="sxs-lookup"><span data-stu-id="49d70-111">Runs the rule set against the sample facts, producing screen output.</span></span>  
  
6.  <span data-ttu-id="49d70-112">Marque un temps d'arrêt vous permettant d'examiner le fichier de l'ensemble de règles SampleRuleStore.xml.</span><span class="sxs-lookup"><span data-stu-id="49d70-112">Pauses, enabling you to examine the rule set file SampleRuleStore.xml.</span></span>  
  
7.  <span data-ttu-id="49d70-113">Effectue un nettoyage en supprimant le fichier de l'ensemble de règles pour préparer les exécutions suivantes de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="49d70-113">Cleans up by deleting the rule set file in preparation for subsequent runs of the sample.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="49d70-114">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="49d70-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="49d70-115">\<*Exemples de chemin d’accès*> \Business Rules\Business règles Hello World1\\</span><span class="sxs-lookup"><span data-stu-id="49d70-115">\<*Samples Path*>\Business Rules\Business Rules Hello World1\\</span></span>  
  
 <span data-ttu-id="49d70-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="49d70-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="49d70-117">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="49d70-117">File(s)</span></span>|<span data-ttu-id="49d70-118"> Description</span><span class="sxs-lookup"><span data-stu-id="49d70-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49d70-119">App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld1.csproj, BusinessRulesHelloWorld1.sln</span><span class="sxs-lookup"><span data-stu-id="49d70-119">App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld1.csproj, BusinessRulesHelloWorld1.sln</span></span>|<span data-ttu-id="49d70-120">Projet, solution et fichiers associés pour la portion de cet exemple qui crée, enregistre, charge et exécute un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="49d70-120">Project, solution, and related files for the portion of this sample that creates, saves, loads, and runs a rule set.</span></span>|  
|<span data-ttu-id="49d70-121">HelloWorld1.cs</span><span class="sxs-lookup"><span data-stu-id="49d70-121">HelloWorld1.cs</span></span>|<span data-ttu-id="49d70-122">Fichier Visual C# contenant les méthodes servant à montrer la création d'un ensemble de règles, son enregistrement dans un fichier et son chargement à partir d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="49d70-122">Visual C# file that contains methods to demonstrate creating a rule set, saving a rule set to a file, and loading a rule set from a file.</span></span> <span data-ttu-id="49d70-123">Il contient également un code environnant qui appelle ces méthodes, puis exécute l'ensemble de règles créé.</span><span class="sxs-lookup"><span data-stu-id="49d70-123">Also contains surrounding code that calls these methods and then runs the created rule set.</span></span>|  
|<span data-ttu-id="49d70-124">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="49d70-124">Cleanup.bat</span></span>|<span data-ttu-id="49d70-125">Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="49d70-125">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="49d70-126">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="49d70-126">Removes send and receive ports.</span></span> <span data-ttu-id="49d70-127">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="49d70-127">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="49d70-128">SampleDocumentInstance.xml</span><span class="sxs-lookup"><span data-stu-id="49d70-128">SampleDocumentInstance.xml</span></span>|<span data-ttu-id="49d70-129">Exemple de fichier d'entrée conforme au schéma défini dans le fichier SampleSchema.xsd.</span><span class="sxs-lookup"><span data-stu-id="49d70-129">Sample input file that conforms to the schema defined in the file SampleSchema.xsd.</span></span>|  
|<span data-ttu-id="49d70-130">SampleSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="49d70-130">SampleSchema.xsd</span></span>|<span data-ttu-id="49d70-131">Fichier de schéma qui définit un schéma unique avec un élément référencé par l'ensemble de règles créé dans le fichier Visual C# HelloWorld1.cs.</span><span class="sxs-lookup"><span data-stu-id="49d70-131">Schema file that defines a simple schema with an element referenced by the rule set created in the Visual C# file HelloWorld1.cs.</span></span>|  
|<span data-ttu-id="49d70-132">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="49d70-132">Setup.bat</span></span>|<span data-ttu-id="49d70-133">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="49d70-133">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="49d70-134">Dans le dossier \MySampleLibrary :</span><span class="sxs-lookup"><span data-stu-id="49d70-134">In the \MySampleLibrary folder:</span></span><br /><br /> <span data-ttu-id="49d70-135">AssemblyInfo.cs, MySampleLibrary.csproj, MySampleLibrary.sln</span><span class="sxs-lookup"><span data-stu-id="49d70-135">AssemblyInfo.cs, MySampleLibrary.csproj, MySampleLibrary.sln</span></span>|<span data-ttu-id="49d70-136">Projet, solution et fichiers associés pour la portion de cet exemple qui fournit la classe définissant les objets référencés par l'ensemble de règles créé.</span><span class="sxs-lookup"><span data-stu-id="49d70-136">Project, solution, and related files for the portion of this sample that provides the class that defines the objects referenced by the created rule set.</span></span>|  
|<span data-ttu-id="49d70-137">Dans le dossier \MySampleLibrary :</span><span class="sxs-lookup"><span data-stu-id="49d70-137">In the \MySampleLibrary folder:</span></span><br /><br /> <span data-ttu-id="49d70-138">MySampleLibraryClass.cs</span><span class="sxs-lookup"><span data-stu-id="49d70-138">MySampleLibraryClass.cs</span></span>|<span data-ttu-id="49d70-139">Les fichiers Visual c# qui contient la propriété référencée dans le **IF** partie de la règle créée et la méthode qui peut être appelée dans le **puis** partie de la règle créée.</span><span class="sxs-lookup"><span data-stu-id="49d70-139">Visual C# file that contains the property referenced in the **IF** portion of the created rule, and the method that may be called in the **THEN** portion of the created rule.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="49d70-140">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="49d70-140">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="49d70-141">Suivez la procédure suivante pour créer et initialiser l'exemple de règles d'entreprise « Hello World1 ».</span><span class="sxs-lookup"><span data-stu-id="49d70-141">Use the following procedure to build and initialize the Business Rules Hello World1 sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="49d70-142">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="49d70-142">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="49d70-143">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="49d70-143">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="49d70-144">\<*Exemples de chemin d’accès*> \Business Rules\Business règles Hello World1\\</span><span class="sxs-lookup"><span data-stu-id="49d70-144">\<*Samples Path*>\Business Rules\Business Rules Hello World1\\</span></span>  
  
2.  <span data-ttu-id="49d70-145">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="49d70-145">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="49d70-146">Compile et déploie le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Microsoft utilisé dans l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="49d70-146">Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49d70-147">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="49d70-147">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49d70-148">Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="49d70-148">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="49d70-149">Celle-ci permet de signer les assemblys obtenus.</span><span class="sxs-lookup"><span data-stu-id="49d70-149">Use this key pair to sign the resulting assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49d70-150">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="49d70-150">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="49d70-151">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="49d70-151">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="49d70-152">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="49d70-152">Running This Sample</span></span>  
 <span data-ttu-id="49d70-153">Pour exécuter l'exemple de règles d'entreprise « Hello World1 », procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="49d70-153">Use the following procedure to run the Business Rules Hello World1 sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="49d70-154">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="49d70-154">To run this sample</span></span>  
  
1.  <span data-ttu-id="49d70-155">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="49d70-155">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="49d70-156">\<*Exemples de chemin d’accès*> \Business Rules\Business règles Hello World1\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="49d70-156">\<*Samples Path*>\Business Rules\Business Rules Hello World1\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="49d70-157">Dans la fenêtre Commande, tapez le nom du fichier exécutable pour cet exemple, (BusinessRulesHelloWorld1.exe), puis appuyez sur ENTREE.</span><span class="sxs-lookup"><span data-stu-id="49d70-157">In the command window, type the name of the executable file for this sample (BusinessRulesHelloWorld1.exe), and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49d70-158">Lors de l’exécution, cet exemple produit l’ensemble de règles de fichier SampleRuleStore.xml dans le **bin\Debug** dossier.</span><span class="sxs-lookup"><span data-stu-id="49d70-158">While running, this sample produces the rule set file SampleRuleStore.xml in the **bin\Debug** folder.</span></span> <span data-ttu-id="49d70-159">Lorsque le fichier exécutable marque un arrêt en attendant que vous appuyiez sur ENTRÉE pour terminer, vous pouvez en examiner le contenu.</span><span class="sxs-lookup"><span data-stu-id="49d70-159">When the executable pauses, waiting for you to press ENTER to finish, you can examine the contents of this file.</span></span> <span data-ttu-id="49d70-160">N'oubliez pas de le fermer avant d'appuyer sur une touche pour terminer.</span><span class="sxs-lookup"><span data-stu-id="49d70-160">Remember to close it before pressing any key to finish.</span></span> <span data-ttu-id="49d70-161">Autrement, le fichier exécutable risque de ne pas pouvoir le supprimer en préparation des exécutions suivantes de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="49d70-161">Otherwise, the executable may not be able to delete it in preparation for subsequent runs of the sample.</span></span>  
  
 <span data-ttu-id="49d70-162">Selon la nature de l’ensemble de règles créé, si vous exécutez cet exemple avec l’exemple d’entrée de fichier fourni SampleDocumentInstance.xml, qui a la valeur un (1) définie pour sa **ID** élément, vous verrez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="49d70-162">Based on the nature of the created rule set, if you run this sample with the provided sample input file SampleDocumentInstance.xml, which has a value of one (1) defined for its **ID** element, you will see the following output:</span></span>  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
> [!NOTE]
>  <span data-ttu-id="49d70-163">La sortie en gras, à la fois dans le code précédent et dans le code qui suit, est la sortie produite par l’exemple d’objet métier défini par les fichiers dans le **MySampleLibrary** dossier, qui est référencé par l’ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="49d70-163">The output shown in bold, both in the preceding code and in the code that follows, is the output produced by the sample business object, defined by the files in the **MySampleLibrary** folder, which is referenced by the rule set.</span></span>  
  
 <span data-ttu-id="49d70-164">Si vous modifiez la valeur associée à la **ID** élément dans l’exemple de fichier d’entrée **SampleDocumentInstance.xml** à partir d’un (1) à deux (2), la sortie pourrait être modifié comme suit :</span><span class="sxs-lookup"><span data-stu-id="49d70-164">If you change the value associated with the **ID** element in the sample input file **SampleDocumentInstance.xml** from one (1) to two (2), the output would change as follows:</span></span>  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
 <span data-ttu-id="49d70-165">Vous n’obtiendrez pas une ligne de sortie pour des objets de la **MySampleBusinessObject** classe qui ont leur **MyValue** propriété une valeur qui correspond à la valeur associée à le (pendantlaconstruction) **ID** élément dans l’exemple de fichier d’entrée SampleDocumentInstance.xml.</span><span class="sxs-lookup"><span data-stu-id="49d70-165">You will not get an output line for any objects of the **MySampleBusinessObject** class that have their **MyValue** property set to a value (during construction) that matches the value associated with the **ID** element in the sample input file SampleDocumentInstance.xml.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="49d70-166">Commentaires</span><span class="sxs-lookup"><span data-stu-id="49d70-166">Comments</span></span>  
 <span data-ttu-id="49d70-167">La règle créée par programme dans le **CreateRuleset()** méthode montre :</span><span class="sxs-lookup"><span data-stu-id="49d70-167">The rule created programmatically within the **CreateRuleset()** method shows:</span></span>  
  
 <span data-ttu-id="49d70-168">**IF**</span><span class="sxs-lookup"><span data-stu-id="49d70-168">**IF**</span></span>  
  
 <span data-ttu-id="49d70-169">**MySampleBusinessObject.MyValue** n’est pas égale à la valeur de la **ID** élément dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="49d70-169">**MySampleBusinessObject.MyValue** is not equal to the value of the **ID** element in the XML document.</span></span>  
  
 <span data-ttu-id="49d70-170">**PUIS**</span><span class="sxs-lookup"><span data-stu-id="49d70-170">**THEN**</span></span>  
  
 <span data-ttu-id="49d70-171">**MySampleBusinessObject.MySampleMethod(int)** avec un paramètre de type entier dur codé à la constante cinq (5) dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="49d70-171">**MySampleBusinessObject.MySampleMethod(int)** with an integer parameter, hard coded to the constant five (5) in this case.</span></span> <span data-ttu-id="49d70-172">Cette méthode génère les lignes de sortie qui commencent **MySampleBusinessObject classe –-**.</span><span class="sxs-lookup"><span data-stu-id="49d70-172">This method produces the output lines that begin **MySampleBusinessObject Class –-**.</span></span>  
  
 <span data-ttu-id="49d70-173">Cette règle dépend de ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="49d70-173">This rule depends on the following:</span></span>  
  
-   <span data-ttu-id="49d70-174">A **MySampleBusinessObject** classe avec une propriété publique appelée **MyValue** et une méthode publique appelée **MySampleMethod** (qui prend un paramètre de type entier).</span><span class="sxs-lookup"><span data-stu-id="49d70-174">A **MySampleBusinessObject** class with a public property called **MyValue** and a public method called **MySampleMethod** (that takes in an integer parameter).</span></span>  
  
-   <span data-ttu-id="49d70-175">Un schéma XML schema definition language (XSD) qui définit un document XML qui contient un **ID** élément.</span><span class="sxs-lookup"><span data-stu-id="49d70-175">An XML schema definition language (XSD) schema that defines an XML document that contains an **ID** element.</span></span>  
  
 <span data-ttu-id="49d70-176">Vous définissez les règles en termes de classes et de schémas, mais, en cours d'exécution, des instances d'objet des classes appropriées et des instances de document des schémas appropriés sont requises.</span><span class="sxs-lookup"><span data-stu-id="49d70-176">You define rules in terms of classes and schemas, but during execution, object instances of the relevant classes and document instances of the relevant schemas are required.</span></span> <span data-ttu-id="49d70-177">Vous évaluez les règles par rapport à ces instances d'exécution (appelées faits).</span><span class="sxs-lookup"><span data-stu-id="49d70-177">You evaluate the rules against these run-time instances (known as facts).</span></span> <span data-ttu-id="49d70-178">Dans cet exemple, les faits sont plusieurs instances de la **MySampleBusinessObject** objet construit avec des valeurs différentes pour leurs **MyValue** propriété et une seule instance XML du schéma défini qui contient une valeur pour le **ID** élément.</span><span class="sxs-lookup"><span data-stu-id="49d70-178">In this sample, the facts are multiple instances of the **MySampleBusinessObject** object, constructed with different values for their **MyValue** property, and a single XML instance of the defined schema that contains a value for the **ID** element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d70-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49d70-179">See Also</span></span>  
 [<span data-ttu-id="49d70-180">Règles d’entreprise (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="49d70-180">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)