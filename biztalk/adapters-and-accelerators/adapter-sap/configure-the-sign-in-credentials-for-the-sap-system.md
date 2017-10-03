---
title: "Configurer l’authentification dans les informations d’identification pour le système SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb41106b-b673-4fcf-a56e-6208e3113469
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a6ace75f66bb7fdd4cfb3362f7d019ab99d73bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-sap-system"></a><span data-ttu-id="23491-102">Configurer l’authentification dans les informations d’identification pour le système SAP</span><span class="sxs-lookup"><span data-stu-id="23491-102">Configure the sign in credentials for the SAP system</span></span>
<span data-ttu-id="23491-103">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] demande que les clients de l’adaptateur fournir des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="23491-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="23491-104">L’adaptateur utilise ces informations d’identification pour authentifier l’utilisateur avec le système SAP et pour établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="23491-104">The adapter uses these credentials to authenticate the user with the SAP system and to establish a connection.</span></span>  
  
 <span data-ttu-id="23491-105">Les clients de l’adaptateur peuvent fournir des informations d’identification à la fois le client au moment du design ou d’exécution.</span><span class="sxs-lookup"><span data-stu-id="23491-105">Adapter clients can provide the client credentials both at design time or run time.</span></span> <span data-ttu-id="23491-106">Au moment du design, les informations d’identification sont requises pour générer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="23491-106">At design time, credentials are required to generate the metadata.</span></span> <span data-ttu-id="23491-107">Au moment de l’exécution, les informations d’identification sont requises pour effectuer des opérations sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="23491-107">At run time, credentials are required to perform operations on the SAP system.</span></span> <span data-ttu-id="23491-108">Cette section fournit des informations sur la spécification des informations d’identification du client au moment du design et le moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="23491-108">This section provides information about specifying client credentials at design time and run time.</span></span>  
  
## <a name="enter-the-client-credentials-at-design-time"></a><span data-ttu-id="23491-109">Entrez les informations d’identification du client au moment du design</span><span class="sxs-lookup"><span data-stu-id="23491-109">Enter the client credentials at design time</span></span>  
 <span data-ttu-id="23491-110">Pour le moment du design, vous pouvez spécifier les informations d’identification à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23491-110">For design time, you can specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
### <a name="enter-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="23491-111">Entrez les informations d’identification à l’aide de complément Consume Adapter Service</span><span class="sxs-lookup"><span data-stu-id="23491-111">Enter credentials using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="23491-112">Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="23491-112">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="23491-113">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="23491-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="23491-114">Utiliser</span><span class="sxs-lookup"><span data-stu-id="23491-114">Use this</span></span>|<span data-ttu-id="23491-115">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="23491-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="23491-116">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="23491-116">**Categories**</span></span>|<span data-ttu-id="23491-117">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="23491-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="23491-118">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="23491-118">**Templates**</span></span>|<span data-ttu-id="23491-119">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="23491-119">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="23491-120">Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="23491-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="23491-121">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **sapBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="23491-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sapBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="23491-122">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="23491-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
6.  <span data-ttu-id="23491-123">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23491-123">Click **OK**.</span></span>  
  
### <a name="enter-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="23491-124">Entrez les informations d’identification à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="23491-124">Enter credentials using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="23491-125">Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="23491-125">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="23491-126">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="23491-126">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="23491-127">Utiliser</span><span class="sxs-lookup"><span data-stu-id="23491-127">Use this</span></span>|<span data-ttu-id="23491-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="23491-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="23491-129">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="23491-129">**Categories**</span></span>|<span data-ttu-id="23491-130">Cliquez sur **ajouter l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="23491-130">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="23491-131">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="23491-131">**Templates**</span></span>|<span data-ttu-id="23491-132">Cliquez sur **ajouter les métadonnées de l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="23491-132">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="23491-133">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="23491-133">Click **Add**.</span></span> <span data-ttu-id="23491-134">Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="23491-134">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="23491-135">Dans l’Assistant Ajout d’adaptateur, sélectionnez **WCF SAP**.</span><span class="sxs-lookup"><span data-stu-id="23491-135">In the Add Adapter Wizard, select **WCF-SAP**.</span></span> <span data-ttu-id="23491-136">Sélectionnez l’ordinateur sur lequel BizTalk Server est installé et le nom de la base de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="23491-136">Select the computer on which BizTalk Server is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="23491-137">Si vous disposez déjà d’un port WCF SAP configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.</span><span class="sxs-lookup"><span data-stu-id="23491-137">If you already have a WCF-SAP port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="23491-138">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="23491-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="23491-139">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **sapBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="23491-139">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **sapBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="23491-140">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="23491-140">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the SAP system.</span></span>  
  
