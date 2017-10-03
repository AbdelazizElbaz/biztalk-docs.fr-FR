---
title: "Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur SAP dans BizTalk | Documents Microsoft"
description: "Créer un port personnalisé WCF pour envoyer ou recevoir des messages à partir de SAP à l’aide de l’adaptateur mySAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3962456-e9ac-4575-8266-b35e892dd428
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66770264e2f76a589080cf86476448c2716b8897
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-sap-adapter"></a><span data-ttu-id="771ae-103">Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="771ae-103">Configure a port using the WCF-custom adapter and SAP adapter</span></span>
<span data-ttu-id="771ae-104">Cette rubrique fournit des instructions sur la configuration d’envoi WCF-Custom et de ports de réception pour effectuer des opérations entrantes et sortantes sur le système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="771ae-104">This topic provides instructions on how to configure WCF-Custom send and receive ports to perform outbound and inbound operations on SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="771ae-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="771ae-105">Prerequisites</span></span>  
<span data-ttu-id="771ae-106">Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="771ae-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="771ae-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [autorisations de sécurité minimales](../../core/minimum-security-user-rights.md).</span><span class="sxs-lookup"><span data-stu-id="771ae-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security User Rights](../../core/minimum-security-user-rights.md).</span></span> 
  
## <a name="deploy-adapters-to-send-messages-to-sap"></a><span data-ttu-id="771ae-108">Déployer des adaptateurs pour envoyer des messages à SAP</span><span class="sxs-lookup"><span data-stu-id="771ae-108">Deploy adapters to send messages to SAP</span></span>  
<span data-ttu-id="771ae-109">Complète les étapes suivantes pour configurer un WCF-Custom un port d’envoi pour envoyer des messages à l’aide de système SAP le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="771ae-109">Complete the following steps to configure a WCF-Custom send port for sending messages to SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1.  <span data-ttu-id="771ae-110">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="771ae-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="771ae-111">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="771ae-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="771ae-112">Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="771ae-112">Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="771ae-113">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, pointez sur un type de port que vous souhaitez configurer en fonction du mode de communication entre BizTalk Server et le système SAP.</span><span class="sxs-lookup"><span data-stu-id="771ae-113">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the SAP system.</span></span>  
  
5.  <span data-ttu-id="771ae-114">Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="771ae-114">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6.  <span data-ttu-id="771ae-115">À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="771ae-115">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="771ae-116">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="771ae-116">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="771ae-117">Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour le système SAP.</span><span class="sxs-lookup"><span data-stu-id="771ae-117">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the SAP system.</span></span> <span data-ttu-id="771ae-118">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="771ae-118">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
    2.  <span data-ttu-id="771ae-119">Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="771ae-119">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="771ae-120">Consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) pour obtenir la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="771ae-120">See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) for a list of actions for each operation.</span></span> <span data-ttu-id="771ae-121">Par exemple, l’action à appeler le RFC_CUSTOMER_GET serait :</span><span class="sxs-lookup"><span data-stu-id="771ae-121">For example, the action to invoke the RFC_CUSTOMER_GET would be:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    3.  <span data-ttu-id="771ae-122">Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**.</span><span class="sxs-lookup"><span data-stu-id="771ae-122">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span> <span data-ttu-id="771ae-123">Vous pouvez spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="771ae-123">You can specify the different binding properties exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="771ae-124">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="771ae-124">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    4.  <span data-ttu-id="771ae-125">Cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="771ae-125">Click the **Credentials** tab and do one of the following:</span></span>  
  
        -   <span data-ttu-id="771ae-126">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="771ae-126">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.</span></span>  
  
        -   <span data-ttu-id="771ae-127">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application d’authentification unique associée.</span><span class="sxs-lookup"><span data-stu-id="771ae-127">Select the **Use Single Sign-On** option, and specify an affiliate SSO application.</span></span>  
  
             <span data-ttu-id="771ae-128">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="771ae-128">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>
  
             <span data-ttu-id="771ae-129">Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="771ae-129">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="771ae-130">À partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="771ae-130">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="771ae-131">Si vous avez choisi de Port d’envoi unidirectionnel statique à l’étape 4, spécifiez un pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="771ae-131">If you chose Static One-Way Send Port in step 4, specify a send pipeline.</span></span> <span data-ttu-id="771ae-132">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.</span><span class="sxs-lookup"><span data-stu-id="771ae-132">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
