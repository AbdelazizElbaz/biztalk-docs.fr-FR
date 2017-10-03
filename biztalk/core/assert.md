---
title: Assert | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assert function [Business Rules Engine], .NET objects
- Assert function [Business Rules Engine], TypedXMLDocument
- Assert function [Business Rules Engine]
- Assert function [Business Rules Engine], examples
- Assert function [Business Rules Engine], TypedData table
- Assert function [Business Rules Engine], DataConnection
- .NET objects
ms.assetid: e9989214-3c10-4691-9c38-f6fe64e511ed
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2de66aab5cde0a9515f41713d3390632180fbff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="assert"></a>Assert
*Assertion* est le processus d’ajout d’instances d’objet dans la mémoire de travail du moteur de règle d’entreprise. Le moteur traite chaque instance selon les conditions et actions écrites d'après le type de l'instance. Ce traitement se déroule en trois étapes : correspondance, résolution des conflits et action.  
  
 Les rubriques suivantes décrivent les comportements qui résultent de l’utilisation du **Assert** fonction pour différents types de faits.  
  
## <a name="net-objects"></a>Objets .NET  
 Chaque objet est déclaré dans la mémoire de travail sous la forme d'une instance distincte. Cela signifie que l'instance est analysée par chaque prédicat référençant le type de l'objet (par exemple IF Object.Property = 1 ). Elle est également mise à la disposition des actions de règles qui font référence au type, en fonction des résultats des conditions de règle.  
  
 Prenons l'exemple suivant.  
  
 **Règle 1**  
  
```  
IF A.Value = 1  
THEN A.Status = "good"  
```  
  
 **Règle 2**  
  
```  
IF B.Value = 1  
THEN A.Status = "good"  
```  
  
 Dans la règle 1, seules les instances de A qui ont une valeur de 1 auront leurs **état** propriété mise à jour. Dans la règle 2, toutefois, si la condition a la valeur **true**, toutes les instances A verront ont leur état mis à jour. En fait, s’il existe plusieurs instances de B, les instances A seront mise à jour chaque fois que la condition a la valeur **true** pour une instance B.  
  
 Pour déclarer un objet .NET à partir d’une règle, vous pouvez ajouter la fonction intégrée **Assert** fonctionner comme une action de règle. Notez que le moteur de règles a un **CreateObject** (fonction), mais il n’est pas affiché comme une fonction distincte dans l’éditeur des règles d’entreprise. Son appel est généré en faisant glisser la méthode de constructeur de l'objet à créer du volet Classe .NET de l'Explorateur de faits vers le volet d'action. L’éditeur des règles d’entreprise convertit ensuite la méthode de constructeur dans un **CreateObject** appeler dans la définition de règle.  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 Lorsqu’un **TypedXmlDocument** est déclaré, le moteur de règles d’entreprise crée enfant **TypedXmlDocument** instances basées sur les sélecteurs définis dans la règle.  
  
 Les sélecteurs et les champs sont tous deux des expressions XPath. Les sélecteurs peuvent constituer un bon moyen d'isoler les nœuds d'un document XML ; les champs peuvent quant à eux servir à identifier des éléments spécifiques dans le sélecteur. Tous les champs à l'intérieur d'un sélecteur sont regroupés sous la forme d'un objet par le moteur. Lorsque vous sélectionnez un nœud sous la **schémas XML** onglet dans l’Explorateur de faits, l’éditeur des règles d’entreprise remplit automatiquement la **sélecteur XPath** propriété pour tous les nœuds et le **XPath Field**  propriété pour n’importe quel nœud qui ne contient pas de nœuds enfants. Vous pouvez également entrer vos propres expressions XPath pour **sélecteur XPath** et **XPath Field** si nécessaire.  
  
 Si le sélecteur correspond à plusieurs parties du document XML, plusieurs objets de ce type sont déclarés dans la mémoire de travail du moteur de règles ou en sont retirés. Supposons que vous disposiez du XML suivant.  
  
```  
<root>  
   <order customer="Joe">  
      <item name="router" quantity="10" cost="550" />  
      <item name="switch" quantity="3" cost="300" />  
   </order>  
   <order customer="Jane">  
      <item name="switch" quantity="1" cost="300" />  
      <item name="cable" quantity="23" cost="9.99" />  
   </order>  
</root>  
```  
  
 Si vous utilisez le sélecteur /root/order (ou //order), deux objets sont ajoutés à la mémoire de travail.  
  
 1\)  
  
```  
<order customer="Joe">  
   <item name="router" quantity="10" cost="550" />  
   <item name="switch" quantity="3" cost="300" />  
</order>  
```  
  
 2\)  
  
