---
title: "Imbriqué enregistrements positionnels et délimités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1688f04-d3c7-492c-82f7-a734bec0e409
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccc3d994a3561f26df1bdffa7b547b1f647936a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nested-positional-and-delimited-records"></a>Enregistrements positionnels et délimités imbriqués
Dans les formats de fichier plat pris en charge par Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], certaines combinaisons d'enregistrements positionnels et délimités sont autorisées et d'autres non. Les combinaisons suivantes sont autorisées :  
  
-   Les fichiers plats dans lesquels des délimiteurs sont utilisés pour déterminer les limites entre tous les enregistrements et leurs enregistrements subordonnés entre eux, et dans lesquels des délimiteurs (éventuellement différents) sont utilisés pour séparer les champs de ces enregistrements.  
  
-   Les fichiers plats dans lesquels les limites entre tous les enregistrements, leurs enregistrements subordonnés et leurs champs sont déterminées sur la base de leur position dans le fichier, selon des longueurs d'enregistrement et de champ prédéfinies.  
  
-   Les fichiers plats dans lesquels des délimiteurs sont utilisés pour déterminer les limites entre au moins l'ensemble d'enregistrements le plus externe dans le fichier, et dans lesquels une combinaison d'enregistrements subordonnés délimités et positionnels est utilisée. Les limites entre les champs d'un enregistrement subordonné délimité ou positionnel sont déterminées en utilisant des délimiteurs ou des longueurs de champ fixes respectivement. Les enregistrements subordonnés d'un enregistrement (subordonné) positionnel doivent également être positionnels. En d'autres termes, une fois qu'une partie du fichier passe d'enregistrements délimités à des enregistrements positionnels, l'ensemble de cette partie subordonnée du fichier doit être positionnelle.  
  
 En raison des ambiguïtés d'analyse qui pourraient en résulter, les enregistrements positionnels, où qu'ils aient lieu, ne doivent en aucune façon contenir des enregistrements subordonnés délimités.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations relatives à la création de plat fichier schémas de Message](../core/considerations-when-creating-flat-file-message-schemas.md)