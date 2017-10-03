---
title: "Erreur : lien de sortie pour le fonctoid script XSLT non valide. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.outputLinkForXsltNotValid
ms.assetid: cdf8e779-6cf6-4d9c-8655-f8b406498fb7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd597a3953db76087086c7ea9038e9fa1fd87eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---output-link-for-xslt-scripting-functoid-not-valid"></a>Erreur : lien de sortie pour le fonctoid script XSLT non valide
**Code d’erreur**  
  
 btm1075  
  
 **Explication**  
  
 Le lien de sortie de la **script** configuré pour utiliser un modèle d’appel XSLT ou XSLT inline ne sont pas valides. La sortie de ces **script** fonctoids doivent être connectés directement à un nœud dans le schéma de destination (et non à un autre fonctoid, par exemple).  
  
 **Action de l’utilisateur**  
  
 Vérifiez que vous vous connectez le lien de sortie à partir de la **script** fonctoid directement à un nœud dans le schéma de destination.