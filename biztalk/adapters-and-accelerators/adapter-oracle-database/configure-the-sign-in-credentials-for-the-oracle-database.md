---
title: Configurer l’authentification dans les informations d’identification pour la base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Enter the credentials
helpviewer_keywords:
- credentials, specifying at run time
- credentials, specifying at design time
ms.assetid: d8f62829-ce77-4d82-a411-2eeefb6fe75a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eda20ad4e04a9962e471ab98eb0bc5695b391007
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-sign-in-credentials-for-the-oracle-database"></a><span data-ttu-id="8072a-102">Configurer l’authentification dans les informations d’identification pour la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="8072a-102">Configure the sign in credentials for the Oracle Database</span></span>
<span data-ttu-id="8072a-103">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] demande que les clients de l’adaptateur fournir des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="8072a-103">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] requires the adapter clients to provide client credentials.</span></span> <span data-ttu-id="8072a-104">L’adaptateur utilise ces informations d’identification pour authentifier l’utilisateur avec la base de données Oracle et pour établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="8072a-104">The adapter uses these credentials to authenticate the user with the Oracle database and to establish a connection.</span></span>  
  
 <span data-ttu-id="8072a-105">Les clients de l’adaptateur peuvent fournir au client les informations d’identification lors de l’utilisation [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et lorsque vous utilisez la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8072a-105">Adapter clients can provide the client credentials both when using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and when using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="8072a-106">Lorsque vous utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], informations d’identification sont requises pour générer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8072a-106">When using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], credentials are required to generate the metadata.</span></span> <span data-ttu-id="8072a-107">Lorsque vous utilisez la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, les informations d’identification sont requises pour effectuer des opérations sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8072a-107">When using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, credentials are required to perform operations on the Oracle database.</span></span> <span data-ttu-id="8072a-108">Cette rubrique fournit des informations sur la spécification des informations d’identification du client dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8072a-108">This topic provides information about specifying client credentials in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="specifying-client-credentials-from-visual-studio"></a><span data-ttu-id="8072a-109">Spécification des informations d’identification du Client à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8072a-109">Specifying Client Credentials from Visual Studio</span></span>  
 <span data-ttu-id="8072a-110">À partir de Visual Studio, vous devez spécifier les informations d’identification à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8072a-110">From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-specify-credentials-using-consume-adapter-service-add-in"></a><span data-ttu-id="8072a-111">Pour spécifier les informations d’identification à l’aide de complément Consume Adapter Service</span><span class="sxs-lookup"><span data-stu-id="8072a-111">To specify credentials using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="8072a-112">Avec le bouton droit de votre projet BizTalk, puis **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="8072a-112">Right-click your BizTalk project, and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="8072a-113">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8072a-113">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="8072a-114">Utiliser</span><span class="sxs-lookup"><span data-stu-id="8072a-114">Use this</span></span>|<span data-ttu-id="8072a-115">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="8072a-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8072a-116">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="8072a-116">**Categories**</span></span>|<span data-ttu-id="8072a-117">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="8072a-117">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="8072a-118">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="8072a-118">**Templates**</span></span>|<span data-ttu-id="8072a-119">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="8072a-119">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="8072a-120">Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8072a-120">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="8072a-121">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **oracleDBBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="8072a-121">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and click **Configure**.</span></span>  
  
5.  <span data-ttu-id="8072a-122">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** zone de liste déroulante, sélectionnez **nom d’utilisateur** et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à la base de données Oracle :</span><span class="sxs-lookup"><span data-stu-id="8072a-122">In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  
  
    -   <span data-ttu-id="8072a-123">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="8072a-123">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
    -   <span data-ttu-id="8072a-124">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="8072a-124">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
6.  <span data-ttu-id="8072a-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8072a-125">Click **OK**.</span></span>  
  
#### <a name="to-specify-credentials-using-add-adapter-metadata-wizard"></a><span data-ttu-id="8072a-126">Pour spécifier les informations d’identification à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="8072a-126">To specify credentials using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="8072a-127">Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="8072a-127">Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="8072a-128">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8072a-128">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="8072a-129">Utiliser</span><span class="sxs-lookup"><span data-stu-id="8072a-129">Use this</span></span>|<span data-ttu-id="8072a-130">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="8072a-130">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8072a-131">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="8072a-131">**Categories**</span></span>|<span data-ttu-id="8072a-132">Cliquez sur **ajouter l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="8072a-132">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="8072a-133">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="8072a-133">**Templates**</span></span>|<span data-ttu-id="8072a-134">Cliquez sur **ajouter les métadonnées de l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="8072a-134">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="8072a-135">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8072a-135">Click **Add**.</span></span> <span data-ttu-id="8072a-136">Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="8072a-136">The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.</span></span>  
  
