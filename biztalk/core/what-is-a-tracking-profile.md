---
title: "Qu'est-ce qu'un modèle de suivi ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, about tracking profiles
- tracking profiles, Tracking Profile Editor
- Tracking Profile Editor, tracking profiles
- tracking profiles
ms.assetid: b579bdc4-7c69-4fa0-bbc1-f98170c13d4f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da032fb6063d81cedca9f21899c5e2bbe6eca947
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-a-tracking-profile"></a>Qu'est-ce qu'un modèle de suivi ?
Un modèle est un ensemble de caractéristiques qui définissent un processus d'entreprise. Un modèle de suivi contient le mappage de ces caractéristiques entre une activité et des orchestrations et des ports. C'est un fichier dont le nom est doté de l'extension .btt.  
  
## <a name="using-tracking-profiles-in-the-tpe"></a>Utilisation de modèles de suivi dans l'Éditeur de modèle de suivi  
 Les utilisateurs de l'Éditeur de modèle de suivi créent un mappage, ou modèle de suivi, entre les éléments d'une activité BAM et les sources de solution BizTalk Server correspondant à ces éléments. Les activités BAM se composent des étapes majeures et des données contextuelles qui constituent la « liste souhaitée de visibilité ». Elles définissent une unité de travail dans l'activité commerciale que suit le modèle de suivi. Pour plus d’informations sur les activités, consultez [mise en œuvre les activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md).  
  
 Lorsque vous créez un modèle de suivi à l'aide de l'Éditeur de modèle de suivi, vous travaillez avec les objets suivants :  
  
-   Activités BAM  
  
-   Orchestrations BizTalk au sein d'assemblys déployés  
  
-   Ports d'envoi et de réception  
  
-   Schémas de message au sein d'assemblys déployés  
  
-   Propriétés de contexte  
  
-   Base de données d'importation principale BAM  
  
-   Base de données de gestion BizTalk  
  
-   Base de données des suivis BizTalk  
  
 Pour définir l'extraction de données issues d'une orchestration, vous devez déplacer les éléments de schémas de message, de formes d'orchestration et de propriétés de contexte et les déposer dans les étapes majeures commerciales (événements) et les dossiers des éléments de données correspondants.  
  
 Prenez par exemple une activité BAM comportant une étape majeure appelée PO Received et dotée d'un port de messagerie qu'un flux de bons de commande traverse dans le but d'initier le traitement. Dans leur solution, les développeurs peuvent associer pour le port l'étape majeure `PO Received` à une propriété de la messagerie BizTalk appelée `PortEndTime`. Sémantiquement, cela indique que le bon de commande est reçu correctement une fois que le port de réception termine son action et renseigne la propriété `PortEndTime`. Le développeur accomplit cette opération et tout autre mappage afin d'achever le modèle de suivi. Tous les éléments de l'activité sont mappés s'ils ont une source de BizTalk Server ou ne le sont pas, afin d'être renseignés par des appels API directement, si la source des données ou de l'événement appartient à un processus extérieur à l'environnement d'exécution de BizTalk Server.  
  
 Si chaque volet ou vue de l'Éditeur de modèle de suivi a une unique fonction, l'ensemble des vues et des dossiers possèdent des fonctionnalités de navigation similaires pour vous aider à trouver et manipuler les informations plus facilement.  
  
## <a name="who-uses-tracking-profiles-and-the-tpe"></a>Qui utilise les modèles de suivi et l'Éditeur de modèle de suivi ?  
 Les utilisateurs participant au développement de l'intégration d'entreprise utilisent des modèles de suivi et l'Éditeur de modèle de suivi pour mapper des sources d'événements à des activités cibles BAM. Le fichier .btt en résultant est remis à l'implémentation informatique en vue de son déploiement.  
  
 Les utilisateurs de l'implémentation informatique appliquent généralement les modèles de suivi à l'aide d'outils de ligne de commande (BTTDeploy). Ils peuvent également utiliser directement l'Éditeur de modèle de suivi à cette fin.  
  
 Les utilisateurs du back office sont susceptibles d'être chargés, de façon planifiée, de la mise à jour périodique des modèles de suivi (ainsi que de toute opération requise sur les bases de données, la sauvegarde et la restauration par exemple), en particulier à la suite de changements dans les spécifications commerciales.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)