---
title: "Faits typés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RuleEngine library
- Business Rule Composer, typed facts
- ITypedFact interface
- DataConnection class
- facts, typed
- TypedDataTable class
- TypedDataRow class
- TypedXmlDocument class
ms.assetid: 8207bfd5-ebd2-45ac-8992-795acdf3ba4c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6041a64fcc4b3496c319a25a2ce758ed7f52a71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="typed-facts"></a>Faits typés
*Faits typés* sont des classes qui implémentent la **ITypedFact** interface : **TypedXmlDocument**, **DataConnection**,  **TypedDataTable**, et **TypedDataRow**.  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 Le **TypedXmlDocument** classe représente le type de document XML dans l’infrastructure de règles d’entreprise. Lorsque vous utilisez un nœud d’un document XML en tant qu’argument dans une règle, les deux expressions XPath sont créées : les liaisons sélecteur et champ.  
  
 Si le nœud n’a pas de nœuds enfants, un *liaison sélecteur* (également appelée liaison XmlDocument) est créée pour le nœud parent et un *liaison champ* (également appelée liaison XmlDocumentMember) est créée. pour le nœud lui-même. La liaison Champ est relative à la liaison Sélecteur. Si le nœud a des nœuds enfants, une liaison Sélecteur est créée avec le nœud et aucune liaison Champ n'est créée.  
  
 Supposons que le schéma suivant existe.  
  
 ![Exemple de schéma affiché dans l’Explorateur de faits](../core/media/xmldocumentbrowser.gif "xmldocumentbrowser")  
Case.xsd  
  
 Si le nœud Income est sélectionné, seule une liaison Sélecteur est créée, car le nœud a des nœuds enfants. L’expression XPath par défaut dans le **sélecteur XPath** propriété du volet propriété contient :  
  
```  
/*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']/*[local-name()='Income' and namespace-uri()='']  
```  
  
 Toutefois, si le nœud Name est sélectionné, une liaison Sélecteur et une liaison Champ sont créées. Les informations de liaison se présentent comme suit.  
  
|Propriété|Valeur|  
|--------------|-----------|  
|**Champ XPath**|*[local-name()='Name' and namespace-uri()='']|  
|**Sélecteur XPath**|/*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']|  
  
 Vous pouvez modifier les expressions XPath par défaut pour les nœuds XML avant de faire glisser le nœud vers un argument de règle, auquel cas les nouvelles informations de liaison sont placées dans la stratégie. Notez toutefois que toute modification apportée aux expressions XPath doit être entrée à nouveau dans l'Éditeur des règles d'entreprise quand le schéma est rechargé.  
  
 Quand des définitions de vocabulaire sont créées pour des nœuds XML, les expressions XPath pour les liaisons ont des valeurs par défaut similaires basées sur les règles décrites précédemment, qui peuvent être modifiées dans l'Assistant Définition de vocabulaire. Les modifications des expressions sont placées dans la définition de vocabulaire et sont prises en compte dans les arguments de règle créés à partir des définitions.  
  
## <a name="dataconnection"></a>DataConnection  
 **DataConnection** est une classe .NET fournie dans le **RuleEngine** bibliothèque. Il contient un .NET **SqlConnection** instance et un **DataSet** nom. Le **DataSet** vous permet de créer un identificateur unique pour le **SqlConnection** et sert à définir le type résultant.  
  
 Le **DataConnection** classe fournit une optimisation des performances pour le moteur de règles d’entreprise. Plutôt que de déclarer dans les tables de base de données très volumineuse moteur (**TypedDataTable** classe) qui peut contenir de nombreuses lignes de base de données (**TypedDataRow** classe) qui ne sont pas pertinentes pour la stratégie, vous pouvez déclarer un léger **DataConnection**. Lorsque le moteur évalue une stratégie, il crée dynamiquement une requête SELECT basée sur les prédicats/actions de règle et les requêtes le **DataConnection** lors de l’exécution. Prenons l'exemple de la règle suivante :  
  
```  
IF NorthWind.Products.UnitPrice >= 0   
THEN <do something>  
```  
  
 La requête SQL suivante est générée à partir de la règle :  
  
```  
Select * From [Product] Where [UnitPrice] >= 0  
```  
  
 Les résultats de la requête sont déclarés dans le moteur sous forme de lignes de données.  
  
> [!NOTE]
>  L’utilisation d’un **OleDbConnection** dans un **DataConnection** n’est pas pris en charge actuellement.  
  
 Lorsque vous sélectionnez une table de base de données ou une colonne à utiliser dans une condition de règle ou une action, vous pouvez choisir de lier à l’objet à l’aide **DataConnection** ou **TypedDataTable** en sélectionnant « Connexion de données » ou » Base de données/ligne de la table » de la **type de liaison de base de données**zone de liste déroulante dans la fenêtre Propriétés pour le **bases de données** onglet de l’Explorateur de faits.  
  
> [!NOTE]
>  La liaison DataConnection est utilisée par défaut.  
  
## <a name="typeddatatable"></a>TypedDataTable  
 Vous pouvez déclarer un élément ADO.NET **DataTable** objet dans le moteur, mais il sera traité comme tout autre objet .NET. Dans la plupart des cas vous souhaiterez plutôt déclarer la classe du moteur de règles **TypedDataTable**.  
  
 **TypedDataTable** est une classe wrapper qui contient un élément ADO.NET **DataTable**. Le constructeur accepte simplement un **DataTable**. À tout moment une table ou colonne de table est utilisée comme un argument de règle, l’expression est évaluée par rapport aux **TypedDataRow** wrappers et non sur le **TypedDataTable**.  
  
## <a name="typeddatarow"></a>TypedDataRow  
 Il s’agit d’un wrapper de fait typé pour ADO **DataRow** objet. En faisant glisser une table ou une colonne à un argument de règle dans l’éditeur des règles d’entreprise entraîne de règles générées à partir de retourné **TypedDataRow** wrappers.  
  
## <a name="see-also"></a>Voir aussi  
 [Faits](../core/facts.md)