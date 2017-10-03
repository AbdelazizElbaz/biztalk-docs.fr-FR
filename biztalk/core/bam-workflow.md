---
title: Flux de travail BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring business activities [BAM], collecting business data
- XML files
- orchestrations, XML files
- business activities, business data
- infrastructure, managing [BAM]
- business activities, monitoring
- monitoring business activities [BAM], monitoring flow
- managing [BAM], infrastructure
- monitoring business activities [BAM], viewing business data
- managing [orchestrations], mapping XML to orchestrations
ms.assetid: 8b4ae145-3e16-4bb8-bfba-09b9f666218d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19356d6191963ec441f0b85c0e987c8515dcf1f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-workflow"></a>Workflow BAM
L'illustration suivante représente les quatre rôles d'utilisateur qui interviennent dans le cadre de l'analyse BAM, ainsi que les outils qu'ils utilisent.  
  
 ![](../core/media/ebiz-tut-bamworkflow.gif "ebiz_tut_bamworkflow")  
Rôles BAM  
  
 Les étapes ci-après constituent une présentation détaillée du workflow de l'utilisation de l'analyse BAM.  
  
## <a name="specifying-the-business-data-to-collect"></a>Spécification des données de l'entreprise à collecter  
 Les données de l'entreprise sont collectées de la manière suivante :  
  
-   L'analyste d'entreprise utilise l'Assistant Activité BAM pour spécifier les données à collecter pour tous les utilisateurs des activités.  
  
-   L'analyste d'entreprise utilise l'Assistant Vue BAM pour définir la vue de chaque catégorie d'utilisateur des activités.  
  
-   Ensuite, il enregistre les activités et les vues dans un classeur Microsoft® Excel appelé le Classeur de définitions BAM.  
  
-   L'analyste d'entreprise exporte le Classeur de définitions BAM au format XML.  
  
-   L'administrateur système et le développeur utilisent le fichier XML dans le cadre de leurs rôles.  
  
-   Les instructions relatives à l’aide du classeur de définition BAM se trouvent dans [définition des activités d’entreprise et les vues dans Excel](../core/defining-business-activities-and-views-in-excel.md).  
  
## <a name="managing-the-bam-infrastructure"></a>Gestion de l'infrastructure BAM  
 Une fois que l'analyste d'entreprise a défini la vue BAM voulue, l'administrateur système utilise l'utilitaire de gestion de l'analyse BAM (BM.EXE), un outil de ligne de commande, pour déployer l'infrastructure BAM à partir du Classeur de définitions BAM ou du fichier XML exporté depuis celui-ci.  
  
 L'utilitaire de gestion de l'analyse BAM crée de manière dynamique les tables, les déclencheurs, les packages DTS et les cubes OLAP nécessaires à la prise en charge de la vue BAM.  
  
 Chaque fois que l'analyste d'entreprise définit une vue BAM différentes ou modifie une vue BAM, l'administrateur système doit redéployer le Classeur de définitions BAM.  
  
## <a name="mapping-the-xml-to-an-orchestration"></a>Mappage du fichier XML vers une orchestration  
 Après que l'analyste d'entreprise a exporté le Classeur de définitions BAM au format XML, le développeur importe le fichier XML dans l'Éditeur de modèle de suivi. Le développeur implémente les demandes d'information de l'analyste d'entreprise en mappant le fichier XML vers une orchestration.  
  
 À l'aide de l'Éditeur de modèle de suivi, le développeur exécute la procédure suivante pour mapper le fichier XML vers une orchestration :  
  
-   Il charge l'assembly déployé qui est stocké dans la base de données de gestion BizTalk (également appelée « base de données de configuration »). L'assembly déployé contient une ou plusieurs orchestrations correspondant aux exigences spécifiées par l'analyste d'entreprise à l'étape 1 ci-dessus.  
  
-   Il définit les données à extraire d'une orchestration. Pour ce faire, il fait glisser des éléments issus des schémas des messages et des formes Orchestration dans les dossiers d'étapes majeures commerciales (événement) et d'éléments de données appropriés.  
  
-   Lorsqu'il a terminé, il enregistre le profil en tant que fichier de suivi BizTalk® Server (.btt) dans une base de données de stockage telle que Visual SourceSafe.  
  
 Le développeur déploie le fichier .btt dans une base de données de test et vérifie le résultat par des tests d'intégration.  
  
## <a name="deploying-the-tracking-profile"></a>Déploiement du modèle de suivi  
 À l'aide de l'Éditeur de modèle de suivi, l'administrateur système déploie le profil vers une ou plusieurs bases de données de gestion BizTalk.  
  
 Chaque fois que le développeur modifie l'orchestration ou que les exigences des utilisateurs des activités changent et qu'ils souhaitent effectuer le suivi d'un plus grand nombre de données, l'administrateur système doit redéployer le modèle de suivi à l'aide de l'utilitaire de ligne de commande bttdeploy.exe.  
  
## <a name="viewing-the-business-data"></a>Affichage des données de l'entreprise  
 L'utilisateur des activités fait appel au classeur _LiveData généré par l'utilitaire BM.exe. Chaque fois que l'utilisateur des activités ouvre ce classeur, il reçoit une nouvelle version à jour des données collectées pour surveiller un aspect spécifique du processus d'entreprise.  
  
-   Pour afficher les données qui sont définies comme une agrégation en temps réel, l’utilisateur doit simplement cliquer sur **Actualiser** dans le classeur pour afficher les données.  
  
-   Si les données d'agrégation ne sont pas en temps réel, l'utilisateur des activités affiche un instantané des données de l'entreprise pris au moment de l'exécution du lot DTS planifié.  
  
-   Si votre organisation a défini des exigences concernant la collaboration, l'utilisateur des activités peut accéder aux données actives à partir du site Web BAS.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des vues et des activités d’entreprise dans Excel](../core/defining-business-activities-and-views-in-excel.md)   
 [Analyse des activités d’entreprise avec BAM](../core/monitoring-business-activities-with-bam.md)