---
title: Infrastructure dynamique BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- infrastructure, BAM
- BAM, infrastructure
ms.assetid: 88f39438-3213-4f0d-8b8d-e6426c266138
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3660eeb6f85fb21ff78b7b833b21adbb3af87385
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-dynamic-infrastructure"></a>Infrastructure dynamique de l'analyse BAM
L’infrastructure BAM se compose de tables SQL Server, des vues BAM, des procédures stockées et des packages de Services DTS (Data Transformation) dans les bases de données BAM (importation principale, l’archivage, schémas en étoile et Analysis) comme configuré et géré via incrémentielle déploiements de définitions BAM. L’infrastructure est où, au moment de l’exécution sont mis en corrélation, agrégées et événements accessibles pour l’interrogation par les utilisateurs.  
  
 Cette section décrit quelques-uns de ces processus d'infrastructure. Par exemple, une fois que vous avez extrait les données d'intérêt à partir de vos applications (la définition BAM), vous pouvez les stocker afin de les rendre interrogeables. De plus, vous pouvez conserver certaines agrégations pré-créées des données pour accélérer l'agrégation des requêtes.  
  
 Généralement, vous obtiendrez une telle fonctionnalité en fournissant un effort de développement important pour implémenter un Data Warehouse. Toutefois, dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'analyse BAM simplifie considérablement ce processus en générant automatiquement les infrastructures SQL et OLAP sur la base de vos définitions d'activité et d'affichage.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Qu’est une définition BAM ?](../core/what-is-a-bam-definition.md)  
  
-   [Qu’est un schéma de définition BAM ?](../core/what-is-a-bam-definition-schema.md)  
  
-   [Stockage des données d’activité](../core/activity-data-storage.md)  
  
-   [Qu’est une agrégation ?](../core/what-is-an-aggregation.md)  
  
-   [Interrogation des données BAM](../core/querying-bam-data.md)  
  
-   [Limitations de l’Infrastructure BAM](../core/bam-infrastructure-limitations.md)  
  
-   [Comment définir des alertes de Dimension numérique de Out-of-Range dans les Installations Non anglaises](../core/define-out-of-range-numeric-dimension-alerts-in-non-english-installations--bam.md)