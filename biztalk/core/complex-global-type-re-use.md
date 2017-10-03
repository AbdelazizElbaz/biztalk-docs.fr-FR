---
title: "Réutilisation de types globaux complexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d8018-f2c6-44cc-9330-2385ac8887eb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 492d1c345b1ac540bc2410c554be29996fc52dd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complex-global-type-re-use"></a>Réutilisation de types globaux complexes
Pour utiliser un type complexe type global est dans un autre emplacement dans l’arborescence du schéma, commencez par insérer un nouveau **enregistrement** nœud à l’emplacement souhaité. Définissez ensuite sa **Data Structure Type** nom à la propriété d’un type global complexe.  
  
 Dans l’exemple suivant, **BillingAddress** est le nom de récemment insérées **enregistrement** nœud, et **GlobalAddrType** est le nom du type global complexe qu’il adopte. Dans l’arborescence du schéma, une structure de nœud en double sera affichée sous le nœud nommé **BillingAddress**, identique à la structure de nœuds adjacents sous le nœud nommé **ShippingAddress**.  
  
-   Avant, avec un nœud nouvellement inséré nommé **BillingAddress**.  
  
    ```  
    <xs:schema>  
        <xs:element name="Root">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                    <xs:element name="BillingAddress">  
                        <xs:sequence />  
                    </xs:element>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
        <xs:complexType name="GlobalAddrType">  
        [Address structure defined globally here.]  
        </xs:complexType>  
    </xs:schema>  
    ```  
  
-   Après avoir utilisé le type complex de base **GlobalAddrType**, comme l’est.  
  
    ```  
    <xs:schema>  
        <xs:element name="Root">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                    <xs:element name="BillingAddress" type="GlobalAddrType" />  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
        <xs:complexType name="GlobalAddrType">  
        [Address structure defined globally here.]  
        </xs:complexType>  
    </xs:schema>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Modes d’utilisation des Types globaux complexes](../core/ways-to-use-complex-global-types.md)