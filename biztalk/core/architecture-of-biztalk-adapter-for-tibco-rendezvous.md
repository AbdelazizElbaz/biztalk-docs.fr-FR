---
title: "Architecture de l’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "En savoir plus sur l’adaptateur BizTalk pour TIBCO Rendezvous fonctionne, y compris la transmission de messages, dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 174d6ceb-8e1d-4c93-827d-8155cfe47836
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3bfee2b51df8781091ea30e512810bae21a5f2a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-the-tibco-rendezvous-adapter"></a>Architecture de l’adaptateur TIBCO Rendezvous

## <a name="overview"></a>Vue d'ensemble
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous assure la connectivité bidirectionnelle entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et TIBCO Rendezvous. Il utilise l'API TIBCO Rendezvous et l'API d'infrastructure d'adaptateurs BizTalk pour offrir une intégration étroite.  
  
 TIBCO Rendezvous est un logiciel qui inclut un bus de messages pour l'intégration des applications d'entreprise (IAE). Il inclut des API de messagerie en C, C++, Java, Visual Basic et pour Microsoft .NET Framework pour la réception de flux de données dans des feuilles de calcul Microsoft Office Excel et d'autres applications spécifiques.  
  
## <a name="message-passing"></a>Transmission de messages  
 Le concept de base de la transmission de messages est relativement simple :  
  
-   Un message inclut un sujet unique constitué d'éléments séparés par des points. Il est envoyé à un démon Rendezvous (même s'il peut être transmis à d'autres démons).  
  
-   Un port d'écoute annonce ses sujets d'intérêt à un démon (à l'aide d'une fonction de caractère générique de base) et les messages ayant des sujets correspondants lui sont remis si les deux démons sont connectés ou correspondent au même démon. Pour plus d’informations, consultez les Messages dans [Messages dans l’adaptateur BizTalk pour TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).  
  
 La figure suivante présente l'architecture de l'adaptateur BizTalk pour TIBCO Rendezvous.  
  
 ![](../core/media/tibcorend-arch.gif "TibcoRend_Arch")  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)  