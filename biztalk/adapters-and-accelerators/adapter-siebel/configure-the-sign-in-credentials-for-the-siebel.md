---
title: "Configurer l’authentification dans les informations d’identification pour le Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, specify credentials for the Siebel system at run time
- credentials, specifying
- how to, specify credentials for the Siebel system at design time
ms.assetid: a9fef2ba-c38e-44f7-84a3-b6a95d4dc210
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e29f79830a3b76c094ebf8b70d533bfd36218f95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-siebel"></a><span data-ttu-id="3970f-102">Configurer l’authentification dans les informations d’identification pour le Siebel</span><span class="sxs-lookup"><span data-stu-id="3970f-102">Configure the sign in credentials for the Siebel</span></span>
<span data-ttu-id="3970f-103">Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] demande que les clients de l’adaptateur fournir des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="3970f-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="3970f-104">L’adaptateur utilise ces informations d’identification pour authentifier l’utilisateur avec le système Siebel et pour établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="3970f-104">The adapter uses these credentials to authenticate the user with the Siebel system and to establish a connection.</span></span>  
  
 <span data-ttu-id="3970f-105">Les clients de l’adaptateur peuvent fournir au client des informations d’identification au moment du design ou d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3970f-105">Adapter clients can provide the client credentials either at design time or run time.</span></span> <span data-ttu-id="3970f-106">Au moment du design, les informations d’identification sont requises pour générer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3970f-106">At design time, credentials are required to generate the metadata.</span></span> <span data-ttu-id="3970f-107">Au moment de l’exécution, les informations d’identification sont requises pour effectuer des opérations sur le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3970f-107">At run time, credentials are required to perform operations on the Siebel system.</span></span> <span data-ttu-id="3970f-108">Cette section fournit des informations sur la spécification des informations d’identification du client au moment du design et le moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3970f-108">This section provides information about specifying client credentials at design time and run time.</span></span>  
  
## <a name="enter-the-client-credentials-at-design-time"></a><span data-ttu-id="3970f-109">Entrez les informations d’identification du client au moment du design</span><span class="sxs-lookup"><span data-stu-id="3970f-109">Enter the client credentials at design time</span></span>  
 <span data-ttu-id="3970f-110">Pour le moment du design, vous devez spécifier les informations d’identification à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3970f-110">For design time, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="enter-client-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="3970f-111">Entrez les informations d’identification du client à l’aide de complément Consume Adapter Service</span><span class="sxs-lookup"><span data-stu-id="3970f-111">Enter client credentials using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="3970f-112">Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="3970f-112">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="3970f-113">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3970f-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="3970f-114">Utiliser</span><span class="sxs-lookup"><span data-stu-id="3970f-114">Use this</span></span>|<span data-ttu-id="3970f-115">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="3970f-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3970f-116">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="3970f-116">**Categories**</span></span>|<span data-ttu-id="3970f-117">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="3970f-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="3970f-118">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="3970f-118">**Templates**</span></span>|<span data-ttu-id="3970f-119">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="3970f-119">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="3970f-120">Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="3970f-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="3970f-121">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **siebelBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3970f-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **siebelBinding**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="3970f-122">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3970f-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.</span></span>  
  
6.  <span data-ttu-id="3970f-123">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3970f-123">Click **OK**.</span></span>  
  
#### <a name="enter-client-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="3970f-124">Entrez les informations d’identification du client à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="3970f-124">Enter client credentials using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="3970f-125">Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="3970f-125">Right-click your BizTalk project, point to **Add**, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="3970f-126">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3970f-126">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="3970f-127">Utiliser</span><span class="sxs-lookup"><span data-stu-id="3970f-127">Use this</span></span>|<span data-ttu-id="3970f-128">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="3970f-128">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3970f-129">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="3970f-129">**Categories**</span></span>|<span data-ttu-id="3970f-130">Cliquez sur **ajouter l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="3970f-130">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="3970f-131">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="3970f-131">**Templates**</span></span>|<span data-ttu-id="3970f-132">Cliquez sur **ajouter les métadonnées de l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="3970f-132">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="3970f-133">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="3970f-133">Click **Add**.</span></span> <span data-ttu-id="3970f-134">Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="3970f-134">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="3970f-135">Dans l’Assistant Ajout d’adaptateur, sélectionnez **WCF-Siebel**.</span><span class="sxs-lookup"><span data-stu-id="3970f-135">In the Add Adapter Wizard, select **WCF-Siebel**.</span></span> <span data-ttu-id="3970f-136">Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3970f-136">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3970f-137">Si vous disposez déjà d’un port WCF-Siebel configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.</span><span class="sxs-lookup"><span data-stu-id="3970f-137">If you already have a WCF-Siebel port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="3970f-138">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="3970f-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3970f-139">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **siebelBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3970f-139">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **siebelBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="3970f-140">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3970f-140">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Siebel system.</span></span>  
  
