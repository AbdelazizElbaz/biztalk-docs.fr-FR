---
title: "Interrogation planifiée des données agrégées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, scheduled data
- queries [BAM], scheduled data
ms.assetid: fb785ec0-7862-4d83-bb6f-0ebd69a28ce6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30f59716ae94701aa793224500643563ece2681e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="querying-scheduled-aggregated-data"></a>Interrogation des données agrégées planifiées
Les données d'agrégation planifiées sont à la disposition des requêtes via des cubes OLAP créés dynamiquement dans la base de données d'analyse BAM.  
  
 Le nom de ce cube est le même que l'attribut Nom de l'élément Vue dans le fichier XML de définition BAM, qui est également le même que le nom de vue entré dans les Assistants Excel. L’analyse BAM actualise ce cube lorsque vous exécutez le package de Services DTS (Data Transformation) BAM_AN_\<*ViewName*>, où le \< *ViewName*> est le nom de la vue décrite vous avez utilisé dans les Assistants Excel.  
  
 Il est essentiel que vous teniez compte des points suivants quand vous interrogez des données agrégées planifiées :  
  
-   Ce cube est un cube virtuel contenant un instantané de l'activité commerciale pris au moment même où l'exécution du lot DTS a démarré. Il contient des agrégations pour les activités terminées ainsi que pour celles qui sont encore en cours. Vous pouvez utiliser la dimension de la progression pour filtrer ou regrouper les agrégations en fonction.  
  
-   Si vous vous intéressez jamais les activités en cours (par exemple, si elles se terminent très rapidement), vous pouvez interroger le cube réel correspondant \< *ViewName*> #Completed.  
  
-   Si vous avez également des agrégations en temps réel, planifiez le lot DTS afin d'actualiser le cube plus souvent que la fenêtre en ligne que vous définissez pour ces dernières Sinon, il y aura une fenêtre de temps pour laquelle vous n'aurez pas d'agrégations.  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation des données BAM](../core/querying-bam-data.md)