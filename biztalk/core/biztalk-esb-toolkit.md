---
title: BizTalk ESB Toolkit | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08035518-17ad-44d2-ab06-90d725c95ced
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 535fd99ee5c1b9f9c25dd49e2a2441acb855c78a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-esb-toolkit"></a>BizTalk ESB Toolkit
Microsoft BizTalk ESB Toolkit utilise Microsoft BizTalk Server pour prendre en charge une architecture de messagerie faiblement couplée. BizTalk Server inclut un mécanisme de publication/d'abonnement puissant pour les applications de messagerie qui crée et définit des abonnements, et offre une plateforme hautement efficace et évolutive pour les applications à l'architecture orientée services. BizTalk ESB Toolkit étend les fonctionnalités de BizTalk Server pour fournir de nouvelles capacités dédiées à la création d'applications orientées services connectées et robustes, qui appellent les services sur la base de l'itinéraire. Une telle approche présente divers avantages : composition légère des services, résolution dynamique des points de terminaison et des mappages, intégration des services Web et WS-*, gestion des erreurs et création de rapports, et intégration à des solutions de gouvernance SOA tierces.  
  
## <a name="overview"></a>Vue d'ensemble  
 BizTalk ESB Toolkit inclut des conseils et modèles relatifs à l'architecture, ainsi que divers composants BizTalk Server et .NET Framework qui simplifient le développement d'une architecture ESB (Enterprise Service Bus) sur la plateforme Microsoft et permettent aux clients Microsoft d'étendre leurs solutions de messagerie et d'intégration.  
  
## <a name="common-scenarios"></a>Scénarios courants  
 Le terme ESB (Enterprise Service Bus) est largement utilisé dans le cadre de l'implémentation d'une infrastructure pour mettre en place une architecture orientée services (SOA, Service-Oriented Architecture). L'expérience réelle de déploiement des SOA a toutefois montré qu'une architecture ESB n'est qu'un des blocs de construction permettant de former une infrastructure orientée services (SOI, Service-Oriented Infrastructure) complète. Le terme ESB a évolué dans différentes directions. Sa définition dépend de l'interprétation des fournisseurs de plateforme ESB et d'intégration individuels d'une part, et des conditions associées aux initiatives SOA spécifiques d'autre part. Selon l'expérience accumulée par Microsoft lors d'implémentations SOI réelles, une architecture ESB peut être comparée à un ensemble de modèles d'architecture basé sur l'intégration traditionnelle des applications de l'entreprise, des applications intermédiaires orientées messagerie, des services Web, l'interopérabilité .NET et Java, l'intégration des systèmes hôtes, l'interopérabilité avec les registres de services et les référentiels de ressources.  
  
## <a name="audience-requirements"></a>Public  
 BizTalk ESB Toolkit est destiné aux développeurs qui créent des solutions Microsoft BizTalk Server ou d'autres solutions basées sur les composants de BizTalk ESB Toolkit. Pour tirer pleinement parti de BizTalk ESB Toolkit, les développeurs doivent avoir des connaissances et de l'expérience en relation avec les éléments suivants :  
  
1.  Microsoft BizTalk Server  
  
2.  Microsoft Visual Studio  
  
3.  techniques de développement Microsoft .NET, notamment le développement de services Web ASP.NET Web et de composants .NET Framework.  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>Fonctionnement de BizTalk ESB Toolkit  
 BizTalk ESB Toolkit accepte les messages entrants et agit sur eux, éventuellement (mais pas toujours) en exécutant des processus (transformation, remise ou tout autre processus personnalisé). Pour spécifier les opérations requises, les instructions ou métadonnées associées qui définissent les processus à appliquer et les tâches à exécuter sur le contenu d'un message doivent être incluses dans le message.   
Cette approche fournit un couplage faible entre les services ; Cela signifie que l’architecture ESB ne nécessite pas la connaissance préalable du traitement spécifique pour chaque message. Elle doit simplement connaître les processus possibles et les modalités d'application de chaque processus. Les diverses options de spécification des processus disponibles et du mappage entre les processus, de même que les instructions au sein des messages, fournissent un mécanisme flexible pour configurer et ajuster le comportement, sans modification du code ni redéploiement des composants.  
  
## <a name="getting-started"></a>Mise en route  
 Après l’installation de BizTalk ESB Toolkit, vous devez lire la rubrique « Getting Started » dans le [BizTalk ESB Toolkit Documentation](http://go.microsoft.com/fwlink/?LinkId=193578) pour comprendre l’architecture, le flux de message et les principaux composants de BizTalk ESB Toolkit. Vous devez également installer et exécuter les exemples inclus dans BizTalk ESB Toolkit. Ceux-ci montrent les cas d'utilisation courants décrits dans la rubrique « Getting Started » et d'autres scénarios de messagerie. Cette approche vous aide à saisir rapidement le fonctionnement de BizTalk ESB Toolkit et l'utilité de ses fonctionnalités dans vos propres applications SOA.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide du Service BizTalk Enterprise](http://go.microsoft.com/fwlink/?LinkId=193577)   
 [Solution orientée services](../core/service-oriented-solution.md)   
 [Utilisation des Services Web](../core/using-web-services.md)