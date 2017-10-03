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
# <a name="simple-type-derivation-using-the-list-mechanism"></a><span data-ttu-id="93940-102">Dérivation de type simple à l'aide du mécanisme de liste</span><span class="sxs-lookup"><span data-stu-id="93940-102">Simple Type Derivation Using the List Mechanism</span></span>
<span data-ttu-id="93940-103">Lorsque vous déduisez un nouveau type simple à partir d'un type simple existant à l’aide du mécanisme de liste, vous spécifiez que la valeur pour l'attribut ou l'élément peut correspondre à une liste des valeurs du type spécifié séparées par des espaces.</span><span class="sxs-lookup"><span data-stu-id="93940-103">When you derive a new simple type from an existing simple type by using the list mechanism, you are specifying that the value for this attribute or element can be a space-separated list of values of the specified type.</span></span> <span data-ttu-id="93940-104">Vous pouvez par exemple spécifier qu'une valeur d'attribut ou d’élément est une liste d'entiers séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="93940-104">For example, you can specify that an attribute or element value is a space-separated list of integers.</span></span>  
  
 <span data-ttu-id="93940-105">Pour obtenir des informations complètes sur la dérivation de nouveaux types simples par le biais du mécanisme de liste, consultez le site Web de W3C.</span><span class="sxs-lookup"><span data-stu-id="93940-105">For comprehensive information about deriving new simple types by using the list mechanism, refer to the W3C Web site.</span></span> <span data-ttu-id="93940-106">Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="93940-106">For various links to this and other Web sites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="93940-107">Pour dériver un type simple sous la forme d’une liste de ce type, sélectionnez la **Fieldelement** nœud ou **attribut de champ** dans l’arborescence du schéma, puis, dans la fenêtre Propriétés, sélectionnez un type simple dans la liste déroulante. la liste pour le **Base Data Type** propriété.</span><span class="sxs-lookup"><span data-stu-id="93940-107">To derive a simple type as a list of that type, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property.</span></span> <span data-ttu-id="93940-108">Dès que vous sélectionnez une valeur pour cette propriété, le **Derived By** propriété change automatiquement de sa valeur par défaut à **Restriction**, qui sert de la valeur par défaut pour la dérivation de type.</span><span class="sxs-lookup"><span data-stu-id="93940-108">As soon as you select a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation.</span></span> <span data-ttu-id="93940-109">Vous devez modifier le **Derived By** propriété à partir de **Restriction** à **liste**, ce qui entraîne la **Base Data Type** doit être renommé en tant que propriété le **Type d’élément** propriété (plus, la propriété renommée déplace vers une autre position dans la liste des propriétés en raison de l’ordre de tri alphabétique des propriétés).</span><span class="sxs-lookup"><span data-stu-id="93940-109">You must change the **Derived By** property from **Restriction** to **List**, which causes the **Base Data Type** property to be renamed as the **Item Type** property (incidentally, the renamed property moves to a different position in the property list due to the alphabetical sorting of the properties).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93940-110">Vous pouvez utiliser les mécanismes de liste et de restriction ensemble, en créant une dérivation de type simple nommée à l’aide du mécanisme de restriction, puis en utilisant celle-ci comme type d’élément d'une autre dérivation de type simple à l'aide du mécanisme de liste.</span><span class="sxs-lookup"><span data-stu-id="93940-110">You can use the restriction and list mechanisms together, creating a named simple type derivation by using the restriction mechanism, and then using that as the item type in another simple type derivation by using the list mechanism.</span></span> <span data-ttu-id="93940-111">Vous pouvez ainsi obtenir une valeur qui serait obligatoirement une liste de chaînes séparées par des espaces appartenant à une énumération de chaînes particulière.</span><span class="sxs-lookup"><span data-stu-id="93940-111">This can result, for example, in a value that is constrained to be a list of space-separated strings belonging to a particular enumerated set of strings.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="93940-112">Il peut s’avérer compliqué d'utiliser le mécanisme de liste pour la dérivation de type simple lorsque le type d’élément que vous choisissez correspond à un type autorisant les espaces, telles que des chaînes.</span><span class="sxs-lookup"><span data-stu-id="93940-112">Using the list mechanism for simple type derivation can be complicated when the item type you choose is one that itself allows spaces, such as strings.</span></span> <span data-ttu-id="93940-113">Cela tient au fait que le mécanisme de liste utilise des espaces pour séparer des valeurs du type autorisé dans la liste.</span><span class="sxs-lookup"><span data-stu-id="93940-113">This is because the list mechanism uses spaces to separate values of the allowed type in the list.</span></span>  
  
 <span data-ttu-id="93940-114">Lorsque vous modifiez un **Fieldelement** nœud ou **attribut de champ** nœud de ne pas avoir de données de type pour un type de base de données (en commençant ainsi le processus de dérivation de type simple), puis définissez le **Derived By** propriété **liste**, vous pouvez observer le changement suivant dans le fragment correspondant dans la vue XSD :</span><span class="sxs-lookup"><span data-stu-id="93940-114">When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), and then set the **Derived By** property to **List**, you can observe the following change in the corresponding fragment in the XSD view:</span></span>  
  
-   <span data-ttu-id="93940-115">Avant, avec un nouvellement inséré **Fieldelement** nœud nommé **ZipCodeList**.</span><span class="sxs-lookup"><span data-stu-id="93940-115">Before, with a newly inserted **Field Element** node named **ZipCodeList**.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   <span data-ttu-id="93940-116">Après avoir défini la **Base Data Type** propriété xs : Integer et la **Derived By** propriété **liste** (après laquelle le **Base Data Type**propriété est renommée pour être le **Type d’élément** propriété).</span><span class="sxs-lookup"><span data-stu-id="93940-116">After setting the **Base Data Type** property to xs:integer, and setting the **Derived By** property to **List** (after which the **Base Data Type** property is renamed to be the **Item Type** property).</span></span>  
  
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
>  <span data-ttu-id="93940-117">Dans un schéma de la vie réelle, il est préférable d’abord définir et nommer une dérivation de type simple d’entier qui limiterait l’entier à cinq chiffres, avant de dériver le **ZipCodeList** élément à partir de ce type, efficace en limitant la liste à entiers de cinq chiffres.</span><span class="sxs-lookup"><span data-stu-id="93940-117">In a real-life schema, it would be better to first define and name a simple type derivation of integer that restricts the integer to five digits, and then to derive the **ZipCodeList** element from that type, effectively limiting the list to integers having five digits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93940-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93940-118">See Also</span></span>  
 [<span data-ttu-id="93940-119">Dérivation de Type simple</span><span class="sxs-lookup"><span data-stu-id="93940-119">Simple Type Derivation</span></span>](../core/simple-type-derivation.md)