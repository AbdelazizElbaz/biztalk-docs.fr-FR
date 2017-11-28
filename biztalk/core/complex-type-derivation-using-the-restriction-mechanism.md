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
# <a name="complex-type-derivation-using-the-restriction-mechanism"></a><span data-ttu-id="b33e1-102">Dérivation de types complexes à l'aide du mécanisme de restriction</span><span class="sxs-lookup"><span data-stu-id="b33e1-102">Complex Type Derivation Using the Restriction Mechanism</span></span>
<span data-ttu-id="b33e1-103">En matière de fonctionnalité Éditeur BizTalk, la dérivation par restriction est similaire à la dérivation par extension.</span><span class="sxs-lookup"><span data-stu-id="b33e1-103">Derivation by restriction is similar to derivation by extension, in terms of BizTalk Editor functionality.</span></span> <span data-ttu-id="b33e1-104">Un type complexe dérivé par restriction est similaire à son type de données de base excepté que ses déclarations sont plus limitées que les déclarations correspondantes dans le type de données de base.</span><span class="sxs-lookup"><span data-stu-id="b33e1-104">A complex type derived by restriction is similar to its base data type, except that its declarations are more limited than the corresponding declarations in the base data type.</span></span> <span data-ttu-id="b33e1-105">Les valeurs représentées par le nouveau type sont en fait un sous-ensemble des valeurs représentées par le type de données de base (comme c'est le cas avec la restriction de types simples).</span><span class="sxs-lookup"><span data-stu-id="b33e1-105">In fact, the values represented by the new type are a subset of the values represented by the base data type (as is the case with restriction of simple types).</span></span> <span data-ttu-id="b33e1-106">Une application préparée pour les valeurs du type de données de base doit pouvoir traiter correctement toutes les valeurs du type limité.</span><span class="sxs-lookup"><span data-stu-id="b33e1-106">An application prepared for the values of the base data type ought to be able to successfully process any of the values of the restricted type.</span></span>  
  
 <span data-ttu-id="b33e1-107">Pour obtenir des informations complètes sur la dérivation de nouveaux types complexes par le biais du mécanisme de restriction, reportez-vous au site Internet de W3C.</span><span class="sxs-lookup"><span data-stu-id="b33e1-107">For comprehensive information about deriving new complex types by using the restriction mechanism, refer to the W3C website.</span></span> <span data-ttu-id="b33e1-108">Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="b33e1-108">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="b33e1-109">Pour dériver un type global complexe par restriction, dans un autre emplacement dans l’arborescence du schéma, commencez par insérer un nouveau **enregistrement** nœud à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="b33e1-109">To derive from a complex global type by restriction, in another location in the schema tree, begin by inserting a new **Record** node at the desired location.</span></span> <span data-ttu-id="b33e1-110">Définissez ensuite sa **Base Data Type** nom à la propriété d’un type global complexe.</span><span class="sxs-lookup"><span data-stu-id="b33e1-110">Then set its **Base Data Type** property to the name of a complex global type.</span></span> <span data-ttu-id="b33e1-111">Enfin, modifiez le paramètre de la **Derived By** propriété sa valeur par défaut de **Extension** (au moins un type de base de données est la valeur) à **Restriction**.</span><span class="sxs-lookup"><span data-stu-id="b33e1-111">Finally, change the setting of the **Derived By** property from its default value of **Extension** (at least when a base data type is set) to **Restriction**.</span></span>  
  
 <span data-ttu-id="b33e1-112">Dans l’exemple suivant, **BillingAddress** est le nom de récemment insérées **enregistrement** nœud, et **GlobalAddrType** est le nom du type complexe global à partir de laquelle elle est dérivé et envisage de se limiter.</span><span class="sxs-lookup"><span data-stu-id="b33e1-112">In the following example, **BillingAddress** is the name of the newly inserted **Record** node, and **GlobalAddrType** is the name of the complex global type from which it derives, and intends to restrict.</span></span> <span data-ttu-id="b33e1-113">Dans l’arborescence du schéma, une structure de nœud en double sera affichée sous le nœud nommé **BillingAddress**, identique à la structure de nœuds adjacents sous le nœud nommé **ShippingAddress**.</span><span class="sxs-lookup"><span data-stu-id="b33e1-113">In the schema tree view, a duplicate node structure would be displayed below the node named **BillingAddress**, identical to the adjacent node structure under the node named **ShippingAddress**.</span></span> <span data-ttu-id="b33e1-114">La différence est que le **BillingAddress** structure de nœud sera soumis à des restrictions possibles pour le type de base de données **GlobalAddrType**et le **ShippingAddress** structure restera identique au type de base de données **GlobalAddrType**.</span><span class="sxs-lookup"><span data-stu-id="b33e1-114">The difference between them is that the **BillingAddress** node structure will be subject to possible restrictions to the base data type **GlobalAddrType**, and the **ShippingAddress** structure will remain identical to the base data type **GlobalAddrType**.</span></span>  
  
 <span data-ttu-id="b33e1-115">Dès lors que vous avez choisi de limiter le type de données de base, il vous est interdit d'insérer de nouveaux nœuds, mais vous pouvez modifier les propriétés des nœuds existants pour limiter davantage leurs valeurs possibles ou leur comportement.</span><span class="sxs-lookup"><span data-stu-id="b33e1-115">Because you have chosen to restrict the base data type, you are not allowed to insert any new nodes, but you can change the properties of the existing nodes to further restrict their possible values or behavior.</span></span>  
  
-   <span data-ttu-id="b33e1-116">Avant, avec la **Derived By** propriété toujours la valeur **Extension**.</span><span class="sxs-lookup"><span data-stu-id="b33e1-116">Before, with the **Derived By** property still set to **Extension**.</span></span>  
  
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
  
-   <span data-ttu-id="b33e1-117">Après avoir basculé le **Derived By** propriété à partir de **Extension** à **Restriction**.</span><span class="sxs-lookup"><span data-stu-id="b33e1-117">After switching the **Derived By** property from **Extension** to **Restriction**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b33e1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b33e1-118">See Also</span></span>  
 [<span data-ttu-id="b33e1-119">Dérivation de Type Global complexe</span><span class="sxs-lookup"><span data-stu-id="b33e1-119">Complex Global Type Derivation</span></span>](../core/complex-global-type-derivation.md)