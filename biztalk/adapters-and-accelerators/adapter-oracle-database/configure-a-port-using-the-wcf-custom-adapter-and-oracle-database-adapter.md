---
title: "Configurer un port à l’aide de l’adaptateur de base de données Oracle et un adaptateur WCF-custom | Documents Microsoft"
description: "Création d’envoi WCF-custom et ports de réception pour utiliser l’adaptateur de base de données Oracle dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c99ff526-ad97-4095-812f-0ce88b071e7f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7831ab57e7cae268aa1f47f380c69ef854b092b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter"></a><span data-ttu-id="6c728-103">Configurer un port à l’aide de l’adaptateur de base de données Oracle et un adaptateur WCF-custom</span><span class="sxs-lookup"><span data-stu-id="6c728-103">Configure a port using the WCF-custom adapter and Oracle Database adapter</span></span>
<span data-ttu-id="6c728-104">La configuration d’envoi WCF-Custom et de ports de réception pour effectuer des opérations de trafic entrantes et sortantes sur la base de données Oracle à l’aide du [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c728-104">How to configure WCF-Custom send and receive ports to perform outbound and inbound operations on the Oracle database using the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6c728-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6c728-105">Prerequisites</span></span>  
<span data-ttu-id="6c728-106">Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c728-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="6c728-107">Consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) pour obtenir des conseils d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="6c728-107">See [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) for permissions guidance.</span></span>
  
## <a name="deploy-adapters-for-sending-messages-to-an-oracle-database"></a><span data-ttu-id="6c728-108">Déployer les adaptateurs d’envoi de messages à une base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="6c728-108">Deploy adapters for sending messages to an Oracle database</span></span>  
  
1.  <span data-ttu-id="6c728-109">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="6c728-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="6c728-110">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="6c728-110">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="6c728-111">Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c728-111">Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="6c728-112">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis pointez sur un type de port que vous souhaitez configurer en fonction du mode de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6c728-112">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the Oracle database.</span></span>  
  
5.  <span data-ttu-id="6c728-113">Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="6c728-113">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6.  <span data-ttu-id="6c728-114">À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="6c728-114">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="6c728-115">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c728-115">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="6c728-116">Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6c728-116">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the Oracle database.</span></span> <span data-ttu-id="6c728-117">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="6c728-117">For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
    2.  <span data-ttu-id="6c728-118">Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="6c728-118">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="6c728-119">Consultez [Messages et des schémas de Message](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) pour obtenir la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="6c728-119">See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) for a list of actions for each operation.</span></span> <span data-ttu-id="6c728-120">Par exemple, l’action à appeler l’opération d’insertion une table d’employés sous le schéma de ressources humaines dans une base de données Oracle est :</span><span class="sxs-lookup"><span data-stu-id="6c728-120">For example, the action to invoke the Insert operation an EMPLOYEE table under the HR schema in an Oracle database is:</span></span>  
  
        ```  
        http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEE/Select  
        ```  
  
    3.  <span data-ttu-id="6c728-121">Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="6c728-121">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span> <span data-ttu-id="6c728-122">Vous pouvez spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c728-122">You can specify the different binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="6c728-123">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6c728-123">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
    4.  <span data-ttu-id="6c728-124">Cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c728-124">Click the **Credentials** tab and do one of the following:</span></span>  
  
        -   <span data-ttu-id="6c728-125">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à une base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6c728-125">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.</span></span>  
  
            -   <span data-ttu-id="6c728-126">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="6c728-126">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
            -   <span data-ttu-id="6c728-127">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="6c728-127">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
        -   <span data-ttu-id="6c728-128">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application d’authentification unique associée.</span><span class="sxs-lookup"><span data-stu-id="6c728-128">Select the **Use Single Sign-On** option, and specify an affiliate SSO application.</span></span>  
  
         <span data-ttu-id="6c728-129">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur de base de données Oracle et BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="6c728-129">For more information about security with respect to BizTalk Server, see [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).</span></span>  
  
         <span data-ttu-id="6c728-130">Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c728-130">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="6c728-131">À partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="6c728-131">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="6c728-132">Si vous avez choisi **Port d’envoi unidirectionnel statique** à l’étape 4, spécifiez un pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="6c728-132">If you chose **Static One-Way Send Port** in step 4, specify a send pipeline.</span></span> <span data-ttu-id="6c728-133">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline qui correspond à XMLTransmit.</span><span class="sxs-lookup"><span data-stu-id="6c728-133">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
