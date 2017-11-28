---
title: "Pour configurer un protocole SOAP emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], virtual directories
- SOAP adapters, code samples
- configuring [SOAP adapters], receive locations
- virtual directories, SOAP adapters
- SOAP adapters, receive locations
- code samples, SOAP adapters
- configuring [SOAP adapters], code samples
- SOAP adapters, virtual directories
- receive locations, SOAP adapters
ms.assetid: 7e348409-9181-47e4-b3c0-c73eb2acffa3
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b33886296441082ea7d7e83b92659f81140d71f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-receive-location"></a><span data-ttu-id="9bea9-102">Configuration d'un emplacement de réception SOAP</span><span class="sxs-lookup"><span data-stu-id="9bea9-102">How to Configure a SOAP Receive Location</span></span>
<span data-ttu-id="9bea9-103">Vous pouvez configurer un emplacement de réception SOAP soit par programme soit à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bea9-103">You can configure a SOAP receive location either programmatically or by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="9bea9-104">**Comment faire pour configurer un emplacement de réception SOAP par programme**</span><span class="sxs-lookup"><span data-stu-id="9bea9-104">**How to Configure a SOAP Receive Location Programmatically**</span></span>  
  
 <span data-ttu-id="9bea9-105">L’Explorateur BizTalk de modèle d’objet vous permet de créer et configurer les emplacements de réception par programmation.</span><span class="sxs-lookup"><span data-stu-id="9bea9-105">The BizTalk Explorer object model enables you to create and configure receive locations programmatically.</span></span> <span data-ttu-id="9bea9-106">Le modèle d’objet de l’Explorateur BizTalk expose le**IReceiveLocation** emplacement interface de configuration de recevoir un **TransportTypeData** propriété en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="9bea9-106">The BizTalk Explorer object model exposes the**IReceiveLocation** receive location configuration interface that has a **TransportTypeData** read/write property.</span></span> <span data-ttu-id="9bea9-107">Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception SOAP sous la forme d'une chaîne XML composée d'une paire nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="9bea9-107">This property accepts a SOAP receive location configuration property bag in the form of a name-value pair of XML strings.</span></span> <span data-ttu-id="9bea9-108">Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, vous devez définir le **InboundTransportLocation** propriété de la **IReceiveLocation** interface.</span><span class="sxs-lookup"><span data-stu-id="9bea9-108">To set this property in the BizTalk Explorer object model, you must set the **InboundTransportLocation** property of the **IReceiveLocation** interface.</span></span>  
  
 <span data-ttu-id="9bea9-109">Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir.</span><span class="sxs-lookup"><span data-stu-id="9bea9-109">The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set.</span></span> <span data-ttu-id="9bea9-110">Dans ce cas, l'adaptateur SOAP utilise les valeurs par défaut pour la configuration de l'emplacement de réception SOAP, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9bea9-110">If it is not set, the SOAP adapter uses the default values for the SOAP receive location configuration as indicated in the following table.</span></span>  
  
 <span data-ttu-id="9bea9-111">Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement de réception SOAP.</span><span class="sxs-lookup"><span data-stu-id="9bea9-111">The following table lists the configuration properties that you can set in the BizTalk Explorer object model for the SOAP receive location.</span></span>  
  
