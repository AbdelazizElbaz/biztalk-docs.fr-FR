---
title: "Comment : valider un Message à l’aide d’une architecture ESB rampe d’entrée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43dfc791-7cb6-45a4-898f-f53def199c08
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63a6a79a12949148f77363d7e4cffd2b2c321d00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-validate-a-message-using-an-esb-on-ramp"></a><span data-ttu-id="30b3e-102">Comment : valider un Message à l’aide d’une architecture ESB rampe d’entrée</span><span class="sxs-lookup"><span data-stu-id="30b3e-102">How to: Validate a Message Using an ESB On-Ramp</span></span>
## <a name="goal"></a><span data-ttu-id="30b3e-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="30b3e-103">Goal</span></span>  
 <span data-ttu-id="30b3e-104">Cette section montre comment configurer le composant de pipeline de désassemblage de répartiteur ESB pour effectuer une validation de message pour les messages XML soumis à une architecture ESB rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="30b3e-104">This section demonstrates how to configure the ESB Dispatcher Disassemble pipeline component to perform message validation for XML messages submitted to an ESB on-ramp.</span></span>  
  
 <span data-ttu-id="30b3e-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b3e-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="30b3e-106">Créer un ESB rampe d’entrée qui utilise le **ItinerarySelectReceiveXml** pipeline.</span><span class="sxs-lookup"><span data-stu-id="30b3e-106">Create an ESB on-ramp that uses the **ItinerarySelectReceiveXml** pipeline.</span></span>  
  
-   <span data-ttu-id="30b3e-107">Configurer le composant de pipeline de désassemblage de répartiteur ESB pour valider le contenu du message.</span><span class="sxs-lookup"><span data-stu-id="30b3e-107">Configure the ESB Dispatcher Disassemble pipeline component to validate message content.</span></span>  
  
-   <span data-ttu-id="30b3e-108">Configurer le composant de pipeline de sélecteur de feuille de route pour résoudre l’itinéraire approprié.</span><span class="sxs-lookup"><span data-stu-id="30b3e-108">Configure the Itinerary Selector pipeline component to resolve the appropriate itinerary.</span></span>  
  
-   <span data-ttu-id="30b3e-109">Validation de message de test à l’aide d’un message valide et un message non valide.</span><span class="sxs-lookup"><span data-stu-id="30b3e-109">Test message validation using a valid message and an invalid message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="30b3e-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="30b3e-110">Prerequisites</span></span>  
 <span data-ttu-id="30b3e-111">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="30b3e-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="30b3e-112">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="30b3e-112">Before You Begin</span></span>  
 <span data-ttu-id="30b3e-113">Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="30b3e-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="30b3e-114">Créer un message de test non valide.</span><span class="sxs-lookup"><span data-stu-id="30b3e-114">Create an invalid test message.</span></span>  
  
-   <span data-ttu-id="30b3e-115">Créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB.</span><span class="sxs-lookup"><span data-stu-id="30b3e-115">Create an ESB itinerary domain-specific language (DSL) model.</span></span>  
  
-   <span data-ttu-id="30b3e-116">Configurez les propriétés de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="30b3e-116">Configure the properties of the itinerary.</span></span>  
  
-   <span data-ttu-id="30b3e-117">Définir la structure de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="30b3e-117">Define the structure of the itinerary.</span></span>  
  
-   <span data-ttu-id="30b3e-118">Exporter le modèle vers la base de données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="30b3e-118">Export the model to the Itinerary database.</span></span>  
  
 <span data-ttu-id="30b3e-119">Les procédures suivantes décrivent comment effectuer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="30b3e-119">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-an-invalid-test-message"></a><span data-ttu-id="30b3e-120">Pour créer un message de test non valide</span><span class="sxs-lookup"><span data-stu-id="30b3e-120">To create an invalid test message</span></span>  
  
1.  <span data-ttu-id="30b3e-121">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="30b3e-121">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="30b3e-122">Créer une copie de NAOrderDoc.xml et renommez la copie Invalid.xml.</span><span class="sxs-lookup"><span data-stu-id="30b3e-122">Create a copy of NAOrderDoc.xml, and then rename the copy Invalid.xml.</span></span>  
  
3.  <span data-ttu-id="30b3e-123">Dans le bloc-notes, ouvrez Invalid.xml.</span><span class="sxs-lookup"><span data-stu-id="30b3e-123">In Notepad, open Invalid.xml.</span></span>  
  