10. <span data-ttu-id="6c728-134">Si vous avez choisi **Port statique avec sollicitation-réponse** à l’étape 4, spécifiez l’envoi et les pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="6c728-134">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="6c728-135">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline qui correspond à XMLTransmit.</span><span class="sxs-lookup"><span data-stu-id="6c728-135">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="6c728-136">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline qui correspond à XMLReceive.</span><span class="sxs-lookup"><span data-stu-id="6c728-136">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
11. <span data-ttu-id="6c728-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c728-137">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-for-receiving-messages-from-an-oracle-database"></a><span data-ttu-id="6c728-138">Déployer les adaptateurs de réception de messages à partir d’une base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="6c728-138">Deploy adapters for receiving messages from an Oracle database</span></span>  
  
1.  <span data-ttu-id="6c728-139">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="6c728-139">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="6c728-140">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="6c728-140">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="6c728-141">Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c728-141">Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="6c728-142">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel** ou **Receive Port requête-réponse**, en fonction de la mode de communication entre BizTalk Server et la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6c728-142">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between BizTalk Server and the Oracle database.</span></span>  
  
5.  <span data-ttu-id="6c728-143">Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="6c728-143">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6.  <span data-ttu-id="6c728-144">Sur le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="6c728-144">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="6c728-145">Le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6c728-145">The **Receive Location Properties** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="6c728-146">Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c728-146">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="6c728-147">Spécifiez un nom pour l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="6c728-147">Specify a name for the receive location.</span></span>  
  
    2.  <span data-ttu-id="6c728-148">À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="6c728-148">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="6c728-149">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c728-149">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="6c728-150">Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6c728-150">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the Oracle database.</span></span> <span data-ttu-id="6c728-151">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="6c728-151">For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
    2.  <span data-ttu-id="6c728-152">Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="6c728-152">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span> <span data-ttu-id="6c728-153">Vous pouvez spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c728-153">You can specify the different binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="6c728-154">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6c728-154">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
    3.  <span data-ttu-id="6c728-155">Cliquez sur le **d’autres** onglet, puis effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c728-155">Click the **Others** tab, and do one of the following:</span></span>  
  
        -   <span data-ttu-id="6c728-156">Sélectionnez **compte d’utilisateur**et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à une base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6c728-156">Select **User account**, and specify the user name and password to connect to an Oracle database.</span></span>  
  
            -   <span data-ttu-id="6c728-157">Pour vous connecter à l’aide des informations d’identification de base de données Oracle, tapez les informations d’identification de base de données dans le **nom d’utilisateur** et **mot de passe** zones de texte.</span><span class="sxs-lookup"><span data-stu-id="6c728-157">To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.</span></span>  
  
            -   <span data-ttu-id="6c728-158">Pour vous connecter à l’aide de l’authentification Windows, tapez  **/**  dans les **nom d’utilisateur** zone de texte et de laisser le **mot de passe** zone de texte vide.</span><span class="sxs-lookup"><span data-stu-id="6c728-158">To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.</span></span>  
  
        -   <span data-ttu-id="6c728-159">Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application associée.</span><span class="sxs-lookup"><span data-stu-id="6c728-159">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
         <span data-ttu-id="6c728-160">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur de base de données Oracle et BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="6c728-160">For more information about security with respect to BizTalk Server, see [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).</span></span>
  
         <span data-ttu-id="6c728-161">Pour revenir à la **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c728-161">To return to the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="6c728-162">À partir de la **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="6c728-162">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="6c728-163">Si vous avez choisi **Port de réception unidirectionnel** à l’étape 4, spécifiez un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="6c728-163">If you chose **One-way Receive Port** in step 4, specify a receive pipeline.</span></span> <span data-ttu-id="6c728-164">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.</span><span class="sxs-lookup"><span data-stu-id="6c728-164">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="6c728-165">Si vous avez choisi **Receive Port requête-réponse** à l’étape 4, spécifiez l’envoi et les pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="6c728-165">If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="6c728-166">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline qui correspond à XMLReceive.</span><span class="sxs-lookup"><span data-stu-id="6c728-166">From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="6c728-167">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline qui correspond à XMLTransmit.</span><span class="sxs-lookup"><span data-stu-id="6c728-167">From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.</span></span>  
  
12. <span data-ttu-id="6c728-168">Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c728-168">In the **Receive Location Properties** dialog box, click **OK**.</span></span>  
  
13. <span data-ttu-id="6c728-169">Dans le **propriétés du Port de réception** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c728-169">In the **Receive Port Properties** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c728-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c728-170">See Also</span></span>  
<span data-ttu-id="6c728-171">[Configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6c728-171">[Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md) </span></span>  
 [<span data-ttu-id="6c728-172">Se connecter à la base de données Oracle à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="6c728-172">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)