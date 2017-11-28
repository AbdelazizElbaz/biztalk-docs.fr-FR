---
title: "Étape 2 : Configurer un WCF-Custom unidirectionnel Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way receive port, configuring
- migration
ms.assetid: e2a8f074-64d5-4e6c-84d0-318fb606c0ba
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6edf75f08bdf6a321188e484eb4f363366f8eb95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-a-wcf-custom-one-way-receive-port"></a><span data-ttu-id="e8d8b-102">Étape 2 : Configurer un WCF-Custom unidirectionnel Port de réception</span><span class="sxs-lookup"><span data-stu-id="e8d8b-102">Step 2: Configure a WCF-Custom One-way Receive Port</span></span>
<span data-ttu-id="e8d8b-103">![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="e8d8b-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="e8d8b-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="e8d8b-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="e8d8b-105">**Objectif :** dans cette étape, vous configurez un port personnalisé WCF pour recevoir un IDOC de fichier plat à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-105">**Objective:** In this step, you configure a WCF-Custom port to receive a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="e8d8b-106">Après avoir configuré le port, vous configurez BizTalk application afin d’utiliser WCF-Custom port de réception.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-106">After configuring the port, you configure the BizTalk application to use the WCF-Custom receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e8d8b-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e8d8b-107">Prerequisites</span></span>  
 <span data-ttu-id="e8d8b-108">Vous devez avoir créé et déployé votre projet BizTalk de vPrev pour recevoir des IDOC à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-108">You must have built and deployed your vPrev BizTalk project to receive IDOCs from an SAP system.</span></span>  
  
### <a name="to-configure-a-wcf-custom-one-way-receive-port"></a><span data-ttu-id="e8d8b-109">Pour configurer les port de réception WCF-Custom unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="e8d8b-109">To configure a WCF-Custom one-way receive port</span></span>  
  
1.  <span data-ttu-id="e8d8b-110">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="e8d8b-111">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="e8d8b-112">Développez l’application sous lequel vous voulez créer le port de réception.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-112">Expand the application under which you want create the receive port.</span></span>  
  
4.  <span data-ttu-id="e8d8b-113">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-113">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port**.</span></span>  
  
5.  <span data-ttu-id="e8d8b-114">Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-114">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6.  <span data-ttu-id="e8d8b-115">Sur le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-115">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="e8d8b-116">Le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-116">The **Receive Location Properties** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="e8d8b-117">Dans le **propriétés de l’emplacement de réception** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e8d8b-117">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e8d8b-118">Spécifiez un nom pour l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-118">Specify a name for the receive location.</span></span>  
  
    2.  <span data-ttu-id="e8d8b-119">À partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-119">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e8d8b-120">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e8d8b-120">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e8d8b-121">Cliquez sur le **général** onglet et dans le **adresse (URI)** champ, spécifiez l’URI de connexion pour recevoir des messages à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-121">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI to receive messages from the SAP system.</span></span> <span data-ttu-id="e8d8b-122">L’URI de connexion pour recevoir des messages à partir du système SAP doit être au format suivant :</span><span class="sxs-lookup"><span data-stu-id="e8d8b-122">The connection URI to receive messages from the SAP system must be in the following format:</span></span>  
  
        ```  
        sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
        ```  
  
         <span data-ttu-id="e8d8b-123">L’illustration suivante montre la boîte de dialogue des propriétés de port avec l’URI spécifié :</span><span class="sxs-lookup"><span data-stu-id="e8d8b-123">The following figure shows the port properties dialog box with the URI specified:</span></span>  
  
         <span data-ttu-id="e8d8b-124">![URI de connexion pour recevoir des messages à partir de SAP](../../adapters-and-accelerators/adapter-sap/media/91e12582-aea3-4f13-8cdc-af69a9a11a5c.gif "91e12582-aea3-4f13-8cdc-af69a9a11a5c")</span><span class="sxs-lookup"><span data-stu-id="e8d8b-124">![Connection URI to receive messages from SAP](../../adapters-and-accelerators/adapter-sap/media/91e12582-aea3-4f13-8cdc-af69a9a11a5c.gif "91e12582-aea3-4f13-8cdc-af69a9a11a5c")</span></span>  
  
         <span data-ttu-id="e8d8b-125">Pour plus d’informations sur l’URI de connexion, consultez [créer une connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).</span><span class="sxs-lookup"><span data-stu-id="e8d8b-125">For more information about the connection URI, see [Create a  connection to the SAP system](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).</span></span>  
  
    2.  <span data-ttu-id="e8d8b-126">Cliquez sur le **liaison** onglet et à partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-126">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span> <span data-ttu-id="e8d8b-127">Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-127">Make sure you specify the following binding properties for the receive port.</span></span>  
  
        |<span data-ttu-id="e8d8b-128">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="e8d8b-128">Binding property</span></span>|<span data-ttu-id="e8d8b-129">Affectez à la valeur</span><span class="sxs-lookup"><span data-stu-id="e8d8b-129">Set value to</span></span>|  
        |----------------------|------------------|  
        |<span data-ttu-id="e8d8b-130">flatFileSegmentIndicator</span><span class="sxs-lookup"><span data-stu-id="e8d8b-130">flatFileSegmentIndicator</span></span>|<span data-ttu-id="e8d8b-131">**SegmentType**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-131">**SegmentType**.</span></span> <span data-ttu-id="e8d8b-132">Cela indique que les fichiers plats doivent contenir le type de segment pour chaque segment dans l’IDOC.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-132">This indicates that the flat files should contain the segment type for each segment in the IDOC.</span></span>|  
        |<span data-ttu-id="e8d8b-133">padReceivedIdocWithSpaces</span><span class="sxs-lookup"><span data-stu-id="e8d8b-133">padReceivedIdocWithSpaces</span></span>|<span data-ttu-id="e8d8b-134">**Vrai**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-134">**True**.</span></span> <span data-ttu-id="e8d8b-135">Spécifie si chaque ligne dans l’IDOC est complétée avec des espaces pour la longueur correcte.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-135">Specifies whether each line in the IDOC is padded with spaces to the correct length.</span></span>|  
        |<span data-ttu-id="e8d8b-136">receiveIDocFormat</span><span class="sxs-lookup"><span data-stu-id="e8d8b-136">receiveIDocFormat</span></span>|<span data-ttu-id="e8d8b-137">**Chaîne**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-137">**String**.</span></span> <span data-ttu-id="e8d8b-138">Spécifie que le message IDOC doit être représenté comme un champ de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-138">This specifies that the IDOC message should be represented as a single string field.</span></span>|  
  
         <span data-ttu-id="e8d8b-139">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e8d8b-139">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    3.  <span data-ttu-id="e8d8b-140">Cliquez sur le **d’autres** onglet et spécifier les informations d’identification pour se connecter à un système SAP.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-140">Click the **Others** tab, and specify the credentials to connect to an SAP system.</span></span>  
  
    4.  <span data-ttu-id="e8d8b-141">Cliquez sur le **Messages** onglet et dans le **le corps du message BizTalk entrant** , choisissez le **chemin d’accès** option.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-141">Click the **Messages** tab, and in the **Inbound BizTalk message body** section, choose the **Path** option.</span></span>  
  
    5.  <span data-ttu-id="e8d8b-142">Dans le **expression de chemin de corps** texte, spécifiez la requête XPath pour extraire l’IDOC de fichier plat du message XML.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-142">In the **Body path expression** text box, specify the XPath query to extract the flat-file IDOC from the XML message.</span></span> <span data-ttu-id="e8d8b-143">En procédant ainsi, le port de réception extrait les données de l’IDOC et ajuste la balise XML qui fait partie de la **ReceiveIdoc** opération pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8d8b-143">By doing so, the receive port extracts the data from the IDOC and trims the XML tag that is part of the **ReceiveIdoc** operation for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="e8d8b-144">Pour plus d’informations sur le schéma de message pour le **ReceiveIdoc** opération, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e8d8b-144">For more information about the message schema for the **ReceiveIdoc** operation, see [Message Schemas for IDOC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).</span></span>  
  
         <span data-ttu-id="e8d8b-145">![XPath de requête pour extraire le plate &#45; fichier IDOC](../../adapters-and-accelerators/adapter-sap/media/8b5b8165-a1e7-40ef-bcf7-de3149c6deb0.gif "8b5b8165-a1e7-40ef-bcf7-de3149c6deb0")</span><span class="sxs-lookup"><span data-stu-id="e8d8b-145">![XPath query to extract the flat&#45;file IDOC](../../adapters-and-accelerators/adapter-sap/media/8b5b8165-a1e7-40ef-bcf7-de3149c6deb0.gif "8b5b8165-a1e7-40ef-bcf7-de3149c6deb0")</span></span>  
  
         <span data-ttu-id="e8d8b-146">Vous devez spécifier la requête XPath suivante :</span><span class="sxs-lookup"><span data-stu-id="e8d8b-146">You must specify the following XPath query:</span></span>  
  
        ```  
        /*[local-name()='ReceiveIdoc']/*[local-name()='idocData']  
        ```  
  
    6.  <span data-ttu-id="e8d8b-147">À partir de la **codage de nœud** la liste déroulante, sélectionnez **chaîne**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-147">From the **Node encoding** drop-down list, select **String**.</span></span>  
  
    7.  <span data-ttu-id="e8d8b-148">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-148">Click **Apply**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="e8d8b-149">Dans la boîte de dialogue Propriétés de l’emplacement de réception à partir de la **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-149">In the Receive Location Properties dialog box, from the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="e8d8b-150">À partir de la **pipeline de réception** la liste déroulante, sélectionnez **ConvertToXML**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-150">From the **Receive pipeline** drop-down list, select **ConvertToXML**.</span></span> <span data-ttu-id="e8d8b-151">Ce pipeline désassembleur de fichier plat fait déjà partie du projet BizTalk vPrev pour convertir un IDOC de fichier plat en un IDOC XML.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-151">This flat-file disassembler pipeline is already a part of the vPrev BizTalk project to convert a flat-file IDOC to an XML IDOC.</span></span>  
  
11. <span data-ttu-id="e8d8b-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-152">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="e8d8b-153">Pour configurer l’application BizTalk</span><span class="sxs-lookup"><span data-stu-id="e8d8b-153">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="e8d8b-154">Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, développez l’Application BizTalk où l’orchestration est déployée.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-154">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="e8d8b-155">Cliquez sur l’application BizTalk, puis sélectionnez **configurer**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-155">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="e8d8b-156">Dans le volet gauche, cliquez sur l’orchestration à configurer.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-156">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="e8d8b-157">Dans le volet droit, à partir de la **hôte** liste déroulante, sélectionnez une instance d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-157">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="e8d8b-158">Sous le **liaisons** zone, mapper les ports logiques de l’orchestration BizTalk pour les ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-158">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="e8d8b-159">Sélectionnez cette option WCF-Custom réception port que vous avez créé précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-159">Select the WCF-Custom receive port you created earlier in this topic.</span></span>  
  
    2.  <span data-ttu-id="e8d8b-160">Sélectionnez un port de fichier dans lequel vous recevez l’IDOC de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-160">Select a file port where you will receive the flat-file IDOC.</span></span>  
  
    3.  <span data-ttu-id="e8d8b-161">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e8d8b-161">Click **OK**.</span></span>  
  
     <span data-ttu-id="e8d8b-162">Pour plus d’informations sur la configuration d’une application, consultez [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span><span class="sxs-lookup"><span data-stu-id="e8d8b-162">For more information about configuring an application, see [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e8d8b-163">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e8d8b-163">Next Steps</span></span>  
 <span data-ttu-id="e8d8b-164">Vous avez maintenant terminé la migration de votre projet BizTalk de vPrev à un projet BizTalk qui reçoit des IDOC à partir d’un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8d8b-164">You have now completed migration of your vPrev BizTalk project to a BizTalk project that receives IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="e8d8b-165">Vous devez maintenant tester l’application migrée de BizTalk en recevant un IDOC de fichier plat, comme décrit dans [étape 3 : tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md).</span><span class="sxs-lookup"><span data-stu-id="e8d8b-165">You must now test the migrated BizTalk application by receiving a flat-file IDOC, as described in [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d8b-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8d8b-166">See Also</span></span>  
 [<span data-ttu-id="e8d8b-167">Didacticiel 4 : Migration d’un SAP de réception projet BizTalk IDOC</span><span class="sxs-lookup"><span data-stu-id="e8d8b-167">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)