---
title: "Préparer les serveurs SQL de récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44b77fe8-393d-4781-b0b0-5b7f6e50a67b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47bd787fe5fa33a30f01bc37fd4988ab26db99d1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="preparing-the-disaster-recovery-sql-servers"></a>Préparer les serveurs SQL de récupération d’urgence
Crée un jeu de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances dans le site de récupération d’urgence de base de données. Pour vous assurer que la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des instances de base de données peuvent fournir le même niveau de performance que la production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des instances de base de données, la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des instances de base de données doivent être configurés avec similaires matériel et le nombre d’ordinateurs physiques en cours d’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Dans ce scénario, BizTalk Server d’envoi de journaux sera configuré pour chaque production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance de base de données à appliquer à un correspondant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance de base de données sur le site de récupération d’urgence.  
  
 Une exigence de livraison de journaux BizTalk Server de la clé est que la lettre de lecteur sur le site de production où sont stockés les fichiers de base de données correspond à la lettre de lecteur sur le site de récupération d’urgence où les fichiers de base de données sont restaurés. Par conséquent, si le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] groupe de fichiers de base de données se trouve sur G:\data en production, il doit y avoir un répertoire G:\data sur le serveur de destination (DR) ou la restauration échoue.  
  
 BizTalk Server d’envoi de journaux ne prend pas en charge la **RESTORE WITH MOVE** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] commande. Pour cette raison, nous recommandons que les noms d’instance de base de données sur le site de récupération d’urgence correspondent aux noms d’instance de base de données de production (par défaut, le nom d’instance fait partie du chemin de fichier). Une autre option consiste à simplement créer un répertoire sur la lettre de lecteur dans l’ordinateur en cours d’exécution pour la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] afin que le **restaurer** opération peut créer le fichier dans la même structure de répertoire qu’est utilisé dans production.  
  
 Créer [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des connexions de sécurité pour le site de récupération d’urgence qui correspondent au site de production par dans le cas où un basculement vers le site de récupération d’urgence est requis, toutes les connexions de sécurité sont présentes sur le système de destination.  
  
 Une fois l’installation de la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances est terminée, effectuez une sauvegarde complète des bases de données master et msdb afin qu’un système propre puisse être restauré dans le cas où un basculement vers le site de récupération d’urgence échoue.