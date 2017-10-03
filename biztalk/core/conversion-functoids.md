---
title: Fonctoids de conversion | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0cd7abcf-f524-4e85-b8d5-d6123767490f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 192db4b03f80674f2eb90be2255a8682454bde2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conversion-functoids"></a>Fonctoids de conversion

## <a name="overview"></a>Vue d'ensemble
**Conversion** fonctoids sont utilisés pour effectuer une conversion entre les nombres et leurs équivalents ASCII et à convertir en base 10 numéros à leur base 8 et 16 équivalents de base.  
  
 Tous les fonctoids de conversion ne prennent qu'un seul paramètre d'entrée.  
  
> [!NOTE]
>  En raison de modifications dans le système de type sous-jacent, les **Conversion** fonctoids dans cette version du Mappeur BizTalk produisent des résultats légèrement différents que celles produites dans les versions précédentes. Par exemple, dans les versions précédentes du Mappeur BizTalk, une valeur d’entrée de -20 à la **hexadécimal** fonctoid a généré en sortie 0xFFEC. Dans cette version, cette même valeur d'entrée de -20 donne en sortie 0xFFFFFFEC.  

## <a name="available-functoids"></a>Fonctoids disponibles  
 Le **Conversion** fonctoids sont : 

* ASCII vers caractère
* Caractère vers ASCII
* Valeur hexadécimale
* Octal

Ces fonctoids sont décrites [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 

## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids de base à une carte](../core/how-to-add-basic-functoids-to-a-map.md)   
