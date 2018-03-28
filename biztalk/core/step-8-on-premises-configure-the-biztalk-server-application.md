---
title: 'Étape 8 (en local) : Configurer l’Application BizTalk Server | Documents Microsoft'
ms.custom: ''
ms.date: 2015-12-08
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5109fb54-8453-444f-bc9c-070a65053397
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa411b7ca828a45aa0d5e58212bb48195c48180f
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="step-8-on-premises-configure-the-biztalk-server-application"></a><span data-ttu-id="65a5e-102">Étape 8 (en local) : Configurer l’Application BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="65a5e-102">Step 8 (On Premises): Configure the BizTalk Server Application</span></span>
<span data-ttu-id="65a5e-103">Lors de l’étape précédente, vous avez créé une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65a5e-103">In the previous step you created a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span> <span data-ttu-id="65a5e-104">Dans cette étape, vous allez générer, déployer et configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="65a5e-104">In this step, you’ll build, deploy, and configure the application.</span></span>  
  
## <a name="build-and-deploy-the-application"></a><span data-ttu-id="65a5e-105">Créer et déployer l'application</span><span class="sxs-lookup"><span data-stu-id="65a5e-105">Build and deploy the application</span></span>  
  
1.  <span data-ttu-id="65a5e-106">Dans Visual Studio, cliquez sur le nom de la solution dans l’Explorateur de solutions, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-106">In Visual Studio, right-click the solution name in the Solution Explorer, and click **Build**.</span></span>  
  
2.  <span data-ttu-id="65a5e-107">Le processus de déploiement requiert la signature avec un nom fort de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="65a5e-107">The deployment process requires that assembly is strongly signed.</span></span>  <span data-ttu-id="65a5e-108">Vous devez vous connecter à vos assemblys en associant le projet avec un fichier de clé de nom fort assembly.</span><span class="sxs-lookup"><span data-stu-id="65a5e-108">You must sign your assemblies by associating the project with a strong name assembly key file.</span></span>  
  
    1.  <span data-ttu-id="65a5e-109">Dans l’Explorateur de solutions, cliquez sur le **OrderProcessingDemo** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-109">In Solution Explorer, right-click the **OrderProcessingDemo** project, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="65a5e-110">Cliquez sur le **signature** et sélectionnez le **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="65a5e-110">Click the **Signing** tab, and select the **Sign the assembly** checkbox.</span></span>  
  
    3.  <span data-ttu-id="65a5e-111">Dans la liste déroulante de la **choisir un fichier de clé de nom fort** boîte, sélectionnez  **\<nouveau... \>**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-111">From the drop-down list in the **Choose a strong name key file** box, select **\<New…\>**.</span></span>  
  
    4.  <span data-ttu-id="65a5e-112">Dans le **créer une clé de nom fort** boîte de dialogue, entrez un nom pour le fichier de clé, par exemple `OrderProcessingDemo.snk`.</span><span class="sxs-lookup"><span data-stu-id="65a5e-112">In the **Create Strong Name Key** dialog box, enter a name for the key file, for example `OrderProcessingDemo.snk`.</span></span> <span data-ttu-id="65a5e-113">Désactivez la case à cocher pour protéger le fichier de clé avec un mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-113">Clear the checkbox for protecting the key file with a password, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="65a5e-114">Cliquez sur le **déploiement** onglet, dans la zone à droite de **nom de l’Application**, type `OrderProcessingDemo`.</span><span class="sxs-lookup"><span data-stu-id="65a5e-114">Click the **Deployment** tab, in the box to the right of **Application Name**, type `OrderProcessingDemo`.</span></span>  
  
4.  <span data-ttu-id="65a5e-115">Dans la liste déroulante dans la zone à droite de **redéployer**, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-115">From the drop-down list in the box to the right of **Redeploy**, select **True**.</span></span>  
  
