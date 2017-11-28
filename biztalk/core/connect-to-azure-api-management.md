---
title: Publier des points de terminaison SOAP gestion des API | Documents Microsoft
description: "Utilisez Feature Pack 1 et Feature Pack 2 pour exposer un HTTP de WCF-Basic BizTalk reçoivent emplacement en tant que point de terminaison SOAP au sein de la gestion des API. Vous pouvez le faire à l’aide de la console Administration de BizTalk, ou collez votre point de terminaison directement au sein de la gestion des API dans le portail Azure."
ms.custom: 
ms.date: 11/21/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a87bfb40-7e6f-46aa-8ac7-db6d13ce7eb2
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: valrobb
manager: anneta
ms.openlocfilehash: 8ac1e824ad11ef18eac6deb1252101bbd1ec187a
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="publish-biztalk-soap-endpoints-in-api-management"></a><span data-ttu-id="10c0c-104">Publier des points de terminaison SOAP BizTalk dans la gestion des API</span><span class="sxs-lookup"><span data-stu-id="10c0c-104">Publish BizTalk SOAP endpoints in API Management</span></span>

<span data-ttu-id="10c0c-105">Exposer vos points de terminaison SOAP BizTalk en tant que services au sein de la gestion des API Azure.</span><span class="sxs-lookup"><span data-stu-id="10c0c-105">Expose your BizTalk SOAP endpoints as services within Azure API Management.</span></span> 

<span data-ttu-id="10c0c-106">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 1**, vous pouvez exposer un point de terminaison SOAP via la gestion des API à partir de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="10c0c-106">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 1**, you can expose a SOAP endpoint through API Management from BizTalk.</span></span> <span data-ttu-id="10c0c-107">Pour cela, à l’aide de la gestion des API dans le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="10c0c-107">You can do this using  API Management in the Azure portal.</span></span> 

<span data-ttu-id="10c0c-108">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, vous pouvez exposer un WCF-BasicHTTP emplacement au sein de la gestion des API Azure à l’aide de la console Administration de BizTalk, un point de terminaison de réception.</span><span class="sxs-lookup"><span data-stu-id="10c0c-108">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, you can expose a WCF-BasicHTTP receive location as an endpoint within Azure API Management using BizTalk Administration.</span></span> 

