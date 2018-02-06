---
title: "Présentation de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 01/30/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06a4a31a-eefe-4b1b-89ca-2cba2b6fa587
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4de6778bef644dc7bbfa25b46c28b36e1741ba6f
ms.sourcegitcommit: d0a1816a8dd8412906245d40c6479b08d7b3b20a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="introducing-biztalk-server"></a>Présentation de BizTalk Server
Relier les systèmes est attendue et est devenu la norme. Grâce à l’adoption de solutions orientées services par les organisations, le véritable objectif (créer des processus d’entreprise efficaces qui unissent des systèmes distincts au sein d’un ensemble cohérent) devient accessible.  
  
 Microsoft BizTalk Server permet de connecter plusieurs logiciels, puis créer graphiquement et modifier la logique de processus qui utilise ce logiciel. BizTalk Server permet aux travailleurs de surveiller les processus en cours d’exécution, d’interagir avec des partenaires commerciaux et d’effectuer d’autres tâches orientées entreprise.  
  
 Nouvelles fonctionnalités principales de BizTalk Server sont :  
  
-   meilleure prise en charge pour le déploiement, la surveillance et la gestion des applications ;  
  
-   installation simplifiée ;  
  
-   capacités améliorées de l'analyse BAM (Business Activity Monitoring).  
  
BizTalk Server utilise également les dernières versions de technologies Microsoft. Il repose sur le .NET Framework, et les outils de développement sont hébergés dans Microsoft Visual Studio. Pour le stockage, BizTalk Server utilise SQL Server. BizTalk Server peut s’exécuter sur les serveurs Windows 64 bits, en tirant parti de la mémoire plus importante et d’autres avantages le matériel.  
  
## <a name="what-is-biztalk-server"></a>Qu'est-ce que BizTalk Server ?  
 La combinaison de différents systèmes en processus d'entreprise efficaces peut être un défi de taille. Dans cette perspective, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un éventail de technologies. Le schéma ci-dessous montre les principaux composants du produit.  
  
 ![Vue d’ensemble des composants de BizTalk Server](../core/media/d167608e-7c51-4d52-b8fa-9d4149242934.gif "d167608e-7c51-4d52-b8fa-9d4149242934")  
  
 Comme le suggère la figure, le moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est le cœur du produit. Il est constitué de deux éléments principaux :  
  
-   un composant de messagerie qui permet de communiquer avec d'autres logiciels. En utilisant des adaptateurs pour différents types de communication, le moteur peut prendre en charge divers protocoles et formats de données, notamment les services Web.  
  
-   la prise en charge de la création et de l'exécution des processus définis graphiquement (appelés orchestrations). Basées sur les composants de messagerie du moteur, les orchestrations implémentent la logique qui gère l’ensemble ou une partie d’un processus d’entreprise.  
  
 Plusieurs autres composants BizTalk peuvent être utilisés avec le moteur, notamment :  
  
-   un moteur de règles d'entreprise qui évalue les ensembles complexes de règles.  
  
-   un hub de groupe qui permet aux développeurs et administrateurs de surveiller et gérer le moteur et les orchestrations qu'il exécute.  
  
-   une fonctionnalité d'authentifications unique de l'entreprise qui permet de mapper les informations d'authentification entre des systèmes Windows et non-Windows.  
  
 Sur cette base, l'analyse BAM (Business Activity Monitoring) de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet aux travailleurs de l'information de contrôler les processus d'entreprise en cours d'exécution. Les informations affichées utilisent des termes professionnels plutôt que techniques. Les utilisateurs déterminent les informations à afficher.  
  
## <a name="connecting-diverse-systems"></a>Connexion de plusieurs systèmes  
 La majorité des processus d'entreprise actuels dépendent au moins en partie des logiciels. Si certains processus sont pris en charge par une seule application, d'autres dépendent de divers systèmes logiciels. Ceux-ci sont souvent créés à différents moments, sur différentes plateformes et à l'aide de différentes technologies. L'automatisation de ces processus d'entreprise requiert la connexion de plusieurs systèmes.  
  
 Désignent ces divers : automatisation des processus métier (BPA), gestion des processus d’entreprise (BPM) et d’autres. Quelle que soit la solution, il existe deux scénarios principaux pour l'intégration d'applications. Le premier consiste à connecter des applications au sein d'une organisation (intégration des applications de l'entreprise). L'autre consiste à connecter des applications de différentes organisations (intégration interentreprise).  
  
 La figure ci-dessous montre un exemple simple du moteur central de BizTalk Server appliqué à un cas d'intégration des applications d'une entreprise. Dans ce cas, une application d'inventaire, éventuellement exécutée sur un macroordinateur IBM, détecte le faible stock d'un article et émet une demande de commande d'exemplaires supplémentaires de cet article. La demande est envoyée à une orchestration BizTalk Server (étape 1). Celle-ci émet une demande de bon de commande auprès de l’application ERP de l’organisation (étape 2). L'application ERP, éventuellement exécutée sur un système Unix, renvoie le bon de commande demandé (étape 3). L'orchestration BizTalk Server informe une application de traitement des commandes, éventuellement basée sur Windows avec .NET Framework, que des exemplaires de l'article doivent être commandés (étape 4).  
  
 ![EAI implémentée dans le moteur de BizTalk.](../core/media/7d8558da-03cf-494b-8334-efe0ea15a6a7.gif "7d8558da-03cf-494b-8334-efe0ea15a6a7")  
  
 Dans cet exemple, chaque application communique à l'aide d'un protocole différent. Le composant de messagerie du moteur BizTalk Server doit donc être en mesure de communiquer avec chaque application dans son style natif. Par ailleurs, aucune application individuelle n'est informée du processus d'entreprise complet. L'intelligence requise pour la coordination des logiciels impliqués est implémentée dans l'orchestration BizTalk Server.  
  
 Si l'intégration d'applications au sein d'une organisation est importante, la connexion d'applications de plusieurs organisations n'a pas moins de valeur. La figure ci-dessous montre un exemple simple de ce type d'intégration interentreprise. Dans ce cas, l'organisation d'achat en haut de la figure exécute une orchestration BizTalk Server qui interagit avec deux organisations de fournisseur. Le fournisseur A utilise également BizTalk Server et offre un accès indirect à son application de fourniture. Le fournisseur B utilise une plateforme d’intégration d’un autre fournisseur et se connecte à l’orchestration BizTalk Server de l’organisation d’achat à l’aide, par exemple, de services Web.  
  
 ![Diagramme d’intégration d’entreprise-entreprise](../core/media/b1d8787d-e842-468e-96c5-b68875d9abc3.gif "b1d8787d-e842-468e-96c5-b68875d9abc3")  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de BizTalk Server](../core/understanding-biztalk-server.md)
