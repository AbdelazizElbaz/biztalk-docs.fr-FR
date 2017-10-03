---
title: "Déploiement du Service de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, service solution tutorial
- deploying, tutorials
- service solution tutorial, deploying
- service solution tutorial, background information
- tutorials, deploying
ms.assetid: 88d4d28d-9031-4fb8-ab62-04ee27949673
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7246635c4e0d55fd424fd0052eee91e118c8cb17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-the-service-oriented-solution"></a>Déploiement du Service de la Solution orientée services
L'architecture orientée services (SOA) est une approche de la génération de systèmes distribués. La solution orientée services montre comment plusieurs systèmes principaux utilisant différents protocoles peuvent être agrégés en un service unique que les clients peuvent consommer. Cette solution intègre des services sur la base d'une approche garantissant des caractéristiques de livraison et de performances.  
  
 La solution orientée services est modélisée selon un scénario d'accord de niveau de service où BizTalk Server et les serveurs d'applications métier (LOB) qui y sont connectés ont trois secondes pour répondre avec une demande de service. L'une de ces trois secondes peut être utilisée par BizTalk Server.  
  
 Les rubriques de cette section décrivent l'installation et le test de la solution orientée services sur un seul ordinateur et plusieurs serveurs de production.  
  
> [!NOTE]
>  Il existe trois versions de la solution orientée services : adaptateur, inline et stub. Pour plus d’informations sur les différences entre les trois versions de la solution orientée services, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).  
  
 **Guide de lecteur**  
  
 Ce document suppose que vous connaissez BizTalk Server, Windows Server et Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Il suppose également que vous comprenez les concepts de base sur l’intégration d’applications d’entreprise et les services Web. En outre, il est recommandé d'être familiarisé avec la création d'applications sous [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], la création de projets, la définition de références et l'utilisation du mode de débogage pour déboguer et tester votre solution. Pour plus d’informations sur les compétences et connaissances préalables pour les professionnels de l’informatique et aux développeurs, consultez [condition préalable compétences et connaissances](../core/prerequisite-skills-and-knowledge5.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Installation d’ordinateur de développeur pour le Service orienté solutions](../core/developer-machine-setup-for-the-service-oriented-solution.md)