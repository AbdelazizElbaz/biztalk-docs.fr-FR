---
title: "Comment mapper des Sources d’événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, alerts
- orchestrations, schedules
- events, mapping sources
- orchestrations, tracking profiles
- events, orchestration schedules
- tracking profiles, orchestrations
- tracking profiles, alerts
- alerts, tracking profiles
- alerts, BAM
- tracking profiles, mapping event sources
- events, tracking profiles
ms.assetid: 507f1624-2cd8-4960-8c63-7797ab22519e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 588a394fb3404872554fc786efa3fe24fdd9b47a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-event-sources"></a>Mappage des sources d'événements
Le mappage des sources d'événements vous permet d'accéder aux éléments de données auxquels le composant BAM applique un suivi pour générer des alertes.  
  
> [!NOTE]
>  Vous pouvez mapper des éléments de données à partir de quatre types de source d’événements différents : les planifications d’orchestration, les charges de message, les propriétés de contexte ou les propriétés de messagerie. La procédure décrite dans cette rubrique illustre le mappage d'éléments de données à partir d'une planification d'orchestration.  
  
### <a name="to-map-an-orchestration-schedule-as-an-event-source"></a>Pour mapper une planification d'orchestration en tant que source d'événement  
  
1.  Ouvrez un modèle de suivi existant ou créez-en un. Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).  
  
2.  Cliquez sur le **Source d’événement sélectionnez** bouton (située au-dessus du volet droit dans l’éditeur de modèle de suivi).  
  
3.  Sélectionnez le **sélectionner une planification d’Orchestration** dans le menu en cascade.  
  
4.  Sélectionnez l’assembly parent à partir duquel dessiner l’orchestration en cliquant sur l’assembly contenant l’orchestration dans le **nom de l’Assembly** zone de liste, puis cliquez sur **suivant**.  
  
     ![Sélectionnez l’Assembly Parent en tant que Source dans l’éditeur de l’événement](../core/media/tpeselectparentassembly.gif "TPESelectParentAssembly")  
  
5.  Sélectionnez l’orchestration qui est la source pour les éléments de données dans le **nom de l’Orchestration** zone de liste, puis cliquez sur **OK**.  
  
6.  Dans le volet droit, sélectionnez les éléments de données et faites-les glisser vers les nœuds appropriés de l'activité dans le volet gauche.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)   
 [Création de modèles de suivi](../core/creating-tracking-profiles.md)