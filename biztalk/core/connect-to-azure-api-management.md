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
# <a name="connect-to-azure-api-management"></a>Se connecter à la gestion des API Azure
Vous pouvez exposer désormais facilement votre point de terminaison SOAP via la gestion des API à partir de BizTalk.

## <a name="what-is-azure-api-management"></a>Qu’est la gestion des API Azure
Utilisez la gestion des API Azure comme une solution clé en main pour la publication d’API pour les clients externes et internes. Créer rapidement cohérent modernes passerelles API pour les services principaux existants hébergés n’importe où, sécuriser et les protéger contre les abus et utilisation abusive, et obtenir des informations sur l’utilisation et d’intégrité. De plus, automatiser et mettre à l’échelle de l’intégration de développeur pour aider votre programme API haut et en cours d’exécution. 

Consultez [gestion des API](https://azure.microsoft.com/en-us/services/api-management/) pour en savoir plus sur la gestion des API.

## <a name="prerequisites"></a>Conditions préalables
* Configurer [gestion des API Azure](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)
* Créer un [réseau virtuel](https://docs.microsoft.com/en-us/azure/api-management/api-management-using-with-vnet) entre votre ordinateur BizTalk et de l’instance de l’API abordés


1. Dans le portail Azure, ouvrez la gestion de l’API, puis sélectionnez **API** à partir du menu :

    ![Sélectionnez les API pour BizTalk](../core/media/select-api-for-biztalk.png)
    
2. Sélectionnez l’option de **WSDL** dans la section de la nouvelle API :

    ![Sélectionnez wsdl biztalk api](../core/media/select-wsdl-biztalk-api.png)
    
3. Pour vous connecter à la gestion des API votre WSDL BizTalk, copiez l’URL à votre ordinateur BizTalk avec l’URI complet pour votre point de terminaison SOAP. Par exemple, copiez `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`:

    ![créer des API à partir de WSDL BizTalk](../core/media/create-api-from-wsdl-biztalk.png)

4. Sélectionnez si vous souhaitez utiliser un **pass-through SOAP**, ou installer un **SOAP reste** service.
5. Entrez le **nom** de votre API, le **Description**et le **suffixe d’Url de l’API** pour votre service.
6. Sélectionnez **créer** pour créer votre point de terminaison SOAP principal de la communication.

## <a name="see-also"></a>Voir aussi
[Télécharger le Feature Pack](configure-the-feature-pack.md)