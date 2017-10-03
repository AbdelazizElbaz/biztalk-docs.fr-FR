---
title: "Modes d’analyse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- pipeline components [custom], parsing
ms.assetid: b1188720-e5ae-47ae-ab8e-16d7ed08b778
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf8f9b2618b8cafd7813f08217457227a0f21809
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="parsing-modes"></a>Modes d’analyse
Le mode d’analyse est un attribut de l’enregistrement schemaInfo, avec deux modes : vitesse et la complexité. Vous pouvez configurer la propriété Optimisation de l'analyseur dans l'Éditeur de schéma BizTalk.  
  
## <a name="example"></a>Exemple  
  
```  
<b:schemaInfo count_positions_by_byte="false" standard="Flat File"   
root_reference="document" parser_optimization="complexity" />.  
```  
  
 En mode vitesse, l'analyseur traite les données à mesure qu'elles apparaissent dans le flux. Voici par exemple le schéma suivant :  
  
```  
<schema>  
   Root ("," prefix)  
      Field1   opt  
      Field2   opt  
      Field3   opt  
      Field4   opt  
      Record ("," infix)  
            Field5  
            Field6  
</schema>  
```  
  
 et le message entrant.  
  
```  
,1,2,3,4  
```  
  
 En mode vitesse, le document XML suivant est généré :  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
   <Field3>3</Field3>  
   <Field4>4</Field4>  
</Root>  
```  
  
 En mode complexité, le même schéma produit le résultat suivant :  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
      <Record>  
         <Field5>3</Field5>  
         <Field6>4</Field6>  
      </Record>  
</Root>  
```  
  
 En mode complexité, le moteur d'analyse de fichier plat utilise à la fois l'analyse descendante et ascendante, et essaie de traiter les données de manière plus précise. En mode vitesse, l'analyseur traite les données à mesure qu'elles apparaissent dans le flux.  
  
 Si des éléments facultatifs se trouvent avec des éléments obligatoires, par exemple :  
  
```  
<schema>  
   Root  
      Record1 (required)  
  
      Record2 (optional)  
  
      Record3 (required)  
  
```  
  
 vous devez utiliser le mode complexité pour analyser correctement les données, car l'analyseur représente en interne le schéma tel que :  
  
```  
<schema>  
   Root  
      Record1 (required)  
      <sequence> (optional)  
         Record2 (required)  
         Record3 (required)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du moteur d’analyse de fichier plat](../core/using-the-flat-file-parsing-engine.md)