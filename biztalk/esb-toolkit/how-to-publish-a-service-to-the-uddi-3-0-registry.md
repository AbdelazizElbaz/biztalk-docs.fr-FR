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
ms.openlocfilehash: da3d2dc400c031ab5febda1568cb18ce5180366b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-publish-a-service-to-the-uddi-30-registry"></a><span data-ttu-id="17d1b-102">Comment : publier un Service à UDDI 3.0 Registre</span><span class="sxs-lookup"><span data-stu-id="17d1b-102">How to: Publish a Service to the UDDI 3.0 Registry</span></span>
## <a name="goal"></a><span data-ttu-id="17d1b-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="17d1b-103">Goal</span></span>  
 <span data-ttu-id="17d1b-104">Cette section montre comment utiliser le site des services UDDI pour publier un point de terminaison de service Web qui peut être résolu à partir d’un itinéraire à des fins de routage d’un message d’ESB.</span><span class="sxs-lookup"><span data-stu-id="17d1b-104">This section demonstrates how to use the UDDI Service site to publish a Web service endpoint that can be resolved from within an itinerary for the purpose of routing an ESB message.</span></span> <span data-ttu-id="17d1b-105">Vous allez dupliquer le service PurchaseOrderSubmitOrderService existant actuellement publié dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="17d1b-105">You will duplicate the existing PurchaseOrderSubmitOrderService service presently published to the registry.</span></span>  
  
 <span data-ttu-id="17d1b-106">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="17d1b-107">Publier un service sur le Universal Description, Discovery, and Integration (UDDI) 3 Registre à l’aide de l’outil de serveur de publication UDDI.</span><span class="sxs-lookup"><span data-stu-id="17d1b-107">Publish a service to the Universal Description, Discovery, and Integration (UDDI) 3 registry using the UDDI Publisher tool.</span></span>  
  
-   <span data-ttu-id="17d1b-108">Test de la publication de service à l’aide d’un bordereau d’itinéraire de routage qui résout le point de terminaison de service à l’aide d’un programme de résolution UDDI3.</span><span class="sxs-lookup"><span data-stu-id="17d1b-108">Test the service publication using an itinerary routing slip that resolves the service endpoint using a UDDI3 resolver.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="17d1b-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="17d1b-109">Prerequisites</span></span>  
 <span data-ttu-id="17d1b-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) et l’exécution de l’outil de serveur de publication UDDI (vous pouvez l’installer à % ESB installer Folder%\Bin\ Microsoft.Practices.ESB.UDDIPublisher.exe).</span><span class="sxs-lookup"><span data-stu-id="17d1b-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) and the execution of the UDDI Publisher tool (you can install it at %ESB Install Folder%\Bin\Microsoft.Practices.ESB.UDDIPublisher.exe).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="17d1b-111">Étapes</span><span class="sxs-lookup"><span data-stu-id="17d1b-111">Steps</span></span>  
  
#### <a name="to-create-the-newposervice-in-the-uddi-registry"></a><span data-ttu-id="17d1b-112">Pour créer le NewPOService dans le Registre UDDI</span><span class="sxs-lookup"><span data-stu-id="17d1b-112">To create the NewPOService in the UDDI registry</span></span>  
  
