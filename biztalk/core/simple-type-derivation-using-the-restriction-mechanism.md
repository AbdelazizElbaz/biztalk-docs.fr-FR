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
# <a name="simple-type-derivation-using-the-restriction-mechanism"></a><span data-ttu-id="8cbcb-102">Dérivation de type simple à l'aide du mécanisme de restriction</span><span class="sxs-lookup"><span data-stu-id="8cbcb-102">Simple Type Derivation Using the Restriction Mechanism</span></span>

## <a name="overview"></a><span data-ttu-id="8cbcb-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8cbcb-103">Overview</span></span>
<span data-ttu-id="8cbcb-104">Lorsque vous déduisez un nouveau type simple à l'aide du mécanisme de restriction à partir d'un type simple existant, vous limitez généralement les valeurs autorisées dans un message d'instance pour cette valeur d'attribut ou d'élément à un sous-ensemble des valeurs autorisées par le type simple de base.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-104">When you derive a new simple type from an existing simple type by using the restriction mechanism, you are typically restricting the values allowed in an instance message for that attribute or element value to a subset of those values allowed by the base simple type.</span></span> <span data-ttu-id="8cbcb-105">Par exemple, vous pouvez limiter un type de chaîne à être une chaîne énumérée parmi plusieurs autres.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-105">For example, you can restrict a string type to be one of several enumerated strings.</span></span>  
  
 <span data-ttu-id="8cbcb-106">Pour obtenir des informations complètes sur la dérivation de nouveaux types simples par le biais du mécanisme de restriction, reportez-vous au site Internet de W3C.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-106">For comprehensive information about deriving new simple types by using the restriction mechanism, refer to the W3C website.</span></span> <span data-ttu-id="8cbcb-107">Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="8cbcb-107">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
## <a name="field-element-and-field-attribute"></a><span data-ttu-id="8cbcb-108">Élément de champ et d’attribut de champ</span><span class="sxs-lookup"><span data-stu-id="8cbcb-108">Field Element and Field Attribute</span></span>
 <span data-ttu-id="8cbcb-109">Pour dériver un type simple à l’aide de restriction, sélectionnez la **Fieldelement** nœud ou **attribut de champ** dans l’arborescence du schéma, puis, dans la fenêtre Propriétés, sélectionnez un type simple dans la liste déroulante. la liste pour le **Base Data Type** propriété.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-109">To derive a simple type by using restriction, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property.</span></span> <span data-ttu-id="8cbcb-110">Dès que vous avez sélectionné une valeur pour cette propriété, le **Derived By** propriété change automatiquement de sa valeur par défaut à **Restriction**, qui sert de la valeur par défaut pour la dérivation de type.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-110">As soon as you have selected a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation.</span></span> <span data-ttu-id="8cbcb-111">En outre, une toute nouvelle catégorie de propriétés, appelée **Restriction**, devient disponible dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-111">Also, a whole new category of properties, called **Restriction**, becomes available in the Properties window.</span></span>  
  
 <span data-ttu-id="8cbcb-112">En fonction du type de données de base que vous sélectionnez, les propriétés pouvant être définies dans cette nouvelle catégorie sont différentes.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-112">Depending on the base data type you select, different properties are available to be set in this new category.</span></span> <span data-ttu-id="8cbcb-113">Par exemple, si le type de base de données est numérique, les propriétés **MaxFacet Type** (lorsque **MaxFacet Value** est défini), **MaxFacet Value**, **MinFacet Type** (lorsque **MinFacet Value** est défini), et **MinFacet Value** sont disponibles pour définir une plage inclusive ou exclusive de valeurs autorisées.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-113">For example, if the base data type is numeric, the properties **MaxFacet Type** (when **MaxFacet Value** is set), **MaxFacet Value**, **MinFacet Type** (when **MinFacet Value** is set), and **MinFacet Value** are available for defining an inclusive or exclusive range of allowed values.</span></span> <span data-ttu-id="8cbcb-114">Si le type de base de données est un type chaîne, la **longueur**, **longueur maximale**, et **longueur minimale** propriétés sont disponibles pour limiter la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-114">If the base data type is a string type, the **Length**, **Maximum Length**, and **Minimum Length** properties are available for constraining the length of the string.</span></span>  
  
 <span data-ttu-id="8cbcb-115">Pour plus d’informations sur les différentes propriétés de la restriction des nœuds de champ, consultez la **propriétés de nœud élément de champ** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="8cbcb-115">For more information about the various restriction properties of field nodes, see the **Field Element Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="8cbcb-116">Lorsque vous modifiez un **Fieldelement** nœud ou **attribut de champ** nœud de l’utilisation d’un type de données ayant un type de base de données (et démarrer le processus de dérivation de type simple), laissez le  **Dérivé par** propriété **Restriction**et fournir une restriction basée sur une énumération pour les valeurs de chaîne autorisée, vous pouvez observer les modifications suivantes dans le fragment correspondant dans la vue XSD :</span><span class="sxs-lookup"><span data-stu-id="8cbcb-116">When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), leave the **Derived By** property set to **Restriction**, and provide an enumeration-based restriction to the allowed string values, you can observe the following changes in the corresponding fragment in the XSD view:</span></span>  
  
-   <span data-ttu-id="8cbcb-117">Avant, avec un nouvellement inséré **Fieldelement** nœud nommé **WestCoastStates**.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-117">Before, with a newly inserted **Field Element** node named **WestCoastStates**.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
-   <span data-ttu-id="8cbcb-118">Après avoir défini la **Base Data Type** à la propriété « xs : String » et laisser la valeur par défaut de dérivation de **Restriction** pour le **Derived By** propriété.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-118">After setting the **Base Data Type** property to "xs:string", and leaving the derivation default of **Restriction** for the **Derived By** property.</span></span>  
  
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
  
-   <span data-ttu-id="8cbcb-119">Après avoir défini la **énumération** propriété dans la catégorie Restriction sur les noms des trois états de la côte ouest des États-Unis continentaux.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-119">After setting the **Enumeration** property in the Restriction category to the names of the three states on the west coast of the continental United States.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8cbcb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cbcb-120">See Also</span></span>  
 [<span data-ttu-id="8cbcb-121">Dérivation de Type simple</span><span class="sxs-lookup"><span data-stu-id="8cbcb-121">Simple Type Derivation</span></span>](../core/simple-type-derivation.md)