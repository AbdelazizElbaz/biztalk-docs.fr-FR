---
title: CBRSample (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, routing
- messages, filters
- outbound maps
- examples, messages
- messages, routing
- examples, outbound maps
- examples, filters
- messages, examples
ms.assetid: 8fba494c-9257-4eed-8b6a-867056147c2c
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b772bc44d4a745d5bfa330e7df7fcadcf2c020db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cbrsample-biztalk-server-sample"></a><span data-ttu-id="5beb1-102">CBRSample (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5beb1-102">CBRSample (BizTalk Server Sample)</span></span>
<span data-ttu-id="5beb1-103">L'exemple CBRSample présente l'application de filtres et d'un mappage sortant pour transformer et acheminer des messages d'instance sur la base de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="5beb1-103">The CBRSample sample demonstrates how to apply filters and an outbound map to transform and route instance messages based on content.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5beb1-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="5beb1-104">What This Sample Does</span></span>  
 <span data-ttu-id="5beb1-105">Cet exemple montre l'acheminement d'un message contenant le nom, l'adresse et les informations de contact vers l'un des deux dossiers en fonction du code pays.</span><span class="sxs-lookup"><span data-stu-id="5beb1-105">This sample demonstrates the routing of a message containing name, address, and contact information to one of two folders based on country code.</span></span> <span data-ttu-id="5beb1-106">Plus précisément, cet exemple effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5beb1-106">Specifically, this sample does the following:</span></span>  
  
1.  <span data-ttu-id="5beb1-107">Définition d'un exemple de format de message contenant des informations de base sur une personne, notamment son identité avec l'ID d'utilisateur et le nom complet, son adresse avec le code pays et ses coordonnées téléphoniques.</span><span class="sxs-lookup"><span data-stu-id="5beb1-107">Defines a sample message format containing basic information about a person including identity with user ID and full name, address with country code, and phone contact information.</span></span>  
  
2.  <span data-ttu-id="5beb1-108">Promeut la **CountryCode** propriété dans le document d’entrée afin qu’elle peut être utilisée dans un filtre de port pour contrôler la transformation et le routage.</span><span class="sxs-lookup"><span data-stu-id="5beb1-108">Promotes the **CountryCode** property in the input document so that it can be used in a port filter to control transformation and routing.</span></span>  
  
3.  <span data-ttu-id="5beb1-109">Transforme le message en une version canadienne lorsque **CountryCode** est égal à 200 ou une version américaine lorsque **CountryCode**est égal à 100.</span><span class="sxs-lookup"><span data-stu-id="5beb1-109">Transforms the message into a Canadian version when **CountryCode** is equal to 200 or a U.S. version when **CountryCode**is equal to 100.</span></span> <span data-ttu-id="5beb1-110">Les deux transformations transmettent toutes les données à l’exception de milieu initiales (**initiale**).</span><span class="sxs-lookup"><span data-stu-id="5beb1-110">Both transforms pass through all data except middle initial (**Initial**).</span></span> <span data-ttu-id="5beb1-111">La version canadienne mappe également **état** à **Province** et **ZipCode** à **PinCode**.</span><span class="sxs-lookup"><span data-stu-id="5beb1-111">The Canadian version also maps **State** to **Province** and **ZipCode** to **PinCode**.</span></span>  
  
4.  <span data-ttu-id="5beb1-112">Acheminement des messages américains vers le répertoire US et des messages canadiens vers le répertoire CAN.</span><span class="sxs-lookup"><span data-stu-id="5beb1-112">Routes U.S. messages to the US directory and Canadian messages to the CAN directory.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="5beb1-113">Cet exemple est conçu et pourquoi</span><span class="sxs-lookup"><span data-stu-id="5beb1-113">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="5beb1-114">La conception s'appuie sur les pipelines d'envoi et de réception XML par défaut, la promotion des propriétés, les filtres d'abonnement et les mappages sortants dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="5beb1-114">The design relies on the default send and receive XML pipelines, property promotion, subscription filters, and outbound maps within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to route messages.</span></span> <span data-ttu-id="5beb1-115">Le tableau suivant répertorie les éléments de conception et leur justification.</span><span class="sxs-lookup"><span data-stu-id="5beb1-115">The following table shows design elements and their justification.</span></span>  
  
|<span data-ttu-id="5beb1-116">Élément de conception</span><span class="sxs-lookup"><span data-stu-id="5beb1-116">Design element</span></span>|<span data-ttu-id="5beb1-117">Raison(s) sélectionnée(s)</span><span class="sxs-lookup"><span data-stu-id="5beb1-117">Reason(s) selected</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="5beb1-118">Pipeline XML de réception par défaut</span><span class="sxs-lookup"><span data-stu-id="5beb1-118">Default XML receive pipeline</span></span>|<span data-ttu-id="5beb1-119">-Le pipeline XMLReceive prend en charge la promotion de propriétés ; le pipeline PassThruReceive ne fait pas.</span><span class="sxs-lookup"><span data-stu-id="5beb1-119">-   The XMLReceive pipeline supports property promotion; the PassThruReceive pipeline does not.</span></span><br /><span data-ttu-id="5beb1-120">-Le message entrant est déjà au format XML et ne nécessite pas de traitement dépasse le désassemblage de base et la résolution du tiers.</span><span class="sxs-lookup"><span data-stu-id="5beb1-120">-   The inbound message is already in XML format and does not require processing beyond basic disassembly and party resolution.</span></span>|  
|<span data-ttu-id="5beb1-121">Promotion des propriétés</span><span class="sxs-lookup"><span data-stu-id="5beb1-121">Property promotion</span></span>|<span data-ttu-id="5beb1-122">-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]dépend des champs de propriété pour effectuer le routage.</span><span class="sxs-lookup"><span data-stu-id="5beb1-122">-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]depends upon property fields to do routing.</span></span> <span data-ttu-id="5beb1-123">Des champs distinctifs sont utilisés par les orchestrations et ne peuvent pas être utilisés à des fins de routage.</span><span class="sxs-lookup"><span data-stu-id="5beb1-123">Distinguished fields are used by orchestrations and cannot be used for routing.</span></span>|  
|<span data-ttu-id="5beb1-124">Filtre d'abonnement</span><span class="sxs-lookup"><span data-stu-id="5beb1-124">Subscription filter</span></span>|<span data-ttu-id="5beb1-125">-Le filtre d’abonnement réalise l’acheminement réel en capturant les messages qui répondent aux critères d’un ou plusieurs en fonction des champs de propriété.</span><span class="sxs-lookup"><span data-stu-id="5beb1-125">-   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.</span></span>|  
|<span data-ttu-id="5beb1-126">Mappage sortant</span><span class="sxs-lookup"><span data-stu-id="5beb1-126">Outbound map</span></span>|<span data-ttu-id="5beb1-127">-Mappages convertissent les données d’un format vers un autre.</span><span class="sxs-lookup"><span data-stu-id="5beb1-127">-   Maps transform data from one format to another.</span></span> <span data-ttu-id="5beb1-128">L'exemple mappe un message entrant à un format américain ou canadien.</span><span class="sxs-lookup"><span data-stu-id="5beb1-128">The sample maps an inbound message to either a U.S. or Canadian format.</span></span>|  
|<span data-ttu-id="5beb1-129">XMLTransmit</span><span class="sxs-lookup"><span data-stu-id="5beb1-129">XMLTransmit</span></span>|<span data-ttu-id="5beb1-130">-Effectue l’assemblage de base de messages XML sortants ; le pipeline PassThruTransmit ne fournit aucune prise en charge supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="5beb1-130">-   Performs basic assembly of outgoing XML messages; the PassThruTransmit pipeline provides no additional support.</span></span>|  
  
 <span data-ttu-id="5beb1-131">Ce modèle de base peut être étendu et utilisé pour des scénarios plus complexes.</span><span class="sxs-lookup"><span data-stu-id="5beb1-131">This basic pattern can be extended and used for more complex scenarios.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5beb1-132">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="5beb1-132">Where to Find This Sample</span></span>  
 <span data-ttu-id="5beb1-133">Cet exemple se trouve dans <`Samples Path>`\Messaging\CBRSample\\.</span><span class="sxs-lookup"><span data-stu-id="5beb1-133">This sample is located at <`Samples Path>`\Messaging\CBRSample\\.</span></span>  
  
 <span data-ttu-id="5beb1-134">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="5beb1-134">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5beb1-135">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="5beb1-135">File(s)</span></span>|<span data-ttu-id="5beb1-136"> Description</span><span class="sxs-lookup"><span data-stu-id="5beb1-136">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5beb1-137">CBRDataCAN.Xml, CBRDataUS.Xml</span><span class="sxs-lookup"><span data-stu-id="5beb1-137">CBRDataCAN.Xml, CBRDataUS.Xml</span></span>|<span data-ttu-id="5beb1-138">Exemples de fichiers d'entrée conformes au schéma défini dans le fichier CBRInputSchema.xsd.</span><span class="sxs-lookup"><span data-stu-id="5beb1-138">Sample input files that conform to the schema defined in the file CBRInputSchema.xsd.</span></span>|  
