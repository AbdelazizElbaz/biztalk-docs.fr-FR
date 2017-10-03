---
title: "Dérivation de Type simple à l’aide du mécanisme de Restriction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ca712e-9563-4917-9bfc-1033a36773e8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dda4b8ad64f1edf262446f1633eda109ba7074ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation-using-the-restriction-mechanism"></a>Dérivation de type simple à l'aide du mécanisme de restriction

## <a name="overview"></a>Vue d'ensemble
Lorsque vous déduisez un nouveau type simple à l'aide du mécanisme de restriction à partir d'un type simple existant, vous limitez généralement les valeurs autorisées dans un message d'instance pour cette valeur d'attribut ou d'élément à un sous-ensemble des valeurs autorisées par le type simple de base. Par exemple, vous pouvez limiter un type de chaîne à être une chaîne énumérée parmi plusieurs autres.  
  
 Pour obtenir des informations complètes sur la dérivation de nouveaux types simples par le biais du mécanisme de restriction, reportez-vous au site Internet de W3C. Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  
  
## <a name="field-element-and-field-attribute"></a>Élément de champ et d’attribut de champ
 Pour dériver un type simple à l’aide de restriction, sélectionnez la **Fieldelement** nœud ou **attribut de champ** dans l’arborescence du schéma, puis, dans la fenêtre Propriétés, sélectionnez un type simple dans la liste déroulante. la liste pour le **Base Data Type** propriété. Dès que vous avez sélectionné une valeur pour cette propriété, le **Derived By** propriété change automatiquement de sa valeur par défaut à **Restriction**, qui sert de la valeur par défaut pour la dérivation de type. En outre, une toute nouvelle catégorie de propriétés, appelée **Restriction**, devient disponible dans la fenêtre Propriétés.  
  
 En fonction du type de données de base que vous sélectionnez, les propriétés pouvant être définies dans cette nouvelle catégorie sont différentes. Par exemple, si le type de base de données est numérique, les propriétés **MaxFacet Type** (lorsque **MaxFacet Value** est défini), **MaxFacet Value**, **MinFacet Type** (lorsque **MinFacet Value** est défini), et **MinFacet Value** sont disponibles pour définir une plage inclusive ou exclusive de valeurs autorisées. Si le type de base de données est un type chaîne, la **longueur**, **longueur maximale**, et **longueur minimale** propriétés sont disponibles pour limiter la longueur de la chaîne.  
  
 Pour plus d’informations sur les différentes propriétés de la restriction des nœuds de champ, consultez la **propriétés de nœud élément de champ** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Lorsque vous modifiez un **Fieldelement** nœud ou **attribut de champ** nœud de l’utilisation d’un type de données ayant un type de base de données (et démarrer le processus de dérivation de type simple), laissez le  **Dérivé par** propriété **Restriction**et fournir une restriction basée sur une énumération pour les valeurs de chaîne autorisée, vous pouvez observer les modifications suivantes dans le fragment correspondant dans la vue XSD :  
  
-   Avant, avec un nouvellement inséré **Fieldelement** nœud nommé **WestCoastStates**.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
-   Après avoir défini la **Base Data Type** à la propriété « xs : String » et laisser la valeur par défaut de dérivation de **Restriction** pour le **Derived By** propriété.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates" >  
                    <xs:simpleType>  
                        <xs:restriction base="xs:string" />  
                    </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
-   Après avoir défini la **énumération** propriété dans la catégorie Restriction sur les noms des trois états de la côte ouest des États-Unis continentaux.  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates">  
                    <xs:simpleType>  
                        <xs:restriction base="xs:string" />  
                            <xs:enumeration value="Washington" />  
                            <xs:enumeration value="Oregon" />  
                            <xs:enumeration value="California" />  
                        </xs:restriction>  
                    </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Dérivation de Type simple](../core/simple-type-derivation.md)