4.  <span data-ttu-id="30b3e-124">Modification  **\<ns0:requestType > 10\</ns0:requestType > à \<ns0:requestType > dix\</ns0:requestType >**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-124">Change **\<ns0:requestType>10\</ns0:requestType> to \<ns0:requestType>TEN\</ns0:requestType>**.</span></span>  
  
5.  <span data-ttu-id="30b3e-125">Enregistrer Invalid.xml en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="30b3e-125">Save Invalid.xml as UTF-8, and then close Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30b3e-126">En modifiant la valeur numérique de cet élément de texte, le message ne seront plus valide selon le schéma.</span><span class="sxs-lookup"><span data-stu-id="30b3e-126">By changing the numerical value of this element to text, the message will no longer be valid according to the schema.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="30b3e-127">Pour créer un modèle DSL de la feuille de route ESB</span><span class="sxs-lookup"><span data-stu-id="30b3e-127">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="30b3e-128">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="30b3e-128">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="30b3e-129">Dans l’Explorateur de solutions, cliquez sur **ItineraryLibrary**, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-129">In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="30b3e-130">Dans le **ajouter un nouvel élément** boîte de dialogue, tapez **Validation** dans les **nom** zone, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-130">In the **Add New Item** dialog box, type **Validation** in the **Name** box, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="30b3e-131">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="30b3e-131">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="30b3e-132">Dans Visual Studio, cliquez sur l’aire de conception de **Validation.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-132">In Visual Studio, click the design surface of **Validation.itinerary**.</span></span> <span data-ttu-id="30b3e-133">Dans le **Validation** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b3e-133">In the **Validation** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="30b3e-134">Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-134">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="30b3e-135">Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.</span><span class="sxs-lookup"><span data-stu-id="30b3e-135">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="30b3e-136">Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).</span><span class="sxs-lookup"><span data-stu-id="30b3e-136">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="30b3e-137">Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-137">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30b3e-138">Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque le message est reçu.</span><span class="sxs-lookup"><span data-stu-id="30b3e-138">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when the message is received.</span></span> <span data-ttu-id="30b3e-139">Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser un programme de résolution statique pour sélectionner l’itinéraire approprié à partir de ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="30b3e-139">You will later configure the Itinerary Selector pipeline component to use a static resolver to select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="30b3e-140">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="30b3e-140">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="30b3e-141">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="30b3e-141">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="30b3e-142">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b3e-142">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="30b3e-143">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-143">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="30b3e-144">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-144">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="30b3e-145">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-145">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="30b3e-146">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-146">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="30b3e-147">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de l’élément de modèle existant.</span><span class="sxs-lookup"><span data-stu-id="30b3e-147">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the existing model element.</span></span> <span data-ttu-id="30b3e-148">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b3e-148">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="30b3e-149">Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-149">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="30b3e-150">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-150">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="30b3e-151">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-151">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="30b3e-152">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-152">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="30b3e-153">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="30b3e-153">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="30b3e-154">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b3e-154">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="30b3e-155">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-155">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="30b3e-156">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-156">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="30b3e-157">Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-157">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="30b3e-158">Avec le bouton droit le **résolveur** collection de la **SendPortFilter** élément, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-158">Right-click the **Resolver** collection of the **SendPortFilter** element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="30b3e-159">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b3e-159">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="30b3e-160">Cliquez sur le **nom** propriété, puis tapez **ConfigureOffRamp**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-160">Click the **Name** property, and then type **ConfigureOffRamp**.</span></span>  
  
    2.  <span data-ttu-id="30b3e-161">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-161">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="30b3e-162">Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-162">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="30b3e-163">Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\Validated%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-163">Click the **Transport Location** property, and then type **C:\HowTos\Out\Validated%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="30b3e-164">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-164">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="30b3e-165">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="30b3e-165">Drag a connection from the **ReceiveNAOrder** model element to the **SendPortFilter** model element.</span></span>  
  
6.  <span data-ttu-id="30b3e-166">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="30b3e-167">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="30b3e-167">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="30b3e-168">Pour exporter le modèle vers la base de données d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="30b3e-168">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="30b3e-169">Dans Visual Studio, cliquez sur l’aire de conception de la **Validation** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-169">In Visual Studio, right-click the design surface of the **Validation** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30b3e-170">L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de pipeline du sélecteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="30b3e-170">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector pipeline component.</span></span>  
  
