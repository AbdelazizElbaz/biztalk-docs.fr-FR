---
title: "Architecture de l’adaptateur BizTalk pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- architecture
- message passing
- messages, passing
ms.assetid: 174d6ceb-8e1d-4c93-827d-8155cfe47836
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 801f92453ffc85d83d57c1caa5c89ec618b96ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-tibco-rendezvous"></a>Architecture de l'adaptateur BizTalk pour TIBCO Rendezvous
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous assure la connectivité bidirectionnelle entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et TIBCO Rendezvous. Il utilise l'API TIBCO Rendezvous et l'API d'infrastructure d'adaptateurs BizTalk pour offrir une intégration étroite.  
  
 TIBCO Rendezvous est un logiciel qui inclut un bus de messages pour l'intégration des applications d'entreprise (IAE). Il inclut des API de messagerie en C, C++, Java, Visual Basic et pour Microsoft .NET Framework pour la réception de flux de données dans des feuilles de calcul Microsoft Office Excel et d'autres applications spécifiques.  
  
## <a name="message-passing"></a>Transmission de messages  
 Le concept de base de la transmission de messages est relativement simple :  
  
-   Un message inclut un sujet unique constitué d'éléments séparés par des points. Il est envoyé à un démon Rendezvous (même s'il peut être transmis à d'autres démons).  
  
-   Un port d'écoute annonce ses sujets d'intérêt à un démon (à l'aide d'une fonction de caractère générique de base) et les messages ayant des sujets correspondants lui sont remis si les deux démons sont connectés ou correspondent au même démon. Pour plus d’informations, consultez les Messages dans [Messages dans l’adaptateur BizTalk pour TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).  
  
 La figure suivante présente l'architecture de l'adaptateur BizTalk pour TIBCO Rendezvous.  
  
 ![](../core/media/tibcorend-arch.gif "TibcoRend_Arch")  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)   
 [Planification et Architecture](../core/planning-and-architecture15.md)