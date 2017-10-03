---
title: Comptage des positions en octets | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf666ec-d15e-4d2d-9df9-49189f352c65
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3cdb7bbf1f0d6af04f0cc28ed1bdb7477b259de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="position-counting-in-bytes"></a>Comptage des positions en octets

## <a name="overview"></a>Vue d'ensemble

Vous pouvez utiliser la **compter les Positions par octet** propriété de la **schéma** nœud : 

* Spécifiez comment les valeurs que vous entrez pour le **longueur positionnelle** et **décalage de position** propriétés des différents champs dans les enregistrements positionnels sont interprétées.
* Spécifiez comment les valeurs que vous entrez pour le **décalage de la balise** propriété des enregistrements positionnels eux-mêmes sont interprétés.

Par défaut, ces valeurs sont interprétées comme un nombre de caractères. Mais lorsque le **compter les Positions par octet** est définie sur **True**, ces valeurs sont interprétées comme un nombre d’octets.  
  
 Définition de la **compter les Positions par octet** propriété **True** peut être nécessaire lors du traitement de caractères multioctets définie (MBCS ou DBCS) des données, ou lorsque vos messages de fichier plat proviennent de SAP, mainframes, ou autres systèmes susceptibles de compter les positions par octet.  
  
 Le comptage des longueurs de champ en octets peut être compliqué lorsque le nombre d'octets utilisés pour coder les caractères est variable et peut entraîner quelques problèmes pour la détermination des limites des champs. Lorsque le désassembleur de fichier plat analyse un fichier plat dans pareil cas, il tente de prendre des mesures d'analyse appropriées en fonction de sa connaissance du codage de caractères utilisé.  
  
 Un exemple de ce type de décision d'analyse est celui des octets de tête des codages de caractères MBCS. Les octets de tête sont des valeurs d'octet connues utilisées pour commencer les codages de caractères multioctet. Ils ne doivent jamais se trouver seuls. En spécifiant la longueur des champs à l'aide d'octets plutôt que de caractères, vous pourrez être confronté à des situations où le dernier octet d'un champ se révèlera être un octet de tête, qui ne pourra donc pas constituer un caractère entier à lui seul. En pareil cas, le désassembleur de fichier plat traitera le caractère précédant immédiatement l'octet de tête comme dernier caractère du champ précédent, et commencera l'analyse du champ suivant à partir de l'octet de tête.  

Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
## <a name="see-also"></a>Voir aussi  
 [Considérations concernant les enregistrements positionnels](../core/positional-record-considerations.md)   