|<span data-ttu-id="5beb1-139">CBRInput2CANMap.btm, CBRInput2USMap.btm</span><span class="sxs-lookup"><span data-stu-id="5beb1-139">CBRInput2CANMap.btm, CBRInput2USMap.btm</span></span>|<span data-ttu-id="5beb1-140">Fichiers de mappage pour les transformations de format canadien et américain, respectivement.</span><span class="sxs-lookup"><span data-stu-id="5beb1-140">Map files for the Canadian and U.S. format transformations, respectively.</span></span>|  
|<span data-ttu-id="5beb1-141">CBRInputSchema.xsd, CBROutputSchemaCAN.xsd, CBROutputSchemaUS.xsd</span><span class="sxs-lookup"><span data-stu-id="5beb1-141">CBRInputSchema.xsd, CBROutputSchemaCAN.xsd, CBROutputSchemaUS.xsd</span></span>|<span data-ttu-id="5beb1-142">Fichiers de schéma du format d'entrée, du format de sotie canadien et du format de sortie américain, respectivement.</span><span class="sxs-lookup"><span data-stu-id="5beb1-142">Schema files for the input format, the Canadian output format, and the U.S. output format, respectively.</span></span>|  
|<span data-ttu-id="5beb1-143">CBRPromotedPropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="5beb1-143">CBRPromotedPropertySchema.xsd</span></span>|<span data-ttu-id="5beb1-144">Fichier de schéma pour la propriété promue qui correspond à la **CountryCode** élément dans le fichier XML des fichiers d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5beb1-144">Schema file for the promoted property that corresponds to the **CountryCode** element in the XML input files.</span></span>|  
|<span data-ttu-id="5beb1-145">CBRSample.btproj, CBRSample.sln</span><span class="sxs-lookup"><span data-stu-id="5beb1-145">CBRSample.btproj, CBRSample.sln</span></span>|<span data-ttu-id="5beb1-146">Fichiers de projet et de solution BizTalk pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5beb1-146">BizTalk project and solution files for this sample.</span></span>|  
|<span data-ttu-id="5beb1-147">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="5beb1-147">Cleanup.bat</span></span>|<span data-ttu-id="5beb1-148">Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="5beb1-148">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="5beb1-149">Supprime les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="5beb1-149">Removes send and receive ports.</span></span> <span data-ttu-id="5beb1-150">Supprime les répertoires virtuels de Services Internet (IIS) si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5beb1-150">Removes Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="5beb1-151">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="5beb1-151">Setup.bat</span></span>|<span data-ttu-id="5beb1-152">Utilisé pour créer et initialiser cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5beb1-152">Used to build and initialize this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="5beb1-153">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="5beb1-153">How to Use This Sample</span></span>  
 <span data-ttu-id="5beb1-154">Utilisez cet exemple comme exemple de travail des actions requises pour acheminer un message sur la base de son contenu.</span><span class="sxs-lookup"><span data-stu-id="5beb1-154">Use this sample as a working example of the actions required to route a message based on content.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="5beb1-155">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="5beb1-155">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="5beb1-156">Pour créer et initialiser l'exemple CBRSample, vous devez créer et déployer le projet BizTalk pour cet exemple, configurer le port et l'emplacement de réception et configurer deux ports d'envoi différents.</span><span class="sxs-lookup"><span data-stu-id="5beb1-156">To build and initialize the CBRSample sample, you need to build and deploy the BizTalk project for this sample, configure the receive port and location, and configure two different send ports.</span></span>  
  
