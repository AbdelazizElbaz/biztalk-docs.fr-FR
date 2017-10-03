---
title: Fonctoids logiques | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e37cdfc3-66de-4333-84eb-a8765afa8407
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7907d1045fde39d5ece963bd78e00d027e8a9da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="logical-functoids"></a>Fonctoids logiques

## <a name="overview"></a>Vue d'ensemble
**Logique** fonctoids permettent d’effectuer les opérations suivantes :  
  
-   Effectuer des tests logiques spécifiques au moment de l’exécution. Le **OR logique**, **NOT logique** et **logiques et** fonctoids peuvent être utilisées pour déterminer si un enregistrement est créé dans un message d’instance de destination, tel que le suivant :  
  
     Si ShipTo **ou** OrderedBy sont présents, créez l’enregistrement d’adresse BillTo.  
  
     Vous pouvez également utiliser ces fonctoids conjointement avec la **bouclage** fonctoid pour configurer le nombre de fois où un enregistrement de boucle.  
  
-   Contrôler si un enregistrement spécifique est créé dans un message d’instance de destination au moment de l’exécution. Fonctoids tels que **IsNil**, **Nombre logique**, **moins**, et **supérieur à** peut être utilisée pour contrôler si un enregistrement est créé.  
  
     Si le résultat de l’un de ces fonctoids logiques est **True**, l’enregistrement correspondant dans le message d’instance de destination est généré. Si le résultat est **False**, l’enregistrement correspondant dans le message d’instance de destination n’est pas généré.  
  
 Les fonctoids **IsNil**, **Date logique**, **Existence logique**, **NOT logique**, **numérique logique**, et **chaîne logique** n'accepter qu’un seul paramètre. Les fonctoids **égal**, **supérieur à**, **supérieur ou égal à**, **moins**, **inférieur ou égal à**, et **n’est pas égal** acceptent deux paramètres d’entrée. Alors que, dans le **logiques et** et **OR logique** fonctoids acceptent des paramètres d’entrée entre 2 et 100.  
  
 La sortie d’un **logiques** fonctoid peut également être accepté comme entrée pour d’autres fonctoids dans un mappage. Si les deux un **logiques** fonctoid et un fonctoid Bouclage sont liés entre eux et ensuite liés à un enregistrement dans le schéma de destination, le fonctoid Bouclage est utilisé uniquement lorsque le **logiques** sortie du fonctoid est  **True**.  
  
 Vous pouvez également utiliser **logiques** fonctoids avec les **mappage** ou **Value Mapping (Flattening)** fonctoids pour contrôler si un enregistrement dans le message d’instance de destination est créé.  
  
> [!IMPORTANT]
>  Si vous liez deux enregistrements ou champs du schéma source à deux **logiques** fonctoids et vous liez chacun de la **logiques** fonctoids au même enregistrement dans le schéma de destination, seul le premier  **Logique** fonctoid est utilisé dans le généré Language Transformations XSLT (Extensible Stylesheet). Le deuxième lien, de la seconde **logiques** fonctoid, est ignoré.  
  
> [!NOTE]
>  Les fonctoids logiques font la distinction entre les majuscules et les minuscules lorsque deux chaînes sont comparées. Par exemple, les chaînes « Abc » et « abc » ne sont pas équivalentes. L’exception à cette règle est quand **logiques** fonctoids comparent des chaînes qui représentent les valeurs booléennes **True** et **False**. Dans ce cas, « True » et « true » sont équivalents.  

## <a name="available-functoids"></a>Fonctoids disponibles  
 Le **logiques** fonctoids sont : 

* Égal à
* Supérieur à
* Supérieur ou égal à
* IsNil
* Inférieur à
* Inférieur ou égal à
* ET logique
* Date logique
* Existence logique
* NOT logique
* Nombre logique
* OU logique
* Chaîne logique
* Non égal

Plus d’informations sur ces fonctions sont [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
-  [Ajout de fonctoids de base à une carte](../core/how-to-add-basic-functoids-to-a-map.md)   
-  **Référence des fonctoids logiques**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]