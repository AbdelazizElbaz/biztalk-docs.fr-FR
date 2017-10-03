---
title: Publication de Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, WCF services
- WCF services, publishing
ms.assetid: 70b7851b-77c1-4ab3-a61f-e7165ceb56fb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5f72f2b300738f2e9a1a643e152048b64cf8f55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-wcf-services"></a>Publication des Services WCF
Une orchestration peut être publiée comme service WCF dans [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à être appelé par les clients WCF.  
  
 **Publication de services WCF avec les adaptateurs WCF isolés**  
  
 L'Assistant Publication de services WCF BizTalk permet de créer et de publier des services WCF pour les adaptateurs WCF isolés tels que les adaptateurs WCF-BasicHttp, WCF-WSHttp et WCF-CustomIsolated. L'emplacement de réception créé dans ce cadre existe comme une application hors processus dans IIS.  
  
 Avant de publier un service WCF avec les adaptateurs WCF isolés, vous devez être familiarisé avec l'hébergement des services WCF dans IIS (Internet Information Services).  
  
 **Publication des métadonnées de service pour les emplacements de réception WCF**  
  
 L'Assistant Publication de services WCF BizTalk permet de créer des métadonnées de service pour les emplacements de réception WCF publiés. Pour générer le code de client de modèle de service à partir de documents de métadonnées publiés, vous pouvez utiliser l’outil Service Model Metadata Utility (SvcUtil.exe) inclus dans le [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Kit de développement logiciel (SDK) pour [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] et [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Composants d’exécution.  
  
> [!IMPORTANT]
>  Avant d'exécuter l'Assistant Publication de services WCF BizTalk, vous devez activer les services WCF. Pour plus d’informations sur l’activation des services WCF pour votre système, consultez [de configurer IIS pour les adaptateurs de réception WCF isolés](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Publication des Services WCF avec WCF isolé des adaptateurs de réception](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [Publication des métadonnées de Service WCF pour les adaptateurs de réception](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [Considérations relatives à la publication de Services WCF avec WCF des adaptateurs de réception](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [En-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md)  
  
-   [Levée des Exceptions d’erreur à partir d’Orchestrations publiées en tant que Services WCF](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)