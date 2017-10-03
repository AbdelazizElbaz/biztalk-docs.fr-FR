---
title: "Qu’est SWIFTNet ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b074385-352c-40f4-b73e-1891c627aa4e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1668c1f568a6cfb853957b3598b41f1cbdf6e33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-swiftnet"></a>Qu’est SWIFTNet ?
Comme un usage général, la solution standard de l’industrie pour le secteur financiers, SWIFTNet fournit une interface de fenêtre indépendante de l’application, unique à toutes les applications connectées de tous les établissements participant à la Communauté financière globale. Accès réel est contrôlé par les décisions de stratégie de chaque administrateur de Service, et non par les limitations techniques de l’infrastructure.  
  
 SWIFTNet fournit une base pour s’assurer de business la continuité des activités et récupération d’urgence pour l’infrastructure d’applications financières critiques dépassant les limites institutionnelles. SWIFTNet est conçu pour satisfaire aux exigences de la Communauté institutionnelles pour l’interopérabilité des solutions logicielles financières critiques.  
  
 Avec des applications métier interconnectés SWIFTNet offre les avantages suivants :  
  
-   Garantie de fiabilité de l’infrastructure  
  
-   Disponibilité  
  
-   Contrôle d’accès en fonction du rôle et non basée sur un rôle  
  
-   Authentification correspondant et message  
  
-   Intégrité des messages  
  
-   Confidentialité  
  
-   Prise en charge de la non répudiation  
  
-   Validation de message  
  
-   Stocker et de transfert  

SWIFTNet utilise **SWIFTNet lien** (SNL) en tant que l’interface de programmation d’application et les services de SWIFTNet, utilise le **SWIFTAlliance passerelle** pour la connectivité et la facilité d’utilisation. En savoir plus sur ces ressources dans cette rubrique.

## <a name="swiftnet-link-overview"></a>Vue d’ensemble de la liaison de SWIFTNet

Applications commerciales utilisent l’interface de programmation d’application (API) de lien SWIFTNet (SNL) pour accéder et utiliser les services SWIFTNet. Le SNL est l’interface réseau obligatoire SWIFTNet. SWIFTNet requiert SNL pour toutes les interfaces externes. La SNL inclut également les processus en arrière-plan qui prennent en charge la messagerie, la sécurité et les fonctions de gestion de service. Le SNL est incorporé dans SWIFTAlliance WebStation et de la passerelle SWIFTAlliance (trous).  
  
 SNL établit une relation de client/serveur faiblement couplée entre les composants d’application métier. Au lieu d’appeler directement les méthodes ou des fonctions, l’interaction est orienté messages : messages structurés sont passés entre le client et le serveur. Une application d’entreprise conçue généralement pour les services de SWIFTNet se compose d’un ensemble de clients et serveurs. Le même client ou le même processus serveur peut être démarré à plusieurs reprises. Notez que vous ne pouvez pas prédire les processus de l’instance de la même application, une demande entrante du message sera remis. Plusieurs threads dans un processus client peuvent appeler la fonction d’API de SwCall. Un processus serveur peut avoir plusieurs threads. Toutefois, un seul thread peut appeler SwCallback. Les processus client et le serveur ne peut pas être combinés dans le même processus.  
  
 SNL fournit un ensemble de fonctionnalités au niveau du transport conçus pour une haute disponibilité et les environnements de débit élevé. Ces fonctionnalités sont notamment :  
  
-   L’équilibrage de charge  
  
-   Transparence de l’emplacement et le routage, les composants d’application à partir de la technologie de transport sous-jacente de protection  
  
-   L’authentification au niveau du transport et la confidentialité, Sever SNL et fourni en toute transparence à l’application  
  
-   Fonctions de sécurité par lequel les logiciels d’application peuvent établir la sécurité de bout en bout (application de l’utilisateur à l’utilisateur de l’application), à la demande.  
  
 En termes de programmation au niveau du code source à l’aide de C++ ou Java, il existe seulement deux fonctions : SwCall et SwCallback. SwCall est utilisé par les applications clientes pour accéder à des applications de serveur via SWIFTNet. SwCallback est utilisé par les applications serveur pour répondre aux clients via SWIFTNet.  
  
 Les fonctions SwCall et SwCallback accéder aux fonctionnalités de SWIFTNet en passant des messages XML structurés vers et depuis SWIFTNet. Au moment de l’exécution, SNL inclut les deux bibliothèques de logiciels, le code qui s’exécute dans le même espace d’adressage en tant que processus client ou serveur d’applications métier, et les espaces d’adressage de processus indépendants (démons ou services), qui s’exécutent dans leurs propre. Les bibliothèques de logiciels sont accessibles via les API SNL.  

## <a name="swiftalliance-gateway-overview"></a>Vue d’ensemble de la passerelle de SWIFTAlliance
  
La passerelle SWIFTAlliance (trous) est une interface pour SWIFTNet. Il intègre toutes les fonctionnalités de la liaison SWIFTNet. En outre, il fournit plusieurs fonctions d’utilisation et de connectivité pour les utilisateurs SWIFTNet, fournir des solutions à une variété de système des problèmes d’intégration.  
  
 Les trous prend en charge plusieurs modes d’opération. Un de ces éléments, le Mode de liaison SWIFTNet strict, est particulièrement utile pour les adaptateurs FileAct et InterAct pour SWIFT. En Mode de liaison SWIFTNet strict, les trous présente une interface de messagerie est fonctionnellement équivalente à l’interface SWIFTNet lien comme cela est décrit dans l’ensemble de ces rubriques.  
  
 Les trous sert un concentrateur de message. Il reçoit des messages à partir de diverses autres applications et les transmet via SWIFTNet. Il reçoit ces messages via des adaptateurs, y compris un adaptateur hôte WebSphere MQ, ce qui permet aux applications d’entreprise en cours d’exécution sur un grand nombre de différents types de plateformes informatiques transmettre les messages via SWIFTNet.  
 
 ## <a name="next-reading"></a>Lecture suivante
 
 [Nouveautés de l’adaptateur FileAct ?](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)  
 [Quelle est l’interagir adaptateur ?](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)  
 [BizTalk FileAct et interagir didacticiel de bout en bout pour les cartes](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md)
 
 ## <a name="see-also"></a>Voir aussi
 [Présentation des adaptateurs FileAct et interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)