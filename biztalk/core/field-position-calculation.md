---
title: Calcul de la Position de champ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e315f09-f2c9-49cc-8d2f-0f4f2d48fd45
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55c58f532ea64300518667d677d2248f5c1c2b6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-position-calculation"></a>Calcul de Position de champ

## <a name="overview"></a>Vue d'ensemble
Lorsque vous utilisez la **longueur positionnelle** et **décalage de position** propriétés de la **élément de champ** et **attribut de champ** nœuds dans votre schéma pour définir la disposition des enregistrements positionnels dans votre message de fichier plat, le **Position de début** et **longueur** les colonnes de la **fichier plat** onglet L’Éditeur BizTalk affiche les positions de départ calculées et les longueurs, respectivement, des enregistrements et champs appropriés.  
  
> [!NOTE]
>  Le **fichier plat** onglet apparaît sous la forme d’une autre vue à onglets avec la vue XSD dans l’Éditeur BizTalk vous avez configuré l’extension de fichier plat à l’aide de la **Extensions de l’éditeur de schéma** propriété de la **Schéma** nœud. Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 En général, la position de départ d’un champ particulier *N* est la position de départ du champ précédent, plus la longueur de champ précédent, plus le décalage (positionnel) que vous avez spécifié pour le champ *N*.  
  
 Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], tous les calculs de position des champs sont effectués automatiquement, immédiatement, sans qu'il faille exécuter une commande (comme c'était le cas dans les précédentes versions de BizTalk Server).  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations concernant les enregistrements positionnels](../core/positional-record-considerations.md)   
-  **Longueur positionnelle (propriété de nœud des schémas de fichier plat)** et **le décalage de position (propriété de nœud des schémas de fichier plat)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]