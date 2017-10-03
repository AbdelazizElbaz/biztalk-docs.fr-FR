---
title: "Avant d’installer le Service de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service solution tutorial, deployment prerequisites
ms.assetid: 865bd21c-e49a-4647-af91-fefee07ee806
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7e611996e58291cdf6ed5d6b38b2b2fe5c299d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="before-installing-the-service-oriented-solution"></a>Avant l'installation de la solution orientée services
Les composants suivants doivent être disponibles pour installer la version stub de la solution orientée services sur un seul ordinateur :  
  
-   [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
-   Logiciels pris en charge pour [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
-   Dernière version du client IBM WebSphere MQ pour Windows  
  
    > [!NOTE]
    >  MQSeries Server n'est pas requis pour la version stub de la solution.  
  
    > [!NOTE]
    >  Vous pouvez télécharger le client IBM WebSphere MQ pour Windows depuis le site Web d'IBM.  
  
 Pour installer la version Inline et la version d'adaptateur de la solution orientée services sur un seul ordinateur :  
  
-   [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
    > [!NOTE]
    >  Un compte de domaine est requis pour mapper les informations d'identification pour l'authentification unique de l'entreprise. Il est recommandé d'utiliser des comptes de domaine pour le service BizTalk et les comptes du service d'authentification unique de l'entreprise.  
  
-   Logiciels pris en charge pour [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
-   MQSeries Server sur l'ordinateur local ou l'accès à l'ordinateur exécutant MQSeries Server. Pour la version Inline, les API du client MQSeries doivent être accessibles sur le serveur BizTalk Server exécutant les orchestrations de la solution.  
  
    > [!NOTE]
    >  La version de MQSeries Server doit correspondre à celle requise par l'adaptateur [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] MQSeries. Ceci peut inclure IBM WebSphere MQ pour Windows Version 5.3 with Fix Pack 10 (CSD10) ou une version ultérieure.  
  
    > [!NOTE]
    >  Lors de l'utilisation de fonctionnalités telles que MQSeries qui effectuent des appels DCOM (Distributed Component Object Model) au serveur, vérifiez que vous n'avez pas de pare-feu de traduction d'adresses réseau (NAT, Network Address Translation) activé. Le client doit pouvoir accéder au serveur par son adresse IP réelle, or les pare-feu NAT convertissent cette adresse en un élément non reconnu par le client.  
  
-   IBM Mainframe with CICS et Transaction X si vous utilisez une variation de la solution nécessitant un macroordinateur. Dans ce cas, l'application CICS (code COBOL) doit être installée sur le macroordinateur et Microsoft Host Integration Server (HIS) est requis pour accéder au macroordinateur.  
  
     Si vous ne disposez pas d'un macroordinateur pour la solution, vous pouvez modifier la liaison du port de manière à utiliser le service Web Pending Transactions stub. Le service Web génère des transactions localement pour émuler celles du macroordinateur. Pour plus d’informations sur la façon de modifier la liaison de port pour le service Web Pending Transactions stub, consultez [comment installer les Versions d’adaptateur de la Solution orientée services Inline](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md).  
  
-   Host Integration Server est requis pour se connecter au macroordinateur.  
  
    > [!NOTE]
    >  Host Integration Server est inclus dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
-   Serveur Web configuré avec un certificat pour les connexions HTTPS.  
  
## <a name="see-also"></a>Voir aussi  
 [Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [Pour exécuter le Service Solution orientée services](../core/how-to-run-the-service-oriented-solution.md)   
 [Installation d’ordinateur de développeur pour le Service orienté solutions](../core/developer-machine-setup-for-the-service-oriented-solution.md)