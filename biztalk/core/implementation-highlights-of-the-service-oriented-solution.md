---
title: "Caractéristiques de l’implémentation du Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, performance
- performance, service solutions
- service solution tutorial, implementing
ms.assetid: 3dbd8dfd-45b7-4290-ba07-b0c5e6264629
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c593c24c72e5666525001e6a52e2b0bf6eac2de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementation-highlights-of-the-service-oriented-solution"></a>Caractéristiques de l’implémentation du Service orienté solutions
Une solution résout un problème particulier dans un contexte spécifique. La solution orientée services n'est pas une exception car elle est spécifique à Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et au scénario. Pour plus d’informations sur le scénario Woodgrove Bank, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).  
  
 Dans le cadre du développement du scénario, plusieurs éléments ont été identifiés comme étant des goulots d'étranglement pour la réduction des délais de réponse à un niveau acceptable. L'envoi des messages aux systèmes principaux à l'aide des adaptateurs entraîne une latence importante dans l'obtention des réponses. En général, les adaptateurs eux-mêmes présentent une faible latence. L'architecture distribuée de BizTalk les oblige toutefois à communiquer avec les instances d'hôte de l'orchestration via la base de données MessageBox. Cela entraîne des allers-retours vers la base de données et affecte les délais de latence. Pour cette raison, la version Inline de la solution (version la plus rapide) développe les fonctionnalités d'adaptateur dans l'orchestration elle-même et appelle directement les systèmes principaux. Avec trois systèmes principaux, il peut y avoir trois mécanismes différents pour communiquer avec les systèmes principaux.  
  
 La récupération des données de configuration de l'authentification unique (SSO) de l'entreprise constituait également un problème pour les performances. Pour conserver la simplicité et l'universalité de l'authentification unique tout en accélérant le délai de récupération, la solution utilise un cache local pour les valeurs de configuration. L'utilisation de l'authentification unique facilite la gestion des données de configuration. L'ajout d'instances d'hôte pour répondre aux impératifs de latence et de performance n'implique pas la modification des paramètres sur le serveur exécutant l'instance de l'hôte.  
  
 L'appel direct des pipelines depuis le code constitue un autre élément inhabituel de la solution. Ceci permet de réutiliser les composants de pipeline personnalisés.  
  
 Enfin, certains paramètres de BizTalk Server peuvent être modifiés pour optimiser la vitesse de la solution.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Appel de Back-end incorporation (inlining)](../core/inlining-back-end-invocation.md)  
  
-   [À l’aide de l’authentification unique efficacement dans le Service de la Solution orientée services](../core/using-sso-efficiently-in-the-service-oriented-solution.md)  
  
-   [À l’aide de Pipelines à partir du Service de la Solution orientée services](../core/using-pipelines-from-the-service-oriented-solution.md)  
  
-   [Le Service de paramétrage de la Solution orientée services](../core/tuning-the-service-oriented-solution.md)  
  
-   [Dissocation du Type de Transport et traitement](../core/decoupling-transport-type-and-processing.md)