|<span data-ttu-id="9bea9-112">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="9bea9-112">Property name</span></span>|<span data-ttu-id="9bea9-113">Type</span><span class="sxs-lookup"><span data-stu-id="9bea9-113">Type</span></span>|<span data-ttu-id="9bea9-114"> Description</span><span class="sxs-lookup"><span data-stu-id="9bea9-114">Description</span></span>|  
|-------------------|----------|-----------------|  
|<span data-ttu-id="9bea9-115">**URI**</span><span class="sxs-lookup"><span data-stu-id="9bea9-115">**URI**</span></span>|<span data-ttu-id="9bea9-116">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9bea9-116">String</span></span>|<span data-ttu-id="9bea9-117">Répertoire virtuel contenant le service Web sur le serveur de déploiement.</span><span class="sxs-lookup"><span data-stu-id="9bea9-117">Virtual directory containing the Web service on the deployment server.</span></span>|  
|<span data-ttu-id="9bea9-118">**AddressableURI**</span><span class="sxs-lookup"><span data-stu-id="9bea9-118">**AddressableURI**</span></span>|<span data-ttu-id="9bea9-119">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9bea9-119">String</span></span>|<span data-ttu-id="9bea9-120">Champ d'adresse publique contenant l'URL entière pouvant être appelée.</span><span class="sxs-lookup"><span data-stu-id="9bea9-120">Public address field containing the entire, callable URL.</span></span><br /><br /> <span data-ttu-id="9bea9-121">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="9bea9-121">Default value: Blank</span></span>|  
|<span data-ttu-id="9bea9-122">**UseSSO**</span><span class="sxs-lookup"><span data-stu-id="9bea9-122">**UseSSO**</span></span>|<span data-ttu-id="9bea9-123">Booléen</span><span class="sxs-lookup"><span data-stu-id="9bea9-123">Boolean</span></span>|<span data-ttu-id="9bea9-124">Spécifie si l'adaptateur SOAP émet le ticket d'authentification unique pour les messages arrivant sur cet emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="9bea9-124">Specifies whether the SOAP adapter issues the Single Sign-On ticket to the messages that arrive on this receive location.</span></span><br /><br /> <span data-ttu-id="9bea9-125">Valeur par défaut : False</span><span class="sxs-lookup"><span data-stu-id="9bea9-125">Default value: False</span></span>|  
  
 <span data-ttu-id="9bea9-126">Pour définir les propriétés, utilisez le format suivant :</span><span class="sxs-lookup"><span data-stu-id="9bea9-126">Use the following format to set the properties:</span></span>  
  
```  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
```  
  
 <span data-ttu-id="9bea9-127">Le **URI** et **AddressableURI** propriétés sont définies à l’aide de la **adresse** et **PublicAddress** propriétés de l’emplacement de réception objet.</span><span class="sxs-lookup"><span data-stu-id="9bea9-127">The **URI** and **AddressableURI** properties are set using the **Address** and **PublicAddress** properties of the receive location object.</span></span>  
  
 <span data-ttu-id="9bea9-128">Le fragment de code suivant illustre la création d'un emplacement de réception SOAP :</span><span class="sxs-lookup"><span data-stu-id="9bea9-128">The following code fragment illustrates creating a SOAP receive location:</span></span>  
  
```  
// Use BizTalk Explorer object model to create new SOAP receive location.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
  
// Add a new Request-Response port  
ReceivePort receivePort = explorer.AddNewReceivePort(true);  
receivePort.Name = "SampleReceivePort";  
receivePort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
  
// Add primary SOAP receive location  
ReceiveLocation receiveLocation = receivePort.AddNewReceiveLocation();  
receiveLocation.Name = "SampleReceiveLocation";  
receiveLocation.Address = "/PurchaseOrder/POOrchestration.asmx";  
receiveLocation.TransportType = explorer.ProtocolTypes["SOAP"];  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
receiveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
foreach (ReceiveHandler receiveHandler in explorer.ReceiveHandlers)  
{  
if (receiveHandler.TransportType.Name == receiveLocation.TransportType.Name)  
{  
receiveLocation.ReceiveHandler = receiveHandler;   
}  
}  
  
// Save  
explorer.SaveChanges();   
```  
  
 <span data-ttu-id="9bea9-129">**Comment configurer un protocole SOAP emplacement de réception avec la Console Administration de BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="9bea9-129">**How to Configure a SOAP Receive Location with the BizTalk Server Administration Console**</span></span>  
  
 <span data-ttu-id="9bea9-130">Vous pouvez définir des variables d'adaptateur d'emplacement de réception SOAP dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bea9-130">You can set SOAP receive location adapter variables in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="9bea9-131">Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="9bea9-131">If properties are not set in the receive location, the default receive handler values set in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console are used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bea9-132">Avant d'effectuer les procédures suivantes, vous devez avoir ajouté un port de réception.</span><span class="sxs-lookup"><span data-stu-id="9bea9-132">Before completing the following procedures you must have already added a receive port.</span></span> <span data-ttu-id="9bea9-133">Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).</span><span class="sxs-lookup"><span data-stu-id="9bea9-133">For more information, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).</span></span>  
  
