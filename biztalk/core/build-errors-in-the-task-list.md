---
title: "Erreurs dans la liste des tâches de build | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building, errors
- errors, building
ms.assetid: 05b36511-3031-4e13-ac2f-bfdbec0f48cb
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bfd5b9f7b974b00d63831484ecbaa44e2568fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="build-errors-in-the-task-list"></a><span data-ttu-id="f1424-102">Erreurs de génération dans la liste des tâches</span><span class="sxs-lookup"><span data-stu-id="f1424-102">Build Errors in the Task List</span></span>
<span data-ttu-id="f1424-103">Lorsque vous générez votre projet ou solution, les résultats s'affichent dans la fenêtre Sortie tandis que les erreurs individuelles et avertissements apparaissent dans la liste des tâches.</span><span class="sxs-lookup"><span data-stu-id="f1424-103">When you build your project, or solution, the results will appear in the Output window, while individual errors and warnings will appear in the task list.</span></span>  
  
 <span data-ttu-id="f1424-104">Les erreurs et avertissements apparaissent dans la liste des tâches.</span><span class="sxs-lookup"><span data-stu-id="f1424-104">Errors and warnings appear in the task list.</span></span> <span data-ttu-id="f1424-105">Vous pouvez double-cliquer sur l'erreur. La sélection s'applique alors à l'objet qui n'est pas configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="f1424-105">You can double-click the error, and the focus will be applied to the object that is not correctly configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1424-106">Lors de la génération, le compilateur ne valide pas les XPath.</span><span class="sxs-lookup"><span data-stu-id="f1424-106">When you build, the compiler does not validate XPaths.</span></span> <span data-ttu-id="f1424-107">Prenez garde d’utiliser une syntaxe XPath valide.</span><span class="sxs-lookup"><span data-stu-id="f1424-107">Take care to use valid XPath syntax.</span></span>  
  
## <a name="insufficient-configuration-action"></a><span data-ttu-id="f1424-108">Action relative à une configuration insuffisante</span><span class="sxs-lookup"><span data-stu-id="f1424-108">Insufficient configuration Action</span></span>  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!CAUTION]
>  <span data-ttu-id="f1424-109">Si le Concepteur d'orchestration fournit des avertissements relatifs à une configuration insuffisante là où il le peut, rien ne garantit que votre orchestration soit correctement compilée en l'absence de ce genre d'avertissements.</span><span class="sxs-lookup"><span data-stu-id="f1424-109">While Orchestration Designer will provide insufficient configuration warnings where it can, there is no guarantee that your orchestration will compile correctly in the absence of such warnings.</span></span>  
  
## <a name="compiler-asks-if-you-are-missing-an-assembly-reference"></a><span data-ttu-id="f1424-110">Le compilateur vous demande s'il manque une référence d'assembly</span><span class="sxs-lookup"><span data-stu-id="f1424-110">Compiler asks if you are missing an assembly reference</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-111">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-111">Problem</span></span>  
 <span data-ttu-id="f1424-112">Lorsque vous compilez l'orchestration, un message d'erreur s'affiche. Il finit par la question « ne manque-t-il pas une référence d'assembly ? ».</span><span class="sxs-lookup"><span data-stu-id="f1424-112">When you compile your orchestration you get an error message that ends with the question "are you missing an assembly reference?"</span></span> <span data-ttu-id="f1424-113">Les deux messages les plus courants sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f1424-113">Two of the more common messages are:</span></span>  
  
-   <span data-ttu-id="f1424-114">Le type ou le nom d'espace de noms 'X' n'existe pas dans l'espace de noms 'Y' (ne manque-t-il pas une référence d'assembly ?)</span><span class="sxs-lookup"><span data-stu-id="f1424-114">The type or namespace name 'X' does not exist in the namespace 'Y' (are you missing an assembly reference?)</span></span>  
  
-   <span data-ttu-id="f1424-115">L'identificateur 'X' n'existe pas dans 'Y' ; ne manque-t-il pas une référence d'assembly ?</span><span class="sxs-lookup"><span data-stu-id="f1424-115">Identifier 'X' does not exist in 'Y'; are you missing an assembly reference?</span></span>  
  
