---
title: "Procédure pas à pas : Utilisation d’enveloppes XML (Basic) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content-based routing, promoting properties
- promoting properties, routing messages
- promoting properties, content-based routing
- routing, messages
- routing, promoting properties
ms.assetid: 02d0c596-0cfe-4bae-9f1b-d7dbc17e18a9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9090c4ee7d576bb7ab610cd81637680d837b2cae
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-using-xml-envelopes-basic"></a><span data-ttu-id="f78dc-102">Procédure pas à pas : Utilisation d’enveloppes XML (Basic)</span><span class="sxs-lookup"><span data-stu-id="f78dc-102">Walkthrough: Using XML Envelopes (Basic)</span></span>
<span data-ttu-id="f78dc-103">Cet exemple illustre le désassemblage de base d'enveloppes XML par l'implémentation en partie d'un système de suivi des erreurs fictif.</span><span class="sxs-lookup"><span data-stu-id="f78dc-103">This example demonstrates basic XML envelope disassembly by implementing part of a fictitious error-tracking system.</span></span> <span data-ttu-id="f78dc-104">Cet exemple remplit les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f78dc-104">The example meets the following requirements:</span></span>  
  
1.  <span data-ttu-id="f78dc-105">les messages d'erreur sont consignés dans divers sites physiques de l'entreprise, puis envoyés vers un emplacement central pour être traités par différents systèmes principaux ;</span><span class="sxs-lookup"><span data-stu-id="f78dc-105">Error messages are logged at various physical sites within the company and sent to a central location for processing into various back-end systems.</span></span>  
  
2.  <span data-ttu-id="f78dc-106">Les messages d'erreur sont écrits au format XML.</span><span class="sxs-lookup"><span data-stu-id="f78dc-106">Error messages are written in XML format.</span></span>  
  
3.  <span data-ttu-id="f78dc-107">Un message d'erreur peut être envoyé seul sans enveloppe ou en tant que lot contenu dans une enveloppe.</span><span class="sxs-lookup"><span data-stu-id="f78dc-107">An error message can be sent singly without an envelope or as a batch contained within an envelope.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f78dc-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f78dc-108">Prerequisites</span></span>  
 <span data-ttu-id="f78dc-109">Pour cet exemple, que vous devez être familiarisé avec la création de projets BizTalk, signature d’un assembly et pour afficher les applications et les ports à l’aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f78dc-109">For this example you need to be comfortable with creating BizTalk projects, signing an assembly, and using the BizTalk Server Administration console to view applications and ports.</span></span> <span data-ttu-id="f78dc-110">Vous devez également être familiarisé avec les concepts présentés dans [procédure pas à pas : déploiement d’une Application BizTalk base](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="f78dc-110">You should also be comfortable with the ideas presented in [Walkthrough: Deploying a Basic BizTalk Application](../core/walkthrough-deploying-a-basic-biztalk-application.md).</span></span>  
  
## <a name="what-this-example-does"></a><span data-ttu-id="f78dc-111">Ce que fait cet exemple</span><span class="sxs-lookup"><span data-stu-id="f78dc-111">What This Example Does</span></span>  
 <span data-ttu-id="f78dc-112">Cet exemple traite les messages entrants contenant soit un seul message d'erreur, soit un lot de messages d'erreur par la définition d'un schéma d'enveloppe et l'utilisation du pipeline XmlDisassembler.</span><span class="sxs-lookup"><span data-stu-id="f78dc-112">The example processes inbound messages containing either a single error message or a batch of error messages by defining an envelope schema and using the XmlDisassembler pipeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f78dc-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="f78dc-113">Example</span></span>  
 <span data-ttu-id="f78dc-114">Pour créer l'exemple, suivez les étapes présentées dans les sections ci-après.</span><span class="sxs-lookup"><span data-stu-id="f78dc-114">To create the example, follow the steps outlined in the following sections.</span></span>  
  
### <a name="create-a-new-biztalk-project"></a><span data-ttu-id="f78dc-115">Créez un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="f78dc-115">Create a New BizTalk Project</span></span>  
 <span data-ttu-id="f78dc-116">Avant de concevoir une solution, vous devez créer un projet BizTalk, vous assurer qu'il porte un nom fort, puis lui attribuer un nom d'application.</span><span class="sxs-lookup"><span data-stu-id="f78dc-116">Before building a solution you need to create a BizTalk project, ensure that it is strongly named, and assign it an application name.</span></span> <span data-ttu-id="f78dc-117">Attribuer un nom d'application empêche BizTalk Server de déployer la solution dans l'application BizTalk par défaut.</span><span class="sxs-lookup"><span data-stu-id="f78dc-117">Assigning an application name prevents BizTalk Server from deploying the solution into the default BizTalk application.</span></span>  
  
##### <a name="to-create-and-configure-a-new-biztalk-project"></a><span data-ttu-id="f78dc-118">Pour créer et configurer un projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="f78dc-118">To create and configure a new BizTalk project</span></span>  
  
1.  <span data-ttu-id="f78dc-119">Créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f78dc-119">Use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to create a new BizTalk project.</span></span> <span data-ttu-id="f78dc-120">Appelez le projet **BasicXMLEnvelope**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-120">Call the project **BasicXMLEnvelope**.</span></span>  
  
