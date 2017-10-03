---
title: "Le Gestionnaire de propriété XPath arbitraire (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
ms.assetid: 4eb26c38-5ece-42b0-a28e-73214df1dc41
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3ce40931caaf8f247afeacdae48721f31a7d99b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="arbitrary-xpath-property-handler-biztalk-server-sample"></a><span data-ttu-id="e5788-102">Gestionnaire de propriété XPath arbitraire (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="e5788-102">Arbitrary XPath Property Handler (BizTalk Server Sample)</span></span>
<span data-ttu-id="e5788-103">Le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) illustre l'écriture d'un composant de pipeline personnalisé pour promouvoir des propriétés spécifiques sur un document XML envoyé à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5788-103">The Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample) demonstrates how to write a custom pipeline component to promote specific properties on an XML document that is submitted to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e5788-104">Vous pouvez utiliser la fonctionnalité contenue dans l'exemple pour créer des composants Standard, Assembleur et Désassembleur personnalisés pour évaluer des expressions XPath.</span><span class="sxs-lookup"><span data-stu-id="e5788-104">You can use functionality contained in the sample to create custom regular, assembler, and disassembler components to evaluate XPath expressions.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="e5788-105">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="e5788-105">What This Sample Does</span></span>  
 <span data-ttu-id="e5788-106">L'exemple inclut un document XML de bon de commande à traiter, DocInstance.xml.</span><span class="sxs-lookup"><span data-stu-id="e5788-106">The sample includes a purchase order (PO) XML document to process, DocInstance.xml.</span></span> <span data-ttu-id="e5788-107">L'exemple utilise les étapes suivantes pour traiter DocInstance.xml :</span><span class="sxs-lookup"><span data-stu-id="e5788-107">The sample uses the following steps to process DocInstance.xml:</span></span>  
  
1.  <span data-ttu-id="e5788-108">DocInstance.xml est récupéré par un port de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et traité par un composant de pipeline personnalisé nommé gestionnaire de propriété XPath arbitraire.</span><span class="sxs-lookup"><span data-stu-id="e5788-108">DocInstance.xml is retrieved by a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive port and processed by a custom pipeline component called Arbitrary XPath Property Handler.</span></span>  
  
2.  <span data-ttu-id="e5788-109">Le composant Gestionnaire de propriété XPath arbitraire promeut tous \<Price > et \<quantité > éléments avec une expression XPath arbitraire comme défini dans le schéma de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="e5788-109">The arbitrary XPath property handler component promotes all \<Price> and \<Quantity> elements with an arbitrary XPath expression as defined in the PO schema.</span></span> <span data-ttu-id="e5788-110">L'expression XPath contient également la position construct à utiliser avec des éléments enfants ambigus de l'élément racine du document de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="e5788-110">The XPath expression also contains the position construct for use with ambiguous child elements of the PO document root element.</span></span>  
  
3.  <span data-ttu-id="e5788-111">Le composant Gestionnaire de propriété XPath arbitraire détermine le type de message et le promeut dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="e5788-111">The arbitrary XPath property handler component determines the message type and promotes it into the message context.</span></span>  
  
4.  <span data-ttu-id="e5788-112">Ensuite, le composant envoie le document XML avec les éléments promus à une orchestration pour un traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="e5788-112">The component then sends the XML document with the promoted elements to an orchestration for further processing.</span></span>  
  
5.  <span data-ttu-id="e5788-113">L'orchestration accède aux éléments promus dans le document de bon de commande et calcule le nombre total d'articles du bon de commande.</span><span class="sxs-lookup"><span data-stu-id="e5788-113">The orchestration accesses the promoted elements in the PO document and calculates the total number of items in the PO.</span></span>  
  
6.  <span data-ttu-id="e5788-114">L'orchestration crée un document de bon de commande contenant les informations du bon de commande d'origine ainsi que le total mis à jour.</span><span class="sxs-lookup"><span data-stu-id="e5788-114">The orchestration creates a new PO document that contains the information from the original PO as well as the updated total.</span></span>  
  