10. <span data-ttu-id="771ae-133">Si vous avez choisi **Port statique avec sollicitation-réponse** à l’étape 4, spécifiez l’envoi et les pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="771ae-133">If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="771ae-134">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.</span><span class="sxs-lookup"><span data-stu-id="771ae-134">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="771ae-135">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.</span><span class="sxs-lookup"><span data-stu-id="771ae-135">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="771ae-136">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="771ae-136">Click **OK**.</span></span>  
  
## <a name="deploy-adapters-to-receive-messages-from-sap"></a><span data-ttu-id="771ae-137">Déployer des adaptateurs pour recevoir des messages à partir de SAP</span><span class="sxs-lookup"><span data-stu-id="771ae-137">Deploy adapters to receive messages from SAP</span></span>
<span data-ttu-id="771ae-138">Complète les étapes suivantes pour configurer un WCF-Custom port de réception pour recevoir des messages de système SAP à l’aide du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="771ae-138">Complete the following steps to configure a WCF-Custom receive port for receiving messages from SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1.  <span data-ttu-id="771ae-139">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="771ae-139">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="771ae-140">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="771ae-140">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="771ae-141">Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="771ae-141">Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="771ae-142">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel** ou **Receive Port requête-réponse** en fonction de la mode de communication entre BizTalk Server et le système SAP.</span><span class="sxs-lookup"><span data-stu-id="771ae-142">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port** depending on the mode of communication between BizTalk Server and the SAP system.</span></span>  
  
5.  <span data-ttu-id="771ae-143">Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="771ae-143">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6.  <span data-ttu-id="771ae-144">Sur le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="771ae-144">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="771ae-145">Le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="771ae-145">The **Receive Location Properties** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="771ae-146">Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="771ae-146">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="771ae-147">Spécifiez un nom pour l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="771ae-147">Specify a name for the receive location.</span></span>  
  
    2.  <span data-ttu-id="771ae-148">À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="771ae-148">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="771ae-149">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="771ae-149">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="771ae-150">Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour le système SAP.</span><span class="sxs-lookup"><span data-stu-id="771ae-150">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the SAP system.</span></span> <span data-ttu-id="771ae-151">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="771ae-151">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
    2.  <span data-ttu-id="771ae-152">Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**.</span><span class="sxs-lookup"><span data-stu-id="771ae-152">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span> <span data-ttu-id="771ae-153">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="771ae-153">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    3.  <span data-ttu-id="771ae-154">Cliquez sur le **d’autres** onglet, puis effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="771ae-154">Click the **Others** tab, and do one of the following:</span></span>  
  
        -   <span data-ttu-id="771ae-155">Sélectionnez **compte d’utilisateur**et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="771ae-155">Select **User account**, and specify the user name and password to connect to an SAP system.</span></span>  
  
        -   <span data-ttu-id="771ae-156">Sélectionnez **obtenir les informations d’identification d’applications associées à l’application** option et spécifiez une application associée.</span><span class="sxs-lookup"><span data-stu-id="771ae-156">Select **Get credentials from affiliate application** option, and specify an affiliate application.</span></span>  
  
             <span data-ttu-id="771ae-157">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="771ae-157">For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).</span></span>
  
             <span data-ttu-id="771ae-158">Cliquez sur **OK** pour revenir à la **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="771ae-158">Click **OK** to return to the **Receive Location Properties** dialog box.</span></span>  
  
9. <span data-ttu-id="771ae-159">À partir de la **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="771ae-159">From the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="771ae-160">Si vous avez choisi **Port de réception unidirectionnel** à l’étape 4, spécifiez un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="771ae-160">If you chose **One-way Receive Port** in step 4, specify a receive pipeline.</span></span> <span data-ttu-id="771ae-161">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.</span><span class="sxs-lookup"><span data-stu-id="771ae-161">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="771ae-162">Si vous avez choisi **Receive Port requête-réponse** à l’étape 4, spécifiez l’envoi et les pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="771ae-162">If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="771ae-163">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.</span><span class="sxs-lookup"><span data-stu-id="771ae-163">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
    2.  <span data-ttu-id="771ae-164">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.</span><span class="sxs-lookup"><span data-stu-id="771ae-164">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
12. <span data-ttu-id="771ae-165">Cliquez sur **OK i**n le **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="771ae-165">Click **OK i**n the **Receive Location Properties** dialog box.</span></span>  
  
13. <span data-ttu-id="771ae-166">Cliquez sur **OK** dans les **propriétés du Port de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="771ae-166">Click **OK** in the **Receive Port Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771ae-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="771ae-167">See Also</span></span>  
[<span data-ttu-id="771ae-168">Configurer manuellement une liaison de port physique à l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="771ae-168">Manually configure a physical port binding to the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)