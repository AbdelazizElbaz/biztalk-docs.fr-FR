---
title: "Ajout d’éléments de projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, orchestrations
- projects, schemas
- projects, files
- projects, pipelines
- projects, maps
ms.assetid: d1b922d5-8ece-4e1a-a390-e6ae1222665a
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfb6aaa0a00488c1181d440e0ce7e5777ef4477d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-project-items"></a>Ajout d’éléments de projet
Dans le contexte d'un système de projet BizTalk, un élément de projet est un élément configuré, comme un mappage ou un schéma. Une application BizTalk pourra contenir un ou plusieurs schémas, orchestrations, mappages et pipelines.  
  
> [!NOTE]
>  Quand vous ajoutez un élément à un projet, n'utilisez pas de point (.) dans le nom de l'élément, car ce symbole est un séparateur pour l'espace de noms .NET. Si vous mettez un point dans le nom d'un élément, le nom de type de l'élément contient un trait de soulignement (_) à la place d'un point.  
  
> [!NOTE]
>  Lorsque vous ajoutez un schéma, le mappage ou le pipeline dans un dossier, le **nom complet** propriété est générée automatiquement et inclut l’espace de noms et le type.  
  
## <a name="orchestrations"></a>Orchestrations  
 Une orchestration est une représentation d'un processus d'entreprise exprimée dans le langage XLANG/s. XLANG/s est une variante mise à jour du langage XML (XLANG) introduite dans Microsoft [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]. XLANG/s peut être utilisé pour compléter les langages procéduraux existants tels que Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] et Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)].  
  
 Vous pouvez vous servir du Concepteur d'orchestration pour créer les orchestrations que vous souhaitez inclure dans un projet BizTalk. Toutes les orchestrations que vous créez dans le Concepteur d'orchestration sont pourvues de l'extension .odx.  
  
## <a name="schemas"></a>Schémas  
 Un schéma est la définition de la structure d'un document ou d'un message. Il contient des informations sur les propriétés des enregistrements et des champs de la structure. Le cas échéant, un schéma peut contenir plusieurs sous-schémas.  
  
 Vous pouvez utiliser l'Éditeur BizTalk pour importer, modifier ou créer des schémas. Vous pouvez ensuite utiliser les schémas que vous créez pour générer des mappages dans le Mappeur BizTalk. Tous les schémas que vous enregistrez à l'aide de l'Éditeur BizTalk sont pourvus de l'extension de fichier .xsd.  
  
 Pour plus d’informations sur les schémas et de l’Éditeur BizTalk, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md).  
  
## <a name="maps"></a>Cartes  
 Un mappage est un fichier XML qui définit la relation entre les enregistrements et champs de deux schémas. Vous créez des mappages en vous basant sur les normes de l'industrie, sur d'autres normes (normes internes ou questions juridiques) ou sur des fichiers existants. Vous créez des mappages quand vous voulez convertir les données que vous recevez ou envoyez d'un format dans un autre. Vous pouvez utiliser le Mappeur BizTalk pour créer les mappages que vous inclurez dans un projet BizTalk. Tous les mappages que vous enregistrez dans le Mappeur BizTalk sont pourvus de l'extension .btm. Pour plus d’informations sur le Mappeur BizTalk, consultez [création de mappages à l’aide du mappeur de BizTalk](../core/creating-maps-using-biztalk-mapper.md).  
  
## <a name="pipelines"></a>Pipelines  
 Vous pouvez utiliser le Concepteur de pipeline pour créer des pipelines de réception et d'envoi. Un pipeline est une infrastructure logicielle qui définit et relie une ou plusieurs étapes de traitement des messages reçus ou envoyés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les pipelines implémentent les étapes dans un ordre précis et incluent des fonctions comme le codage ou le décodage, l'assemblage ou le désassemblage et le chiffrement ou le déchiffrement.  
  
 Les pipelines par défaut inclus dans un projet BizTalk ne peuvent traiter que des documents XML. Si vous voulez traiter des fichiers plats, des documents EDI ou d'autres types de fichiers, vous devez créer les pipelines appropriés. Tous les pipelines créés avec le Concepteur de pipeline ont une extension .btp. Pour plus d’informations sur les pipelines et le Concepteur de Pipeline, consultez [création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md).  
  
## <a name="valid-files-for-biztalk-projects"></a>Fichiers valides pour les projets BizTalk  
 Quand vous travaillez sur un projet BizTalk, vous pouvez inclure de nombreux fichiers différents comme des fichiers HTML, des fichiers XML, des fichiers de pipeline de réception et des fichiers de schéma. Avant la publication de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009, lorsque vous créiez un projet BizTalk dans un assembly, seuls les types de fichiers suivants étaient inclus dans l'assembly : orchestrations, schémas, mappages, et pipelines. Depuis la publication de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009, l'assembly peut désormais contenir tout objet supporté par le système version [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des projets BizTalk](../core/working-with-biztalk-projects.md)