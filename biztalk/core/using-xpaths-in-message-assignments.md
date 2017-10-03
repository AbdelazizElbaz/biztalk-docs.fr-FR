---
title: Utilisation des XPaths dans une assignation de Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XPaths, XPath function
- XPaths, messages
- code samples, XPaths
- messages, XPaths
- XPath function
- XPaths, code samples
- XPaths, nodes
ms.assetid: f2e12409-bb77-4315-b03b-5c7736ae51d5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9ec1e5b56f382601c79324df8651c91c483cb4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-xpaths-in-message-assignments"></a><span data-ttu-id="44135-102">Utilisation des XPaths dans une assignation de Message</span><span class="sxs-lookup"><span data-stu-id="44135-102">Using XPaths in Message Assignments</span></span>
<span data-ttu-id="44135-103">Vous pouvez utiliser la **xpath** fonction pour attribuer une valeur XPath à une partie de message, ou pour affecter une valeur à un XPath qui fait référence à une partie de message.</span><span class="sxs-lookup"><span data-stu-id="44135-103">You can use the **xpath** function to assign an XPath value to a message part, or to assign a value to an XPath that refers to a message part.</span></span> <span data-ttu-id="44135-104">Pour plus d’informations sur l’affectation à des messages et les parties de message, consultez [construction de Messages](../core/constructing-messages.md).</span><span class="sxs-lookup"><span data-stu-id="44135-104">For more information on assigning to messages and message parts, see [Constructing Messages](../core/constructing-messages.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44135-105">Pour plus d'informations sur la fonction xpath, voir la documentation tierce sur le langage XML (XPath).</span><span class="sxs-lookup"><span data-stu-id="44135-105">For more information on the xpath function, see third-party documentation on the XML Path Language (XPath).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44135-106">L’utilisation de la **xpath** fonction n’est pas limitée à l’assignation du message.</span><span class="sxs-lookup"><span data-stu-id="44135-106">The use of the **xpath** function is not limited to message assignment.</span></span> <span data-ttu-id="44135-107">Vous pouvez également l'utiliser dans d'autres expressions, telles que :</span><span class="sxs-lookup"><span data-stu-id="44135-107">You can also use it in any expression, for example:</span></span>  
  
```  
If ((System.Double) xpath(_RequestMessage.part, "number(//book[last()]/price)") == 75.00 && (System.Boolean) xpath(msgBoolean, "string(//boolean)") == false)...  
```  
  
> [!NOTE]
>  <span data-ttu-id="44135-108">Si vous souhaitez assigner une valeur à une chaîne, utilisez la fonction XPath string().</span><span class="sxs-lookup"><span data-stu-id="44135-108">If you want to assign a value to a string, use the XPath string() function.</span></span> <span data-ttu-id="44135-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="44135-109">For example:</span></span>  
  
```  
myString = xpath(msg, "string(/*/book[1]/title)");  
```  
  
> [!NOTE]
>  <span data-ttu-id="44135-110">Le moteur ne tient pas compte des schémas. Vous pouvez donc uniquement lire les valeurs à partir d'un nœud existant ou écrire des valeurs dans ce nœud d'un message (le chemin d'accès complet doit être indiqué), sinon le moteur lève une exception.</span><span class="sxs-lookup"><span data-stu-id="44135-110">The engine is not schema-aware, so you can only read values from or write values to a node that exists in the containing message (the complete path must exist), or the engine will raise an exception.</span></span> <span data-ttu-id="44135-111">Ceci est vrai même si vous fournissez une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="44135-111">This is true even if you supply a default value.</span></span>  
  
## <a name="assigning-to-an-xpath-in-a-message-part"></a><span data-ttu-id="44135-112">Affectation à un XPath dans une partie de message</span><span class="sxs-lookup"><span data-stu-id="44135-112">Assigning to an XPath in a message part</span></span>  
 <span data-ttu-id="44135-113">Examinez le schéma suivant :</span><span class="sxs-lookup"><span data-stu-id="44135-113">Consider the following schema:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="catalog">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="book">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="title" type="xs:string" />  
              <xs:element name="author">  
                <xs:complexType>  
                  <xs:sequence>  
                    <xs:element name="FirstName" type="xs:string" />  
                    <xs:element name="LastName" type="xs:string" />  
                  </xs:sequence>  
                </xs:complexType>  
              </xs:element>  
              <xs:element name="price" type="xs:string" />  
            </xs:sequence>  
            <xs:attribute name="country" type="xs:string" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="44135-114">Vous pouvez utiliser la fonction de la façon indiquée ci-dessous pour définir les valeur d'une instance de document de ce type de schéma :</span><span class="sxs-lookup"><span data-stu-id="44135-114">You can use the  function as follows to set values on a document instance of that schema type:</span></span>  
  
```  
//assumes that a message named _ResponseMessage is already constructed  
_ResponseMessage.part = _RequestMessage.part;  
xpath(_ResponseMessage.part, "/*/book[1]/@country") = "USA";  
xpath(_ResponseMessage.part, "/*/book[1]/title") = "Legends";  
xpath(_ResponseMessage.part, "/*/book[1]/author/FirstName") = "A";  
xpath(_ResponseMessage.part, "/*/book[1]/author/LastName") = "B";  
xpath(_ResponseMessage.part, "/*/book[1]/price") = 50;  
```  
  
## <a name="assigning-to-a-message-part-from-an-xpath"></a><span data-ttu-id="44135-115">Affectation à une partie de message à partir d'un XPath</span><span class="sxs-lookup"><span data-stu-id="44135-115">Assigning to a message part from an XPath</span></span>  
  
```  
//assumes that a message named objMessage is already constructed  
objMessage.BooleanPart = xpath("false()");  
objMessage.IntPart = xpath("100");  
objMessage.StringPart = xpath("'Hello'");  
objMessage.StringPart2 = xpath("'World'");  
```  
  
## <a name="using-xpath-to-assign-from-nodes-and-node-sets"></a><span data-ttu-id="44135-116">Utilisation de XPath pour affecter des valeurs à partir de nœuds et de jeux de nœuds</span><span class="sxs-lookup"><span data-stu-id="44135-116">Using XPath to assign from nodes and node sets</span></span>  
 <span data-ttu-id="44135-117">Vous pouvez également utiliser XPath pour affecter des nœuds et jeux de nœuds XML à un élément XML, une classe, ou encore un message basé sur un schéma ou une classe.</span><span class="sxs-lookup"><span data-stu-id="44135-117">You can also use XPath to assign XML nodes and node sets to an XML element, a class, or a schema-based or class-based message.</span></span>  
  
 <span data-ttu-id="44135-118">Supposons que vous utilisiez une classe sérialisable XML intitulée « Book » (livre, en anglais). Examinez les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="44135-118">Suppose you have an XML-serializable class called Book, and consider the following examples:</span></span>  
  
```  
[Serializable]  
Class Book {...}  
```  
  
 <span data-ttu-id="44135-119">Exemple un : sélectionnez le quatrième élément « book » du catalogue et affectez-le à une variable d'élément XML :</span><span class="sxs-lookup"><span data-stu-id="44135-119">Example One — select the fourth book element from the catalog, and assign it to an XML element variable:</span></span>  
  
```  
myXmlElement = xpath(myMsg, "/catalog/book[3]");  
```  
  
 <span data-ttu-id="44135-120">Exemple deux : sélectionnez le quatrième élément « book » du catalogue et convertissez-le à l'aide de la désérialisation XML en une instance de classe Book :</span><span class="sxs-lookup"><span data-stu-id="44135-120">Example Two — select the fourth book element from the catalog, and convert it using XML deserialization into a Book class instance:</span></span>  
  
```  
myBook = xpath(myMsg, "/catalog/book[3]");  
```  
  
 <span data-ttu-id="44135-121">Exemple trois : sélectionnez le quatrième élément « book » du catalogue et convertissez-le en un message de type Book :</span><span class="sxs-lookup"><span data-stu-id="44135-121">Example Three — select the fourth book element from the catalog, and convert it a message of type Book:</span></span>  
  
```  
myBookMsg = xpath(myMsg, "/catalog/book[3]");  
```  
  
 <span data-ttu-id="44135-122">Exemple quatre : sélectionnez tous les éléments « book » du catalogue, où MyMethod utilise un XmlNodeSet en tant que paramètre :</span><span class="sxs-lookup"><span data-stu-id="44135-122">Example Four — select all book elements in the catalog, where MyMethod takes an XmlNodeSet as a parameter:</span></span>  
  
```  
MyMethod(xpath(myMsg, "/catalog/book"));  
```  
  
 <span data-ttu-id="44135-123">Exemple cinq : ajoutez un élément « book » au conteneur « BookOfTheMonth » :</span><span class="sxs-lookup"><span data-stu-id="44135-123">Example Five — add a book element to the "BookOfTheMonth" container:</span></span>  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BookOfTheMonth") = myBook;  
```  
  
 <span data-ttu-id="44135-124">Exemple six : ajoutez tous les livres dont le prix est inférieur ou égal à vingt à un ensemble de livres recommandés :</span><span class="sxs-lookup"><span data-stu-id="44135-124">Example Six — add all books that are priced at twenty or less to a set of recommended books:</span></span>  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BestPriceBooks") = xpath(MyMsg, "/catalog/book[@price <= 20]");  
```  
  
 <span data-ttu-id="44135-125">Exemple sept : appelez le code utilisateur retournant un élément XML :</span><span class="sxs-lookup"><span data-stu-id="44135-125">Example Seven — call user code that returns an XML element:</span></span>  
  
```  
xpath(MyMsg2, "/RecommendedBooks/AdvertisedByPartner") = GetPartnerAdvertisedBook();  
```  
  
 <span data-ttu-id="44135-126">Avant d'appliquer les exemples cinq et sept :</span><span class="sxs-lookup"><span data-stu-id="44135-126">Before applying examples five and seven:</span></span>  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth/>  
       <BestPriceBooks/>  
       <AdvertisedByPartner/>  
</RecommendedBooks>  
```  
  
 <span data-ttu-id="44135-127">Après application des exemples cinq et sept :</span><span class="sxs-lookup"><span data-stu-id="44135-127">After applying examples five and seven:</span></span>  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth>  
              <Book country="USA">  
                     <title>McSharry</title>  
                     <author>  
                            <FirstName>Nancy</FirstName>  
                            <LastName>Jensen</LastName>  
                     </author>  
              </Book>  
       </BookOfTheMonth>  
       <BestPriceBooks/>  
       <AdvertisedByPartner>  
              <Book country="USA">  
                     <title>The Rooster</title>  
                     <author>  
                            <FirstName>Mindy</FirstName>  
                            <LastName>Martin</LastName>  
                     </author>  
              </Book>  
       </AdvertisedByPartner>  
</RecommendedBooks>  
```