---
title: "La mise à jour à l’aide du contrôle de version côte à côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9721a091-98ec-4f0b-ad1f-6ca184956e7c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe8264b76867c2f4fa3200f906e1d99975c9e0eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="updating-using-side-by-side-versioning"></a>La mise à jour à l’aide du contrôle de version côte à côte
Si vous n’êtes pas en mesure de planifier des temps d’arrêt, ou avoir des instances d’orchestration très longue qui ne peut pas être terminées, le contrôle de version côte à côte peut être requis. Dans ce type de mise à niveau, les deux versions de la même application ou les artefacts de l’application s’exécuter côte à côte. Le runtime .NET permet, par nature, en cours d’exécution et les assemblys portant le même nom mais différemment avec version à déployer, et permet également par BizTalk Server.  
  
 Le contrôle de version côte à côte des applications est utile lorsque vous souhaitez déployer une mise à niveau de l’application principale de façon incrémentielle, par exemple rendre disponible pour un sous-ensemble de partenaires commerciaux, plutôt qu’à tous les partenaires à la fois. Ainsi, vous pouvez continuer à exécuter l'application existante afin de desservir les utilisateurs qui n'utilisent pas encore la nouvelle version, jusqu'à-ce que vous soyez prêt à passer définitivement à la nouvelle version.  
  
 Vous ne pouvez pas créer des versions d'une application de la même manière que vous créez des versions d'un assembly, c'est-à-dire en augmentant le numéro de version. Au lieu de cela, vous créez une application qui a un nom différent de l’application d’origine et remplissez avec les nouvelles versions des artefacts d’application.  
  
 Étant donné que de nombreux types d'artefacts, tout comme les assemblys, peuvent exister dans une seule application d'un groupe BizTalk, vous devez augmenter le numéro de version de tout assembly existant dans le groupe avant de pouvoir les déployer dans la nouvelle application.  
  
 Pour obtenir une liste détaillée des tâches requises pour mettre à jour une application ou une orchestration à l’aide du contrôle de version côte à côte, consultez [liste de vérification : mise à jour d’un contrôle de version côte à côte à l’aide de l’Application](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md) et [liste de vérification : mise à jour d’un Orchestration à l’aide du contrôle de version côte à côte](../technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md). Pour obtenir des instructions détaillées à suivre pour que le déploiement côte à côte des applications, consultez «[comment déployer une nouvelle Version d’une Application à l’exécution côte à côte avec une Version existante](http://go.microsoft.com/fwlink/?LinkId=155143) (http://go.Microsoft.com/fwlink/?) LinkId = 155143) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment mettre à jour un mappage à l’aide de la gestion des versions côte à côte](../technical-guides/how-to-update-a-map-using-side-by-side-versioning.md)  
  
-   [Comment mettre à jour d’un Pipeline à l’aide de la gestion des versions côte à côte](../technical-guides/how-to-update-a-pipeline-using-side-by-side-versioning.md)  
  
-   [Mise à jour un schéma à l’aide du contrôle de version côte à côte](../technical-guides/updating-a-schema-using-side-by-side-versioning.md)