5.  <span data-ttu-id="65a5e-116">Dans l’Explorateur de solutions, cliquez sur **OrderProcessingDemo**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-116">In Solution Explorer, right-click **OrderProcessingDemo**, and then click **Deploy**.</span></span>  <span data-ttu-id="65a5e-117">La fenêtre Sortie doit s'afficher :</span><span class="sxs-lookup"><span data-stu-id="65a5e-117">The Output window should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
## <a name="configure-the-application"></a><span data-ttu-id="65a5e-118">Configurez l'application</span><span class="sxs-lookup"><span data-stu-id="65a5e-118">Configure the application</span></span>  
  
1.  <span data-ttu-id="65a5e-119">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65a5e-119">Click **Start**, point to **All Programs**, point to **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="65a5e-120">Dans l’arborescence de la console, dans le volet gauche, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-120">In the console tree on the left pane, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="65a5e-121">Développez **groupe BizTalk**, développez **Applications**, développez **OrderProcessingDemo**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-121">Expand **BizTalk Group**, expand **Applications**, expand **OrderProcessingDemo**, and then click **Orchestrations**.</span></span> <span data-ttu-id="65a5e-122">Vous verrez que le **OrderProcessingDemo.OrderProcessing** orchestration est déployée.</span><span class="sxs-lookup"><span data-stu-id="65a5e-122">You will see that the **OrderProcessingDemo.OrderProcessing** orchestration is deployed.</span></span>  
  
