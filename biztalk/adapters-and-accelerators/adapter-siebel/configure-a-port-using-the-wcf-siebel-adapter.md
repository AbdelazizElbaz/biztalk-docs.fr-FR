---
title: "Configurer un port à l’aide de l’adaptateur WCF-Siebel | Documents Microsoft"
description: "Créer des ports d’envoi WCF-Siebel pour utiliser l’adaptateur des Applications Siebel eBusiness dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6314104-c742-440c-b530-b5a82295353a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486e33b6c8f61a315548a84f145dc45824300710
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-siebel-adapter"></a><span data-ttu-id="3bcf6-103">Configurer un port à l’aide de l’adaptateur WCF-Siebel</span><span class="sxs-lookup"><span data-stu-id="3bcf6-103">Configure a port using the WCF-Siebel adapter</span></span>
<span data-ttu-id="3bcf6-104">Comment configurer les ports d’envoi WCF-Siebel pour effectuer des opérations sortantes sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3bcf6-104">How to configure WCF-Siebel send ports to perform outbound operations on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3bcf6-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3bcf6-105">Prerequisites</span></span>  
<span data-ttu-id="3bcf6-106">Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="3bcf6-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span><span class="sxs-lookup"><span data-stu-id="3bcf6-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
  
## <a name="deploy-adapters-for-sending-messages-to-a-siebel-system"></a><span data-ttu-id="3bcf6-108">Déployer les adaptateurs d’envoi de messages à un système Siebel</span><span class="sxs-lookup"><span data-stu-id="3bcf6-108">Deploy adapters for sending messages to a Siebel system</span></span>  
 <span data-ttu-id="3bcf6-109">Procédez comme suit pour configurer un port d’envoi WCF-Siebel pour envoyer des messages à un système Siebel en utilisant le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-109">Perform the following steps to configure a WCF-Siebel send port for sending messages to a Siebel system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
1.  <span data-ttu-id="3bcf6-110">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="3bcf6-111">Ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-111">Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="3bcf6-112">Pour obtenir des instructions, consultez [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf6-112">For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="3bcf6-113">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-113">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
4.  <span data-ttu-id="3bcf6-114">Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3bcf6-114">Expand the application under which you wish to deploy the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
5.  <span data-ttu-id="3bcf6-115">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, pointez sur un type de port que vous souhaitez configurer en fonction du mode de communication entre BizTalk Server et le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-115">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the Siebel system.</span></span>  
  
6.  <span data-ttu-id="3bcf6-116">Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-116">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
7.  <span data-ttu-id="3bcf6-117">À partir de la **Type** liste déroulante, sélectionnez le WCF-Siebel adaptateur vous ajouté précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-117">From the **Type** drop-down list, select the WCF-Siebel adapter you added earlier and click **Configure**.</span></span>  
  
8.  <span data-ttu-id="3bcf6-118">Dans la boîte de dialogue Propriétés du transport, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3bcf6-118">In the transport properties dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3bcf6-119">Cliquez sur le **général** , cliquez sur le **configurer** bouton et fournir des valeurs pour les paramètres de connexion.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-119">Click the **General** tab, click the **Configure** button, and provide values for the connection parameters.</span></span> <span data-ttu-id="3bcf6-120">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf6-120">For more information about the connection URI, see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  
  
    2.  <span data-ttu-id="3bcf6-121">Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-121">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="3bcf6-122">Consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) pour obtenir la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-122">See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation.</span></span> <span data-ttu-id="3bcf6-123">Par exemple, l’action à appeler l’opération d’insertion sur le composant de gestion de compte est :</span><span class="sxs-lookup"><span data-stu-id="3bcf6-123">For example, the action to invoke the Insert operation on the Account business component is:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    3.  <span data-ttu-id="3bcf6-124">Cliquez sur le **liaison** onglet et spécifier des valeurs pour les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-124">Click the **Binding** tab and specify values for the binding properties.</span></span> <span data-ttu-id="3bcf6-125">Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf6-125">For more information, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
    4.  <span data-ttu-id="3bcf6-126">Cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3bcf6-126">Click the **Credentials** tab and do one of the following:</span></span>  
  
        -   <span data-ttu-id="3bcf6-127">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-127">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  
  
        -   <span data-ttu-id="3bcf6-128">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-128">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  
  
         <span data-ttu-id="3bcf6-129">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="3bcf6-129">For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span></span>  
  
    5.  <span data-ttu-id="3bcf6-130">Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-130">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="3bcf6-131">À partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-131">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="3bcf6-132">Si vous avez choisi de Port d’envoi unidirectionnel statique à l’étape 5, spécifiez un pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-132">If you chose Static One-Way Send Port in step 5, specify a send pipeline.</span></span> <span data-ttu-id="3bcf6-133">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-133">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
11. <span data-ttu-id="3bcf6-134">Si vous avez choisi de Port statique avec sollicitation-réponse à l’étape 5, spécifiez l’envoi et les pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-134">If you chose Static Solicit-Response Port in step 5, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="3bcf6-135">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-135">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="3bcf6-136">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-136">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
12. <span data-ttu-id="3bcf6-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3bcf6-137">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcf6-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bcf6-138">See Also</span></span>  
[<span data-ttu-id="3bcf6-139">Configurer manuellement une liaison de port physique à l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="3bcf6-139">Manually configure a physical port binding to the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)