2.  <span data-ttu-id="f78dc-121">Générez un fichier de clé et attribuez-le au projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-121">Generate a key file and assign it to the project.</span></span> <span data-ttu-id="f78dc-122">Pour plus d’informations, consultez [comment configurer un fichier de clé de Assembly de nom fort](../core/how-to-configure-a-strong-name-assembly-key-file.md).</span><span class="sxs-lookup"><span data-stu-id="f78dc-122">For more information about this task, see [How to Configure a Strong Name Assembly Key File](../core/how-to-configure-a-strong-name-assembly-key-file.md).</span></span>  
  
3.  <span data-ttu-id="f78dc-123">Dans les propriétés de configuration de déploiement pour le projet, vous devez affecter un **nom de l’Application** et **redémarrer les Instances d’hôte** à `True`.</span><span class="sxs-lookup"><span data-stu-id="f78dc-123">In the deployment configuration properties for the project, assign an **Application Name** and set **Restart Host Instances** to `True`.</span></span> <span data-ttu-id="f78dc-124">La définition de cet indicateur indique à l'hôte d'effacer toutes les instances mises en cache de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="f78dc-124">Setting this flag tells the host to clear any cached instances of the assembly.</span></span>  
  
### <a name="create-the-error-schema"></a><span data-ttu-id="f78dc-125">Créer le schéma d’erreur</span><span class="sxs-lookup"><span data-stu-id="f78dc-125">Create the Error Schema</span></span>  
 <span data-ttu-id="f78dc-126">Cette étape permet de créer le schéma d'erreur.</span><span class="sxs-lookup"><span data-stu-id="f78dc-126">In this step you create the Error schema.</span></span> <span data-ttu-id="f78dc-127">Il définit le message clé du système.</span><span class="sxs-lookup"><span data-stu-id="f78dc-127">It defines the key message for the system.</span></span>  
  
##### <a name="to-create-the-error-schema"></a><span data-ttu-id="f78dc-128">Pour créer le schéma d'erreur</span><span class="sxs-lookup"><span data-stu-id="f78dc-128">To create the Error schema</span></span>  
  
1.  <span data-ttu-id="f78dc-129">Ajoutez un nouveau schéma intitulé « Error » au projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-129">Add a new schema named "Error" to the project.</span></span>  
  
2.  <span data-ttu-id="f78dc-130">Modifier l’espace de noms cible du schéma à **http://BasicXMLEnvelope**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-130">Change the target namespace for the schema to **http://BasicXMLEnvelope**.</span></span>  
  
3.  <span data-ttu-id="f78dc-131">Modifier la propriété de schéma **Element FormDefault** sous le **avancé** catégorie **Qualified**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-131">Change the schema property **Element FormDefault** under the **Advanced** category to **Qualified**.</span></span> <span data-ttu-id="f78dc-132">Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.</span><span class="sxs-lookup"><span data-stu-id="f78dc-132">This indicates that locally declared elements must be qualified by the target namespace in an instance document.</span></span>  
  
4.  <span data-ttu-id="f78dc-133">Renommez le nœud racine « Error » et créez cinq éléments enfants avec les types indiqués :</span><span class="sxs-lookup"><span data-stu-id="f78dc-133">Rename the root node "Error" and create five child elements with the types indicated:</span></span>  
  
    -   <span data-ttu-id="f78dc-134">ID, xs:int</span><span class="sxs-lookup"><span data-stu-id="f78dc-134">ID, xs:int</span></span>  
  
    -   <span data-ttu-id="f78dc-135">Type, xs:int</span><span class="sxs-lookup"><span data-stu-id="f78dc-135">Type, xs:int</span></span>  
  
    -   <span data-ttu-id="f78dc-136">Priority, xs:string</span><span class="sxs-lookup"><span data-stu-id="f78dc-136">Priority, xs:string</span></span>  
  
    -   <span data-ttu-id="f78dc-137">Description, xs:string</span><span class="sxs-lookup"><span data-stu-id="f78dc-137">Description, xs:string</span></span>  
  
    -   <span data-ttu-id="f78dc-138">ErrorDateTime, xs:string</span><span class="sxs-lookup"><span data-stu-id="f78dc-138">ErrorDateTime, xs:string</span></span>  
  
     <span data-ttu-id="f78dc-139">Votre schéma doit présenter l'aspect suivant :</span><span class="sxs-lookup"><span data-stu-id="f78dc-139">Your schema should look like the following:</span></span>  
  
     <span data-ttu-id="f78dc-140">![Schéma d’erreur terminé](../core/media/error-schema.gif "error_schema")</span><span class="sxs-lookup"><span data-stu-id="f78dc-140">![Completed Error schema](../core/media/error-schema.gif "error_schema")</span></span>  
  
5.  <span data-ttu-id="f78dc-141">Créez un exemple de message pour ce schéma.</span><span class="sxs-lookup"><span data-stu-id="f78dc-141">Create a sample message for this schema.</span></span> <span data-ttu-id="f78dc-142">Vous pouvez ainsi vérifier que les messages seuls hors enveloppe sont correctement traités.</span><span class="sxs-lookup"><span data-stu-id="f78dc-142">This is used to verify that single messages outside of an envelope are processed properly.</span></span> <span data-ttu-id="f78dc-143">Voici un exemple de message :</span><span class="sxs-lookup"><span data-stu-id="f78dc-143">An example sample message is:</span></span>  
  
    ```  
    <Error xmlns="http://BasicXMLEnvelope">  
      <ID>1</ID>  
      <Type>5</Type>  
      <Priority>Low</Priority>  
      <Description>Sprocket widget prints reports slowly.</Description>  
      <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
    </Error>  
    ```  
  
     <span data-ttu-id="f78dc-144">Enregistrez ce message dans un fichier du répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-144">Save this message in a file in the project directory.</span></span>  
  
