---
title: "Comment : publier un Service à UDDI 3.0 Registre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c3bd0ed-e5f1-43eb-98d1-e3247a565ba2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca41923dc4c392959af9f19cf3b7c32f6bfe7c20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-publish-a-service-to-the-uddi-30-registry"></a><span data-ttu-id="2aba5-102">Comment : publier un Service à UDDI 3.0 Registre</span><span class="sxs-lookup"><span data-stu-id="2aba5-102">How to: Publish a Service to the UDDI 3.0 Registry</span></span>
## <a name="goal"></a><span data-ttu-id="2aba5-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="2aba5-103">Goal</span></span>  
 <span data-ttu-id="2aba5-104">Cette section montre comment utiliser le site des services UDDI pour publier un point de terminaison de service Web qui peut être résolu à partir d’un itinéraire à des fins de routage d’un message d’ESB.</span><span class="sxs-lookup"><span data-stu-id="2aba5-104">This section demonstrates how to use the UDDI Service site to publish a Web service endpoint that can be resolved from within an itinerary for the purpose of routing an ESB message.</span></span> <span data-ttu-id="2aba5-105">Vous allez dupliquer le service PurchaseOrderSubmitOrderService existant actuellement publié dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="2aba5-105">You will duplicate the existing PurchaseOrderSubmitOrderService service presently published to the registry.</span></span>  
  
 <span data-ttu-id="2aba5-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="2aba5-107">Publier un service sur le Universal Description, Discovery, and Integration (UDDI) 3 Registre à l’aide de l’outil de serveur de publication UDDI.</span><span class="sxs-lookup"><span data-stu-id="2aba5-107">Publish a service to the Universal Description, Discovery, and Integration (UDDI) 3 registry using the UDDI Publisher tool.</span></span>  
  
-   <span data-ttu-id="2aba5-108">Test de la publication de service à l’aide d’un bordereau d’itinéraire de routage qui résout le point de terminaison de service à l’aide d’un programme de résolution UDDI3.</span><span class="sxs-lookup"><span data-stu-id="2aba5-108">Test the service publication using an itinerary routing slip that resolves the service endpoint using a UDDI3 resolver.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2aba5-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2aba5-109">Prerequisites</span></span>  
 <span data-ttu-id="2aba5-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) et l’exécution de l’outil de serveur de publication UDDI (vous pouvez l’installer à % ESB installer Folder%\Bin\ Microsoft.Practices.ESB.UDDIPublisher.exe).</span><span class="sxs-lookup"><span data-stu-id="2aba5-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) and the execution of the UDDI Publisher tool (you can install it at %ESB Install Folder%\Bin\Microsoft.Practices.ESB.UDDIPublisher.exe).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="2aba5-111">Étapes</span><span class="sxs-lookup"><span data-stu-id="2aba5-111">Steps</span></span>  
  
#### <a name="to-create-the-newposervice-in-the-uddi-registry"></a><span data-ttu-id="2aba5-112">Pour créer le NewPOService dans le Registre UDDI</span><span class="sxs-lookup"><span data-stu-id="2aba5-112">To create the NewPOService in the UDDI registry</span></span>  
  
