---
title: "Encodage de caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transaction support
- character encoding
- encoding characters
- messages, character encoding
ms.assetid: 0a0c21c8-3318-4533-9734-89302527cb67
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19d3204cae7b82e9d18325b223e5c3b7a2d40808
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding"></a>Codage des caractères
TIBCO Enterprise Message Service (EMS) prend en charge plusieurs codages de caractères dans les messages qui lui sont transmis par les adaptateurs BizTalk pour TIBCO EMS. Les messages sont codés à l'aide du codage UTF-8 par défaut. Lorsqu'un adaptateur reçoit un message, il détermine le codage de celui-ci et convertit les chaînes appropriées au format UTF-8 avant de l'envoyer à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Toutes les opérations de conversion exploitant les classes Microsoft .NET Framework; l'adaptateur prend en charge la conversion des caractères fournie par ce même cadre.  
  
## <a name="running-in-a-clustered-environment"></a>Exécution dans un environnement en clusters  
 Les messages publiés dans les files d'attente sont utilisés par les consommateurs dans un ordre prédéterminé par le serveur EMS (un seul adaptateur reçoit le message dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en clusters). La file d’attente peut être configuré en tant que *exclusif*. Cela signifie que seul le premier adaptateur qui s'enregistre pour l'utilisation des messages dans la file d'attente reçoit les messages. Le serveur EMS envoie des messages aux autres consommateurs seulement si le consommateur exclusif n'accuse pas réception des messages. La configuration exclusive de la file d'attente est effectuée dans la configuration EMS et n'est pas réalisable par le client.  
  
> [!NOTE]
>  Concernant les abonnements aux rubriques : étant donné que toutes les cartes dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe sont configurés de façon identique, ils sont tous les abonnés aux messages, et chaque abonnement à une rubrique reçoit le message.  
  
## <a name="transaction-support"></a>Prise en charge des transactions  
 L'adaptateur permet de prendre en charge les transactions lorsque cela est demandé par les ports d'envoi de l'orchestration. Il n'existe aucune prise en charge des transactions avec le serveur EMS lorsque l'adaptateur écoute les messages. Toutefois, celui-ci accuse réception de tous les messages provenant d'EMS après la réussite de leur envoi à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. EMS renvoie à l'adaptateur les messages non acquittés.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’adaptateur BizTalk pour TIBCO EMS](../core/security-in-biztalk-adapter-for-tibco-ems.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)