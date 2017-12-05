---
title: "L’utilisation du système de projet BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Editor, opening
- BizTalk Mapper, opening
- Orchestration Designer, opening
- Pipeline Designer, opening
ms.assetid: a28c715e-128c-463a-b421-9b3efe76a530
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5b8c3a83d75219b9e52fd2ab13124480d772832
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-biztalk-project-system"></a>Utilisation du système de projet BizTalk 
Le système de projet BizTalk® permet de créer, organiser et configurer des solutions BizTalk dans l'environnement Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Les rubriques et les procédures de cette section expliquent comment effectuer diverses tâches à l'aide du système de projet BizTalk.  
  
 Le système de projet BizTalk Server utilise les mêmes principes de gestion de projet et les procédures que vous utilisez avec d’autres projets Microsoft Build Engine (MSBuild) dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Cette section détaille les procédures courantes que vous serez éventuellement amené à utiliser pour créer une application s'exécutant sur Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour plus d’informations sur MSBuild, consultez la section de référence MSBuild dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection combinée à [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).  
  
 Pour plus d’informations sur l’utilisation de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environnement, consultez « Gestion des Solutions, projets et fichiers » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection combinée à [http://msdn.microsoft.com/library/wbzbtw81.aspx](http://msdn.microsoft.com/library/wbzbtw81.aspx).  
  
 L’illustration suivante montre l’environnement de conception de système de projet BizTalk avec le **nouveau projet** boîte de dialogue ouverte.  
  
 ![Systèmes de projet](../core/media/bts-biztalk2009-projectsystems.gif "bts_BizTalk2009_ProjectSystems")  
Représentation de l'environnement de conception du système de projet  
  
### <a name="to-open-biztalk-editor"></a>Pour ouvrir l'Éditeur BizTalk  
  
1.  Dans l'Explorateur de solutions, cliquez sur un schéma.  
  
    > [!NOTE]
    >  Pour ouvrir l'Éditeur BizTalk, vous devez d'abord créer un schéma ou ouvrir un schéma créé au préalable. Pour plus d’informations sur la création d’un schéma, consultez [comment créer les schémas des Messages XML](../core/how-to-create-schemas-for-xml-messages.md). Consultez également [Ajout des éléments de projet](../core/adding-project-items.md).  
  
2.  Sur le **vue** menu, cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Cliquez sur le schéma, puis cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Double-cliquez sur le schéma.  
  
     Le schéma sélectionné s'ouvre dans l'Éditeur BizTalk.  
  
    > [!NOTE]
    >  Si vous voulez créer un schéma, un projet doit être ouvert. Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md). Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [comment créer les schémas des Messages XML](../core/how-to-create-schemas-for-xml-messages.md). Consultez également [Ajout des éléments de projet](../core/adding-project-items.md).  
  
### <a name="to-open-biztalk-mapper"></a>Pour ouvrir le Mappeur BizTalk  
  
1.  Dans l'Explorateur de solutions, cliquez sur un mappage.  
  
    > [!NOTE]
    >  Pour ouvrir le Mappeur BizTalk, vous devez d'abord créer un mappage ou ouvrir un mappage créé au préalable. Pour plus d’informations sur la création d’un mappage, consultez [comment créer de nouveaux mappages](../core/how-to-create-new-maps.md). Consultez également [Ajout des éléments de projet](../core/adding-project-items.md).  
  
2.  Sur le **vue** menu, cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Avec le bouton droit de la carte, puis cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Double-cliquez sur un mappage.  
  
     Le mappage sélectionné s'ouvre dans le Mappeur BizTalk.  
  
    > [!NOTE]
    >  Si vous voulez créer un mappage, un projet doit être ouvert. Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md). Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [Ajout des éléments de projet](../core/adding-project-items.md). Consultez également [comment créer de nouveaux mappages](../core/how-to-create-new-maps.md).  
  
### <a name="to-open-orchestration-designer"></a>Pour ouvrir le Concepteur d'orchestration  
  
1.  Dans l'Explorateur de solutions, cliquez sur une orchestration (.odx).  
  
    > [!NOTE]
    >  Pour ouvrir le Concepteur d'orchestration, vous devez d'abord créer une orchestration ou ouvrir une orchestration créée au préalable. Pour plus d’informations sur la création d’une orchestration, consultez [dans le Concepteur d’Orchestration](../core/working-in-orchestration-designer.md).  
  
2.  Sur le **vue** menu, cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Avec le bouton droit de l’orchestration, puis cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Double-cliquez sur l'orchestration.  
  
     Le Concepteur d'orchestration s'ouvre.  
  
    > [!NOTE]
    >  Si vous voulez créer une orchestration, un projet doit être ouvert. Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md). Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [Ajout des éléments de projet](../core/adding-project-items.md). Consultez également [dans le Concepteur d’Orchestration](../core/working-in-orchestration-designer.md).  
  
### <a name="to-open-pipeline-designer"></a>Pour ouvrir le Concepteur de pipeline  
  
1.  Dans l'Explorateur de solutions, cliquez sur un pipeline.  
  
    > [!NOTE]
    >  Pour ouvrir le Concepteur de pipeline, vous devez d'abord créer un pipeline ou ouvrir un pipeline créé au préalable. Pour plus d’informations sur la création d’un pipeline, consultez [comment créer un Pipeline](../core/how-to-create-a-new-pipeline.md).  
  
2.  Sur le **vue** menu, cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Le pipeline d’avec le bouton droit, puis cliquez sur **ouvrir**.  
  
     — Ou :  
  
     Double-cliquez sur le pipeline.  
  
     Le Concepteur de pipeline s'ouvre.  
  
    > [!NOTE]
    >  Si vous voulez créer un pipeline, un projet doit être ouvert. Pour plus d’informations sur la création d’un projet, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md). Pour plus d’informations sur l’ajout d’éléments à un projet, consultez [Ajout des éléments de projet](../core/adding-project-items.md). Consultez également [dans le Concepteur d’Orchestration](../core/working-in-orchestration-designer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Orchestrations à l’aide du Concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md)   
 [À l’aide du Concepteur de Pipeline](../core/using-pipeline-designer.md)   
 [Fenêtres de l’éditeur des règles d’entreprise](../core/windows-of-the-business-rule-composer.md)   
 [À l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md)   
 [À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md)   
 [Outils de développement](../core/developer-tools.md)