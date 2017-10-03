---
title: "Exemple d’Architectures pour les petites &amp; moyennes entreprises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: architecture, examples
ms.assetid: fc8c2fdd-bcb1-481c-b351-03092dd48540
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa7911b7b2da942d559f2c85ad32e896c79d174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architectures-for-small-amp-medium-sized-companies"></a>Exemple d’Architectures pour les petites &amp; moyennes entreprises
Cette section inclut un exemple d'architecture pour le déploiement de Microsoft BizTalk Server qui permet de protéger les ressources d'une entreprise petite ou moyenne (PME). Si ce type d'architecture favorise la sécurité et la séparation des services afin de réduire l'impact des attaques, il implique des ressources matérielles, logicielles et humaine que seules les grandes entreprises ont à disposition.  
  
 Ceci ne doit pas empêcher les PME (et les grandes entreprises dotées de petits déploiements BizTalk Server) de se préoccuper de la protection de leurs environnements. Les modalités envisagées ou mises en œuvre par les entreprises pour le déploiement de leurs solutions [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] nous ont permis de définir un modèle d'architecture adapté aux PME, combinant les ressources disponibles et une sécurité optimisée. Vous pouvez utiliser les informations de cette section pour planifier votre propre déploiement. L'évaluation des besoins et ressources de votre entreprise vous conduira peut-être à adopter une autre architecture pour votre déploiement BizTalk Server.  
  
 Pour vous aider à visualiser votre architecture, cette section inclut des exemples d'architecture basés sur divers adaptateurs que vous pouvez utiliser dans votre environnement. Les figures indiquent les composants de la topologie indépendants de l'adaptateur utilisé dans votre environnement BizTalk Server, et ceux qui en dépendent.  
  
 Les scénarios d'utilisation basés sur certains des adaptateurs que vous pouvez utiliser avec BizTalk Server sont également décrits. Pour vous aider à planifier et concevoir votre propre architecture, nous avons inclus une analyse du modèle des menaces de cet exemple d'architecture. Celle-ci décrit de façon détaillée les risques de sécurité potentiels qui peuvent affecter votre entreprise,selon les adaptateurs que vous utilisez pour communiquer avec vos partenaires.  
  
 Si les informations de cette section vous aident à créer un déploiement sécurisé de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez également envisager de sécuriser la communication entre les serveurs de votre environnement pour en accroître la sécurité.  
  
> [!IMPORTANT]
>  Cette section part du principe que vous n'utilisez pas l'analyse BAM (Business Activity Monitoring). Cette fonctionnalité implique d'autre considérations de sécurité Ce sujet est abordé dans [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
> [!NOTE]
>  Pour plus d’informations sur les adaptateurs non décrits dans ce document, consultez le centre de développement BizTalk Server ([http://go.microsoft.com/fwlink/?LinkId=46420](http://go.microsoft.com/fwlink/?LinkId=46420).)  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md)  
  
-   [Exemple d’Architecture : Adaptateurs HTTP et SOAP](../core/sample-architecture-http-and-soap-adapters.md)  
  
-   [Exemple d’Architecture : Message Queuing de BizTalk](../core/sample-architecture-biztalk-message-queuing.md)  
  
-   [Exemple d’Architecture : L’adaptateur FTP](../core/sample-architecture-ftp-adapter.md)  
  
-   [Exemple d’Architecture : Adaptateur de fichier](../core/sample-architecture-file-adapter.md)