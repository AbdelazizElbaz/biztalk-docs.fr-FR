---
title: CallOrchestration (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, calling
- examples, orchestrations
ms.assetid: 0c4194f0-c1e2-419a-8a1a-a3c96e8d2667
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6460091297e34609365989739f58ed1f04204c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="callorchestration-biztalk-server-sample"></a><span data-ttu-id="52aeb-102">CallOrchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="52aeb-102">CallOrchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="52aeb-103">L'exemple CallOrchestration illustre l'appel d'une orchestration BizTalk à partir d'une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="52aeb-103">The CallOrchestration sample demonstrates how to call one BizTalk orchestration from another orchestration.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="52aeb-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="52aeb-104">What This Sample Does</span></span>  
 <span data-ttu-id="52aeb-105">Cet exemple illustre l'appel d'une orchestration par une autre orchestration en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="52aeb-105">This sample demonstrates one orchestration calling another orchestration using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="52aeb-106">L'orchestration principale reçoit un message de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="52aeb-106">The primary orchestration receives a purchase order (PO) message.</span></span>  
  
2.  <span data-ttu-id="52aeb-107">L'orchestration principale appelle l'orchestration secondaire pour déterminer le prix d'expédition correspondant au bon de commande.</span><span class="sxs-lookup"><span data-stu-id="52aeb-107">The primary orchestration calls the secondary orchestration to determine the shipping price for the PO.</span></span>  
  
3.  <span data-ttu-id="52aeb-108">L'orchestration secondaire calcule le prix d'expédition demandé et le renvoie à l'orchestration principale.</span><span class="sxs-lookup"><span data-stu-id="52aeb-108">The secondary orchestration calculates the requested shipping price and returns it to the primary orchestration.</span></span>  
  
4.  <span data-ttu-id="52aeb-109">L'orchestration principale met à jour le message de bon de commande avec le prix d'expédition reçu.</span><span class="sxs-lookup"><span data-stu-id="52aeb-109">The primary orchestration updates the PO message with the returned shipping price.</span></span>  
  
5.  <span data-ttu-id="52aeb-110">L'orchestration principale place le message de bon de commande mis à jour dans un dossier à des fins d'inspection.</span><span class="sxs-lookup"><span data-stu-id="52aeb-110">The primary orchestration puts the updated PO message into a folder for your inspection.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="52aeb-111">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="52aeb-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="52aeb-112">La fonction principale de cet exemple est de présenter l'appel d'une orchestration à partir d'une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="52aeb-112">The primary purpose of this sample is to show you how to call an orchestration from within another orchestration.</span></span> <span data-ttu-id="52aeb-113">La possibilité d'appeler des orchestrations permet de diviser les processus d'entreprise en composants réutilisables.</span><span class="sxs-lookup"><span data-stu-id="52aeb-113">The ability to call orchestrations gives you a way to divide your business processes into reusable components.</span></span> <span data-ttu-id="52aeb-114">Vous pouvez factoriser vos processus les plus répandus en orchestrations distinctes pour que d'autres utilisateurs puissent les réutiliser.</span><span class="sxs-lookup"><span data-stu-id="52aeb-114">You can factor your common processes out into separate orchestrations for others to re-use.</span></span>  
  
 <span data-ttu-id="52aeb-115">Dans cet exemple, le **appeler Orchestration** forme dans receivePO.odx appelle findShippingPrice.odx et attend que l’orchestration imbriquée findShippingPrice.odx, pour calculer et retourner le prix d’expédition avant d’envoyer l’achat commande.</span><span class="sxs-lookup"><span data-stu-id="52aeb-115">In this sample, the **Call Orchestration** shape in receivePO.odx invokes findShippingPrice.odx and waits for the nested orchestration, findShippingPrice.odx, to calculate and return the shipping price before sending the purchase order.</span></span> <span data-ttu-id="52aeb-116">L'orchestration findShippingPrice.odx utilise la logique suivante pour calculer le prix d'expédition :</span><span class="sxs-lookup"><span data-stu-id="52aeb-116">The orchestration findShippingPrice.odx uses the following logic to calculate the shipping price:</span></span>  
  
```  
If ( weight * shippingRate ) < minShippingPrice Then  
    shippingPrice = minShippingPrice  
Else  
    shippingPrice = weight * shippingRate  
End If  
```  
  
 <span data-ttu-id="52aeb-117">Le fichier d'exemple de bon de commande entrant InputPO.xml spécifie un poids de 20, ce qui signifie que le message de bon de commande de sortie est passé de 10 à 20.</span><span class="sxs-lookup"><span data-stu-id="52aeb-117">The sample input PO file, InputPO.xml, specifies a weight of 20, resulting in the output PO message having its shipping price changed from 10 to 20.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52aeb-118">Vous ne pouvez pas appeler une transaction à long terme à partir d'une orchestration atomique.</span><span class="sxs-lookup"><span data-stu-id="52aeb-118">You cannot call a long-running transaction from an atomic orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52aeb-119">La différence entre l’utilisation de la **appeler Orchestration** forme et **démarrer Orchestration** forme est que lors de l’appel d’une orchestration, l’appelant attend que l’orchestration imbriquée avant continuer.</span><span class="sxs-lookup"><span data-stu-id="52aeb-119">The difference between using the **Call Orchestration** shape and the **Start Orchestration** shape is that when calling an orchestration, the caller waits for the nested orchestration to return before continuing.</span></span> <span data-ttu-id="52aeb-120">Lors du démarrage d'une orchestration à partir d'une autre orchestration, après que l'appelant démarre l'action, il passe à l'étape suivante du flux de processus.</span><span class="sxs-lookup"><span data-stu-id="52aeb-120">When starting an orchestration from an orchestration, after the caller initiates the action, the caller moves forward to the next step in the process flow.</span></span> <span data-ttu-id="52aeb-121">L'orchestration invoquée par l'appelant est exécutée indépendamment jusqu'à ce que le flux de processus soit terminé.</span><span class="sxs-lookup"><span data-stu-id="52aeb-121">The orchestration that was invoked by the caller runs independently until it finishes the process flow.</span></span> <span data-ttu-id="52aeb-122">Pour plus d’informations, consultez [comment configurer la forme d’Orchestration appeler](../core/how-to-configure-the-call-orchestration-shape.md).</span><span class="sxs-lookup"><span data-stu-id="52aeb-122">For more information, see [How to Configure the Call Orchestration Shape](../core/how-to-configure-the-call-orchestration-shape.md).</span></span> <span data-ttu-id="52aeb-123">Consultez également [comment configurer la forme de démarrer l’Orchestration](../core/how-to-configure-the-start-orchestration-shape.md).</span><span class="sxs-lookup"><span data-stu-id="52aeb-123">Also see [How to Configure the Start Orchestration Shape](../core/how-to-configure-the-start-orchestration-shape.md).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="52aeb-124">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="52aeb-124">Where to Find This Sample</span></span>  
 <span data-ttu-id="52aeb-125">\<*Exemples de chemin d’accès*> \Orchestrations\CallOrchestration\\</span><span class="sxs-lookup"><span data-stu-id="52aeb-125">\<*Samples Path*>\Orchestrations\CallOrchestration\\</span></span>  
  
 <span data-ttu-id="52aeb-126">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="52aeb-126">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="52aeb-127">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="52aeb-127">File(s)</span></span>|<span data-ttu-id="52aeb-128"> Description</span><span class="sxs-lookup"><span data-stu-id="52aeb-128">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52aeb-129">CallOrchestration.btproj, CallOrchestration.sln</span><span class="sxs-lookup"><span data-stu-id="52aeb-129">CallOrchestration.btproj, CallOrchestration.sln</span></span>|<span data-ttu-id="52aeb-130">Fichiers projet et solution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="52aeb-130">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="52aeb-131">CallOrchestrationBinding.xml</span><span class="sxs-lookup"><span data-stu-id="52aeb-131">CallOrchestrationBinding.xml</span></span>|<span data-ttu-id="52aeb-132">Utilisé pour l’installation automatique, notamment la liaison de port.</span><span class="sxs-lookup"><span data-stu-id="52aeb-132">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="52aeb-133">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="52aeb-133">Cleanup.bat</span></span>|<span data-ttu-id="52aeb-134">Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="52aeb-134">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="52aeb-135">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="52aeb-135">Removes send and receive ports.</span></span> <span data-ttu-id="52aeb-136">Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="52aeb-136">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="52aeb-137">findShippingPrice.odx</span><span class="sxs-lookup"><span data-stu-id="52aeb-137">findShippingPrice.odx</span></span>|<span data-ttu-id="52aeb-138">Orchestration BizTalk qui sert d'orchestration secondaire, appelée à partir de l'orchestration principale, receivePO.odx.</span><span class="sxs-lookup"><span data-stu-id="52aeb-138">BizTalk orchestration that serves as a secondary orchestration, called from the primary orchestration, receivePO.odx.</span></span>|  
|<span data-ttu-id="52aeb-139">InputPO.xml</span><span class="sxs-lookup"><span data-stu-id="52aeb-139">InputPO.xml</span></span>|<span data-ttu-id="52aeb-140">Exemple de fichier de bon de commande conforme au schéma défini dans le fichier PO.xsd.</span><span class="sxs-lookup"><span data-stu-id="52aeb-140">Sample input PO message that conforms to the schema defined in the file PO.xsd.</span></span>|  
|<span data-ttu-id="52aeb-141">PO.xsd</span><span class="sxs-lookup"><span data-stu-id="52aeb-141">PO.xsd</span></span>|<span data-ttu-id="52aeb-142">Schéma définissant la structure des messages de bon de commande entrants comme l'exemple de fichier entrant InputPO.xml, ainsi que la promotion des propriétés pour les trois éléments du schéma.</span><span class="sxs-lookup"><span data-stu-id="52aeb-142">Schema that defines the structure of inbound PO messages such as the sample input file InputPO.xml, and defines property promotion for all three elements in the schema.</span></span>|  
|<span data-ttu-id="52aeb-143">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="52aeb-143">PropertySchema.xsd</span></span>|<span data-ttu-id="52aeb-144">Fichier de schéma de propriété qui prend part à la promotion des propriétés pour les trois éléments du schéma PO.xsd.</span><span class="sxs-lookup"><span data-stu-id="52aeb-144">Property schema file that participates in property promotion for all three elements in the schema PO.xsd.</span></span>|  
|<span data-ttu-id="52aeb-145">receivePO.odx</span><span class="sxs-lookup"><span data-stu-id="52aeb-145">receivePO.odx</span></span>|<span data-ttu-id="52aeb-146">Orchestration BizTalk qui sert d'orchestration principale dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="52aeb-146">BizTalk orchestration that serves as the primary orchestration in this sample.</span></span> <span data-ttu-id="52aeb-147">Elle récupère les messages de bon de commande dans le dossier de réception, puis appelle l'autre orchestration, findShippingPrice.odx, pour le calcul et la mise à jour du prix d'expédition.</span><span class="sxs-lookup"><span data-stu-id="52aeb-147">It retrieves PO messages from the receive folder and then calls the other orchestration, findShippingPrice.odx, to calculate and update the shipping price.</span></span>|  
|<span data-ttu-id="52aeb-148">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="52aeb-148">Setup.bat</span></span>|<span data-ttu-id="52aeb-149">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="52aeb-149">Used to build and initialize this sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="52aeb-150">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="52aeb-150">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-callorchestration-sample"></a><span data-ttu-id="52aeb-151">Pour créer et initialiser l'exemple CallOrchestration</span><span class="sxs-lookup"><span data-stu-id="52aeb-151">To build and initialize the CallOrchestration sample</span></span>  
  
1.  <span data-ttu-id="52aeb-152">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="52aeb-152">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="52aeb-153">\<*Exemples de chemin d’accès*> \Orchestrations\CallOrchestration\\</span><span class="sxs-lookup"><span data-stu-id="52aeb-153">\<*Samples Path*>\Orchestrations\CallOrchestration\\</span></span>  
  
2.  <span data-ttu-id="52aeb-154">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="52aeb-154">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="52aeb-155">Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier CallOrchestration.</span><span class="sxs-lookup"><span data-stu-id="52aeb-155">Creates the input (In) and output (Out) folders for this sample in the CallOrchestration folder.</span></span>  
  
    -   <span data-ttu-id="52aeb-156">Compilation et déploiement du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], contenant les deux orchestrations, pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="52aeb-156">Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project, containing both orchestrations, for this sample.</span></span>  
  
    -   <span data-ttu-id="52aeb-157">crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :</span><span class="sxs-lookup"><span data-stu-id="52aeb-157">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="52aeb-158">Active l'emplacement de réception, et démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="52aeb-158">Enables the receive location, and starts the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52aeb-159">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="52aeb-159">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="52aeb-160">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="52aeb-160">Running This Sample</span></span>  
  