### <a name="create-the-envelope-schema"></a><span data-ttu-id="f78dc-145">Création du schéma d'enveloppe</span><span class="sxs-lookup"><span data-stu-id="f78dc-145">Create the Envelope Schema</span></span>  
 <span data-ttu-id="f78dc-146">L'enveloppe contient un ou plusieurs messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="f78dc-146">The envelope contains one or more error messages.</span></span> <span data-ttu-id="f78dc-147">Dans cet exemple simple, l'enveloppe ne dispose pas de ses propres propriétés et éléments.</span><span class="sxs-lookup"><span data-stu-id="f78dc-147">In this basic example, the envelope does not have properties and elements of its own.</span></span>  
  
##### <a name="to-create-the-envelope-schema"></a><span data-ttu-id="f78dc-148">Pour créer le schéma d'enveloppe</span><span class="sxs-lookup"><span data-stu-id="f78dc-148">To create the envelope schema</span></span>  
  
1.  <span data-ttu-id="f78dc-149">Ajoutez un nouveau schéma intitulé « Envelope » au projet BasicXMLEnvelope.</span><span class="sxs-lookup"><span data-stu-id="f78dc-149">Add a new schema named "Envelope" to the BasicXMLEnvelope project.</span></span>  
  
2.  <span data-ttu-id="f78dc-150">Modifier l’espace de noms cible **http://BasicXMLEnvelope**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-150">Change the target namespace to **http://BasicXMLEnvelope**.</span></span>  
  
3.  <span data-ttu-id="f78dc-151">Modifiez le nom du nœud racine de « Root » en « Envelope ».</span><span class="sxs-lookup"><span data-stu-id="f78dc-151">Change the name of the root node from "Root" to "Envelope".</span></span>  
  
4.  <span data-ttu-id="f78dc-152">Marquez le schéma en tant que schéma d'enveloppe.</span><span class="sxs-lookup"><span data-stu-id="f78dc-152">Now mark the schema as an envelope schema.</span></span> <span data-ttu-id="f78dc-153">Cliquez sur le  **\<schéma\>**  nœud.</span><span class="sxs-lookup"><span data-stu-id="f78dc-153">Click the **\<Schema\>** node.</span></span> <span data-ttu-id="f78dc-154">Dans le volet Propriétés, définissez la propriété de référence du schéma **enveloppe** à `OK`.</span><span class="sxs-lookup"><span data-stu-id="f78dc-154">In the Properties pane, set the schema reference property **Envelope** to `OK`.</span></span>  
  
5.  <span data-ttu-id="f78dc-155">Définir le **XPath de corps** propriété.</span><span class="sxs-lookup"><span data-stu-id="f78dc-155">Set the **Body XPath** property.</span></span> <span data-ttu-id="f78dc-156">Pour ce faire, cliquez sur le **enveloppe** nœud.</span><span class="sxs-lookup"><span data-stu-id="f78dc-156">To do this, click the **Envelope** node.</span></span> <span data-ttu-id="f78dc-157">Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) situé dans le **XPath de corps** propriété, sélectionnez **enveloppe**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-157">In the Properties window, click the ellipsis (**...**) button in the **Body XPath** property, select **Envelope**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="f78dc-158">Ajoutez tout élément enfant au nœud Envelope.</span><span class="sxs-lookup"><span data-stu-id="f78dc-158">Add an Any element child to the Envelope node.</span></span> <span data-ttu-id="f78dc-159">Le message d'erreur sera contenu dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="f78dc-159">The error message will be contained in this element.</span></span> <span data-ttu-id="f78dc-160">Votre schéma doit présenter l'aspect suivant :</span><span class="sxs-lookup"><span data-stu-id="f78dc-160">Your schema should look like the following:</span></span>  
  
     <span data-ttu-id="f78dc-161">![Schéma d’enveloppe terminé](../core/media/envelope-schema.gif "envelope_schema")</span><span class="sxs-lookup"><span data-stu-id="f78dc-161">![Completed envelope schema](../core/media/envelope-schema.gif "envelope_schema")</span></span>  
  
7.  <span data-ttu-id="f78dc-162">Créez un exemple de message contenant une enveloppe et un ou plusieurs exemples de message.</span><span class="sxs-lookup"><span data-stu-id="f78dc-162">Create a sample message containing an envelope and one or more sample messages.</span></span> <span data-ttu-id="f78dc-163">Un exemple de message est :</span><span class="sxs-lookup"><span data-stu-id="f78dc-163">An example message is:</span></span>  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error>  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
     <span data-ttu-id="f78dc-164">Enregistrez ce message dans un fichier du répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-164">Save this message in a file in the project directory.</span></span>  
  
### <a name="deploy-and-configure-the-send-and-receive-ports"></a><span data-ttu-id="f78dc-165">Déploiement et configuration des ports de réception et d'envoi</span><span class="sxs-lookup"><span data-stu-id="f78dc-165">Deploy and Configure the Send and Receive Ports</span></span>  
 <span data-ttu-id="f78dc-166">Une fois les schémas créés, vous devez compiler et déployer le projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-166">With the schemas created, you need to compile and deploy the project.</span></span> <span data-ttu-id="f78dc-167">Lorsque le projet est déployé, vous pouvez utiliser la console Administration de BizTalk Server pour configurer les ports d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="f78dc-167">After it is deployed, you can use the BizTalk Server Administration console to configure the send and receive ports.</span></span>  
  
