---
title: "Appelée « Incidents2 » | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 709c19ea-1138-49f8-8898-c2d2c60c3923
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28378697c145f48881f4ae850488c0c5afcb4ea3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues"></a>Problèmes connus
Le tableau suivant répertorie tous les problèmes connus avec la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack pour Operations Manager 2007 R2/2012.  
  
|Problème| Description|Résolution|  
|-----------|-----------------|----------------|  
|Compteurs de performances liés les erreurs et avertissements après le redémarrage|Vous pouvez voir les erreurs associées dans des performances et des avertissements dans le journal des événements Operations Manager après l’agent de redémarrer.|Le Pack d’administration permet de récupérer après les erreurs et reprend le travail.|  
|Avertissements dans le journal des événements liés à la découverte d’objets|Lorsqu’une opération de découverte (y compris la détection de relation) ne parvient pas à trouver une instance, un avertissement est écrit dans le journal des événements Operations Manager indiquant que la valeur null a été retournée par le script de découverte.||  
|Génération d’alertes dans le nœud physique dans un environnement en cluster n’est pas fiable|Il existe deux problèmes connus associés à la surveillance dans les environnements en cluster :<br /><br /> -Lors de la modification d’un nœud actif au mode passif, l’état d’analyse du nœud et artefacts associés ne seront pas reportée correctement dans la Console opérateur.<br />-Dans les environnements en cluster, Operations Manager crée un nœud virtuel qui peut afficher des alertes et l’état en double.|Dans les environnements en cluster qui contient les nœuds de type actif/passif. s’appuient sur les informations d’analyse s’affichées dans le nœud virtuel uniquement. Il s’agit, car le nœud virtuel pointe toujours vers le nœud physique qui est actif à n’importe quel point dans le temps.|  
|Relations et des moniteurs de dépendance|Voici les problèmes connus liés aux relations et des moniteurs de dépendance : cela produit généralement lorsque le Pack d’administration de BizTalk est réimporté sur un serveur donné de SCOM. L’utilisateur est alors requise pour commenter l’état précédent, tel qu’indiqué dans la section « Étapes pour reproduire le problème ».<br /><br /> -Les relations entre les artefacts BizTalk ne sont pas détectées.<br />-Relations de dépendance ne s’affichent pas comme prévu.<br />-Cumul de surveillance de l’état n’a pas lieu.<br />-Certains moniteurs de dépendance ne sont pas initialisées même après la détection de relation.|Les solutions de contournement pour résoudre ces problèmes sont les suivantes :<br /><br /> <ul><li>Redémarrez le Service de contrôle d’intégrité Operations Manager sur l’ordinateur de l’agent de BizTalk. <br />     -OU-</li><li>Exécuter la tâche de vidage Health Service State et Cache. Les étapes à suivre sont les suivantes :<br /><br /> <ol><li>Dans l’arborescence de navigation, sélectionnez l’état d’intégrité d’Operations Manager Agent Agent.</li><li>Sélectionnez l’ordinateur qui exécute BizTalk Server dans l’état de l’Agent à partir de l’Observateur du Service de contrôle d’intégrité.</li><li>Sélectionnez l’état de l’agent sous l’état de l’Agent.</li><li>Cliquez sur la tâche de vidage Health Service State et Cache dans le volet de droite.</li><li>Dans la tâche d’exécution - état du Service de contrôle d’intégrité vidage et la boîte de dialogue de Cache, cliquez sur Exécuter.</li></ol></li></ul>|  
|Présente les incorrect d’état des ports d’envoi et les emplacements de réception|Lorsque le service SSO est arrêté, le Pack d’administration de BizTalk Server ne pas afficher l’état correct des ports d’envoi et emplacements de réception.||