### <a name="cause"></a><span data-ttu-id="f1424-116">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-116">Cause</span></span>  
 <span data-ttu-id="f1424-117">Cette erreur peut être générée par l'un des cas suivants :</span><span class="sxs-lookup"><span data-stu-id="f1424-117">Any of the following could be the cause of this error.</span></span>  
  
-   <span data-ttu-id="f1424-118">Votre projet ne fait pas référence aux assemblys requis.</span><span class="sxs-lookup"><span data-stu-id="f1424-118">Your project does not reference one or more required assemblies.</span></span>  
  
-   <span data-ttu-id="f1424-119">Votre projet comporte un mappage ou un autre type d'objet dont le nom est identique au projet.</span><span class="sxs-lookup"><span data-stu-id="f1424-119">Your project has a map or other object type that has the same name as the project.</span></span>  
  
-   <span data-ttu-id="f1424-120">Votre projet utilise des schémas PIP (Partner Interface Process) basés sur le langage XSD (XML Schema definition language) et contient des schémas XSD dans un sous-dossier appelé Système.</span><span class="sxs-lookup"><span data-stu-id="f1424-120">Your project uses XML Schema definition language (XSD)-based Partner Interface Process (PIP) schemas and contains XSD schemas in a subfolder that is named System.</span></span>  
  
-   <span data-ttu-id="f1424-121">Votre projet utilise une propriété globale dont l'espace de noms est un sous-ensemble de l'espace de nom actuel du projet.</span><span class="sxs-lookup"><span data-stu-id="f1424-121">Your project is using a Global Property whose namespace is a subset of the current project's namespace.</span></span> <span data-ttu-id="f1424-122">Par exemple, l'utilisation de l'espace de noms de propriété globale « File.ReceivedFileName » dans une orchestration contenue dans le projet « Accounts.FILE ».</span><span class="sxs-lookup"><span data-stu-id="f1424-122">For example, using the Global Property namespace "File.ReceivedFileName" in an orchestration contained in the project "Accounts.FILE".</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-123">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-123">Resolution</span></span>  
 <span data-ttu-id="f1424-124">Les solutions suivantes peuvent s'appliquer, en fonction de la cause du problème :</span><span class="sxs-lookup"><span data-stu-id="f1424-124">Depending upon the cause of the problem, the resolution could be any of the following:</span></span>  
  
-   <span data-ttu-id="f1424-125">Ajoutez une référence aux assemblys manquants nécessaires au projet.</span><span class="sxs-lookup"><span data-stu-id="f1424-125">Add a reference to the missing assemblies your project requires.</span></span>  
  
-   <span data-ttu-id="f1424-126">Attribuez un nom de mappage ou d'objet différent du nom du projet.</span><span class="sxs-lookup"><span data-stu-id="f1424-126">Change the name of the map or other object to something other than the project name.</span></span> <span data-ttu-id="f1424-127">Vous pouvez effectuer cette opération dans la page des propriétés de l'objet (par exemple, la page de propriétés du mappage contient une propriété Nom).</span><span class="sxs-lookup"><span data-stu-id="f1424-127">This can typically be done through the object's property page (for example, the Map property page contains a Name property).</span></span>  
  
-   <span data-ttu-id="f1424-128">Modifiez l'espace de noms des schémas dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1424-128">Change the namespace for the schemas in Visual Studio.</span></span> <span data-ttu-id="f1424-129">Pour faire cela à l’aide de Visual Studio, cliquez sur **afficher tous les fichiers** sur la **projet** menu, puis développez le **système** nœud dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="f1424-129">To do this using Visual Studio, click **Show All Files** on the **Project** menu, and then expand the **System** node in Solution Explorer.</span></span> <span data-ttu-id="f1424-130">Cliquez sur chaque fichier dans le dossier système et de ses sous-dossiers et modifiez l’entrée de l’espace de noms dans la fenêtre Propriétés ainsi que toute occurrence de **système** devienne _**système**.</span><span class="sxs-lookup"><span data-stu-id="f1424-130">Click each file in the System folder and in any subfolders, and then change the namespace entry in the Properties window so that any occurrence of **System** becomes _**System**.</span></span> <span data-ttu-id="f1424-131">Par exemple, remplacez le **MyProject.System.SubFolder** espace de noms **MyProject._System.Subfolder** espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f1424-131">For example, change the **MyProject.System.SubFolder** namespace to **the MyProject._System.Subfolder** namespace.</span></span> <span data-ttu-id="f1424-132">Pour plus d’informations sur ce problème, consultez l’article [916649](http://support.microsoft.com/?kbid=916649).</span><span class="sxs-lookup"><span data-stu-id="f1424-132">For more information about this issue, see KB article [916649](http://support.microsoft.com/?kbid=916649).</span></span>  
  