4.  <span data-ttu-id="65a5e-123">Dans l’orchestration, vous avez créé un port logique (**ReceiveSO**) pour recevoir des messages à partir de la file d’attente du Bus de Service.</span><span class="sxs-lookup"><span data-stu-id="65a5e-123">In the orchestration, you created a logical port (**ReceiveSO**) to receive messages from the Service Bus Queue.</span></span> <span data-ttu-id="65a5e-124">Dans cette étape, vous allez créer un port de réception physique à mapper vers le port logique.</span><span class="sxs-lookup"><span data-stu-id="65a5e-124">In this step, you create a physical receive port to map to the logical port.</span></span>  
  
    1.  <span data-ttu-id="65a5e-125">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **OrderProcessingDemo** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-125">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
    2.  <span data-ttu-id="65a5e-126">Sous l'onglet **Général** , effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="65a5e-126">On the **General** tab, do the following:</span></span>  
  
        |<span data-ttu-id="65a5e-127">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-127">Use this</span></span>|<span data-ttu-id="65a5e-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-128">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-129">**Nom**</span><span class="sxs-lookup"><span data-stu-id="65a5e-129">**Name**</span></span>|<span data-ttu-id="65a5e-130">Type **ReceiveSO**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-130">Type **ReceiveSO**.</span></span>|  
        |<span data-ttu-id="65a5e-131">**Activer le routage des messages ayant échoué**</span><span class="sxs-lookup"><span data-stu-id="65a5e-131">**Enable routing for failed messages**</span></span>|<span data-ttu-id="65a5e-132">(désactivé)</span><span class="sxs-lookup"><span data-stu-id="65a5e-132">(clear)</span></span>|  
  
    3.  <span data-ttu-id="65a5e-133">Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-133">Click **Receive Locations**, and then click **New**.</span></span>  
  
    4.  <span data-ttu-id="65a5e-134">Dans la boîte de dialogue Emplacement de réception 1 - Propriétés d’emplacement de réception, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="65a5e-134">From Receive Location1 – Receive Location Properties dialog box, do the following:</span></span>  
  
        |<span data-ttu-id="65a5e-135">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-135">Use this</span></span>|<span data-ttu-id="65a5e-136">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-136">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-137">**Nom**</span><span class="sxs-lookup"><span data-stu-id="65a5e-137">**Name**</span></span>|<span data-ttu-id="65a5e-138">Type **ReceiveOrders_SO**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-138">Type **ReceiveOrders_SO**.</span></span>|  
        |<span data-ttu-id="65a5e-139">**Type**</span><span class="sxs-lookup"><span data-stu-id="65a5e-139">**Type**</span></span>|<span data-ttu-id="65a5e-140">Sélectionnez **SB-Messaging**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-140">Select **SB-Messaging**.</span></span>|  
        |<span data-ttu-id="65a5e-141">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="65a5e-141">**Receive handler**</span></span>|<span data-ttu-id="65a5e-142">Sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-142">Select **BizTalkServerApplication**.</span></span>|  
        |<span data-ttu-id="65a5e-143">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="65a5e-143">**Receive pipeline**</span></span>|<span data-ttu-id="65a5e-144">Sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-144">Select **XMLReceive**.</span></span>|  
  
    5.  <span data-ttu-id="65a5e-145">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-145">Click **Configure**.</span></span>  
  
    6.  <span data-ttu-id="65a5e-146">À partir de la boîte de dialogue Propriétés du Transport SB-Messaging, sur le **général** onglet, pour **file d’attente ou abonnement URL**, entrez **sb://mynamespace.servicebus.appfabriclabs.com/queueordersedi**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-146">From SB-Messaging Transport Properties dialog box, on the **General** tab, for **Queue or Subscription URL**, enter **sb://mynamespace.servicebus.appfabriclabs.com/queueordersedi**.</span></span> <span data-ttu-id="65a5e-147">Ici, *mynamespace* est l’espace de noms Service Bus et *file_attente_commandes_edi* est la file d’attente du Bus de Service que vous avez créé dans [étape 3 (pour Azure) : créer une file d’attente du Bus de Service](../core/step-3-for-azure-create-a-service-bus-queue.md).</span><span class="sxs-lookup"><span data-stu-id="65a5e-147">Here, *mynamespace* is the Service Bus namespace and *queueordersedi* is the Service Bus Queue that you created in [Step 3 (For Azure): Create a Service Bus Queue](../core/step-3-for-azure-create-a-service-bus-queue.md).</span></span>  
  
    7.  <span data-ttu-id="65a5e-148">À partir de la boîte de dialogue Propriétés du Transport SB-Messaging, sur le **authentification** onglet, spécifiez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="65a5e-148">From SB-Messaging Transport Properties dialog box, on the **Authentication** tab, specify the following values:</span></span>  
  
        |<span data-ttu-id="65a5e-149">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-149">Use this</span></span>|<span data-ttu-id="65a5e-150">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-150">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-151">**STS Uri de Service de contrôle d’accès**</span><span class="sxs-lookup"><span data-stu-id="65a5e-151">**Access Control Service STS Uri**</span></span>|<span data-ttu-id="65a5e-152">Type`https://mynamespace-sb.accesscontrol.appfabriclabs.com/`</span><span class="sxs-lookup"><span data-stu-id="65a5e-152">Type `https://mynamespace-sb.accesscontrol.appfabriclabs.com/`</span></span>|  
        |<span data-ttu-id="65a5e-153">**Nom de l’émetteur**</span><span class="sxs-lookup"><span data-stu-id="65a5e-153">**Issuer name**</span></span>|<span data-ttu-id="65a5e-154">Spécifiez le nom de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="65a5e-154">Specify the issuer name.</span></span> <span data-ttu-id="65a5e-155">En général, il est défini sur `owner`.</span><span class="sxs-lookup"><span data-stu-id="65a5e-155">Typically this is set to `owner`.</span></span>|  
        |<span data-ttu-id="65a5e-156">**Clé de l’émetteur**</span><span class="sxs-lookup"><span data-stu-id="65a5e-156">**Issuer key**</span></span>|<span data-ttu-id="65a5e-157">Spécifiez la clé de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="65a5e-157">Specify the issuer key.</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="65a5e-158">Vous pouvez obtenir les valeurs de l’émetteur de l’URL de la file d’attente, les URL des services ACS, nom et la clé à partir de la [portail de gestion Windows Azure CTP](http://go.microsoft.com/fwlink/p/?LinkId=202886).</span><span class="sxs-lookup"><span data-stu-id="65a5e-158">You can get the values for the Queue URL, ACS URL, issuer name and key from the [Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886).</span></span>  
  
    8.  <span data-ttu-id="65a5e-159">Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="65a5e-159">Click **OK** until you exit all the dialog boxes.</span></span>  
  
5.  <span data-ttu-id="65a5e-160">Dans l’orchestration, vous avez créé un port logique (**SendToSQL**) pour envoyer des messages à la **SalesOrder** table de base de données.</span><span class="sxs-lookup"><span data-stu-id="65a5e-160">In the orchestration, you created a logical port (**SendToSQL**) to send messages to the **SalesOrder** database table.</span></span> <span data-ttu-id="65a5e-161">Dans cette étape, vous allez créer un port d’envoi physique à mapper vers le port logique.</span><span class="sxs-lookup"><span data-stu-id="65a5e-161">In this step, you create a physical send port to map to the logical port.</span></span>  
  
    1.  <span data-ttu-id="65a5e-162">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **OrderProcessingDemo** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-162">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
    2.  <span data-ttu-id="65a5e-163">Sous l’onglet Général, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="65a5e-163">On the General tab, do the following:</span></span>  
  
        |<span data-ttu-id="65a5e-164">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-164">Use this</span></span>|<span data-ttu-id="65a5e-165">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-165">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-166">**Nom**</span><span class="sxs-lookup"><span data-stu-id="65a5e-166">**Name**</span></span>|<span data-ttu-id="65a5e-167">Type **SendToSQL**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-167">Type **SendToSQL**.</span></span>|  
        |<span data-ttu-id="65a5e-168">**Type**</span><span class="sxs-lookup"><span data-stu-id="65a5e-168">**Type**</span></span>|<span data-ttu-id="65a5e-169">Sélectionnez **WCF-SQL**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-169">Select **WCF-SQL**.</span></span>|  
        |<span data-ttu-id="65a5e-170">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="65a5e-170">**Send handler**</span></span>|<span data-ttu-id="65a5e-171">Sélectionnez **BizTAlkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-171">Select **BizTAlkServerApplication**.</span></span>|  
        |<span data-ttu-id="65a5e-172">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="65a5e-172">**Send pipeline**</span></span>|<span data-ttu-id="65a5e-173">Sélectionnez **PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-173">Select **PassThruTransmit**.</span></span>|  
  
    3.  <span data-ttu-id="65a5e-174">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-174">Click **Configure**.</span></span>  
  
    4.  <span data-ttu-id="65a5e-175">À partir des propriétés du Transport WCF-SQL, sur le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="65a5e-175">From WCF-SQL Transport Properties, on the **General** tab, do the following:</span></span>  
  
        |<span data-ttu-id="65a5e-176">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-176">Use this</span></span>|<span data-ttu-id="65a5e-177">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-177">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-178">**Adresse (URI)**</span><span class="sxs-lookup"><span data-stu-id="65a5e-178">**Address (URI)**</span></span>|<span data-ttu-id="65a5e-179">Type **MSSQL://Nom_Ordinateur/nom_instance_base_de_donn ées/nom_base_de_données**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-179">Type **mssql://computername/database_instance_name/databasename**.</span></span> <span data-ttu-id="65a5e-180">Par exemple, pour se connecter à un **DemoDB** de la base de données sur l’ordinateur local en cours d’exécution sous l’instance de base de données par défaut, entrez`mssql://.//DemoDB`</span><span class="sxs-lookup"><span data-stu-id="65a5e-180">For example, to connect to a **DemoDB** database on the local computer running under the default database instance, enter `mssql://.//DemoDB`</span></span><br /><br /> <span data-ttu-id="65a5e-181">Pour plus d’informations, consultez [créer l’URI de connexion SQL Server](../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="65a5e-181">For more information, see [Create the SQL Server connection URI](../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>|  
        |<span data-ttu-id="65a5e-182">**Action**</span><span class="sxs-lookup"><span data-stu-id="65a5e-182">**Action**</span></span>|<span data-ttu-id="65a5e-183">Type **TableOp/Insert/dbo/SalesOrder**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-183">Type **TableOp/Insert/dbo/SalesOrder**.</span></span>|  
  
    5.  <span data-ttu-id="65a5e-184">À partir des propriétés du Transport WCF-SQL, sur le **informations d’identification** onglet, sélectionnez **n’utilisez pas l’authentification unique sur**et spécifiez les informations d’identification (respecte la casse) pour se connecter à la base de données SQL Server que vous avez spécifié dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="65a5e-184">From WCF-SQL Transport Properties, on the **Credentials** tab, select **Do not use Single Sign-On**, and specify credentials (case-sensitive) to connect to the SQL Server database you specified in the connection string.</span></span> <span data-ttu-id="65a5e-185">Si vous souhaitez vous connecter à l’aide de l’authentification Windows, ne renseignez pas les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="65a5e-185">If you want to connect using Windows Authentication, leave the credentials blank.</span></span>  
  
    6.  <span data-ttu-id="65a5e-186">Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="65a5e-186">Click **OK** until you exit all the dialog boxes.</span></span>  
  
6.  <span data-ttu-id="65a5e-187">Dans l’orchestration, vous avez créé un port logique (**SendToFile**) pour envoyer des messages vers un emplacement de fichier partagé.</span><span class="sxs-lookup"><span data-stu-id="65a5e-187">In the orchestration, you created a logical port (**SendToFile**) to send messages to a shared file location.</span></span> <span data-ttu-id="65a5e-188">Dans cette étape, vous allez créer un port d’envoi physique à mapper vers le port logique.</span><span class="sxs-lookup"><span data-stu-id="65a5e-188">In this step, you create a physical send port to map to the logical port.</span></span>  
  
    1.  <span data-ttu-id="65a5e-189">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **OrderProcessingDemo** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-189">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
    2.  <span data-ttu-id="65a5e-190">Sous l’onglet Général, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="65a5e-190">On the General tab, do the following:</span></span>  
  
        |<span data-ttu-id="65a5e-191">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-191">Use this</span></span>|<span data-ttu-id="65a5e-192">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-192">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-193">**Nom**</span><span class="sxs-lookup"><span data-stu-id="65a5e-193">**Name**</span></span>|<span data-ttu-id="65a5e-194">Type **SendToFile**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-194">Type **SendToFile**.</span></span>|  
        |<span data-ttu-id="65a5e-195">**Type**</span><span class="sxs-lookup"><span data-stu-id="65a5e-195">**Type**</span></span>|<span data-ttu-id="65a5e-196">Sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-196">Select **File**.</span></span>|  
        |<span data-ttu-id="65a5e-197">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="65a5e-197">**Send handler**</span></span>|<span data-ttu-id="65a5e-198">Sélectionnez **BizTAlkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-198">Select **BizTAlkServerApplication**.</span></span>|  
        |<span data-ttu-id="65a5e-199">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="65a5e-199">**Send pipeline**</span></span>|<span data-ttu-id="65a5e-200">Sélectionnez **XML Transmit**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-200">Select **XML Transmit**.</span></span>|  
  
    3.  <span data-ttu-id="65a5e-201">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-201">Click **Configure**.</span></span>  
  
    4.  <span data-ttu-id="65a5e-202">Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="65a5e-202">From File Transport Properties, do the following:</span></span>  
  
        |<span data-ttu-id="65a5e-203">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-203">Use this</span></span>|<span data-ttu-id="65a5e-204">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-204">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-205">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="65a5e-205">**Receive folder**</span></span>|<span data-ttu-id="65a5e-206">Spécifier l’emplacement dans lequel vous souhaitez envoyer le message.</span><span class="sxs-lookup"><span data-stu-id="65a5e-206">Specify the location where you want to send the message.</span></span>|  
        |<span data-ttu-id="65a5e-207">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="65a5e-207">**File name**</span></span>|<span data-ttu-id="65a5e-208">Conserver **%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-208">Retain **%MessageID%.xml**.</span></span>|  
  
    5.  <span data-ttu-id="65a5e-209">Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="65a5e-209">Click **OK** until you exit all the dialog boxes.</span></span>  
  
7.  <span data-ttu-id="65a5e-210">Pour configurer l’application, vous devez maintenant lier le port logique et le port physique.</span><span class="sxs-lookup"><span data-stu-id="65a5e-210">You must now bind the physical and logical ports together to configure the application.</span></span>  
  
    1.  <span data-ttu-id="65a5e-211">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **OrderProcessingDemo**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-211">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **OrderProcessingDemo**, and then click **Configure**.</span></span>  
  
    2.  <span data-ttu-id="65a5e-212">Configurer l’application, dans le volet gauche, cliquez sur **OrderProcessing**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-212">From Configure Application, in the left pane, click **OrderProcessing**.</span></span>  
  
    3.  <span data-ttu-id="65a5e-213">Utilisez les valeurs du tableau suivant pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="65a5e-213">Use the values in the following table to configure the application.</span></span>  
  
        |<span data-ttu-id="65a5e-214">Utiliser</span><span class="sxs-lookup"><span data-stu-id="65a5e-214">Use this</span></span>|<span data-ttu-id="65a5e-215">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="65a5e-215">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="65a5e-216">Pour **hôte**</span><span class="sxs-lookup"><span data-stu-id="65a5e-216">For **Host**</span></span>|<span data-ttu-id="65a5e-217">Sélectionnez **BizTalkServerApplication**</span><span class="sxs-lookup"><span data-stu-id="65a5e-217">Select **BizTalkServerApplication**</span></span>|  
        |<span data-ttu-id="65a5e-218">Port logique **ReceiveSO**</span><span class="sxs-lookup"><span data-stu-id="65a5e-218">For logical port **ReceiveSO**</span></span>|<span data-ttu-id="65a5e-219">Sélectionner le port physique **ReceiveSO**</span><span class="sxs-lookup"><span data-stu-id="65a5e-219">Select physical port **ReceiveSO**</span></span>|  
        |<span data-ttu-id="65a5e-220">Port logique **SendToSQL**</span><span class="sxs-lookup"><span data-stu-id="65a5e-220">For logical port **SendToSQL**</span></span>|<span data-ttu-id="65a5e-221">Sélectionner le port physique **SendToSQL**</span><span class="sxs-lookup"><span data-stu-id="65a5e-221">Select physical port **SendToSQL**</span></span>|  
        |<span data-ttu-id="65a5e-222">Port logique **SendToFile**</span><span class="sxs-lookup"><span data-stu-id="65a5e-222">For logical port **SendToFile**</span></span>|<span data-ttu-id="65a5e-223">Sélectionner le port physique **SendToFile**</span><span class="sxs-lookup"><span data-stu-id="65a5e-223">Select physical port **SendToFile**</span></span>|  
  
    4.  <span data-ttu-id="65a5e-224">Cliquez sur **OK** pour enregistrer la configuration.</span><span class="sxs-lookup"><span data-stu-id="65a5e-224">Click **OK** to save the configuration.</span></span>  
  
## <a name="start-the-application"></a><span data-ttu-id="65a5e-225">Démarrer l’application</span><span class="sxs-lookup"><span data-stu-id="65a5e-225">Start the application</span></span>  
  
1.  <span data-ttu-id="65a5e-226">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **OrderProcessingDemo**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-226">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **OrderProcessingDemo**, and then click **Start**.</span></span>  
  
2.  <span data-ttu-id="65a5e-227">Dans la boîte de dialogue, cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="65a5e-227">From the dialog, click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a5e-228">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65a5e-228">See Also</span></span>  
 [<span data-ttu-id="65a5e-229">Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="65a5e-229">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)