### <a name="to-configure-variables-for-a-soap-receive-location"></a><span data-ttu-id="9bea9-134">Pour configurer les variables pour un emplacement de réception SOAP</span><span class="sxs-lookup"><span data-stu-id="9bea9-134">To configure variables for a SOAP receive location</span></span>  
  
1.  <span data-ttu-id="9bea9-135">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le vous souhaitez créer un emplacement de réception dans l’application.</span><span class="sxs-lookup"><span data-stu-id="9bea9-135">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application you want to create a receive location in.</span></span>  
  
2.  <span data-ttu-id="9bea9-136">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, dans le volet gauche, cliquez sur le **Port de réception** nœud.</span><span class="sxs-lookup"><span data-stu-id="9bea9-136">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, in the left pane, click the **Receive Port** node.</span></span> <span data-ttu-id="9bea9-137">Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-137">Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="9bea9-138">Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="9bea9-138">In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and then in the right pane, double-click an existing receive location or click **New**to create a new receive location.</span></span>  
  
4.  <span data-ttu-id="9bea9-139">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section regard **Type**, sélectionnez **SOAP** dans la liste déroulante, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-139">In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **SOAP** from the drop-down list, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="9bea9-140">Dans le **propriétés du Transport SOAP** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9bea9-140">In the **SOAP Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="9bea9-141">Utiliser</span><span class="sxs-lookup"><span data-stu-id="9bea9-141">Use this</span></span>|<span data-ttu-id="9bea9-142">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="9bea9-142">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="9bea9-143">**Répertoire virtuel assorti de fichier .asmx du Service Web**</span><span class="sxs-lookup"><span data-stu-id="9bea9-143">**Virtual directory plus Web Service .asmx file**</span></span>|<span data-ttu-id="9bea9-144">Indiquer le fichier .asmx créé par l'Assistant Publication de services Web de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9bea9-144">Indicate the .asmx file created by the BizTalk Web Services Publishing Wizard.</span></span><br /><br /> <span data-ttu-id="9bea9-145">Le format de ce message est similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9bea9-145">The format of this message is similar to the following:</span></span><br /><br /> <span data-ttu-id="9bea9-146">/BonDeCommande/OrganisationBDC.asmx</span><span class="sxs-lookup"><span data-stu-id="9bea9-146">/PurchaseOrder/POOrchestration.asmx</span></span><br /><br /> <span data-ttu-id="9bea9-147">Où l'emplacement complet du fichier .asmx est http://localhost/BonDeCommande/OrchestrationBDC.asmx.</span><span class="sxs-lookup"><span data-stu-id="9bea9-147">Where the full location of the .asmx file is http://localhost/PurchaseOrder/POOrchestration.asmx.</span></span> <span data-ttu-id="9bea9-148">**Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="9bea9-148">**Note:**  The URI for a send port or receive location cannot exceed 256 characters.</span></span>|  
    |<span data-ttu-id="9bea9-149">**Adresse publique**</span><span class="sxs-lookup"><span data-stu-id="9bea9-149">**Public address**</span></span>|<span data-ttu-id="9bea9-150">Indiquer l'adresse URI complète de cet emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="9bea9-150">Specify the fully qualified URI for this receive location.</span></span> <span data-ttu-id="9bea9-151">La valeur de cette propriété est constituée du nom du serveur et de celui du répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="9bea9-151">The value for this property is a combination of the server name and the virtual directory.</span></span> <span data-ttu-id="9bea9-152">L'URI indiquée doit désigner l'URL du site Web public de manière à ce que les partenaires commerciaux puissent s'y connecter lors de l'envoi de messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bea9-152">The specified URI should designate the public Web site URL for trading partners to connect to when sending messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="9bea9-153">Ces informations sont facultatives et ne sont pas utilisées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bea9-153">This information is optional and is not used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="9bea9-154">Ce paramètre est disponible pour permettre aux administrateurs de documenter l'URL publique à laquelle est lié l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="9bea9-154">This parameter is available to allow administrators to document the public URL that the receive location is tied to.</span></span>|  
    |<span data-ttu-id="9bea9-155">**Utiliser l’authentification unique**</span><span class="sxs-lookup"><span data-stu-id="9bea9-155">**Use Single Sign-On**</span></span>|<span data-ttu-id="9bea9-156">Indiquer que l'adaptateur SOAP utilise l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9bea9-156">Indicate that the SOAP adapter uses Enterprise Single Sign-On.</span></span> <span data-ttu-id="9bea9-157">**Remarque :** l’Assistant de publication des Services Web BizTalk vous permet d’utiliser SharePoint Portal Server Single Sign-On ; cette propriété active seulement Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="9bea9-157">**Note:**  The BizTalk Web Services Publishing Wizard allows you to use SharePoint Portal Server Single Sign-On; this property only enables Enterprise Single Sign-On.</span></span>|  
  
