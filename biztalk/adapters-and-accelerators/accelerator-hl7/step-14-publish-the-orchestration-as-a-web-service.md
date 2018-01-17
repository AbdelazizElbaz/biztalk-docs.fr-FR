---
title: "Étape 14 : Publier l’Orchestration en tant que Service Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- publishing, orchestrations
- Web services, orchestrations
- message enrichment tutorial, orchestrations
- publishing, Web services
- message enrichment tutorial, Web services
ms.assetid: 8f29a7be-a679-4ca6-a648-35338d9e9e98
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c742d21dd2f2e1d95f697beea3d5d5dfa0461d2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="step-14-publish-the-orchestration-as-a-web-service"></a><span data-ttu-id="41dfd-102">Étape 14 : Publier l’Orchestration en tant que Service Web</span><span class="sxs-lookup"><span data-stu-id="41dfd-102">Step 14: Publish the Orchestration as a Web Service</span></span>
<span data-ttu-id="41dfd-103">Dans cette étape, vous utilisez l’Assistant de publication des Services Web BizTalk pour publier une orchestration en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="41dfd-103">In this step, you use the BizTalk Web Services Publishing Wizard to publish your orchestration as a Web service.</span></span>  
  
 <span data-ttu-id="41dfd-104">Avant de publier l’orchestration en tant qu’un service Web, vous devez vous assurer que le compte d’ouverture de session pour BizTalkServerIsolatedHost fait partie du groupe utilisateurs d’hôtes BizTalk isolés, elle a accès aux bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="41dfd-104">Before publishing the orchestration as a Web service, you need to ensure that the logon account for BizTalkServerIsolatedHost is part of the BizTalk Isolated Host Users group, so it has access to the BizTalk databases.</span></span> <span data-ttu-id="41dfd-105">Cela est nécessaire car le Gestionnaire de réception pour l’emplacement de réception SOAPReceivePort qui est créé par l’Assistant Publication de services Web pour ce didacticiel est BizTalkServerIsolatedHost, pas BizTalkServerApplication.</span><span class="sxs-lookup"><span data-stu-id="41dfd-105">This is necessary because the receive handler for the SOAPReceivePort receive location that is created by the Web Service Publishing Wizard for this tutorial is BizTalkServerIsolatedHost, not BizTalkServerApplication.</span></span> <span data-ttu-id="41dfd-106">Le Gestionnaire de réception est BizTalkServerIsolatedHost car l’adaptateur SOAP s’exécute sous le processus IIS, pas le processus BizTalk.</span><span class="sxs-lookup"><span data-stu-id="41dfd-106">The receive handler is BizTalkServerIsolatedHost because the SOAP adapter runs under the IIS process, not the BizTalk process.</span></span>  
  
### <a name="to-ensure-access-privileges-for-the-soapreceiveport-receive-location"></a><span data-ttu-id="41dfd-107">Pour garantir l’accès des privilèges pour le SOAPReceivePort emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="41dfd-107">To ensure access privileges for the SOAPReceivePort receive location</span></span>  
  
1.  <span data-ttu-id="41dfd-108">Dans la Console Administration de BizTalk Server, sous **Instances d’hôte** dans les **paramètres de plateforme** nœud, avec le bouton droit **BizTalkServerIsolatedHost**, puis cliquez sur  **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-108">In BizTalk Server Administration Console, under **Host Instances** in the **Platform Settings** node, right-click **BizTalkServerIsolatedHost**, and then click **Properties**.</span></span> <span data-ttu-id="41dfd-109">Dans la boîte de dialogue Propriétés, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-109">In the Properties dialog box, click **Configure**.</span></span> <span data-ttu-id="41dfd-110">Remarque la **ouverture de session** compte.</span><span class="sxs-lookup"><span data-stu-id="41dfd-110">Note the **Logon** account.</span></span>  
  
2.  <span data-ttu-id="41dfd-111">Dans la boîte de dialogue Gestion de l’ordinateur sous **groupes** dans les **utilisateurs et groupes locaux** nœud, double-cliquez sur **utilisateurs d’hôtes BizTalk isolés**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-111">In the Computer Management dialog box, under **Groups** in the **Local Users and Groups** node, double-click **BizTalk Isolated Host Users**.</span></span> <span data-ttu-id="41dfd-112">Si l’ouverture de session du compte pour **BizTalkServerIsolatedHost** n’est pas un membre de **BizTalkServerIsolatedHost**, ajoutez-le au groupe.</span><span class="sxs-lookup"><span data-stu-id="41dfd-112">If the logon account for **BizTalkServerIsolatedHost** is not a member of **BizTalkServerIsolatedHost**, add it to the group.</span></span>  
  
### <a name="to-run-the-biztalk-web-services-publishing-wizard"></a><span data-ttu-id="41dfd-113">Pour exécuter l’Assistant de publication des Services Web BizTalk</span><span class="sxs-lookup"><span data-stu-id="41dfd-113">To run the BizTalk Web Services Publishing Wizard</span></span>  
  