##### <a name="to-deploy-basicxmlenvelope"></a><span data-ttu-id="f78dc-168">Pour déployer BasicXMLEnvelope</span><span class="sxs-lookup"><span data-stu-id="f78dc-168">To deploy BasicXMLEnvelope</span></span>  
  
1.  <span data-ttu-id="f78dc-169">À partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], choisissez **déployer BasicXMLEnvelope** dans le menu Générer.</span><span class="sxs-lookup"><span data-stu-id="f78dc-169">From [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], choose **Deploy BasicXMLEnvelope** from the Build menu.</span></span> <span data-ttu-id="f78dc-170">Il sera généré et déployé sur BizTalk Server en tant qu'application « BasicXMLEnvelope ».</span><span class="sxs-lookup"><span data-stu-id="f78dc-170">This will build and deploy it to BizTalk Server as the application "BasicXMLEnvelope".</span></span>  
  
2.  <span data-ttu-id="f78dc-171">Dans la console Administration de BizTalk Server, développez le **Applications** groupe pour vérifier que **BasicXMLEnvelope** est présent sous la forme d’une application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f78dc-171">In the BizTalk Server Administration console, expand the **Applications** group to verify that **BasicXMLEnvelope** is present as a custom application.</span></span>  
  
##### <a name="to-configure-the-receive-port"></a><span data-ttu-id="f78dc-172">Pour configurer le port de réception</span><span class="sxs-lookup"><span data-stu-id="f78dc-172">To configure the receive port</span></span>  
  
1.  <span data-ttu-id="f78dc-173">Utilisez l’Explorateur Windows pour créer un répertoire nommé « Receive » sous le **BasicXMLEnvelope** répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-173">Use Windows Explorer to create a directory named "Receive" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="f78dc-174">Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-174">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="f78dc-175">Dans le **propriétés du Port de réception** boîte de dialogue, définissez le nom du port sur « Réception ».</span><span class="sxs-lookup"><span data-stu-id="f78dc-175">In the **Receive Port Properties** dialog box, set the name of the port to "Receive".</span></span>  
  
4.  <span data-ttu-id="f78dc-176">Cliquez sur les emplacements de réception, puis cliquez sur **nouveau** pour ajouter un port de réception.</span><span class="sxs-lookup"><span data-stu-id="f78dc-176">Right-click Receive Locations, and then click **New** to add a receive port.</span></span> <span data-ttu-id="f78dc-177">Nommez le nouveau port « ReceiveError ».</span><span class="sxs-lookup"><span data-stu-id="f78dc-177">Name the new port "ReceiveError".</span></span> <span data-ttu-id="f78dc-178">Définir le **Pipeline de réception** à **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-178">Set the **Receive Pipeline** to **XMLReceive**.</span></span> <span data-ttu-id="f78dc-179">Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-179">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f78dc-180">Sélectionnez le répertoire de réception créé précédemment et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-180">Select the receive directory created above and click **OK**.</span></span> <span data-ttu-id="f78dc-181">Votre port de réception devrait à présent être configuré.</span><span class="sxs-lookup"><span data-stu-id="f78dc-181">Your receive port should now be configured.</span></span> <span data-ttu-id="f78dc-182">Cliquez sur **OK** à fermer.</span><span class="sxs-lookup"><span data-stu-id="f78dc-182">Click **OK** to close.</span></span>  
  
##### <a name="to-configure-the-send-port"></a><span data-ttu-id="f78dc-183">Pour configurer le port d'envoi</span><span class="sxs-lookup"><span data-stu-id="f78dc-183">To configure the send port</span></span>  
  
1.  <span data-ttu-id="f78dc-184">Utilisez l’Explorateur Windows pour créer un répertoire nommé « Send » sous le **BasicXMLEnvelope** répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-184">Use Windows Explorer to create a directory named "Send" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="f78dc-185">Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-185">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way**.</span></span>  
  
3.  <span data-ttu-id="f78dc-186">Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « Send ».</span><span class="sxs-lookup"><span data-stu-id="f78dc-186">In the **Send Port Properties** dialog box, set the name of the port to "Send".</span></span>  
  
4.  <span data-ttu-id="f78dc-187">Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-187">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="f78dc-188">Définissez le dossier de destination sur le répertoire d’envoi que vous avez créé précédemment et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-188">Set the destination folder to the send directory you created earlier and click **OK**.</span></span>  
  
5.  <span data-ttu-id="f78dc-189">Cliquez sur **filtres** et ajouter un filtre :</span><span class="sxs-lookup"><span data-stu-id="f78dc-189">Click **Filters** and add a single filter:</span></span>  
  
    -   <span data-ttu-id="f78dc-190">BIZTALK SERVER. MessageType == **http://BasicXMLEnvelope#Error**</span><span class="sxs-lookup"><span data-stu-id="f78dc-190">BTS.MessageType == **http://BasicXMLEnvelope#Error**</span></span>  
  
6.  <span data-ttu-id="f78dc-191">Cliquez sur **OK** pour terminer la configuration de port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="f78dc-191">Click **OK** to complete the send port configuration.</span></span> <span data-ttu-id="f78dc-192">Votre port d'envoi devrait à présent être configuré.</span><span class="sxs-lookup"><span data-stu-id="f78dc-192">Your send port should be configured.</span></span>  
  
### <a name="run-the-example"></a><span data-ttu-id="f78dc-193">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f78dc-193">Run the Example</span></span>  
 <span data-ttu-id="f78dc-194">Il est maintenant temps d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="f78dc-194">It is now time to run the example.</span></span> <span data-ttu-id="f78dc-195">Après avoir utilisé la console Administration de BizTalk Server pour lancer l'application BasicXMLEnvelope, copiez les fichiers de test dans l'emplacement de réception et observez le résultat produit dans l'emplacement d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f78dc-195">After using the BizTalk Server Management console to start the BasicXMLEnvelope application, you will copy the test files to the receive location and observe what is produced in the send location.</span></span>  
  
