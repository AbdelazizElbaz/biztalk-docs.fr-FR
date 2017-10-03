---
title: "Présentation de l'adaptateur MQSeries | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, about MQSeries adapters
- MQSeries adapters
ms.assetid: fd3dfa9a-344a-46e5-a342-bc56da7c1c50
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f72d0012050fc8022b53120377aeb648641d21f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-mqseries-adapter"></a>Présentation de l'adaptateur MQSeries
L'adaptateur MQSeries permet d'envoyer et de recevoir des messages avec les systèmes MQSeries à l'aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Cet adaptateur s'appuie sur MQSeries Server pour Windows. Cette conception garantit la fiabilité de la messagerie du fait que MQSeries Server pour Windows prend en charge le composant MSDTC (Microsoft Distributed Transaction Coordinator).  
  
 L'adaptateur prend en charge les serveurs MQSeries et les gestionnaires de file d'attente MQSeries mis en clusters, ainsi que les serveurs BizTalk mis en cluster.  
  
 Vous pouvez utiliser l'adaptateur MQSeries pour effectuer les opérations suivantes :  
  
-   Envoyer des messages aux files d'attente de définitions distantes MQSeries, aux files d'attente locales, aux files d'attente de transmission et aux files d'attente d'alias depuis BizTalk Server.  
  
-   Recevoir des messages à partir de files d'attente de transmission MQSeries, de files d'attente locales et de files d'attente d'alias.  
  
-   Envoyer et recevoir des messages depuisMQSeries Server pour Windows (MQSeries Server peut être exécuté sur le même ordinateur que BizTalk Server ou sur une installation distante). Vous ne devez déployer qu'une copie de MQSAgent (le composant COM+ de l'adaptateur) pour prendre en charge l'ensemble de vos installations BizTalk Server.  
  
-   Interroger MQSeries Server avec un intervalle d'attente.  
  
-   Utiliser des ports d'envoi dynamiques pour contrôler l'adaptateur.  
  
-   Créer des files d'attente de manière dynamique lors de l'exécution.  
  
-   Recevoir des messages de manière dynamique à partir de files d'attente basées sur MQSeries MatchOptions.  
  
-   Mettre en correspondance les propriétés de contexte aux propriétés d'en-tête, à la fois pour la transmission et la réception de messages. Vous pouvez obtenir et définir les propriétés d'en-tête MQSeries (y compris MQMD, MQXQH, MQCIH et MQIIH) par le biais des propriétés de contexte BizTalk Server.  
  
-   Permettre la corrélation avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou MQSeries Server qui crée l'identificateur de corrélation.  
  
-   Demander la remise transactionnelle et non transactionnelle de messages pour l'envoi et la réception.  
  
> [!NOTE]
>  Lors de l'utilisation de fonctionnalités telles que MQSeries qui effectuent des appels DCOM (Distributed Component Object Model) au serveur, vérifiez que vous n'avez pas de pare-feu de traduction d'adresses réseau (NAT, Network Address Translation) activé. Le client doit pouvoir accéder au serveur par son adresse IP réelle, or les pare-feu NAT convertissent cette adresse en un élément non reconnu par le client.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Composants de l’adaptateur MQSeries](../core/components-of-the-mqseries-adapter.md)  
  
-   [Architecture de l’adaptateur MQSeries](../core/mqseries-adapter-architecture.md)  
  
-   [À l’aide de l’adaptateur MQSeries](../core/using-the-mqseries-adapter.md)  
  
-   [Sécurité de l’adaptateur MQSeries](../core/mqseries-adapter-security.md)