```  
<order customer="Jane">  
   <item name="switch" quantity="1" cost="300" />  
   <item name="cable" quantity="23" cost="9.99" />  
</order>  
```  
  
 Dans chaque sélecteur, les différents champs sont désignés par des XPath.  
  
 Si vous utilisez le sélecteur /root/order/item (ou (//order/item ou //item), quatre objets sont ajoutés à la mémoire de travail du moteur des règles : deux éléments pour Joe et deux pour Jane.  
  
```  
<root>  
   <order customer="Joe">  
  
   </order>  
   <order customer="Jane">  
  
   </order>  
</root>  
```  
  
 Chaque objet a accès à trois champs :@name, @quantity, et @cost. Étant donné que l’objet est une référence dans le document d’origine, vous pouvez faire référence à des champs parents (par exemple, «../@customer»).  
  
 Vous pouvez utiliser plusieurs sélecteurs dans le même document. Ceci vous permet d'afficher différentes parties du document (par exemple, si une section est la commande et qu'une autre contient l'adresse de livraison). N'oubliez pas cependant que les objets créés sont définis par la chaîne XPath qui les a créés. À l’aide d’une expression XPath différente, même si elle correspond au même nœud, des résultats dans un unique **TypedXmlDocument**.  
  
 Le moteur des règles prend en charge les types scalaires .NET de base de façon native, ainsi que les objets pour les types de référence. Les documents XML sont essentiellement de type texte, mais la valeur du champ peut être de n'importe quel type en fonction du type spécifié lors de l'élaboration de la règle. Par ailleurs, dans la mesure où les champs sont des expressions XPath, ils peuvent renvoyer un ensemble de nœuds dans lequel le premier élément est utilisé comme valeur.  
  
 En arrière-plan, le moteur de règles peut convertir une valeur de champ de texte à l’un types pris en charge par le biais de la **XmlConvert** (fonction). Vous pouvez spécifier cela en définissant le type dans l'Éditeur des règles d'entreprise. Si une conversion est impossible, une exception est levée. Les types **bool** et **double** peuvent être récupérées uniquement en tant que leur type respectif, chaînes ou objets.  
  
## <a name="typeddatatable"></a>TypedDataTable  
 Lorsqu’un **TypedDataTable** est déclaré, tous les **DataRows** contenus dans le **DataTable** sont automatiquement déclarées dans le moteur comme **TypedDataRows**. À tout moment une table ou colonne de table est utilisée comme un argument de règle, l’expression est évaluée par rapport aux **TypedDataRows**et non sur le **TypedDataTable**.  
  
 Supposez par exemple que vous avez construit la règle suivante à partir d'une table Customers :  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
> [!NOTE]
>  Pour créer une règle sur une table de base de données, vous devez utiliser **Data table / ligne** comme type de liaison de base de données.  
  
 Supposez que vous déclariez suit **DataTable** avec trois **DataRows** dans le moteur (comme un **TypedDataTable**).  
  
|CustomerID|ContactTitle|  
|----------------|------------------|  
|001|Assistant approvisionnement|  
|002|Assistant approvisionnement|  
|003|Assistant approvisionnement|  
  
 Le moteur insère trois **TypedDataRows**: 001 et 002 003.  
  
 Chaque **TypedDataRow** est évalué indépendamment par rapport à la règle. La première **TypedDataRow** répond à la condition de règle et les deux suivants. Les résultats apparaissent comme suit.  
  
|CustomerID|ContactTitle|  
|----------------|------------------|  
|001|Responsable des achats|  
|002|Assistant approvisionnement|  
|003|Assistant approvisionnement|  
  
> [!NOTE]
>  Les TypedDataRows peuvent également être directement déclarés dans le moteur. Ils sont alors traités de la même manière que précédemment.  
  
 Le **DataSetName.DataTableName** est considéré comme un identificateur unique. Par conséquent, si une seconde **TypedDataTable** est déclarée avec le même **DataSet** nom et **DataTable** nom, elle remplace la première **TypedDataTable**. Tous les **TypedDataRow**associés à la première **TypedDataTable** sont retirées et le second **TypedDataTable** est déclarée.  
  
## <a name="dataconnection"></a>DataConnection  
 Comme avec un **TypedDataTable**, en faisant glisser une table ou une colonne en tant qu’argument de règle dans l’éditeur des règles d’entreprise entraîne de règles générées à partir de retourné **TypedDataRow**par opposition à la  **DataConnection** lui-même.  
  
 Supposons que la règle suivante est créée et un **DataConnection** déclaré contienne un **SqlConnection** à Northwind.Customers :  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
 Lorsque le moteur évalue la règle utilisée dans le **TypedDataTable** section, il crée dynamiquement une requête qui ressemble à :  
  
```  
SELECT *  
FROM Northwind.Customers  
WHERE CustomerID = 1  
```  
  
 Étant donné que qu’une seule ligne dans la base de données répond à ce critère, seul un **TypedDataRow** est créé et déclaré dans le moteur pour traitement.  
  
## <a name="summary-of-asserted-entities-and-instance-types"></a>Résumé des entités déclarées et des types d'instance  
 Le tableau suivant récapitule le comportement de déclaration des différents types, en illustrant le nombre d'instances résultantes créées dans le moteur pour chaque entité déclarée, ainsi que le type qui est appliqué à chacune de ces instances pour les identifier.  
  
|Entité|Nombrer d'instances déclarées|Type d’instance|  
|------------|----------------------------------|-------------------|  
|Objet .NET|1 (l'objet lui-même)|Classe .NET complète|  
|TypedXmlDocument|1-N TypedXmlDocument (s) : basé sur les liaisons sélecteur créées et le contenu du document|DocumentType.selector|  
|TypedDataTable|TypedDataRow(s) 1-N :<br /><br /> Une pour chaque DataRow dans le DataTable|DataSetName.DataTableName|  
|TypedDataRow|1 (le TypedDataRow déclaré)|DataSetName.DataTableName|  
|DataConnection|1-N (un pour chaque TypedDataRow renvoyé après interrogation du DataConnection)|DataSetName.DataTableName|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de contrôle du moteur](../core/engine-control-functions.md)