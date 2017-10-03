---
title: "Gérer les pipelines | Documents Microsoft"
description: "Liens rapides pour activer le suivi et les propriétés du pipeline sur un port d’envoi ou emplacement de réception dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60b54e0-0a5a-4264-b0e5-96bb187d782b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0edfbdd97e134abc6f153acf136ff62a979f8b0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-pipelines"></a>Gestion des pipelines

## <a name="overview"></a>Vue d'ensemble
Cette section fournit des instructions sur la gestion des pipelines dans un groupe BizTalk à l'aide de la console Administration de BizTalk Server. Vous pouvez configurer le suivi des événements et des messages, ainsi que les propriétés de pipeline d'un emplacement de réception ou port d'envoi spécifique.  
  
 Les pipelines effectuent des actions sur les messages entrants et sortants, telles que la conversion de ces messages d'un format natif en XML, le chiffrement ou le déchiffrement de données, la promotion de propriétés, etc.  
  
 Vous ne pouvez pas ajouter un pipeline de manière individuelle à une application. Son ajout s'effectue dans les cas suivants :  
  
-   Lorsque vous ajoutez un assembly BizTalk contenant un pipeline à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
-   Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant un pipeline, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
-   Lorsqu’un développeur déploie dans une application un assembly contenant un pipeline à partir de Visual Studio, comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
 Pour des informations générales sur les pipelines, consultez [Pipelines](../core/pipelines.md). Pour plus d’informations sur le développement de pipelines, consultez [création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md).  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Configurer le suivi d’un Pipeline](../core/how-to-configure-tracking-for-a-pipeline.md)  
  
-   [Configurer les propriétés de Pipeline par Instance pour un Port d’envoi](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)  
  
-   [Configurer les propriétés de Pipeline par instance d’un emplacement de réception](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)