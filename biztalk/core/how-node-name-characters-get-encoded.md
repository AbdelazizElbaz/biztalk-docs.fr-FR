---
title: "Comment les caractères de nom de nœud codés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6462856b-7a52-40c9-9aff-c0579130eec9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d2c9410e56b2b50a32ec73ce5f49ae59909f59a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-node-name-characters-get-encoded"></a>Codage des caractères des noms de nœud
Si vous utilisez un caractère qui n’est pas autorisé dans un nom de nœud, l’Éditeur BizTalk vous invite à entrer vous demande si vous voulez poursuivre l’ou les caractères encodés non autorisée (**OK** ou **Annuler**). Si vous en décidez ainsi, chaque caractère non autorisé est codé comme indiqué ci-dessous :  
  
-   Caractères non autorisés sont codés en tant que « _xDDDD\_» où « DDDD » est la représentation Unicode hexadécimale de 4 chiffres du caractère. Par exemple, le caractère espace (0 x 0020) est encodé comme « _x0020\_».  
  
-   Si au moins deux caractères adjacents non autorisés sont codés, un seul caractère de soulignement est placé entre eux. Par exemple, trois espaces sont encodés en tant que « _x0020_x0020_x0020\_» plutôt que « _x0020\__x0020\__x0020\_».  
  
> [!NOTE]
>  Vous pouvez désactiver les invites pour le codage d’un nom de nœud en définissant le **afficher Encoder boîte de dialogue Avertissement** propriété **False** dans le dossier de l’Éditeur BizTalk de la **Options** boîte de dialogue disponible sur le **outils** menu, ou en sélectionnant le **ne plus afficher cette boîte de dialogue** case à cocher dans la boîte de dialogue de codage le nom du nœud. Pour plus d’informations sur les options de cette boîte de dialogue, consultez [la gestion de l’arborescence du schéma](../core/how-to-manage-the-schema-tree-view.md).  
  
 Dans l'Éditeur BizTalk, l'arborescence des schémas affiche les noms de nœud en utilisant les caractères que vous tapez. Le Mappeur BizTalk affiche également les caractères tapés plutôt que la version codée. Dans la vue XSD de l'Éditeur BizTalk et dans le fichier XSD lui-même, le nom de nœud codé est utilisé. Par exemple, si vous donnez à un nœud le nom Bon de commande, il s'affichera tel quel dans les arborescences de schéma de l'Éditeur BizTalk et du Mappeur BizTalk. Dans la vue XSD de l'Éditeur BizTalk, le nœud d'élément correspondant prendra la forme suivante lorsqu'il sera inséré pour la première fois :  
  
```  
<element name="Purchase_x0020_Order" type="xs:string />  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété de nom de nœud](../core/node-name-property.md)   
 [Les caractères de nom de nœud codés](../core/which-node-name-characters-get-encoded.md)