1.  <span data-ttu-id="2aba5-113">Dans Internet Explorer, accédez au site des services UDDI (par défaut, l’URL pour cette est http://localhost/uddi).</span><span class="sxs-lookup"><span data-stu-id="2aba5-113">In Internet Explorer, browse to the UDDI Service site (by default, the URL for this is http://localhost/uddi).</span></span>  
  
2.  <span data-ttu-id="2aba5-114">Sur le **les Services uddi** , cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-114">On the **uddi Services** page, click **Publish**.</span></span>  
  
3.  <span data-ttu-id="2aba5-115">Dans le volet de la publication, cliquez sur **Microsoft.Practices.ESB**, puis cliquez sur **ajouter un Service**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-115">In the Publish pane, right-click **Microsoft.Practices.ESB**, and then click **Add Service**.</span></span>  
  
4.  <span data-ttu-id="2aba5-116">Sur la page suivante, sélectionnez **spécifier la clé à utiliser**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-116">On the following page, select **Specify a key to use**, and then click **Continue**.</span></span>  
  
5.  <span data-ttu-id="2aba5-117">Dans la page suivante, cliquez sur le **esb** clé de partition.</span><span class="sxs-lookup"><span data-stu-id="2aba5-117">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="2aba5-118">Dans le **clé suffixe** , tapez **newposervice**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-118">In the **Key Suffix** box, type **newposervice**, and then click **Continue**.</span></span>  
  
6.  <span data-ttu-id="2aba5-119">Sur la page suivante, à côté (**nouveau nom de Service**), cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-119">On the following page, next to (**New Service Name**), click **Edit**.</span></span> <span data-ttu-id="2aba5-120">Nom de service **NewPOService**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-120">Name the service **NewPOService**, and then click **Update**.</span></span>  
  
7.  <span data-ttu-id="2aba5-121">Cliquez sur **ajouter une Description**, tapez une description pour le service (par exemple, **exemple de Service**), puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-121">Click **Add Description**, type a description for the service (for example, **Sample Service**), and then click **Update**.</span></span>  
  
#### <a name="to-add-a-binding-for-the-newposervice"></a><span data-ttu-id="2aba5-122">Pour ajouter une liaison pour le NewPOService</span><span class="sxs-lookup"><span data-stu-id="2aba5-122">To add a binding for the NewPOService</span></span>  
  
1.  <span data-ttu-id="2aba5-123">Cliquez sur le **liaisons** onglet, puis cliquez sur **ajouter la liaison**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-123">Click the **Bindings** tab, and then click **Add Binding**.</span></span>  
  
2.  <span data-ttu-id="2aba5-124">Sélectionnez **spécifier la clé à utiliser**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-124">Select **Specify a key to use**, and then click **Continue**.</span></span>  
  
3.  <span data-ttu-id="2aba5-125">Dans la page suivante, cliquez sur le **esb** clé de partition.</span><span class="sxs-lookup"><span data-stu-id="2aba5-125">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="2aba5-126">Dans le **clé suffixe** , tapez **newposervicebinding**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-126">In the **Key Suffix** box, type **newposervicebinding**, and then click **Continue**.</span></span>  
  
4.  <span data-ttu-id="2aba5-127">Sous **le Point d’accès**, cliquez sur **modifier**et puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2aba5-127">Under **Access Point**, click **Edit**, and then complete the following:</span></span>  
  
    1.  <span data-ttu-id="2aba5-128">Dans le **le Point d’accès** , tapez **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-128">In the **Access Point** box, type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-129">Dans le **Type d’utilisation** la liste déroulante, cliquez sur **point de terminaison**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-129">In the **Use Type** drop-down list, click **endpoint**, and then click **Update**.</span></span>  
  
#### <a name="to-configure-the-binding-instance-information"></a><span data-ttu-id="2aba5-130">Pour configurer les informations d’instance de liaison</span><span class="sxs-lookup"><span data-stu-id="2aba5-130">To configure the binding instance information</span></span>  
  
1.  <span data-ttu-id="2aba5-131">Cliquez sur le **Infos sur l’Instance** onglet, puis cliquez sur **ajouter des informations d’Instance**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-131">Click the **Instance Info** tab, and then click **Add Instance Info**.</span></span>  
  
2.  <span data-ttu-id="2aba5-132">Dans le **recherche les noms de tModel contenant** , tapez **esb %** puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-132">In the **Search for tModel names containing** box, type **%esb%** and then click **Search**.</span></span>  
  
3.  <span data-ttu-id="2aba5-133">Recherchez et cliquez sur le **tModel** pour **transporttype**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-133">Locate and click the **tModel** for **transporttype**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2aba5-134">Pour effectuer les étapes restantes de cette procédure, vous devrez peut-être passer à la page 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="2aba5-134">To complete the remaining steps in this procedure, you may be required to change between page 1 and page 2.</span></span>  
  
4.  <span data-ttu-id="2aba5-135">Dans le **Descriptions** , cliquez sur **ajouter une Description**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-135">In the **Descriptions** section, click **Add Description**.</span></span>  
  
5.  <span data-ttu-id="2aba5-136">Dans le **Description** , tapez **Type de Transport pour une utilisation d’itinéraire ESB**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-136">In the **Description** box, type **Transport Type for ESB Itinerary Use**, and then click **Update**.</span></span>  
  
6.  <span data-ttu-id="2aba5-137">Cliquez sur le **détails de l’Instance** onglet, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-137">Click the **Instance Details** tab, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="2aba5-138">Dans le **paramètres de l’Instance** , tapez **WCF-BasicHttp**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-138">In the **Instance Parameters** box, type **WCF-BasicHttp**, and then click **Update**.</span></span>  
  
8.  <span data-ttu-id="2aba5-139">Dans le **Descriptions** , cliquez sur **ajouter une Description**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-139">In the **Descriptions** section, click **Add Description**.</span></span>  
  
9. <span data-ttu-id="2aba5-140">Dans le **Description** , tapez **WCF de base du Transport HTTP**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-140">In the **Description** box, type **WCF Basic HTTP Transport**, and then click **Update**.</span></span>  
  
10. <span data-ttu-id="2aba5-141">Dans le volet de la publication, sous **NewPOService**, cliquez sur **http://localhost/esb.canadianservices/submitposervice.asmx**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-141">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  
  
11. <span data-ttu-id="2aba5-142">Sur le **Infos sur l’Instance** , cliquez sur **ajouter des informations d’Instance**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-142">On the **Instance Info** tab, click **Add Instance Info**.</span></span>  
  
12. <span data-ttu-id="2aba5-143">À l’aide de la procédure décrite précédemment, ajoutez les informations d’instance suivantes, selon les valeurs indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="2aba5-143">Using the steps described earlier, add the following instance information, according to the values shown in the following table.</span></span>  
  
    |<span data-ttu-id="2aba5-144">élément tModel</span><span class="sxs-lookup"><span data-stu-id="2aba5-144">tModel</span></span>|<span data-ttu-id="2aba5-145"> Description</span><span class="sxs-lookup"><span data-stu-id="2aba5-145">Description</span></span>|<span data-ttu-id="2aba5-146">Paramètre</span><span class="sxs-lookup"><span data-stu-id="2aba5-146">Parameter</span></span>|<span data-ttu-id="2aba5-147">Description du paramètre</span><span class="sxs-lookup"><span data-stu-id="2aba5-147">Parameter description</span></span>|  
    |------------|-----------------|---------------|---------------------------|  
    |<span data-ttu-id="2aba5-148">Microsoft-com:esb:runtimeresolution:messageexchangepattern</span><span class="sxs-lookup"><span data-stu-id="2aba5-148">microsoft-com:esb:runtimeresolution:messageexchangepattern</span></span>|<span data-ttu-id="2aba5-149">Modèle d’échange de message</span><span class="sxs-lookup"><span data-stu-id="2aba5-149">Message Exchange Pattern</span></span>|<span data-ttu-id="2aba5-150">Bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="2aba5-150">Two-Way</span></span>|<span data-ttu-id="2aba5-151">Opération bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="2aba5-151">Two-way operation</span></span>|  
    |<span data-ttu-id="2aba5-152">Microsoft-com:esb:runtimeresolution:cachetimeout</span><span class="sxs-lookup"><span data-stu-id="2aba5-152">microsoft-com:esb:runtimeresolution:cachetimeout</span></span>|<span data-ttu-id="2aba5-153">Délai d’expiration du cache</span><span class="sxs-lookup"><span data-stu-id="2aba5-153">Cache Timeout</span></span>|<span data-ttu-id="2aba5-154">-1</span><span class="sxs-lookup"><span data-stu-id="2aba5-154">-1</span></span>|<span data-ttu-id="2aba5-155">Actuellement désactivé</span><span class="sxs-lookup"><span data-stu-id="2aba5-155">Currently disabled</span></span>|  
    |<span data-ttu-id="2aba5-156">Microsoft-com:esb:runtimeresolution:jaxrpcresponse</span><span class="sxs-lookup"><span data-stu-id="2aba5-156">microsoft-com:esb:runtimeresolution:jaxrpcresponse</span></span>|<span data-ttu-id="2aba5-157">JaxRpcResponse</span><span class="sxs-lookup"><span data-stu-id="2aba5-157">JaxRpcResponse</span></span>|<span data-ttu-id="2aba5-158">false</span><span class="sxs-lookup"><span data-stu-id="2aba5-158">false</span></span>||  
    |<span data-ttu-id="2aba5-159">Microsoft-com:esb:runtimeresolution:action</span><span class="sxs-lookup"><span data-stu-id="2aba5-159">microsoft-com:esb:runtimeresolution:action</span></span>|<span data-ttu-id="2aba5-160">Action de service</span><span class="sxs-lookup"><span data-stu-id="2aba5-160">Service Action</span></span>|<span data-ttu-id="2aba5-161">submitOrder</span><span class="sxs-lookup"><span data-stu-id="2aba5-161">submitOrder</span></span>|<span data-ttu-id="2aba5-162">Spécifie la méthode de service à appeler</span><span class="sxs-lookup"><span data-stu-id="2aba5-162">Specifies the service method to invoke</span></span>|  
    |<span data-ttu-id="2aba5-163">Microsoft-com:esb:runtimeresolution:targetnamespace</span><span class="sxs-lookup"><span data-stu-id="2aba5-163">microsoft-com:esb:runtimeresolution:targetnamespace</span></span>|<span data-ttu-id="2aba5-164">Service Namespace</span><span class="sxs-lookup"><span data-stu-id="2aba5-164">Service Namespace</span></span>|<span data-ttu-id="2aba5-165">http://globalbank.ESB.dynamicresolution.com/canadianservices</span><span class="sxs-lookup"><span data-stu-id="2aba5-165">http://globalbank.esb.dynamicresolution.com/canadianservices</span></span>|<span data-ttu-id="2aba5-166">Espace de noms cible</span><span class="sxs-lookup"><span data-stu-id="2aba5-166">Target namespace</span></span>|  
  
#### <a name="to-configure-the-binding-categorization"></a><span data-ttu-id="2aba5-167">Pour configurer la catégorisation de liaison</span><span class="sxs-lookup"><span data-stu-id="2aba5-167">To configure the binding categorization</span></span>  
  
1.  <span data-ttu-id="2aba5-168">Dans le volet de la publication, sous **NewPOService**, cliquez sur **http://localhost/esb.canadianservices/submitposervice.asmx**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-168">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  
  
2.  <span data-ttu-id="2aba5-169">Sur le **catégories** , cliquez sur **ajouter une catégorie personnalisée**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-169">On the **Categories** tab, click **Add Custom Category**.</span></span>  
  
3.  <span data-ttu-id="2aba5-170">Dans le **recherche** , tapez **esb %** puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-170">In the **Search** box, type **%esb%** and then click **Search**.</span></span>  
  
4.  <span data-ttu-id="2aba5-171">Recherchez et cliquez sur le **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.</span><span class="sxs-lookup"><span data-stu-id="2aba5-171">Locate and click the **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.</span></span>  
  
5.  <span data-ttu-id="2aba5-172">Dans le **nom de la clé** , tapez **Application BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-172">In the **Key Name** box, type **BizTalk Application**.</span></span>  
  
6.  <span data-ttu-id="2aba5-173">Dans le **clé valeur** , tapez **Microsoft.Practices.ESB**, puis cliquez sur **ajouter une catégorie**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-173">In the **Key Value** box, type **Microsoft.Practices.ESB**, and then click **Add Category**.</span></span>  
  
7.  <span data-ttu-id="2aba5-174">Les étapes décrites précédemment, ajoutez les catégories personnalisées suivantes, selon les valeurs indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="2aba5-174">Using the steps described earlier, add the following custom categories, according to the values shown in the following table.</span></span>  
  
    |<span data-ttu-id="2aba5-175">élément tModel</span><span class="sxs-lookup"><span data-stu-id="2aba5-175">tModel</span></span>|<span data-ttu-id="2aba5-176">Nom de clé</span><span class="sxs-lookup"><span data-stu-id="2aba5-176">Key name</span></span>|<span data-ttu-id="2aba5-177">Valeur de clé</span><span class="sxs-lookup"><span data-stu-id="2aba5-177">Key value</span></span>|  
    |------------|--------------|---------------|  
    |<span data-ttu-id="2aba5-178">Microsoft-com:esb:runtimeresolution:portname</span><span class="sxs-lookup"><span data-stu-id="2aba5-178">microsoft-com:esb:runtimeresolution:portname</span></span>|<span data-ttu-id="2aba5-179">Nom du port</span><span class="sxs-lookup"><span data-stu-id="2aba5-179">Port Name</span></span>|<span data-ttu-id="2aba5-180">NewPOService</span><span class="sxs-lookup"><span data-stu-id="2aba5-180">NewPOService</span></span>|  
    |<span data-ttu-id="2aba5-181">Microsoft-com:esb:runtimeresolution:transporttype</span><span class="sxs-lookup"><span data-stu-id="2aba5-181">microsoft-com:esb:runtimeresolution:transporttype</span></span>|<span data-ttu-id="2aba5-182">Type de transport</span><span class="sxs-lookup"><span data-stu-id="2aba5-182">Transport Type</span></span>|<span data-ttu-id="2aba5-183">WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="2aba5-183">WCF-BasicHttp</span></span>|  
  
#### <a name="to-locate-the-service-in-the-uddi-registry"></a><span data-ttu-id="2aba5-184">Pour localiser le service dans le Registre UDDI</span><span class="sxs-lookup"><span data-stu-id="2aba5-184">To locate the service in the UDDI registry</span></span>  
  
1.  <span data-ttu-id="2aba5-185">Dans Internet Explorer, sur le **les Services uddi** , cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-185">In Internet Explorer, on the **uddi Services** page, click **Search**.</span></span>  
  
2.  <span data-ttu-id="2aba5-186">Cliquez sur le **Services** onglet.</span><span class="sxs-lookup"><span data-stu-id="2aba5-186">Click the **Services** tab.</span></span>  
  
3.  <span data-ttu-id="2aba5-187">Dans le **nom du Service** , tapez **% PO**, puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-187">In the **Service Name** box, type **%PO%**, and then click **Search**.</span></span>  
  
4.  <span data-ttu-id="2aba5-188">Dans le **recherche** volet, dans le **résultats** , cliquez sur **NewPOService**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-188">In the **Search** pane, on the **Results** tab, click **NewPOService**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2aba5-189">Cela confirme que le service a été publié avec succès dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="2aba5-189">This confirms the service was successfully published to the registry.</span></span>  
  
#### <a name="to-create-an-itinerary-model-to-test-the-uddi-service-publication"></a><span data-ttu-id="2aba5-190">Pour créer un modèle d’itinéraire pour tester la publication des services UDDI</span><span class="sxs-lookup"><span data-stu-id="2aba5-190">To create an itinerary model to test the UDDI service publication</span></span>  
  
1.  <span data-ttu-id="2aba5-191">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="2aba5-191">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="2aba5-192">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-192">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="2aba5-193">Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **NewBindingKeySearch**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-193">In the **Add New Item** dialog box, in the **Name** box, type **NewBindingKeySearch**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="2aba5-194">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="2aba5-194">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="2aba5-195">Dans Visual Studio, cliquez sur l’aire de conception de **NewBindingKeySearch.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-195">In Visual Studio, click the design surface of **NewBindingKeySearch.itinerary**.</span></span> <span data-ttu-id="2aba5-196">Dans le **NewBindingKeySearch** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-196">In the **NewBindingKeySearch** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-197">Dans le **réponse à la demande est** la liste déroulante, cliquez sur **True**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-197">In the **Is Request Response** drop-down list, click **True**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-198">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-198">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-199">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="2aba5-199">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    4.  <span data-ttu-id="2aba5-200">Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\NewBindingKeySearch** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-200">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\NewBindingKeySearch** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2aba5-201">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="2aba5-201">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="2aba5-202">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="2aba5-202">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="2aba5-203">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2aba5-203">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="2aba5-204">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="2aba5-204">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="2aba5-205">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="2aba5-205">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="2aba5-206">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-206">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-207">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-207">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-208">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-208">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-209">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-209">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="2aba5-210">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary.Response**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-210">In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.</span></span>  
  
2.  <span data-ttu-id="2aba5-211">Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="2aba5-211">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="2aba5-212">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-212">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-213">Cliquez sur le **nom** propriété, puis tapez **TransformNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-213">Click the **Name** property, and then type **TransformNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-214">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-214">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-215">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-215">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="2aba5-216">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-216">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="2aba5-217">Avec le bouton droit le **résolveur** collection de la **TransformNAOrder** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-217">Right-click the **Resolver** collection of the **TransformNAOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="2aba5-218">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-218">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-219">Cliquez sur le **nom** propriété, puis tapez **NAOrder_to_CNOrder**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-219">Click the **Name** property, and then type **NAOrder_to_CNOrder**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-220">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-220">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-221">Dans le **transformer un Type** la liste déroulante, cliquez sur **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-221">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
4.  <span data-ttu-id="2aba5-222">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-222">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="2aba5-223">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **TransformNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="2aba5-223">Drag a connection from the **ReceiveNAOrder** model element to the **TransformNAOrder** model element.</span></span>  
  
5.  <span data-ttu-id="2aba5-224">Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="2aba5-224">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="2aba5-225">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-225">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-226">Cliquez sur le **nom** propriété, puis tapez **BindingKeyRoute**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-226">Click the **Name** property, and then type **BindingKeyRoute**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-227">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-227">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-228">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-228">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="2aba5-229">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-229">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
6.  <span data-ttu-id="2aba5-230">Avec le bouton droit le **résolveur** collection de la **BindingKeyRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-230">Right-click the **Resolver** collection of the **BindingKeyRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="2aba5-231">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-231">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-232">Cliquez sur le **nom** propriété, puis tapez **BindingKeySearch**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-232">Click the **Name** property, and then type **BindingKeySearch**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-233">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Uddi3 programme de résolution d’Extension**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-233">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-234">Dans le **Moniker du programme de résolution** la liste déroulante, cliquez sur **UDDI3**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-234">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  
  
    4.  <span data-ttu-id="2aba5-235">Cliquez sur le **clé de liaison** propriété, puis tapez **uddi:esb:newposervicebinding**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-235">Click the **Binding key** property, and then type **uddi:esb:newposervicebinding**.</span></span> <span data-ttu-id="2aba5-236">Pour rechercher la valeur de clé, cliquez sur le service http://localhost/ESB.CanadianServices/SubmitPOService.asmx dans UDDI, puis cliquez sur plus de détails.</span><span class="sxs-lookup"><span data-stu-id="2aba5-236">To find the key value, click the http://localhost/ESB.CanadianServices/SubmitPOService.asmx service in UDDI, and then click More Details.</span></span>  
  
7.  <span data-ttu-id="2aba5-237">Cliquez sur le **BindingKeySearch** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-237">Right-click the **BindingKeySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2aba5-238">Vérifiez la sortie affichée dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="2aba5-238">Verify the output displayed in the Output window.</span></span>  
  
8.  <span data-ttu-id="2aba5-239">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-239">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="2aba5-240">Faites glisser une connexion à partir de la **TransformNAOrder** élément de modèle à la **BindingKeyRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="2aba5-240">Drag a connection from the **TransformNAOrder** model element to the **BindingKeyRoute** model element.</span></span>  
  
9. <span data-ttu-id="2aba5-241">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **BindingKeyRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="2aba5-241">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BindingKeyRoute** model element.</span></span> <span data-ttu-id="2aba5-242">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-242">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-243">Cliquez sur le **nom** propriété, puis tapez **SendCNOrder**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-243">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-244">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-244">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-245">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-245">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="2aba5-246">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionSolicitResp**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-246">In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.</span></span>  
  
10. <span data-ttu-id="2aba5-247">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **BindingKeyRoute** élément de modèle et la **SendCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="2aba5-247">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BindingKeyRoute** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="2aba5-248">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-248">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2aba5-249">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-249">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="2aba5-250">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-250">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="2aba5-251">Dans le **rampe** déroulante liste, développez **SendCNOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-251">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
11. <span data-ttu-id="2aba5-252">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-252">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="2aba5-253">Faites glisser une connexion à partir de la **BindingKeyRoute** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="2aba5-253">Drag a connection from the **BindingKeyRoute** model element to the **SendPortFilter** model element.</span></span>  
  
12. <span data-ttu-id="2aba5-254">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-254">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="2aba5-255">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="2aba5-255">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="2aba5-256">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="2aba5-256">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="2aba5-257">Dans Visual Studio, cliquez sur l’aire de conception de la **NewBindingKeySearch** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-257">In Visual Studio, right-click the design surface of the **NewBindingKeySearch** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2aba5-258">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2aba5-258">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2aba5-259">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="2aba5-259">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="2aba5-260">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (NewBindingKeySearch.xml).</span><span class="sxs-lookup"><span data-stu-id="2aba5-260">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (NewBindingKeySearch.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="2aba5-261">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="2aba5-261">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="2aba5-262">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="2aba5-262">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="2aba5-263">Dans le Client Test de la feuille de route, dans le **Options du Service Web** groupe, désactivez le **utiliser le Service WCF** zone, puis sélectionnez le **bidirectionnel Service** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="2aba5-263">In the Itinerary Test Client, in the **Web Service Options** group, clear the **Use WCF Service** box and then select the **Two-Way Service** check box.</span></span>  
  
3.  <span data-ttu-id="2aba5-264">Cliquez sur le **charge itinéraire** bouton.</span><span class="sxs-lookup"><span data-stu-id="2aba5-264">Click the **Load Itinerary** button.</span></span>  
  
4.  <span data-ttu-id="2aba5-265">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="2aba5-265">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="2aba5-266">Sélectionnez **NewBindingKeySearch.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="2aba5-266">Select **NewBindingKeySearch.xml**, and then click **Open** to load the itinerary.</span></span>  
  
5.  <span data-ttu-id="2aba5-267">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="2aba5-267">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
6.  <span data-ttu-id="2aba5-268">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="2aba5-268">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
7.  <span data-ttu-id="2aba5-269">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="2aba5-269">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="2aba5-270">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="2aba5-270">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
8.  <span data-ttu-id="2aba5-271">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="2aba5-271">Click the **Submit Request** button.</span></span> <span data-ttu-id="2aba5-272">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2aba5-272">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
9. <span data-ttu-id="2aba5-273">Vérifiez que le message de réponse correcte s’affiche dans le **résultat** zone de texte de la **Itineray Test Client**.</span><span class="sxs-lookup"><span data-stu-id="2aba5-273">Verify that the correct response message appears in the **Result** text box of the **Itineray Test Client**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="2aba5-274">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2aba5-274">Additional Resources</span></span>  
 <span data-ttu-id="2aba5-275">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2aba5-275">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="2aba5-276">Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de clé de liaison de UDDI</span><span class="sxs-lookup"><span data-stu-id="2aba5-276">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [<span data-ttu-id="2aba5-277">Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de catégorie UDDI</span><span class="sxs-lookup"><span data-stu-id="2aba5-277">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [<span data-ttu-id="2aba5-278">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="2aba5-278">Development Activities</span></span>](../esb-toolkit/development-activities.md)