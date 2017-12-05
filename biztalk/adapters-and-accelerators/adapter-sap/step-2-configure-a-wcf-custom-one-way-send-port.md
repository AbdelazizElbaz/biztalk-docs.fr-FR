---
title: "Étape 2 : Configurer un Port d’envoi unidirectionnel WCF-Custom | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way send port, configuring
- migration
ms.assetid: ae13222e-42e7-45a7-9b2a-0a6779b21736
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8aab14799076d3f774130b357ab90c5ed5335f4a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-configure-a-wcf-custom-one-way-send-port"></a><span data-ttu-id="fd8f8-102">Étape 2 : Configurer un Port d’envoi unidirectionnel WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="fd8f8-102">Step 2: Configure a WCF-Custom One-way Send Port</span></span>
<span data-ttu-id="fd8f8-103">![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="fd8f8-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="fd8f8-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="fd8f8-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="fd8f8-105">**Objectif :** dans cette étape, vous configurez un port personnalisé WCF pour envoyer l’IDOC de fichier plat à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-105">**Objective:** In this step, you configure a WCF-Custom port to send the flat-file IDOC to an SAP system.</span></span> <span data-ttu-id="fd8f8-106">Après avoir configuré le port, vous configurez l’application BizTalk à utiliser le port d’envoi WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-106">After configuring the port, you configure the BizTalk application to use the WCF-Custom send port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fd8f8-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="fd8f8-107">Prerequisites</span></span>  
 <span data-ttu-id="fd8f8-108">Vous devez avoir créé et déployé votre projet BizTalk de vPrev pour envoyer des IDOC à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-108">You must have built and deployed your vPrev BizTalk project to send IDOCs to an SAP system.</span></span>  
  
### <a name="to-configure-a-wcf-custom-one-way-send-port"></a><span data-ttu-id="fd8f8-109">Pour configurer un port d’envoi unidirectionnel WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="fd8f8-109">To configure a WCF-Custom one-way send port</span></span>  
  
1.  <span data-ttu-id="fd8f8-110">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="fd8f8-111">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="fd8f8-112">Développez l’application sous lequel vous souhaitez créer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-112">Expand the application under which you want to create the send port.</span></span>  
  
4.  <span data-ttu-id="fd8f8-113">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-113">Right-click **Send Ports**, point to **New**, and click **Static One-way Send Port**.</span></span>  
  
5.  <span data-ttu-id="fd8f8-114">Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** , tapez un nom pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-114">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6.  <span data-ttu-id="fd8f8-115">À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-115">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="fd8f8-116">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fd8f8-116">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="fd8f8-117">Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour envoyer des messages au système SAP.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-117">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI to send messages to the SAP system.</span></span> <span data-ttu-id="fd8f8-118">Pour plus d’informations sur l’URI de connexion, consultez [créer l’URI de connexion du système SAP](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span><span class="sxs-lookup"><span data-stu-id="fd8f8-118">For more information about the connection URI, see [Create the SAP System Connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
         <span data-ttu-id="fd8f8-119">![URI de connexion spécifié dans le port d’envoi](../../adapters-and-accelerators/adapter-sap/media/53ae71e1-89ec-49c5-8096-ff04a2c94c0a.gif "53ae71e1-89ec-49c5-8096-ff04a2c94c0a")</span><span class="sxs-lookup"><span data-stu-id="fd8f8-119">![Connection URI specified in the send port](../../adapters-and-accelerators/adapter-sap/media/53ae71e1-89ec-49c5-8096-ff04a2c94c0a.gif "53ae71e1-89ec-49c5-8096-ff04a2c94c0a")</span></span>  
  
    2.  <span data-ttu-id="fd8f8-120">Sur le **général** sous l’onglet du **Action** texte, tapez l’action pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-120">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="fd8f8-121">Pour envoyer un IDOC de fichier plat, vous devez utiliser le **SendIdoc** opération exposée par la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8f8-121">To send a flat-file IDOC, you must use the **SendIdoc** operation exposed by the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="fd8f8-122">**SendIdoc** opération permet aux clients de l’adaptateur envoyer des IDOC ayant un schéma faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-122">**SendIdoc** operation enables adapter clients to send IDOCs having a weakly-typed schema.</span></span> <span data-ttu-id="fd8f8-123">Pour plus d’informations, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="fd8f8-123">For more information, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span></span> <span data-ttu-id="fd8f8-124">L’illustration suivante montre le **Action** zone de texte avec l’action pour le **SendIdoc** opération.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-124">The following figure shows the **Action** text box with the action for the **SendIdoc** operation.</span></span>  
  
         <span data-ttu-id="fd8f8-125">![Spécifier l’action dans le port d’envoi](../../adapters-and-accelerators/adapter-sap/media/94dd1505-5529-43cf-a27b-2588a022dfb9.gif "94dd1505-5529-43cf-a27b-2588a022dfb9")</span><span class="sxs-lookup"><span data-stu-id="fd8f8-125">![Specify action in the send port](../../adapters-and-accelerators/adapter-sap/media/94dd1505-5529-43cf-a27b-2588a022dfb9.gif "94dd1505-5529-43cf-a27b-2588a022dfb9")</span></span>  
  
    3.  <span data-ttu-id="fd8f8-126">Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-126">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span>  
  
    4.  <span data-ttu-id="fd8f8-127">Cliquez sur le **informations d’identification** onglet et spécifier les informations d’identification pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-127">Click the **Credentials** tab and specify the credentials to connect to an SAP system.</span></span>  
  
    5.  <span data-ttu-id="fd8f8-128">Cliquez sur le **Messages** onglet et dans le **le corps du message WCF sortant** , choisissez le **modèle** option.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-128">Click the **Messages** tab, and in the **Outbound WCF message body** section, choose the **Template** option.</span></span>  
  
    6.  <span data-ttu-id="fd8f8-129">Dans le **XML** texte, spécifiez le modèle qui servira à construire le message WCF.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-129">In the **XML** text box, specify the template that will be used to construct the WCF message.</span></span> <span data-ttu-id="fd8f8-130">En procédant ainsi, vous créez un message qui est conforme à la **SendIdoc** opération pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8f8-130">By doing so, you create a message that conforms to the **SendIdoc** operation for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="fd8f8-131">Pour plus d’informations sur la structure du message pour le **SendIdoc** opération, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).</span><span class="sxs-lookup"><span data-stu-id="fd8f8-131">For more information about the message structure for the **SendIdoc** operation, see [Message Schemas for IDOC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).</span></span>  
  
         <span data-ttu-id="fd8f8-132">![Spécifiez le modèle de message WCF sortant](../../adapters-and-accelerators/adapter-sap/media/909835c3-a941-49dc-87f0-858fe0e1fc63.gif "909835c3-a941-49dc-87f0-858fe0e1fc63")</span><span class="sxs-lookup"><span data-stu-id="fd8f8-132">![Specify template for outbound WCF message](../../adapters-and-accelerators/adapter-sap/media/909835c3-a941-49dc-87f0-858fe0e1fc63.gif "909835c3-a941-49dc-87f0-858fe0e1fc63")</span></span>  
  
         <span data-ttu-id="fd8f8-133">Pour l’opération SendIdoc, vous devez spécifier le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="fd8f8-133">For the SendIdoc operation, you must specify the following template:</span></span>  
  
        ```  
        <SendIdoc xmlns="http://Microsoft.LobServices.Sap/2007/03/Idoc/">  
        <idocData><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/></idocData>  
        </SendIdoc>  
        ```  
  
         <span data-ttu-id="fd8f8-134">Dans le modèle précédent, le `bts-msg-body` est port de réception IDOC XML qui est créé en utilisant le désassembleur de fichier plat associé au fichier.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-134">In the preceding template, the `bts-msg-body` is XML IDOC that is created using the flat-file disassembler associated with the file receive port.</span></span> <span data-ttu-id="fd8f8-135">L’IDOC XML est encapsulé dans le message SendIdoc.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-135">The XML IDOC is encapsulated in the SendIdoc message.</span></span>  
  
    7.  <span data-ttu-id="fd8f8-136">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-136">Click **Apply**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="fd8f8-137">Dans le **propriétés de Port d’envoi** boîte de dialogue, à partir de la **Gestionnaire d’envoi** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-137">In the **Send Port Properties** dialog box, from the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="fd8f8-138">À partir de la **pipeline d’envoi** la liste déroulante, sélectionnez **ConvertToFlatFile**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-138">From the **Send pipeline** drop-down list, select **ConvertToFlatFile**.</span></span> <span data-ttu-id="fd8f8-139">Ce pipeline assembleur de fichier plat fait déjà partie du projet BizTalk vPrev et est utilisé pour convertir un IDOC XML en un IDOC de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-139">This flat-file assembler pipeline is already a part of the vPrev BizTalk project and is used to convert an XML IDOC to a flat-file IDOC.</span></span>  
  
10. <span data-ttu-id="fd8f8-140">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-140">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="fd8f8-141">Pour configurer l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="fd8f8-141">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="fd8f8-142">Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, développez l’Application BizTalk où l’orchestration est déployée.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-142">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="fd8f8-143">Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-143">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="fd8f8-144">Dans le volet gauche, cliquez sur l’orchestration à configurer.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-144">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="fd8f8-145">Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-145">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="fd8f8-146">Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-146">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="fd8f8-147">Sélectionnez le port de fichier dans lequel vous allez déposer l’IDOC de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-147">Select the file port where you will drop the flat-file IDOC.</span></span>  
  
    2.  <span data-ttu-id="fd8f8-148">Sélectionnez le port d’envoi WCF-Custom que vous avez créé précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-148">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
    3.  <span data-ttu-id="fd8f8-149">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-149">Click **OK**.</span></span>  
  
     <span data-ttu-id="fd8f8-150">Pour plus d’informations sur la configuration d’une application, consultez « Configuration d’une Application » à [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span><span class="sxs-lookup"><span data-stu-id="fd8f8-150">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fd8f8-151">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fd8f8-151">Next Steps</span></span>  
 <span data-ttu-id="fd8f8-152">Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui envoie des IDOC à un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd8f8-152">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends IDOCs to an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="fd8f8-153">Vous devez maintenant tester l’application migrée de BizTalk en envoyant un IDOC de fichier plat, comme décrit dans [étape 3 : tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md).</span><span class="sxs-lookup"><span data-stu-id="fd8f8-153">You must now test the migrated BizTalk application by sending a flat-file IDOC, as described in [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8f8-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd8f8-154">See Also</span></span>  
 [<span data-ttu-id="fd8f8-155">Didacticiel 3 : Migration d’un projet BizTalk SAP d’envoi d’un IDOC</span><span class="sxs-lookup"><span data-stu-id="fd8f8-155">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)