##### <a name="to-run-the-basicxmlenvelope-example"></a><span data-ttu-id="f78dc-196">Pour exécuter l'exemple BasicXMLEnvelope</span><span class="sxs-lookup"><span data-stu-id="f78dc-196">To run the BasicXMLEnvelope example</span></span>  
  
1.  <span data-ttu-id="f78dc-197">Dans la console Administration de BizTalk Server, cliquez sur le **BasicXMLEnvelope** application, puis sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-197">In the BizTalk Server Administration console, right-click the **BasicXMLEnvelope** application and then click **Start**.</span></span> <span data-ttu-id="f78dc-198">Ceci inscrit et démarre les ports d'envoi et de réception</span><span class="sxs-lookup"><span data-stu-id="f78dc-198">This will enlist and start the send and receive ports.</span></span>  
  
2.  <span data-ttu-id="f78dc-199">Faites glisser le fichier exemple dans le répertoire de réception.</span><span class="sxs-lookup"><span data-stu-id="f78dc-199">Drop each of the sample files into the receive directory.</span></span> <span data-ttu-id="f78dc-200">Si vous utilisez les exemples fournis plus haut, vous devez trouver trois messages d'erreur distincts dans l'emplacement d'envoi lorsque le traitement est terminé.</span><span class="sxs-lookup"><span data-stu-id="f78dc-200">If you use the samples given earlier, you should find three individual error messages in the send location when processing is completed.</span></span>  
  
## <a name="extending-the-example"></a><span data-ttu-id="f78dc-201">Extension de l'exemple</span><span class="sxs-lookup"><span data-stu-id="f78dc-201">Extending the Example</span></span>  
 <span data-ttu-id="f78dc-202">Vous pouvez étendre l'exemple afin qu'il réponde à d'autres exigences.</span><span class="sxs-lookup"><span data-stu-id="f78dc-202">You can extend the example to accommodate other requirements.</span></span> <span data-ttu-id="f78dc-203">Cette section traite deux scénarios communs :</span><span class="sxs-lookup"><span data-stu-id="f78dc-203">This section addresses two common scenarios:</span></span>  
  
-   <span data-ttu-id="f78dc-204">Si un lot d'erreurs est envoyé dans une enveloppe, les échecs de messages individuels dans le désassemblage ne doivent pas empêcher le traitement des messages qui ne rencontrent pas d'échec.</span><span class="sxs-lookup"><span data-stu-id="f78dc-204">If a batch of errors is submitted within an envelope, individual message failures in disassembly should not prohibit other nonfailing messages from being further processed.</span></span>  
  
-   <span data-ttu-id="f78dc-205">Les erreurs doivent être remises à différents emplacements en fonction de leur priorité.</span><span class="sxs-lookup"><span data-stu-id="f78dc-205">Errors should be delivered to different locations based on error priority.</span></span> <span data-ttu-id="f78dc-206">Les messages dont la priorité est élevée sont expédiés tandis que les autres priorités sont traités via les canaux normaux.</span><span class="sxs-lookup"><span data-stu-id="f78dc-206">High-priority messages are expedited while other priorities are handled through normal channels.</span></span>  
  
 <span data-ttu-id="f78dc-207">Les sections suivantes étendent l'exemple pour gérer ces cas.</span><span class="sxs-lookup"><span data-stu-id="f78dc-207">The following sections extend the example to handle these requirements.</span></span>  
  
### <a name="recoverable-interchange-processing"></a><span data-ttu-id="f78dc-208">Traitement des échanges récupérables</span><span class="sxs-lookup"><span data-stu-id="f78dc-208">Recoverable Interchange Processing</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f78dc-209"> prend en charge le traitement des échanges récupérables.</span><span class="sxs-lookup"><span data-stu-id="f78dc-209"> supports recoverable interchange processing.</span></span> <span data-ttu-id="f78dc-210">Grâce à cette fonction, vous pouvez vous assurer que les lots de messages échouent de manière individuelle dans le désassemblage, et non en tant que lot.</span><span class="sxs-lookup"><span data-stu-id="f78dc-210">By using this feature, you can ensure that batches of messages fail individually in disassembly and not as a batch.</span></span>  
  
##### <a name="to-configure-the-example-for-recoverable-interchange-processing"></a><span data-ttu-id="f78dc-211">Pour configurer l'exemple pour le traitement des échanges récupérables</span><span class="sxs-lookup"><span data-stu-id="f78dc-211">To configure the example for recoverable interchange processing</span></span>  
  
1.  <span data-ttu-id="f78dc-212">Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, cliquez sur **Ports de réception**, puis double-cliquez sur le port de réception.</span><span class="sxs-lookup"><span data-stu-id="f78dc-212">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, click **Receive Ports**, and then double-click the Receive port.</span></span> <span data-ttu-id="f78dc-213">Il s'agit du port que vous avez précédemment créé.</span><span class="sxs-lookup"><span data-stu-id="f78dc-213">This is the port you created previously.</span></span>  
  
