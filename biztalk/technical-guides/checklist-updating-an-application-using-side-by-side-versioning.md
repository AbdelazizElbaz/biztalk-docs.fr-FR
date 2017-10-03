---
title: "Liste de vérification : Mise à jour d’une Application à l’aide du contrôle de version côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3adee8da-18d4-4b9e-a22e-148b90d18179
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5447743ff9cdc7a109d78c3dac57e0e3345556a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-updating-an-application-using-side-by-side-versioning"></a>Liste de vérification : Mise à jour d’une Application à l’aide du contrôle de version côte à côte
La liste de vérification suivante décrit le processus de déploiement d’une version mise à jour d’une application BizTalk qui s’exécute côte à côte avec une version existante.  
  
 Une installation côte à côte vous permet de déployer une mise à niveau de l’application incrémentielle. Vous pouvez effectuer une installation disponible à un sous-ensemble de partenaires commerciaux, plutôt qu’à tous les partenaires à la fois. Cette approche vous permet de continuer à s’exécuter l’application existante pour les utilisateurs qui se ne sont pas encore à l’aide de la nouvelle version jusqu'à ce que vous êtes prêt à déplacer complètement vers la nouvelle version de service.  
  
 Les deux applications côte à côte aura recevoir des messages sur deux emplacements de réception. Par conséquent, pour exécuter des applications côte à côte vous devez demander ces partenaires commerciaux qui doit utiliser la nouvelle version de l’application pour envoyer des messages vers le nouvel emplacement de réception, afin qu’ils seront traités par la nouvelle version. Ces partenaires qui doivent utiliser l’ancienne version doivent envoyer l’emplacement de réception de messages à la précédente.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Créer et implémenter une stratégie de contrôle de version.|Section « Contrôle de version » [meilleures pratiques pour la mise à jour des Applications](../technical-guides/best-practices-for-updating-applications.md).|  
|Apportez les modifications nécessaires pour les projets que vous souhaitez déployer dans la nouvelle version de l’application.|-   [Comment créer ou ajouter un artefact](http://go.microsoft.com/fwlink/?LinkID=154724) (http://go.microsoft.com/fwlink/?LinkID=154724).<br />-   [La gestion des artefacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725).<br />-   [Fichiers de liaison et déploiement d’applications](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.microsoft.com/fwlink/?LinkID=154726).<br />-   [Ajout d’artefacts à une Application](../technical-guides/adding-artifacts-to-an-application.md)|  
|Incrémenter le numéro de version de chaque assembly.|[Comment mettre à jour un Assembly](../technical-guides/how-to-update-an-assembly.md)|  
|Définissez les propriétés de déploiement pour chaque projet dans la solution (définition de l’application de destination et l’activation de l’installation dans le global assembly cache (GAC)).|[Comment mettre à jour un Assembly](../technical-guides/how-to-update-an-assembly.md)|  
|Déployer des solutions contenant les assemblys modifiés dans une application dans votre environnement de développement.|-   [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).<br />-   [Comment redéployer un Assembly BizTalk à partir de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720).<br />-   [Déploiement d’un Assembly](../technical-guides/deploying-an-assembly.md)|  
|Créer un nouveau port de réception et un emplacement de réception nécessaire en spécifiant les nouvelles URL que vous souhaitez pour envoyer des messages aux partenaires.<br /><br /> Si nécessaire, créez les ports d’envoi approprié.<br /><br /> Si nécessaire, lier la nouvelle application vers le nouvel recevoir et envoyer des ports et tester le fonctionnement de l’application.|-   [Comment créer un Port de réception](http://go.microsoft.com/fwlink/?LinkId=154843) (http://go.microsoft.com/fwlink/?LinkId=154843).<br />-   [Comment créer un emplacement de réception](http://go.microsoft.com/fwlink/?LinkId=154844) (http://go.microsoft.com/fwlink/?LinkId=154844).<br />-   [Comment créer un Port d’envoi](http://go.microsoft.com/fwlink/?LinkId=154845) (http://go.microsoft.com/fwlink/?LinkId=154845).<br />-   [Comment configurer une Application](http://go.microsoft.com/fwlink/?LinkId=154847) (http://go.microsoft.com/fwlink/?LinkId=154847).|  
|Exporter la nouvelle application dans un fichier .msi à partir de votre environnement de développement.|-   [Comment exporter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkId=154848) (http://go.microsoft.com/fwlink/?LinkId=154848).<br />-   [Fichiers de liaison et déploiement d’applications](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.microsoft.com/fwlink/?LinkID=154726).<br />-   [Comment exporter une Application vers un fichier .msi](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   [Comment exporter des liaisons vers un fichier de liaison](../technical-guides/how-to-export-bindings-to-a-binding-file.md)|  
|Importer le fichier .msi d’application dans le groupe BizTalk dans votre environnement de production.|-   [Comment importer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkId=154827) (http://go.microsoft.com/fwlink/?LinkId=154827).<br />-   [Comment installer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154728) (http://go.microsoft.com/fwlink/?LinkID=154728).<br />-   [Comment importer une Application à partir d’un fichier .msi](../technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-   [Comment importer des liaisons à partir d’un fichier de liaison](../technical-guides/how-to-import-bindings-from-a-binding-file.md)|  
|Effectuer un démarrage complet de l’application.|-   [Comment démarrer et arrêter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154729) (http://go.microsoft.com/fwlink/?LinkID=154729).<br />-   [Tâches de test pour le déploiement d’applications BizTalk](http://go.microsoft.com/fwlink/?LinkId=154825) (http://go.microsoft.com/fwlink/?LinkId=154825).|  
|Informez vos partenaires qu’ils doivent démarrer l’envoi de messages aux nouvelle URL. Ainsi, l'application commence à traiter les messages des partenaires spécifiés.|-|