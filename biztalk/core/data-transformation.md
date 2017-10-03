---
title: "Transformation de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, data translation
- data translation, about data translation
- data transformation, about data transformation
- maps, data transformation
- data transformation, maps
- data translation, maps
ms.assetid: a6aa5e9a-8d9c-478d-8f69-f9b16ed1a18c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ee1cd9b7e825f210032f7caaaa292496cfa44c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-transformation"></a>Transformation des données
Le mappage des données repose sur la transformation des données.  
  
 La transformation des données est le processus de création d'une correspondance entre des enregistrements et des champs d'un schéma source et des enregistrements et des champs (souvent différents) d'un schéma de destination. Par exemple, elle peut consister à mapper les adresses d'expédition et de facturation d'un bon de commande avec celles d'une facture. Il s'agit là du type de mappage le plus basique. La transformation des données peut aussi s'appliquer à des opérations comme :  
  
-   le calcul des données moyennes à partir d'un enregistrement de bouclage et l'envoi du résultat vers un champ du schéma de destination ;  
  
-   la conversion d'un caractère en son format ASCII ;  
  
-   l'ajout ou la soustraction de données d'un ou de plusieurs enregistrements et l'envoi du résultat vers un champ du schéma de destination.  
  
 Pour convertir les données dans un autre format, utilisez un pipeline. Cela peut s'avérer utile pour résoudre les problèmes d'intégration des applications d'entreprise en convertissant un type de message donné dans les autres formats requis par les systèmes existants, mais cela ne peut pas se faire en utilisant un mappage.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages](../core/maps.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)