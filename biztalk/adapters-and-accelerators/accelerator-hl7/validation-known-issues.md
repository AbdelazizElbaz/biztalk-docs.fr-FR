---
title: "Problèmes connus de validation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- known issues, validating
- validating, known issues
ms.assetid: 136596f2-ee0f-4ea9-918c-3608f2ee1be3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69400c5196b31a53d49055e500356c7ce3430e58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-known-issues"></a>Problèmes connus de validation
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs de validation.  
  
## <a name="disabling-xml-validation"></a>La désactivation de la validation XML  
 Les Segments valider de corps » » indicateur de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration de l’Explorateur de contrôle de la validation du corps XML et n’inclut pas de validation des délimiteurs inattendues et des délimiteurs de fin. Si un message n’a pas de séparateurs appropriés, le message ne peut pas correctement analysé. Si un message ne peut pas être analysé avec succès, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Impossible de générer le fichier XML intermédiaire valid. La désactivation de l’indicateur « Valider des Segments de corps » renvoie les éléments suivants :  
  
1.  Champs obligatoires vides.  
  
2.  Types de données n’a ne pas validés.  
  
3.  Structure de segment n’est pas validé (ordre des segments n’est pas validé).  
  
## <a name="v2xml-acks-with-multiple-errors-will-fail-validation"></a>V2. Accusés de réception XML avec plusieurs erreurs échoue la validation  
 Si un V2 entrant. Message XML contient plusieurs erreurs, la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) analyseur peut générer un V2. XML accusé de réception (ACK) avec plusieurs erreurs dans le champ d’erreur. Une telle V2. XML ACK validation échoue, étant donné que la norme HL7 Spécifie que l’analyseur peut signaler qu’une erreur dans un V2. Champ d’erreur XML ACK.  
  
## <a name="two-parsing-errors-are-logged-when-messages-in-the-batch-inbatch-out-scenario-contain-validation-errors"></a>Deux erreurs d’analyse sont enregistrés lorsque les messages du lot dans / scénario hors lot contiennent des erreurs de validation  
 Lorsque le premier message dans le lot dans / scénario de lot Out (plusieurs messages traités par lot sans en-têtes de lot) contient des erreurs de validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ouvre deux erreurs dans le journal des événements. La première erreur concernant le premier message dans le lot, et la deuxième erreur relative au reste des messages.  
  
## <a name="restrictions-in-validating-field-length"></a>Restrictions de validation de longueur de champ  
 Champs associés HL7 types de données complexes sont constituées de composants et les sous-composants. Les règles de HL7 spécifient la longueur et le caractère facultatif au niveau du champ et non au niveau du composant/sous-composant. Par exemple dans la version V2.4, HL7 régit MSH3 pour être de type de données HD et dépasser 180 caractères. HD est un type de données composites avec HD1 ensemble en l’état, HD2 ensemble en tant que ST et ensemble HD3 comme code. La restriction de longueur de champ implique que les données dans les trois composants (y compris les séparateurs de deux composants) doivent être inférieure ou égale à 180. Toutefois, le caractère facultatif des trois types de données n’est pas spécifié ; ce qui signifie que la totalité ou une partie des composants peuvent exister. En outre, les types de données ST et IS sont définis par l’utilisateur et par conséquent [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne peut pas être informé de la distribution de longueur parmi les trois composants, car il s’agit normalement de site défini.  
  
 En raison de ces et d’autres complications, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne valide pas la longueur de champ. Toutefois, vous pouvez appliquer des restrictions de longueur à chaque composant/sous-composant individuel (de simple de type de données) à l’aide de l’Éditeur BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]pendant le traitement valide.  
  
## <a name="validation-of-batch-and-file-headerstrailers-are-affected-by-enabling-fragmentation"></a>Validation du lot et le fichier en-têtes/codes de fin sont affectées par l’activation de la fragmentation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]ne valide pas les en-têtes de lot et le fichier/codes lorsque le champ FHS3 contient un tiers qui a activé la fragmentation.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)