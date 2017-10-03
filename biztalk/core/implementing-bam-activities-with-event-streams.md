---
title: "Implémentation d’activités BAM avec les flux d’événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], about activities
- activities [BAM]
- BAM, activities
ms.assetid: 94e6d9dd-93c3-4ab0-9de7-a860dd1e3406
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63594b956affc0f5b94f26ccdcb10d904ef171cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-bam-activities-with-event-streams"></a>Implémentation d'activités BAM avec des flux d'événements
Une activité BAM représente une unité de travail dans une activité commerciale : un bon de commande ou une application d'emprunt par exemple. L'activité affiche l'historique (étapes majeures) et les données ayant trait à cette unité de travail à l'utilisateur final du processus d'entreprise ou au travailleur de l'information. Par exemple, une application d'emprunt pourra contenir des étapes majeures telles que « Emprunt approuvé » et des données comme « Nom du candidat » et « Montant de l'emprunt ». Les activités BAM sont souvent directement mappées vers un processus d'entreprise même si, en tant qu'abstractions de haut niveau, les activités sont indépendantes de l'implémentation de votre infrastructure informatique.  
  
 En tant que développeur, votre rôle consiste à conserver cette abstraction en n'exposant que les données et les étapes majeures pertinentes de l'implémentation dans le contexte d'une activité spécifique. Pour voir un exemple de code qui illustre l’utilisation d’une activité, [l’API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Pourquoi écrire du Code pour l’analyse BAM ?](../core/why-write-code-for-bam.md)  
  
-   [Concepts d’analyse BAM pour les développeurs](../core/bam-concepts-for-the-developer.md)  
  
-   [Vue d’ensemble du processus de développement BAM](../core/overview-of-the-bam-development-process.md)  
  
-   [Classes EventStream](../core/eventstream-classes.md)  
  
-   [À l’aide d’une activité](../core/using-an-activity.md)  
  
-   [Relations d’activité](../core/activity-relationships.md)  
  
-   [Continuation d’activités](../core/activity-continuation.md)  
  
-   [Activités de bouclage](../core/looping-activities.md)  
  
-   [Instrumentation d’une Solution : utilisation de l’API pas à pas](../core/instrumenting-a-solution-step-by-step-api-usage.md)