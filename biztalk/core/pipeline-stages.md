---
title: Canalisation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- CATID_AssemblingSerializer component category
- CATID_Encoder component category
- pipelines, stages
- CATID_DisassemblingParser component category
- CATID_Validate component category
- ComponentCategory class attribute
- CATID_Decoder component category
- CATID_Any component category
- CATID_PartyResolver component category
- Execution Mode property
ms.assetid: ac50c48c-6ed5-4322-95cc-af55df6bcd1c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aeb675f39cb39ade4230e6e39f798e95115aaf78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pipeline-stages"></a>Étapes d'un pipeline
Cette rubrique décrit la **Mode d’exécution** affinité d’étape et de la propriété.  
  
## <a name="execution-mode-property"></a>propriété Mode Exécution  
 Pendant l'exécution d'un pipeline, les étapes d'un pipeline peuvent exécuter uniquement le premier composant qui reconnaît le format du message, ou tous les composants. La propriété qui détermine le modèle d’exécution est **Mode d’exécution**.  
  
> [!NOTE]
>  Elle est en lecture seule dans les étapes incluses dans les modèles de pipeline, mais il est important de comprendre son fonctionnement.  
  
 Lorsque le **Mode d’exécution** est définie sur **tous les**, tous les composants dans l’étape sont exécutés dans la séquence configurée. Ce mode exécute plusieurs composants pour terminer une tâche logique. Une erreur d'exécution se produit si un composant rencontre une erreur lors du traitement d'un message pendant cette étape de pipeline.  
  
 Lorsqu’un pipeline est utilisé pour recevoir des messages dans plusieurs formats, puis le **Mode d’exécution** est définie sur **PremièreCorrespondance**. Dans ce mode, seul le premier composant qui reconnaît le message est exécuté. Si aucun composant de l'étape ne reconnaît le message, une erreur d'exécution est générée.  
  
 Notez que chaque étape peut avoir son propre **Mode d’exécution** , les différentes étapes d’un pipeline peuvent avoir des modes d’exécution différents.  
  
> [!NOTE]
>  Dans cette version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], toutes les étapes dans un envoi de pipeline et toutes les étapes sauf désassembler dans un pipeline de réception ont la valeur de la **Mode d’exécution** propriété **tous les**. La valeur de la **Mode d’exécution** dans l’étape de désassemblage est définie sur **PremièreCorrespondance**. Vous ne pouvez pas modifier le **Mode d’exécution** propriété d’une étape.  
  
#### <a name="to-read-pipeline-stage-properties"></a>Pour lire les propriétés des étapes d'un pipeline  
  
1.  Dans le Concepteur de pipeline, cliquez sur une forme d'étape.  
  
2.  Dans la fenêtre Propriétés, dans le **général** section, lisez les propriétés suivantes :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Indique le nom de l'étape.|  
    |**Mode d'exécution**|Indique le modèle d'exécution de l'étape.<br /><br /> Valeurs valides : **tous les** ou **PremièreCorrespondance**|  
    |**Nombre minimal de composants**|Indique le nombre minimal de composants de pipeline pouvant être ajoutés à l'étape.|  
    |**Nombre maximal de composants**|Indique le nombre maximal de composants de pipeline pouvant être ajoutés à l'étape.|  
    |**StageID**|Indique l'identificateur unique de l'étape.|  
  
## <a name="stage-affinity"></a>Affinité d'étape  
 Les composants de pipeline ont une affinité d'étape, ce qui veut dire qu'ils sont créés pour être utilisés dans une ou plusieurs étapes particulières d'un pipeline.  
  
 Composants de pipeline COM express leur affinité d’étape en s’inscrivant avec l’ID d’étape comme catégorie d’implémentation, tandis que. Composants de pipeline NET spécifient leur affinité d’étape à l’aide de la **ComponentCategory** attribut de classe. Notez qu’il est possible qu’un composant s’associer à plusieurs étapes : composants peuvent avoir plusieurs catégories de mise en œuvre ou **ComponentCategory** attribut.  
  
 Le tableau suivant présente les catégories de composants disponibles et les étapes associées.  
  
|Catégorie de composant|Étape où le composant peut être placé| Description|  
|------------------------|-----------------------------------------|-----------------|  
|CATID_Decoder {9d0e4103-4cce-4536-83fa-4a5040674ad6}|Décoder|Tous les composants de décodage doivent implémenter cette catégorie.|  
|CATID_DisassemblingParser {9d0e4105-4cce-4536-83fa-4a5040674ad6}|Désassembler|Tous les composants de désassemblage et d'analyse doivent implémenter cette catégorie.|  
|CATID_Validate {9d0e410d-4cce-4536-83fa-4a5040674ad6}|Valider|Les composants de validation doivent implémenter cette catégorie.|  
|CATID_PartyResolver {9d0e410e-4cce-4536-83fa-4a5040674ad6}|RésoudreTiers|Étape utilisée pour le composant Résolution du tiers|  
|CATID_Encoder {9d0e4108-4cce-4536-83fa-4a5040674ad6}|Encoder|Tous les composants de codage doivent implémenter cette catégorie.|  
|CATID_AssemblingSerializer {9d0e4107-4cce-4536-83fa-4a5040674ad6}|Sérialiser|Tous les composants de sérialisation et d'assemblage doivent implémenter cette catégorie.|  
|CATID_Any {9d0e4101-4cce-4536-83fa-4a5040674ad6}|N'importe laquelle de ces étapes|Si un composant de pipeline implémente cette catégorie, cela signifie que le composant peut être placé à n'importe quelle étape d'un pipeline.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md)   
 [À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md)