---
title: "Procédure de cumul d’intégrité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c37644cd-7d3c-4e93-ad56-101043cfa685
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25dd7a2aea4d01a2fd84fe294f793cda833d1322
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-health-rolls-up"></a>Procédure de cumul d'intégrité
Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration classe ses artefacts qui le composent, des applications et le déploiement de BizTalk Server dans une structure de la couche où l’intégrité d’une couche peut dépendre de l’intégrité du niveau inférieur.  
  
-   Déploiement de BizTalk  
  
-   Application BizTalk  
  
## <a name="health-roll-up-for-biztalk-deployment"></a>Restauration de contrôle d’intégrité pour le déploiement de BizTalk  
 Le diagramme suivant montre comment cumule les États d’intégrité du déploiement de BizTalk Server dans ce pack d’administration.  
  
 ![Modèle de déploiement](../technical-guides/media/biztalk2010mp-deploymentmodel.gif "BizTalk2010MP-DeploymentModel")  
  
 Le tableau suivant décrit les composants affichés dans le diagramme de flux de travail de déploiement de BizTalk Server.  
  
|Nom| Description|Contrôle d’intégrité|  
|----------|-----------------|------------|  
|Groupe de déploiement BizTalk|Un groupe qui contient plusieurs serveurs d’exécution avec les composants, tels que le moteur d’exécution de règle.|L’intégrité de ce groupe dépend de la disponibilité de<br /><br /> -Rôle de l’analyse BAM<br />-Déploiement de l’hôte BizTalk<br />-Rôle d’exécution de BizTalk<br />-Règle de moteur|  
|Rôle de l’analyse BAM|Un serveur sur le BAM composant est installé.|Contrôle d’intégrité de ce varie selon le rôle d’exécution BAM et le portail BAM.|  
|Déploiement de l’hôte BizTalk|Une entité logique définissant les paramètres d’exécution ou les limites pour les divers artefacts de l’application à exécuter. Plusieurs instances de ce (instances de l’hôte) s’exécuter en tant que services NT sur les serveurs d’exécution différents.|L’intégrité de ce groupe dépend de la disponibilité des différentes instances de cet hôte.|  
|Rôle de l’exécution de BizTalk|Un serveur sur lequel le moment de l’exécution de BizTalk est installé.|L’intégrité de ce groupe dépend de la disponibilité de<br /><br /> : Service d’authentification unique<br />-Gestion de base de données<br />-Base de données MessageBox<br />-Base de données SSO<br />-Base de données de suivi|  
|Rôle de moteur de règle|Un serveur qui a installé du moteur de règles.|L’intégrité de ce groupe dépend de la disponibilité de Service de moteur de règles et de la base de données du moteur de règles<br /><br /> -Service de moteur de règles<br />-Base de données de moteur de règles|  
|Rôle d’exécution BAM|Un serveur sur le BAM composant d’exécution est installé.|L’intégrité de ce dépend de la disponibilité de<br /><br /> : Base de données importation principale BAM<br />-Base de données des archives BAM<br />-L’analyse BAM<br />: Alertes BAM|  
|Portail BAM|Un serveur Web qui a des applications de portail BAM installé et configuré.|L’intégrité de ce dépend de la disponibilité de l’application du portail BAM.|  
|Instance de l'hôte|Un service Windows NT est configuré pour s’exécuter sur le serveur d’exécution BizTalk.|L’intégrité de ce dépend de l’état du service Windows NT.|  
|Service SSO|Un service Windows NT pour l’authentification unique.|L’intégrité de ce dépend de l’état du service d’authentification unique.|  
|Base de données de gestion|Un serveur SQL qui contient une ou plusieurs bases de données BizTalk.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Base de données MessageBox|Un serveur SQL qui contient une ou plusieurs bases de données MessageBox de BizTalk.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Service de moteur de règles|Service de moteur de règles qui permet de traiter les règles de BizTalk.|L’intégrité de ce dépend de la disponibilité du Service de moteur de règles.|  
|Base de données du moteur de règles|Un serveur SQL qui contient une ou plusieurs bases de données du moteur de règles BizTalk.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Base de données d’importation principale BAM|SQL Server qui contient les bases de données BAM.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Base de données des archives BAM|Une base de données SQL Server qui contient les données archivées.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Analyse BAM|Contient les données d’analyse BAM et hors connexion.|L’intégrité de ce dépend de la disponibilité des données d’analyse BAM.|  
|Alertes BAM|Un service de notification SQL.|L’intégrité de ce dépend de l’état du service de notification.|  
|Service d’alerte BAM|Un service de notification SQL.|L’intégrité de ce dépend de l’état du service de notification.|  
|Base de données Analyse BAM|Une base de données SQL Server qui contient les données d’analyse BAM et hors connexion.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Base de données de schémas en étoile BAM|Contient le tableau intermédiaire et les tables de mesures et de dimensions.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Base de données de suivi|Une base de données SQL Server qui stocke les données suivies par le moteur de suivis BizTalk Server d’analyse du fonctionnement.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
|Base de données SSO|SQL Server qui héberge la base de données SSO.|L’intégrité de ce dépend de la disponibilité de la disponibilité de base de données SQL Server.|  
  
