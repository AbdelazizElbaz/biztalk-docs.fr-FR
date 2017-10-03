---
title: Gestion des Exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, handlers
- scopes, errors
- errors, scopes
- handlers [adapters], errors
ms.assetid: 30b88d8a-8737-4700-b856-1b49fdf6b6d0
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 004e4f29bcfc292edb33bae816a52b588a89771c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-exceptions-are-handled"></a>Gestion des Exceptions 
Lorsqu’une exception se produit dans une étendue, chaque thread d’exécution logique présent de l’étendue est arrêté. Le moteur d'exécution recherche un gestionnaire d'exceptions pour l’exception appropriée.  
  
 Si le gestionnaire d’exception trouvé correspond au type spécifique ou à un de ses types de base, le contrôle est transmis au gestionnaire et son code est exécuté.  
  
> [!NOTE]
>  Le type d’exception doit être dérivé **System.Exception**.  
  
 Les gestionnaires d’exception sont séquentiels ; c’est-à-dire qu’ils feront l’objet d’une vérification afin de déterminer s’ils peuvent ou non gérer une exception particulière. Pour qu’ils fonctionnent correctement, les gestionnaires d’exception doivent être placés de telle sorte que ceux qui assurent la gestion de types spécifiques arrivent en premier, suivi de ceux qui gèrent les types plus généraux. Cela permet de garantir qu'une exception d'un type spécifique est gérée par le gestionnaire approprié, et non par un gestionnaire conçu pour gérer un type de base.  
  
 Si le gestionnaire d’exception fonctionne normalement, le contrôle est transmis à l'étendue voisine. Si aucune exception n’est émise dans l'étendue voisine, l'exécution de l'orchestration se poursuit. Si le gestionnaire d’exception se termine par une instruction throw, l'exception d'origine est à nouveau émise pour agir sur l’étendue voisine, sauf si vous avez précisé qu’une exception différente doit être émise.  
  
 Si aucun gestionnaire ne peut être localisé, le gestionnaire d'exceptions par défaut est exécuté. Le gestionnaire d’exception par défaut pour une étendue appellera les compensations pour toutes les transactions imbriquées, puis émettra à nouveau l'exception. Si vous écrivez votre propre gestionnaire d'exception, vous pouvez choisir de ne pas propager l’exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Exceptions](../core/exceptions.md)