7.  <span data-ttu-id="e5788-115">Le nouveau document de bon de commande est écrit dans un fichier du répertoire \Output.</span><span class="sxs-lookup"><span data-stu-id="e5788-115">The new PO document is written to a file in the \Output directory.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="e5788-116">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="e5788-116">Where to Find This Sample</span></span>  
 <span data-ttu-id="e5788-117">*\<Exemples de chemin d’accès >*\Pipelines\ArbitraryXPathPropertyHandler</span><span class="sxs-lookup"><span data-stu-id="e5788-117">*\<Samples Path>*\Pipelines\ArbitraryXPathPropertyHandler</span></span>  
  
 <span data-ttu-id="e5788-118">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="e5788-118">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="e5788-119">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="e5788-119">File(s)</span></span>|<span data-ttu-id="e5788-120"> Description</span><span class="sxs-lookup"><span data-stu-id="e5788-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5788-121">ArbitraryXPathPropertyHandler.sln</span><span class="sxs-lookup"><span data-stu-id="e5788-121">ArbitraryXPathPropertyHandler.sln</span></span>|<span data-ttu-id="e5788-122">Fichier de solution du composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e5788-122">Custom pipeline component solution file.</span></span>|  
|<span data-ttu-id="e5788-123">ArbitraryXPathPropertyHandler.resX</span><span class="sxs-lookup"><span data-stu-id="e5788-123">ArbitraryXPathPropertyHandler.resX</span></span>|<span data-ttu-id="e5788-124">Fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="e5788-124">Resource file.</span></span>|  
|<span data-ttu-id="e5788-125">ArbitraryXPathPropertyHandlerComp.cs</span><span class="sxs-lookup"><span data-stu-id="e5788-125">ArbitraryXPathPropertyHandlerComp.cs</span></span>|<span data-ttu-id="e5788-126">Implémentation du composant principal.</span><span class="sxs-lookup"><span data-stu-id="e5788-126">Main component implementation.</span></span>|  
|<span data-ttu-id="e5788-127">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="e5788-127">AssemblyInfo.cs</span></span>|<span data-ttu-id="e5788-128">Informations de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="e5788-128">Assembly information.</span></span>|  
|<span data-ttu-id="e5788-129">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="e5788-129">Cleanup.bat</span></span>|<span data-ttu-id="e5788-130">Exemple de fichier de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="e5788-130">Sample cleanup file.</span></span>|  
|<span data-ttu-id="e5788-131">PromotingMap.cs</span><span class="sxs-lookup"><span data-stu-id="e5788-131">PromotingMap.cs</span></span>|<span data-ttu-id="e5788-132">Promotion de propriétés comme implémentation du mappage des types CLR natifs.</span><span class="sxs-lookup"><span data-stu-id="e5788-132">Property promotion as native CLR types map implementation.</span></span>|  
|<span data-ttu-id="e5788-133">PropertyAttributes.cs</span><span class="sxs-lookup"><span data-stu-id="e5788-133">PropertyAttributes.cs</span></span>|<span data-ttu-id="e5788-134">Attributs personnalisés, descripteur de propriété et implémentation d'ICustomTypePropertyDescriptor.</span><span class="sxs-lookup"><span data-stu-id="e5788-134">Custom attributes, property descriptor, and ICustomTypePropertyDescriptor implementation.</span></span>|  
|<span data-ttu-id="e5788-135">SchemaMap.cs</span><span class="sxs-lookup"><span data-stu-id="e5788-135">SchemaMap.cs</span></span>|<span data-ttu-id="e5788-136">Mappage de schéma à partir du type de message à IDocumentSpec pour résoudre l'ambiguïté de schéma.</span><span class="sxs-lookup"><span data-stu-id="e5788-136">Schema mapping from message type to IDocumentSpec to resolve schema ambiguity.</span></span>|  
|<span data-ttu-id="e5788-137">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="e5788-137">Setup.bat</span></span>|<span data-ttu-id="e5788-138">Création et configuration de l'exemple de composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="e5788-138">Build and setup sample pipeline component.</span></span>|  
|<span data-ttu-id="e5788-139">VirtualStream.cs</span><span class="sxs-lookup"><span data-stu-id="e5788-139">VirtualStream.cs</span></span>|<span data-ttu-id="e5788-140">Implémentation du flux virtuel.</span><span class="sxs-lookup"><span data-stu-id="e5788-140">Virtual stream implementation.</span></span>|  
|<span data-ttu-id="e5788-141">SeekableReadOnlyStream.cs</span><span class="sxs-lookup"><span data-stu-id="e5788-141">SeekableReadOnlyStream.cs</span></span>|<span data-ttu-id="e5788-142">Implémentation du flux en lecture seule et identifiable.</span><span class="sxs-lookup"><span data-stu-id="e5788-142">Seekable read-only stream implementation.</span></span>|  
|<span data-ttu-id="e5788-143">ArbitraryXPathSample.sln</span><span class="sxs-lookup"><span data-stu-id="e5788-143">ArbitraryXPathSample.sln</span></span>|<span data-ttu-id="e5788-144">Exemple de fichier de solution de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="e5788-144">Sample orchestration solution file.</span></span>|  
|<span data-ttu-id="e5788-145">CalculateTotalAmount.odx</span><span class="sxs-lookup"><span data-stu-id="e5788-145">CalculateTotalAmount.odx</span></span>|<span data-ttu-id="e5788-146">Exemple d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="e5788-146">Sample orchestration.</span></span>|  
|<span data-ttu-id="e5788-147">PODocument.xsd</span><span class="sxs-lookup"><span data-stu-id="e5788-147">PODocument.xsd</span></span>|<span data-ttu-id="e5788-148">Schéma de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="e5788-148">Purchase order schema.</span></span>|  
|<span data-ttu-id="e5788-149">DocInstance.xml</span><span class="sxs-lookup"><span data-stu-id="e5788-149">DocInstance.xml</span></span>|<span data-ttu-id="e5788-150">Exemple d'instance de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="e5788-150">Sample purchase order instance.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="e5788-151">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="e5788-151">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="e5788-152">Cet exemple est conçu pour s'exécuter dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] s'exécutant sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e5788-152">This sample is designed to run in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] running on the same machine.</span></span> <span data-ttu-id="e5788-153">Si votre environnement ne correspond pas à cette configuration, vous devez modifier le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) pour qu'il pointe sur l'ordinateur SQL Server correct.</span><span class="sxs-lookup"><span data-stu-id="e5788-153">If your environment does not match this configuration, you must modify the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample) to point to the correct SQL Server computer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5788-154">Setup.bat suppose que votre répertoire d'installation de Microsoft Windows est C:\Windows.</span><span class="sxs-lookup"><span data-stu-id="e5788-154">Setup.bat assumes your Microsoft Windows installation directory is C:\Windows.</span></span> <span data-ttu-id="e5788-155">Si votre installation Windows se trouve dans un autre répertoire, vous devez modifier le fichier ArbitraryXPathPropertyHandler.csproj pour refléter l'emplacement de l'assembly Microsoft.BizTalk.Component.Utilities dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="e5788-155">If your Windows installation is in another directory, you must modify the ArbitraryXPathPropertyHandler.csproj file to reflect the location of the Microsoft.BizTalk.Component.Utilities assembly in the global assembly cache.</span></span> <span data-ttu-id="e5788-156">Dans l’élément de référence, modifiez \<SYSTEMROOT > à l’emplacement où Windows est installé (par exemple, C:\WINNT\\).</span><span class="sxs-lookup"><span data-stu-id="e5788-156">In the Reference element, change \<SYSTEMROOT> to the location where Windows is installed (for example, C:\WINNT\\).</span></span>  
  
