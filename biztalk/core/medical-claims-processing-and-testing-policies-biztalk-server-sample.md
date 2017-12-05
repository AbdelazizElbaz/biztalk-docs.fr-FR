---
title: "Soins médicaux des revendications de traitement et de test des stratégies (exemple BizTalk Server) | Documents Microsoft"
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
ms.assetid: c0bdf7b7-3e55-4560-a5a8-00c5b661d14d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70cba6055c51371ddaaf99775bd5e7a60e7f3929
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="medical-claims-processing-and-testing-policies-biztalk-server-sample"></a><span data-ttu-id="bad1c-102">Soins médicaux revendications le traitement et le tests de stratégies (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="bad1c-102">Medical Claims Processing and Testing Policies (BizTalk Server Sample)</span></span>
<span data-ttu-id="bad1c-103">L'exemple Stratégies de test et de traitement des demandes de remboursement de soins médicaux illustre la création d'un ensemble de règles qui examinent des faits dérivés d'une table de base de données et du document entrant et qui utilisent les objets .NET pour enregistrer les résultats du traitement des demandes de remboursement.</span><span class="sxs-lookup"><span data-stu-id="bad1c-103">The Medical Claims Processing and Testing Policies sample demonstrates how to create a rule set containing multiple rules that examine facts derived from a database table and the inbound document, and which use .NET-based objects to record the results of the claims processing.</span></span>  
  
 <span data-ttu-id="bad1c-104">Cet exemple montre l'exécution de bout en bout du scénario de traitement des demandes de remboursement à l'aide d'une simple application .NET utilisant le Moteur de règles d'entreprise pour exécuter un ensemble de règles relatives aux demandes de remboursement de soins médicaux sur les demandes de remboursement entrantes afin de déterminer l'ÉTAT de la demande de remboursement et la RAISON de l'état.</span><span class="sxs-lookup"><span data-stu-id="bad1c-104">This sample demonstrates end-end execution of the claim processing scenario using a simple .NET-based application that uses the Business Rule Engine to run a medical claims rule set against incoming claims to determine the STATUS of the claim and the REASON for the status.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bad1c-105">Cet exemple présente également le suivi de l'exécution du Moteur de règles d'entreprise à l'aide d'un fichier de suivi de débogage.</span><span class="sxs-lookup"><span data-stu-id="bad1c-105">This sample also demonstrates how to trace Business Rule Engine execution using a debug trace file.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="bad1c-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="bad1c-106">What This Sample Does</span></span>  
 <span data-ttu-id="bad1c-107">Cet exemple applique la séquence suivante de règles aux demandes de remboursement envoyées :</span><span class="sxs-lookup"><span data-stu-id="bad1c-107">This sample applies the following sequence of rules to submitted claims:</span></span>  
  
1.  <span data-ttu-id="bad1c-108">Rejette la demande de remboursement si le montant total demandé dépasse le maximum autorisé par la police.</span><span class="sxs-lookup"><span data-stu-id="bad1c-108">Rejects the claim if the total amount claimed exceeds the maximum permitted by the policy.</span></span>  
  
2.  <span data-ttu-id="bad1c-109">Rejette la demande de remboursement si le nombre de nuits passées à l'hôpital par le client dépasse le maximum autorisé par la police.</span><span class="sxs-lookup"><span data-stu-id="bad1c-109">Rejects the claim if the client has stayed in hospitals more nights than the maximum permitted by the policy.</span></span>  
  
3.  <span data-ttu-id="bad1c-110">Rejette la demande de remboursement si la date sur la demande de remboursement est dans le futur.</span><span class="sxs-lookup"><span data-stu-id="bad1c-110">Rejects the claim if the date on the claim is in the future.</span></span>  
  
4.  <span data-ttu-id="bad1c-111">Rejette la demande de remboursement si la police n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="bad1c-111">Rejects the claim if the policy is not valid.</span></span>  
  
5.  <span data-ttu-id="bad1c-112">Envoie un message au service commercial avec l'ID de police et le nom du client si la police a expiré.</span><span class="sxs-lookup"><span data-stu-id="bad1c-112">Sends a lead to the sales department with the policy ID and customer name if the policy has expired.</span></span>  
  
6.  <span data-ttu-id="bad1c-113">Dans le cas contraire, approuve la demande de remboursement.</span><span class="sxs-lookup"><span data-stu-id="bad1c-113">Otherwise, approves the claim.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="bad1c-114">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="bad1c-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="bad1c-115">\<*Exemples de chemin d’accès*\>\Business Rules\Medical les revendications de traitement et de test Policies\\</span><span class="sxs-lookup"><span data-stu-id="bad1c-115">\<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\\</span></span>  
  
 <span data-ttu-id="bad1c-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="bad1c-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="bad1c-117">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="bad1c-117">File(s)</span></span>|<span data-ttu-id="bad1c-118"> Description</span><span class="sxs-lookup"><span data-stu-id="bad1c-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bad1c-119">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="bad1c-119">Cleanup.bat</span></span>|<span data-ttu-id="bad1c-120">Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="bad1c-120">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="bad1c-121">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="bad1c-121">Removes send and receive ports.</span></span> <span data-ttu-id="bad1c-122">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="bad1c-122">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="bad1c-123">Create_PolicyValidity_Table.sql</span><span class="sxs-lookup"><span data-stu-id="bad1c-123">Create_PolicyValidity_Table.sql</span></span>|<span data-ttu-id="bad1c-124">Script SQL qui ajoute une nouvelle table nommée PolicyValidity à l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="bad1c-124">SQL script that adds a new table named PolicyValidity to the Northwind sample database.</span></span>|  
|<span data-ttu-id="bad1c-125">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="bad1c-125">Setup.bat</span></span>|<span data-ttu-id="bad1c-126">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bad1c-126">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="bad1c-127">Dans le dossier \Claims :</span><span class="sxs-lookup"><span data-stu-id="bad1c-127">In the \Claims folder:</span></span><br /><br /> <span data-ttu-id="bad1c-128">AssemblyInfo.cs, Claims.csproj, Claims.sln, Claims.cs</span><span class="sxs-lookup"><span data-stu-id="bad1c-128">AssemblyInfo.cs, Claims.csproj, Claims.sln, Claims.cs</span></span>|<span data-ttu-id="bad1c-129">Projet, solution, source et les fichiers associés pour la partie de cet exemple qui enregistre le résultat de réclamations, appelée la **puis** partie d’une règle.</span><span class="sxs-lookup"><span data-stu-id="bad1c-129">Project, solution, source, and related files for the portion of this sample that records the result of the claims processing, called the **THEN** portion of a rule.</span></span>|  
|<span data-ttu-id="bad1c-130">Dans le dossier \FactRetrieverForClaimsProcessing :</span><span class="sxs-lookup"><span data-stu-id="bad1c-130">In the \FactRetrieverForClaimsProcessing folder:</span></span><br /><br /> <span data-ttu-id="bad1c-131">AssemblyInfo.cs, FactRetrieverForClaimsProcessing.cs, FactRetrieverForClaimsProcessing.csproj, FactRetrieverForClaimsProcessing.sln</span><span class="sxs-lookup"><span data-stu-id="bad1c-131">AssemblyInfo.cs, FactRetrieverForClaimsProcessing.cs, FactRetrieverForClaimsProcessing.csproj, FactRetrieverForClaimsProcessing.sln</span></span>|<span data-ttu-id="bad1c-132">Fichiers de projet, de solution, source et associé pour la partie de cet exemple qui fournit l'extracteur de faits à long terme qui extrait des informations de la table PolicyValidity créée par cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bad1c-132">Project, solution, source, and related files for the portion of this sample that provides the long-term fact retriever that retrieves information from the PolicyValidity table created by this sample.</span></span>|  
|<span data-ttu-id="bad1c-133">Dans le dossier \RulesForMedicalClaims :</span><span class="sxs-lookup"><span data-stu-id="bad1c-133">In the \RulesForMedicalClaims folder:</span></span><br /><br /> <span data-ttu-id="bad1c-134">App.ico, AssemblyInfo.cs, RulesForMedicalClaims.cs, RulesForMedicalClaims.csproj, RulesForMedicalClaims.sln</span><span class="sxs-lookup"><span data-stu-id="bad1c-134">App.ico, AssemblyInfo.cs, RulesForMedicalClaims.cs, RulesForMedicalClaims.csproj, RulesForMedicalClaims.sln</span></span>|<span data-ttu-id="bad1c-135">Projet, solution, source et les fichiers associés pour la partie de cet exemple qui constitue le principal exécutable pour cet exemple (RulesForMedicalClaims.exe) et qui par programme définit et stocke l’ensemble de règles, construit les exemples de faits et exécute ensuite le règle définie à l’aide un **PolicyTester** objet.</span><span class="sxs-lookup"><span data-stu-id="bad1c-135">Project, solution, source, and related files for the portion of this sample that constitutes the main executable for this sample (RulesForMedicalClaims.exe), and which programmatically defines and stores the rule set, constructs sample facts, and then runs the rule set using a **PolicyTester** object.</span></span>|  
|<span data-ttu-id="bad1c-136">Dans le dossier \RulesForMedicalClaims :</span><span class="sxs-lookup"><span data-stu-id="bad1c-136">In the \RulesForMedicalClaims folder:</span></span><br /><br /> <span data-ttu-id="bad1c-137">MedicalClaims.xsd</span><span class="sxs-lookup"><span data-stu-id="bad1c-137">MedicalClaims.xsd</span></span>|<span data-ttu-id="bad1c-138">Fichier de schéma qui définit la structure des exemples de demandes de remboursement de soins médicaux envoyés à cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bad1c-138">Schema file that defines the structure of the sample medical claims submitted to this sample.</span></span>|  
|<span data-ttu-id="bad1c-139">Dans le dossier \RulesForMedicalClaims :</span><span class="sxs-lookup"><span data-stu-id="bad1c-139">In the \RulesForMedicalClaims folder:</span></span><br /><br /> <span data-ttu-id="bad1c-140">sampleClaim.xml</span><span class="sxs-lookup"><span data-stu-id="bad1c-140">sampleClaim.xml</span></span>|<span data-ttu-id="bad1c-141">Exemple de fichier d'entrée correspondant au schéma défini dans le fichier MedicalClaims.xsd.</span><span class="sxs-lookup"><span data-stu-id="bad1c-141">Sample input file that conforms to the schema defined in the file MedicalClaims.xsd.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="bad1c-142">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="bad1c-142">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-medical-claims-processing-and-testing-policies-sample"></a><span data-ttu-id="bad1c-143">Pour créer et initialiser l'exemple Stratégies de test et de traitement des demandes de remboursement de soins médicaux</span><span class="sxs-lookup"><span data-stu-id="bad1c-143">To build and initialize the Medical Claims Processing and Testing Policies sample</span></span>  
  
1.  <span data-ttu-id="bad1c-144">Vérifiez que vous disposez de la base de données Northwind sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bad1c-144">Make sure that you have the Northwind database on your machine.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bad1c-145">Pour exécuter cet exemple, vous devez disposer de la base de données Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bad1c-145">To run this sample, you must have the Northwind SQL Server sample database.</span></span> <span data-ttu-id="bad1c-146">[Télécharger](https://www.microsoft.com/download/details.aspx?id=23654)et l’installer.</span><span class="sxs-lookup"><span data-stu-id="bad1c-146">[Download](https://www.microsoft.com/download/details.aspx?id=23654), and install.</span></span> 
  
2.  <span data-ttu-id="bad1c-147">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="bad1c-147">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="bad1c-148">\<*Exemples de chemin d’accès*\>\Business Rules\Medical les revendications de traitement et de test Policies\\</span><span class="sxs-lookup"><span data-stu-id="bad1c-148">\<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\\</span></span>  
  
3.  <span data-ttu-id="bad1c-149">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="bad1c-149">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="bad1c-150">Compilation et déploiement des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple, y compris Claims.dll, FactRetrieverForClaimsProcessing.dll et RulesForMedicalClaims.dll.</span><span class="sxs-lookup"><span data-stu-id="bad1c-150">Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, including Claims.dll, FactRetrieverForClaimsProcessing.dll, and RulesForMedicalClaims.dll.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bad1c-151">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bad1c-151">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bad1c-152">Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="bad1c-152">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="bad1c-153">Celle-ci permet de signer les assemblys obtenus.</span><span class="sxs-lookup"><span data-stu-id="bad1c-153">Use this key pair to sign the resulting assemblies.</span></span>  
  
    -   <span data-ttu-id="bad1c-154">Exécution du script SQL fourni, Create_PolicyValidity_Table.sql, à l'aide de l'Analyseur de requêtes SQL.</span><span class="sxs-lookup"><span data-stu-id="bad1c-154">Runs the provided SQL script Create_PolicyValidity_Table.sql using SQL Query Analyzer.</span></span> <span data-ttu-id="bad1c-155">Le script crée la table PolicyValidity avec deux exemples de lignes dans l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="bad1c-155">The script creates the table, PolicyValidity, with two sample rows in the Northwind sample database.</span></span> <span data-ttu-id="bad1c-156">Cette table contient deux colonnes : ID et PolicyStatus.</span><span class="sxs-lookup"><span data-stu-id="bad1c-156">This table has two columns: ID and PolicyStatus.</span></span>  
  
    -   <span data-ttu-id="bad1c-157">Crée et lie les ports d'envoi et de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bad1c-157">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports.</span></span>  
  
    -   <span data-ttu-id="bad1c-158">Active l'emplacement de réception, et démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bad1c-158">Enables the receive location, and starts the send port.</span></span>  
  
    -   <span data-ttu-id="bad1c-159">Inscrit et démarre l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="bad1c-159">Enlists and starts orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bad1c-160">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="bad1c-160">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="bad1c-161">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="bad1c-161">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="bad1c-162">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="bad1c-162">Running This Sample</span></span>  
  
#### <a name="to-run-the-medical-claims-processing-and-testing-policies-sample"></a><span data-ttu-id="bad1c-163">Pour exécuter l'exemple Stratégies de test et de traitement des demandes de remboursement de soins médicaux</span><span class="sxs-lookup"><span data-stu-id="bad1c-163">To run the Medical Claims Processing and Testing Policies sample</span></span>  
  
1.  <span data-ttu-id="bad1c-164">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="bad1c-164">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="bad1c-165">\<*Exemples de chemin d’accès*\>\Business Rules\Medical les revendications de traitement et de test Policies\RulesForMedicalClaims\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="bad1c-165">\<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\RulesForMedicalClaims\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="bad1c-166">Exécutez le fichier RulesForMedicalClaims.exe sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bad1c-166">Run the file RulesForMedicalClaims.exe on the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bad1c-167">Vous pouvez modifier les valeurs des éléments individuels dans l'exemple de fichier de demande de remboursement sampleClaim.xml, puis exécuter l'exemple de façon répétée.</span><span class="sxs-lookup"><span data-stu-id="bad1c-167">You can change the values of individual elements in the sample claim file sampleClaim.xml and run the sample repeatedly.</span></span> <span data-ttu-id="bad1c-168">Les résultats attendus des différentes valeurs de ces éléments sont affichés dans la liste suivante.</span><span class="sxs-lookup"><span data-stu-id="bad1c-168">The expected outputs for different values in these elements are shown in the list that follows.</span></span>  
  
 <span data-ttu-id="bad1c-169">Les scénarios de sortie en fonction des différentes combinaisons de valeurs dans l'exemple de fichier de demande de remboursement envoyé sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="bad1c-169">Output scenarios based on various combinations of values in the submitted sample claims file are:</span></span>  
  
-   <span data-ttu-id="bad1c-170">Pour une demande de remboursement dont le montant dépasse 1000 $, le résultat suivant est obtenu :</span><span class="sxs-lookup"><span data-stu-id="bad1c-170">For a claim whose amount exceeds $1000, the following output is obtained:</span></span>  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of claim has exceeded Policy limit  
    ```  
  
-   <span data-ttu-id="bad1c-171">Pour une demande de remboursement dont le nombre de nuits dépasse 10, le résultat suivant est obtenu :</span><span class="sxs-lookup"><span data-stu-id="bad1c-171">For a claim whose number of nights exceeds 10, the following output is obtained:</span></span>  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of Nights has exceeded Policy limit  
    ```  
  
-   <span data-ttu-id="bad1c-172">Pour une demande de remboursement dont la date n'est pas valide (date > date actuelle), le résultat suivant est obtenu :</span><span class="sxs-lookup"><span data-stu-id="bad1c-172">For a claim whose date is not valid (date > current date), the following output in obtained:</span></span>  
  
    ```  
    Status:  REJECTED!  
    Reason:  Cannot submit claims for future dates!  
    ```  
  
-   <span data-ttu-id="bad1c-173">Pour une revendication avec un ID de stratégie n’est pas valide (par exemple, en modifiant le **ID** ont une valeur de 2) en raison de l’expiration de la stratégie, le résultat suivant est obtenu :</span><span class="sxs-lookup"><span data-stu-id="bad1c-173">For a claim with a policy ID that is not valid (for example, by changing the **ID** element to have a value of 2) because of policy expiration, the following output is obtained:</span></span>  
  
    ```  
    Sending to Renewal Department for Customer Smir with Policy # 2  
    Status:  REJECTED!  
    Reason:  Policy ID is invalid  
    ```  
  
-   <span data-ttu-id="bad1c-174">Pour une demande de remboursement valide, le résultat suivant est obtenu :</span><span class="sxs-lookup"><span data-stu-id="bad1c-174">For a claim that is valid, the following output is obtained:</span></span>  
  
    ```  
    Status:  Claim Accepted!  
    Reason:  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bad1c-175">Un fichier texte, outputtrace.txt, est créé dans le dossier ...\RulesForMedicalClaims\bin\Debug à chaque exécution de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bad1c-175">A text file, outputtrace.txt, is created in the folder ...\RulesForMedicalClaims\bin\Debug folder every time you run this sample.</span></span> <span data-ttu-id="bad1c-176">Il contient un suivi de débogage de l'exécution des règles, et il est créé après chaque cycle d'exécution dans le dossier \RulesForMedicalClaims\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="bad1c-176">It contains a debug trace of rule execution, and it is created after every execution cycle under the folder \RulesForMedicalClaims\bin\Debug.</span></span> <span data-ttu-id="bad1c-177">Vous pouvez examiner ce fichier pour afficher le suivi de sortie de l'exécution des règles.</span><span class="sxs-lookup"><span data-stu-id="bad1c-177">You can examine this file to see the output trace of rule execution.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="bad1c-178">Commentaires</span><span class="sxs-lookup"><span data-stu-id="bad1c-178">Comments</span></span>  
 <span data-ttu-id="bad1c-179">Les sources de faits utilisées dans l'évaluation de l'ensemble de règles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bad1c-179">The fact sources used in the rule set evaluation are:</span></span>  
  
-   <span data-ttu-id="bad1c-180">Un extracteur de faits à long terme, un. Application basée sur le réseau qui implémente le **IFactReriever** de l’interface, est créé dans le dossier FactRetrieverForClaimsProcessing.</span><span class="sxs-lookup"><span data-stu-id="bad1c-180">A long-term fact retriever, a .NET-based application that implements the **IFactReriever** interface, is built in the folder FactRetrieverForClaimsProcessing.</span></span> <span data-ttu-id="bad1c-181">Il est utilisé par la stratégie de traitement des demandes de remboursement de soins médicaux pour extraire des données (sous forme de groupes de données) de la base de données PolicyValidity ainsi que pour l'évaluation de condition de règles.</span><span class="sxs-lookup"><span data-stu-id="bad1c-181">It is used by the medical claims processing policy to retrieve data (in the form of a dataset) from the PolicyValidity database and to use in rule condition evaluation.</span></span>  
  
-   <span data-ttu-id="bad1c-182">La demande de remboursement est un document XML contenant les informations suivantes, stockées dans des éléments frères : Nom, ID, Montant, Nuits et Date.</span><span class="sxs-lookup"><span data-stu-id="bad1c-182">The claim is in the form of an XML document that contains the following information, stored in sibling elements: Name, ID, Amount, Nights, and Date.</span></span>  
  
-   <span data-ttu-id="bad1c-183">UN FICHIER. Bibliothèque de classes NET (Claims), avec un **ClaimResults** classe est utilisée pour enregistrer l’état et la raison de la demande à l’aide des propriétés et pour envoyer un message (si la stratégie n’est pas valide) en appelant le **SendLeads** méthode avec l’ID et le nom en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="bad1c-183">A .NET-based class library (Claims), with a **ClaimResults** class is used to record the STATUS and REASON of the claim using properties, and to send a lead (if the policy is not valid) by invoking the **SendLeads** method with ID and name as parameters.</span></span>  
  
 <span data-ttu-id="bad1c-184">En fonction de ces sources de faits, vous pouvez décrire de manière informelle les règles définies pour ce scénario comme suit :</span><span class="sxs-lookup"><span data-stu-id="bad1c-184">Based on these fact sources, you can informally describe the rules defined for this scenario as follows:</span></span>  
  
1.  <span data-ttu-id="bad1c-185">Vérifiez si la demande de remboursement entrante est valide.</span><span class="sxs-lookup"><span data-stu-id="bad1c-185">Check to see if the incoming claim is valid.</span></span> <span data-ttu-id="bad1c-186">La demande de remboursement n'est pas valide si le montant dépasse la limite autorisée pour une demande de remboursement, si la police a expiré (vérification de la table de base de données), si le nombre de nuits dépasse la limite autorisée et si la demande de remboursement est effectuée dans le futur.</span><span class="sxs-lookup"><span data-stu-id="bad1c-186">The claim is not valid if the amount is over the allowable limit for a claim, if the policy has expired (verified by checking the database table), if the number of nights has exceeded the maximum allowable limit, and if the claim is made for a future date.</span></span> <span data-ttu-id="bad1c-187">Si la demande de remboursement a été déterminée comme non valide, définissez l'ÉTAT et la RAISON de la demande de remboursement de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="bad1c-187">If the claim has been determined to be not valid, set the STATUS and REASON of the claim appropriately.</span></span>  
  
2.  <span data-ttu-id="bad1c-188">Si l'ID de police de la demande de remboursement entrante a expiré, envoyez un message (avec l'ID de police et le nom du client) au service de renouvellement des polices.</span><span class="sxs-lookup"><span data-stu-id="bad1c-188">If the policy ID of the incoming claim has expired, send a lead (with policy ID and customer name) to the policy renewal department.</span></span>  
  
3.  <span data-ttu-id="bad1c-189">Si la demande de remboursement est valide, définissez l'ÉTAT et la RAISON de la demande de remboursement de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="bad1c-189">If the claim is valid, set the STATUS and REASON of the claim appropriately.</span></span>  
  
 <span data-ttu-id="bad1c-190">Une représentation plus formelle des règles et de leurs liaisons à terme est la suivante :</span><span class="sxs-lookup"><span data-stu-id="bad1c-190">A more formal representation of the rules and their term bindings is as follows:</span></span>  
  
-   <span data-ttu-id="bad1c-191">**Règle 1. Vérification de la quantité**</span><span class="sxs-lookup"><span data-stu-id="bad1c-191">**Rule 1. Amount check**</span></span>  
  
    ```  
    IF Amount in the XML document is > 1000  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"\  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="bad1c-192">**Règle 2. Nuits passées à l’hôpital**</span><span class="sxs-lookup"><span data-stu-id="bad1c-192">**Rule 2. Nights spent in the hospital**</span></span>  
  
    ```  
    IF number of nights in the XML document is > 10  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="bad1c-193">**Règle 3. Validité de date**</span><span class="sxs-lookup"><span data-stu-id="bad1c-193">**Rule 3. Date validity**</span></span>  
  
    ```  
    IF date on the incoming XML claim is > Today  
      AND   
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Cannot submit claims in the future!"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="bad1c-194">**Règle 4. Validité de la stratégie**</span><span class="sxs-lookup"><span data-stu-id="bad1c-194">**Rule 4. Policy validity**</span></span>  
  
    ```  
    IF Policy is invalid for the ID in the XML claim (check database)  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Policy Invalid"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="bad1c-195">**Règle 5. Prospects**</span><span class="sxs-lookup"><span data-stu-id="bad1c-195">**Rule 5. Sales lead**</span></span>  
  
    ```  
    IF Claim.ClaimResults.Reason = "Policy invalid"  
  
    THEN send a lead to the policy department by invoking the function Claim.ClaimResults.SendLead with customer ID and Name from the incoming XML document.  
  
    ```  
  
-   <span data-ttu-id="bad1c-196">**Règle 6. Demande de remboursement acceptée**</span><span class="sxs-lookup"><span data-stu-id="bad1c-196">**Rule 6. Claim accepted**</span></span>  
  
    ```  
    IF Claim.ClaimResults.Status = null  
  
    THEN Set the claim status to be valid  
         &&  
         Send the lead to the sales department  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bad1c-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bad1c-197">See Also</span></span>  
 [<span data-ttu-id="bad1c-198">Règles d’entreprise (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="bad1c-198">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)