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
# <a name="simple-type-derivation-using-the-union-mechanism"></a><span data-ttu-id="03347-102">Dérivation de type simple à l'aide du mécanisme d'union</span><span class="sxs-lookup"><span data-stu-id="03347-102">Simple Type Derivation Using the Union Mechanism</span></span>
<span data-ttu-id="03347-103">Lorsque vous dérivez un nouveau type simple à partir d'un type simple existant à l'aide du mécanisme d'union, vous spécifiez que la valeur de cet attribut ou de cet élément peut appartenir à plus d'un type, d'après une liste de types que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="03347-103">When you derive a new simple type from an existing simple type by using the union mechanism, you are specifying that the value for this attribute or element can be of more than one type, according to a list of types that you specify.</span></span> <span data-ttu-id="03347-104">Par exemple, vous pouvez spécifier qu'une valeur d'attribut ou d'élément est une valeur de date, d'heure ou de date/heure.</span><span class="sxs-lookup"><span data-stu-id="03347-104">For example, you can specify that an attribute or element value is either a date, a time, or a date/time value.</span></span>  
  
 <span data-ttu-id="03347-105">Pour obtenir des informations complètes sur la dérivation de nouveaux types simples par le biais du mécanisme d'union, reportez-vous au site Web de W3C.</span><span class="sxs-lookup"><span data-stu-id="03347-105">For comprehensive information about deriving new simple types by using the union mechanism, refer to the W3C website.</span></span> <span data-ttu-id="03347-106">Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="03347-106">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="03347-107">Pour dériver un type simple sous la forme d’une union de plusieurs types, sélectionnez la **Fieldelement** nœud ou **attribut de champ** dans l’arborescence du schéma, puis, dans la fenêtre Propriétés, sélectionnez un type simple à partir de la liste déroulante pour le **Base Data Type** propriété.</span><span class="sxs-lookup"><span data-stu-id="03347-107">To derive a simple type as a union of several possible types, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property.</span></span> <span data-ttu-id="03347-108">Dès que vous avez sélectionné une valeur pour cette propriété, le **Derived By** propriété change automatiquement de sa valeur par défaut à **Restriction**, qui sert de la valeur par défaut pour la dérivation de type.</span><span class="sxs-lookup"><span data-stu-id="03347-108">As soon as you have selected a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation.</span></span> <span data-ttu-id="03347-109">Vous devez modifier le **Derived By** propriété à partir de **Restriction** à **Union**, ce qui entraîne la **Base Data Type** doit être renommé en tant que propriété le **Types de membres** propriété (plus, la propriété renommée déplace vers une autre position dans la liste des propriétés en raison de l’ordre de tri alphabétique des propriétés).</span><span class="sxs-lookup"><span data-stu-id="03347-109">You must change the **Derived By** property from **Restriction** to **Union**, which causes the **Base Data Type** property to be renamed as the **Member Types** property (incidentally, the renamed property moves to a different position in the property list due to the alphabetical sorting of the properties).</span></span>  
  
 <span data-ttu-id="03347-110">Enfin, vous pouvez utiliser les cases à cocher dans la **Types de membres** liste de contrôle de liste déroulante pour sélectionner les types supplémentaires afin d’autoriser les valeurs correspondantes dans les messages d’instance.</span><span class="sxs-lookup"><span data-stu-id="03347-110">Finally, you can use the check boxes in the **Member Types** drop-down checklist to select additional types to allow for corresponding values in instance messages.</span></span>  
  
 <span data-ttu-id="03347-111">Lorsque vous modifiez un **Fieldelement** nœud ou **attribut de champ** nœud de ne pas avoir de données de type pour un type de base de données (en commençant ainsi le processus de dérivation de type simple), puis définissez le **Derived By** propriété **Union**, vous pouvez observer le changement suivant dans le fragment correspondant dans la vue XSD.</span><span class="sxs-lookup"><span data-stu-id="03347-111">When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), and then set the **Derived By** property to **Union**, you can observe the following change in the corresponding fragment in the XSD view.</span></span>  
  
-   <span data-ttu-id="03347-112">Avant, avec un nouvellement inséré **Fieldelement** nœud nommé **DatesAndOrTimes**.</span><span class="sxs-lookup"><span data-stu-id="03347-112">Before, with a newly inserted **Field Element** node named **DatesAndOrTimes**.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   <span data-ttu-id="03347-113">Après avoir défini la **Base Data Type** propriété **xs : date**et en définissant le **Derived By** propriété **Union** (après laquelle le  **Type de base de données** propriété est renommée pour être le **Types de membres** propriété), puis en sélectionnant également **xs : DateTime** et **xs : Time** en tant que supplémentaires autorisées des types dans les **Types de membres** liste de contrôle de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="03347-113">After setting the **Base Data Type** property to **xs:date**, and setting the **Derived By** property to **Union** (after which the **Base Data Type** property is renamed to be the **Member Types** property), and then also selecting **xs:datetime** and **xs:time** as additional allowed types in the **Member Types** drop-down checklist.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="03347-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03347-114">See Also</span></span>  
 [<span data-ttu-id="03347-115">Dérivation de Type simple</span><span class="sxs-lookup"><span data-stu-id="03347-115">Simple Type Derivation</span></span>](../core/simple-type-derivation.md)