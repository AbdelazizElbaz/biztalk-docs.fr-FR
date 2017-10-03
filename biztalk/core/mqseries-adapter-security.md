---
title: "Sécurité de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, MQSeries adapters
- MQSeries adapters, security
ms.assetid: 0bd82c21-6b77-4a66-a4e9-4a91ba4a56c4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08d5228dab8463c2ad5dc7f9d9347899d4c41a67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-with-the-mqseries-adapter"></a>Sécurité avec l’adaptateur MQSeries

La fonctionnalité de sécurité de l'adaptateur MQSeries commence par sécuriser vos serveurs BizTalk et MQSeries. Pour plus d’informations sur la sécurisation de BizTalk Server, consultez [sécurisé et protégez vos données](secure-and-protect-your-biztalk-messages.md). Pour plus d'informations sur la sécurité du serveur MQSeries, consultez la documentation IBM associée.  
  
> [!NOTE]
>  L'adaptateur utilise automatiquement la confidentialité du paquet pour l'envoi et la réception des messages entre le serveur BizTalk et le serveur MQSeries.  

## <a name="adapter-security"></a>Sécurité de l’adaptateur  
 L'utilisation sécurisée de l'adaptateur requiert votre attention sur quatre points importants :  
  
-   la sélection de l'identité et des membres de l'application pour MQSAgent ;  
  
-   le contrôle des comptes BizTalk Server à l'aide de l'adaptateur ;  
  
-   la sécurisation des scripts de création de la file d'attente ;  
  
-   Utilisation appropriée de la **Application associée SSO** propriété  
  
 Le compte affecté à l'identité de l'application lors de la configuration ne doit pas être un compte d'administrateur. Il ne doit bénéficier que des privilèges requis minimaux, à savoir l'accès en lecture/écriture aux files d'attente MQSeries.  
  
 Vérifiez que vous affectez uniquement des comptes BizTalk Server à l'aide de l'adaptateur au rôle MQSAgent.  
  
 Lors de l'utilisation de scripts exportés créés lors du processus de définition de la file d'attente, conservez ceux-ci dans une zone sécurisée. Seuls les administrateurs utilisant les scripts doivent y avoir accès.  
  
 Si votre application utilise les propriétés d’en-tête MQCIH et MQIIH pour placer les informations d’identification de l’utilisateur dans les messages sortants, utilisez le **Application associée SSO** propriété sur le **propriétés du Transport** page. Pour plus d’informations sur cette propriété, consultez [comment configurer les emplacements de réception de la carte de MQSeries et les Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Structure de l’adaptateur MQSeries](../core/structure-of-the-mqseries-adapter.md)   
 [Nouveautés de l’adaptateur MQSeries ?](../core/what-is-the-mqseries-adapter.md)