> [!TIP]
> <span data-ttu-id="10c0c-109">[Quelle est la gestion des API ? ](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts) est un bon point de départ pour comprendre et en savoir plus sur ce service Azure.</span><span class="sxs-lookup"><span data-stu-id="10c0c-109">[What is API Management?](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts) is a great resource to understand and learn more about this Azure service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10c0c-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="10c0c-110">Prerequisites</span></span>
* <span data-ttu-id="10c0c-111">Configurer [gestion des API Azure](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)</span><span class="sxs-lookup"><span data-stu-id="10c0c-111">Configure and set up [Azure API Management](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)</span></span>
* <span data-ttu-id="10c0c-112">Créer un [réseau virtuel](https://docs.microsoft.com/azure/api-management/api-management-using-with-vnet) entre votre ordinateur BizTalk et de l’instance de la gestion des API</span><span class="sxs-lookup"><span data-stu-id="10c0c-112">Create a [virtual network](https://docs.microsoft.com/azure/api-management/api-management-using-with-vnet) between your BizTalk computer and the API Management instance</span></span>
* <span data-ttu-id="10c0c-113">Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur le serveur BizTalk</span><span class="sxs-lookup"><span data-stu-id="10c0c-113">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on the BizTalk Server</span></span>

## <a name="create-using-api-management-in-azure-portal"></a><span data-ttu-id="10c0c-114">Créer à l’aide de la gestion des API dans le portail Azure</span><span class="sxs-lookup"><span data-stu-id="10c0c-114">Create using API Management in Azure portal</span></span> 
1. <span data-ttu-id="10c0c-115">Dans le [portail Azure](https://portal.azure.com), ouvrez la gestion de l’API, puis sélectionnez **API**:</span><span class="sxs-lookup"><span data-stu-id="10c0c-115">In the [Azure portal](https://portal.azure.com), open up your API management, and select **APIs**:</span></span>

    ![Sélectionnez les API pour BizTalk](../core/media/select-api-for-biztalk.png)
    
2. <span data-ttu-id="10c0c-117">Sélectionnez **WSDL**:</span><span class="sxs-lookup"><span data-stu-id="10c0c-117">Select **WSDL**:</span></span>

    ![Sélectionnez wsdl biztalk api](../core/media/select-wsdl-biztalk-api.png)
    
3. <span data-ttu-id="10c0c-119">Configurer les propriétés WSDL :</span><span class="sxs-lookup"><span data-stu-id="10c0c-119">Configure your WSDL properties:</span></span> 

    1. <span data-ttu-id="10c0c-120">**Spécification WSDL** : entrez l’URI complet pour votre point de terminaison SOAP BizTalk.</span><span class="sxs-lookup"><span data-stu-id="10c0c-120">**WSDL specification** : Enter the full URI to your BizTalk SOAP endpoint.</span></span> <span data-ttu-id="10c0c-121">Par exemple, entrez un nom tel que `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl` ou `http://biztalkfp1.westus.cloudapp.azure.com/RestEndPoint/OrderIncome.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="10c0c-121">For example, enter something like `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl` or `http://biztalkfp1.westus.cloudapp.azure.com/RestEndPoint/OrderIncome.svc?wsdl`.</span></span>  

    2. <span data-ttu-id="10c0c-122">**Pass-through SOAP** ou **SOAP reste** : sélectionnez votre préférence :</span><span class="sxs-lookup"><span data-stu-id="10c0c-122">**SOAP pass-through** or **SOAP to REST** : Select your preference:</span></span> 
        * <span data-ttu-id="10c0c-123">**SOAP reste**: créer le reste APIs basées sur HTTP à partir d’un service web basé sur SOAP existant</span><span class="sxs-lookup"><span data-stu-id="10c0c-123">**SOAP to REST**: Create REST-based HTTP APIs from an existing SOAP-based web service</span></span>
        * <span data-ttu-id="10c0c-124">**Pass-through SOAP**: agit comme un proxy pour l’API SOAP</span><span class="sxs-lookup"><span data-stu-id="10c0c-124">**SOAP pass-through**: Acts as a proxy for the SOAP API</span></span> 

    3. <span data-ttu-id="10c0c-125">Entrez votre choix **nom d’affichage**, **nom**, **Description**, **suffixe d’Url de l’API**, **produits**, et **Version**.</span><span class="sxs-lookup"><span data-stu-id="10c0c-125">Enter your preferred **Display Name**, **Name**, **Description**, **API Url suffix**, **Products**, and **Version**.</span></span>

    <span data-ttu-id="10c0c-126">Lorsque vous avez terminé, votre configuration WSDL se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="10c0c-126">When finished, your WSDL configuration looks something like the following:</span></span> 

    ![créer des API à partir de WSDL BizTalk](../core/media/create-api-from-wsdl-biztalk.png)

4. <span data-ttu-id="10c0c-128">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="10c0c-128">Select **Create**.</span></span>

## <a name="create-using-the-biztalk-administration"></a><span data-ttu-id="10c0c-129">Créer à l’aide de la console Administration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="10c0c-129">Create using the BizTalk Administration</span></span>

> [!NOTE] 
> <span data-ttu-id="10c0c-130">Cette fonctionnalité est prise en charge avec WCF-BasicHTTP les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="10c0c-130">This feature is supported with WCF-BasicHTTP receive locations.</span></span> 

1. <span data-ttu-id="10c0c-131">Dans la Console Administration de BizTalk, avec le bouton de l’emplacement de réception de votre WCF-BasicHTTP, puis sélectionnez **publier sur la gestion des API**:</span><span class="sxs-lookup"><span data-stu-id="10c0c-131">In the BizTalk Administration Console, right-click your WCF-BasicHTTP receive location, and select **Publish to API Management**:</span></span>  

    ![publier l’option de menu](../core/media/publish-to-api-management-option.png)
 
2. <span data-ttu-id="10c0c-133">Configurer les propriétés de gestion d’API :</span><span class="sxs-lookup"><span data-stu-id="10c0c-133">Configure your API management properties:</span></span> 

    1. <span data-ttu-id="10c0c-134">**Connectez-vous** à votre abonnement Azure, sélectionnez le **abonnement** et **groupe de ressources** dont votre gestion des API de service, puis sélectionnez votre service.</span><span class="sxs-lookup"><span data-stu-id="10c0c-134">**Sign-in** to your Azure subscription, select the **Subscription** and **Resource Group** that has your API management service, and then select your service.</span></span>

    2. <span data-ttu-id="10c0c-135">Le **lien de spécification WSDL** est automatiquement renseignée avec le fichier WSDL.</span><span class="sxs-lookup"><span data-stu-id="10c0c-135">The **WSDL specification link** is automatically populated with your WSDL file.</span></span> <span data-ttu-id="10c0c-136">Remplacez **localhost** avec le nom DNS ou l’adresse IP du serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="10c0c-136">Replace **localhost** with the DNS name or IP address of the BizTalk Server.</span></span> 

    3. <span data-ttu-id="10c0c-137">Sélectionnez **pass-through SOAP** ou **SOAP reste**:</span><span class="sxs-lookup"><span data-stu-id="10c0c-137">Select **SOAP pass-through** or **SOAP to REST**:</span></span>  
        * <span data-ttu-id="10c0c-138">**SOAP reste**: créer le reste APIs basées sur HTTP à partir de des services web basés sur SOAP existants</span><span class="sxs-lookup"><span data-stu-id="10c0c-138">**SOAP to REST**: Create REST-based HTTP APIs from an existing SOAP-based web services</span></span>
        * <span data-ttu-id="10c0c-139">**Pass-through SOAP**: agit comme un proxy pour l’API SOAP</span><span class="sxs-lookup"><span data-stu-id="10c0c-139">**SOAP pass-through**: Acts as a proxy for the SOAP API</span></span> 

        <span data-ttu-id="10c0c-140">L’API peut être publié les deux sens en modifiant le **suffixe d’URL de l’API**, puis les publier à nouveau à l’aide d’un autre type de l’API.</span><span class="sxs-lookup"><span data-stu-id="10c0c-140">The API can be published both ways by changing the **API URL suffix**, and then publishing again using a different API type.</span></span>

    4. <span data-ttu-id="10c0c-141">Le **nom de l’API** est automatiquement renseigné avec le nom d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="10c0c-141">The **API name** is automatically populated with the receive location name.</span></span>

    5. <span data-ttu-id="10c0c-142">Sélectionnez un **suffixe d’URL de l’API** qui doit être utilisé par les consommateurs de l’API.</span><span class="sxs-lookup"><span data-stu-id="10c0c-142">Select an **API URL suffix** that is to be used by consumers of the API.</span></span> 

    <span data-ttu-id="10c0c-143">Lorsque vous avez terminé, les propriétés ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="10c0c-143">When finished, your properties look similar to the following:</span></span>  
    ![publier dans la fenêtre de l’API](../core/media/api-management-publish-window.png)


3. <span data-ttu-id="10c0c-145">Sélectionnez **publier**.</span><span class="sxs-lookup"><span data-stu-id="10c0c-145">Select **Publish**.</span></span> <span data-ttu-id="10c0c-146">Cas de réussite, l’emplacement de réception est affiché en tant que service de gestion des API dans le [portail Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="10c0c-146">When successful, the receive location is displayed as a service in API Management in the [Azure portal](https://portal.azure.com).</span></span> 

## <a name="do-more"></a><span data-ttu-id="10c0c-147">Faire plus</span><span class="sxs-lookup"><span data-stu-id="10c0c-147">Do more</span></span>
<span data-ttu-id="10c0c-148">Gestion des API Azure est un service puissant qui est utilisé par un grand nombre de services Azure, y compris les applications de la logique.</span><span class="sxs-lookup"><span data-stu-id="10c0c-148">Azure API Management is a powerful service that is used by a lot of Azure services, including Logic Apps.</span></span> <span data-ttu-id="10c0c-149">Gestion des API inclut de nombreuses fonctionnalités, y compris les limites de taux et les quotas, ce qui a accès à votre API, la mise en cache et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="10c0c-149">API Management includes many features, including rate limits and quotas, who has access to your APIs, caching, and more.</span></span> <span data-ttu-id="10c0c-150">Consultez [quelle est la gestion des API ?](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts) pour commencer.</span><span class="sxs-lookup"><span data-stu-id="10c0c-150">See [What is API Management?](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts) to get started.</span></span>

## <a name="see-also"></a><span data-ttu-id="10c0c-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10c0c-151">See also</span></span>
[<span data-ttu-id="10c0c-152">Télécharger le Feature Pack</span><span class="sxs-lookup"><span data-stu-id="10c0c-152">Configure the feature pack</span></span>](configure-the-feature-pack.md)
