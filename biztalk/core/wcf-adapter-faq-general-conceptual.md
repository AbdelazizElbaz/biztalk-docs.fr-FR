---
title: "FAQ sur les adaptateurs WCF : Informations conceptuelles générales | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbeac135-3ba8-4b0b-a8ca-4eb5eb3d3ca3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f5acc3cb968ab35436fe684edd0eb41088b48a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-adapter-faq-general-conceptual"></a>FAQ sur les adaptateurs WCF : informations conceptuelles générales
Ci-dessous figurent certaines questions générales et conceptuelles fréquemment posées concernant les adaptateurs Windows ® Communication Foundation (WCF).  
  
## <a name="what-is-a-wcf-adapter"></a>Qu'est-ce qu'un adaptateur WCF ?  
 Un adaptateur BizTalk est un élément clé de la communication entre Microsoft® BizTalk® Server et le monde extérieur. Un adaptateur WCF est un composant qui gère le processus de communication entre une application BizTalk et son besoin d'échanger des messages avec un point de terminaison WCF. Dans [!INCLUDE[prague](../includes/prague-md.md)], les adaptateurs WCF sont exposés en tant que liaisons WCF. Cela signifie que toute application WCF capable d'utiliser une liaison WCF peut communiquer directement avec les adaptateurs, sans intervention de BizTalk Server. Toutefois, l'utilisation des adaptateurs WCF via BizTalk Server offre un grand nombre des avantages d'infrastructure pour les applications offerts par BizTalk Server. Ce Forum Aux Questions (FAQ) est essentiellement consacré à l'utilisation des adaptateurs WCF à partir de l'environnement BizTalk Server.  
  
 Un adaptateur WCF permet à BizTalk Server d'utiliser les liaisons WCF pour envoyer et recevoir des messages WCF. Une application WCF cliente peut envoyer un message WCF à un emplacement de réception BizTalk, où le message est reçu par un adaptateur de réception WCF. L'adaptateur convertit le message WCF en un message BizTalk. Le mode de conversion dépend de certains paramètres de configuration d'adaptateur qui sont définis à l'aide de la console Administration de BizTalk Server. L'adaptateur soumet le message BizTalk à la base de données MessageBox BizTalk interne. Ensuite, un port d'envoi BizTalk utilisant un adaptateur WCF peut s'abonner à ce type de message, obtenir le message BizTalk, le convertir en message WCF, puis transmettre ce dernier à un point de terminaison de service WCF à l'aide de l'un des protocoles WCF pris en charge.  
  
 L'utilisation des adaptateurs WCF à partir de BizTalk Server permet d'éviter les complexités masquées liées à une solution d'application BizTalk-WCF, telles que le choix et l'implémentation de protocoles de communication, les problèmes de sécurité et les opérations transactionnelles.  
  
## <a name="what-are-the-wcf-adapter-bindings"></a>Quelles sont les liaisons de l'adaptateur WCF ?  
 Les liaisons WCF se classent en deux catégories :  
  
-   **Liaisons personnalisées :** pour améliorer la flexibilité de liaison, la liaison personnalisée spéciale existe. Celle-ci a trait à des situations de communication qui nécessitent des écarts par rapport aux liaisons standard. Les adaptateurs WCF-Custom et WCF-CustomIsolated permettent le développement de personnalisations de liaison étendues. Cela est effectué en autorisant la composition d'éléments de liaison existants (classe BindingElement) avec l'application de comportements (classe Behavior).  
  
-   **Les liaisons standard :** l’objectif de Microsoft consiste à développer des adaptateurs axés sur les scénarios de communication les plus courants. L'utilisation de liaisons standard simplifie l'expérience du développeur en masquant de nombreux détails des protocoles de communication. L'ensemble des adaptateurs WCF dans [!INCLUDE[prague](../includes/prague-md.md)] reflète l'ensemble des liaisons disponibles dans les bibliothèques WCF .NET Framework 4.0. Les liaisons standard ont été introduites dans les bibliothèques WCF .NET afin de faciliter l'utilisation des modèles de liaison classiques. Elles recouvrent les scénarios de communication les plus couramment utilisés et comprennent les éléments suivants :  
  
    -   WCF-WsHttp  
  
    -   WCF-BasicHttp  
  
    -   WCF-NetTcp  
  
    -   WCF NetMsmg  
  
    -   WCF-NetNamedPipe  
  
 BizTalk Server R2 comprend les adaptateurs WCF suivants :  
  
