---
title: "Sur le système de projet BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, about projects
- applications, creating
- creating, applications
- creating, business solutions
- business solutions, creating
ms.assetid: 69807e57-356e-451d-b803-4253b891b617
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddff6ff13611ee404a5517384455b0c59f968ee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-biztalk-project-system"></a>Sur le système de projet BizTalk
Le système de projet BizTalk permet de créer tout ou partie d'une application ou solution d'entreprise Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'élément principal d'une telle solution est un projet BizTalk : un ensemble d'éléments, tels que des schémas, des orchestrations, des types de messages Web, des classes, des pipelines, des mappages et des références que vous pouvez créer et générer dans un assembly que vous déployez ensuite.  
  
 Une solution d'entreprise relativement simple peut par exemple consister en un projet BizTalk unique généré dans un assembly unique. Si votre solution d'entreprise est plus complexe (par exemple parce qu'elle intègre de nombreux systèmes et processus différents), une possibilité de solution BizTalk pourra comporter de nombreux assemblys générés à partir de nombreux projets BizTalk et déployés vers plusieurs ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!IMPORTANT]
>  Vous ne devez pas utiliser de virgules dans les noms d'assembly.  
  
 Lorsque vous créez un projet BizTalk, vous incluez généralement un ou plusieurs des types de fichiers de la liste ci-dessous. Ces types de fichiers jouent des rôles spécifiques dans la création de votre solution et le système de projet BizTalk vous fournit un outil de conception graphique pour chacun d'eux.  
  
-   **Orchestrations.** une orchestration représente le workflow d'un processus d'entreprise. Utilisez le Concepteur d'orchestration pour concevoir des orchestrations. Pour plus d’informations sur le Concepteur d’Orchestration, consultez [création d’Orchestrations à l’aide de concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md).  
  
-   **Schémas.** les schémas décrivent la structure des documents XML. Les schémas échangent des informations entre les applications d'une organisation ou entre des partenaires commerciaux. L'Éditeur BizTalk simplifie le processus de définition des schémas. Pour plus d’informations sur l’Éditeur BizTalk, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md).  
  
-   **Elle est mappée.** les mappages convertissent les données d'un format vers un autre. Le Mappeur BizTalk présente les schémas source et de destination en vis-à-vis et permet de définir les transformations entre les éléments de données de différents messages. Pour plus d’informations sur le Mappeur BizTalk, consultez [création de mappages à l’aide du mappeur de BizTalk](../core/creating-maps-using-biztalk-mapper.md).  
  
-   **Pipelines.** les pipelines effectuent plusieurs opérations afin de préparer les messages entrants et sortants au traitement suivant. Le Concepteur de pipeline permet d'implémenter les opérations telles que le chiffrement et le déchiffrement, la compression, le reformatage et la validation. Pour plus d’informations sur le Concepteur de Pipeline, consultez [création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md).  
  
 Les projets BizTalk sont compatibles avec Team Foundation Server (TFS). Pour plus d’informations sur la conception, développer et déployer des solutions BizTalk Server avec TFS, consultez [Developing Integration Solutions à l’aide de BizTalk Server et Team Foundation Server](http://www.microsoft.com/downloads/details.aspx?FamilyID=ed7bd0ee-1385-4041-8f2a-354594ee88f3&DisplayLang=en).  
  
> [!IMPORTANT]
>  TFS Build expose une propriété appelée « Plateforme MSBuild » qui peut prendre 3 valeurs : « Auto », « x86 » et « x64 ». Pour garantir la réussite de la génération, la valeur de cette propriété doit être définie sur x86.  
  
 Les projets BizTalk peuvent coexister avec d'autres projets dans Visual Studio. Comme pour tous les systèmes de projet Visual Studio, les projets BizTalk peuvent inclure d'autres fichiers, tels que des pages ASP.NET, et peuvent faire référence à d'autres projets et assemblys que vous avez créés. Pour plus d’informations sur le modèle de projet BizTalk, consultez [modèles de projet BizTalk Server](../core/biztalk-server-project-templates.md). Pour plus d’informations sur la création de projets BizTalk, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).  
  
> [!WARNING]
>  Il est possible d'accéder aux outils de conception BizTalk à partir d'autres systèmes de projet utilisables dans Visual Studio, mais leur comportement est imprévisible. N'utilisez le Concepteur d'orchestration, le Concepteur de pipeline, l'Éditeur BizTalk et le Mappeur BizTalk que dans le contexte d'un projet BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Orchestrations à l’aide du Concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md)   
 [Création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)   
 [Création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md)   
 [Outils de développement](../core/developer-tools.md)