## <a name="health-roll-up-for-biztalk-application"></a>Rapport de fonctionnement pour l’Application BizTalk  
 Le diagramme suivant montre comment cumule les États d’intégrité de l’application BizTalk et ses artefacts constitutifs de ce pack d’administration.  
  
 ![Modèle d’application](../technical-guides/media/biztalkserver2010mp-applicationmodel.gif "BizTalkServer2010MP-ApplicationModel")  
  
 Le tableau suivant décrit les composants affichés dans le diagramme de flux de travail d’application BizTalk.  
  
|Nom| Description|Contrôle d’intégrité|  
|----------|-----------------|------------|  
|Groupe BizTalk|Un groupe qui contient des artefacts de l’application. Tous ces artefacts sont stockés dans une base de données centralisée qui est nommé en tant que base de données de configuration. Ces artefacts peuvent être détectés à partir des ordinateurs d’exécution.|L’intégrité de ce groupe dépend de la disponibilité de l’hôte BizTalk et les applications BizTalk.|  
|Hôte|Une entité logique définissant les paramètres d’exécution ou les limites pour les divers artefacts de l’application à exécuter. Plusieurs instances de ce (instances de l’hôte) s’exécuter en tant que services NT sur les serveurs d’exécution différents.|L’intégrité de ce groupe dépend de la disponibilité d’une autre instance de cet hôte.|  
|Application|Groupe d’artefacts de l’application BizTalk tels que les Orchestrations, schémas, mappages et pipelines. Composants de messagerie tels que les ports d’envoi, emplacements de réception et ports de réception. Les instances de ces artefacts sont exécutés dans l’instance de l’hôte lorsqu’un message approprié est reçu par BizTalk Server.|L’intégrité de ce dépend de la<br /><br /> -État configuration de port de réception<br />-État Runtime de port de réception<br />-État configuration du port d’envoi<br />-Contrôle d’intégrité de l’orchestration<br />-État d’exécution d’orchestration|  
|Port de réception|Un artefact BizTalk qui s’exécute dans une instance d’hôte. Il s’exécute lorsque le serveur BizTalk Server reçoit un message. Réception port contient un ou plusieurs emplacement de réception.|L’intégrité de ce dépend de l’état de configuration et l’état d’exécution de port de réception.|  
|Emplacement de réception|Un artefact BizTalk qui reçoit le message à partir d’un système externe. Il utilise une carte avec son point de terminaison associé pour recevoir un message.|L’intégrité de ce dépend de l’état de la configuration et l’état d’exécution de l’emplacement de réception.|  
|Port d’envoi|Envoie le message traité à un système externe.|L’intégrité de ce dépend de l’état de la configuration et l’état d’exécution d’un port d’envoi.|  
|Orchestration|Reçoit un message à partir de port de réception et traite le message. Orchestration est semblable au workflow.|L’intégrité de ce dépend de l’état de statut et d’exécution de configuration d’orchestration.|  
|Groupe de ports d'envoi|Un groupe logique de ports d’envoi qui reçoit le message à partir de la boîte de message BizTalk et l’envoie aux systèmes externes.|L’intégrité de ce groupe dépend de l’intégrité des ports d’envoi de ce groupe.|