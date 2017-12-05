---
title: "Comment : créer un itinéraire pour acheminer un Message à une adresse de messagerie à l’aide d’une requête LDAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d9929dd-5e45-4b0d-90df-52a35e68b0ba
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 751eaf381b762372652bb77ddf6f00ffe43971c2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-create-an-itinerary-to-dynamically-route-a-message-to-an-email-address-using-an-ldap-query"></a><span data-ttu-id="a0852-102">Comment : créer un itinéraire pour acheminer un Message à une adresse de messagerie à l’aide d’une requête LDAP</span><span class="sxs-lookup"><span data-stu-id="a0852-102">How to: Create an Itinerary to Dynamically Route a Message to an Email Address Using an LDAP Query</span></span>
## <a name="goal"></a><span data-ttu-id="a0852-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="a0852-103">Goal</span></span>  
 <span data-ttu-id="a0852-104">Cette section montre comment créer un itinéraire qui interroge une adresse de messagerie via le protocole LDAP (Lightweight Directory Access Protocol), puis envoie un message électronique au point de terminaison résolu à l’aide de l’adaptateur SMTP de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a0852-104">This section demonstrates how to create an itinerary that queries an e-mail address through LDAP (Lightweight Directory Access Protocol) and then sends an e-mail message to the resolved endpoint using the BizTalk Server SMTP adapter.</span></span>  
  
 <span data-ttu-id="a0852-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="a0852-106">Créer un bordereau d’itinéraire de routage pour acheminer un message à l’aide d’une requête LDAP.</span><span class="sxs-lookup"><span data-stu-id="a0852-106">Create an itinerary routing slip to dynamically route a message using an LDAP query.</span></span>  
  
-   <span data-ttu-id="a0852-107">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="a0852-107">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a0852-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a0852-108">Prerequisites</span></span>  
 <span data-ttu-id="a0852-109">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="a0852-109">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
 <span data-ttu-id="a0852-110">L’ordinateur sur lequel vous allez réaliser cette section doit avoir le service d’annuaire Microsoft Active Directory configuré et en cours d’exécution (il n’est pas nécessaire que l’ordinateur est le contrôleur de domaine, mais il doit être connecté au domaine).</span><span class="sxs-lookup"><span data-stu-id="a0852-110">The computer on which you will complete this section must have Microsoft Active Directory directory service configured and running (it is not required that the computer is the domain controller, but it must be connected to the domain).</span></span> <span data-ttu-id="a0852-111">En outre, un serveur SMTP doit être configuré et en cours d’exécution ; Pour tester le résultat de cette rubrique, vous devez disposer d’un client pour vérifier le courrier électronique envoyé par l’architecture ESB.</span><span class="sxs-lookup"><span data-stu-id="a0852-111">Also, an SMTP server must be configured and running; in order to test the outcome of this How-to topic, you must have a client with which to check the e-mail sent by the ESB.</span></span>  
  
 <span data-ttu-id="a0852-112">Les instructions de cette section supposent qu’une organisation appelée Global Bank, avec un domaine globalbank.com, avec une unité organisationnelle Active Directory nommé Employees qui contient un utilisateur nommé John Evans avec une adresse de messagerie valide dans son profil (par exemple, johne@globalbank.com).</span><span class="sxs-lookup"><span data-stu-id="a0852-112">The instructions in this section assume an organization named Global Bank, with a domain of globalbank.com, with an Active Directory Organizational Unit named Employees that contains a user named John Evans with a valid e-mail address in his profile (such as johne@globalbank.com).</span></span> <span data-ttu-id="a0852-113">Il n’est pas nécessaire de répliquer ces facteurs environnementaux ; Toutefois, pour des raisons d’avoir à recréer cette implémentation dans votre environnement, veuillez prendre en compte ces facteurs et effectuer des substitutions selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="a0852-113">It is not necessary to replicate these environmental factors; however, for purposes of recreating this implementation in your environment, please account for these factors and make substitutions as necessary.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="a0852-114">Étapes</span><span class="sxs-lookup"><span data-stu-id="a0852-114">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model"></a><span data-ttu-id="a0852-115">Pour créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB</span><span class="sxs-lookup"><span data-stu-id="a0852-115">To create an ESB itinerary domain-specific language (DSL) model</span></span>  
  
