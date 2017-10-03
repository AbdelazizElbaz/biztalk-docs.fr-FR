---
title: "Comment définir des agrégations BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, BAM
- aggregations [BAM], creating
- Excel add-in [BAM], security
- Excel add-in [BAM], creating aggregations
- managing [BAM], creating aggregations
ms.assetid: a5ef3a15-b1de-4099-8e94-64af4b5ec746
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef1b5b377611eb8e28088cb2d0c2f2ed6f829de8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-bam-aggregations"></a>Définition d'agrégations BAM
L'analyse BAM prend en charge deux types d'agrégation de données :  
  
-   Les agrégations de traitement analytique en ligne (OLAP)  
  
-   Les agrégations RTA  
  
 L'analyse BAM utilise Microsoft SQL Analysis Service pour implémenter les agrégations OLAP.  
  
 Vous devez configurer les déclencheurs sur la base de données d'importation principale BAM qui définit les agrégations RTA.  
  
### <a name="to-define-olap-aggregations"></a>Pour définir des agrégations OLAP  
  
1.  Dans le classeur Excel BAM, créez une vue, ajoutez au moins une dimension et une mesure au rapport de tableau croisé dynamique, désactivez le bouton RTA dans la barre d'outils, et enregistrez le classeur.  
  
    -   Pour plus d’informations sur l’ouverture du classeur BAM, la création d’une vue et ajout de dimensions et mesures, consultez [définition d’une vue BAM](../core/defining-a-bam-view.md).  
  
2.  Déployez le classeur.  
  
    -   Pour déployer le classeur, suivez les instructions de [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).  
  
3.  Un développeur de solutions utilise la **DirectEventStream** classe pour importer des événements dans la base de données d’importation principale BAM.  
  
    -   Pour plus d’informations sur la **DirectEventStream** de classe, consultez [classe DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).  
  
4.  Exécutez le lot DTS (Data Transformation Services) de cube de mise à jour.  
  
    -   Pour plus d’informations sur l’exécution du lot DTS de mise à jour de cube, consultez [lots DTS BAM](../core/bam-dts-packages.md).  
  
5.  Ouvrez la copie de données actives la plus récente du classeur pour afficher les agrégations OLAP.  
  
    > [!IMPORTANT]
    >  Pour des raisons de sécurité, l'analyse BAM ne supprime pas les copies de données actives existantes du classeur. Au lieu de cela, elle incrémente le nom de fichier de la copie de données actives.  
  
### <a name="to-define-the-rta"></a>Pour définir l'agrégation RTA  
  
1.  Dans le classeur Excel BAM, créez une vue, ajoutez au moins une dimension et une mesure au rapport de tableau croisé dynamique, sélectionnez le bouton RTA dans la barre d'outils, et enregistrez le classeur.  
  
    > [!WARNING]
    >  Ne définissez pas plusieurs RTA utilisant une même activité BAM. Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.  
  
    -   Pour plus d’informations sur l’ouverture du classeur BAM, création d’une vue et ajout de dimensions et mesures, consultez « Définition d’une vue activité d’entreprise » et « Définition d’agrégations » dans le *Guide de l’utilisateur des informations travailleurs*.  
  
2.  Déployez le classeur.  
  
    -   Pour déployer le classeur, suivez les instructions de [comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md).  
  
3.  Un développeur de solutions utilise la **DirectEventStream** classe pour importer des événements dans la base de données d’importation principale BAM.  

  
4.  Ouvrez la copie de données actives la plus récente du classeur pour afficher les agrégations RTA.  
  
    > [!IMPORTANT]
    >  Pour des raisons de sécurité, l'analyse BAM ne supprime pas les copies de données actives existantes du classeur. Au lieu de cela, elle incrémente le nom de fichier de la copie de données actives.  
  
## <a name="see-also"></a>Voir aussi  
 [Lots DTS BAM](../core/bam-dts-packages.md)   
 [Comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md)   
 [Mise à jour des propriétés de chaîne de connexion RTA et OLAP](../core/updating-olap-and-rta-connection-string-properties.md)   
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)