2.  <span data-ttu-id="f78dc-214">Dans le **propriétés du Port de réception** boîte de dialogue, cliquez sur **emplacements de réception**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-214">In the **Receive Port Properties** dialog box, click **Receive Locations**.</span></span> <span data-ttu-id="f78dc-215">Cliquez sur **propriétés** pour afficher les **propriétés d’emplacement de réception ReceiveError** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f78dc-215">Click **Properties** to bring up the **ReceiveError Receive Location Properties** dialog box.</span></span> <span data-ttu-id="f78dc-216">Cliquez sur le bouton de sélection (**...** ) bouton pour le **Pipeline de réception**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-216">Click the ellipsis (**...**) button for the **Receive Pipeline**.</span></span>  
  
3.  <span data-ttu-id="f78dc-217">Dans le **configurer le Pipeline - XMLReceive** boîte de dialogue, définissez la **traitement des échanges récupérables** propriété `True`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-217">In the **Configure Pipeline - XMLReceive** dialog box, set the **Recoverable Interchange Processing** property to `True`, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="f78dc-218">Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue, puis cliquez sur **OK** pour fermer la **propriétés du Port de réception** boîte de dialogue zone.</span><span class="sxs-lookup"><span data-stu-id="f78dc-218">Click **OK** to close the **Receive Location Properties** dialog box, and then click **OK** to close the **Receive Port Properties** dialog box.</span></span>  
  
##### <a name="to-create-a-sample-file-and-run-the-example"></a><span data-ttu-id="f78dc-219">Pour créer un fichier exemple et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f78dc-219">To create a sample file and run the example</span></span>  
  
1.  <span data-ttu-id="f78dc-220">Pour créer un fichier exemple, faites une copie du fichier d'enveloppe créé dans l'exemple, ajoutez un espace de noms inexistant à l'une des instances Error, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="f78dc-220">To create a sample file, make a copy of the envelope sample file created in the example, add a nonexistent namespace to one of the Error instances, and then save the file:</span></span>  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails to return any sprockets even though some exist</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error xmlns="http://ThisIsAnError">  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
2.  <span data-ttu-id="f78dc-221">Dans la console Administration de BizTalk Server, cliquez sur **Applications** et vérifiez que le **BasicXMLEnvelope** application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f78dc-221">In the BizTalk Server Administration console, click **Applications** and verify that the **BasicXMLEnvelope** application is running.</span></span>  
  
3.  <span data-ttu-id="f78dc-222">Déposez le message dans l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f78dc-222">Drop the message in the receive location.</span></span> <span data-ttu-id="f78dc-223">Après traitement, vous devez trouver le premier message dans l'emplacement d'envoi et le second, avec une priorité basse, dans la file d'attente des messages interrompus.</span><span class="sxs-lookup"><span data-stu-id="f78dc-223">After processing, you should find the first message in the send location and the second, low-priority, message in the Suspended queue.</span></span>  
  
### <a name="content-based-routing-cbr"></a><span data-ttu-id="f78dc-224">Routage basé sur le contenu</span><span class="sxs-lookup"><span data-stu-id="f78dc-224">Content-Based Routing (CBR)</span></span>  
 <span data-ttu-id="f78dc-225">Vous avez la possibilité d'utiliser le routage basé sur le contenu pour acheminer les messages en fonction de leur contenu.</span><span class="sxs-lookup"><span data-stu-id="f78dc-225">You can use content-based routing to route messages based on their content.</span></span> <span data-ttu-id="f78dc-226">Dans ce scénario, l'acheminement est basé sur la priorité : les messages dont la priorité est élevée sont dirigés vers un emplacement d'envoi, et ceux dont la priorité est moyenne ou basse le sont vers un emplacement d'envoi différent.</span><span class="sxs-lookup"><span data-stu-id="f78dc-226">In this scenario, routing is based on priority, with High messages going to one send location and Low and Medium messages going to a different send location.</span></span>  
  
 <span data-ttu-id="f78dc-227">Pour étendre l'exemple, vous devez effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f78dc-227">To extend the sample, you must complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="f78dc-228">Promouvoir le **priorité** champ du schéma Error dans le projet BasicXMLEnvelope.</span><span class="sxs-lookup"><span data-stu-id="f78dc-228">Promote the **Priority** field in the Error schema in the BasicXMLEnvelope project.</span></span> <span data-ttu-id="f78dc-229">Le routage basé sur le contenu s'appuie sur les propriétés promues pour acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="f78dc-229">Content-based routing relies on promoted properties to route messages.</span></span> <span data-ttu-id="f78dc-230">Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f78dc-230">For more information, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
2.  <span data-ttu-id="f78dc-231">Créer et configurer deux ports d'envoi supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f78dc-231">Create and configure two additional send ports.</span></span> <span data-ttu-id="f78dc-232">Les ports utilisent un filtre pour s'assurer qu'ils reçoivent les messages appropriés.</span><span class="sxs-lookup"><span data-stu-id="f78dc-232">The ports use a filter to ensure they receive appropriate messages.</span></span>  
  
##### <a name="to-promote-the-priority-field-in-the-error-schema"></a><span data-ttu-id="f78dc-233">Pour promouvoir le champ Priorité du schéma Error</span><span class="sxs-lookup"><span data-stu-id="f78dc-233">To promote the Priority field in the Error schema</span></span>  
  
1.  <span data-ttu-id="f78dc-234">Avec la **BasicXMLEnvelope** ouvert dans le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **erreur** schéma et développez le **erreur** nœud.</span><span class="sxs-lookup"><span data-stu-id="f78dc-234">With the **BasicXMLEnvelope** project open in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **Error** schema and expand the **Error** node.</span></span>  
  
2.  <span data-ttu-id="f78dc-235">Cliquez sur le **priorité** élément, pointez sur **promouvoir**, puis cliquez sur **promotion rapide**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-235">Right-click the **Priority** element, point to **Promote**, and then click **Quick Promote**.</span></span>  
  