1.  <span data-ttu-id="17d1b-113">Dans Internet Explorer, accédez au site des services UDDI (par défaut, l’URL pour cette est http://localhost/uddi).</span><span class="sxs-lookup"><span data-stu-id="17d1b-113">In Internet Explorer, browse to the UDDI Service site (by default, the URL for this is http://localhost/uddi).</span></span>  
  
2.  <span data-ttu-id="17d1b-114">Sur le **les Services uddi** , cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-114">On the **uddi Services** page, click **Publish**.</span></span>  
  
3.  <span data-ttu-id="17d1b-115">Dans le volet de la publication, cliquez sur **Microsoft.Practices.ESB**, puis cliquez sur **ajouter un Service**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-115">In the Publish pane, right-click **Microsoft.Practices.ESB**, and then click **Add Service**.</span></span>  
  
4.  <span data-ttu-id="17d1b-116">Sur la page suivante, sélectionnez **spécifier la clé à utiliser**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-116">On the following page, select **Specify a key to use**, and then click **Continue**.</span></span>  
  
5.  <span data-ttu-id="17d1b-117">Dans la page suivante, cliquez sur le **esb** clé de partition.</span><span class="sxs-lookup"><span data-stu-id="17d1b-117">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="17d1b-118">Dans le **clé suffixe** , tapez **newposervice**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-118">In the **Key Suffix** box, type **newposervice**, and then click **Continue**.</span></span>  
  
6.  <span data-ttu-id="17d1b-119">Sur la page suivante, à côté (**nouveau nom de Service**), cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-119">On the following page, next to (**New Service Name**), click **Edit**.</span></span> <span data-ttu-id="17d1b-120">Nom de service **NewPOService**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-120">Name the service **NewPOService**, and then click **Update**.</span></span>  
  
7.  <span data-ttu-id="17d1b-121">Cliquez sur **ajouter une Description**, tapez une description pour le service (par exemple, **exemple de Service**), puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-121">Click **Add Description**, type a description for the service (for example, **Sample Service**), and then click **Update**.</span></span>  
  
#### <a name="to-add-a-binding-for-the-newposervice"></a><span data-ttu-id="17d1b-122">Pour ajouter une liaison pour le NewPOService</span><span class="sxs-lookup"><span data-stu-id="17d1b-122">To add a binding for the NewPOService</span></span>  
  
1.  <span data-ttu-id="17d1b-123">Cliquez sur le **liaisons** onglet, puis cliquez sur **ajouter la liaison**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-123">Click the **Bindings** tab, and then click **Add Binding**.</span></span>  
  
2.  <span data-ttu-id="17d1b-124">Sélectionnez **spécifier la clé à utiliser**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-124">Select **Specify a key to use**, and then click **Continue**.</span></span>  
  
3.  <span data-ttu-id="17d1b-125">Dans la page suivante, cliquez sur le **esb** clé de partition.</span><span class="sxs-lookup"><span data-stu-id="17d1b-125">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="17d1b-126">Dans le **clé suffixe** , tapez **newposervicebinding**, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-126">In the **Key Suffix** box, type **newposervicebinding**, and then click **Continue**.</span></span>  
  
4.  <span data-ttu-id="17d1b-127">Sous **le Point d’accès**, cliquez sur **modifier**et puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="17d1b-127">Under **Access Point**, click **Edit**, and then complete the following:</span></span>  
  
    1.  <span data-ttu-id="17d1b-128">Dans le **le Point d’accès** , tapez **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-128">In the **Access Point** box, type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-129">Dans le **Type d’utilisation** la liste déroulante, cliquez sur **point de terminaison**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-129">In the **Use Type** drop-down list, click **endpoint**, and then click **Update**.</span></span>  
  
#### <a name="to-configure-the-binding-instance-information"></a><span data-ttu-id="17d1b-130">Pour configurer les informations d’instance de liaison</span><span class="sxs-lookup"><span data-stu-id="17d1b-130">To configure the binding instance information</span></span>  
  
1.  <span data-ttu-id="17d1b-131">Cliquez sur le **Infos sur l’Instance** onglet, puis cliquez sur **ajouter des informations d’Instance**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-131">Click the **Instance Info** tab, and then click **Add Instance Info**.</span></span>  
  
2.  <span data-ttu-id="17d1b-132">Dans le **recherche les noms de tModel contenant** , tapez **esb %** puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-132">In the **Search for tModel names containing** box, type **%esb%** and then click **Search**.</span></span>  
  
3.  <span data-ttu-id="17d1b-133">Recherchez et cliquez sur le **tModel** pour **transporttype**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-133">Locate and click the **tModel** for **transporttype**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17d1b-134">Pour effectuer les étapes restantes de cette procédure, vous devrez peut-être passer à la page 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="17d1b-134">To complete the remaining steps in this procedure, you may be required to change between page 1 and page 2.</span></span>  
  
4.  <span data-ttu-id="17d1b-135">Dans le **Descriptions** , cliquez sur **ajouter une Description**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-135">In the **Descriptions** section, click **Add Description**.</span></span>  
  
5.  <span data-ttu-id="17d1b-136">Dans le **Description** , tapez **Type de Transport pour une utilisation d’itinéraire ESB**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-136">In the **Description** box, type **Transport Type for ESB Itinerary Use**, and then click **Update**.</span></span>  
  
6.  <span data-ttu-id="17d1b-137">Cliquez sur le **détails de l’Instance** onglet, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-137">Click the **Instance Details** tab, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="17d1b-138">Dans le **paramètres de l’Instance** , tapez **WCF-BasicHttp**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-138">In the **Instance Parameters** box, type **WCF-BasicHttp**, and then click **Update**.</span></span>  
  
8.  <span data-ttu-id="17d1b-139">Dans le **Descriptions** , cliquez sur **ajouter une Description**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-139">In the **Descriptions** section, click **Add Description**.</span></span>  
  
9. <span data-ttu-id="17d1b-140">Dans le **Description** , tapez **WCF de base du Transport HTTP**, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-140">In the **Description** box, type **WCF Basic HTTP Transport**, and then click **Update**.</span></span>  
  
10. <span data-ttu-id="17d1b-141">Dans le volet de la publication, sous **NewPOService**, cliquez sur **http://localhost/esb.canadianservices/submitposervice.asmx**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-141">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  
  
11. <span data-ttu-id="17d1b-142">Sur le **Infos sur l’Instance** , cliquez sur **ajouter des informations d’Instance**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-142">On the **Instance Info** tab, click **Add Instance Info**.</span></span>  
  
12. <span data-ttu-id="17d1b-143">À l’aide de la procédure décrite précédemment, ajoutez les informations d’instance suivantes, selon les valeurs indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="17d1b-143">Using the steps described earlier, add the following instance information, according to the values shown in the following table.</span></span>  
  
    |<span data-ttu-id="17d1b-144">élément tModel</span><span class="sxs-lookup"><span data-stu-id="17d1b-144">tModel</span></span>|<span data-ttu-id="17d1b-145"> Description</span><span class="sxs-lookup"><span data-stu-id="17d1b-145">Description</span></span>|<span data-ttu-id="17d1b-146">Paramètre</span><span class="sxs-lookup"><span data-stu-id="17d1b-146">Parameter</span></span>|<span data-ttu-id="17d1b-147">Description du paramètre</span><span class="sxs-lookup"><span data-stu-id="17d1b-147">Parameter description</span></span>|  
    |------------|-----------------|---------------|---------------------------|  
    |<span data-ttu-id="17d1b-148">Microsoft-com:esb:runtimeresolution:messageexchangepattern</span><span class="sxs-lookup"><span data-stu-id="17d1b-148">microsoft-com:esb:runtimeresolution:messageexchangepattern</span></span>|<span data-ttu-id="17d1b-149">Modèle d’échange de message</span><span class="sxs-lookup"><span data-stu-id="17d1b-149">Message Exchange Pattern</span></span>|<span data-ttu-id="17d1b-150">Bidirectionnel</span><span class="sxs-lookup"><span data-stu-id="17d1b-150">Two-Way</span></span>|<span data-ttu-id="17d1b-151">Opération bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="17d1b-151">Two-way operation</span></span>|  
    |<span data-ttu-id="17d1b-152">Microsoft-com:esb:runtimeresolution:cachetimeout</span><span class="sxs-lookup"><span data-stu-id="17d1b-152">microsoft-com:esb:runtimeresolution:cachetimeout</span></span>|<span data-ttu-id="17d1b-153">Délai d’expiration du cache</span><span class="sxs-lookup"><span data-stu-id="17d1b-153">Cache Timeout</span></span>|<span data-ttu-id="17d1b-154">-1</span><span class="sxs-lookup"><span data-stu-id="17d1b-154">-1</span></span>|<span data-ttu-id="17d1b-155">Actuellement désactivé</span><span class="sxs-lookup"><span data-stu-id="17d1b-155">Currently disabled</span></span>|  
    |<span data-ttu-id="17d1b-156">Microsoft-com:esb:runtimeresolution:jaxrpcresponse</span><span class="sxs-lookup"><span data-stu-id="17d1b-156">microsoft-com:esb:runtimeresolution:jaxrpcresponse</span></span>|<span data-ttu-id="17d1b-157">JaxRpcResponse</span><span class="sxs-lookup"><span data-stu-id="17d1b-157">JaxRpcResponse</span></span>|<span data-ttu-id="17d1b-158">false</span><span class="sxs-lookup"><span data-stu-id="17d1b-158">false</span></span>||  
    |<span data-ttu-id="17d1b-159">Microsoft-com:esb:runtimeresolution:action</span><span class="sxs-lookup"><span data-stu-id="17d1b-159">microsoft-com:esb:runtimeresolution:action</span></span>|<span data-ttu-id="17d1b-160">Action de service</span><span class="sxs-lookup"><span data-stu-id="17d1b-160">Service Action</span></span>|<span data-ttu-id="17d1b-161">submitOrder</span><span class="sxs-lookup"><span data-stu-id="17d1b-161">submitOrder</span></span>|<span data-ttu-id="17d1b-162">Spécifie la méthode de service à appeler</span><span class="sxs-lookup"><span data-stu-id="17d1b-162">Specifies the service method to invoke</span></span>|  
    |<span data-ttu-id="17d1b-163">Microsoft-com:esb:runtimeresolution:targetnamespace</span><span class="sxs-lookup"><span data-stu-id="17d1b-163">microsoft-com:esb:runtimeresolution:targetnamespace</span></span>|<span data-ttu-id="17d1b-164">Service Namespace</span><span class="sxs-lookup"><span data-stu-id="17d1b-164">Service Namespace</span></span>|<span data-ttu-id="17d1b-165">http://globalbank.ESB.dynamicresolution.com/canadianservices</span><span class="sxs-lookup"><span data-stu-id="17d1b-165">http://globalbank.esb.dynamicresolution.com/canadianservices</span></span>|<span data-ttu-id="17d1b-166">Espace de noms cible</span><span class="sxs-lookup"><span data-stu-id="17d1b-166">Target namespace</span></span>|  
  
#### <a name="to-configure-the-binding-categorization"></a><span data-ttu-id="17d1b-167">Pour configurer la catégorisation de liaison</span><span class="sxs-lookup"><span data-stu-id="17d1b-167">To configure the binding categorization</span></span>  
  
1.  <span data-ttu-id="17d1b-168">Dans le volet de la publication, sous **NewPOService**, cliquez sur **http://localhost/esb.canadianservices/submitposervice.asmx**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-168">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  
  
2.  <span data-ttu-id="17d1b-169">Sur le **catégories** , cliquez sur **ajouter une catégorie personnalisée**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-169">On the **Categories** tab, click **Add Custom Category**.</span></span>  
  
3.  <span data-ttu-id="17d1b-170">Dans le **recherche** , tapez **esb %** puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-170">In the **Search** box, type **%esb%** and then click **Search**.</span></span>  
  
4.  <span data-ttu-id="17d1b-171">Recherchez et cliquez sur le **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.</span><span class="sxs-lookup"><span data-stu-id="17d1b-171">Locate and click the **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.</span></span>  
  
5.  <span data-ttu-id="17d1b-172">Dans le **nom de la clé** , tapez **Application BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-172">In the **Key Name** box, type **BizTalk Application**.</span></span>  
  
6.  <span data-ttu-id="17d1b-173">Dans le **clé valeur** , tapez **Microsoft.Practices.ESB**, puis cliquez sur **ajouter une catégorie**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-173">In the **Key Value** box, type **Microsoft.Practices.ESB**, and then click **Add Category**.</span></span>  
  
7.  <span data-ttu-id="17d1b-174">Les étapes décrites précédemment, ajoutez les catégories personnalisées suivantes, selon les valeurs indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="17d1b-174">Using the steps described earlier, add the following custom categories, according to the values shown in the following table.</span></span>  
  
    |<span data-ttu-id="17d1b-175">élément tModel</span><span class="sxs-lookup"><span data-stu-id="17d1b-175">tModel</span></span>|<span data-ttu-id="17d1b-176">Nom de clé</span><span class="sxs-lookup"><span data-stu-id="17d1b-176">Key name</span></span>|<span data-ttu-id="17d1b-177">Valeur de clé</span><span class="sxs-lookup"><span data-stu-id="17d1b-177">Key value</span></span>|  
    |------------|--------------|---------------|  
    |<span data-ttu-id="17d1b-178">Microsoft-com:esb:runtimeresolution:portname</span><span class="sxs-lookup"><span data-stu-id="17d1b-178">microsoft-com:esb:runtimeresolution:portname</span></span>|<span data-ttu-id="17d1b-179">Nom du port</span><span class="sxs-lookup"><span data-stu-id="17d1b-179">Port Name</span></span>|<span data-ttu-id="17d1b-180">NewPOService</span><span class="sxs-lookup"><span data-stu-id="17d1b-180">NewPOService</span></span>|  
    |<span data-ttu-id="17d1b-181">Microsoft-com:esb:runtimeresolution:transporttype</span><span class="sxs-lookup"><span data-stu-id="17d1b-181">microsoft-com:esb:runtimeresolution:transporttype</span></span>|<span data-ttu-id="17d1b-182">Type de transport</span><span class="sxs-lookup"><span data-stu-id="17d1b-182">Transport Type</span></span>|<span data-ttu-id="17d1b-183">WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="17d1b-183">WCF-BasicHttp</span></span>|  
  
#### <a name="to-locate-the-service-in-the-uddi-registry"></a><span data-ttu-id="17d1b-184">Pour localiser le service dans le Registre UDDI</span><span class="sxs-lookup"><span data-stu-id="17d1b-184">To locate the service in the UDDI registry</span></span>  
  
1.  <span data-ttu-id="17d1b-185">Dans Internet Explorer, sur le **les Services uddi** , cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-185">In Internet Explorer, on the **uddi Services** page, click **Search**.</span></span>  
  
2.  <span data-ttu-id="17d1b-186">Cliquez sur le **Services** onglet.</span><span class="sxs-lookup"><span data-stu-id="17d1b-186">Click the **Services** tab.</span></span>  
  
3.  <span data-ttu-id="17d1b-187">Dans le **nom du Service** , tapez **% PO**, puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-187">In the **Service Name** box, type **%PO%**, and then click **Search**.</span></span>  
  
4.  <span data-ttu-id="17d1b-188">Dans le **recherche** volet, dans le **résultats** , cliquez sur **NewPOService**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-188">In the **Search** pane, on the **Results** tab, click **NewPOService**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17d1b-189">Cela confirme que le service a été publié avec succès dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="17d1b-189">This confirms the service was successfully published to the registry.</span></span>  
  
#### <a name="to-create-an-itinerary-model-to-test-the-uddi-service-publication"></a><span data-ttu-id="17d1b-190">Pour créer un modèle d’itinéraire pour tester la publication des services UDDI</span><span class="sxs-lookup"><span data-stu-id="17d1b-190">To create an itinerary model to test the UDDI service publication</span></span>  
  
1.  <span data-ttu-id="17d1b-191">Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="17d1b-191">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="17d1b-192">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-192">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="17d1b-193">Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **NewBindingKeySearch**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-193">In the **Add New Item** dialog box, in the **Name** box, type **NewBindingKeySearch**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="17d1b-194">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="17d1b-194">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="17d1b-195">Dans Visual Studio, cliquez sur l’aire de conception de **NewBindingKeySearch.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-195">In Visual Studio, click the design surface of **NewBindingKeySearch.itinerary**.</span></span> <span data-ttu-id="17d1b-196">Dans le **NewBindingKeySearch** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-196">In the **NewBindingKeySearch** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-197">Dans le **réponse à la demande est** la liste déroulante, cliquez sur **True**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-197">In the **Is Request Response** drop-down list, click **True**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-198">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-198">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-199">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="17d1b-199">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    4.  <span data-ttu-id="17d1b-200">Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\NewBindingKeySearch** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-200">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\NewBindingKeySearch** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="17d1b-201">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="17d1b-201">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="17d1b-202">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="17d1b-202">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="17d1b-203">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="17d1b-203">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="17d1b-204">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="17d1b-204">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="17d1b-205">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="17d1b-205">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="17d1b-206">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-206">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-207">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-207">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-208">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-208">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-209">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-209">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="17d1b-210">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary.Response**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-210">In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.</span></span>  
  
2.  <span data-ttu-id="17d1b-211">Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="17d1b-211">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="17d1b-212">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-212">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-213">Cliquez sur le **nom** propriété, puis tapez **TransformNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-213">Click the **Name** property, and then type **TransformNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-214">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-214">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-215">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-215">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="17d1b-216">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-216">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="17d1b-217">Avec le bouton droit le **résolveur** collection de la **TransformNAOrder** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-217">Right-click the **Resolver** collection of the **TransformNAOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="17d1b-218">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-218">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-219">Cliquez sur le **nom** propriété, puis tapez **NAOrder_to_CNOrder**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-219">Click the **Name** property, and then type **NAOrder_to_CNOrder**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-220">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-220">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-221">Dans le **transformer un Type** la liste déroulante, cliquez sur **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-221">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
4.  <span data-ttu-id="17d1b-222">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-222">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="17d1b-223">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **TransformNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="17d1b-223">Drag a connection from the **ReceiveNAOrder** model element to the **TransformNAOrder** model element.</span></span>  
  
5.  <span data-ttu-id="17d1b-224">Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="17d1b-224">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="17d1b-225">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-225">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-226">Cliquez sur le **nom** propriété, puis tapez **BindingKeyRoute**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-226">Click the **Name** property, and then type **BindingKeyRoute**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-227">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-227">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-228">Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-228">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="17d1b-229">Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-229">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
6.  <span data-ttu-id="17d1b-230">Avec le bouton droit le **résolveur** collection de la **BindingKeyRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-230">Right-click the **Resolver** collection of the **BindingKeyRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="17d1b-231">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-231">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-232">Cliquez sur le **nom** propriété, puis tapez **BindingKeySearch**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-232">Click the **Name** property, and then type **BindingKeySearch**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-233">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Uddi3 programme de résolution d’Extension**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-233">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-234">Dans le **Moniker du programme de résolution** la liste déroulante, cliquez sur **UDDI3**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-234">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  
  
    4.  <span data-ttu-id="17d1b-235">Cliquez sur le **clé de liaison** propriété, puis tapez **uddi:esb:newposervicebinding**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-235">Click the **Binding key** property, and then type **uddi:esb:newposervicebinding**.</span></span> <span data-ttu-id="17d1b-236">Pour rechercher la valeur de clé, cliquez sur le service http://localhost/ESB.CanadianServices/SubmitPOService.asmx dans UDDI, puis cliquez sur plus de détails.</span><span class="sxs-lookup"><span data-stu-id="17d1b-236">To find the key value, click the http://localhost/ESB.CanadianServices/SubmitPOService.asmx service in UDDI, and then click More Details.</span></span>  
  
7.  <span data-ttu-id="17d1b-237">Cliquez sur le **BindingKeySearch** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-237">Right-click the **BindingKeySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17d1b-238">Vérifiez la sortie affichée dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="17d1b-238">Verify the output displayed in the Output window.</span></span>  
  
8.  <span data-ttu-id="17d1b-239">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-239">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="17d1b-240">Faites glisser une connexion à partir de la **TransformNAOrder** élément de modèle à la **BindingKeyRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="17d1b-240">Drag a connection from the **TransformNAOrder** model element to the **BindingKeyRoute** model element.</span></span>  
  
9. <span data-ttu-id="17d1b-241">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **BindingKeyRoute** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="17d1b-241">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BindingKeyRoute** model element.</span></span> <span data-ttu-id="17d1b-242">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-242">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-243">Cliquez sur le **nom** propriété, puis tapez **SendCNOrder**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-243">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-244">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-244">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-245">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-245">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="17d1b-246">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionSolicitResp**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-246">In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.</span></span>  
  
10. <span data-ttu-id="17d1b-247">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **BindingKeyRoute** élément de modèle et la **SendCNOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="17d1b-247">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BindingKeyRoute** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="17d1b-248">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-248">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="17d1b-249">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-249">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="17d1b-250">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-250">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="17d1b-251">Dans le **rampe** déroulante liste, développez **SendCNOrder**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-251">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
11. <span data-ttu-id="17d1b-252">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-252">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="17d1b-253">Faites glisser une connexion à partir de la **BindingKeyRoute** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="17d1b-253">Drag a connection from the **BindingKeyRoute** model element to the **SendPortFilter** model element.</span></span>  
  
12. <span data-ttu-id="17d1b-254">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-254">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="17d1b-255">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="17d1b-255">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="17d1b-256">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="17d1b-256">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="17d1b-257">Dans Visual Studio, cliquez sur l’aire de conception de la **NewBindingKeySearch** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-257">In Visual Studio, right-click the design surface of the **NewBindingKeySearch** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17d1b-258">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17d1b-258">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="17d1b-259">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="17d1b-259">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="17d1b-260">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (NewBindingKeySearch.xml).</span><span class="sxs-lookup"><span data-stu-id="17d1b-260">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (NewBindingKeySearch.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="17d1b-261">Pour tester la feuille de route</span><span class="sxs-lookup"><span data-stu-id="17d1b-261">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="17d1b-262">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="17d1b-262">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="17d1b-263">Dans le Client Test de la feuille de route, dans le **Options du Service Web** groupe, désactivez le **utiliser le Service WCF** zone, puis sélectionnez le **bidirectionnel Service** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="17d1b-263">In the Itinerary Test Client, in the **Web Service Options** group, clear the **Use WCF Service** box and then select the **Two-Way Service** check box.</span></span>  
  
3.  <span data-ttu-id="17d1b-264">Cliquez sur le **charge itinéraire** bouton.</span><span class="sxs-lookup"><span data-stu-id="17d1b-264">Click the **Load Itinerary** button.</span></span>  
  
4.  <span data-ttu-id="17d1b-265">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="17d1b-265">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="17d1b-266">Sélectionnez **NewBindingKeySearch.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="17d1b-266">Select **NewBindingKeySearch.xml**, and then click **Open** to load the itinerary.</span></span>  
  
5.  <span data-ttu-id="17d1b-267">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="17d1b-267">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
6.  <span data-ttu-id="17d1b-268">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="17d1b-268">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
7.  <span data-ttu-id="17d1b-269">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="17d1b-269">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="17d1b-270">Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="17d1b-270">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
8.  <span data-ttu-id="17d1b-271">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="17d1b-271">Click the **Submit Request** button.</span></span> <span data-ttu-id="17d1b-272">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="17d1b-272">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
9. <span data-ttu-id="17d1b-273">Vérifiez que le message de réponse correcte s’affiche dans le **résultat** zone de texte de la **Itineray Test Client**.</span><span class="sxs-lookup"><span data-stu-id="17d1b-273">Verify that the correct response message appears in the **Result** text box of the **Itineray Test Client**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="17d1b-274">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="17d1b-274">Additional Resources</span></span>  
 <span data-ttu-id="17d1b-275">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="17d1b-275">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="17d1b-276">Guide pratique pour résoudre un point de terminaison de service à l’aide d’une recherche de clé de liaison UDDI</span><span class="sxs-lookup"><span data-stu-id="17d1b-276">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [<span data-ttu-id="17d1b-277">Guide pratique pour résoudre un point de terminaison de service à l’aide d’une recherche de catégorie UDDI</span><span class="sxs-lookup"><span data-stu-id="17d1b-277">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [<span data-ttu-id="17d1b-278">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="17d1b-278">Development Activities</span></span>](../esb-toolkit/development-activities.md)