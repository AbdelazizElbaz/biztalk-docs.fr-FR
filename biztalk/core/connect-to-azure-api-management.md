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
# <a name="publish-biztalk-soap-endpoints-in-api-management"></a>Publier des points de terminaison SOAP BizTalk dans la gestion des API

Exposer vos points de terminaison SOAP BizTalk en tant que services au sein de la gestion des API Azure. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 1**, vous pouvez exposer un point de terminaison SOAP via la gestion des API à partir de BizTalk. Pour cela, à l’aide de la gestion des API dans le portail Azure. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, vous pouvez exposer un WCF-BasicHTTP emplacement au sein de la gestion des API Azure à l’aide de la console Administration de BizTalk, un point de terminaison de réception. 

> [!TIP]
> [Quelle est la gestion des API ? ](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts) est un bon point de départ pour comprendre et en savoir plus sur ce service Azure.

## <a name="prerequisites"></a>Conditions préalables
* Configurer [gestion des API Azure](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)
* Créer un [réseau virtuel](https://docs.microsoft.com/azure/api-management/api-management-using-with-vnet) entre votre ordinateur BizTalk et de l’instance de la gestion des API
* Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur le serveur BizTalk

## <a name="create-using-api-management-in-azure-portal"></a>Créer à l’aide de la gestion des API dans le portail Azure 
1. Dans le [portail Azure](https://portal.azure.com), ouvrez la gestion de l’API, puis sélectionnez **API**:

    ![Sélectionnez les API pour BizTalk](../core/media/select-api-for-biztalk.png)
    
2. Sélectionnez **WSDL**:

    ![Sélectionnez wsdl biztalk api](../core/media/select-wsdl-biztalk-api.png)
    
3. Configurer les propriétés WSDL : 

    1. **Spécification WSDL** : entrez l’URI complet pour votre point de terminaison SOAP BizTalk. Par exemple, entrez un nom tel que `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl` ou `http://biztalkfp1.westus.cloudapp.azure.com/RestEndPoint/OrderIncome.svc?wsdl`.  

    2. **Pass-through SOAP** ou **SOAP reste** : sélectionnez votre préférence : 
        * **SOAP reste**: créer le reste APIs basées sur HTTP à partir d’un service web basé sur SOAP existant
        * **Pass-through SOAP**: agit comme un proxy pour l’API SOAP 

    3. Entrez votre choix **nom d’affichage**, **nom**, **Description**, **suffixe d’Url de l’API**, **produits**, et **Version**.

    Lorsque vous avez terminé, votre configuration WSDL se présente comme suit : 

    ![créer des API à partir de WSDL BizTalk](../core/media/create-api-from-wsdl-biztalk.png)

4. Sélectionnez **Créer**.

## <a name="create-using-the-biztalk-administration"></a>Créer à l’aide de la console Administration de BizTalk

> [!NOTE] 
> Cette fonctionnalité est prise en charge avec WCF-BasicHTTP les emplacements de réception. 

1. Dans la Console Administration de BizTalk, avec le bouton de l’emplacement de réception de votre WCF-BasicHTTP, puis sélectionnez **publier sur la gestion des API**:  

    ![publier l’option de menu](../core/media/publish-to-api-management-option.png)
 
2. Configurer les propriétés de gestion d’API : 

    1. **Connectez-vous** à votre abonnement Azure, sélectionnez le **abonnement** et **groupe de ressources** dont votre gestion des API de service, puis sélectionnez votre service.

    2. Le **lien de spécification WSDL** est automatiquement renseignée avec le fichier WSDL. Remplacez **localhost** avec le nom DNS ou l’adresse IP du serveur BizTalk. 

    3. Sélectionnez **pass-through SOAP** ou **SOAP reste**:  
        * **SOAP reste**: créer le reste APIs basées sur HTTP à partir de des services web basés sur SOAP existants
        * **Pass-through SOAP**: agit comme un proxy pour l’API SOAP 

        L’API peut être publié les deux sens en modifiant le **suffixe d’URL de l’API**, puis les publier à nouveau à l’aide d’un autre type de l’API.

    4. Le **nom de l’API** est automatiquement renseigné avec le nom d’emplacement de réception.

    5. Sélectionnez un **suffixe d’URL de l’API** qui doit être utilisé par les consommateurs de l’API. 

    Lorsque vous avez terminé, les propriétés ressembler à ce qui suit :  
    ![publier dans la fenêtre de l’API](../core/media/api-management-publish-window.png)


3. Sélectionnez **publier**. Cas de réussite, l’emplacement de réception est affiché en tant que service de gestion des API dans le [portail Azure](https://portal.azure.com). 

## <a name="do-more"></a>Faire plus
Gestion des API Azure est un service puissant qui est utilisé par un grand nombre de services Azure, y compris les applications de la logique. Gestion des API inclut de nombreuses fonctionnalités, y compris les limites de taux et les quotas, ce qui a accès à votre API, la mise en cache et bien plus encore. Consultez [quelle est la gestion des API ?](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts) pour commencer.

## <a name="see-also"></a>Voir aussi
[Télécharger le Feature Pack](configure-the-feature-pack.md)