6.  <span data-ttu-id="9bea9-158">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-158">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="9bea9-159">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, entrez les valeurs appropriées pour terminer la configuration de l’emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres.</span><span class="sxs-lookup"><span data-stu-id="9bea9-159">In the **Receive Location Properties** dialog box, enter the appropriate values to complete the configuration of the receive location, and then click **OK** to save settings.</span></span> <span data-ttu-id="9bea9-160">Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="9bea9-160">For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
 <span data-ttu-id="9bea9-161">Les paramètres de sécurité utilisés par l'emplacement de réception SOAP sont définis dans IIS.</span><span class="sxs-lookup"><span data-stu-id="9bea9-161">The security settings used by the SOAP receive location are set in IIS.</span></span> <span data-ttu-id="9bea9-162">Par défaut, l'emplacement de réception SOAP n'est pas configuré pour utiliser l'authentification anonyme.</span><span class="sxs-lookup"><span data-stu-id="9bea9-162">By default, the SOAP receive location is not set to use anonymous authentication.</span></span>  
  
 <span data-ttu-id="9bea9-163">Tandis que le client SOAP appelle le service Web, l'adaptateur SOAP authentifie le client à l'aide de l'authentification Anonyme, De base, Digest ou Intégrée Windows.</span><span class="sxs-lookup"><span data-stu-id="9bea9-163">While the SOAP client calls the Web service, the SOAP adapter authenticates the SOAP client by using either Anonymous, Basic, Digest, or Windows Integrated authentication.</span></span> <span data-ttu-id="9bea9-164">Si la vérification de l'utilisateur est activée, le contexte utilisateur est transmis au gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="9bea9-164">If the user is verified, the user context is passed to the receive handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bea9-165">Toute configuration IIS menant au partage du même processus par SOAP et HTTP est non valide.</span><span class="sxs-lookup"><span data-stu-id="9bea9-165">Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid.</span></span> <span data-ttu-id="9bea9-166">Vous ne pouvez utiliser qu'un seul récepteur isolé par processus.</span><span class="sxs-lookup"><span data-stu-id="9bea9-166">You can have only one isolated receiver per process.</span></span>  
  
### <a name="to-update-a-virtual-directory-to-use-aspnet-40"></a><span data-ttu-id="9bea9-167">Pour mettre à jour un répertoire virtuel pour utiliser ASP.NET 4.0</span><span class="sxs-lookup"><span data-stu-id="9bea9-167">To update a virtual directory to use ASP.NET 4.0</span></span>  
  