1.  <span data-ttu-id="41dfd-114">Dans l’Explorateur de solutions de Visual Studio, cliquez sur **Solution 'BTAHL7V22Common'**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-114">In Solution Explorer of Visual Studio, click **Solution 'BTAHL7V22Common'**.</span></span> <span data-ttu-id="41dfd-115">Sur le **outils** menu, cliquez sur **Assistant Publication des Services Web BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-115">On the **Tools** menu, click **BizTalk Web Services Publishing Wizard**.</span></span>  
  
2.  <span data-ttu-id="41dfd-116">Dans le **Assistant Publication des Services Web BizTalk**, dans le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-116">In the **BizTalk Web Services Publishing Wizard**, on the **Welcome** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="41dfd-117">Sur le **créer un Service Web** page, sélectionnez **publier des orchestrations BizTalk en tant que services web**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-117">On the **Create Web Service** page, select **Publish BizTalk orchestrations as web services**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="41dfd-118">Sur le **BizTalk Assembly** page, dans le **fichier d’assembly BizTalk (\\*.dll)** champ, tapez ou recherchez  **\< *lecteur* \>: \Tutorial\BTAHL7V22Common\BTAHL7 Project\bin\development**, cliquez sur **BTAHL7 Project.dll**, cliquez sur **ouvrir**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-118">On the **BizTalk Assembly** page, in the **BizTalk assembly file (\\*.dll)** field, browse to or type **\<*drive*\>:\Tutorial\BTAHL7V22Common\BTAHL7 Project\bin\development**, click **BTAHL7 Project.dll**, click **Open**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="41dfd-119">Sur le **Orchestrations et Ports** , vérifiez que tous les nœuds sont sélectionnés, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-119">On the **Orchestrations and Ports** page, ensure that all nodes are selected, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="41dfd-120">Sur le **propriétés du Service Web** page, pour **espace de noms cible du service web**, type **http://localhost**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-120">On the **Web Service Properties** page, for **Target namespace of web service**, type **http://localhost**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="41dfd-121">Sur le **projet de Service Web** page, sélectionnez **autorise l’accès anonyme au service web** et **BizTalk de créer les emplacements de réception dans l’application suivante**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-121">On the **Web Service Project** page, select **Allow anonymous access to web service** and **Create BizTalk receive locations in the following application**.</span></span> <span data-ttu-id="41dfd-122">Sélectionnez **BizTalk Application 1** pour l’application.</span><span class="sxs-lookup"><span data-stu-id="41dfd-122">Select **BizTalk Application 1** for the application.</span></span> <span data-ttu-id="41dfd-123">Conserver la valeur par défaut dans le **emplacement** champ.</span><span class="sxs-lookup"><span data-stu-id="41dfd-123">Keep the default in the **Location** field.</span></span> <span data-ttu-id="41dfd-124">Cliquez sur **suivant** pour accepter l’emplacement par défaut du projet.</span><span class="sxs-lookup"><span data-stu-id="41dfd-124">Click **Next** to accept the default project location.</span></span>  
  
8.  <span data-ttu-id="41dfd-125">Sur le **résumé du projet de Service Web** , cliquez sur **créer** pour générer le projet de Service Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="41dfd-125">On the **Web Service Project Summary** page, click **Create** to generate the ASP.NET Web Service project.</span></span>  
  
9. <span data-ttu-id="41dfd-126">Cliquez sur **Terminer** pour fermer l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="41dfd-126">Click **Finish** to close the wizard.</span></span>  
  
10. <span data-ttu-id="41dfd-127">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="41dfd-127">Open the BizTalk Server Administration Console.</span></span> <span data-ttu-id="41dfd-128">Dans la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1** .</span><span class="sxs-lookup"><span data-stu-id="41dfd-128">In the console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
11. <span data-ttu-id="41dfd-129">Cliquez sur **emplacements de réception**, avec le bouton droit **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-129">Click **Receive Locations**, right-click **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, and then click **Properties**.</span></span>  
  
12. <span data-ttu-id="41dfd-130">Dans la boîte de dialogue Propriétés de l’emplacement de réception, cliquez sur **Pipeline de réception**, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLReceive** dans la liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-130">In the Receive Location Properties dialog box, click **Receive Pipeline**, select **Microsoft.BizTalk.DefaultPipelines.XMLReceive** from the drop-down list, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="41dfd-131">Avec le bouton droit **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="41dfd-131">Right-click **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, and then click **Enable**.</span></span>  
  
 <span data-ttu-id="41dfd-132">Passez à [étape 15 : configurer l’envoi et de Ports de réception](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md).</span><span class="sxs-lookup"><span data-stu-id="41dfd-132">Proceed to [Step 15: Configure the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dfd-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41dfd-133">See Also</span></span>  
 [<span data-ttu-id="41dfd-134">Didacticiel sur l’enrichissement des messages</span><span class="sxs-lookup"><span data-stu-id="41dfd-134">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)