2.  <span data-ttu-id="30b3e-171">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="30b3e-171">Save all project artifacts.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="30b3e-172">Étapes</span><span class="sxs-lookup"><span data-stu-id="30b3e-172">Steps</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="30b3e-173">Pour créer et configurer un ESB rampe d’entrée</span><span class="sxs-lookup"><span data-stu-id="30b3e-173">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="30b3e-174">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-174">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="30b3e-175">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, développez **groupe BizTalk**, développez **Applications**, puis développez **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-175">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="30b3e-176">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-176">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="30b3e-177">Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-177">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="30b3e-178">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, tapez **OnRamp.Itinerary.HowTo** dans les **nom** boîte.</span><span class="sxs-lookup"><span data-stu-id="30b3e-178">In the **Receive Location Properties** dialog box, type **OnRamp.Itinerary.HowTo** in the **Name** box.</span></span>  
  
6.  <span data-ttu-id="30b3e-179">Dans le **Type** la liste déroulante, cliquez sur **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-179">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="30b3e-180">Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\HowTos\DropFolder** dans les **dossier de réception** zone, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-180">In the **FILE Transport Properties** dialog box, type **C:\HowTos\DropFolder** in the **Receive folder** box, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-on-ramp-to-perform-message-validation"></a><span data-ttu-id="30b3e-181">Pour configurer la rampe d’entrée pour effectuer une validation de message</span><span class="sxs-lookup"><span data-stu-id="30b3e-181">To configure the on-ramp to perform message validation</span></span>  
  
