---
title: "Référence à Microsoft.BizTalk.DefaultPipelines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, PassThruTransmit
- pipelines, PassThruReceive
- pipelines
- PassThruTransmit pipelines
- XMLReceive pipelines
- pipelines, XMLTransmit
- Pipeline Designer
- pipelines, XMLReceive
- pipelines, about pipelines
- PassThruReceive pipelines
- XMLTransmit pipelines
- namespaces, Microsoft.BizTalk.DefaultPipelines namespace
- Microsoft.BizTalk.DefaultPipelines namespace
ms.assetid: a54f8813-9c6f-4afe-8c76-2db3fa478947
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ad7cad78e3e8606371a5fa49673297cf590ddbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="microsoftbiztalkdefaultpipelines-reference"></a>Référence à Microsoft.BizTalk.DefaultPipelines
Le **Microsoft.BizTalk.DefaultPipelines** espace de noms contient les pipelines suivants :  
  
-   XMLReceive  
  
-   PassThruReceive  
  
-   XMLTransmit  
  
-   PassThruTransmit  
  
 Un pipeline est un composant logiciel qui définit et relie une ou plusieurs étapes de traitement des messages reçus ou envoyés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ces étapes incluent des fonctions comme le codage ou le décodage, le désassemblage ou l'assemblage et le chiffrement ou le déchiffrement. Ces fonctions sont implémentées dans un ordre précis. Vous pouvez utiliser le Concepteur de pipeline pour créer des pipelines de réception et d'envoi.  
  
 Les pipelines par défaut inclus dans un projet BizTalk peuvent traiter tous les types de documents à l’aide de la **PassThruReceive** et **PassThruTransmit** pipelines.  
  
 Les listes suivantes présentent les composants des pipelines par défaut. Elles indiquent aussi l'ordre par défaut des composants de chaque pipeline. Vous pouvez ajouter et supprimer des composants selon les besoins.  
  
 Voici les composants par défaut du pipeline XMLReceive par défaut :  
  
-   Décrypteur  
  
-   Décodeur  
  
-   Désassembleur  
  
-   Valideur  
  
-   Résolution du tiers  
  
 Voici les composants par défaut du pipeline XMLTransmit par défaut :  
  
-   Assembleur  
  
-   Encodeur  
  
-   Encrypteur  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md)   
 [À propos des références de Namespace de BizTalk inclus dans les projets BizTalk](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)