---
title: Publier des Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70b7851b-77c1-4ab3-a61f-e7165ceb56fb
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00136b64d5feaf552f77b92b3ad4442da4e447cc
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="publish-wcf-services"></a>Publier des Services WCF
Une orchestration peut être publiée comme service WCF dans BizTalk Server d’être appelée par les clients WCF.  
  
## <a name="publish-wcf-services-with-the-isolated-wcf-adapters"></a>Publier les services WCF avec les adaptateurs WCF isolés 
  
 L'Assistant Publication de services WCF BizTalk permet de créer et de publier des services WCF pour les adaptateurs WCF isolés tels que les adaptateurs WCF-BasicHttp, WCF-WSHttp et WCF-CustomIsolated. L'emplacement de réception créé dans ce cadre existe comme une application hors processus dans IIS.  
  
 Avant de publier un service WCF avec les adaptateurs WCF isolés, vous devez être familiarisé avec l'hébergement des services WCF dans IIS (Internet Information Services).  
  
## <a name="publish-service-metadata-for-the-wcf-receive-locations"></a>Publier les métadonnées de service pour les emplacements de réception WCF
  
 L'Assistant Publication de services WCF BizTalk permet de créer des métadonnées de service pour les emplacements de réception WCF publiés. Pour générer un code de client de modèle de service à partir de documents de métadonnées publiés, vous pouvez utiliser l’outil Service Model Metadata Utility (SvcUtil.exe) inclus dans le Kit de développement logiciel (SDK) Windows et les composants d’exécution .NET Framework.  
  
> [!IMPORTANT]
>  Avant d'exécuter l'Assistant Publication de services WCF BizTalk, vous devez activer les services WCF. Pour plus d’informations sur l’activation des services WCF pour votre système, consultez [de configurer IIS pour les adaptateurs de réception WCF isolés](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Publication des services WCF avec les adaptateurs de réception WCF isolés](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [Publication des métadonnées de service pour les adaptateurs de réception WCF](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [Considérations à prendre en compte lors de la publication de services WCF avec les adaptateurs de réception WCF](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [En-têtes SOAP avec les services WCF publiés](../core/soap-headers-with-published-wcf-services.md)  
  
-   [Lever des exceptions d’erreur à partir d’orchestrations publiées sous forme de services WCF](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)