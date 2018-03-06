---
title: "Ajouter des éléments de projet | Documents Microsoft"
description: "Ajouter des orchestrations, schémas, mappages et pipelines à votre projet BizTalk Server dans Visual Studio"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1b922d5-8ece-4e1a-a390-e6ae1222665a
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef998865a1851e546a3648b60e0141b3cd137c1b
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="add-project-items"></a>Ajouter des éléments de projet
Dans le contexte d'un système de projet BizTalk, un élément de projet est un élément configuré, comme un mappage ou un schéma. Une application BizTalk pourra contenir un ou plusieurs schémas, orchestrations, mappages et pipelines.  
  
> [!NOTE]
>  Quand vous ajoutez un élément à un projet, n'utilisez pas de point (.) dans le nom de l'élément, car ce symbole est un séparateur pour l'espace de noms .NET. Si vous mettez un point dans le nom d'un élément, le nom de type de l'élément contient un trait de soulignement (_) à la place d'un point.  
  
> [!NOTE]
>  Lorsque vous ajoutez un schéma, le mappage ou le pipeline dans un dossier, le **nom complet** propriété est générée automatiquement et inclut l’espace de noms et le type.  
  
## <a name="orchestrations"></a>Orchestrations  
 Une orchestration est une représentation d'un processus d'entreprise exprimée dans le langage XLANG/s. XLANG/s peut être utilisé pour compléter les langages procéduraux existants tels que Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] et Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)].  
  
 Vous pouvez vous servir du Concepteur d'orchestration pour créer les orchestrations que vous souhaitez inclure dans un projet BizTalk. Toutes les orchestrations que vous créez dans le Concepteur d'orchestration sont pourvues de l'extension .odx.  
  
## <a name="schemas"></a>Schémas  
 Un schéma est la définition de la structure d'un document ou d'un message. Il contient des informations sur les propriétés des enregistrements et des champs de la structure. Le cas échéant, un schéma peut contenir plusieurs sous-schémas.  
  
 Vous pouvez utiliser l'Éditeur BizTalk pour importer, modifier ou créer des schémas. Vous pouvez ensuite utiliser les schémas que vous créez pour générer des mappages dans le Mappeur BizTalk. Tous les schémas que vous enregistrez à l'aide de l'Éditeur BizTalk sont pourvus de l'extension de fichier .xsd.  
  
 Pour plus d’informations sur les schémas et de l’Éditeur BizTalk, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md).  
  
## <a name="maps"></a>Cartes  
 Un mappage est un fichier XML qui définit la relation entre les enregistrements et champs de deux schémas. Vous créez des mappages en vous basant sur les normes de l'industrie, sur d'autres normes (normes internes ou questions juridiques) ou sur des fichiers existants. Vous créez des mappages quand vous voulez convertir les données que vous recevez ou envoyez d'un format dans un autre. Vous pouvez utiliser le Mappeur BizTalk pour créer les mappages que vous inclurez dans un projet BizTalk. Tous les mappages que vous enregistrez dans le Mappeur BizTalk sont pourvus de l'extension .btm. Pour plus d’informations sur le Mappeur BizTalk, consultez [création de mappages à l’aide du mappeur de BizTalk](../core/creating-maps-using-biztalk-mapper.md).  
  
## <a name="pipelines"></a>Pipelines  
 Vous pouvez utiliser le Concepteur de pipeline pour créer des pipelines de réception et d'envoi. Un pipeline est une infrastructure logicielle qui définit et relie une ou plusieurs étapes du traitement des messages reçus ou envoyés par BizTalk Server. Les pipelines implémentent les étapes dans un ordre précis et incluent des fonctions comme le codage ou le décodage, l'assemblage ou le désassemblage et le chiffrement ou le déchiffrement.  
  
 Les pipelines par défaut inclus dans un projet BizTalk ne peuvent traiter que des documents XML. Si vous voulez traiter des fichiers plats, des documents EDI ou d'autres types de fichiers, vous devez créer les pipelines appropriés. Tous les pipelines créés avec le Concepteur de pipeline ont une extension .btp. Pour plus d’informations sur les pipelines et le Concepteur de Pipeline, consultez [création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md).  
  
## <a name="valid-files-for-biztalk-projects"></a>Fichiers valides pour les projets BizTalk  
 Quand vous travaillez sur un projet BizTalk, vous pouvez inclure de nombreux fichiers différents comme des fichiers HTML, des fichiers XML, des fichiers de pipeline de réception et des fichiers de schéma. Avec BizTalk Server, l’assembly peut contenir n’importe quel objet pris en charge par le système de génération Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des projets BizTalk](../core/working-with-biztalk-projects.md)