---
title: "Configurer le traitement par lot pour améliorer les performances de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65589925-af94-45f1-b501-37c21618b2cf
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dbee8e5b238af0a6dc7f15d54b85d85e0c4b26c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching-to-improve-adapter-performance"></a>Configurer le traitement par lot pour améliorer les performances de l’adaptateur
La façon dont un adaptateur traite un lot peut avoir un impact significatif sur les performances. Un délai fixe étant associé à chaque transaction, vous devez faire en sorte de limiter le nombre de transactions en les combinant dans un lot unique.  
  
 Si vous envoyez des messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par lots, ne pas limiter la taille de lot basée uniquement sur le nombre de messages. Par exemple, si la taille de lot est deux et que l’adaptateur obtient quatre messages de taille de 4 Ko, 8 Ko, 1 Mo et 5 Mo respectivement, le premier lot sera de taille 12 Ko et le deuxième lot sera de 6 Mo. Le moteur de messagerie BizTalk traitant tous les messages d'un lot unique de manière séquentielle, le deuxième lot dans cet exemple sera traité beaucoup plus lentement que le premier. L’effet est le débit réduit.  
  
 Pour gérer ce problème, nous vous recommandons de ce lot vous selon le nombre de messages et le nombre total d’octets dans le lot (autrement dit, taille de lot en octets). Il n’existe aucun nombre optimal pour le nombre total d’octets. Toutefois, dans un scénario de traitement normal, si la taille de lot dépasse 1 Mo, vous allez commencer rencontrer de débit et accès concurrentiel médiocre.  
  
 Adaptateurs traitent généralement les messages de taille variable dans l’environnement de production. Les tailles des messages entrants sont susceptibles de varier considérablement. Par conséquent, toujours utiliser octets de nombre et le nombre total de messages pour générer le lot.