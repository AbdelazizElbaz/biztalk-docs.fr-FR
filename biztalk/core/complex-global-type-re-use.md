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
# <a name="complex-global-type-re-use"></a><span data-ttu-id="a8934-102">Réutilisation de types globaux complexes</span><span class="sxs-lookup"><span data-stu-id="a8934-102">Complex Global Type Re-use</span></span>
<span data-ttu-id="a8934-103">Pour utiliser un type complexe type global est dans un autre emplacement dans l’arborescence du schéma, commencez par insérer un nouveau **enregistrement** nœud à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="a8934-103">To use a complex global type as is, in another location in the schema tree, begin by inserting a new **Record** node at the desired location.</span></span> <span data-ttu-id="a8934-104">Définissez ensuite sa **Data Structure Type** nom à la propriété d’un type global complexe.</span><span class="sxs-lookup"><span data-stu-id="a8934-104">Then set its **Data Structure Type** property to the name of a complex global type.</span></span>  
  
 <span data-ttu-id="a8934-105">Dans l’exemple suivant, **BillingAddress** est le nom de récemment insérées **enregistrement** nœud, et **GlobalAddrType** est le nom du type global complexe qu’il adopte.</span><span class="sxs-lookup"><span data-stu-id="a8934-105">In the following example, **BillingAddress** is the name of the newly inserted **Record** node, and **GlobalAddrType** is the name of the complex global type that it adopts.</span></span> <span data-ttu-id="a8934-106">Dans l’arborescence du schéma, une structure de nœud en double sera affichée sous le nœud nommé **BillingAddress**, identique à la structure de nœuds adjacents sous le nœud nommé **ShippingAddress**.</span><span class="sxs-lookup"><span data-stu-id="a8934-106">In the schema tree view, a duplicate node structure would be displayed below the node named **BillingAddress**, identical to the adjacent node structure under the node named **ShippingAddress**.</span></span>  
  
-   <span data-ttu-id="a8934-107">Avant, avec un nœud nouvellement inséré nommé **BillingAddress**.</span><span class="sxs-lookup"><span data-stu-id="a8934-107">Before, with a newly inserted node named **BillingAddress**.</span></span>  
  
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
  
-   <span data-ttu-id="a8934-108">Après avoir utilisé le type complex de base **GlobalAddrType**, comme l’est.</span><span class="sxs-lookup"><span data-stu-id="a8934-108">After using the complex base type **GlobalAddrType**, as is.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8934-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8934-109">See Also</span></span>  
 [<span data-ttu-id="a8934-110">Modes d’utilisation des Types globaux complexes</span><span class="sxs-lookup"><span data-stu-id="a8934-110">Ways to Use Complex Global Types</span></span>](../core/ways-to-use-complex-global-types.md)