1.  **Adaptateur WCF-WSHttp :** fournit WS-* prend en charge les normes via le transport HTTP. L'adaptateur WCF-WSHttp met en œuvre les spécifications suivantes : WS-Transaction pour les interactions transactionnelles entre des applications externes et la base de données MessageBox, et WS-Security pour la sécurité et l'authentification des messages. Le transport est HTTP ou HTTPS, et l’encodage de message est un texte ou encodage (Message Transmission Optimization Mechanism).  
  
2.  **Adaptateur WCF-BasicHttp :** communique avec les services Web basés sur ASMX et les clients et autres services conformes à WS-I Basic Profile 1.1. Le transport est de type HTTP ou HTTPS, et le codage des messages de type texte.  
  
3.  **Adaptateur WCF-NetTcp :** fournit WS-* prend en charge les normes via le transport TCP. L'adaptateur WCF-NetTcp permet une communication efficace et met en œuvre les spécifications suivantes : WS-Transaction pour les interactions transactionnelles entre des applications externes et la base de données MessageBox, et WS-Security pour la sécurité et l'authentification des messages. Le transport est de type TCP et le codage des messages est binaire.  
  
4.  **Adaptateur WCF-NetMsmq :** prend en charge queuing en utilisant Message Queuing (également appelé MSMQ) comme une prise en charge du transport et permet de faiblement couplés des applications, l’isolation de défaillance, le nivellement de charge et des opérations déconnectées.  
  
5.  **Adaptateur WCF-NetNamedPipe :** assure une optimisation sécurisée pour la communication entre processus sur l’ordinateur. L'adaptateur WCF-NetNamedPipe utilise la sécurité de transport pour le transfert, des canaux nommés pour la remise des messages, ainsi qu'un codage de message binaire.  
  
     Chacun des cinq adaptateurs précités correspond à une liaison WCF dans une relation de 1 à 1. La structure des deux adaptateurs personnalisés que nous allons décrire s'écarte légèrement du modèle WCF en ce qu'il s'agit en réalité de deux adaptateurs distincts qui correspondent à la liaison WCF CustomBinding.  
  
6.  **Adaptateur WCF-Custom :** permet d’utiliser des fonctionnalités d’extensibilité WCF. L'adaptateur permet de sélectionner et de configurer une liaison WCF et les informations de comportement pour un emplacement de réception et un port d'envoi hébergés dans le processus BizTalk Server.  
  
7.  **Adaptateur WCF-CustomIsolated :** permet d’utiliser des fonctionnalités d’extensibilité WCF via le transport HTTP. L'adaptateur permet de sélectionner et de configurer une liaison WCF et les informations de comportement pour un emplacement de réception exécuté dans l'hôte isolé des services Internet (IIS).  
  
## <a name="what-is-the-difference-between-the-wcf-xxx-adapter-and-the-wcf-xxx-binding"></a>Quelle est la différence entre l'adaptateur WCF-xxx et la liaison WCF-xxx ?  
 Chacun des adaptateurs WCF correspond à l'une des liaisons WCF intégrées. À un niveau supérieur, ces termes sont utilisés presque indistinctement en disant que l'adaptateur WCF-xxx utilise la liaison WCF-xxx. Par exemple, l'adaptateur WCF-BasicHttp utilise le classe WCF BasicHttpBinding. Une liaison WCF fait partie de la définition d'un point de terminaison WCF. C'est ce qu'on appelle l'« ABC » d'un point de terminaison WCF. Ces lettres sont les initiales des mots anglais Address (adresse), Binding (liaison) et Contract (contrat).  
  
 Une liaison est constituée d'une série d'éléments de liaison. Chaque élément décrit un aspect de la manière dont le point de terminaison communique avec les clients. Une liaison doit inclure :  
  
-   au moins un élément de liaison de transport ;  
  
