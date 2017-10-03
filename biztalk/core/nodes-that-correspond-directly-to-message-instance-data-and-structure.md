---
title: "Les nœuds qui correspondent directement à un Message d’Instance Structure et les données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cf721c-2972-43c6-8ae4-f2f8f83ba2c5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d5ed1aae517bb81e5a6cfb888300015e99ec017
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nodes-that-correspond-directly-to-message-instance-data-and-structure"></a>Nœuds correspondant directement à une structure et à des données d’instance de message
Certains types de nœuds que vous utilisez pour créer des schémas dans l’Éditeur BizTalk correspondent directement à des éléments et à des attributs de représentation XML de messages d'instance gérés par le schéma (pour les autres formats de message d’instance, tels que les formats de fichier plat, cette correspondance n’existe qu’après conversion depuis un autre format ou avant conversion vers un autre format). Ces types de nœuds sont **enregistrement** nœuds (y compris racine **enregistrement** nœuds), **élément de champ** nœuds, et **attribut de champ** nœuds.  
  
 Les valeurs que vous donnez à la **nom de nœud** propriété du **enregistrement** et **élément de champ** nœuds spécifient le nom de l’élément correspondant dans les messages d’instance XML gérés par le schéma. De même, les valeurs que vous donnez à la **nom de nœud** propriété du **attribut de champ** nœuds spécifient le nom de l’attribut correspondant dans les messages d’instance XML gérés par le schéma. Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Le reste de cette section fournit des informations sur cette classe de nœuds, avec racine **enregistrement** nœuds reçoit un traitement distinct en raison de leur rôle spécial dans les schémas.  
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Nœuds racine](../core/root-nodes.md)  
  
-   [Nœuds d’enregistrement](../core/record-nodes.md)  
  
-   [Nœuds élément de champ](../core/field-element-nodes.md)  
  
-   [Nœuds attribut de champ](../core/field-attribute-nodes.md)