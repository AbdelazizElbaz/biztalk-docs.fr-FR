---
title: "Analyse l’espace disque | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac68022-a9c5-4eb9-8854-cd1ee849282b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ae87de0b00e70ae03a30dd8ef20ede4a972388d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-disk-space-usage"></a>Analyse l’espace disque
Dans le cadre du processus d’analyse pour l’état de préparation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], surveillez l’utilisation de l’espace disque comme suit :  
  
-   **Déterminer le disque de l’espace requis.**  
  
     Lorsque utilisant MSMQ ou envoi / emplacements de réception, assurez-vous qu’il existe beaucoup d’espace disque disponible pour prendre en compte les pannes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou des systèmes de réception. Par exemple, si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est l’écriture de fichiers sur un partage sur un réseau SAN et le système de réception est arrêté pendant deux jours, déterminez s’il existe suffisamment d’espace disque pour permettre les fichiers en file d’attente.  
  
-   **Nettoyer périodiquement le répertoire de fichiers de sauvegarde de BizTalk Server.**  
  
     Vous pouvez effectuer à l’aide d’un script appelé à partir d’un travail de l’Agent SQL Server.  
  
-   **Nettoyez régulièrement le répertoire des fichiers archive de base de données des suivis BizTalk.**  
  
-   **Vérifiez qu’il existe suffisamment d’espace disque disponible pour prendre en compte la plus grande base de données BizTalk Server (.mdf) et des journaux de transactions (.ldf) pendant les heures de pointe du flux de données.**