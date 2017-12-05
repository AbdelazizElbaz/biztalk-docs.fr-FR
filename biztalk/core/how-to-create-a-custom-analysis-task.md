---
title: "Comment créer une tâche d’analyse personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, DTS tasks
- DTS tasks
- DTS packages, tasks
- BAM, processing
ms.assetid: 6046c113-fb58-4e72-8f48-5470e52be9a8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3566e40deaa05886ead701e1871634cf6fb94e2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-a-custom-analysis-task"></a>Création d'une tâche d'analyse personnalisée
Le moyen le plus simple de créer une tâche DTS personnalisée pour traiter des données BAM consiste à démarrer à partir du lot généré automatiquement par BAM et à remplacer l'ensemble du processus existant.  
  
### <a name="to-create-a-custom-dts-task"></a>Pour créer une tâche DTS personnalisée  
  
1.  Créez une définition BAM nécessitant un cube OLAP. Utilisez par exemple les Assistants Excel et gardez un rapport de tableau croisé dynamique sous la forme d'une vue non-RTA.  
  
2.  Ouvrez le lot DTS de traitement des cubes créé par BAM. BAM crée un tel package pour chaque vue, intitulé BAM_AN_\<*nom de la vue*\>.  
  
3.  Ouvrez le lot dans le Concepteur DTS, puis supprimez toutes les étapes à l'exception des deux premières et de la dernière. Peut-être voudrez-vous aussi conserver la connexion avec la base de données d'importation principale.  
  
4.  Modifiez les propriétés de la première tâche ActiveX®. Supprimez toutes les lignes contenant DTSGlobalVariables.Parent.Steps car elles font référence aux étapes supprimées. Le script commence ainsi :  
  
    ```  
    serverName = "<your server here>"   
    databaseName = "<your analysis database here>"  
    cubeName = "<your cube name here>"  
    ```  
  
    > [!NOTE]
    >  La tâche Commencer l'analyse de données, qui est la deuxième du lot, est très importante car elle fournit à votre lot :  
    >   
    >  -   Une fenêtre interactive pour un traitement incrémentiel des activités terminées (vue SQL dynamique intitulée bam_(BamView)_View(Activity)_CompletedInstancesWindow  
    > -   Un instantané des activités qui sont en cours, une table nommée bam\_(BamView) _View (Activity) _ActiveInstancesSnapshot.  
  
5.  Vous obtenez la vue et la table grâce à une courte transaction, au cours de laquelle vous n'insérez aucune donnée, de façon à ce que les données représentent un véritable instantané de la base de données d'importation principale. Effectuez une ou plusieurs étapes pour réaliser la véritable transformation des données en fonction de la vue et de la table. Si l'objectif de votre tâche d'analyse est autre que le remplissage d'un cube OLAP, veillez à conserver un horodatage du moment où la tâche est effectuée pour la dernière fois et à remplacer la première tâche ActiveX par le code qui associe cet horodatage à la variable globale CompletedCubeLastProcessTime. La deuxième tâche utilise cette variable pour garantir qu'aucune donnée n'est perdue, ni traitée deux fois en cas d'incident et de redémarrage du lot DTS.  
  
6.  Vous devez enfin appeler la dernière tâche, intitulée Terminer l'analyse de données. Cette tâche libère les activités traitées et terminées de façon à ce qu'elles soient archivées et supprimées de l'importation principale dès qu'elles se trouvent en dehors de la fenêtre en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Business Activity Monitoring](../core/using-business-activity-monitoring.md)