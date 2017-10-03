---
title: "Fonctionnalités de sécurité dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- Master Secret server, security
- security, Master Secret server
- security, runtime
- security, data
- deploying, security
- security, configuring
- runtime, security
- security, security features
- security, messages
- security, access control
- security, about security
- access control
- security, deploying
- data, security
- messages, security
ms.assetid: 5ab15023-fa71-439e-b3aa-420fe28806fa
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50371f0b0c5d5a56fc9f7c392e4ee8d69e637b47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-features-in-biztalk-server"></a>Fonctionnalités de sécurité sous BizTalk Server 2010
Microsoft® BizTalk® Server fournit une passerelle standard pour envoyer et recevoir des documents via un intranet et via Internet. La teneur de certains messages envoyés vers et à partir de BizTalk Server peut être stratégique pour l'entreprise. Aussi, il est important d'envisager des mesures permettant de sécuriser ces messages et les informations qu'ils contiennent lorsqu'ils sont en transit et lorsqu'ils sont traités et stockés par BizTalk Server. Cette section fournit des informations sur les fonctionnalités de sécurité de BizTalk Server, et comment vous pouvez les utiliser pour sécuriser vos données et votre environnement.  
  
 BizTalk Server fait appel aux mesures suivantes pour permettre de sécuriser les messages entrants et sortants, le composant d'exécution et les informations de configuration ainsi que pour permettre son intégration à d'autres applications et systèmes en toute sécurité :  
  
 **Sécurité des messages**  
  
-   Authentification de l'expéditeur d'un message. BizTalk Server peut authentifier l'expéditeur d'un message (en utilisant soit les informations de certificat soit la sécurité intégrée de Windows) afin de valider l'identité de celui-ci. Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).  
  
-   Approbation du récepteur d'un message. Après la réception d'un message par BizTalk Server, celui-ci peut déterminer les processus et les utilisateurs disposant des autorisations pour recevoir le message. Pour plus d’informations, consultez [autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md).  
  
 **Runtime et configuration de sécurité**  
  
-   **Contrôle d’accès et protection des données.** BizTalk Server fait appel au contrôle d'accès pour garantir que ses processus disposent de limites appropriées et que l'accès aux informations stratégiques est contrôlé. En d'autres termes, BizTalk Server vérifie que les utilisateurs et les comptes disposent des droits d'utilisateur minimaux nécessaires à l'exécution de leurs tâches. Pour plus d’informations, consultez [contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md).  
  
 **Sécurité intégrée**  
  
-   Authentification unique de l'entreprise. BizTalk Server utilise l'authentification unique de l'entreprise pour garantir qu'il chiffre les informations de configuration stratégiques nécessaires aux adaptateurs et aux emplacements d'envoi et de réception. Cela permet également de garantir que BizTalk Server stocke et transmet ces informations de manière sécurisée. Pour plus d’informations, consultez [à l’aide de l’authentification unique](../core/using-sso.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Conception des Architectures système pour BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)   
 [Planification de la sécurité de Message](../core/planning-message-security.md)   
 [Contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md)   