3.  <span data-ttu-id="f78dc-236">Cliquez sur **OK** pour confirmer l’ajout d’un nouveau schéma de propriété pour les propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="f78dc-236">Click **OK** to confirm the addition of a new property schema for the promoted properties.</span></span>  
  
4.  <span data-ttu-id="f78dc-237">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, ouvrez le schéma de propriété PropertySchema.xsd.</span><span class="sxs-lookup"><span data-stu-id="f78dc-237">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, open the new property schema PropertySchema.xsd.</span></span> <span data-ttu-id="f78dc-238">Supprimez « Field1 » à partir du schéma.</span><span class="sxs-lookup"><span data-stu-id="f78dc-238">Remove "Field1" from the schema.</span></span>  
  
5.  <span data-ttu-id="f78dc-239">Recompilez et redéployez la solution.</span><span class="sxs-lookup"><span data-stu-id="f78dc-239">Now recompile and redeploy the solution.</span></span> <span data-ttu-id="f78dc-240">Dans le menu Générer, sélectionnez Déployer BasicXMLEnvelope.</span><span class="sxs-lookup"><span data-stu-id="f78dc-240">On the Build menu, choose Deploy BasicXMLEnvelope.</span></span>  
  
6.  <span data-ttu-id="f78dc-241">Le projet était configuré pour réinitialiser l'instance hôte une fois la solution redéployée.</span><span class="sxs-lookup"><span data-stu-id="f78dc-241">The project was configured to reset the host instance when the solution is redeployed.</span></span> <span data-ttu-id="f78dc-242">Si vous avez modifié cet élément, vous devez arrêter et démarrer l'hôte.</span><span class="sxs-lookup"><span data-stu-id="f78dc-242">If you have changed this, you need to stop and start the host.</span></span>  
  
##### <a name="to-configure-the-low-and-medium-priority-send-port"></a><span data-ttu-id="f78dc-243">Pour configurer le port d'envoi de priorité basse et moyenne</span><span class="sxs-lookup"><span data-stu-id="f78dc-243">To configure the low and medium-priority send port</span></span>  
  
1.  <span data-ttu-id="f78dc-244">Utilisez l’Explorateur Windows pour créer un répertoire nommé « SendLowMediumPriority » sous le **BasicXMLEnvelope** répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-244">Use Windows Explorer to create a directory named "SendLowMediumPriority" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="f78dc-245">Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-245">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way**.</span></span>  
  
3.  <span data-ttu-id="f78dc-246">Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « SendLowMediumPriority ».</span><span class="sxs-lookup"><span data-stu-id="f78dc-246">In the **Send Port Properties** dialog box, set the name of the port to "SendLowMediumPriority".</span></span>  
  
4.  <span data-ttu-id="f78dc-247">Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-247">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="f78dc-248">Définissez le dossier de destination sur le répertoire que vous avez créé auparavant.</span><span class="sxs-lookup"><span data-stu-id="f78dc-248">Set the destination folder to the directory you created earlier.</span></span> <span data-ttu-id="f78dc-249">Cliquez sur **OK** à fermer.</span><span class="sxs-lookup"><span data-stu-id="f78dc-249">Click **OK** to close.</span></span>  
  
5.  <span data-ttu-id="f78dc-250">Cliquez sur **filtres** et ajouter trois expressions de filtre :</span><span class="sxs-lookup"><span data-stu-id="f78dc-250">Click **Filters** and add three filter expressions:</span></span>  
  
    -   <span data-ttu-id="f78dc-251">BTS.MessageType == http://BasicXMLEnvelope#Error And</span><span class="sxs-lookup"><span data-stu-id="f78dc-251">BTS.MessageType == http://BasicXMLEnvelope#Error And</span></span>  
  
    -   <span data-ttu-id="f78dc-252">BasicXMLEnvelope.PropertySchema.Priority == Low Or</span><span class="sxs-lookup"><span data-stu-id="f78dc-252">BasicXMLEnvelope.PropertySchema.Priority == Low Or</span></span>  
  
    -   <span data-ttu-id="f78dc-253">BasicXMLEnvelope.PropertySchema.Priority == Medium</span><span class="sxs-lookup"><span data-stu-id="f78dc-253">BasicXMLEnvelope.PropertySchema.Priority == Medium</span></span>  
  
6.  <span data-ttu-id="f78dc-254">Cliquez sur **OK** pour terminer la configuration de port d’envoi de faible priorité et moyenne.</span><span class="sxs-lookup"><span data-stu-id="f78dc-254">Click **OK** to complete the low and medium-priority send port configuration.</span></span>  
  
##### <a name="to-configure-the-high-priority-send-port"></a><span data-ttu-id="f78dc-255">Pour configurer le port d'envoi de priorité élevée</span><span class="sxs-lookup"><span data-stu-id="f78dc-255">To configure the high-priority send port</span></span>  
  
1.  <span data-ttu-id="f78dc-256">Utilisez l’Explorateur Windows pour créer un répertoire nommé « SendHighPriority » sous le **BasicXMLEnvelope** répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="f78dc-256">Use Windows Explorer to create a directory named "SendHighPriority" under the **BasicXMLEnvelope** project directory.</span></span>  
  
2.  <span data-ttu-id="f78dc-257">Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-257">In the BizTalk Server Administration console, expand the **BasicXMLEnvelope** application, right-click **Send Ports**, point to **New**, and then click **Static One-Way**.</span></span>  
  
