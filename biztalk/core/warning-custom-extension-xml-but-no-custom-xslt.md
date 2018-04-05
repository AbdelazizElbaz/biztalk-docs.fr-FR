---
title: 'Avertissement : XML avec extensions personnalisées, mais aucun XSLT personnalisé | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.warning.customExtensionXmlButNoCustomXSLT
ms.assetid: 3219c73c-2e58-4fe2-bc6e-2d60348d2415
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b626f8ede3231c04ae74dc0097cbdf524c90522
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---custom-extension-xml-but-no-custom-xslt"></a>Avertissement : XML avec extensions personnalisées, mais aucun XSLT personnalisé
**Code d’erreur**  
  
 btm1033  
  
 **Explication**  
  
 Le **XML avec extensions personnalisées** propriété a été remplacée, mais pas les **chemin du XSLT personnalisé** propriété substituée. Si cela est intentionnel, ne tenez pas compte de cet avertissement.  
  
 Le Mappeur BizTalk va utiliser l'élément XSLT produit lors de la compilation du mappage, puis va générer l'élément XML avec extensions qui sera ensuite ajouté à l'élément XML avec extensions personnalisées remplacé. Cela peut être utile lorsque le mappage contient **script** modèles qui effectuent des appels à une ou plusieurs méthodes dans les assemblys externes d’appel de fonctoids qui utilisent inline XSLT ou XSLT inline. Dans ce cas, l’utilisateur peut alors affecter le préfixe au mappage de nom d’assembly dans le **XML avec extensions personnalisées** propriété.  
  
 **Action de l’utilisateur**  
  
 Si la condition indiquée par cet avertissement n’est pas intentionnelle, vous devez attribuer une valeur compatible à la **chemin du XSLT personnalisé** propriété ou supprimez la valeur de remplacement pour le **XML avec extensions personnalisées** propriété.