---
title: "Schémas source et Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- destination schemas
- source schemas, maps
- XML schemas, defining
- destination schemas, about destination schemas
- schemas, destination
- destination schemas, maps
- maps, source schemas
- schemas, Root Reference property
- Root Reference property, modifying
- source schemas
- modifying, Root Reference property
- maps, Root Reference property
- source schemas, about source schemas
- schemas, maps
- maps, schema requirements
- schemas, requirements
- schemas, source schemas
- maps, destination schemas
- Root Reference property
ms.assetid: 8c805854-9fa1-4ce3-938d-a2e61ba17fa1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d82fb8445260b505fbd04b648c251b99fe896dcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="source-and-destination-schemas"></a>Schémas source et de destination
Chaque mappage BizTalk utilise deux schémas : un schéma source et un schéma de destination. Le schéma source définit la structure des messages d'instance desquels vous prélevez des données. Le schéma de destination définit la structure des messages d'instance que le mappage produit. Par exemple, si vous souhaitez mapper les informations d'expédition et de facturation d'un bon de commande avec une facture, il vous faut un schéma pour définir des bons de commande pour le schéma source, et un schéma définissant les factures pour le schéma de destination.  
  
 Les schémas utilisés dans les mappages BizTalk doivent satisfaire aux conditions suivantes :  
  
-   Les schémas source et de destination doivent faire partie de votre projet BizTalk en cours, ou vous devez inclure une référence aux schémas dans l'assembly de manière à ce qu'ils soient accessibles pendant l'exécution.  
  
-   Les schémas utilisés dans le Mappeur BizTalk doivent être basés sur le langage XSD (XML Schema Definition). L'Éditeur BizTalk constitue un moyen aisé de créer ce genre de schémas. Pour plus d’informations sur la création de schémas avec l’Éditeur BizTalk, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md). Consultez également [création de schémas](../core/creating-schemas.md).  
  
 Dans l'Éditeur BizTalk, vous pouvez créer des schémas avec plusieurs nœuds racine. Mais si vous utilisez un schéma avec plusieurs nœuds racine dans un mappage BizTalk, vous devez choisir quel nœud racine (et la sous-structure correspondante) utiliser dans ce dernier. Schémas ont un **référence de racine** propriété qui identifie la racine est le principale. Si un schéma a plusieurs racines et **référence de racine** propriété est définie lorsque le schéma de la première ouverture correspond à la source ou le schéma de destination, le Mappeur BizTalk utilise la racine spécifiée. Si un schéma a plusieurs racines et **référence de racine** propriété n’est pas définie, le Mappeur BizTalk vous invite à choisir une racine.  
  
 Si vous modifiez le **référence de racine** ne tient pas compte de la modification de propriété d’un schéma déjà utilisé dans un mappage, le Mappeur BizTalk et continue d’utiliser la racine initialement spécifiée. Si vous souhaitez créer divers mappages à l’aide de différentes racines d’un même schéma, il est préférable de ne pas définir le **référence de racine** propriété. Ainsi, dès que le schéma est utilisé dans un nouveau mappage, vous devez explicitement choisir la racine.  
  
 Modifier un schéma après l'avoir inclus dans un mappage peut entraîner la rupture de liens à l'intérieur de ce dernier.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages](../core/maps.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)