1.  <span data-ttu-id="30b3e-182">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **pipeline de réception** la liste déroulante, cliquez sur **ItinerarySelectReceiveXml**, puis cliquez sur le bouton de sélection (...) ).</span><span class="sxs-lookup"><span data-stu-id="30b3e-182">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="30b3e-183">Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **désassembleur XML** les propriétés du composant :</span><span class="sxs-lookup"><span data-stu-id="30b3e-183">Use the **Configure Pipeline** dialog box to configure the following **XML disassembler** component properties:</span></span>  
  
    1.  <span data-ttu-id="30b3e-184">Développez l’application GlobalBank.Esb, puis cliquez sur **schémas**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-184">Expand the GlobalBank.Esb application, and then click **Schemas**.</span></span> <span data-ttu-id="30b3e-185">Avec le bouton droit **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-185">Right-click **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**, and then click **Properties**.</span></span> <span data-ttu-id="30b3e-186">Copie le **nom** et **Assembly** propriétés et les coller dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="30b3e-186">Copy the **Name** and **Assembly** properties and paste them into a text file.</span></span>  
  
    2.  <span data-ttu-id="30b3e-187">Dans le **désassembler** composant, cliquez sur **True** dans les **ValidateDocument** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="30b3e-187">In the **Disassemble** component, click **True** in the **ValidateDocument** drop-down list.</span></span>  
  
    3.  <span data-ttu-id="30b3e-188">Cliquez sur le **DocumentSpecNames** propriété, puis tapez le nom qualifié complet du schéma.</span><span class="sxs-lookup"><span data-stu-id="30b3e-188">Click the **DocumentSpecNames** property, and then type the fully qualified name of the schema.</span></span> <span data-ttu-id="30b3e-189">Le nom qualifié complet commence par le nom et est suivi par une virgule et les informations d’assembly extrait à l’étape un.</span><span class="sxs-lookup"><span data-stu-id="30b3e-189">The fully qualified name starts with the name and is followed by a comma and the assembly information extracted in step a.</span></span> <span data-ttu-id="30b3e-190">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="30b3e-190">The following is an example:</span></span>  
  
         <span data-ttu-id="30b3e-191">GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc, GlobalBank.ESB.DynamicResolution.Schemas, Version = 2.0.0.0, Culture = neutral, PublicKeyToken = c2c8b2b87f54180a</span><span class="sxs-lookup"><span data-stu-id="30b3e-191">GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc, GlobalBank.ESB.DynamicResolution.Schemas, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="30b3e-192">Il s’agit du nom qualifié complet du schéma à valider ; Il est composé du nom de schéma et les quatre propriétés de l’assembly : nom de l’assembly, version, culture et jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="30b3e-192">This is the fully qualified name of the schema to be validated; it is comprised of the schema name and four assembly properties: assembly name, version, culture, and public key token.</span></span> <span data-ttu-id="30b3e-193">Plusieurs valeurs sont autorisées ; Séparez plusieurs schémas avec une barre verticale (&#124;) symbole.</span><span class="sxs-lookup"><span data-stu-id="30b3e-193">Multiple values are allowed; separate multiple schemas with a pipe (&#124;) symbol.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="30b3e-194">Pour configurer le composant de Pipeline de sélecteur de feuille de route</span><span class="sxs-lookup"><span data-stu-id="30b3e-194">To configure the Itinerary Selector Pipeline component</span></span>  
  
1.  <span data-ttu-id="30b3e-195">Dans le **configurer le Pipeline** boîte de dialogue zone, configurez les éléments suivants **itinéraire sélecteur** les propriétés du composant :</span><span class="sxs-lookup"><span data-stu-id="30b3e-195">In the **Configure Pipeline** dialog box, configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="30b3e-196">Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-196">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="30b3e-197">Cliquez sur le **ResolverConnectionString** propriété, puis tapez **itinéraire :\\\name=Validation ;**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-197">Click the **ResolverConnectionString** property, and then type **ITINERARY:\\\name=Validation;**.</span></span>  
  
    3.  <span data-ttu-id="30b3e-198">Cliquez sur **OK** pour fermer la **configurer le Pipeline** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="30b3e-198">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
2.  <span data-ttu-id="30b3e-199">Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="30b3e-199">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="30b3e-200">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-200">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-message-validation-and-itinerary-selection"></a><span data-ttu-id="30b3e-201">Pour tester la sélection de validation et de la feuille de route des messages</span><span class="sxs-lookup"><span data-stu-id="30b3e-201">To test the message validation and itinerary selection</span></span>  
  
1.  <span data-ttu-id="30b3e-202">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="30b3e-202">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="30b3e-203">Copie (ne déplacez pas) NAOrderDoc.xml dans le dossier Dossier_dépôt.</span><span class="sxs-lookup"><span data-stu-id="30b3e-203">Copy (do not move) NAOrderDoc.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="30b3e-204">Accédez à C:\HowTos\Out. Vérifiez que Validated%MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="30b3e-204">Browse to C:\HowTos\Out. Verify that Validated%MessageID%.xml has been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30b3e-205">Le message valid terminé son routage basé sur l’itinéraire, comme prévu.</span><span class="sxs-lookup"><span data-stu-id="30b3e-205">The valid message completed its itinerary-based routing, as expected.</span></span>  
  
4.  <span data-ttu-id="30b3e-206">Supprimez Validated%MessageID%.xml dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="30b3e-206">Delete Validated%MessageID%.xml from the Out folder.</span></span>  
  
5.  <span data-ttu-id="30b3e-207">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="30b3e-207">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
6.  <span data-ttu-id="30b3e-208">Copie (ne déplacez pas) Invalid.xml dans le dossier Dossier_dépôt.</span><span class="sxs-lookup"><span data-stu-id="30b3e-208">Copy (do not move) Invalid.xml to the DropFolder folder.</span></span>  
  
7.  <span data-ttu-id="30b3e-209">Accédez à C:\HowTos\Out. Vérifiez qu’aucun message n’a été remis.</span><span class="sxs-lookup"><span data-stu-id="30b3e-209">Browse to C:\HowTos\Out. Verify that no new message has been delivered.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30b3e-210">Le message n’a pas pu être validé ; Par conséquent, le routage basé sur la feuille de route pas pu être effectué.</span><span class="sxs-lookup"><span data-stu-id="30b3e-210">The message could not be validated; therefore, itinerary-based routing could not be completed.</span></span>  
  
8.  <span data-ttu-id="30b3e-211">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **outils d’administration**, puis cliquez sur **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-211">Click **Start** on the taskbar, point to **Administrative Tools**, and then click **Event Viewer**.</span></span>  
  
9. <span data-ttu-id="30b3e-212">Dans l’Observateur d’événements, développez **journaux Windows**, puis cliquez sur **Application**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-212">In Event Viewer, expand **Windows Logs**, and then click **Application**.</span></span>  
  
10. <span data-ttu-id="30b3e-213">Recherchez un événement récent où le **Source** est  **[!INCLUDE[prague](../includes/prague-md.md)]** et le **ID d’événement** est **5719**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-213">Locate a recent event where the **Source** is **[!INCLUDE[prague](../includes/prague-md.md)]**, and the **Event ID** is **5719**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30b3e-214">La présentation et l’échec du message non valide a entraîné une entrée d’exception dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="30b3e-214">The submission and failure of the invalid message resulted in an exception entry to the application event log.</span></span>  
  
11. <span data-ttu-id="30b3e-215">Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-215">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.</span></span>  
  
12. <span data-ttu-id="30b3e-216">Après le **OnRamp.Itinerary.HowTo** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-216">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="30b3e-217">Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="30b3e-217">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="30b3e-218">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="30b3e-218">Additional Resources</span></span>  
 <span data-ttu-id="30b3e-219">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="30b3e-219">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="30b3e-220">Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="30b3e-220">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="30b3e-221">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="30b3e-221">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="30b3e-222">Installer et exécuter l’exemple de résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="30b3e-222">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)