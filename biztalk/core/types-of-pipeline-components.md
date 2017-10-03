---
title: Types de composants de Pipeline | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: pipelines, components
ms.assetid: 9b493758-6b0f-4223-94bb-8f077ee735a9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9ba18aed137380f6b3d491ad52cfcee94bf111a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-pipeline-components"></a>Types de composants de Pipeline
Trois types de composants de pipeline sont incluses avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]: général, le désassemblage et assemblage. Chacun de ces types peut aussi implémenter une fonctionnalité de sonde. Cette rubrique décrit chaque type de composant et les étapes auxquelles chaque composant est utilisé en général.  
  
## <a name="general"></a>Général  
 Les composants généraux acceptent un message, traitent ce message et peuvent générer un message ou aucun.  
  
 Les composants généraux fournis sont les composants Décodeur MIME/SMIME, Encodeur MIME/SMIME, Résolution du tiers et Valideur. Vous pourrez être amené à créer des composants généraux personnalisés pour compresser un message avant de l'envoyer ou pour utiliser un message en attendant de disposer d'informations complémentaires pour le traiter.  
  
 Les composants généraux doivent être placés aux étapes Décoder, Encoder, Préassembler, RésoudreTiers ou Valider.  
  
 Pour plus d’informations sur le développement de composants de pipeline généraux, consultez [développement d’un composant de Pipeline général](../core/developing-a-general-pipeline-component.md).  
  
## <a name="assembling"></a>Composants d'assemblage  
 Les composants d'assemblage jouent un rôle important dans la préparation du message à envoyer. Un composant d'assemblage commence par convertir le message XML au format natif XML ou non XML approprié, en fonction du type de l'assembleur et des propriétés définies dans le schéma. De plus, les composants d'assemblage assemblent le message et lui associent une enveloppe, ou ajoutent un en-tête ou un code de fin (ou les deux) au message. Pendant l'assemblage, certaines propriétés sont transférées du contexte du message au corps du document ou à l'enveloppe.  
  
 Les composants d'assemblage par défaut sont l'Assembleur BizTalk Framework, l'Assembleur de fichier plat et l'Assembleur XML.  
  
 Les composants d'assemblage doivent être placés à l'étape d'assemblage des pipelines d'envoi.  
  
 Pour plus d’informations sur le développement de composants de pipeline d’assemblage, voir [développement d’un composant de Pipeline d’assemblage](../core/developing-an-assembling-pipeline-component.md).  
  
## <a name="disassembling"></a>Composants de désassemblage  
 Les composants de désassemblage effectuent de nombreuses tâches pour préparer le fractionnement du message en documents individuels en fonction des schémas d'enveloppe et de document et en vue d'une utilisation dans BizTalk Server. Tout d'abord, un composant de désassemblage peut convertir des messages non XML dans leur représentation XML, ce qui est nécessaire en vue d'un traitement par BizTalk Server. Ensuite, le message est désassemblé en messages simples qui peuvent être envoyés à des orchestrations distinctes. Le désassemblage consiste à retirer l'enveloppe du message, à fractionner le message en documents individuels en fonction des schémas d'enveloppe et de message, puis à transférer les propriétés de l'enveloppe vers les contextes du message. De plus, certaines propriétés peuvent être promues du corps du message vers l'en-tête. Les propriétés promues sont déterminées par le schéma.  
  
 Le composant de désassemblage doit aussi définir la propriété Type de message qui sert à router les messages correctement. Cette propriété est le Namespace#RootElement du corps du message. D'autres propriétés, comme le type de contenu et le jeu de caractères, sont définies avec la propriété de contexte.  
  
 Les composants de pipeline de désassemblage par défaut fournis avec BizTalk Server sont le Désassembleur BizTalk Framework, le Désassembleur de fichier plat et le Désassembleur XML.  
  
 Les composants de désassemblage doivent être utilisés dans l'étape de désassemblage des pipelines de réception.  
  
 Pour plus d’informations sur le développement de composants de pipeline de désassemblage, consultez [développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md).  
  
## <a name="probing"></a>Composants de sonde  
 Un composant de sonde analyse la première portion du message pour déterminer s'il comprend le format du message. Dans l'affirmative, la totalité du message est remise à ce composant pour traitement.  
  
 Pour plus d’informations sur le développement de détection des composants de pipeline, consultez [développement d’un composant de Pipeline détection](../core/developing-a-probing-pipeline-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de Pipelines](../core/types-of-pipelines.md)   
 [Pipelines par défaut](../core/default-pipelines.md)   
 [Modèles de pipeline](../core/pipeline-templates.md)   
 [Composants de pipeline](../core/pipeline-components.md)   
 [À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md)