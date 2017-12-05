---
title: Fonctoid Mappage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Value Mapping functoids
- functoids, empty tags
- Concatenate functoids
ms.assetid: 3dd626fb-3bf6-4ede-9fd2-ddae5a54d178
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 038d59827a62c9f4e83879ec7cf2e0b47fd738f4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="value-mapping-functoid"></a>Fonctoid Mappage
Le **mappage** fonctoid retourne la valeur de son deuxième paramètre si son premier paramètre a la valeur true. Un fonctoid sert souvent à modifier les attributs d'un champ en attributs d'un enregistrement. Pour mettre à plat une partie d’un message d’entrée en convertissant plusieurs enregistrements en un seul enregistrement, utilisez la [fonctoid Mappage des valeurs (mise à plat)](../core/value-mapping-flattening-functoid.md).  
  
 La figure suivante illustre un mappage avec le **mappage** fonctoid permet de modifier les attributs d’un champ en attributs d’un enregistrement.  
  
 ![](../core/media/valuemappingfunctoid.gif "valuemappingfunctoid")  
Mappage du fonctoid Mappage des valeurs  
  
 Le code suivant montre un message d’instance d’entrée dans les paires de noms et valeurs sont assignées aux **nom** et **valeur** attributs.  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherIn">  
    <Record>  
        <Field Name="WindSpeed" Value="5"/>   
        <Field Name="Temperature" Value="20" />  
    </Record>  
    <Record>  
        <Field Name="WindSpeed" Value="15" />  
        <Field Name="Temperature" Value="18" />  
    </Record>  
</ns0:Root>  
```  
  
 Le mappage précédent convertit le message en une version dans laquelle les valeurs sont affectées aux attributs avec les noms correspondants dans des enregistrements séparés.  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherOut">  
    <Record WindSpeed="5"/>  
    <Record Temperature="20"/>  
    <Record WindSpeed="15"/>  
    <Record Temperature="18"/>  
</ns0:Root>  
```  
  
 Le **égal** fonctoids testent les valeurs de la **nom** attribut. La première **égal** fonctoid teste la valeur de **nom** « windspeed ». Lorsque le **nom** est « WindSpeed », la première **égal** fonctoid retourne **True**. À son tour, ainsi le **mappage** fonctoid pour définir la valeur de la **WindSpeed** attribut dans le message d’instance de sortie.  
  
## <a name="suppressing-the-creation-of-empty-tags"></a>Suppression de la création de balises vides  
 Pour supprimer des balises vides, utilisez le fonctoid Mappage des valeurs pour vérifier si une balise doit être créée ou non. Si la valeur de la condition est true, le champ de destination sera créé, sinon, il ne le sera pas. Dans un scénario de bouclage, utilisez un fonctoid logique et connectez-le à l'enregistrement ou au champ de destination. Si la condition a la valeur false, la balise ne sera pas créée. Pour obtenir un exemple, consultez [bouclage conditionnel](../core/conditional-looping.md).  
  
## <a name="forcing-the-creation-of-empty-tags"></a>Création forcée de balises vides  
 Pour forcer la création de balises vides, vous pouvez ajouter une valeur dans la propriété valeur du champ de destination ou de lien un **Concatenate** fonctoid pour le champ de destination.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est possible de forcer la génération de balises vides en sélectionnant la «\<vide\>« valeur de la propriété de la valeur du champ de destination. Dans ce cas, le champ sera créé avec la valeur vide.  
  
## <a name="see-also"></a>Voir aussi  
 [(Mise à plat) fonctoid Mappage](../core/value-mapping-flattening-functoid.md)   
 [Comment ajouter des fonctoids de mappage à un mappage de valeur](../core/how-to-add-value-mapping-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)