-   <span data-ttu-id="f1424-133">Supprimez l'espace de noms de propriété globale conflictuel du projet.</span><span class="sxs-lookup"><span data-stu-id="f1424-133">Remove the conflicting Global Property namespace from the project.</span></span>  
  
## <a name="you-receive-a-message-has-not-been-initialized-in-construct-statement-error-when-building-your-project"></a><span data-ttu-id="f1424-134">L'erreur « le message n'a pas été initialisé dans l'instruction de construction » s'affiche lors de la génération du projet</span><span class="sxs-lookup"><span data-stu-id="f1424-134">You receive a "Message has not been initialized in construct statement" error when building your project</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-135">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-135">Problem</span></span>  
 <span data-ttu-id="f1424-136">Lorsque vous compilez l'application BizTalk, l'erreur « le message n'a pas été initialisé dans l'instruction de construction » s'affiche.</span><span class="sxs-lookup"><span data-stu-id="f1424-136">When you compile your BizTalk application, you get the error "Message has not been initialized in construct statement".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="f1424-137">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-137">Cause</span></span>  
 <span data-ttu-id="f1424-138">Lorsque vous créez un message, vous en indiquez toutes les variables.</span><span class="sxs-lookup"><span data-stu-id="f1424-138">When you construct a message, you specify all the message variables.</span></span> <span data-ttu-id="f1424-139">Vous procédez ensuite aux affectations au message ou à des parties de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="f1424-139">Then you make assignments to the message or its parts.</span></span> <span data-ttu-id="f1424-140">Si une affectation de message est inclus dans une fonction **construire un Message** forme, vous pouvez recevoir le message d’erreur d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="f1424-140">If part of a specific message assignment is included in a separate **Construct Message** shape, you may receive the initialization error message.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-141">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-141">Resolution</span></span>  
 <span data-ttu-id="f1424-142">Pour résoudre ce problème, assurez-vous que vous incluez toutes les parties d’une assignation de message spécifique dans le même **construire un Message** forme.</span><span class="sxs-lookup"><span data-stu-id="f1424-142">To resolve this behavior, make sure that you include all parts of a specific message assignment in the same **Construct Message** shape.</span></span> <span data-ttu-id="f1424-143">Pour obtenir un support liées, consultez l’article [870606](http://support.microsoft.com/?kbid=870606).</span><span class="sxs-lookup"><span data-stu-id="f1424-143">For a related support issue, see KB article [870606](http://support.microsoft.com/?kbid=870606).</span></span>  
  
 <span data-ttu-id="f1424-144">Vous pouvez également résoudre ce problème en créant un message dans un **construire** forme avant d’utiliser une instance de celui-ci dans un **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="f1424-144">You can also resolve this behavior by creating your message in a **Construct** shape before using an instance of it in an **Expression** shape.</span></span> <span data-ttu-id="f1424-145">Par exemple, le code suivant génère une erreur si placé dans un **Expression** forme :</span><span class="sxs-lookup"><span data-stu-id="f1424-145">For example, the following code will cause an error if placed in an **Expression** shape:</span></span>  
  
```  
XMLDOM = new System.Xml.XmlDocument();  
POAckMsg = XMLDOM;  
```  
  
 <span data-ttu-id="f1424-146">Pour résoudre le problème, créez une instance de XMLDOM dans une **construire** mettre en forme, puis effectuez l’assignation dans une en aval **Expression** forme.</span><span class="sxs-lookup"><span data-stu-id="f1424-146">To fix, create the instance of XMLDOM in a **Construct** shape, and then do the assignment in a downstream **Expression** shape.</span></span>  
  
## <a name="you-receive-a-use-of-unconstructed-message-error-when-building-your-project"></a><span data-ttu-id="f1424-147">L'erreur « utilisation du message non construit » s'affiche lors de la génération du projet</span><span class="sxs-lookup"><span data-stu-id="f1424-147">You receive a "use of unconstructed message" error when building your project</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-148">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-148">Problem</span></span>  
 <span data-ttu-id="f1424-149">Lorsque vous compilez votre projet BizTalk, vous recevez l’erreur « utilisation du message non construit '\<message >' ».</span><span class="sxs-lookup"><span data-stu-id="f1424-149">When you compile your BizTalk project, you receive the error "use of unconstructed message '\<message>'".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="f1424-150">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-150">Cause</span></span>  
 <span data-ttu-id="f1424-151">Cette erreur se produit lorsqu’un message non construit est utilisé dans un **envoyer** forme.</span><span class="sxs-lookup"><span data-stu-id="f1424-151">This error occurs when an unconstructed message is used in a **Send** shape.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-152">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-152">Resolution</span></span>  
 <span data-ttu-id="f1424-153">Pour résoudre ce problème, ajoutez un **construire un Message** forme à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1424-153">To resolve this issue, add a **Construct Message** shape to the orchestration.</span></span> <span data-ttu-id="f1424-154">Inclure le **construire un Message** avant de mettre en forme le **envoyer** forme est liée à un service Web.</span><span class="sxs-lookup"><span data-stu-id="f1424-154">Include the **Construct Message** shape before the **Send** shape that is bound to the Web service.</span></span>  
  
 <span data-ttu-id="f1424-155">Pour plus d’informations sur cette erreur et les services Web, consultez l’article [921043](http://support.microsoft.com/?kbid=921043).</span><span class="sxs-lookup"><span data-stu-id="f1424-155">For more information about this error and Web services, see KB article [921043](http://support.microsoft.com/?kbid=921043).</span></span>  
  
## <a name="setting-a-transaction-level-for-a-scope-results-in-an-error"></a><span data-ttu-id="f1424-156">Définition du niveau de transaction pour les résultats de l'étendue d'une erreur</span><span class="sxs-lookup"><span data-stu-id="f1424-156">Setting a transaction level for a scope results in an error</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-157">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-157">Problem</span></span>  
 <span data-ttu-id="f1424-158">Une fois le type de transaction configuré pour une étendue ou une autre entité prenant en charge des transactions dans l'orchestration, le message « Une orchestration non transactionnelle ne peut contenir aucune autre transaction » s'affiche.</span><span class="sxs-lookup"><span data-stu-id="f1424-158">After configuring the transaction type for a scope or other entity supporting transactions in an orchestration, you receive the error "A Non-transactional Orchestration cannot contain any other Transactions".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="f1424-159">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-159">Cause</span></span>  
 <span data-ttu-id="f1424-160">Cette erreur se produit lorsque vous tentez de configurer le type de transaction d'une étendue (ou d'une autre entité) d'une orchestration en « Atomique » ou « À long terme » lorsque le type de transaction de l'orchestration elle-même est « Aucun ».</span><span class="sxs-lookup"><span data-stu-id="f1424-160">This error occurs when you try to configure the transaction type of a scope (or other entity) in an orchestration to "Atomic" or "Long-Running" when the orchestration itself has a transaction type of "None".</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-161">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-161">Resolution</span></span>  
 <span data-ttu-id="f1424-162">Assurez-vous que les paramètres du type de transaction de l'orchestration et des objets qui la composent sont compatibles.</span><span class="sxs-lookup"><span data-stu-id="f1424-162">Ensure that the transaction type settings of your orchestration and constituent objects are compatible.</span></span>  
  
## <a name="project-build-results-in-the-error-you-must-specify-at-least-one-already-initialized-correlation-set-for-a-non-activation-receive-that-is-on-a-non-selfcorrelating-port"></a><span data-ttu-id="f1424-163">La génération du projet entraîne l'affichage du message d'erreur « vous devez indiquer au moins un ensemble de corrélations déjà initialisé pour une réception sans activation située sur un port autre qu'un port d'autocorrélation »</span><span class="sxs-lookup"><span data-stu-id="f1424-163">Project build results in the error "you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port"</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-164">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-164">Problem</span></span>  
 <span data-ttu-id="f1424-165">Lorsque vous compilez votre projet BizTalk, le message d'erreur « vous devez indiquer au moins un ensemble de corrélations déjà initialisé pour une réception sans activation située sur un port autre qu'un port d'autocorrélation » s'affiche.</span><span class="sxs-lookup"><span data-stu-id="f1424-165">When you compile your BizTalk project, you receive the error "you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port".</span></span>  
  
### <a name="cause"></a><span data-ttu-id="f1424-166">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-166">Cause</span></span>  
 <span data-ttu-id="f1424-167">Cette erreur peut se produire si votre orchestration ne possède aucune forme **réception** formes (activer = true) ou ne possède aucune forme **réception** formes et n’est pas appelé directement par une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1424-167">This error can occur if your orchestration has no activating **Receive** shapes (Activate = true) or has no activating **Receive** shapes and is not called directly by another orchestration.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-168">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-168">Resolution</span></span>  
 <span data-ttu-id="f1424-169">Si votre orchestration n’est pas appelée par une autre orchestration, vous devez configurer un de le **réception** formes soit active.</span><span class="sxs-lookup"><span data-stu-id="f1424-169">If your orchestration is not called by another orchestration, you must configure one of the **Receive** shapes to be an activated receive.</span></span> <span data-ttu-id="f1424-170">Pour plus d’informations sur la configuration de la **réception** forme, y compris des liens vers la corrélation, consultez [comment configurer la forme réception](../core/how-to-configure-the-receive-shape.md).</span><span class="sxs-lookup"><span data-stu-id="f1424-170">For more information about configuring the **Receive** shape, including links to correlation, see [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md).</span></span>  
  
## <a name="you-receive-the-error-assembly-generation-failed----referenced-assembly-assembly-does-not-have-a-strong-name-when-building-your-solution"></a><span data-ttu-id="f1424-171">Vous recevez l’erreur « Échec de la génération de l’Assembly--l’assembly référencé '\<assembly >' n’a pas un nom fort » lors de la génération de votre solution</span><span class="sxs-lookup"><span data-stu-id="f1424-171">You receive the error "Assembly generation failed -- Referenced assembly '\<assembly>' does not have a strong name" when building your solution</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-172">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-172">Problem</span></span>  
 <span data-ttu-id="f1424-173">Vous recevez l’erreur « Échec de la génération de l’Assembly--l’assembly référencé '\<assembly >' n’a pas un nom fort » lorsque la génération de votre solution qui a une orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1424-173">You receive the error "Assembly generation failed -- Referenced assembly '\<assembly>' does not have a strong name" when building your solution that has an orchestration.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="f1424-174">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-174">Cause</span></span>  
 <span data-ttu-id="f1424-175">Ce problème se produit lorsqu'un type issu d'un assembly référencé non signé est utilisé dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1424-175">This problem occurs when a type from an unsigned referenced assembly is used within an orchestration.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-176">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-176">Resolution</span></span>  
 <span data-ttu-id="f1424-177">Attribuez un nom fort à l'assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="f1424-177">Apply a strong name to the referenced assembly.</span></span> <span data-ttu-id="f1424-178">S'il s'agit d'un assembly personnalisé que vous pouvez recompiler, utilisez l'outil Strong Name Tool pour créer un fichier (de clé) .snk, puis référencez ce fichier de clé dans les propriétés de l'assembly du projet.</span><span class="sxs-lookup"><span data-stu-id="f1424-178">If it is a custom assembly that you can recompile, use the strong name tool to create an .snk (key) file and then reference that key file in the assembly properties for the project.</span></span> <span data-ttu-id="f1424-179">Pour plus d’informations sur un assembly de noms forts, consultez [comment configurer un fichier de clé de Assembly de nom fort](../core/how-to-configure-a-strong-name-assembly-key-file.md).</span><span class="sxs-lookup"><span data-stu-id="f1424-179">For more information about strong naming an assembly, see [How to Configure a Strong Name Assembly Key File](../core/how-to-configure-a-strong-name-assembly-key-file.md).</span></span>  
  
## <a name="the-error-failed-to-add-resources-change-requests-failed-for-some-resources-occurs-when-deploying-an-orchestration"></a><span data-ttu-id="f1424-180">L'erreur « Échec d'ajout de ressource(s).</span><span class="sxs-lookup"><span data-stu-id="f1424-180">The error "Failed to add resource(s).</span></span> <span data-ttu-id="f1424-181">Échec des requêtes de modification pour certaines ressources » se produit lors du déploiement d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="f1424-181">Change requests failed for some resources" occurs when deploying an orchestration</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-182">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-182">Problem</span></span>  
 <span data-ttu-id="f1424-183">Lors du déploiement d'une orchestration, le message d'erreur suivant s'affiche et le déploiement échoue :</span><span class="sxs-lookup"><span data-stu-id="f1424-183">When deploying an orchestration, an error similar to the following is displayed and deployment of the orchestration fails:</span></span>  
  
```  
Failed to add resource(s). Change requests failed for some resources. BizTalkAssemblyResourceManager failed to complete end type change request. Object reference not set to an instance of an object.  
```  
  
### <a name="cause"></a><span data-ttu-id="f1424-184">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-184">Cause</span></span>  
 <span data-ttu-id="f1424-185">Cette erreur se produit si l'orchestration contient des objets qui utilisent les mots clés de C#.</span><span class="sxs-lookup"><span data-stu-id="f1424-185">This error can occur if the orchestration contains any objects that use C# keywords.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-186">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-186">Resolution</span></span>  
 <span data-ttu-id="f1424-187">Supprimez tout mot clé de C# de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1424-187">Remove any C# keywords from the orchestration.</span></span> <span data-ttu-id="f1424-188">Pour obtenir la liste des mots clés c#, consultez [http://go.microsoft.com/fwlink/?LinkId=74346](http://go.microsoft.com/fwlink/?LinkId=74346).</span><span class="sxs-lookup"><span data-stu-id="f1424-188">For a list of C# keywords, see [http://go.microsoft.com/fwlink/?LinkId=74346](http://go.microsoft.com/fwlink/?LinkId=74346).</span></span>  
  
## <a name="you-receive-an-invalid-property-value-error-when-compiling-your-orchestration"></a><span data-ttu-id="f1424-189">Une erreur de valeur de propriété incorrecte s'affiche lors de la compilation de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="f1424-189">You receive an "invalid property value" error when compiling your orchestration</span></span>  
  
### <a name="problem"></a><span data-ttu-id="f1424-190">Problème</span><span class="sxs-lookup"><span data-stu-id="f1424-190">Problem</span></span>  
 <span data-ttu-id="f1424-191">Une erreur de valeur de propriété incorrecte s'affiche lors de la génération de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1424-191">You receive the error dialog "Invalid property value" when building your orchestration.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="f1424-192">Cause</span><span class="sxs-lookup"><span data-stu-id="f1424-192">Cause</span></span>  
 <span data-ttu-id="f1424-193">Des objets de la solution ont des noms identiques.</span><span class="sxs-lookup"><span data-stu-id="f1424-193">One or more of the objects in your solution has the same name as another object.</span></span> <span data-ttu-id="f1424-194">Par exemple, un message a le même nom qu'un port.</span><span class="sxs-lookup"><span data-stu-id="f1424-194">For example, a message name is the same as a port name.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="f1424-195">Résolution</span><span class="sxs-lookup"><span data-stu-id="f1424-195">Resolution</span></span>  
 <span data-ttu-id="f1424-196">Vérifiez que chaque objet de la solution a un nom unique.</span><span class="sxs-lookup"><span data-stu-id="f1424-196">Ensure that every object in your solution has a unique name.</span></span> <span data-ttu-id="f1424-197">Pour éviter que cette erreur se produise, vous pouvez adhérer à une convention d'affectation de nom.</span><span class="sxs-lookup"><span data-stu-id="f1424-197">You can minimize the risk of this error by adhering to a naming convention.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1424-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1424-198">See Also</span></span>  
 [<span data-ttu-id="f1424-199">Comment créer des Orchestrations</span><span class="sxs-lookup"><span data-stu-id="f1424-199">How to Build Orchestrations</span></span>](../core/how-to-build-orchestrations.md)