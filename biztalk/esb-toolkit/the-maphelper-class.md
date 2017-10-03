---
title: La classe MapHelper | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c552c066-835f-4515-939f-dd465a7a5ed0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de74610c40b37560abcbce040d80320525f0a21c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-maphelper-class"></a>La classe MapHelper
Utilisez le **MapHelper** classe pour effectuer des transformations directement sans utiliser la transformation de service Web.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme d’installation installe et inscrit l’assembly **Microsof.Practices.ESB.Transform.dll** avec la **MapHelper** classe dans le global assembly cache.  
  
 Le **MapHelper** classe expose deux méthodes publiques :  
  
-   **TransformMessage**. Cette méthode prend comme paramètres une chaîne qui contient le message à transformer et une chaîne qui contient le nom qualifié complet d’un mappage déployé dans BizTalk. La méthode retourne une chaîne qui contient le document transformé.  
  
-   **TransformMessageStream**. Cette méthode prend comme paramètres un flux qui contient le message à transformer et une chaîne qui contient le nom qualifié complet d’un mappage déployé dans BizTalk. La méthode retourne une chaîne qui contient le document transformé.