#### <a name="to-run-the-callorchestration-sample"></a><span data-ttu-id="52aeb-161">Pour exécuter l'exemple CallOrchestration</span><span class="sxs-lookup"><span data-stu-id="52aeb-161">To run the CallOrchestration sample</span></span>  
  
1.  <span data-ttu-id="52aeb-162">Placez une copie du fichier InputPO.xml dans le dossier In.</span><span class="sxs-lookup"><span data-stu-id="52aeb-162">Put a copy of the file InputPO.xml into the In folder.</span></span>  
  
2.  <span data-ttu-id="52aeb-163">Observez le fichier de bon de commande XML mis à jour créé dans le dossier Out.</span><span class="sxs-lookup"><span data-stu-id="52aeb-163">Observe the updated XML PO file created in the Out folder.</span></span> <span data-ttu-id="52aeb-164">Il contient le message de bon de commande d'origine, modifié de manière à inclure le prix d'expédition calculé, comme expliqué plus haut.</span><span class="sxs-lookup"><span data-stu-id="52aeb-164">It contains the original PO message, modified to include a shipping cost calculated as explained earlier.</span></span> <span data-ttu-id="52aeb-165">Le format du nom de ce fichier est \< *MessageID*> .xml, où  *\<MessageID >* est le GUID généré pour identifier de façon unique le message.</span><span class="sxs-lookup"><span data-stu-id="52aeb-165">The format of the name of this file is \<*MessageID*>.xml, where *\<MessageID>* is the GUID generated to uniquely identify the message.</span></span>  
  
## <a name="uninstalling-this-sample"></a><span data-ttu-id="52aeb-166">Désinstallation de l'exemple</span><span class="sxs-lookup"><span data-stu-id="52aeb-166">Uninstalling This Sample</span></span>  
  
#### <a name="to-uninstall-the-callorchestration-sample"></a><span data-ttu-id="52aeb-167">Pour désinstaller l'exemple CallOrchestration</span><span class="sxs-lookup"><span data-stu-id="52aeb-167">To uninstall the CallOrchestration sample</span></span>  
  
1.  <span data-ttu-id="52aeb-168">Dans une fenêtre de commande [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="52aeb-168">In a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="52aeb-169">\<*Exemples de chemin d’accès*> \Orchestrations\CallOrchestration\\</span><span class="sxs-lookup"><span data-stu-id="52aeb-169">\<*Samples Path*>\Orchestrations\CallOrchestration\\</span></span>  
  
2.  <span data-ttu-id="52aeb-170">Exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="52aeb-170">Run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52aeb-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52aeb-171">See Also</span></span>  
 [<span data-ttu-id="52aeb-172">Orchestrations (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="52aeb-172">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)