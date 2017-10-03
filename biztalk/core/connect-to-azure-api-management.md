---
title: "Se connecter à la gestion des API Azure à l’aide de BizTalk Server | Documents Microsoft"
description: "Utilisez BizTalk Feature Pack 1 pour vous connecter à la gestion des API à partir de votre serveur BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a87bfb40-7e6f-46aa-8ac7-db6d13ce7eb2
caps.latest.revision: "2"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: d0c5e4cd2a0ebbd7108845ea15de468d0e0a5a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-azure-api-management"></a><span data-ttu-id="8cac0-103">Se connecter à la gestion des API Azure</span><span class="sxs-lookup"><span data-stu-id="8cac0-103">Connect to Azure API Management</span></span>
<span data-ttu-id="8cac0-104">Vous pouvez exposer désormais facilement votre point de terminaison SOAP via la gestion des API à partir de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8cac0-104">You can now easily expose your SOAP endpoint through API Management from BizTalk.</span></span>

## <a name="what-is-azure-api-management"></a><span data-ttu-id="8cac0-105">Qu’est la gestion des API Azure</span><span class="sxs-lookup"><span data-stu-id="8cac0-105">What is Azure API Management</span></span>
<span data-ttu-id="8cac0-106">Utilisez la gestion des API Azure comme une solution clé en main pour la publication d’API pour les clients externes et internes.</span><span class="sxs-lookup"><span data-stu-id="8cac0-106">Use Azure API Management as a turnkey solution for publishing APIs to external and internal customers.</span></span> <span data-ttu-id="8cac0-107">Créer rapidement cohérent modernes passerelles API pour les services principaux existants hébergés n’importe où, sécuriser et les protéger contre les abus et utilisation abusive, et obtenir des informations sur l’utilisation et d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="8cac0-107">Quickly create consistent and modern API gateways for existing back-end services hosted anywhere, secure and protect them from abuse and overuse, and get insights into usage and health.</span></span> <span data-ttu-id="8cac0-108">De plus, automatiser et mettre à l’échelle de l’intégration de développeur pour aider votre programme API haut et en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8cac0-108">Plus, automate and scale developer onboarding to help get your API program up and running.</span></span> 

<span data-ttu-id="8cac0-109">Consultez [gestion des API](https://azure.microsoft.com/en-us/services/api-management/) pour en savoir plus sur la gestion des API.</span><span class="sxs-lookup"><span data-stu-id="8cac0-109">See [API Management](https://azure.microsoft.com/en-us/services/api-management/) to learn more about API Management.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8cac0-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8cac0-110">Prerequisites</span></span>
* <span data-ttu-id="8cac0-111">Configurer [gestion des API Azure](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)</span><span class="sxs-lookup"><span data-stu-id="8cac0-111">Configure and set up [Azure API Management](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)</span></span>
* <span data-ttu-id="8cac0-112">Créer un [réseau virtuel](https://docs.microsoft.com/en-us/azure/api-management/api-management-using-with-vnet) entre votre ordinateur BizTalk et de l’instance de l’API abordés</span><span class="sxs-lookup"><span data-stu-id="8cac0-112">Create a [virtual network](https://docs.microsoft.com/en-us/azure/api-management/api-management-using-with-vnet) between your BizTalk Machine and the API Managemenet instance</span></span>


1. <span data-ttu-id="8cac0-113">Dans le portail Azure, ouvrez la gestion de l’API, puis sélectionnez **API** à partir du menu :</span><span class="sxs-lookup"><span data-stu-id="8cac0-113">In the Azure portal, open up your API management, and select **APIs** from the menu:</span></span>

    ![Sélectionnez les API pour BizTalk](../core/media/select-api-for-biztalk.png)
    
2. <span data-ttu-id="8cac0-115">Sélectionnez l’option de **WSDL** dans la section de la nouvelle API :</span><span class="sxs-lookup"><span data-stu-id="8cac0-115">Select the option for **WSDL** in the New API section:</span></span>

    ![Sélectionnez wsdl biztalk api](../core/media/select-wsdl-biztalk-api.png)
    
3. <span data-ttu-id="8cac0-117">Pour vous connecter à la gestion des API votre WSDL BizTalk, copiez l’URL à votre ordinateur BizTalk avec l’URI complet pour votre point de terminaison SOAP.</span><span class="sxs-lookup"><span data-stu-id="8cac0-117">To connect to API Management to your BizTalk WSDL, copy the URL to your BizTalk computer with the full URI to your SOAP endpoint.</span></span> <span data-ttu-id="8cac0-118">Par exemple, copiez `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`:</span><span class="sxs-lookup"><span data-stu-id="8cac0-118">For example, copy `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`:</span></span>

    ![créer des API à partir de WSDL BizTalk](../core/media/create-api-from-wsdl-biztalk.png)

4. <span data-ttu-id="8cac0-120">Sélectionnez si vous souhaitez utiliser un **pass-through SOAP**, ou installer un **SOAP reste** service.</span><span class="sxs-lookup"><span data-stu-id="8cac0-120">Select if you want to use a **SOAP pass-through**, or set up a **SOAP to REST** service.</span></span>
5. <span data-ttu-id="8cac0-121">Entrez le **nom** de votre API, le **Description**et le **suffixe d’Url de l’API** pour votre service.</span><span class="sxs-lookup"><span data-stu-id="8cac0-121">Enter the **name** of your API, the **Description**, and the **API Url suffix** for your service.</span></span>
6. <span data-ttu-id="8cac0-122">Sélectionnez **créer** pour créer votre point de terminaison SOAP principal de la communication.</span><span class="sxs-lookup"><span data-stu-id="8cac0-122">Select **Create** to create the communication to your backend SOAP endpoint.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cac0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cac0-123">See also</span></span>
[<span data-ttu-id="8cac0-124">Télécharger le Feature Pack</span><span class="sxs-lookup"><span data-stu-id="8cac0-124">Configure the feature pack</span></span>](configure-the-feature-pack.md)