-   au moins un élément de liaison de codage de message (que l'élément de liaison de transport peut fournir par défaut) ;  
  
-   un nombre quelconque d'autres éléments de liaison de protocole.  
  
 Le processus qui crée un environnement d'exécution à partir de cette description permet à chaque élément de liaison de contribuer au code de cet environnement. Il faut généralement que les types de liaisons et l'adaptateur d'un client correspondent à ceux pris en charge par le service WCF appelé. Au niveau du WCF, une liaison peut être définie de façon déclarative dans un fichier de configuration ou de façon explicite à l'aide d'un code. Un adaptateur WCF facilite la communication à l'aide d'une liaison WCF spécifique. Les termes « adaptateur » et « liaison » tendent ainsi à devenir synonymes dans leur usage.  
  
## <a name="when-using-the-wcf-adapters-how-do-you-decide-which-wcf-binding-to-use"></a>Lors de l'utilisation des adaptateurs WCF, comment décidez-vous de la liaison WCF à utiliser ?  
 Vous prenez cette décision en fonction du modèle de messagerie, des contraintes externes et des performances, dans cet ordre.  
  
1.  **Modèle de messagerie :** le modèle de communication est la façon dont la communication a lieu en fonction du flux du message. Par exemple, le message peut être unidirectionnel (requête) ou bidirectionnel (requête-réponse), traité, mis en file d'attente, etc.  
  
    -   S'il est mis en file d'attente, vous devez utiliser l'adaptateur WCF-NetMsmq qui prend en charge la communication traitée mise en file d'attente unidirectionnelle.  
  
    -   Si le modèle est une requête-réponse bidirectionnelle et que le flux intervient entre deux ordinateurs, vous devez utiliser HTTP (si vous souhaitez favoriser la flexibilité) ou WCF-NetTcp (si vous souhaitez favoriser les performances).  
  
    -   Si le message reste sur un seul ordinateur où il fait l'objet de divers processus, vous pouvez utiliser la liaison WCF-NetNamedPipe.  
  
2.  **Contraintes externes :** il peut y avoir des problèmes qui vous amener à opter une liaison spécifique. Par exemple, supposons que le système externe nécessite SOAP Web Services version 1.2 et Addressing 1.0. Dans ce cas, le meilleur choix de liaison est WSHttpBinding avec l'adaptateur WCF-WsHttp. En toute probabilité, le système externe impose également des exigences en relation avec le mode de sécurité particulier à configurer. Si le système externe requiert Soap Web Services 1.1, vous devez utiliser l'adaptateur WCF-BasicHttp pour la liaison HTTP.  
  
3.  **Performances :** la vitesse à laquelle l’appel peut être un facteur décisif dans la liaison à laquelle vous souhaitez utiliser dans votre application :  
  
    -   Si le service WCF est exécuté sur le même ordinateur que BizTalk Server, l'utilisation de l'adaptateur WCF-NetNamedPipe constitue meilleur choix en termes de performances.  
  
    -   Si le service WCF est exécuté sur votre réseau local, l'adaptateur WCF-NetTcp offre les meilleures performances.  
  
    -   Si les performances ne sont pas une considération majeure et que l'appel passe par Internet, les deux adaptateurs basés sur HTTP (WCF-WsHttp et WCF-BasicHttp) conviennent.  
  
         Le choix de l'adaptateur le plus approprié varie selon que vous utilisez une fonctionnalité HTTP avancée (WCF-WsHttp) ou de base (WCF-BasicHttp).  
  
## <a name="when-do-you-use-one-of-the-two-custom-wcf-adapters"></a>Quand utilisez-vous un des deux adaptateurs WCF personnalisés ?  
 [!INCLUDE[prague](../includes/prague-md.md)] intègre deux adaptateurs WCF personnalisés. La raison à cela est que BizTalk Server exige que l'hébergement d'un type d'adaptateur particulier fasse partie de son inscription dans le système. Bien qu'il n'y ait qu'un seul type de liaison CustomBinding dans l'infrastructure WCF, BizTalk Server intègre deux adaptateurs pour répondre à cette limitation du modèle d'adaptateur BizTalk préexistant. En réalité, ces adaptateurs sont réellement les seuls dont vous puissiez avoir besoin car ils permettent de contrôler totalement la configuration de la pile de canaux WCF.  
  
 Le seul inconvénient des adaptateurs personnalisés est qu'ils exigent que vous maîtrisiez bien la configuration WCF et les diverses techniques d'extensibilité.  Microsoft fournit des adaptateurs pour les liaisons WCF standard dans le but de simplifier la configuration. Les liaisons standard sont prédéfinies pour couvrir la plupart des cas d'utilisation courante et pour simplifier au maximum l'envoi et la réception de messages via BizTalk Server. La nécessité d'utiliser l'un de ces adaptateurs personnalisés ne se présente généralement que quand les liaisons standard ne permettent pas de répondre complètement ou exactement aux besoins de votre port d'envoi ou de votre emplacement de réception. Par exemple, il se peut qu'une application utilise un système de compression propriétaire pour ses messages. Dans ce cas, il convient d'écrire un élément de liaison personnalisée. Le recours à l'un des adaptateurs personnalisés standard permet de configurer cette liaison personnalisée pour prendre en compte l'exigence de transmission. Ainsi, un adaptateur personnalisé permet de mieux contrôler la configuration des liaisons pour ce processus de communication via la pile de canaux.  
  
 La principale différence entre l'adaptateur personnalisé et l'adaptateur isolé personnalisé a trait à l'hébergement qui n'a d'incidence que sur le côté réception de BizTalk Server. L'adaptateur WCF-CustomIsolated est utilisé uniquement avec un emplacement de réception et non avec un port d'envoi. Dans BizTalk, le terme « isolé » fait référence à un hébergement hors du processus BtsNtSvc.exe de BizTalk Server. C'est pourquoi l'adaptateur WCF-CustomIsolated est utilisé quand le transport est hébergé hors du processus BtsNtSvc.exe standard à l'intérieur des services Internet (IIS) qui utilisent le transport HTTP. L'adaptateur WCF-Custom peut être utilisé indifféremment avec un emplacement de réception ou un port d'envoi. Il est utilisé lorsque le transport est hébergé à l'intérieur du processus BtsNtSvc.exe standard.  
  
## <a name="how-does-a-wcf-endpoint-relate-to-biztalk-server"></a>Quel est l relation entre un point de terminaison WCF et BizTalk Server ?  
 Un point de terminaison WCF se compose d'une adresse, d'une liaison et d'un contrat (ABC pour Address, Binding, Contract). Dans BizTalk Server, l'utilisateur spécifie l'adresse dans l'emplacement de réception ou le port d'envoi. La liaison est dictée par l'adaptateur WCF que l'utilisateur a choisi. Le contrat dépend du programmeur dans la mesure où il spécifie l'interface exposée par le point de terminaison.  
  
 Le point de terminaison réel existe en tant qu'emplacement de réception auquel les messages WCF sont envoyés.  Il existe plusieurs façons d'exposer un point de terminaison WCF dans une application BizTalk Server :  
  
-   Vous pouvez utiliser l'Assistant Publication de services WCF BizTalk pour publier une orchestration BizTalk en tant que point de terminaison WCF.  
  
-   Vous pouvez utiliser l'Assistant Publication de services WCF BizTalk pour créer un emplacement de réception dans une application BizTalk existante.  
  
-   Vous pouvez créer manuellement un point de terminaison WCF en configurant la liaison et l'adresse d'un emplacement de réception à l'aide d'un code.  Dans ce cas, l'emplacement de réception est en réalité non typé.  Il est lié à un contrat qui spécifie uniquement la classe de message WCF, ce qui permet la réception de messages de tous formats dans la base de données MessageBox.  
  
 Chaque emplacement de réception BizTalk utilisant un adaptateur WCF est exposé en tant que point de terminaison WCF auquel un client WCF peut faire appel.  Un emplacement de réception utilise en interne son propre ServiceHost WCF, de façon à ce qu'il soit possible d'activer ou de désactiver les différents emplacements de réception indépendamment les uns des autres. La durée de vie du point de terminaison de service équivaut au temps d'activation de l'emplacement de réception. En raison de cette durée de vie, les ServiceHosts WCF correspondent aux emplacements de réception plutôt qu'aux ports de réception. La conception de WCF garantit que les différents ServiceHosts ne soient pas onéreux en ressources d'exécution et qu'il soit possible d'en exécuter un grand nombre à l'intérieur du même fichier exécutable sans aucun problème.  
  
 Chaque port d'envoi BizTalk utilisant un adaptateur WCF correspond à un appel fait à un service WCF. Quand il y a des messages à envoyer, BizTalk Server transmet à l'adaptateur les messages qui correspondent à la création du proxy de client WCF à l'intérieur de l'adaptateur WCF BizTalk. Une fois les messages envoyés, le proxy de client WCF est libéré. La durée de vie de WCF sur un port d'envoi varie constamment en fonction de la création, de l'utilisation et de la libération de proxy.