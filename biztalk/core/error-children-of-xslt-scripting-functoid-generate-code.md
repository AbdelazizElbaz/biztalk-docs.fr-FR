---
title: 'Erreur : Code généré par les enfants du fonctoid script XSLT | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.xsltScriptingChildrenGenCode
ms.assetid: 9cdac362-177f-445e-904b-aa6a9b1eb46f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 810fe9befecd9bbd1a15468ca714177900450cb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---children-of-xslt-scripting-functoid-generate-code"></a>Erreur : Code généré par les enfants du fonctoid script XSLT
**Code d’erreur**  
  
 btm1063  
  
 **Explication**  
  
 Un scénario qui se révèle contradictoire avec l’utilisation d’un **script** fonctoid qui est configuré pour utiliser un modèle d’appel XSLT ou XSLT inline a été trouvé dans le mappage. Dans le schéma de destination, les descendants d’un nœud qui est lié à la sortie d’un **script** fonctoid tentent de générer leur propre code XSLT.  
  
 **Action de l’utilisateur**  
  
 Supprimer l’incompatibilité en modifiant l’utilisation de la **script** fonctoid ou modifiez les nœuds enfants, tels qu’ils ne sont plus de générer leur propre code XSLT.