1.  <span data-ttu-id="a0852-116">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="a0852-116">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="a0852-117">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="a0852-117">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="a0852-118">Dans le **ajouter un nouvel élément** boîte de dialogue, tapez **LdapResolution** dans les **nom** zone, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a0852-118">In the **Add New Item** dialog box, type **LdapResolution** in the **Name** box, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="a0852-119">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a0852-119">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="a0852-120">Dans Visual Studio, cliquez sur l’aire de conception de **LdapResolution.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="a0852-120">In Visual Studio, click the design surface of **LdapResolution.itinerary**.</span></span> <span data-ttu-id="a0852-121">Dans le **LdapResolution** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-121">In the **LdapResolution** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a0852-122">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-122">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="a0852-123">Sous le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="a0852-123">Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="a0852-124">Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\LdapResolution** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a0852-124">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\LdapResolution** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a0852-125">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="a0852-125">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="a0852-126">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="a0852-126">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="a0852-127">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a0852-127">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="a0852-128">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a0852-128">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="a0852-129">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="a0852-129">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="a0852-130">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-130">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a0852-131">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="a0852-131">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="a0852-132">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-132">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="a0852-133">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="a0852-133">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="a0852-134">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="a0852-134">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="a0852-135">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a0852-135">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="a0852-136">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-136">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a0852-137">Cliquez sur le **nom** propriété, puis tapez **RouteMessageEmail**.</span><span class="sxs-lookup"><span data-stu-id="a0852-137">Click the **Name** property, and then type **RouteMessageEmail**.</span></span>  
  
    2.  <span data-ttu-id="a0852-138">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="a0852-138">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a0852-139">Cette propriété définit que le processus a lieu dans un pipeline (messagerie).</span><span class="sxs-lookup"><span data-stu-id="a0852-139">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="a0852-140">Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-140">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="a0852-141">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="a0852-141">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="a0852-142">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="a0852-142">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="a0852-143">Avec le bouton droit le **résolveur** collection de la **RouteMessageEmail** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="a0852-143">Right-click the **Resolver** collection of the **RouteMessageEmail** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="a0852-144">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-144">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a0852-145">Cliquez sur le **nom** propriété, puis tapez **LdapResolver**.</span><span class="sxs-lookup"><span data-stu-id="a0852-145">Click the **Name** property, and then type **LdapResolver**.</span></span>  
  
    2.  <span data-ttu-id="a0852-146">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension du programme de résolution LDAP**.</span><span class="sxs-lookup"><span data-stu-id="a0852-146">In the **Resolver Implementation** drop-down list, click **LDAP Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="a0852-147">Dans le **nom Transport** la liste déroulante, cliquez sur **SMTP**.</span><span class="sxs-lookup"><span data-stu-id="a0852-147">In the **Transport Name** drop-down list, click **SMTP**.</span></span>  
  
    4.  <span data-ttu-id="a0852-148">Cliquez sur le **Transport emplacement** propriété, puis tapez **{message}**</span><span class="sxs-lookup"><span data-stu-id="a0852-148">Click the **Transport Location** property, and then type **{mail}**</span></span>  
  
    5.  <span data-ttu-id="a0852-149">Cliquez sur le **SearchRoot** propriété, puis tapez **unité d’organisation = employés, dc = globalbank, dc = com**</span><span class="sxs-lookup"><span data-stu-id="a0852-149">Click the **SearchRoot** property, and then type **ou=Employees,dc=globalbank,dc=com**</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a0852-150">Si vous n’avez pas configuré votre environnement en fonction des spécifications dans la section « Conditions préalables », remplacez les valeurs dans la propriété précédente par celles qui sont appropriées pour votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a0852-150">If you have not set up your environment according to the specifications in the "Prerequisites" section, replace the values in the preceding property with ones that are appropriate for your environment.</span></span>  
  
    6.  <span data-ttu-id="a0852-151">Cliquez sur le **filtre** propriété, puis modifiez la valeur à **(&(objectClass=User) (&#124;(givenName=john)))**</span><span class="sxs-lookup"><span data-stu-id="a0852-151">Click the **Filter** property, and then change the value to **(&(objectClass=User)(&#124;(givenName=john)))**</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a0852-152">Tapez la valeur précédente pour remplacer le texte existant.</span><span class="sxs-lookup"><span data-stu-id="a0852-152">Type the preceding value to replace the existing text.</span></span>  
  
    7.  <span data-ttu-id="a0852-153">Dans le **ThrowErrorIfNotFound** la liste déroulante, cliquez sur **True**.</span><span class="sxs-lookup"><span data-stu-id="a0852-153">In the **ThrowErrorIfNotFound** drop-down list, click **True**.</span></span>  
  
4.  <span data-ttu-id="a0852-154">Dans la fenêtre Propriétés, cliquez sur le **Configuration de point de terminaison** propriété, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="a0852-154">In the Properties window, click the **Endpoint Configuration** property, and then click the ellipsis button (...).</span></span>  
  
    1.  <span data-ttu-id="a0852-155">Dans le **Configuration de point de terminaison** boîte de dialogue, cliquez sur le **EmailBodyText** propriété, puis tapez **ordre est prêt à être traité**.</span><span class="sxs-lookup"><span data-stu-id="a0852-155">In the **Endpoint Configuration** dialog box, click the **EmailBodyText** property, and then type **Order is ready to be processed**.</span></span>  
  
    2.  <span data-ttu-id="a0852-156">Cliquez sur le **de** propriété, puis tapez  **orders@globalbank.com** .</span><span class="sxs-lookup"><span data-stu-id="a0852-156">Click the **From** property, and then type **orders@globalbank.com**.</span></span>  
  
    3.  <span data-ttu-id="a0852-157">Cliquez sur le **MessagePartsAttachment** propriété, puis tapez **2**.</span><span class="sxs-lookup"><span data-stu-id="a0852-157">Click the **MessagePartsAttachment** property, and then type **2**.</span></span>  
  
    4.  <span data-ttu-id="a0852-158">Cliquez sur le **sujet** propriété, puis tapez **afin que {givenName}**.</span><span class="sxs-lookup"><span data-stu-id="a0852-158">Click the **Subject** property, and then type **Order for {givenName}**.</span></span>  
  
    5.  <span data-ttu-id="a0852-159">Configurer le **SMTPAuthentication, SMTPHost, nom d’utilisateur,** et **mot de passe** propriétés à l’aide des informations de connexion pour votre environnement local.</span><span class="sxs-lookup"><span data-stu-id="a0852-159">Configure the **SMTPAuthentication, SMTPHost, UserName,** and **Password** properties using the connection information for your local environment.</span></span>  
  
    6.  <span data-ttu-id="a0852-160">Cliquez sur **OK** pour fermer la **Configuration de point de terminaison** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a0852-160">Click **OK** to close the **Endpoint Configuration** dialog box.</span></span>  
  
5.  <span data-ttu-id="a0852-161">Cliquez sur le **LdapResolver** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.</span><span class="sxs-lookup"><span data-stu-id="a0852-161">Right-click the **LdapResolver** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
6.  <span data-ttu-id="a0852-162">Dans la fenêtre Sortie, vérifiez que l’objet dans le résolu **Configuration de point de terminaison** valeur est **afin que John**, puis vérifiez que le résolu **Transport emplacement** est le envoyer par courrier électronique adresse associée au compte de l’utilisateur dans Active Directory (par exemple, johne@globalbank.com).</span><span class="sxs-lookup"><span data-stu-id="a0852-162">In the Output window, verify the subject in the resolved **Endpoint Configuration** value is **Order for John**, and then verify that the resolved **Transport Location** is the e-mail address associated with the user's account in Active Directory (for example, johne@globalbank.com).</span></span>  
  
7.  <span data-ttu-id="a0852-163">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-163">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="a0852-164">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessageEmail** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a0852-164">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessageEmail** model element.</span></span>  
  
8.  <span data-ttu-id="a0852-165">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteMessageEmail** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a0852-165">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteMessageEmail** model element.</span></span> <span data-ttu-id="a0852-166">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-166">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a0852-167">Cliquez sur le **nom** propriété, puis tapez **EmailNAOrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="a0852-167">Click the **Name** property, and then type **EmailNAOrderDoc**.</span></span>  
  
    2.  <span data-ttu-id="a0852-168">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-168">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="a0852-169">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="a0852-169">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="a0852-170">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="a0852-170">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
9. <span data-ttu-id="a0852-171">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteMessageEmail** élément de modèle et la **EmailNAOrderDoc**élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a0852-171">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteMessageEmail** model element and the **EmailNAOrderDoc** model element.</span></span> <span data-ttu-id="a0852-172">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-172">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="a0852-173">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="a0852-173">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="a0852-174">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-174">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="a0852-175">Dans le **rampe** déroulante liste, développez **EmailNAOrderDoc**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="a0852-175">In the **Off-Ramp** drop-down list, expand **EmailNAOrderDoc**, and then click **Send Handlers**.</span></span>  
  
10. <span data-ttu-id="a0852-176">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-176">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="a0852-177">Faites glisser une connexion à partir de la **RouteMessageEmail** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a0852-177">Drag a connection from the **RouteMessageEmail** model element to the **SendPortFilter** model element.</span></span>  
  
11. <span data-ttu-id="a0852-178">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="a0852-178">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="a0852-179">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **EmailNAOrderDoc** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="a0852-179">Drag a connection from the **SendPortFilter** model element to the **EmailNAOrderDoc** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="a0852-180">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="a0852-180">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="a0852-181">Dans Visual Studio, cliquez sur l’aire de conception de la **LdapResolution** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="a0852-181">In Visual Studio, right-click the design surface of the **LdapResolution** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0852-182">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0852-182">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a0852-183">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="a0852-183">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="a0852-184">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (LdapResolution.xml).</span><span class="sxs-lookup"><span data-stu-id="a0852-184">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (LdapResolution.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="a0852-185">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a0852-185">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="a0852-186">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="a0852-186">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="a0852-187">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="a0852-187">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="a0852-188">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="a0852-188">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="a0852-189">Sélectionnez **LdapResolution.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="a0852-189">Select **LdapResolution.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="a0852-190">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="a0852-190">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="a0852-191">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="a0852-191">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="a0852-192">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="a0852-192">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="a0852-193">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="a0852-193">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="a0852-194">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="a0852-194">Click the **Submit Request** button.</span></span> <span data-ttu-id="a0852-195">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a0852-195">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="a0852-196">Ouvrez Microsoft Outlook Express (ou le client de messagerie de votre choix) et la vérification de la remise du message au message électronique de John Evans.</span><span class="sxs-lookup"><span data-stu-id="a0852-196">Open Microsoft Outlook Express (or the mail client of your choice) and verify delivery of the message to the e-mail of John Evans.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="a0852-197">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a0852-197">Additional Resources</span></span>  
 <span data-ttu-id="a0852-198">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0852-198">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="a0852-199">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="a0852-199">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="a0852-200">Utilisation de la résolution et du routage dynamiques</span><span class="sxs-lookup"><span data-stu-id="a0852-200">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)