```  
<Reference  
  Name = "Microsoft.BizTalk.Component.Utilities"  
  AssemblyName = "Microsoft.BizTalk.Component.Utilities"  
  HintPath = "<SYSTEMROOT>\assembly\GAC\Microsoft.BizTalk.Component.Utilities\3.0.1.0__31bf3856ad364e35\Microsoft.BizTalk.Component.Utilities.dll"  
/>  
```  
  
 <span data-ttu-id="e5788-157">Utilisez la procédure suivante pour créer et initialiser le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="e5788-157">Use the following procedure to build and initialize the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample).</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="e5788-158">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="e5788-158">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="e5788-159">Dans une fenêtre de commande, remplacez les répertoires (**cd**) dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="e5788-159">In a command window, change directories (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="e5788-160">*\<Exemples de chemin d’accès >*\Pipelines\ArbitraryXPathPropertyHandler</span><span class="sxs-lookup"><span data-stu-id="e5788-160">*\<Samples Path>*\Pipelines\ArbitraryXPathPropertyHandler</span></span>  
  
2.  <span data-ttu-id="e5788-161">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5788-161">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="e5788-162">crée le composant de pipeline Gestionnaire de propriété XPath arbitraire ;</span><span class="sxs-lookup"><span data-stu-id="e5788-162">Builds the Arbitrary XPath Property Handler pipeline component.</span></span>  
  
    -   <span data-ttu-id="e5788-163">Composant de pipeline copies générés le  *\<chemin d’Installation >*répertoire \Pipeline Components.</span><span class="sxs-lookup"><span data-stu-id="e5788-163">Copies built pipeline component to the *\<Installation Path>*\Pipeline Components directory.</span></span>  
  
    -   <span data-ttu-id="e5788-164">crée les ports d'envoi et de réception ;</span><span class="sxs-lookup"><span data-stu-id="e5788-164">Creates the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="e5788-165">crée les répertoires d'entrée et de sortie utilisés dans l'exemple ;</span><span class="sxs-lookup"><span data-stu-id="e5788-165">Creates the input and output directories used in the sample.</span></span>  
  
    -   <span data-ttu-id="e5788-166">installe l'exemple d'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ArbitraryXPathSample ;</span><span class="sxs-lookup"><span data-stu-id="e5788-166">Installs the sample [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration ArbitraryXPathSample.</span></span>  
  
    -   <span data-ttu-id="e5788-167">lie les ports à l'exemple d'orchestration ;</span><span class="sxs-lookup"><span data-stu-id="e5788-167">Binds the ports to the sample orchestration.</span></span>  
  
    -   <span data-ttu-id="e5788-168">démarre l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="e5788-168">Starts the orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5788-169">Aucune erreur ne doit être signalée lors de la création et de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="e5788-169">No errors should be reported during the build and initialization.</span></span> <span data-ttu-id="e5788-170">En cas d'erreur, veillez à ce que vous ayez tous les logiciels nécessaires installés et que les outils de création Microsoft sont disponibles dans le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="e5788-170">If any errors occur, make sure that you have all necessary software installed and that Microsoft build tools are available on the path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5788-171">Pour annuler les modifications apportées par Setup.bat, arrêtez puis redémarrez l'instance de l'hôte à partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5788-171">To undo changes made by Setup.bat, you must first stop and restart the host instance from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="e5788-172">Ensuite, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="e5788-172">Next, run Cleanup.bat.</span></span> <span data-ttu-id="e5788-173">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="e5788-173">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="e5788-174">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="e5788-174">Running This Sample</span></span>  
 <span data-ttu-id="e5788-175">La procédure suivante permet d'exécuter le gestionnaire de propriété XPath arbitraire (exemple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="e5788-175">Use the following procedure to run the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample).</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="e5788-176">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="e5788-176">To run this sample</span></span>  
  
1.  <span data-ttu-id="e5788-177">Copiez le fichier de bon de commande DocInstance.xml dans le répertoire \Input.</span><span class="sxs-lookup"><span data-stu-id="e5788-177">Copy the purchase order (PO) file DocInstance.xml to the \Input directory.</span></span> <span data-ttu-id="e5788-178">Le fichier de bon de commande est récupéré par un port de réception qui envoie les données XML au composant de pipeline Gestionnaire de propriété XPath arbitraire.</span><span class="sxs-lookup"><span data-stu-id="e5788-178">The PO file is picked up by a receive port, which sends the XML data to the Arbitrary XPath Property Handler pipeline component.</span></span>  
  
2.  <span data-ttu-id="e5788-179">Affichez le contenu dans le répertoire \Output.</span><span class="sxs-lookup"><span data-stu-id="e5788-179">View the contents in the \Output directory.</span></span> <span data-ttu-id="e5788-180">Notez la création d'un fichier contenant toutes les informations du fichier DocInstance.xml qui vous avez copié dans le répertoire \Input.</span><span class="sxs-lookup"><span data-stu-id="e5788-180">Notice that a new file is created that contains all the information from the DocInstance.xml file that you copied to the \Input directory.</span></span> <span data-ttu-id="e5788-181">La différence dans le fichier qui est désormais le \<TotalAmount > élément a été rempli avec le montant total pour le bon de commande.</span><span class="sxs-lookup"><span data-stu-id="e5788-181">The difference in the file is that now the \<TotalAmount> element has been populated with the total amount for the PO.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="e5788-182">Commentaires</span><span class="sxs-lookup"><span data-stu-id="e5788-182">Comments</span></span>  
 <span data-ttu-id="e5788-183">Les expressions XPath canoniques sont des expressions simples tels que « / * [local-name () = 'element-name' and namespaceURI() = 'http://MyUri.org'] /\*[local-name () = 'element-name'] / @\*[local-name = 'attribute name'] ».</span><span class="sxs-lookup"><span data-stu-id="e5788-183">Canonical XPath expressions are simple expressions such as "/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/\*[local-name()='element-name']/@\*[local-name='attribute-name']".</span></span>  
  
 <span data-ttu-id="e5788-184">Une expression XPath arbitraire peut être complexe, par exemple « //element-name//*[local-name()='element-name' and position()=2] ».</span><span class="sxs-lookup"><span data-stu-id="e5788-184">An arbitrary XPath expression can be as complex as "//element-name//*[local-name()='element-name' and position()=2]".</span></span> <span data-ttu-id="e5788-185">En fait, vous obtenez une erreur d'exécution indiquant que les expressions XPath non canoniques ne sont pas prises en charge par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] si votre schéma a un XPath non canonique utilisé dans le corps XPath ou une propriété XPath.</span><span class="sxs-lookup"><span data-stu-id="e5788-185">If fact, you will receive a run-time error stating that non-canonical XPath expressions are not supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] if your schema has a non-canonical XPath used in the XPath body or an XPath property.</span></span> <span data-ttu-id="e5788-186">Une solution pour la prise en charge des expressions XPath arbitraires consiste à créer des composants Désassembleur et Assembleur personnalisés prenant en charge un corps XPath arbitraire ainsi que des expressions de propriété XPath arbitraire.</span><span class="sxs-lookup"><span data-stu-id="e5788-186">A solution to support arbitrary XPath expressions is to create custom disassembler and assembler components that support an arbitrary XPath body as well as arbitrary XPath property expressions.</span></span>  
  
 <span data-ttu-id="e5788-187">Cet exemple utilise la séquence d’étapes suivante dans le composant de pipeline personnalisé lorsque **IComponent.Execute** est implémenté :</span><span class="sxs-lookup"><span data-stu-id="e5788-187">This sample uses the following sequence of steps in the custom pipeline component when **IComponent.Execute** is implemented:</span></span>  
  
1.  <span data-ttu-id="e5788-188">Crée un flux virtuel identifiable sur le flux du corps du message entrant.</span><span class="sxs-lookup"><span data-stu-id="e5788-188">Creates a virtual seekable stream over the input message body part stream.</span></span> <span data-ttu-id="e5788-189">(Comme le message entrant peut être volumineux et que le flux peut être non identifiable, il doit avoir un faible encombrement mémoire et être capable de modifier les positions de flux.)</span><span class="sxs-lookup"><span data-stu-id="e5788-189">(Because the input message can be large and the stream can be non-seekable, it should have a small memory footprint and be able to change stream positions.)</span></span>  
  
2.  <span data-ttu-id="e5788-190">Crée un message sortant et un corps, attribue un flux virtuel au nouveau corps, clone les propriétés du corps ainsi que le contexte de message.</span><span class="sxs-lookup"><span data-stu-id="e5788-190">Creates a new outgoing message and a new body part for it, assigns a virtual stream to the new body part, clones body part properties, and clones message context.</span></span>  
  
3.  <span data-ttu-id="e5788-191">Obtient un schéma pour le message entrant ou basé sur les schémas spécifiés au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="e5788-191">Gets a schema for the input message or based on schemas specified during design time.</span></span>  
  
4.  <span data-ttu-id="e5788-192">Charge le flux de données dans une instance de **System.Xml.XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="e5788-192">Loads the stream into an instance of **System.Xml.XmlDocument**.</span></span>  
  
5.  <span data-ttu-id="e5788-193">Passe en revue les propriétés promues et les champs distinctifs et les promeut ou les écrit dans le contexte de message du message sortant.</span><span class="sxs-lookup"><span data-stu-id="e5788-193">Walks through promoted properties and distinguished fields and promotes or writes them to the message context of the outgoing message.</span></span>  
  
6.  <span data-ttu-id="e5788-194">Renvoie le message sortant.</span><span class="sxs-lookup"><span data-stu-id="e5788-194">Returns the outgoing message.</span></span>  
  
7.  <span data-ttu-id="e5788-195">Écrit le message sortant dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="e5788-195">Writes the outgoing message to a file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5788-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5788-196">See Also</span></span>  
 [<span data-ttu-id="e5788-197">Pipelines (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="e5788-197">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)