1.  <span data-ttu-id="9bea9-168">Lancez le Gestionnaire des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="9bea9-168">Launch the Internet Information Services (IIS) Manager.</span></span> <span data-ttu-id="9bea9-169">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-169">Click **Start**, click **All Programs**, and click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="9bea9-170">Si vous avez besoin pour se connecter à un serveur IIS distant, bouton droit sur le **Internet Information Services** nœud, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-170">If you need to connect to a remote IIS server, right click the **Internet Information Services** node and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="9bea9-171">Tapez le nom d'ordinateur du serveur IIS distant et les informations d'identification, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="9bea9-171">Type the computer name for the remote IIS server and credentials if necessary.</span></span>  
  
4.  <span data-ttu-id="9bea9-172">Développez le nom du serveur qui héberge le site Web ou le répertoire virtuel à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="9bea9-172">Expand the server name that houses the Web site or virtual directory to be updated.</span></span>  
  
5.  <span data-ttu-id="9bea9-173">Développez **Sites**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-173">Expand **Sites**.</span></span>  
  
6.  <span data-ttu-id="9bea9-174">Développez **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-174">Expand **Default Web Site**.</span></span>  
  
7.  <span data-ttu-id="9bea9-175">Développez le site Web par défaut pour afficher les répertoires virtuels sous le site Web.</span><span class="sxs-lookup"><span data-stu-id="9bea9-175">Expand the Default Web site to view the virtual directories under the Web site.</span></span>  
  
8.  <span data-ttu-id="9bea9-176">Cliquez sur le répertoire virtuel que vous souhaitez mettre à jour pour utiliser ASP.NET 4.0, cliquez sur **gérer l’Application**, puis cliquez sur **paramètres avancés**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-176">Right-click the virtual directory that you want to update to use ASP.NET 4.0, click **Manage Application**, and then click **Advanced Settings**.</span></span> <span data-ttu-id="9bea9-177">Le **Pool d’applications** champ affiche le pool d’applications défini pour le répertoire virtuel sélectionné.</span><span class="sxs-lookup"><span data-stu-id="9bea9-177">The **Application Pool** field displays the application pool set for the selected virtual directory.</span></span> <span data-ttu-id="9bea9-178">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-178">Click **OK**.</span></span>  
  
9. <span data-ttu-id="9bea9-179">Dans la fenêtre Gestionnaire des Services Internet (IIS), cliquez sur **Pools d’applications**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-179">In the Internet Information Services (IIS) Manager window, click **Application Pools**.</span></span> <span data-ttu-id="9bea9-180">Le volet Détails affiche la liste des pools d'applications sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="9bea9-180">The details pane displays a list of application pools on the server.</span></span>  
  
10. <span data-ttu-id="9bea9-181">Cliquez sur le pool d’applications défini à l’étape 8, puis cliquez sur **les paramètres de base**.</span><span class="sxs-lookup"><span data-stu-id="9bea9-181">Right-click the application pool set in step 8, and then click **Basic Settings**.</span></span>  
  
11. <span data-ttu-id="9bea9-182">Dans le **modifier le Pool d’applications** boîte de dialogue zone, modifier les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="9bea9-182">In the **Edit Application Pool** dialog box, change the following:</span></span>  
  
    -   <span data-ttu-id="9bea9-183">**Version du .NET framework** à **4.0**</span><span class="sxs-lookup"><span data-stu-id="9bea9-183">**.NET Framework version** to **4.0**</span></span>  
  
    -   <span data-ttu-id="9bea9-184">**Mode pipeline géré** à **classique**</span><span class="sxs-lookup"><span data-stu-id="9bea9-184">**Managed pipeline mode** to **Classic**</span></span>  
  
12. <span data-ttu-id="9bea9-185">Cliquez sur **OK** pour appliquer les modifications.</span><span class="sxs-lookup"><span data-stu-id="9bea9-185">Click **OK** to apply the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bea9-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bea9-186">See Also</span></span>  
 [<span data-ttu-id="9bea9-187">Utilisation de Services Web</span><span class="sxs-lookup"><span data-stu-id="9bea9-187">Consuming Web Services</span></span>](../core/consuming-web-services.md)