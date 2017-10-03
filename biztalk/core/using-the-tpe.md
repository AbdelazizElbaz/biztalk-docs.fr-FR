---
title: "À l’aide de l’éditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, about Tracking Profile Editor
- tracking profiles, prerequisites
ms.assetid: ebe9a5da-66ec-482d-8aac-892a829ca996
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0fa826ce68042336c2b6e4fb006ecb278a3f981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-tpe"></a>Utilisation de l'Éditeur de modèle de suivi
Vous utilisez l'Éditeur de modèle de suivi pour mapper des orchestrations et des propriétés sur les définitions d'activité BAM.  
  
 Les utilisateurs de l'Éditeur de modèle de suivi créent un mappage, ou modèle de suivi, entre les éléments d'une activité BAM tels que des étapes majeures et données contextuelles (parfois appelées « liste souhaitée de visibilité ») et les fichiers sources de la solution BizTalk correspondant à ces éléments.  
  
 **Création d’un modèle de suivi**  
  
 Prenons l'exemple d'une activité BAM comportant une étape majeure appelée « PO Received ». Pour avoir créé des processus dans d'autres outils de développement BizTalk Server, le développeur sait que ce processus inclut un port de messagerie via lequel des bons de commande sont transmis pour initier le traitement. Le développeur détermine qu'il est préférable que l'étape majeure d'activité, appelée « PO Received », soit associée à une propriété de messagerie BizTalk appelée « PortEndTime » pour le port dans la solution. En outre, le développeur procède à tous les mappages nécessaires pour terminer le modèle de suivi. Pour cela, il charge l'activité, sélectionne des sources d'événements et fait glisser les éléments appropriés depuis les sources d'événements dans les nœuds correspondants de la définition de l'arborescence d'activité.  
  
 **Configuration requise pour la création d’un profil**  
  
 Il existe deux conditions préalables à la création d'un modèle de suivi :  
  
1.  Une activité BAM a été définie par l'analyste d'entreprise comme faisant partie d'un modèle d'observation global et a été déployée par l'administrateur système.  
  
2.  Une solution BizTalk (incluant des orchestrations, des schémas, un mappage et des pipelines) a été correctement déployée dans l'environnement cible.  
  
 Ces conditions préalables sont nécessaires puisque après son installation, l'Éditeur de modèle de suivi n'est plus renseigné avec des données pouvant être extraites depuis les bases de données.  
  
 **Création d’un profil pour des Solutions BAM personnalisées**  
  
 Les modèles de suivi s'appliquent uniquement aux composants d'exécution possédant un intercepteur. Pour les solutions BAM constituées de code personnalisé utilisant les API de l'analyse BAM, il n'existe pas d'intercepteur d'exécution BAM associé et l'envoi des données vers l'analyse BAM peut se faire de deux façons uniquement :  
  
-   Directement par le biais des API de l'analyse BAM. Grâce aux API, les développeurs peuvent explicitement envoyer des données d'événement à l'infrastructure BAM. Pour plus d’informations sur l’utilisation de l’API BAM, consultez [mise en œuvre les activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md).  
  
-   Indirectement, par l'intermédiaire des propriétés de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans le cas où le code personnalisé est exécuté à l'intérieur d'un contexte d'exécution ne disposant pas d'une technologie d'interception associée, telle qu'un pipeline personnalisé ou des formes d'expression/action pour l'invocation d'un assembly personnalisé, vous pouvez utiliser les API de l'analyse BAM selon les indications ci-dessus ou mettre en œuvre les techniques traditionnelles de promotion des données. En promouvant les propriétés, vous les rendez accessibles à l'Éditeur de modèle de suivi. De plus, l'association des données d'événement à un élément d'activité BAM peut ensuite être réalisée dans l'Éditeur de modèle de suivi à l'aide de la propriété de contexte appropriée. Pour plus d’informations sur la promotion des propriétés, consultez [promotion des propriétés](../core/promoting-properties.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de modèles de suivi](../core/creating-tracking-profiles.md)  
  
-   [Comment supprimer des profils de suivi orphelins](../core/how-to-remove-orphaned-tracking-profiles.md)  
  
-   [À l’aide de plusieurs Continuations](../core/using-multiple-continuations.md)