#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a><span data-ttu-id="5beb1-157">Pour créer et déployer le projet BizTalk pour cet exemple</span><span class="sxs-lookup"><span data-stu-id="5beb1-157">To build and deploy the BizTalk project for this sample</span></span>  
  
1.  <span data-ttu-id="5beb1-158">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="5beb1-158">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="5beb1-159">`<Samples Path>`**\Messaging\CBRSample**</span><span class="sxs-lookup"><span data-stu-id="5beb1-159">`<Samples Path>` **\Messaging\CBRSample**</span></span>  
  
2.  <span data-ttu-id="5beb1-160">Exécutez **Setup.bat**, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5beb1-160">Run **Setup.bat**, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="5beb1-161">Crée l’entrée (**dans**) et les dossiers de sortie (**américain** et **pouvez**) pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5beb1-161">Creates the input (**In**) and output folders (**US** and **CAN**) for this sample.</span></span>  
  
    -   <span data-ttu-id="5beb1-162">Compilation et déploiement du projet Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] utilisé dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="5beb1-162">Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="5beb1-163">crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :</span><span class="sxs-lookup"><span data-stu-id="5beb1-163">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5beb1-164">Cet exemple affiche l’avertissement suivant lors de la création et la liaison des ports :</span><span class="sxs-lookup"><span data-stu-id="5beb1-164">This sample displays the following warning when creating and binding the ports:</span></span>  
    >   
    >  <span data-ttu-id="5beb1-165">**Avertissement : Réception non spécifié pour le Gestionnaire de réception « CBRReceiveLocation » ; mise à jour avec le premier gestionnaire de réception avec type de transport correspondant.**</span><span class="sxs-lookup"><span data-stu-id="5beb1-165">**Warning: Receive handler not specified for receive location "CBRReceiveLocation"; updating with first receive handler with matching transport type.**</span></span>  
    >   
    >  <span data-ttu-id="5beb1-166">Vous pouvez ignorer cet avertissement sans problème.</span><span class="sxs-lookup"><span data-stu-id="5beb1-166">You can safely ignore this warning.</span></span> <span data-ttu-id="5beb1-167">(Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)</span><span class="sxs-lookup"><span data-stu-id="5beb1-167">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5beb1-168">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5beb1-168">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5beb1-169">Si vous décidez d'ouvrir et de créer le projet de cet exemple sans exécuter Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="5beb1-169">If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="5beb1-170">Utilisez cette paire de clés pour signer l'assembly obtenu.</span><span class="sxs-lookup"><span data-stu-id="5beb1-170">Use this key pair to sign the resulting assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5beb1-171">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="5beb1-171">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="5beb1-172">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="5beb1-172">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
