---
title: Utilisation des Services Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services
- Web services, about Web services
- orchestrations, Web services
- Web services, orchestrations
ms.assetid: a54261e3-d8ef-4770-8d9a-147685846051
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 236acb42c010effe5c3d45cde1daaf9a7097ede5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-web-services"></a>Utilisation des Services Web
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assure la prise en charge intégrée des services Web. BizTalk Server permet la réutilisation et l'agrégation de l'ensemble de vos services web existants dans vos orchestrations. Vous pouvez également publier (exposer) vos orchestrations en tant que services Web afin de séparer la logique du service Web de celle du processus d'entreprise.  
  
 BizTalk Server assure la prise en charge des adaptateurs natifs dans les services Web. Une telle prise en charge offre une évolutivité, une tolérance aux pannes et des capacités de suivi pour vos services sans que vous ayez besoin d'écrire du code. Pour plus d’informations sur l’adaptateur SOAP, consultez [adaptateur SOAP](../core/soap-adapter.md).  
  
 La prise en charge des services Web dans BizTalk Server se répartissent en deux catégories : consommation ou l’appel de services Web et la publication ou la création de services Web.  
  
 Avant d’utiliser ou publier un service Web, vous devez avoir une compréhension des services Web XML dans ASP.NET. Pour plus d’informations sur les principes de base des services Web XML, consultez l’article « XML Web Services Basics » à [http://go.microsoft.com/fwlink/?LinkId=193057](http://go.microsoft.com/fwlink/?LinkId=193057).  
  
 **Utilisation de services Web**  
  
 Vous pouvez utiliser (appeler) les services Web à partir d'une orchestration. Vous pouvez regrouper plusieurs services Web dans une seule orchestration pour achever un processus d'entreprise dans sa totalité.  
  
 **Publication de services Web**  
  
 Vous pouvez publier des services Web à l'aide de l'Assistant Publication de services Web BizTalk. Les orchestrations et les adaptateurs d'envoi peuvent utiliser ces services Web publiés.  
  
 **Utilisation des en-têtes SOAP**  
  
 BizTalk Server prend en charge les en-têtes SOAP définis et inconnus. BizTalk Server crée une propriété de contexte pour chaque en-tête SOAP défini dans le service Web.  
  
 **Normes de Services Web**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit fonctionner avec toutes les normes de services web lors de l'envoi et de la réception. Les normes n'ont pas toutes été testées. En règle générale, les normes prises en charge par WCF le sont également par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Voici quelques exemples de normes :  
  
-   WS-ReliableMessaging  
  
-   WS-Security  
  
-   WS-SecureConversation  
  
-   WS-Trust  
  
-   WS-Federation  
  
-   WS-Addressing  
  
-   WS-Policy  
  
-   WS-MetadataExchange  
  
-   WS-Coordination  
  
-   WS-Atomic  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation de Services Web](../core/consuming-web-services.md)  
  
-   [Publication de Services Web](../core/publishing-web-services.md)  
  
-   [Utilisation des en-têtes SOAP](../core/using-soap-headers.md)