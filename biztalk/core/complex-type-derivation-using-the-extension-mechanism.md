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
# <a name="complex-type-derivation-using-the-extension-mechanism"></a><span data-ttu-id="812d7-102">Dérivation de types complexes à l'aide du mécanisme d'extension</span><span class="sxs-lookup"><span data-stu-id="812d7-102">Complex Type Derivation Using the Extension Mechanism</span></span>
<span data-ttu-id="812d7-103">Un type complexe dérivé par extension est un sur-ensemble fonctionnel de son type de données de base.</span><span class="sxs-lookup"><span data-stu-id="812d7-103">A complex type derived by extension is a functional superset of its base data type.</span></span> <span data-ttu-id="812d7-104">Comme son nom l'indique, son type de données de base est la base du type en cours de définition. Les différences par rapport au type de base sont additives.</span><span class="sxs-lookup"><span data-stu-id="812d7-104">As the name implies, its base data type is the basis for the type being defined, where the differences from the base type are additive.</span></span> <span data-ttu-id="812d7-105">Cette rubrique fournit un exemple dans lequel les deux éléments **ShippingAddress** et **BillingAddress** sont basées sur le type global complex **GlobalAddrType**.</span><span class="sxs-lookup"><span data-stu-id="812d7-105">This topic provides an example in which the two elements **ShippingAddress** and **BillingAddress** are based on the complex global type **GlobalAddrType**.</span></span> <span data-ttu-id="812d7-106">**ShippingAddress** est simplement définie pour être de type **GlobalAddrType**, alors que **BillingAddress** est défini pour étendre le type **GlobalAddrType**.</span><span class="sxs-lookup"><span data-stu-id="812d7-106">**ShippingAddress** is simply defined to be of type **GlobalAddrType**, whereas **BillingAddress** is defined to extend the type **GlobalAddrType**.</span></span> <span data-ttu-id="812d7-107">À la fin de l’exemple, un élément supplémentaire est ajouté à **BillingAddress**, nommé **service**, avec un type de chaîne et la valeur par défaut comptes fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="812d7-107">At the end of the example, an additional element is added to **BillingAddress**, named **Department**, with a type of string and a default value of Accounts Payable.</span></span>  
  
 <span data-ttu-id="812d7-108">Pour obtenir des informations complètes sur la dérivation de nouveaux types complexes par le biais du mécanisme d'extension, reportez-vous au site Internet de W3C.</span><span class="sxs-lookup"><span data-stu-id="812d7-108">For comprehensive information about deriving new complex types by using the extension mechanism, refer to the W3C website.</span></span> <span data-ttu-id="812d7-109">Pour obtenir différents liens correspondant à ces informations et autres sites Web, consultez [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="812d7-109">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="812d7-110">Pour dériver un type global complexe par extension, à un autre emplacement dans l’arborescence du schéma, commencez par insérer un nouveau **enregistrement** nœud à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="812d7-110">To derive from a complex global type by extension, in another location in the schema tree, begin by inserting a new **Record** node at the desired location.</span></span> <span data-ttu-id="812d7-111">Définissez ensuite sa **Base Data Type** nom à la propriété d’un type global complexe.</span><span class="sxs-lookup"><span data-stu-id="812d7-111">Then set its **Base Data Type** property to the name of a complex global type.</span></span>  
  
 <span data-ttu-id="812d7-112">Dans l’exemple suivant, **BillingAddress** est le nom de récemment insérées **enregistrement** nœud, et **GlobalAddrType** est le nom du type complexe global à partir de laquelle elle est dérivé et essaie de s’étendre.</span><span class="sxs-lookup"><span data-stu-id="812d7-112">In the following example, **BillingAddress** is the name of the newly inserted **Record** node, and **GlobalAddrType** is the name of the complex global type from which it derives, and intends to extend.</span></span> <span data-ttu-id="812d7-113">Dans l’arborescence du schéma, une fois **Base Data Type** a été défini sur **GlobalAddrType**, une structure de nœud en double s’affiche sous le nœud nommé **BillingAddress**, identique à la structure de nœuds adjacents sous le nœud nommé **ShippingAddress**.</span><span class="sxs-lookup"><span data-stu-id="812d7-113">In the schema tree view, after **Base Data Type** has been set to **GlobalAddrType**, a duplicate node structure would be displayed below the node named **BillingAddress**, identical to the adjacent node structure under the node named **ShippingAddress**.</span></span> <span data-ttu-id="812d7-114">La différence est que le **BillingAddress** structure de nœud sera extensible au-delà du type de base de données **GlobalAddrType**et le **ShippingAddress** structure restera identique au type de base de données **GlobalAddrType**.</span><span class="sxs-lookup"><span data-stu-id="812d7-114">The difference between them is that the **BillingAddress** node structure will be extensible beyond the base data type **GlobalAddrType**, and the **ShippingAddress** structure will remain identical to the base data type **GlobalAddrType**.</span></span>  
  
-   <span data-ttu-id="812d7-115">Avant, avec un nœud nouvellement inséré nommé **BillingAddress**.</span><span class="sxs-lookup"><span data-stu-id="812d7-115">Before, with a newly inserted node named **BillingAddress**.</span></span>  
  
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
  
-   <span data-ttu-id="812d7-116">Après avoir dérivé d’un type complex de base **GlobalAddrType**, par extension.</span><span class="sxs-lookup"><span data-stu-id="812d7-116">After deriving from the complex base type **GlobalAddrType**, by extension.</span></span>  
  
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
  
 <span data-ttu-id="812d7-117">Vous spécifiez des extensions pour le type de base de données par l’insertion de nœuds dans le **BillingAddress** nœud dans l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="812d7-117">You specify extensions to the base data type by inserting nodes into the **BillingAddress** node in the schema tree.</span></span> <span data-ttu-id="812d7-118">Le fragment XSD suivant montre comment l’élément d’extension vide est développé lorsque un **groupe séquence** nœud est inséré en tant que nouvel enfant du **BillingAddress** nœud, puis un **élément de champ**  nœud, nommé **type de paiement**, est inséré en tant que nœud enfant de la **groupe séquence** nœud.</span><span class="sxs-lookup"><span data-stu-id="812d7-118">The following XSD fragment shows how the empty extension element is expanded when a **Sequence Group** node is inserted as a new child of the **BillingAddress** node and then a **Field Element** node, named **PaymentType**, is inserted as a child node of the **Sequence Group** node.</span></span>  
  
```  
<xs:extension base="GlobalAddrType">  
    <xs:sequence>  
        <xs:element default="Accounts Payable"  
            name="Department" type="xs:string" />  
    </xs:sequence>  
</xs:extension>  
```  
  
## <a name="see-also"></a><span data-ttu-id="812d7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="812d7-119">See Also</span></span>  
 [<span data-ttu-id="812d7-120">Dérivation de Type Global complexe</span><span class="sxs-lookup"><span data-stu-id="812d7-120">Complex Global Type Derivation</span></span>](../core/complex-global-type-derivation.md)