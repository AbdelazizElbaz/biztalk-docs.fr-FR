---
title: "Conception de l’infrastructure de gestion d’Exception ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfc2688c-c01c-4244-9e35-3d482135d8b7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c9bf8691701aa9fba8060865fcd3cb5abfba06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="design-of-the-esb-exception-management-framework"></a>Conception de l’infrastructure de gestion d’Exception ESB
Cohérentes et réutilisables des modèles pour la gestion des exceptions sont un facteur important de noyaux d’un projet de développement ; ils aident à optimiser la facilité de maintenance et en faciliter la prise en charge de l’application après le déploiement.  
  
 Une application BizTalk de type peut utiliser les fonctionnalités de messagerie BizTalk, si vous le souhaitez démarrer une orchestration de traitement, appeler le moteur de règles d’entreprise, interagir avec plusieurs line-of-business (LOB) ou une ressource d’entreprise (ERP) systèmes et retourner un réponse à un système tiers distinct. En outre, l’emplacement d’exécution de ces composants, y compris les sous-systèmes de BizTalk, peut-être résider sur un ou plusieurs serveurs répartis dans l’environnement actuel. Ceci est un scénario classique et requiert le système pour prendre en charge les intercepter et les rapports d’exceptions qui peuvent se produire dans les ESB ou BizTalk découplées sous-systèmes ou dans les différents systèmes métier tiers, chacune ayant ses propres contraintes d’exceptions. Par exemple, le macroordinateur peut rejeter une commande envoyée à partir d’un site Web pendant un cycle de traitement normal. le site Web doit compenser cette erreur et informer l’utilisateur.  
  
 En raison de la complexité des applications d’ESB et leur environnement, le développement d’une solution cohérente pour la gestion des exceptions application doit sont basées sur les objectifs de conception courants suivants :  
  
-   Fournir une approche standardisée de détection et la gestion des exceptions qui se produisent dans l’environnement BizTalk Server (autrement dit, dans les sous-systèmes de messagerie et d’orchestration).  
  
-   Fournir des modèles courants qui autorisent les processus automatisés réagir à et de gérer les exceptions d’application.  
  
-   Fournissent un modèle de gestion d’exception faiblement couplées qui facilite la réutilisation.  
  
-   Fournissent un mécanisme de création de rapports commun pour les exceptions d’application et de leurs États de message disponibles qui peuvent s’appliquer à n’importe quel sous-système de BizTalk.  
  
 Pour comprendre pourquoi le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit un mécanisme d’erreur personnalisés, à savoir l’infrastructure de gestion des exceptions, et comment il fonctionne, il est nécessaire de comprendre les fonctionnalités de gestion des exceptions disponibles dans BizTalk Server et pourquoi ces fonctionnalités ne sont pas entièrement capable de satisfaire les objectifs de conception précédent.  
  
## <a name="biztalk-server-exception-reporting"></a>Rapports d’exceptions BizTalk Server  
 BizTalk Server prend en charge l’exception suivante, la gestion et de mécanismes de notification :  
  
-   Routage des messages ayant échoué  
  
-   Console Administration de BizTalk Server  
  
-   Journal des événements Microsoft  
  
-   Options de développement personnalisé  
  
 Par défaut, les fonctionnalités de BizTalk Server pour la gestion des exceptions dépendent beaucoup l’intervention de l’opérateur. Par exemple, considérons la situation où un utilisateur envoie un message à BizTalk Server qui lève une exception pendant l’étape de validation. Par défaut, le message est publié dans la base de données MessageBox, où il est routé vers une file d’attente suspendue. Cela signifie qu’un opérateur doit effectuer les opérations suivantes :  
  
-   Indépendamment de détecter qu’une exception s’est produite.  
  
