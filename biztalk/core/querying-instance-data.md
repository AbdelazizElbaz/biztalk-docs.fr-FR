---
title: "Interrogation des données de l’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, instance data
- queries [BAM], instance data
ms.assetid: ae4a8854-d5c2-4b36-a0ef-3f74e138306e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43310756cf12c0c2a48eb6716221afc5395ecb0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="querying-instance-data"></a>Interrogation de données d'instance
Les données relatives à des instances d'activité individuelles sont disponibles pour d'éventuelles requêtes dans une vue SQL créée dynamiquement dans la base de données d'importation principale BAM.  
  
 Le nom de cette vue est  
  
 **bam_\<**  *ViewName*  **\>_\<**  *Nomactivité*  **\>_View**  
  
 Où  
  
 **\<***ViewName*  **\>**  est l’attribut Name de l’élément d’affichage dans le fichier XML de définition BAM, qui est le même que le nom de vue entré dans les Assistants Microsoft Excel associés.  
  
 **\<***Nomactivité*  **\>**  est l’attribut de nom de l’élément d’activité dans le fichier XML de définition BAM, qui est le même que le nom d’activité entré dans les Assistants Excel.  
  
 Il est important que vous teniez compte des points suivants quand vous interrogez des données d'instance :  
  
-   Si vous envoyez des données d'activité à l'analyse BAM via la classe DirectEventStream, les données d'instance n'ont pas de latence, c'est-à-dire qu'elles apparaissent instantanément lorsque la transaction est validée dans l'application d'appel.  
  
-   Si les données d'activité sont envoyées à l'analyse BAM via la classe BufferedEventStream, les données d'instance s'afficheront à des fins de requête quelques secondes plus tard, en fonction de la charge du service Bus d'événements BAM et du serveur SQL Server qui héberge la base de données d'importation principale BAM.  
  
-   La structure réelle des tables sous-tendant cette vue est plus complexe afin de garantir que les données des activités actuelles ou récentes sont disponibles pour d'éventuelles requêtes. Les données correspondant à des activités terminées et qui n'ont plus lieu de faire l'objet de requêtes actives sont archivées ou éliminées sans déconnexion du système. Pour plus d’informations, consultez [stockage des données d’activité](../core/activity-data-storage.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage des données d’activité](../core/activity-data-storage.md)   
 [Interrogation des données BAM](../core/querying-bam-data.md)