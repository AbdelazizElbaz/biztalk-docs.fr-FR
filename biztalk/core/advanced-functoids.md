---
title: Advanced fonctoids | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bf2547-5e44-45f8-b577-97e5760a0339
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5002b639df79ece1019c2d013c128f615517ae5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="advanced-functoids"></a>Fonctoids avancés

## <a name="overview"></a>Vue d'ensemble
Les fonctoids avancés se répartissent en cinq catégories différentes en fonction de leur usage :  
  
-   **La gestion des enregistrements de boucle.** Le **Index**, **itération**, **bouclage**, **valeur Nil**, **nombre d’enregistrements**, **Table Extracteur**, et **bouclage de Table** fonctoids sont utilisés dans différentes combinaisons lorsque le message d’instance d’entrée contient des sections comportant un imprévisibles nombre d’éléments se répétant, comme représenté par un bouclage enregistrements dans le schéma source.  
  
-   **Mappage conditionnel.** Le **mappage** et **Value Mapping (Flattening)** fonctoids sont utilisés pour fournir un mappage conditionnel à partir d’un message d’instance d’entrée et un message d’instance de sortie. Lorsque leur premier paramètre d'entrée est True, le second est placé dans l'élément ou l'attribut spécifié dans le message d'instance de sortie. Sinon, cet élément ou cet attribut n'est pas créé dans le message d'instance de sortie.  
  
-   **Script arbitraire.** Le **script** fonctoid est utilisé pour exécuter un script arbitraire ou code compilé lorsqu’un message d’instance d’entrée est mappé à un message d’instance de sortie. Un tel script ou code compilé peut être créé de manière à ce qu'il accepte les paramètres d'entrée issus du message d'instance source, des valeurs constantes configurées, de la sortie d'un autre fonctoid, ou d'une combinaison de tout cela.  
  
-   **Mappage simple.** Le **copie de masse** fonctoid peut être utilisé pour copier un élément entier, y compris ses sous-éléments jusqu'à une profondeur arbitraire, à partir d’un message d’instance d’entrée et un message d’instance de sortie.  
  
-   **Résolution des problèmes**. Le **Assert** fonctoid peut être utilisé pour tester vos hypothèses sur les valeurs d’élément.  
  
## <a name="available-functoids"></a>Fonctoids disponibles
  
 Le **avancé** fonctoids sont : 

* Fonctoid déclarer
* Fonctoid Index 
* Fonctoid Itération 
* Fonctoid Bouclage 
* Fonctoid Copie de masse 
* Fonctoid Valeur nil
* Fonctoid Nombre d’enregistrements 
* Fonctoid script 
* Bouclage de table et de fonctoids Extracteur de Table
* Fonctoid Mappage
* Fonctoid Mappage des valeurs (mise à plat)

Plus d’informations sur ces fonctoids sont dans le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Fonctoid déclarer](../core/assert-functoid.md)  
  
-   [Fonctoid Index](../core/index-functoid.md)  
  
-   [Fonctoid Itération](../core/iteration-functoid.md)  
  
-   [Fonctoid Bouclage](../core/looping-functoid.md)  
  
-   [Fonctoid copie de masse](../core/mass-copy-functoid.md)  
  
-   [Fonctoid Valeur nil](../core/nil-value-functoid.md)  
  
-   [Fonctoid Nombre d’enregistrements](../core/record-count-functoid.md)  
  
-   [Bouclage de table et de fonctoids Extracteur de Table](../core/table-looping-and-table-extractor-functoids.md)  
  
-   [Fonctoid Mappage](../core/value-mapping-functoid.md)  
  
-   [(Mise à plat) fonctoid Mappage](../core/value-mapping-flattening-functoid.md)  
  
-   [Fonctoid script](../core/scripting-functoid.md)