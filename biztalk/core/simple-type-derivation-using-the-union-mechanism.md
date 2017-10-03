---
title: "Dérivation de Type simple à l’aide du mécanisme d’Union | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e51ae390-78f5-4fb9-9163-2a8023aea1ec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1414fa506f824415de8e8449e8b2b27befd2fc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation-using-the-union-mechanism"></a>Dérivation de type simple à l'aide du mécanisme d'union
Lorsque vous dérivez un nouveau type simple à partir d'un type simple existant à l'aide du mécanisme d'union, vous spécifiez que la valeur de cet attribut ou de cet élément peut appartenir à plus d'un type, d'après une liste de types que vous spécifiez. Par exemple, vous pouvez spécifier qu'une valeur d'attribut ou d'élément est une valeur de date, d'heure ou de date/heure.  
  
 Pour obtenir des informations complètes sur la dérivation de nouveaux types simples par le biais du mécanisme d'union, reportez-vous au site Web de W3C. Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  
  
 Pour dériver un type simple sous la forme d’une union de plusieurs types, sélectionnez la **Fieldelement** nœud ou **attribut de champ** dans l’arborescence du schéma, puis, dans la fenêtre Propriétés, sélectionnez un type simple à partir de la liste déroulante pour le **Base Data Type** propriété. Dès que vous avez sélectionné une valeur pour cette propriété, le **Derived By** propriété change automatiquement de sa valeur par défaut à **Restriction**, qui sert de la valeur par défaut pour la dérivation de type. Vous devez modifier le **Derived By** propriété à partir de **Restriction** à **Union**, ce qui entraîne la **Base Data Type** doit être renommé en tant que propriété le **Types de membres** propriété (plus, la propriété renommée déplace vers une autre position dans la liste des propriétés en raison de l’ordre de tri alphabétique des propriétés).  
  
 Enfin, vous pouvez utiliser les cases à cocher dans la **Types de membres** liste de contrôle de liste déroulante pour sélectionner les types supplémentaires afin d’autoriser les valeurs correspondantes dans les messages d’instance.  
  
 Lorsque vous modifiez un **Fieldelement** nœud ou **attribut de champ** nœud de ne pas avoir de données de type pour un type de base de données (en commençant ainsi le processus de dérivation de type simple), puis définissez le **Derived By** propriété **Union**, vous pouvez observer le changement suivant dans le fragment correspondant dans la vue XSD.  
  
-   Avant, avec un nouvellement inséré **Fieldelement** nœud nommé **DatesAndOrTimes**.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   Après avoir défini la **Base Data Type** propriété **xs : date**et en définissant le **Derived By** propriété **Union** (après laquelle le  **Type de base de données** propriété est renommée pour être le **Types de membres** propriété), puis en sélectionnant également **xs : DateTime** et **xs : Time** en tant que supplémentaires autorisées des types dans les **Types de membres** liste de contrôle de liste déroulante.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Dérivation de Type simple](../core/simple-type-derivation.md)