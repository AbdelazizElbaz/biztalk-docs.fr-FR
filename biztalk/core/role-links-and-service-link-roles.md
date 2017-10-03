---
title: "Liens de rôle et le Service de rôles lier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, orchestrations
- service link roles
- role links
- roles, orchestrations
- roles
- roles, about roles
- service link roles, about service link roles
- orchestrations, roles
- role links, about role links
- orchestrations, deleting
ms.assetid: 23b4ca34-a1a5-44d4-a50d-661277681c72
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6630b1ad22ba86f3efe8a19409f3b731880c8a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="role-links-and-service-link-roles"></a>Liens de rôle et rôles de lien de service
A *rôle* est une collection de types de port qui utilise un service ou implémente un service. Un rôle représente le type d’interaction qu’un tiers peut avoir avec une ou de nombreuses orchestrations. Les rôles confèrent une flexibilité et une facilité de gestion à mesure que le nombre de tiers augmente. Par exemple, une orchestration peut revêtir le rôle d'un Expéditeur. Un ou deux tiers sont associés à ce rôle. Lorsque l'orchestration choisit la société de transport à utiliser pour un élément, elle compare le prix des tiers dans le rôle Expéditeur.  
  
 A *type de lien de rôle* est une propriété qui représente la relation entre deux services ou orchestrations. Il définit le rôle joué par chaque service dans la relation et spécifie les types de ports fournis par chaque rôle.  
  
 Un tiers, ou unité d'organisation, représente une entité, en dehors de BizTalk Server, qui interagit avec une orchestration. Dans BizTalk Server, chaque organisation avec laquelle vous échangez des messages est représentée par un tiers. Vous pouvez définir de quelle façon le tiers interagira en l'inscrivant dans un rôle.  
  
 Vous pouvez déployer ou supprimer un type de lien de rôle lorsqu'il est associé à une orchestration.  
  
## <a name="orchestrations-and-roles"></a>Orchestrations et rôles  
 Lorsque vous déployez une orchestration qui utilise un type de lien de rôle, la base de données de configuration enregistre le rôle. Étant donné qu'un rôle peut être utilisé par plusieurs orchestrations, la base de données de gestion n'enregistre qu'une copie du type de lien de rôle.  
  
 Si votre projet BizTalk contient deux types de liens de rôle dans des fichiers d'orchestration distincts (.odx) qui portent le même nom et espace de noms, votre projet BizTalk n'est pas compilé.  
  
### <a name="orchestration-removals-that-use-roles"></a>Suppressions d'orchestration qui utilisent des rôles  
 Étant donné qu'un type de lien de rôle peut être utilisé par plusieurs orchestrations, lorsque vous annulez le déploiement d'un assembly qui contient une orchestration utilisant un rôle, la base de données de gestion ne supprime le rôle que si aucune autre orchestration ne l'utilise.  
  
 Par ailleurs, la base de données de gestion ne supprime un rôle que si aucun tiers n'est inscrit auprès de lui. De même que vous ne pouvez pas remplacer un rôle auprès duquel des tiers sont inscrits, vous ne pouvez pas non plus en supprimer.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md)   
 [Artefacts](../core/artifacts.md)