#### <a name="to-prepare-to-configure-the-receive-port-and-location-and-the-send-ports"></a><span data-ttu-id="5beb1-173">Pour préparer la configuration du port et de l'emplacement de réception et des ports d'envoi</span><span class="sxs-lookup"><span data-stu-id="5beb1-173">To prepare to configure the receive port and location, and the send ports</span></span>  
  
1.  <span data-ttu-id="5beb1-174">Dans **Microsoft SQL Management Studio**, sélectionnez la base de données de gestion BizTalk correcte.</span><span class="sxs-lookup"><span data-stu-id="5beb1-174">In **Microsoft SQL Management Studio**, select the correct BizTalk Management database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5beb1-175">La base de données de gestion BizTalk est également appelée « base de données de configuration BizTalk ».</span><span class="sxs-lookup"><span data-stu-id="5beb1-175">The BizTalk Management database is also referred to as the BizTalk Configuration database.</span></span>  
  
#### <a name="to-configure-enlist-and-start-the-us-send-port"></a><span data-ttu-id="5beb1-176">Pour configurer, inscrire et démarrer le port d'envoi américain</span><span class="sxs-lookup"><span data-stu-id="5beb1-176">To configure, enlist, and start the U.S. send port</span></span>  
  
1.  <span data-ttu-id="5beb1-177">Dans la console Administration de BizTalk Server, développez **Ports d’envoi**, avec le bouton droit **CBRUSSendPort**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="5beb1-177">In the BizTalk Server Administration console, expand **Send Ports**, right-click **CBRUSSendPort**, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="5beb1-178">Dans le **statique propriétés du Port d’envoi unidirectionnel** boîte de dialogue, dans l’arborescence des dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Filtres**, puis ajoutez une nouvelle ligne en définissant **propriété** à **CBRSample.CountryCode**, laissant le **opérateur** colonne définie sur  **==** et en définissant le **valeur** colonne **100**.</span><span class="sxs-lookup"><span data-stu-id="5beb1-178">In the **Static One-Way Send Port Properties** dialog box, in the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Filters**, and then add a new row by setting **Property** to **CBRSample.CountryCode**, leaving the **Operator** column set to **==**, and setting the **Value** column to **100**.</span></span>  
  
