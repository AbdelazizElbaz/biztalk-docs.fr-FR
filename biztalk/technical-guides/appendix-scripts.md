---
title: "Annexe : Scripts | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6394321-13c9-4b1d-b529-eba3d53b33c4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12df00876f6b2da9ebb98631016bd42947b4a40a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-scripts"></a>Annexe : Scripts
Les scripts suivants sont inclus dans ce pack d’administration.  
  
|Script|Fonction|  
|------------|-------------|  
|Microsoft.BizTalk.Server.2013.ArtifactsDiscovery.vbs|Ce script détecte des artefacts de l’application en fonction de $Config option de paramètre de $. Incluent des options<br /><br /> -Tous les ports d’envoi, groupes de ports d’envoi dans une application, les relations d’hébergements à une application et les relations de « envoyer le groupe de ports contient le port d’envoi ».<br />-Toutes les orchestrations dans une application, leurs relations d’hébergements pour l’application.<br />-Tous les ports de réception, emplacements de réception dans une application, et leur relation d’hébergement ' à une application et « port de réception contient l’emplacement de réception ' relations.|  
|Microsoft.BizTalk.Server.2013.ApplicationDiscovery.vbs|Ce script détecte les éléments suivants :<br /><br /> -Tous les applications dans un groupe et les relations de « groupe les applications hôtes ».<br />-Tous les ordinateurs hôtes dans un groupe et les relations « héberge un hôte groupe ».|  
|Microsoft.BizTalk.Server.2013.BAMAnalysisDiscovery.vbs|Ce script détecte l’analyse BAM et alertes de composants sur un ordinateur sur lequel le composant d’exécution BAM est détecté.|  
|Microsoft.BizTalk.Server.2013.BAMPortalDiscovery.vbs|Ce script détecte le portail BAM configuré sur un ordinateur qui exécute IIS. Il détecte également les rôle BAM et la relation contenant-contenu du portail BAM qu’elle contient.|  
|Microsoft.BizTalk.Server.2013.BAMRuntimeDiscovery.vbs|Ce script détecte le composant d’exécution BAM sur un ordinateur passé comme paramètre $Config/NomOrdinateur$. Si le nom de l’ordinateur n’est pas passé BAM sur un ordinateur d’exécution avec l’ID de serveur le plus bas dans la base de données de gestion qu’il détecte. Il détecte également les rôle BAM et la relation contenant-contenu d’exécution BAM qu’elle contient.|  
|Microsoft.BizTalk.Server.2013.BizTalkApplicationServiceDiscovery.vbs|Ce script détecte tous les services d’application BizTalk sur un ordinateur, ainsi que ses relations d’hébergements avec le rôle d’exécution.|  
|Microsoft.BizTalk.Server.2013.BizTalkGroupDiscovery.vbs|Ce script détecte le groupe BizTalk sur un ordinateur passé comme paramètre $Config/NomOrdinateur$. Si le nom de l’ordinateur n’est pas passé elle découvre des groupe sur un ordinateur d’exécution avec l’ID de serveur le plus bas dans la base de données de gestion.|  
|Microsoft.BizTalk.Server.2013.BizTalkRoleDiscovery.vbs|Ce script détecte les rôles de serveur BizTalk dans un ordinateur spécifié selon le paramètre. $Config option$. Vous pouvez choisir les options suivantes :<br /><br /> Rôle d’exécution BizTalk, déploiement d’un groupe BizTalk et relation contenant-contenu du runtime dans le déploiement d’un groupe.<br />-Rôle de moteur de règles BizTalk, déploiement d’un groupe BizTalk et relation contenant-contenu de moteur de règles dans un déploiement de groupe. Rôle de l’analyse BAM est toujours détecté avec une des options et sa relation contenant-contenu dans le déploiement d’un groupe.|  
|BizTalkAnalysisDatabaseMonitor.vbs|Ce script génère des données d’analyse de la disponibilité de base de données de l’analyse SQL en fonction de la connectivité. Les États d’analyse peuvent être une réussite ou erreur.|  
|BizTalkArtifactConfigurationMonitor.vbs|Ce script génère des données d’analyse de configuration de l’artefact application BizTalk. Chaque artefact peut avoir l’un des trois analyse succès d’états, avertissement et erreur.|  
|BizTalkArtifactSuspendedInstancesMonitor.vbs|Ce script génère des données d’analyse de l’état d’exécution BizTalk application artefact en fonction du nombre d’instances suspendues par l’artefact. Chaque artefact peut avoir l’un des trois analyse succès d’états, avertissement et erreur.|  
|BizTalkBAMPortalMonitor.vbs|Ce script génère des données d’analyse de disponibilité du portail BAM. Les États d’analyse peuvent être une réussite ou erreur.|  
|BizTalkHostConfigurationMonitor.vbs|Ce script génère des données d’analyse de l’hôte BizTalk en fonction de la disponibilité de toutes ses instances d’hôte (BTSNTSvc.exe). États de l’analyse peut être un succès (en cours d’exécution > = limite de réussite), avertissements (en cours d’exécution > = la limite d’avertissement et en cours d’exécution < limite de réussite) ou une erreur.|  
|BizTalkDatabaseMonitor.vbs|Ce script génère des données d’analyse de la disponibilité d’une base de données SQL en fonction de la connectivité. Les États d’analyse peuvent être une réussite ou erreur.|  
|BizTalkMultipleDatabaseMonitor.vbs|Ce script génère des données d’analyse de la disponibilité d’un groupe de bases de données SQL comme une entité unique, en fonction de la connectivité. États de l’analyse peuvent être une erreur (base de données primaire non disponible), avertissement (certaines non primaire bases de données non disponibles) ou réussite (toutes les bases de données disponibles).|  
|BizTalkHostProbeAction.vbs|Ce script génère des données de diagnostic pour l’hôte BizTalk en fonction de la disponibilité de toutes ses instances d’hôte (BTSNTSvc.exe). Pour les erreurs et les États d’avertissement, il montre instance d’hôte qui ne sont pas en cours d’exécution.|  
|Microsoft.BizTalk.Server.2013.HostAction.vbs|Ce script est utilisé pour démarrer/arrêter un hôte BizTalk.|  
|Microsoft.BizTalk.Server.2013.OrchestrationAction.vbs|Ce script est utilisé pour démarrer/arrêter une orchestration (objet d’application BizTalk).|  
|Microsoft.BizTalk.Server.2013.EnableReceiveLocation.vbs|Ce script est utilisé pour activer ou désactiver un emplacement de réception (objet d’application BizTalk).|  
|Microsoft.BizTalk.Server.2013.SendPortAction.vbs|Ce script est utilisé pour démarrer/arrêter un Port d’envoi (objet d’application BizTalk).|  
|Microsoft.BizTalk.Server.2013.SendPortGroupAction.vbs|Ce script est utilisé pour démarrer/arrêter un groupe de ports d’envoi (objet d’application BizTalk).|