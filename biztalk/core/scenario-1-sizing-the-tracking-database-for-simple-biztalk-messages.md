---
title: 'Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: 5b8fed48-d9c9-4d1f-a320-d3e23b8b1ec9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b9c99c99485e34f95c6f6a75b86170d73678518
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-1-sizing-the-tracking-database--for-simple-biztalk-messages"></a>Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples
Dans le schéma ci-dessous, un message BizTalk entre et sort du serveur BizTalk Server sans être soumis à aucune transformation.  
  
 ![Message de BizTalk Server simple &#45; Aucune transformation](../core/media/simple-bts-message.gif "Simple_BTS_Message")  
  
 **Un message BizTalk Server simple : aucune transformation**  
  
 Avant d'appliquer la formule décrite dans la section précédente, vous devez rassembler quelques informations concernant le présent scénario. Dans cet exemple, les données sont les suivantes :  
  
-   taille du message : 5 Ko ;  
  
-   aucune propriété promue ;  
  
-   nombre de messages reçus dans une année : 3,5 millions ;  
  
-   suivi activé pour tous les événements, ici au nombre de quatre Les événements sont :  
  
    -   Réception du message M0  
  
    -   Sortie du message M1 provenant du port de réception  
  
    -   Réception du message M1 par le pipeline de transmission  
  
    -   Sortie du message M2 par le pipeline d'envoi  
  
-   création de deux messages dans ce scénario : le message M0 étant le message entrant, il n'est pas créé par BizTalk Server. le message M1 sortant du port de réception et le message M2 sortant du port de transmission sont créés par BizTalk Server.  
  
 L'intégration de ces données à la formule précédemment mentionnée donne le résultat suivant :  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-with-a-single-promoted-property"></a>Messages dont la propriété promue est unique  
 Reprenons l'exemple précédemment mentionné et prenons en compte les nouveaux éléments suivants dans le scénario. Vous souhaitez promouvoir un seul champ, d'environ 10 octets, du message d'origine. La taille maximale d'un champ promu est de 256 caractères, soit environ 256 octets (512 octets s'il s'agit de caractères Unicode).  
  
 En tenant compte de ces nouvelles données, l'équation se présente comme suit :  
  
```  
[(2*150 bytes) + (4*230 bytes) + (1*2(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 124) * 3,500,000]/1024/1024 = 4486 MB ~ 4.38 GB per year  
```  
  
 Si vous souhaitez promouvoir un autre champ de 10 octets, l'équation est alors la suivante :  
  
```  
[(2*150 bytes) + (4*230 bytes) + ((1*2*(52 bytes + 10 bytes) + (1*2*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 248) * 3,500,000]/1024/1024 = 4899 MB ~ 4.78 GB per year  
```  
  
 Vous pouvez donc constater que lorsqu'une seule propriété de 10 octets est promue dans ce scénario, la taille de la base de données des suivis augmente de 333,79 Mo (environ 0,33 Go) par an.  
  
 Deux propriétés de 10 octets promues entraînent donc une augmentation annuelle de l'espace occupé par la base de données des suivis équivalente à 667,58 Mo (environ 0,65 Go).  
  
## <a name="messages-with-message-body-tracking-activated"></a>Messages pour lesquels le suivi du corps des messages est activé  
 Dans cet exemple, supposons qu'il soit prévu d'activer le suivi du corps des messages. Il faut alors ajouter la seconde équation de suivi des messages comme indiqué dans la section précédente. L'équation se présente comme suit :  
  
```  
[3,500,000 * 4 * 5KB]/1024 = 68359.375 MB ~ 66.75 GB per year  
  
```  
  
 En ajoutant les résultats des deux équations, il est possible d'estimer que la taille de la base de données des suivis augmentera de 54,48 Go à 54,88 Go par an.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md)   
 [Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)   
 [Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)