8.  <span data-ttu-id="23491-141">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23491-141">Click **OK**.</span></span>  
  
## <a name="enter-client-credentials-at-run-time"></a><span data-ttu-id="23491-142">Entrez les informations d’identification du client au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="23491-142">Enter client credentials at run time</span></span>  
 <span data-ttu-id="23491-143">Temps d’exécution, vous pouvez spécifier les informations d’identification du client dans le cadre de la configuration du port WCF-Custom ou WCF-SAP dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="23491-143">For run time, you can specify the client credentials as part of the WCF-Custom or WCF-SAP port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
### <a name="enter-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="23491-144">Entrez les informations d’identification pour le port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="23491-144">Enter credentials for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="23491-145">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="23491-145">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="23491-146">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="23491-146">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="23491-147">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="23491-147">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="23491-148">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="23491-148">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23491-149">Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="23491-149">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="23491-150">Pour un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="23491-150">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="23491-151">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="23491-151">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="23491-152">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.</span><span class="sxs-lookup"><span data-stu-id="23491-152">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
5.  <span data-ttu-id="23491-153">Pour un port de réception dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **autres** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="23491-153">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="23491-154">Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="23491-154">Select **User account** option, and specify the user name and password to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="23491-155">Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application associée.</span><span class="sxs-lookup"><span data-stu-id="23491-155">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
6.  <span data-ttu-id="23491-156">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23491-156">Click **OK**.</span></span>  
  
### <a name="enter-credentials-for-the-wcf-sap-port"></a><span data-ttu-id="23491-157">Entrez les informations d’identification pour le port WCF SAP</span><span class="sxs-lookup"><span data-stu-id="23491-157">Enter credentials for the WCF-SAP port</span></span>  
  
1.  <span data-ttu-id="23491-158">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="23491-158">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="23491-159">Ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="23491-159">Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="23491-160">Pour obtenir des instructions, consultez [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="23491-160">For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="23491-161">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="23491-161">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="23491-162">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="23491-162">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="23491-163">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SAP que vous avez ajouté précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="23491-163">In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23491-164">Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="23491-164">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="23491-165">Si vous créez un port d’envoi dans la boîte de dialogue des propriétés de transport, cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="23491-165">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="23491-166">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="23491-166">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="23491-167">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.</span><span class="sxs-lookup"><span data-stu-id="23491-167">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
6.  <span data-ttu-id="23491-168">Si vous créez un port de réception dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **autres** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="23491-168">If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    1.  <span data-ttu-id="23491-169">Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système SAP.</span><span class="sxs-lookup"><span data-stu-id="23491-169">Select **User account** option, and specify the user name and password to connect to the SAP system.</span></span>  
  
    2.  <span data-ttu-id="23491-170">Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.</span><span class="sxs-lookup"><span data-stu-id="23491-170">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
7.  <span data-ttu-id="23491-171">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23491-171">Click **OK**.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="23491-172">prend également en charge le système Enterprise Single Sign-On (SSO).</span><span class="sxs-lookup"><span data-stu-id="23491-172"> also supports the Enterprise Single Sign-On (SSO) system.</span></span> <span data-ttu-id="23491-173">L’authentification unique est uniquement applicable dans le scénario de BizTalk, dans lequel le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] tient compte des applications associées SSO.</span><span class="sxs-lookup"><span data-stu-id="23491-173">SSO is only applicable in the BizTalk scenario, in which the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] is aware of SSO affiliate applications.</span></span> <span data-ttu-id="23491-174">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="23491-174">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="23491-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23491-175">See Also</span></span>  
[<span data-ttu-id="23491-176">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="23491-176">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)