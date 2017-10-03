---
title: "Dérivation de Type complexe à l’aide du mécanisme d’Extension | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7125fb5b-f77a-47c9-8000-f2332940df89
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5d36778b5ad99a0273e6199f59bdd337429a74b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complex-type-derivation-using-the-extension-mechanism"></a>Dérivation de types complexes à l'aide du mécanisme d'extension
Un type complexe dérivé par extension est un sur-ensemble fonctionnel de son type de données de base. Comme son nom l'indique, son type de données de base est la base du type en cours de définition. Les différences par rapport au type de base sont additives. Cette rubrique fournit un exemple dans lequel les deux éléments **ShippingAddress** et **BillingAddress** sont basées sur le type global complex **GlobalAddrType**. **ShippingAddress** est simplement définie pour être de type **GlobalAddrType**, alors que **BillingAddress** est défini pour étendre le type **GlobalAddrType**. À la fin de l’exemple, un élément supplémentaire est ajouté à **BillingAddress**, nommé **service**, avec un type de chaîne et la valeur par défaut comptes fournisseurs.  
  
 Pour obtenir des informations complètes sur la dérivation de nouveaux types complexes par le biais du mécanisme d'extension, reportez-vous au site Internet de W3C. Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  
  
 Pour dériver un type global complexe par extension, à un autre emplacement dans l’arborescence du schéma, commencez par insérer un nouveau **enregistrement** nœud à l’emplacement souhaité. Définissez ensuite sa **Base Data Type** nom à la propriété d’un type global complexe.  
  
 Dans l’exemple suivant, **BillingAddress** est le nom de récemment insérées **enregistrement** nœud, et **GlobalAddrType** est le nom du type complexe global à partir de laquelle elle est dérivé et essaie de s’étendre. Dans l’arborescence du schéma, une fois **Base Data Type** a été défini sur **GlobalAddrType**, une structure de nœud en double s’affiche sous le nœud nommé **BillingAddress**, identique à la structure de nœuds adjacents sous le nœud nommé **ShippingAddress**. La différence est que le **BillingAddress** structure de nœud sera extensible au-delà du type de base de données **GlobalAddrType**et le **ShippingAddress** structure restera identique au type de base de données **GlobalAddrType**.  
  
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
  
-   Après avoir dérivé d’un type complex de base **GlobalAddrType**, par extension.  
  
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
  
 Vous spécifiez des extensions pour le type de base de données par l’insertion de nœuds dans le **BillingAddress** nœud dans l’arborescence du schéma. Le fragment XSD suivant montre comment l’élément d’extension vide est développé lorsque un **groupe séquence** nœud est inséré en tant que nouvel enfant du **BillingAddress** nœud, puis un **élément de champ**  nœud, nommé **type de paiement**, est inséré en tant que nœud enfant de la **groupe séquence** nœud.  
  
```  
<xs:extension base="GlobalAddrType">  
    <xs:sequence>  
        <xs:element default="Accounts Payable"  
            name="Department" type="xs:string" />  
    </xs:sequence>  
</xs:extension>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Dérivation de Type Global complexe](../core/complex-global-type-derivation.md)