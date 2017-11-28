---
title: OperationsSamples (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c9e3f3e-a570-4edd-aa2e-3f8e2e37c8a0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3e190d06c084a6b1b3c9965856897e0df94daab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operationssamples-biztalk-server-sample"></a><span data-ttu-id="fc7f2-102">OperationsSamples (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="fc7f2-102">OperationsSamples (BizTalk Server Sample)</span></span>
<span data-ttu-id="fc7f2-103">L'exemple OperationsSamples montre comment réaliser des activités opérationnelles à l'aide du modèle objet Opérations.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-103">The OperationsSamples sample demonstrates how to perform operational activities using the Operations object model.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="fc7f2-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="fc7f2-104">What This Sample Does</span></span>  
 <span data-ttu-id="fc7f2-105">Cet exemple illustre les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-105">This sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="fc7f2-106">Utilisation d'un modèle de suivi pour commenter une orchestration contenant des activités.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-106">How to use a tracking profile to comment an orchestration with activities.</span></span>  
  
-   <span data-ttu-id="fc7f2-107">Recherche d'un ID d'activité dans la base de données des suivis BAM pour ensuite rechercher à l'aide de cet ID une instance d'orchestration liée.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-107">How to use the BAM tracking database to find an activity ID and then use the ID to find a related orchestration instance.</span></span>  
  
-   <span data-ttu-id="fc7f2-108">Comment rechercher et utiliser des flux de messages à l’aide de la **MessageFlow** classe et d’autres API et classes du modèle objet opérations.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-108">How to find and work with message flows by using the **MessageFlow** class and other Operations object model classes and APIs.</span></span>  
  
-   <span data-ttu-id="fc7f2-109">Comment accéder aux ports, messages et d’autres instances à l’aide des classes dérivées de la **Instance** classe.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-109">How to access ports, messages, and other instances by using classes derived from the **Instance** class.</span></span>  
  
 <span data-ttu-id="fc7f2-110">Cet exemple contient de nombreuses classes et méthodes d'assistance pour assurer la prise en charge des opérations précitées.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-110">The sample contains many useful helper classes and methods to support the operations above.</span></span> <span data-ttu-id="fc7f2-111">Elles sont présentées dans la section suivante, avec d'autres éléments de code.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-111">These and other code highlights are discussed in the next section.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="fc7f2-112">Conception et finalité de l'exemple</span><span class="sxs-lookup"><span data-stu-id="fc7f2-112">How This Sample Is Designed and Why</span></span>  
 <span data-ttu-id="fc7f2-113">Cet exemple est conçu de façon à présenter plusieurs des principales classes et méthodes du modèle objet Opérations et pour expliquer comment exécuter une requête dans la base de données publique des suivis BAM.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-113">This sample is designed to demonstrate several of the key classes and methods in the Operations object model and to show how to query the publicly available BAM tracking database.</span></span>  
  
 <span data-ttu-id="fc7f2-114">Le modèle objet Opérations contient des classes qui permettent de manipuler des messages ainsi que d'autres instances dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-114">The Operations object model contains classes that provide the ability to manipulate messages and other instances within BizTalk Server.</span></span>  
  
### <a name="using-a-bam-activity-id"></a><span data-ttu-id="fc7f2-115">Utilisation d'un ID d'activité BAM</span><span class="sxs-lookup"><span data-stu-id="fc7f2-115">Using a BAM Activity ID</span></span>  
 <span data-ttu-id="fc7f2-116">Cet exemple montre comment interagir avec la base de données des suivis BAM en utilisant les vues publiques pour rechercher un message actif dans le MessageBox à l'aide des données de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-116">This sample shows how to interact with BAM and how to use the publicly available views in the tracking database to locate a live message in the message box by using business data.</span></span> <span data-ttu-id="fc7f2-117">Pour ce faire, l'exemple procède à l'extraction d'un ID d'orchestration correspondant à un numéro de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-117">The sample does this by retrieving an orchestration ID corresponding to a purchase order number.</span></span> <span data-ttu-id="fc7f2-118">Pour que cette tâche aboutisse, la procédure suivante doit être respectée :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-118">For this task to succeed, it must do the following:</span></span>  
  
1.  <span data-ttu-id="fc7f2-119">Utiliser des données d’entreprise (un numéro de commande) pour rechercher un ID d’activité.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-119">Use business data (a purchase order number) to find an activity ID.</span></span> <span data-ttu-id="fc7f2-120">Cette étape mappe les données d’entreprise à un ID interne qui peut être utilisé pour rechercher des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-120">This step maps business data to an internal ID that can be used to find additional information.</span></span>  
  
2.  <span data-ttu-id="fc7f2-121">Extraction des références BAM associées à l'ID de l'activité.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-121">Retrieve the BAM references related to the activity ID.</span></span>  
  
3.  <span data-ttu-id="fc7f2-122">Recherche d'une référence dont le type correspond à « BizTalkService » et se rapporte à une orchestration.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-122">Find a reference that has a type of "BizTalkService" and refers to an orchestration.</span></span> <span data-ttu-id="fc7f2-123">Si une référence est trouvée, l'ID correspondant à l'instance doit être renvoyée.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-123">If one is found, return its instance ID.</span></span>  
  
 <span data-ttu-id="fc7f2-124">Cette fonctionnalité est fournie par le **BAMWebService.GetOrchestrationID** méthode statique et les méthodes d’assistance associées, y compris les classes et méthodes dans le fichier source BamManagementService.cs.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-124">This functionality is provided by the **BAMWebService.GetOrchestrationID** static method and associated helper methods including classes and methods in the BamManagementService.cs source file.</span></span>  
  
### <a name="suspending-terminating-and-resuming-an-instance"></a><span data-ttu-id="fc7f2-125">Interruption, arrêt et reprise d'une instance</span><span class="sxs-lookup"><span data-stu-id="fc7f2-125">Suspending, Terminating, and Resuming an Instance</span></span>  
 <span data-ttu-id="fc7f2-126">L’exemple de programme inclut un **Samples.OperateOnInstance** méthode qui accepte un ID d’opération et l’instance et effectue l’opération spécifiée sur l’instance.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-126">The sample program includes a **Samples.OperateOnInstance** method that takes an operation and instance ID and performs the specified operation on the instance.</span></span> <span data-ttu-id="fc7f2-127">Les opérations valides sont définies par le **InstanceOperation** énumération et inclure l’interrompre, terminer et reprendre.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-127">Valid operations are defined by the **InstanceOperation** enumeration and include Suspend, Terminate, and Resume.</span></span> <span data-ttu-id="fc7f2-128">Ces opérations sont directement mappent aux méthodes de la classe BizTalkOperations :**SuspendInstance**, **TerminateInstance**, et **ResumeInstance**.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-128">These operations map directly to methods of the BizTalkOperations class—**SuspendInstance**, **TerminateInstance**, and **ResumeInstance**.</span></span>  
  
 <span data-ttu-id="fc7f2-129">Notez que cette méthode gère à la fois les exceptions ArgumentException et les exceptions SqlException.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-129">Notice that the method handles both ArgumentException and SqlException exceptions.</span></span> <span data-ttu-id="fc7f2-130">Vous devez veiller à anticiper les exceptions (y compris l’exception SqlException) lorsque vous travaillez avec les classes et méthodes du modèle objet Opérations.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-130">You must be careful to anticipate exceptions—including SqlException—when working with the classes and methods in the Operations object model.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc7f2-131">De nombreuses méthodes Opérations nécessitent un accès à la base de données.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-131">Many of the Operations methods require access to the database.</span></span> <span data-ttu-id="fc7f2-132">Vous devez anticiper les exceptions générées par ces méthodes et les gérer de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-132">You should anticipate the exceptions thrown by these methods and handle them appropriately.</span></span>  
  
### <a name="retrieving-all-live-messages"></a><span data-ttu-id="fc7f2-133">Récupération de tous les messages actifs</span><span class="sxs-lookup"><span data-stu-id="fc7f2-133">Retrieving All Live Messages</span></span>  
 <span data-ttu-id="fc7f2-134">Avec le modèle objet Opérations, il s'avère très simple d'effectuer des itérations sur tous les messages actifs disponibles, comme l'illustre le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-134">The Operations object model makes it straightforward to iterate over all of the available live messages, as shown in the following code fragment:</span></span>  
  
```  
BizTalkOperations _operations = new BizTalkOperations()  
IEnumerable messages = _operations.GetMessages();  
foreach (BizTalkMessage msg in messages)  
…  
```  
  
 <span data-ttu-id="fc7f2-135">Le programme OperationsSamples va encore plus loin puisqu'il permet d'accéder aux informations relatives à chaque message, notamment l'ID et le type du message, ainsi que le nombre de parties dont est constitué le message, et leur type.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-135">The OperationsSamples program takes this a step further by demonstrating how to access information about each message, including message ID and message type along with the number and types of message parts.</span></span> <span data-ttu-id="fc7f2-136">Vous pouvez modifier ce code et l'utiliser dans le cadre de scénarios dans lesquels vous devez effectuer des itérations sur tous les messages actifs ou sur un grand nombre d'entre eux dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-136">You can modify this code and use it in scenarios where you have to iterate through many or all of the available live messages in BizTalk Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc7f2-137">Il peut y avoir des centaines, voire des milliers de messages disponibles.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-137">There may be hundreds or thousands of messages available.</span></span> <span data-ttu-id="fc7f2-138">Une analyse complète de la liste risque de nuire aux performances.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-138">Scanning the entire list may adversely affect performance.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="fc7f2-139">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="fc7f2-139">Where to Find This Sample</span></span>  
 <span data-ttu-id="fc7f2-140">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-140">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="fc7f2-141">\<*Exemples de chemin d’accès*> \Admin\OperationsOM\OperationsSamples\\</span><span class="sxs-lookup"><span data-stu-id="fc7f2-141">\<*Samples Path*>\Admin\OperationsOM\OperationsSamples\\</span></span>  
  
 <span data-ttu-id="fc7f2-142">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-142">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="fc7f2-143">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="fc7f2-143">File(s)</span></span>|<span data-ttu-id="fc7f2-144"> Description</span><span class="sxs-lookup"><span data-stu-id="fc7f2-144">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc7f2-145">BamManagementService.cs</span><span class="sxs-lookup"><span data-stu-id="fc7f2-145">BamManagementService.cs</span></span>|<span data-ttu-id="fc7f2-146">Classe proxy Web du service Web BAM.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-146">Web proxy class for the BAM Web service.</span></span>|  
|<span data-ttu-id="fc7f2-147">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="fc7f2-147">Cleanup.bat</span></span>|<span data-ttu-id="fc7f2-148">Supprime l'exemple d'orchestration et rétablit l'exemple HelloWorld à son état d'origine.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-148">Removes the sample orchestration and restores the HelloWorld sample to its original state.</span></span>|  
|<span data-ttu-id="fc7f2-149">HelloOrchestration.btt</span><span class="sxs-lookup"><span data-stu-id="fc7f2-149">HelloOrchestration.btt</span></span>|<span data-ttu-id="fc7f2-150">Modèle de suivi permettant de mapper des sources d'événements BizTalk à des activités cible BAM.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-150">Tracking profile used to map BizTalk event sources to BAM target activities.</span></span>|  
|<span data-ttu-id="fc7f2-151">HelloOrchestration.xls</span><span class="sxs-lookup"><span data-stu-id="fc7f2-151">HelloOrchestration.xls</span></span>|<span data-ttu-id="fc7f2-152">Feuille de style de définition BAM.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-152">BAM definition style sheet.</span></span>|  
|<span data-ttu-id="fc7f2-153">OperationsSamples.cs</span><span class="sxs-lookup"><span data-stu-id="fc7f2-153">OperationsSamples.cs</span></span>|<span data-ttu-id="fc7f2-154">Fichier source C# contenant le code qui illustre les différents aspects du modèle objet Opérations.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-154">C# source file containing code that demonstrates various aspects of the Operations object model.</span></span>|  
|<span data-ttu-id="fc7f2-155">OperationsSamples.csproj, OperationsSamples.sln, AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="fc7f2-155">OperationsSamples.csproj, OperationsSamples.sln, AssemblyInfo.cs</span></span>|<span data-ttu-id="fc7f2-156">Fichiers de projet, de solution et d'informations de l'assembly pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-156">Project, solution, and assembly information files for this sample.</span></span>|  
|<span data-ttu-id="fc7f2-157">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="fc7f2-157">Setup.bat</span></span>|<span data-ttu-id="fc7f2-158">Permet de créer et d'initialiser cet exemple en modifiant l'exemple d'orchestration HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-158">Used to build and initialize this sample by modifying the HelloWorld orchestration sample.</span></span> <span data-ttu-id="fc7f2-159">Il installe un exemple d'orchestration, déploie des fichiers de définition d'activités BAM et d'éditeur de modèle de suivi, configure des ports et dépose un fichier exemple dans l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-159">It installs a sample orchestration, deploys a BAM Activity Definition and a Tracking Profile Editor file, configures ports, and drops a sample file into the receive location.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="fc7f2-160">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="fc7f2-160">How to Use This Sample</span></span>  
 <span data-ttu-id="fc7f2-161">Cet exemple permet d'explorer les fonctionnalités disponibles dans le modèle objet Opérations.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-161">Use this sample to explore the functionality available in the Operations object model.</span></span> <span data-ttu-id="fc7f2-162">Vous pouvez modifier les routines existantes pour rechercher et utiliser des messages de façon différente, ou ajouter du code répliquant des portions du Hub du groupe dans BizTalk Server Management Console.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-162">Modify existing routines to find and work with messages differently or add new code that replicates portions of the Group Hub in the BizTalk Server Management console.</span></span>  
  
 <span data-ttu-id="fc7f2-163">Vous pouvez également réaliser les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-163">You may also consider some of the following tasks:</span></span>  
  
-   <span data-ttu-id="fc7f2-164">Écrire une application qui assure la réplication du sous-ensemble le plus utilisé dans le Hub du groupe sous la forme d'une application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-164">Write an application that replicates the most-used subset of the Group Hub into a custom application.</span></span>  
  
-   <span data-ttu-id="fc7f2-165">Écrire une application d'approvisionnement personnalisée qui assure la création de ports et l'envoi d'un message destiné aux nouveaux partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-165">Write a custom provisioning application that creates ports and sends a test message through for new trading partners.</span></span>  
  
-   <span data-ttu-id="fc7f2-166">Modifier l'exemple de programme en utilitaire de ligne de commande qui indique à l'écran, dans un fichier XML ou un rapport de type texte, des informations sur un seul ou plusieurs bons de commande.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-166">Modify the sample program into a command-line utility that provides information about a single purchase order or a range of purchase orders to the screen, an XML file, or a text report.</span></span>  
  
## <a name="installing-sample-support-files"></a><span data-ttu-id="fc7f2-167">Installation de fichiers d'exemple de support</span><span class="sxs-lookup"><span data-stu-id="fc7f2-167">Installing Sample Support Files</span></span>  
 <span data-ttu-id="fc7f2-168">Cette section présente les procédures requises pour installer et exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-168">This section walks through the procedures required to install and run the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc7f2-169">Avant de procéder à l'installation et à l'exécution de cet exemple, vous devez vérifier que l'analyse BAM est bien installée et en état de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-169">Before installing and running this sample, you must verify that BAM has been installed and is functioning.</span></span> <span data-ttu-id="fc7f2-170">Dans le cas contraire, cet exemple ne pourra pas s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-170">If BAM has not been installed, this sample will not work.</span></span>  
  
#### <a name="to-compile-and-install-the-support-files-for-this-sample"></a><span data-ttu-id="fc7f2-171">Pour compiler et installer les fichiers de support de cet exemple</span><span class="sxs-lookup"><span data-stu-id="fc7f2-171">To compile and install the support files for this sample</span></span>  
  
1.  <span data-ttu-id="fc7f2-172">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-172">In a command window, navigate to the following folder:</span></span>  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
2.  <span data-ttu-id="fc7f2-173">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-173">Run Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="fc7f2-174">Création de répertoires d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="fc7f2-174">Creates send and receive directories</span></span>  
  
    -   <span data-ttu-id="fc7f2-175">Création et démarrage de ports d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="fc7f2-175">Creates and starts send and receive ports</span></span>  
  
    -   <span data-ttu-id="fc7f2-176">Compilation et déploiement de l'orchestration HelloWorld dans le dossier `<Samples Path>`\Orchestrations\HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-176">Compiles and deploys the HelloWorld orchestration in the `<Samples Path>`\Orchestrations\HelloWorld folder.</span></span>  
  
    -   <span data-ttu-id="fc7f2-177">Modification du jeton de clé publique pour l'orchestration HelloWorld</span><span class="sxs-lookup"><span data-stu-id="fc7f2-177">Modifies the public key token for the HelloWorld orchestration</span></span>  
  
    -   <span data-ttu-id="fc7f2-178">Déploiement des fichiers de définition d'activité BAM et d'éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="fc7f2-178">Deploys the BAM Activity Definition and Tracking Profile Editor file</span></span>  
  
    -   <span data-ttu-id="fc7f2-179">Attribution d'un nouveau nom au répertoire de sortie</span><span class="sxs-lookup"><span data-stu-id="fc7f2-179">Renames the out directory</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc7f2-180">Pour abandonner l'installation, appuyez sur CTRL+C lorsque la première invite s'affiche, vous demandant d'appuyer sur une touche pour continuer.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-180">To abort the installation, press CTRL+C at the first "press any key to continue" prompt.</span></span> <span data-ttu-id="fc7f2-181">Le script est ainsi arrêté et l'exemple HelloWorld reste à son état d'origine.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-181">This stops the script and leaves the HelloWorld sample in its original state.</span></span> <span data-ttu-id="fc7f2-182">Si vous appuyez sur CTRL+C à la deuxième et dernière invite, le processus d'installation ne s'arrête pas.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-182">Pressing CTRL+C on the second and final prompt does not stop the installation.</span></span> <span data-ttu-id="fc7f2-183">Dans ce cas, vous devez exécuter le fichier Cleanup.bat pour désinstaller l'exemple OperationsOM et rétablir l'exemple HelloWorld à son état d'origine.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-183">In this case, run Cleanup.bat to uninstall the OperationsOM sample and restore the HelloWorld sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="fc7f2-184">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="fc7f2-184">Running This Sample</span></span>  
 <span data-ttu-id="fc7f2-185">La procédure suivante permet d'exécuter l'exemple OperationsOM.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-185">Use the following procedure to run the OperationsOM sample.</span></span>  
  
#### <a name="to-compile-and-run-the-sample"></a><span data-ttu-id="fc7f2-186">Pour compiler et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="fc7f2-186">To compile and run the sample</span></span>  
  
1.  <span data-ttu-id="fc7f2-187">Cliquez sur **Démarrer**, sélectionnez **tous les programmes**, sélectionnez **Microsoft BizTalk Server**, puis sélectionnez **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-187">Click **Start**, select **All Programs**, select **Microsoft BizTalk Server**, and then select **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fc7f2-188">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Instances de l’hôte**.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-188">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="fc7f2-189">Avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-189">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc7f2-190">Il peut s'avérer nécessaire de redémarrer l'instance de l'hôte BizTalkServerApplication pour définir la base de données effective pour l'analyse BAM, si vous n'avez pas redémarré l'instance de l'hôte depuis la configuration du produit.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-190">Restarting the BizTalkServerApplication host instance may be necessary to set the correct working database for BAM if you have not restarted the host instance since configuring the product.</span></span>  
  
4.  <span data-ttu-id="fc7f2-191">Dans l'Explorateur Windows, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="fc7f2-191">From Windows Explorer, navigate to the following folder:</span></span>  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
5.  <span data-ttu-id="fc7f2-192">Double-cliquez sur le **OperationsOM.sln** fichier projet pour le charger dans [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc7f2-192">Double-click the **OperationsOM.sln** project file to load it into [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span></span>  
  
6.  <span data-ttu-id="fc7f2-193">Appuyez sur la touche F5 pour exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-193">Press F5 to run the sample.</span></span>  
  
     <span data-ttu-id="fc7f2-194">--OU--</span><span class="sxs-lookup"><span data-stu-id="fc7f2-194">-- OR --</span></span>  
  
     <span data-ttu-id="fc7f2-195">Sur le **générer** menu, cliquez sur **régénérer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-195">On the **Build** menu, click **Rebuild Solution**.</span></span> <span data-ttu-id="fc7f2-196">Lorsque la build est terminée, utilisez l’Explorateur Windows pour accéder à `<Samples Path>\Admin\OperationsOM\OperationSamples\bin\Debug,` , puis double-cliquez sur **OperationsSamples.exe**.</span><span class="sxs-lookup"><span data-stu-id="fc7f2-196">When the build is complete, use Windows Explorer to navigate to `<Samples Path>\Admin\OperationsOM\OperationSamples\bin\Debug,` and then double-click **OperationsSamples.exe**.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="fc7f2-197">Classes ou méthodes utilisées dans l'exemple</span><span class="sxs-lookup"><span data-stu-id="fc7f2-197">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="fc7f2-198">[Microsoft.BizTalk.Operations.BizTalkOperations](http://msdn.microsoft.com/library/microsoft.biztalk.operations.biztalkoperations.aspx)&#124; [Microsoft.BizTalk.Operations.MessageFlow](http://msdn.microsoft.com/library/microsoft.biztalk.operations.messageflow.aspx)&#124; [Microsoft.BizTalk.Operations.SendPortInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.sendportinstance.aspx)&#124; [Microsoft.BizTalk.Operations.RoutingFailureInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.routingfailureinstance.aspx)&#124; [Microsoft.BizTalk.Operations.OrchestrationInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.orchestrationinstance.aspx)&#124; [Microsoft.BizTalk.Operations.MSMQtInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.msmqtinstance.aspx)&#124; [Microsoft.BizTalk.Operations.TrackedServiceInstance](http://msdn.microsoft.com/library/Microsoft.BizTalk.Operations.TrackedServiceInstance.aspx)</span><span class="sxs-lookup"><span data-stu-id="fc7f2-198">[Microsoft.BizTalk.Operations.BizTalkOperations](http://msdn.microsoft.com/library/microsoft.biztalk.operations.biztalkoperations.aspx)&#124; [Microsoft.BizTalk.Operations.MessageFlow](http://msdn.microsoft.com/library/microsoft.biztalk.operations.messageflow.aspx)&#124; [Microsoft.BizTalk.Operations.SendPortInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.sendportinstance.aspx)&#124; [Microsoft.BizTalk.Operations.RoutingFailureInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.routingfailureinstance.aspx)&#124; [Microsoft.BizTalk.Operations.OrchestrationInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.orchestrationinstance.aspx)&#124; [Microsoft.BizTalk.Operations.MSMQtInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.msmqtinstance.aspx)&#124; [Microsoft.BizTalk.Operations.TrackedServiceInstance](http://msdn.microsoft.com/library/Microsoft.BizTalk.Operations.TrackedServiceInstance.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc7f2-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc7f2-199">See Also</span></span>  
 [<span data-ttu-id="fc7f2-200">Admin-OperationsOM (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="fc7f2-200">Admin-OperationsOM (BizTalk Server Samples Folder)</span></span>](../core/admin-operationsom-biztalk-server-samples-folder.md)