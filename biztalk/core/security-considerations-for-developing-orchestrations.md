---
title: "Considérations de sécurité pour le développement d’Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, orchestrations
- messages, subscriptions
- orchestrations, security
- messages, security
ms.assetid: a29b2018-4a8f-49ad-a817-6f279db3f801
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e020759a8d389461978a4de4138bcc139d527539
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-developing-orchestrations"></a>Considérations de sécurité pour le développement d’Orchestrations
Lorsque vous concevez vos orchestrations, vous devez envisager l'éventualité de problèmes de sécurité.  
  
## <a name="avoid-subscriptions-based-on-content-from-untrusted-messages"></a>Évitez les abonnements basés sur des contenus de messages non approuvés  
 Pour vous assurer qu'un message doté de peu de privilèges n'initie pas une instance d'orchestration qui pourrait créer des abonnements basés sur le contenu du message ou le contexte, nous vous recommandons fortement d'empêcher vos orchestrations de créer leurs abonnements de message sur la base du contenu ou du contexte d'un message non approuvé.  
  
 Pour plus d’informations sur la sécurité dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [sécurisation de BizTalk Server](../core/securing-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Orchestrations](../core/creating-orchestrations.md)   
 [À propos des Orchestrations](../core/about-orchestrations.md)