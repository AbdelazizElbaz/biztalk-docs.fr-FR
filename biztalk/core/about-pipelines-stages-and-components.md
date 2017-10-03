---
title: "À propos des Pipelines, des étapes et composants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Microsoft.BizTalk.Component.Interop namespace
- pipelines, about pipelines
ms.assetid: a98e1c93-f264-4577-bd12-4430a5859e3c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 070c785924021f8e398a547c01afe969fa6430cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-pipelines-stages-and-components"></a>À propos des pipelines, des étapes et des composants
Un pipeline est une portion de l'infrastructure logicielle qui contient un ensemble de composants .NET ou COM qui traitent les messages dans un ordre prédéfini. Il divise le traitement en catégories de travail appelées étapes et détermine l'ordre d'exécution de ces étapes. Chaque étape définit des groupes de travail logiques, identifie les composants qui la constituent et détermine le mode d'exécution des composants de pipeline de cette étape.  
  
 À chaque étape, les composants de pipeline effectuent des tâches spécifiques. Par exemple, les composants des étapes d'un pipeline de réception pourront décoder, désassembler puis convertir des documents au format XML à partir d'autres formats. Pipelines d’envoi est essentiellement inverse : conversion de documents XML vers d’autres formats, assembler et chiffrer avec chaque composant de pipeline exécutant une portion de l’ensemble du processus. Bien qu'une étape soit un conteneur de composants, chaque étape est elle-même un composant avec des métadonnées. Les étapes n'ont pas de code d'exécution, contrairement aux composants de pipeline.  
  
 La figure suivante montre comment la surface de conception de pipeline illustre les pipelines. Ce pipeline comporte deux étapes : l'étape d'assemblage et l'étape de codage. Le composant de pipeline Assembleur XML a été ajouté à l’étape d’assemblage, mais la phase de codage est encore vide, car elle affiche toujours **Déposer ici !** pour indiquer qu’un composant de pipeline peut être ajouté à l’étape.  
  
 ![Étapes et les composants d’un pipeline BizTalk](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")  
Illustration des étapes et des composants d'un pipeline BizTalk  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient un ensemble de modèles de pipeline, de composants de pipeline et de pipelines par défaut. Vous pouvez créer et configurer des pipelines à l’aide de l’interface utilisateur du Concepteur de Pipeline ; vous implémentez les pipelines à l’aide de l’API dans le **Microsoft.BizTalk.Component.Interop** espace de noms. Il n'est pas possible de modifier les modèles de pipeline.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Types de Pipelines](../core/types-of-pipelines.md)  
  
-   [Types de composants de Pipeline](../core/types-of-pipeline-components.md)  
  
-   [Étapes de canalisation](../core/pipeline-stages.md)  
  
-   [Pipelines par défaut](../core/default-pipelines.md)  
  
-   [Modèles de pipeline](../core/pipeline-templates.md)  
  
-   [Composants de pipeline](../core/pipeline-components.md)  
  
-   [Résolution de schéma dans les composants de Pipeline](../core/schema-resolution-in-pipeline-components.md)  
  
-   [Utilisation d’enveloppes dans l’assembleur XML et les composants de Pipeline désassembleur](../core/envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components.md)  
  
-   [Rétrogradation de propriétés dans les composants de Pipeline assembleur](../core/property-demotion-in-assembler-pipeline-components.md)  
  
-   [Promotion des propriétés dans les composants de Pipeline désassembleur](../core/property-promotion-in-disassembler-pipeline-components.md)  
  
-   [Composants de Pipeline désassembleur les champs distinctifs](../core/distinguished-fields-in-disassembler-pipeline-components.md)