3.  <span data-ttu-id="5beb1-179">Dans l’arborescence de dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Mappages sortants**, définissez le **mappage à appliquer** propriété **CBRSample.CBRInput2USMap**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5beb1-179">In the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Outbound Maps**, set the **Map to apply** property to **CBRSample.CBRInput2USMap**, and then click **OK**.</span></span> <span data-ttu-id="5beb1-180">Vous devrez peut-être cliquer sur le bouton de défilement pour afficher le mappage.</span><span class="sxs-lookup"><span data-stu-id="5beb1-180">You may have to click the scroll button to bring the map into view.</span></span>  
  
#### <a name="to-configure-enlist-and-start-the-canadian-send-port"></a><span data-ttu-id="5beb1-181">Pour configurer, inscrire et démarrer le port d'envoi canadien</span><span class="sxs-lookup"><span data-stu-id="5beb1-181">To configure, enlist, and start the Canadian send port</span></span>  
  
1.  <span data-ttu-id="5beb1-182">Dans la console Administration de BizTalk Server, développez **Ports d’envoi**, avec le bouton droit **CBRCANSendPort**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="5beb1-182">In the BizTalk Server Administration console, expand **Send Ports**, right-click **CBRCANSendPort**, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="5beb1-183">Dans le **statique propriétés du Port d’envoi unidirectionnel** boîte de dialogue, dans l’arborescence des dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Filtres**, puis ajoutez une nouvelle ligne en définissant **propriété** à **CBRSample.CountryCode**, laissant le **opérateur** colonne définie sur  **==** et en définissant le **valeur** colonne **200**.</span><span class="sxs-lookup"><span data-stu-id="5beb1-183">In the **Static One-Way Send Port Properties** dialog box, in the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Filters**, and then add a new row by setting **Property** to **CBRSample.CountryCode**, leaving the **Operator** column set to **==**, and setting the **Value** column to **200**.</span></span>  
  
