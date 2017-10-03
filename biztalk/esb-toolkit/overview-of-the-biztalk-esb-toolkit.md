---
title: "Vue d’ensemble de la boîte à outils ESB dans BizTalk Server | Documents Microsoft"
description: "Explication de la boîte à outils ESB, et ce qu’il fait dans BizTalk Server"
caps.latest.revision: "6"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e190b34-40bc-4f27-9b4f-56e98591e1d4
ms.author: mandia
ms.openlocfilehash: 9ce0bbe3710530a63127701447db87b0a3135b4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-biztalk-esb-toolkit"></a>Nouveautés de BizTalk ESB Toolkit

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] étend les fonctionnalités de BizTalk Server pour prendre en charge une architecture de messagerie faiblement couplée. La plupart des développeurs connaissent des paradigmes de développement orienté code, procédures ou orientée objet. Toutefois, lors du démarrage de développer des solutions BizTalk, les développeurs ont tendance à ignorer les fonctionnalités orienté messages de BizTalk Server.  
  
 BizTalk Server comprend un mécanisme de publication/abonnement puissant qui fonctionne en créant et en remplissant des abonnements. Lorsqu’un nouveau message arrive dans la base de données MessageBox de BizTalk, un agent de message identifie les abonnés et envoie le message à des points de terminaison qui ont des abonnements. Abonnements peuvent être créés de différentes façons, notamment la liaison d’une orchestration à un port de réception ayant une réception corrélée en attente d’un message ou la création d’un port d’envoi d’une condition de filtre qui correspond à une propriété du message (par exemple, le type, la réception point, ou la valeur d’une propriété routable).  
  
 Grâce à cette approche efficace et évolutive, BizTalk Server permet aux développeurs de créer une série de sous-processus discrètes, définir les types de messages qui déclenchent leur appel et ne vous inquiétez pas sur la séquence. Un processus initié par l’arrivée d’un message effectue son traitement du message ; Lorsqu’il a traité le message, il peut fournir ou dans un autre message à la base de données MessageBox, qui, à son tour, peut-être y activer un ou plusieurs sous-processus.  
  
 Microsoft fournit les blocs de construction clés qui sont requis pour la création d’Infrastructures de Service-Oriented complète, y compris Windows Server, le .NET Framework et BizTalk Server. Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est basée sur BizTalk Server, car il fournit la base pour les services ESB courants, notamment les suivantes :  
  
-   Routage des messages  
  
-   Validation de message  
  
-   Transformation des messages  
  
-   Structure d’adaptateur extensible pour la connectivité  
  
-   Orchestration des services  
  
-   Moteur des règles d’entreprise  
  
-   L’analyse BAM  
  
-   Service Web et WS-* intégration (adaptateur WCF)  

## <a name="core-capabilities"></a>Fonctionnalités principales  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] étend les fonctionnalités de BizTalk Server pour fournir une plage de nouvelles fonctionnalités de focus sur la création d’applications orientées service robustes, connectées. Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] traite des composants de BizTalk Server comme des unités de travail qui peuvent être connectés, comme vous le souhaitez, pour former faiblement couplés solutions. Voici certaines des fonctionnalités de base qui le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit pour améliorer les fonctionnalités de BizTalk Server :  
  
-   **Fonction de médiation des stratégies.** Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :  
  
    -   Il fournit le routage basé sur un itinéraire qui prend en charge la composition légère de service au moment de la publication des messages. Cette approche permet la découverte dynamique des points de terminaison de service et les exigences de médiation pour le routage des messages à l’aide d’un Registre de service ou de la stratégie de règles d’entreprise.  
  
    -   Il ajoute la prise en charge de centralisation de la stratégie du routage à l’aide d’itinéraires côté serveur qui sont résolus et ajoutés au contexte du message après un message dynamiquement en fonction des itinéraire est reçu. La gestion des itinéraires dans un emplacement central permet le traitement des messages à partir de clients qui ne connaissent pas complètement comment leurs demandes sont routés.  
  
    -   Elle utilise une version améliorée de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et l’infrastructure du fournisseur de carte, ce qui permet une résolution dynamique des points de terminaison et les exigences de la transformation ; Cela dissocie efficacement le consommateur à partir des services.  
  
-   **Connexion de systèmes.** Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :  
  
    -   Il fournit des composants de pipeline normalisent les espaces de noms de message XML.  
  
    -   Il s’intègre avec JMS via l’adaptateur WebSphere MQ pour BizTalk Server.  
  
    -   Il facilite les modèles d’échange de message qui permettent une agrégation dynamique, le routage des messages, validation de message et transformation des messages.  
  
    -   Il prend en charge la découverte de point de terminaison de service à partir du Registre et intégration du référentiel à l’aide de UDDI 3.0.  
  
    -   Il prend en charge le routage des messages via des cartes de métier (LOB) à l’aide de l’adaptateur BizTalk WCF-Custom pour BizTalk Server.  
  
-   **Gestion et surveillance.** Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :  
  
    -   Il fournit des outils et infrastructure de gestion des exceptions.  
  
    -   Il facilite le message repair et renvoyés à l’aide d’un portail de gestion fournis comme exemple d’application. Cette application Web prend également en charge les notifications par courrier électronique personnalisable lorsqu’une erreur spécifique se produit.  
  
    -   Elle permet l’intégration de point de terminaison et le Registre de BizTalk Server, la gestion et la publication.  
  
    -   Il fournit un référentiel centralisé des itinéraires de côté serveur avec version.  
  
    -   Il prend en charge analytique et création de rapports pour les applications BizTalk Server.  
  
    -   Il inclut des composants de l’analyse BAM pour effectuer le suivi de l’exécution de la feuille de route de service, y compris l’heure de début, heure de fin et de séquences de médiation de service.  
  
-   **Gouvernance SOA.** Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] effectue les opérations suivantes :  
  
    -   Il s’intègre avec les solutions de gouvernance SOA tierces, y compris les agents de gestion intégrée pour BizTalk Server à partir de AmberPoint et SOA logiciel.  

> [!TIP]
> [Présentation de BizTalk Server](../core/understanding-biztalk-server.md) fournit plus de détails sur le moteur de messagerie et bien plus encore.

## <a name="get-some-help"></a>Obtenir de l’aide
Obtenir de l’aide et aider les autres à le [BizTalk ESB Toolkit forums](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409).

## <a name="next-steps"></a>Étapes suivantes
[Contenu de BizTalk ESB Toolkit](contents-of-the-biztalk-esb-toolkit.md)  
