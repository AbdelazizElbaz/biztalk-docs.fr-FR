---
title: Erreur - Max de la propriété promue | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.promoPropMaxOccurs
ms.assetid: fc07367e-40f2-46e9-aeeb-bfa2498b1b37
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c8395757d19eff5241d47c31b15409a00b6faf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---promoted-property-max-occurs"></a>Erreur - Max de la propriété promue
**Code d’erreur**  
  
 BEC2002  
  
 **Explication**  
  
 Le paramètre de la **Max Occurs** propriété du nœud en cours de promotion, ou de l’un de ses nœuds ancêtres, n’est pas compatible avec la promotion de propriété. La promotion de propriétés n'est pas possible pour les nœuds pouvant apparaître plusieurs fois dans un message d'instance. Par conséquent, le **Max Occurs** propriétés de tous les nœuds à partir du nœud en cours de promotion et le nœud racine doivent être définies sur 1.  
  
 **Action de l’utilisateur**  
  
 Vérifiez que le **Max Occurs** du nœud en cours de promotion et tous ses nœuds de niveau supérieur est définie sur un (1).