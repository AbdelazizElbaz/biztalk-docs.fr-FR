---
title: "Dérivation de Type complexe à l’aide du mécanisme de Restriction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3003d88-6b75-4dcb-834f-1babcf7449cb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddbd9d8266d9c289b9b4bae9dd7060906e01ebd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complex-type-derivation-using-the-restriction-mechanism"></a>Dérivation de types complexes à l'aide du mécanisme de restriction
En matière de fonctionnalité Éditeur BizTalk, la dérivation par restriction est similaire à la dérivation par extension. Un type complexe dérivé par restriction est similaire à son type de données de base excepté que ses déclarations sont plus limitées que les déclarations correspondantes dans le type de données de base. Les valeurs représentées par le nouveau type sont en fait un sous-ensemble des valeurs représentées par le type de données de base (comme c'est le cas avec la restriction de types simples). Une application préparée pour les valeurs du type de données de base doit pouvoir traiter correctement toutes les valeurs du type limité.  
  
 Pour obtenir des informations complètes sur la dérivation de nouveaux types complexes par le biais du mécanisme de restriction, reportez-vous au site Internet de W3C. Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  
  
 Pour dériver un type global complexe par restriction, dans un autre emplacement dans l’arborescence du schéma, commencez par insérer un nouveau **enregistrement** nœud à l’emplacement souhaité. Définissez ensuite sa **Base Data Type** nom à la propriété d’un type global complexe. Enfin, modifiez le paramètre de la **Derived By** propriété sa valeur par défaut de **Extension** (au moins un type de base de données est la valeur) à **Restriction**.  
  
 Dans l’exemple suivant, **BillingAddress** est le nom de récemment insérées **enregistrement** nœud, et **GlobalAddrType** est le nom du type complexe global à partir de laquelle elle est dérivé et envisage de se limiter. Dans l’arborescence du schéma, une structure de nœud en double sera affichée sous le nœud nommé **BillingAddress**, identique à la structure de nœuds adjacents sous le nœud nommé **ShippingAddress**. La différence est que le **BillingAddress** structure de nœud sera soumis à des restrictions possibles pour le type de base de données **GlobalAddrType**et le **ShippingAddress** structure restera identique au type de base de données **GlobalAddrType**.  
  
 Dès lors que vous avez choisi de limiter le type de données de base, il vous est interdit d'insérer de nouveaux nœuds, mais vous pouvez modifier les propriétés des nœuds existants pour limiter davantage leurs valeurs possibles ou leur comportement.  
  
-   Avant, avec la **Derived By** propriété toujours la valeur **Extension**.  
  
    ```  
    <xs:schema>  
        <xs:element name="Root">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                    <xs:element name="BillingAddress">  
                        <xs:complexType>  
                            <xs:complexContent mixed="false">  
                                <xs:extension base="GlobalAddrType" />  
                            </xs:complexContent>  
                        </xs:complexType>  
                    </xs:element>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
        <xs:complexType name="GlobalAddrType">  
        [Address structure defined globally here.]  
        </xs:complexType>  
    </xs:schema>  
    ```  
  
-   Après avoir basculé le **Derived By** propriété à partir de **Extension** à **Restriction**.  
  
    ```  
    <xs:schema>  
        <xs:element name="Root">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                    <xs:element name="BillingAddress">  
                        <xs:complexType>  
                            <xs:complexContent mixed="false">  
                                <xs:restriction base="GlobalAddrType">  
                   [Duplicate of address structure now appears  
                   here, ready to be restricted with additional  
                   attributes, set using the properties of the  
                   relevant nodes in the schema tree.]  
                                </xs:restriction>  
                            </xs:complexContent>  
                        </xs:complexType>  
                    </xs:element>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
        <xs:complexType name="GlobalAddrType">  
        [Address structure defined globally here.]  
        </xs:complexType>  
    </xs:schema>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Dérivation de Type Global complexe](../core/complex-global-type-derivation.md)