3.  <span data-ttu-id="5beb1-184">Dans l’arborescence de dossiers à gauche de la boîte de dialogue, sélectionnez **filtres & mappage &#124; Mappages sortants**, définissez le **mappage à appliquer** propriété **CBRSample.CBRInput2CANMap**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5beb1-184">In the folder tree to the left of the dialog box, select **Filters & Mapping &#124; Outbound Maps**, set the **Map to apply** property to **CBRSample.CBRInput2CANMap**, and then click **OK**.</span></span>  
  
 <span data-ttu-id="5beb1-185">Ces étapes connectent le port d'envoi au port de réception.</span><span class="sxs-lookup"><span data-stu-id="5beb1-185">These steps connect the send port to the receive port.</span></span> <span data-ttu-id="5beb1-186">L'exemple utilise les propriétés promues pour acheminer les documents.</span><span class="sxs-lookup"><span data-stu-id="5beb1-186">The sample uses promoted properties to route the documents.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5beb1-187"> est maintenant prêt à travailler avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5beb1-187"> is ready now to work with this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="5beb1-188">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="5beb1-188">Running This Sample</span></span>  
 <span data-ttu-id="5beb1-189">La procédure suivante permet d'exécuter l'exemple CBRSample.</span><span class="sxs-lookup"><span data-stu-id="5beb1-189">Use the following procedure to run the CBRSample sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="5beb1-190">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5beb1-190">To run this sample</span></span>  
  
1.  <span data-ttu-id="5beb1-191">Copiez les fichiers d’entrée, **CBRDataCAN.xml** et **CBRDataUS.xml**, dans le dossier d’entrée suivant :</span><span class="sxs-lookup"><span data-stu-id="5beb1-191">Copy the input files, **CBRDataCAN.xml** and **CBRDataUS.xml**, into the following input folder:</span></span>  
  
     <span data-ttu-id="5beb1-192">`<Samples Path>`**\Messaging\CBRSample\In**</span><span class="sxs-lookup"><span data-stu-id="5beb1-192">`<Samples Path>` **\Messaging\CBRSample\In**</span></span>  
  
2.  <span data-ttu-id="5beb1-193">Observez la façon dont chacun de ces fichiers est transformé et acheminé vers une de ces deux sortie dossiers en fonction de la valeur de leur **CountryCode** élément (100 ou 200) :</span><span class="sxs-lookup"><span data-stu-id="5beb1-193">Observe how each of these files is transformed and routed to one of the following two output folders based on the value of their **CountryCode** element (100 versus 200):</span></span>  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5beb1-194">transforme et achemine le fichier d’entrée **CBRDataCAN.xml** dans le dossier :</span><span class="sxs-lookup"><span data-stu-id="5beb1-194"> transforms and routes the input file **CBRDataCAN.xml** to the folder:</span></span>  
  
         <span data-ttu-id="5beb1-195">`<Samples Path>`**\Messaging\CBRSample\CAN**</span><span class="sxs-lookup"><span data-stu-id="5beb1-195">`<Samples Path>` **\Messaging\CBRSample\CAN**</span></span>  
  
    -   <span data-ttu-id="5beb1-196">BizTalk Server transforme et achemine le fichier d’entrée **CBRDataUS.xml** dans le dossier :</span><span class="sxs-lookup"><span data-stu-id="5beb1-196">BizTalk Server transforms and routes the input file **CBRDataUS.xml** to the folder:</span></span>  
  
         <span data-ttu-id="5beb1-197">`<Samples Path>`**\Messaging\CBRSample\US**</span><span class="sxs-lookup"><span data-stu-id="5beb1-197">`<Samples Path>` **\Messaging\CBRSample\US**</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="5beb1-198">Classes ou méthodes utilisées dans l'exemple</span><span class="sxs-lookup"><span data-stu-id="5beb1-198">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="5beb1-199">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5beb1-199">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5beb1-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5beb1-200">See Also</span></span>  
 <span data-ttu-id="5beb1-201">[Pipelines par défaut](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="5beb1-201">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="5beb1-202">[Comment configurer les mappages sortants pour un Port d’envoi](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="5beb1-202">[How to Configure Outbound Maps for a Send Port](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span></span>  
 [<span data-ttu-id="5beb1-203">Messagerie (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="5beb1-203">Messaging (BizTalk Server Samples Folder)</span></span>](../core/messaging-biztalk-server-samples-folder.md)