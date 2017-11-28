---
title: "Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur Siebel dans BizTalk | Documents Microsoft"
description: "Création d’envoi WCF-custom et ports de réception pour utiliser l’adaptateur des Applications Siebel eBusiness dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53c5ee07-36ae-474b-9241-8b53c9066ca1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 485bfaf7bd958528630e96a64ca0129a56ec330d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-custom-adapter-and-siebel-adapter"></a><span data-ttu-id="f7bc0-103">Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="f7bc0-103">Configure a port using the WCF-custom adapter and Siebel adapter</span></span>
<span data-ttu-id="f7bc0-104">Cette rubrique fournit des instructions sur la configuration WCF-Custom ports d’envoi pour effectuer des opérations sortantes sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7bc0-104">This topic provides instructions on how to configure WCF-Custom send ports to perform outbound operations on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f7bc0-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f7bc0-105">Prerequisites</span></span>  
<span data-ttu-id="f7bc0-106">Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-106">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="f7bc0-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span><span class="sxs-lookup"><span data-stu-id="f7bc0-107">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
  
## <a name="deploying-adapters-for-sending-messages-to-a-siebel-system"></a><span data-ttu-id="f7bc0-108">Déploiement des adaptateurs d’envoi de Messages à un système Siebel</span><span class="sxs-lookup"><span data-stu-id="f7bc0-108">Deploying Adapters for Sending Messages to a Siebel System</span></span>  
 <span data-ttu-id="f7bc0-109">Procédez comme suit pour configurer un port d’envoi WCF-Custom pour envoyer des messages à un système Siebel en utilisant le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-109">Perform the following steps to configure a WCF-Custom send port for sending messages to a Siebel system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 
1.  <span data-ttu-id="f7bc0-110">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="f7bc0-111">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="f7bc0-112">Développez l’application sous lequel vous souhaitez déployer le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7bc0-112">Expand the application under which you wish to deploy the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="f7bc0-113">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, pointez sur un type de port que vous souhaitez configurer en fonction du mode de communication entre BizTalk Server et le système Siebel.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-113">Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the Siebel system.</span></span>  
  
5.  <span data-ttu-id="f7bc0-114">Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-114">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6.  <span data-ttu-id="f7bc0-115">À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom** et cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-115">From the **Type** drop-down list, select **WCF-Custom** and click **Configure**.</span></span>  
  
7.  <span data-ttu-id="f7bc0-116">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f7bc0-116">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="f7bc0-117">Cliquez sur le **général** onglet et dans le **adresse (URI)** champ spécifier l’URI de connexion pour se connecter à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-117">Click the **General** tab and in the **Address (URI)** field specify the connection URI to connect to a Siebel system.</span></span> <span data-ttu-id="f7bc0-118">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="f7bc0-118">For more information about the connection URI, see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).</span></span>  
  
    2.  <span data-ttu-id="f7bc0-119">Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-119">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="f7bc0-120">Consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) pour obtenir la liste des actions pour chaque opération.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-120">See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation.</span></span> <span data-ttu-id="f7bc0-121">Par exemple, l’action à appeler l’opération d’insertion sur le composant de gestion de compte est :</span><span class="sxs-lookup"><span data-stu-id="f7bc0-121">For example, the action to invoke the Insert operation on the Account business component is:</span></span>  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    3.  <span data-ttu-id="f7bc0-122">Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **siebelBinding**.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-122">Click the **Binding** tab and from the **Binding Type** drop-down list, select **siebelBinding**.</span></span> <span data-ttu-id="f7bc0-123">Vous pouvez également spécifier les propriétés de liaison différentes exposées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7bc0-123">You can also specify the different binding properties exposed by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="f7bc0-124">Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f7bc0-124">For more information, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
    4.  <span data-ttu-id="f7bc0-125">Cliquez sur le **informations d’identification** onglet, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f7bc0-125">Click the **Credentials** tab and do one of the following:</span></span>  
  
        -   <span data-ttu-id="f7bc0-126">Sélectionnez le **n’utilisez pas l’authentification unique sur** option et spécifiez le nom d’utilisateur et un mot de passe pour se connecter à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-126">Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.</span></span>  
  
        -   <span data-ttu-id="f7bc0-127">Sélectionnez le **utilisez Single Sign-On** option et spécifiez une application de l’entreprise associée.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-127">Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.</span></span>  
  
         <span data-ttu-id="f7bc0-128">Pour plus d’informations sur la sécurité par rapport à BizTalk Server, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="f7bc0-128">For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).</span></span>  
  
    5.  <span data-ttu-id="f7bc0-129">Pour revenir à la **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-129">To return to the **Send Port Properties** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="f7bc0-130">À partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-130">From the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="f7bc0-131">Si vous avez choisi de Port d’envoi unidirectionnel statique à l’étape 4, spécifiez un pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-131">If you chose Static One-Way Send Port in step 4, specify a send pipeline.</span></span> <span data-ttu-id="f7bc0-132">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-132">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
10. <span data-ttu-id="f7bc0-133">Si vous avez choisi de Port statique avec sollicitation-réponse à l’étape 4, spécifiez l’envoi et les pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-133">If you chose Static Solicit-Response Port in step 4, specify send and receive pipelines.</span></span>  
  
    1.  <span data-ttu-id="f7bc0-134">À partir de la **pipeline d’envoi** liste déroulante, sélectionnez le pipeline XMLTransmit correspondant.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-134">From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.</span></span>  
  
    2.  <span data-ttu-id="f7bc0-135">À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline XMLReceive correspondant.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-135">From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.</span></span>  
  
11. <span data-ttu-id="f7bc0-136">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f7bc0-136">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bc0-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7bc0-137">See Also</span></span>  
[<span data-ttu-id="f7bc0-138">Configurer manuellement une liaison de port physique à l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="f7bc0-138">Manually configure a physical port binding to the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)