---
title: "Messages de l’adaptateur BizTalk pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- TIBCO Rendezvous
- messages
- message passing
- messages, passing
ms.assetid: 12699550-22e7-4a11-a024-2302570970af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4bc1eadbefdeb5c59df9a1b999ffdd3e530587a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-in-biztalk-adapter-for-tibco-rendezvous"></a>Messages dans l'adaptateur BizTalk pour TIBCO Rendezvous
L'adaptateur BizTalk pour TIBCO Rendezvous assure la connectivité bidirectionnelle entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et TIBCO Rendezvous. Il utilise l'API TIBCO Rendezvous et l'API d'infrastructure d'adaptateurs BizTalk pour offrir une intégration étroite.  
  
## <a name="about-tibco-rendezvous"></a>À propos de TIBCO Rendezvous  
 TIBCO Rendezvous est un logiciel qui inclut un bus de messages pour l'intégration des applications d'entreprise (IAE). Il inclut des API de messagerie en C, C++, Java, Visual Basic et pour Microsoft .NET Framework recevoir des flux de données sur des feuilles de calcul Microsoft Office Excel et d’autres applications de choix. Pour plus d’informations, consultez [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md).  
  
### <a name="message-passing"></a>Transmission de messages  
 Le concept de base de la transmission de messages est relativement simple :  
  
-   Un message inclut un sujet unique constitué d'éléments séparés par des points. Un message est envoyé à un démon Rendezvous (même s'il peut être transmis à d'autres démons).  
  
-   Un port d'écoute annonce ses sujets d'intérêt à un démon (à l'aide d'une fonction de caractère générique de base). Les messages ayant des sujets correspondants lui sont remis si les deux démons sont connectés ou correspondent au même démon.  
  
 Des fonctionnalités pour l'entreprise peuvent être superposées à celle-ci (options Tolérance de panne/Fiable ou Certifié possibles), toutes implémentées via les messages de base sous-jacents.  
  
 Les messages eux-mêmes peuvent être affichés comme champs nom/valeur ou nombre/valeur entrés (les deux mécanismes d'identification dans un message peuvent être combinés avec certaines restrictions). Un message peut contenir des sous-messages, qui peuvent eux-mêmes contenir des sous-messages.  
  
 Les noms de sujet sont constitués d'un ou plusieurs éléments séparés par des points. Les éléments implémentent une hiérarchie de noms de sujet qui reflète la structure des informations dans un système d'application. Les chaînes suivantes sont des exemples de noms de sujet valides :  
  
-   RUN.HOME  
  
-   RUN.for.Elected_Office  
  
 L'adaptateur BizTalk pour TIBCO Rendezvous utilise le Kit de développement logiciel (SDK) TIBCO Rendezvous pour publier des messages dans les sujets TIBCO Rendezvous et s'inscrire à des événements TIBCO Rendezvous. Les classes associées à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont hébergées sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Un processus distinct (agent d'exécution) est démarré et agit comme programme Rendezvous. L'accès à distance .NET Framework permet l'échange de messages entre les deux.  
  
-   Les messages des niveaux Informations, Avertissement et Erreur sont envoyés au journal des événements Windows.  
  
-   Tous les niveaux de message, y compris les messages de niveau Débogage, sont envoyés au journal des suivis Windows.  
  
#### <a name="transmitter"></a>Émetteur  
 L'adaptateur BizTalk pour TIBCO Rendezvous lance un agent d'exécution par port d'envoi. L'API .NET Framework TIBCO Rendezvous permet uniquement de définir le codage des caractères sur une étendue globale. Aussi, l'une des options de configuration des ports est un numéro de page de codes. En démarrant un autre processus pour chaque page de codes, l'adaptateur offre une prise en charge optimisée de la globalisation.  
  
#### <a name="receiver"></a>Récepteur  
 L'adaptateur BizTalk pour TIBCO Rendezvous lance un agent d'exécution par emplacement de réception.  
  
#### <a name="transactions"></a>Transactions  
 Le produit TIBCO Rendezvous n'est pas transactionnel. Un produit distinct, TIBCO Rendezvous TX, est requis. Cette version de l'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les transactions.  
  
#### <a name="security"></a>Sécurité  
 TIBCO Rendezvous prend uniquement en charge l'authentification entre les programmes et démons TIBCO Rendezvous. Il n'utilise pas l'autorisation ou le chiffrement. Un produit distinct, TIBCO Rendezvous DataSecurity, est requis.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)