4.  <span data-ttu-id="8072a-137">Dans le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], sélectionnez **WCF-OracleDB**.</span><span class="sxs-lookup"><span data-stu-id="8072a-137">In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleDB**.</span></span> <span data-ttu-id="8072a-138">Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8072a-138">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8072a-139">Si vous disposez déjà d’un port WCF-OracleDB configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.</span><span class="sxs-lookup"><span data-stu-id="8072a-139">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="8072a-140">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="8072a-140">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="8072a-141">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **oracleDBBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="8072a-141">In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="8072a-142">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** liste, sélectionnez **nom d’utilisateur** et Spécifiez le nom d’utilisateur et un mot de passe pour se connecter à la base de données Oracle :</span><span class="sxs-lookup"><span data-stu-id="8072a-142">In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle database:</span></span>  
  
    -   <span data-ttu-id="8072a-143">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="8072a-143">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
    -   <span data-ttu-id="8072a-144">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="8072a-144">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
8.  <span data-ttu-id="8072a-145">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8072a-145">Click **OK**.</span></span>  
  
## <a name="specifying-client-credentials-from-the-biztalk-server-administration-console"></a><span data-ttu-id="8072a-146">Spécification des informations d’identification du Client à partir de la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8072a-146">Specifying Client Credentials from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="8072a-147">À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez spécifier les informations d’identification dans le cadre de la configuration du port WCF-Custom ou WCF-OracleDB.</span><span class="sxs-lookup"><span data-stu-id="8072a-147">From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the credentials as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span>  
  
#### <a name="to-specify-client-credentials-for-the-wcf-custom-port"></a><span data-ttu-id="8072a-148">Pour spécifier les informations d’identification du client pour le Port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="8072a-148">To specify client credentials for the WCF-Custom Port</span></span>  
  
1.  <span data-ttu-id="8072a-149">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8072a-149">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8072a-150">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="8072a-150">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="8072a-151">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="8072a-151">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="8072a-152">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="8072a-152">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="8072a-153">Pour un port d’envoi dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8072a-153">For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="8072a-154">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à une base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8072a-154">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="8072a-155">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="8072a-155">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="8072a-156">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="8072a-156">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="8072a-157">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.</span><span class="sxs-lookup"><span data-stu-id="8072a-157">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
5.  <span data-ttu-id="8072a-158">Pour un port de réception dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **autres** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8072a-158">For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:</span></span>  
  
    -   <span data-ttu-id="8072a-159">Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à une base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8072a-159">Select **User account** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
        -   <span data-ttu-id="8072a-160">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="8072a-160">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="8072a-161">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="8072a-161">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="8072a-162">Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application associée.</span><span class="sxs-lookup"><span data-stu-id="8072a-162">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
6.  <span data-ttu-id="8072a-163">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8072a-163">Click **OK**.</span></span>  
  
#### <a name="to-specify-credentials-for-the-wcf-oracledb-port"></a><span data-ttu-id="8072a-164">Pour spécifier les informations d’identification pour le port WCF-OracleDB</span><span class="sxs-lookup"><span data-stu-id="8072a-164">To specify credentials for the WCF-OracleDB port</span></span>  
  
1.  <span data-ttu-id="8072a-165">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8072a-165">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="8072a-166">Ajouter l’adaptateur WCF-OracleDB à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="8072a-166">Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="8072a-167">Pour obtenir des instructions, consultez [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="8072a-167">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="8072a-168">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="8072a-168">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="8072a-169">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="8072a-169">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="8072a-170">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-OracleDB**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="8072a-170">In the port properties dialog box, from the **Type** drop-down list, select **WCF-OracleDB**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8072a-171">Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="8072a-171">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="8072a-172">Dans la boîte de dialogue Propriétés du port, cliquez sur le **liaison** onglet. À partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="8072a-172">In the port properties dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span>  
  
6.  <span data-ttu-id="8072a-173">Si vous créez un port d’envoi dans la boîte de dialogue des propriétés de transport, cliquez sur le **informations d’identification** onglet, puis effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8072a-173">If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="8072a-174">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8072a-174">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
        -   <span data-ttu-id="8072a-175">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="8072a-175">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="8072a-176">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="8072a-176">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="8072a-177">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une Enterprise Single Sign-on (SSO de) l’application associée.</span><span class="sxs-lookup"><span data-stu-id="8072a-177">Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.</span></span>  
  
7.  <span data-ttu-id="8072a-178">Si vous créez un port de réception dans la boîte de dialogue des propriétés de transport, cliquez sur le **autres** onglet, puis effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8072a-178">If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="8072a-179">Sélectionnez **compte d’utilisateur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="8072a-179">Select **User account** option, and specify the user name and password to connect to the Oracle database.</span></span>  
  
        -   <span data-ttu-id="8072a-180">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="8072a-180">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
        -   <span data-ttu-id="8072a-181">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="8072a-181">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
    -   <span data-ttu-id="8072a-182">Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application d’authentification unique associée.</span><span class="sxs-lookup"><span data-stu-id="8072a-182">Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.</span></span>  
  
8.  <span data-ttu-id="8072a-183">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8072a-183">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8072a-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8072a-184">See Also</span></span>  
<span data-ttu-id="8072a-185">[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span><span class="sxs-lookup"><span data-stu-id="8072a-185">[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) </span></span>  
 [<span data-ttu-id="8072a-186">Se connecter à la base de données Oracle à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="8072a-186">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)