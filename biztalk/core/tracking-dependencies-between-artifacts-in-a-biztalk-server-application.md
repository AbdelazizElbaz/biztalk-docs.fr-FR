---
title: "Suivi des dépendances entre les artefacts dans une Application BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 503cadfc-08e5-4b34-94a2-3b0ea6ad6228
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3edd162075f1ad660c005fd387ac9bc6c8c79e38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-dependencies-between-artifacts-in-a-biztalk-server-application"></a>Suivi des dépendances entre les artefacts dans une application BizTalk Server
Une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] typique inclut divers artefacts tels que des orchestrations, des ports d’envoi, des emplacements de réception, des pipelines, des schémas, des mappages, etc. Tous ces artefacts sont interdépendants. Le tableau suivant répertorie ces dépendances.  
  
|Artefacts|Orchestration|Port d’envoi|Port de réception|Emplacement de réception|Pipeline|Cartes|Schémas|  
|---------------|-------------------|---------------|------------------|----------------------|--------------|----------|-------------|  
|**Orchestration**||![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||||  
|**Port d’envoi**|![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||||![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")|![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||  
|**Port de réception**|![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")|||![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||  
|**Emplacement de réception**|||![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")|||  
|**Pipeline**||![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||||  
|**Carte**||![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")|![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||||![À l’aide de](../core/media/dependency-using-icon.png "Dependency_Using_Icon")|  
|**Schéma**||||||![Utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||  
  
 Comme l’indique le tableau, il existe deux modes de dépendances.  
  
-   Utilise (![Using](../core/media/dependency-using-icon.png "Dependency_Using_Icon")) – un artefact utilise un autre artefact, par exemple, un port d’envoi utilise un pipeline.  
  
-   Utilisé par (![utilisé par](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")) – un artefact est utilisé par un autre artefact, par exemple, un port d’envoi est utilisé par une orchestration.  
  
 Avec ces dépendances, si vous avez besoin de mettre à jour un artefact, vous devez connaître les artefacts présents dans la hiérarchie des dépendances qui doivent être arrêtés ou redéployés. Ces informations sont disponibles dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration affiche les informations de dépendance dans les deux modes, si un artefact utilise un autre artefact *ainsi que* si un artefact est utilisé par un autre artefact.  
  
## <a name="viewing-dependencies"></a>Affichage des dépendances  
 Cette section contient des informations sur l’affichage des dépendances à l’aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  La procédure suivante contient des instructions sur l’affichage des dépendances d’une orchestration. Vous pouvez suivre les mêmes instructions pour afficher les dépendances d’autres artefacts.  
  
#### <a name="to-view-dependencies-for-an-artifact"></a>Pour afficher les dépendances d’un artefact  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, développez une application, puis cliquez sur **Orchestrations**. Dans le volet central, cliquez sur l’orchestration pour laquelle vous souhaitez afficher les dépendances, puis cliquez sur **afficher les dépendances**.  
  
2.  Au bas du volet, le **statistiques sur les dépendances** volet, affiche deux catégories de dépendances. Le **utilisé par** catégorie affiche les artefacts qui utilisent cette orchestration. Le **Using** catégorie affiche les artefacts qui sont utilisés par l’orchestration spécifique.  
  
     ![Dépendances d’une orchestration](../core/media/dependency-orchestration.jpg "Dependency_Orchestration")  
  
     Car aucun autre artefact ne dépend d’une orchestration, le **utilisé par** catégorie de dépendances d’une orchestration est vide. Toutefois, sous la **Using** mode de dépendance, l’illustration montre que l’orchestration dépend d’un port d’envoi. Le nombre de dépendances est affiché sous forme de lien hypertexte. Le fait de cliquer sur ce lien affiche uniquement les ports d’envoi dont dépend l’orchestration. Notez que même après avoir cliqué sur le lien hypertexte pour lister les ports d’envoi, le volet des dépendances affiche toujours les statistiques sur les dépendances pour l’orchestration, et non celles correspondant au port d’envoi.  
  
     Vous pouvez cliquez sur les ports d’envoi, puis sur **afficher les dépendances** là encore, pour afficher la matrice des dépendances pour le port d’envoi. Vous pouvez afficher une telle arborescence des dépendances jusqu’à n’importe quel niveau. Le niveau auquel vous vous trouvez dans l’arborescence des dépendances est signalé par des pointillés en haut du volet, comme le montre l’image ci-dessous.  
  
     ![Pain pour une arborescence des dépendances des vues miniatures](../core/media/dependency-breadcrumbs.jpg "Dependency_BreadCrumbs")