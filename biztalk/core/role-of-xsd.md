---
title: "Rôle du langage XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fe08f6b-563f-4bae-a5be-551e487b2a6d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad2f99b60de5ebb2a3cd7e102a2f3f7b787d1ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="role-of-xsd"></a>Rôle du langage XSD
Le langage XSD (XML Schema definition) fournit la syntaxe sous-jacente des schémas de message définis dans BizTalk. Bien que les arborescences de l’Éditeur et du Mappeur BizTalk utilisent une hiérarchie graphique propre à BizTalk pour les nœuds d'enregistrement et de champ (entre autres types de nœuds), chacune associée à son propre ensemble de propriétés, de telles hiérarchies sont élaborées et conservées au format XSD. L’Éditeur BizTalk fournit une vue XSD en lecture seule dans laquelle vous pouvez voir le XSD construit lorsque différents nœuds sont ajoutés ou supprimés de la représentation graphique du schéma dans la vue de l’arborescence et lors de la modification des valeurs des propriétés associées à ces nœuds. Bien qu'il ne soit généralement pas nécessaire de comprendre les détails de XSD pour créer correctement des schémas simples avec l’Éditeur BizTalk, si vous étudiez les modifications XSD à mesure que vous apportez des modifications à la hiérarchie de schéma dans la vue d'arborescence, vous apprendrez à utiliser XSD.  
  
 Le composant d'annotation de schéma dans XSD, associé au large éventail d’annotations définies par BizTalk Server, permet d’étendre XSD efficacement afin qu'il prenne en charge la sémantique nécessaire à la représentation des messages non XML tels que les fichiers plats.  
  
## <a name="see-also"></a>Voir aussi  
 [Ressources XSD sur le Web](../core/xsd-resources-on-the-web.md)   
 [À propos des schémas](../core/about-schemas.md)