8.  <span data-ttu-id="3970f-141">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3970f-141">Click **OK**.</span></span>  
  
## <a name="enter-client-credentials-at-run-time"></a><span data-ttu-id="3970f-142">Entrez les informations d’identification du client au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="3970f-142">Enter client credentials at run time</span></span>  
 <span data-ttu-id="3970f-143">Temps d’exécution, vous devez spécifier les informations d’identification du client dans le cadre de la configuration du port WCF-Custom ou WCF-Siebel dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="3970f-143">For run time, you must specify the client credentials as part of the WCF-Custom or WCF-Siebel port configuration in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
#### <a name="enter-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="3970f-144">Entrez les informations d’identification pour le port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="3970f-144">Enter credentials for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="3970f-145">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="3970f-145">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="3970f-146">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** .</span><span class="sxs-lookup"><span data-stu-id="3970f-146">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="3970f-147">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="3970f-147">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="3970f-148">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3970f-148">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="3970f-149">Pour un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3970f-149">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="3970f-150">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3970f-150">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  
  
    -   <span data-ttu-id="3970f-151">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.</span><span class="sxs-lookup"><span data-stu-id="3970f-151">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  
  
5.  <span data-ttu-id="3970f-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3970f-152">Click **OK**.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="3970f-153">prend également en charge le système d’entreprise unique de session de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="3970f-153"> also supports the Enterprise Single Sign-On (ESSO) system.</span></span> <span data-ttu-id="3970f-154">L’entreprise est uniquement applicable dans le scénario de BizTalk, dans lequel l’adaptateur WCF est prenant en charge des applications associées de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="3970f-154">ESSO is only applicable in the BizTalk scenario, in which the WCF adapter is aware of ESSO affiliate applications.</span></span> <span data-ttu-id="3970f-155">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="3970f-155">For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span></span>
  
#### <a name="enter-credentials-for-the-wcf-siebel-port"></a><span data-ttu-id="3970f-156">Entrez les informations d’identification pour le port WCF-Siebel</span><span class="sxs-lookup"><span data-stu-id="3970f-156">Enter credentials for the WCF-Siebel port</span></span>  
  
1.  <span data-ttu-id="3970f-157">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="3970f-157">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="3970f-158">Ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="3970f-158">Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="3970f-159">Pour obtenir des instructions, consultez [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="3970f-159">For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="3970f-160">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** .</span><span class="sxs-lookup"><span data-stu-id="3970f-160">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and then click **Send Ports**.</span></span> <span data-ttu-id="3970f-161">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="3970f-161">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="3970f-162">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez le port WCF-Siebel que vous avez ajouté précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3970f-162">In the port properties dialog box, from the **Type** drop-down list, select the WCF-Siebel port you added earlier, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="3970f-163">Pour un port d’envoi dans la boîte de dialogue Propriétés du transport, cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3970f-163">For a send port, in the transport properties dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="3970f-164">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3970f-164">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  
  
    -   <span data-ttu-id="3970f-165">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.</span><span class="sxs-lookup"><span data-stu-id="3970f-165">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  
  
6.  <span data-ttu-id="3970f-166">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3970f-166">Click **OK**.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]<span data-ttu-id="3970f-167">prend également en charge le système d’entreprise unique de session de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="3970f-167"> also supports the Enterprise Single Sign-On (ESSO) system.</span></span> <span data-ttu-id="3970f-168">L’entreprise est uniquement applicable dans le scénario de BizTalk, dans lequel l’adaptateur WCF est prenant en charge des applications associées de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="3970f-168">ESSO is only applicable in the BizTalk scenario, in which the WCF adapter is aware of ESSO affiliate applications.</span></span> <span data-ttu-id="3970f-169">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="3970f-169">For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3970f-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3970f-170">See Also</span></span>  
[<span data-ttu-id="3970f-171">Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="3970f-171">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)