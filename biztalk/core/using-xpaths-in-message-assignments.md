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
# <a name="using-xpaths-in-message-assignments"></a>Utilisation des XPaths dans une assignation de Message
Vous pouvez utiliser la **xpath** fonction pour attribuer une valeur XPath à une partie de message, ou pour affecter une valeur à un XPath qui fait référence à une partie de message. Pour plus d’informations sur l’affectation à des messages et les parties de message, consultez [construction de Messages](../core/constructing-messages.md).  
  
> [!NOTE]
>  Pour plus d'informations sur la fonction xpath, voir la documentation tierce sur le langage XML (XPath).  
  
> [!NOTE]
>  L’utilisation de la **xpath** fonction n’est pas limitée à l’assignation du message. Vous pouvez également l'utiliser dans d'autres expressions, telles que :  
  
```  
If ((System.Double) xpath(_RequestMessage.part, "number(//book[last()]/price)") == 75.00 && (System.Boolean) xpath(msgBoolean, "string(//boolean)") == false)...  
```  
  
> [!NOTE]
>  Si vous souhaitez assigner une valeur à une chaîne, utilisez la fonction XPath string(). Exemple :  
  
```  
myString = xpath(msg, "string(/*/book[1]/title)");  
```  
  
> [!NOTE]
>  Le moteur ne tient pas compte des schémas. Vous pouvez donc uniquement lire les valeurs à partir d'un nœud existant ou écrire des valeurs dans ce nœud d'un message (le chemin d'accès complet doit être indiqué), sinon le moteur lève une exception. Ceci est vrai même si vous fournissez une valeur par défaut.  
  
## <a name="assigning-to-an-xpath-in-a-message-part"></a>Affectation à un XPath dans une partie de message  
 Examinez le schéma suivant :  
  
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
  
 Vous pouvez utiliser la fonction de la façon indiquée ci-dessous pour définir les valeur d'une instance de document de ce type de schéma :  
  
```  
//assumes that a message named _ResponseMessage is already constructed  
_ResponseMessage.part = _RequestMessage.part;  
xpath(_ResponseMessage.part, "/*/book[1]/@country") = "USA";  
xpath(_ResponseMessage.part, "/*/book[1]/title") = "Legends";  
xpath(_ResponseMessage.part, "/*/book[1]/author/FirstName") = "A";  
xpath(_ResponseMessage.part, "/*/book[1]/author/LastName") = "B";  
xpath(_ResponseMessage.part, "/*/book[1]/price") = 50;  
```  
  
## <a name="assigning-to-a-message-part-from-an-xpath"></a>Affectation à une partie de message à partir d'un XPath  
  
```  
//assumes that a message named objMessage is already constructed  
objMessage.BooleanPart = xpath("false()");  
objMessage.IntPart = xpath("100");  
objMessage.StringPart = xpath("'Hello'");  
objMessage.StringPart2 = xpath("'World'");  
```  
  
## <a name="using-xpath-to-assign-from-nodes-and-node-sets"></a>Utilisation de XPath pour affecter des valeurs à partir de nœuds et de jeux de nœuds  
 Vous pouvez également utiliser XPath pour affecter des nœuds et jeux de nœuds XML à un élément XML, une classe, ou encore un message basé sur un schéma ou une classe.  
  
 Supposons que vous utilisiez une classe sérialisable XML intitulée « Book » (livre, en anglais). Examinez les exemples suivants :  
  
```  
[Serializable]  
Class Book {...}  
```  
  
 Exemple un : sélectionnez le quatrième élément « book » du catalogue et affectez-le à une variable d'élément XML :  
  
```  
myXmlElement = xpath(myMsg, "/catalog/book[3]");  
```  
  
 Exemple deux : sélectionnez le quatrième élément « book » du catalogue et convertissez-le à l'aide de la désérialisation XML en une instance de classe Book :  
  
```  
myBook = xpath(myMsg, "/catalog/book[3]");  
```  
  
 Exemple trois : sélectionnez le quatrième élément « book » du catalogue et convertissez-le en un message de type Book :  
  
```  
myBookMsg = xpath(myMsg, "/catalog/book[3]");  
```  
  
 Exemple quatre : sélectionnez tous les éléments « book » du catalogue, où MyMethod utilise un XmlNodeSet en tant que paramètre :  
  
```  
MyMethod(xpath(myMsg, "/catalog/book"));  
```  
  
 Exemple cinq : ajoutez un élément « book » au conteneur « BookOfTheMonth » :  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BookOfTheMonth") = myBook;  
```  
  
 Exemple six : ajoutez tous les livres dont le prix est inférieur ou égal à vingt à un ensemble de livres recommandés :  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BestPriceBooks") = xpath(MyMsg, "/catalog/book[@price <= 20]");  
```  
  
 Exemple sept : appelez le code utilisateur retournant un élément XML :  
  
```  
xpath(MyMsg2, "/RecommendedBooks/AdvertisedByPartner") = GetPartnerAdvertisedBook();  
```  
  
 Avant d'appliquer les exemples cinq et sept :  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth/>  
       <BestPriceBooks/>  
       <AdvertisedByPartner/>  
</RecommendedBooks>  
```  
  
 Après application des exemples cinq et sept :  
  
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