---
title: "L’analyse des schémas de fichier plat avec des enregistrements positionnels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], flat file documents
- pipeline components [custom], parsing
ms.assetid: 1ceb8c06-ac21-490e-b3d5-54e5035e5f6a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c4a6a1d5d6c263c0f794d1b703eff256f15c43b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="parsing-flat-file-schemas-with-positional-records"></a>L’analyse des schémas de fichier plat avec des enregistrements positionnels
Lorsque vous analysez un schéma de fichier plat avec des enregistrements positionnels de taille inégale, vous devez inclure une balise dans chaque enregistrement de schéma ou dans le code de fin indiquant la taille de chaque enregistrement positionnel. Sinon, le moteur d'analyse renvoie la taille d'enregistrement la plus grande.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du moteur d’analyse de fichier plat](../core/using-the-flat-file-parsing-engine.md)