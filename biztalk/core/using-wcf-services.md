---
title: Utilisation des Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services
- Windows Communication Foundation (WCF)
ms.assetid: 34fe5e4c-6a92-4627-b2aa-e8b58a708320
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29b984bcda798796565113739c6088af6d569f7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-wcf-services"></a>utilisation des services WCF
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assure la prise en charge intégrée de Windows Communication Foundation (WCF). [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de réutiliser et d'agréger vos services WCF existants dans vos orchestrations. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]implémente également la prise en charge pour les adaptateurs natifs dans les services WCF. Une telle prise en charge offre une évolutivité, une tolérance aux pannes et des capacités de suivi pour vos services WCF sans que vous ayez besoin d'écrire un code. Pour plus d’informations sur les adaptateurs WCF, consultez [adaptateurs WCF](../core/wcf-adapters.md).  
  
 Prise en charge dans les services WCF [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se répartissent en deux catégories : publication ou création de services WCF, ou l’appel ou utilisation des services WCF.  
  
 **Publication des services WCF**  
  
 Grâce aux adaptateurs WCF, vous pouvez publier (exposer) les orchestrations et schémas en tant que services WCF afin de séparer la logique de service WCF de celle du processus d'entreprise. Pour les adaptateurs WCF isolés, l'Assistant Publication de services WCF BizTalk vous permet de créer des emplacements de réception WCF isolés qui sont hébergés sur des applications Web exécutées dans les services Internet (IIS). Pour les adaptateurs WCF In-process, l'Assistant Publication de services WCF BizTalk vous permet de publier des métadonnées de service pour tout emplacement WCF.  La publication de métadonnées permet de créer un code client à l'aide de l'utilitaire svcutil.exe.  
  
 **Utilisation des services WCF**  
  
 Utilisez l'Assistant Consommation de service WCF BizTalk pour générer les artefacts BizTalk, par exemple des orchestrations et des types BizTalk, afin d'utiliser un service WCF basé sur le document de métadonnées du service WCF. Les métadonnées permettent à un port d'envoi d'accéder à un service externe en tant que client. Elles permettent avant tout de décrire l'adresse du point de terminaison, la liaison et le contrat.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Publication des Services WCF](../core/publishing-wcf-services.md)  
  
-   [Utilisation des Services WCF](../core/consuming-wcf-services.md)  
  
-   [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [Procédures pas à pas l’adaptateur WCF](../core/wcf-adapter-walkthroughs.md)