---
title: Infrastructure de gestion des exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b5aebc0-2467-4f48-a385-056507ed1c1e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4d4d19caebb667e822b15b937d9045a26493a57
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="exception-management-framework"></a>Infrastructure de gestion des exceptions
L’infrastructure de gestion d’Exception ESB fournit un mécanisme de génération des pannes orienté messages unifiée pour gérer toutes les exceptions qui peuvent se produire dans un environnement BizTalk Server. L’infrastructure de gestion d’Exception ESB peut recevoir des messages d’exception publiées via le Service de publication (Exception), en plus des messages à partir du mécanisme de BizTalk Server Échec de routage des messages.  
  
 Le framework fournit une API pour la création de messages d’erreur, de publication et de gestion des processus d’orchestration, la réplication de la fonctionnalité de routage du message ayant échoué BizTalk Server introduite avec BizTalk Server 2006. En outre, le framework fournit des fonctionnalités pour la normalisation de toutes les exceptions, l’enrichissement, application de suivi de l’analyse BAM (Business Activity) et la publication de la sortie finale à la base de données de gestion des exceptions pour l’affichage et la création de rapports dans l’architecture ESB Portail de gestion.  
  
 La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut les composants suivants qui prennent en charge l’infrastructure de gestion d’Exception ESB :  
  
-   **Composant de pipeline exception erreur processeur.** Ce composant est inclus dans le pipeline associé à l’Exception d’ESB rampe. Cette rampe s’abonne à tous les messages d’ESB généré l’erreur, en plus des exceptions générées par le message ayant échoué de BizTalk Server mécanisme de routage. Les itinéraires de composant messages à la base de données du portail de gestion ESB ESB exception Gestion d’erreur, ou il peut être configuré pour router vers un autre emplacement. Le composant de pipeline également enrichit tous les messages d’erreur et les exceptions avec les métadonnées et normalise les dans un format commun.  
  
-   **Composant de pipeline de suivi BAM.** Ce composant intercepte et enregistre les informations d’exception dans le sous-système BAM de BizTalk Server et est utilisé exclusivement par le pipeline Exception erreur dans le cadre de la gestion des exceptions. Fourni avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est un exemple qui illustre l’utilisation de BAM comme une fonctionnalité facultative de suivi pour des informations sur l’exception.  
  
 Pour plus d’informations sur l’infrastructure de gestion des exceptions, consultez [à l’aide de gestion des exceptions ESB](../esb-toolkit/using-esb-exception-management.md).