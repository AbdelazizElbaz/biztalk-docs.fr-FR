---
title: "Gestion de l’Infrastructure dynamique BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- infrastructure, managing [BAM]
- managing [BAM], infrastructure
ms.assetid: af8a76b5-407a-484d-aff4-0d911f88313e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98cf9c3513a4fbd4a55a752233c9f0d704c59ecf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="managing-the-bam-dynamic-infrastructure"></a>Gestion de l'infrastructure dynamique de l'analyse BAM
Les fonctions BAM (Business Activity Monitoring) utilisent une infrastructure de traitement analytique en ligne (OLAP) et SQL générée dynamiquement. Les administrateurs ont recours à l'utilitaire de gestion de l'analyse BAM pour déployer le classeur ou le fichier XML de définition BAM qu'un analyste d'entreprise se charge ensuite de développer.  
  
 L'infrastructure dynamique de l'analyse BAM est composée des vues du classeur BAM, des déploiements de l'analyse BAM, des lots DTS (Data Transformation Services) BAM et des bases de données BAM. Pour plus d’informations sur l’infrastructure dynamique BAM, consultez [Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md).  
  
 BizTalk Server crée les bases de données BAM suivantes lorsque vous configurez BizTalk Server :  
  
-   Base de données d'importation principale BAM (BAMPrimaryImport)  
  
-   Base de données de schémas en étoile BAM (BAMStarSchema) (facultative)  
  
-   Base de données d'analyse BAM (BAMAnalysis) (facultative)  
  
-   Base de données des archives BAM (BAMArchive)  
  
 Pour plus d’informations sur les bases de données BAM, consultez [la gestion des bases de données BAM](../core/managing-bam-databases.md).  
  
 Les administrateurs accomplissent les tâches de gestion décrites dans cette section pour l'infrastructure de l'analyse BAM :  
  
-   Déployer et annuler le déploiement de définitions et de vues BAM  
  
-   Gérer l'accès utilisateur aux vues BAM  
  
-   Exécuter les lots DTS BAM  
  
-   Sauvegarder les bases de données BAM  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Gestion des définitions BAM](../core/managing-bam-definitions.md)
  
-   [Gestion de la sécurité BAM](../core/managing-bam-security.md)  
  
-   [Gestion des agrégations](../core/managing-aggregations.md) 
  
-   [Gestion des bases de données BAM](../core/managing-bam-databases.md)
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’analyse BAM](../core/managing-bam.md)