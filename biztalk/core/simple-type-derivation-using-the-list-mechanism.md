---
title: "Dérivation de Type simple à l’aide du mécanisme de liste | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f3c7b7-7585-4297-9177-2deaef8355f0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aafc6a540e9595f426858bc16fedfb1f8fe0bc8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation-using-the-list-mechanism"></a>Dérivation de type simple à l'aide du mécanisme de liste
Lorsque vous déduisez un nouveau type simple à partir d'un type simple existant à l’aide du mécanisme de liste, vous spécifiez que la valeur pour l'attribut ou l'élément peut correspondre à une liste des valeurs du type spécifié séparées par des espaces. Vous pouvez par exemple spécifier qu'une valeur d'attribut ou d’élément est une liste d'entiers séparés par des espaces.  
  
 Pour obtenir des informations complètes sur la dérivation de nouveaux types simples par le biais du mécanisme de liste, consultez le site Web de W3C. Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  
  
 Pour dériver un type simple sous la forme d’une liste de ce type, sélectionnez la **Fieldelement** nœud ou **attribut de champ** dans l’arborescence du schéma, puis, dans la fenêtre Propriétés, sélectionnez un type simple dans la liste déroulante. la liste pour le **Base Data Type** propriété. Dès que vous sélectionnez une valeur pour cette propriété, le **Derived By** propriété change automatiquement de sa valeur par défaut à **Restriction**, qui sert de la valeur par défaut pour la dérivation de type. Vous devez modifier le **Derived By** propriété à partir de **Restriction** à **liste**, ce qui entraîne la **Base Data Type** doit être renommé en tant que propriété le **Type d’élément** propriété (plus, la propriété renommée déplace vers une autre position dans la liste des propriétés en raison de l’ordre de tri alphabétique des propriétés).  
  
> [!NOTE]
>  Vous pouvez utiliser les mécanismes de liste et de restriction ensemble, en créant une dérivation de type simple nommée à l’aide du mécanisme de restriction, puis en utilisant celle-ci comme type d’élément d'une autre dérivation de type simple à l'aide du mécanisme de liste. Vous pouvez ainsi obtenir une valeur qui serait obligatoirement une liste de chaînes séparées par des espaces appartenant à une énumération de chaînes particulière.  
  
> [!CAUTION]
>  Il peut s’avérer compliqué d'utiliser le mécanisme de liste pour la dérivation de type simple lorsque le type d’élément que vous choisissez correspond à un type autorisant les espaces, telles que des chaînes. Cela tient au fait que le mécanisme de liste utilise des espaces pour séparer des valeurs du type autorisé dans la liste.  
  
 Lorsque vous modifiez un **Fieldelement** nœud ou **attribut de champ** nœud de ne pas avoir de données de type pour un type de base de données (en commençant ainsi le processus de dérivation de type simple), puis définissez le **Derived By** propriété **liste**, vous pouvez observer le changement suivant dans le fragment correspondant dans la vue XSD :  
  
-   Avant, avec un nouvellement inséré **Fieldelement** nœud nommé **ZipCodeList**.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   Après avoir défini la **Base Data Type** propriété xs : Integer et la **Derived By** propriété **liste** (après laquelle le **Base Data Type**propriété est renommée pour être le **Type d’élément** propriété).  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList">  
                    <xs:simpleType>  
               <xs:list itemType="xs:integer" />   
                       </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
> [!NOTE]
>  Dans un schéma de la vie réelle, il est préférable d’abord définir et nommer une dérivation de type simple d’entier qui limiterait l’entier à cinq chiffres, avant de dériver le **ZipCodeList** élément à partir de ce type, efficace en limitant la liste à entiers de cinq chiffres.  
  
## <a name="see-also"></a>Voir aussi  
 [Dérivation de Type simple](../core/simple-type-derivation.md)