-   Enregistrer manuellement le message ayant échoué sur le disque à l’aide de la [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration.  
  
-   Manuellement, modifier et corriger le message et renvoyez-le au système. Dans certains cas, ce processus présente un risque de perdre des informations de contexte importantes.  
  
 Pour résoudre ces problèmes, [!INCLUDE[prague](../includes/prague-md.md)] fournit le mécanisme de routage des messages a échoué. Les développeurs et administrateurs cela utiliser pour créer des processus d’orchestration ou de messagerie des ports d’envoi configurés pour s’abonner à toutes les exceptions qui se produisent dans le sous-système de messagerie. Cela fournit une détection automatique des erreurs et le mécanisme de routage qui conserve l’état du message d’origine et qui résout le problème de détection d’exceptions.  
  
 Étant donné que le routage automatique des messages ayant échoué n’est fourni que pour les processus d’orchestration, le développeur doit tenir compte des erreurs en ajoutant des blocs de gestionnaire d’exception pour les formes d’orchestration étendue. Avec cette solution, chaque orchestration peut avoir sa propre gestion des exceptions, mais il n’existe aucun mécanisme de réutilisation des fonctionnalités sur plusieurs orchestrations de gestion des exceptions.  
  
 Cela signifie qu’il existe désormais deux manières très différentes, dans laquelle les exceptions de messagerie sont traitées et gérées dans un système BizTalk Server et une troisième méthode dans quelle orchestration exceptions sont traitées. Par conséquent, les développeurs doivent personnaliser mécanisme en fonction de leurs propres spécifications s’ils souhaitent mettre en œuvre d’un système qui correspond aux critères décrits précédemment dans cette section de la gestion des exceptions.  
  
## <a name="biztalk-server-administration-console"></a>Console Administration de BizTalk Server  
 Le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration fournit un ensemble de pages de vue d’ensemble du groupe, appelé le Hub du groupe BizTalk. À l’aide de ces pages, les administrateurs peuvent interroger pour les messages suspendus et les exceptions groupées par application, nom du service, code d’erreur ou un URI, comme indiqué dans la Figure 1.  
  
 ![Console d’administration](../esb-toolkit/media/ch4-adminconsole.gif "chapitre 4-AdminConsole")  
  
 **Figure 1**  
  
 **Le [!INCLUDE[prague](../includes/prague-md.md)] pages de vue d’ensemble du groupe Administration Console**  
  
 Bien que la fonctionnalité de vue d’ensemble du groupe fournit une interface utilisateur commune pour afficher les exceptions, les vues sont limitées à des instances de service « live ». Examiner l’état peut être une tâche fastidieuse, car les administrateurs doivent descendre dans l’arborescence à chaque élément. En outre, plusieurs autres facteurs limitent les fonctionnalités de la Console Administration de BizTalk Server comme outil de rapport d’exception d’application :  
  
-   Il n’existe aucune fonctionnalité d’exploration de données business intelligence. Par exemple, vous ne peut pas interroger pour les applications le pire des cas qui posent problème sur une base mensuelle ou examiner les tendances de tous les trimestres pour les exceptions d’application.  
  
-   L’entreprise peut-être nécessiter des alertes à déclencher lorsque certaines exceptions d’application se produisent ou moment d’atteindre des seuils spécifiques, mais il n’existe aucune fonctionnalité pour vous abonner à ces types d’événements d’exception.  
  
-   La Console MMC (Microsoft Management Console) que la Console d’Administration utilise en tant que son interface utilisateur mécanisme (d’interface utilisateur) n’est pas une interface idéale, et il n’est pas toujours pratique accéder aux environnements de production. Au minimum, il requiert que les utilisateurs soient membres du rôle opérateurs BizTalk ; et, dans les environnements de production, l’accès à la console MMC n’est possible que via les services Terminal Server.  
  
-   La console affiche uniquement les exceptions (instances de service suspendues) non gérées. Si le développeur gère l’exception dans l’orchestration, l’orchestration à se terminer normalement, les informations sur les exceptions n’apparaîtront jamais dans la Console d’Administration.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] traite ces limitations par le biais du mécanisme d’ESB Échec de l’Orchestration Exception routage. Cela ressemble étroitement au mécanisme de routage des messages d’échec de [!INCLUDE[prague](../includes/prague-md.md)]. En outre, le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut un composant de pipeline dans un port d’envoi qui s’abonne aux messages générés à partir du mécanisme ESB Échec de l’Orchestration Exception routage et le mécanisme de routage des messages a échoué et normalise les.  
  
 L’infrastructure de gestion d’Exception ESB tire parti d’autres fonctionnalités dans BizTalk Server, telles que le modèle d’abonnement et sur des événements d’analyse BAM (Business Activity). Cela signifie que l’infrastructure de gestion d’Exception ESB peut suivre les points de données d’exception avec BAM, puis les publier sur le portail BAM de BizTalk pour l’analyse.