3.  <span data-ttu-id="f78dc-258">Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « SendHighPriority ».</span><span class="sxs-lookup"><span data-stu-id="f78dc-258">In the **Send Port Properties** dialog box, set the name of the port to "SendHighPriority".</span></span>  
  
4.  <span data-ttu-id="f78dc-259">Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-259">For **Transport Type**, select **FILE**, and then click **Configure**.</span></span> <span data-ttu-id="f78dc-260">Définissez le dossier de destination sur le répertoire que vous avez créé auparavant.</span><span class="sxs-lookup"><span data-stu-id="f78dc-260">Set the destination folder to the directory you created earlier.</span></span> <span data-ttu-id="f78dc-261">Cliquez sur **OK** à fermer.</span><span class="sxs-lookup"><span data-stu-id="f78dc-261">Click **OK** to close.</span></span>  
  
5.  <span data-ttu-id="f78dc-262">Cliquez sur **filtres** et ajouter deux expressions de filtre :</span><span class="sxs-lookup"><span data-stu-id="f78dc-262">Click **Filters** and add two filter expressions:</span></span>  
  
    -   <span data-ttu-id="f78dc-263">BTS.MessageType == http://BasicXMLEnvelope#Error And</span><span class="sxs-lookup"><span data-stu-id="f78dc-263">BTS.MessageType == http://BasicXMLEnvelope#Error And</span></span>  
  
    -   <span data-ttu-id="f78dc-264">BasicXMLEnvelope.PropertySchema.Priority == High</span><span class="sxs-lookup"><span data-stu-id="f78dc-264">BasicXMLEnvelope.PropertySchema.Priority == High</span></span>  
  
6.  <span data-ttu-id="f78dc-265">Cliquez sur **OK** pour terminer la configuration de port d’envoi de priorité élevée.</span><span class="sxs-lookup"><span data-stu-id="f78dc-265">Click **OK** to complete the high-priority send port configuration.</span></span>  
  
##### <a name="to-test-the-routing-solution"></a><span data-ttu-id="f78dc-266">Pour tester la solution de routage</span><span class="sxs-lookup"><span data-stu-id="f78dc-266">To test the routing solution</span></span>  
  
1.  <span data-ttu-id="f78dc-267">Dans la console Administration de BizTalk Server, développez le **Applications** de groupe, cliquez sur le **BasicXMLEnvelope** application, puis sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-267">In the BizTalk Server Administration console, expand the **Applications** group, right-click the **BasicXMLEnvelope** application, and then click **Start**.</span></span> <span data-ttu-id="f78dc-268">Lorsque vous êtes invité à confirmer, cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="f78dc-268">When prompted to confirm, click **Start**.</span></span> <span data-ttu-id="f78dc-269">Les nouveaux ports d'envoi sont ainsi inscrits.</span><span class="sxs-lookup"><span data-stu-id="f78dc-269">This enlists the new send ports.</span></span>  
  
2.  <span data-ttu-id="f78dc-270">Déposez le message test dans l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f78dc-270">Drop the test message into the receive location.</span></span> <span data-ttu-id="f78dc-271">Notez la façon dont les messages d'erreur sont acheminés vers les différents emplacements :</span><span class="sxs-lookup"><span data-stu-id="f78dc-271">Notice how error messages are routed to the different send locations:</span></span>  
  
    -   <span data-ttu-id="f78dc-272">Les messages dont la priorité est basse, moyenne ou élevée et dont le traitement n'échoue pas sont acheminés vers l'emplacement d'envoi d'origine (configuré au cœur de l'exemple) et l'emplacement d'envoi par priorité.</span><span class="sxs-lookup"><span data-stu-id="f78dc-272">Error messages that have a Low, Medium, or High priority and do not fail message processing are routed both to the original send location (configured in the core example) and the send location by priority.</span></span> <span data-ttu-id="f78dc-273">Pour les messages dont la priorité est basse ou moyenne, une copie s'affiche à la fois dans l'emplacement d'envoi d'origine et dans l'emplacement d'envoi de priorité basse ou moyenne.</span><span class="sxs-lookup"><span data-stu-id="f78dc-273">For messages with a Low or Medium priority, a copy appears in both the original send location and the Low/Medium send location.</span></span>  
  
    -   <span data-ttu-id="f78dc-274">Si le traitement des échanges récupérables est activé, le message d'erreur ayant échoué n'est pas acheminé et le message n'ayant pas échoué est acheminé comme prévu.</span><span class="sxs-lookup"><span data-stu-id="f78dc-274">If recoverable interchange processing is enabled, the failed error message is not routed and the nonfailed message is properly routed as expected.</span></span> <span data-ttu-id="f78dc-275">Le message ayant échoué n'est pas acheminé car son type ne correspond pas au type utilisé dans les filtres configurés.</span><span class="sxs-lookup"><span data-stu-id="f78dc-275">The failed message is not routed because its message type does not match the type used in the configured filters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78dc-276">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f78dc-276">See Also</span></span>  
 <span data-ttu-id="f78dc-277">[Traitement des échanges récupérables](../core/recoverable-interchange-processing.md) </span><span class="sxs-lookup"><span data-stu-id="f78dc-277">[Recoverable Interchange Processing](../core/recoverable-interchange-processing.md) </span></span>  
 <span data-ttu-id="f78dc-278">[Promotion des propriétés](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f78dc-278">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 [<span data-ttu-id="f78dc-279">CBRSample (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="f78dc-279">CBRSample (BizTalk Server Sample)</span></span>](../core/cbrsample-biztalk-server-sample.md)