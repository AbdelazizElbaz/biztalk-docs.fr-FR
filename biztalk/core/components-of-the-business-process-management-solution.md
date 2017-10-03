---
title: "Solution de gestion de traitent les composants de l’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, back-end systems, process management solutions
- process management solution tutorial, client applications
- orchestrations, process management solutions
- adapters, process management solutions
- process management solution tutorial, adapters
- client applications, process management solutions
- process management solution tutorial, components
- process management solution tutorial, orchestrations
- pipelines, process management solutions
- process management solution tutorial, pipelines
- assemblies, process management solutions
- process management solution tutorial, assemblies
ms.assetid: e3ccebb9-b677-4c17-acd2-0f986f7bd3f0
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b63234dbf4a8dc62a620bf2b384b832e4887b0d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="components-of-the-business-process-management-solution"></a>Composants de la Solution gestion des processus d’entreprise
Cette section décrit les principaux composants BizTalk Server de la solution de gestion des processus d'entreprise. Pour plus d’informations sur les fichiers source, consultez [inventaire des fichiers de la Solution de gestion des processus métier](../core/file-inventory-for-the-business-process-management-solution.md).  
  
## <a name="orchestrations"></a>Orchestrations  
 Il existe deux orchestrations principales : **OrderBroker** et **OrderManager**. Le **OrderBroker** orchestration accepte les demandes des clients via un service Web ou par lot via FTP et renvoie des réponses via une file d’attente Microsoft Message Queuing (MSMQ). Les demandes passent du **OrderBroker** à la **OrderManager**. Les deux orchestrations sont directement liées par l'intermédiaire de la base de données MessageBox.  
  
 Le **OrderManager** exécute les demandes via deux étapes de traitement asynchrone à l’aide de la **CableOrder1** et **CableOrder2** orchestrations. Ensemble, le **CableOrder1** et **CableOrder2** orchestrations représentent un seul processus d’entreprise. Cependant, le processus peut être divisé en deux orchestrations afin que des étapes puissent être modifiées sans interrompre le traitement de commande. Pour plus d’informations sur la conception des phases, consultez « Division des processus d’entreprise » dans [certains principes de conception dans la Solution de gestion des processus métier](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
 Le **CableOrder1** d’orchestration utilise la **Validate** orchestration pour valider la commande et pour convertir les codes de demande en actions, appelle l’orchestration Analyze pour analyser l’ordre, puis appelle le **activer**, **Annuler**, ou **modification** orchestration en fonction de l’action requise. Le **CableOrder2** gère l’achèvement de la commande en appelant le **Complete** orchestration. Notez que **CableOrder1** et **CableOrder2** utiliser **appeler** formes pour appeler les orchestrations subordonnées.  
  
> [!NOTE]
>  Le **Annuler** orchestration inclut un bloc de compensation qui appelle le **activer** orchestration. Cela garantit que la commande est correctement restaurée dans le cadre de la compensation de la demande Cancel.  
  
 Le **CableOrder1** et **CableOrder2** les orchestrations utilisent une liaison directe. Pour plus d’informations sur la liaison directe de ces orchestrations, consultez [met en surbrillance de l’implémentation de la Solution de gestion des processus métier](../core/implementation-highlights-of-the-business-process-management-solution.md).  
  
 La plupart des orchestrations sont écrits afin qu’elles puissent être interrompues au cours de traitement à l’aide du **interruption** orchestration. Pour plus d’informations sur le mécanisme d’interruption, consultez [logique du Gestionnaire de processus](../core/process-manager-logic.md).  
  
## <a name="back-end-applications"></a>Applications principales  
 La solution de gestion des processus d'entreprise utilise des simulations pour toutes les applications principales. **CableOrder1**, **CableOrder2**, et elles utilisent toutes les orchestrations utilisent une spéciale **OrderHandler** objet. Le **OrderHandler** utilise .NET remoting pour communiquer avec une simulation d’un système de gestion des commandes. Le **CableProvisioningSystemClient** et **BTSScnBPMProvisioning** (le **CableProvisioningSystemServer** projet) les extrémités avant et arrière de simulent des assemblys l’ordre de la gestion de système, respectivement.  
  
 La solution utilise une application Windows forms, **BSTScnBPMFacilities** (le **simulateur d’installations** projet), pour simuler le serveur MSMQ qui gère les demandes d’installations.  
  
 Outre ces composants, les orchestrations créent également des entrées dans une base de données SQL Server pour maintenir un historique des commandes et de leur traitement.  
  
## <a name="pipelines"></a>Pipelines  
 La solution utilise uniquement des pipelines par défaut standard configurés à l'aide de la console Administration de BizTalk ou des fichiers de liaison. Toutefois, les pipelines exploitent pleinement la configuration par instance. Le port de réception pour les commandes envoyées par FTP utilise la configuration par instance pour configurer l'enveloppe. Pour plus d’informations sur la configuration par instance, consultez [comment déployer des Pipelines](../core/how-to-deploy-pipelines.md).  
  
## <a name="custom-adapter"></a>Adaptateur personnalisé  
 La solution utilise un adaptateur personnalisé, le **OpsAdapter**, pour traiter des erreurs détectées dans le **OrderManager** et **ErrorHandler** orchestrations. La solution utilise l'adaptateur sur les ports pour lesquels la création de rapports d'erreurs est spécifiée. L'adaptateur prend les erreurs et les envoie au système d'opérations. Pour plus d’informations sur le rapport d’erreurs, consultez [à l’aide d’Échec de routage des messages](../core/using-failed-message-routing.md).  
  
## <a name="client-application"></a>Application cliente  
 La solution inclut une soutenu par un programme c#, la page Web ASP.NET **CSRMain.aspx**, pour simuler le système de service client.  
  
## <a name="other-assemblies"></a>Autres assemblys  
 La solution utilise deux assemblys supplémentaires, **schémas** et **utilitaires**. Le **schémas** assembly définit les messages que la solution utilise pour communiquer entre les différentes orchestrations, tels que les **interruption** message. La solution utilise également plusieurs messages .NET définis dans le **SchemaClasses** assembly.  
  
 Le **utilitaires** assembly inclut les classes d’utilitaire et les méthodes pour aider à gérer les messages, pour définir un type d’exception spécifique à la solution, pour lire les valeurs de configuration à partir du magasin de secret principal SSO et pour faciliter la gestion des erreurs. L’assembly inclut également le **Recaller** objet.  
  
 Autres assemblys incluent des assemblys de mappage et de schéma, tels que **OrderBrokerMaps**, **OrderBrokerSchemas**, **cartes**, **MessagingSchemas**, et **SchemaClasses**.  
  
 Le **ServiceLevelTracking** assembly contient les artefacts communs utilisés avec BAM pour suivre les commandes et traitement. Actions de traitement de commande utilisées par les étapes sont dans le **CableOrderActions** assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles dans la Solution gestion des processus d’entreprise](../core/patterns-in-the-business-process-management-solution.md)   
 [Traitement dans la Solution gestion des processus d’entreprise](../core/processing-in-the-business-process-management-solution.md)   
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Analyse de la Solution gestion des processus d’entreprise avec BAM](../core/monitoring-the-business-process-management-solution-with-bam.md)   
 [Contrôle de version de la Solution gestion des processus d’entreprise](../core/versioning-the-business-process-management-solution.md)   
 [Référence de la Solution de gestion du processus métier](../core/business-process-management-solution-reference.md)   
 [Développement d’une Solution de gestion des processus métiers](../core/developing-a-business-process-management-solution.md)   
 [Inventaire des fichiers de la Solution gestion des processus d’entreprise](../core/file-inventory-for-the-business-process-management-solution.md)