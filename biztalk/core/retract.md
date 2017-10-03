---
title: Retirez | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], TypedData table
- Retract function [Business Rules Engine], TypedXMLDocument
- Retract function [Business Rules Engine]
- Retract function [Business Rules Engine], DataConnection
- Retract function [Business Rules Engine], .NET objects
- .NET objects
ms.assetid: 24b6b894-6810-4497-a122-8c91f0b2e816
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17eb4739412d310d2a69b53c8470abc7461ce3ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="retract"></a>Retract
Vous pouvez utiliser la **Retract** afin de supprimer des objets à partir de la mémoire de travail du moteur de règles métier. Les paragraphes suivants décrivent le comportement associé à la rétractation des entités de types différents à partir de la mémoire de travail du moteur de règles.  
  
## <a name="net-objects"></a>Objets .NET  
 Un objet .NET est rétracté dans une stratégie à l’aide de la **Retract** (fonction). Cette fonction est disponible dans l’éditeur des règles d’entreprise en tant qu’un **fonctions** vocabulaire : faites glisser la classe (pas l’assembly ou une méthode) dans le **Retract** paramètre.  
  
> [!NOTE]
>  Si vous faites glisser une méthode dans le **Retract** (fonction), le moteur essaie de rétracter l’objet retourné par la méthode.  
  
 La rétraction d'un objet .NET le supprime de la mémoire de travail du moteur de règles et a l'impact suivant :  
  
-   Les règles qui utilisent l'objet dans un prédicat ont leurs actions supprimées de l'agenda (si des actions figurent dans l'agenda).  
  
-   Des actions de l'agenda qui utilisent les objets sont supprimées de celui-ci.  
  
    > [!NOTE]
    >  Autres actions en haut de l’agenda peuvent avoir été exécutées avant le **Retract** fonction a été appelée.  
  
-   L'objet n'est plus évalué par le moteur.  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 Vous pouvez rétracter l’original **TypedXmlDocument** qui a été déclaré dans le moteur ou l’un de l’enfant **TypedXmlDocument**créés à partir d’un nœud du parent **XmlDocument** .  
  
 À l’aide du code XML suivant comme exemple, vous pouvez rétracter le **TypedXmlDocument** associé à la commande ou d’un ou deux de la **TypedXmlDocument**associés à orderline.  
  
```  
<order>  
   <orderline customer="Joe" linenumber="001">  
      <product name="router" quantity="10" cost="550" />  
   </orderline>  
   <orderline customer="Jane" linenumber="002">  
      <product name="switch" quantity="1" cost="300" />  
   </orderline>  
</order>  
```  
  
 Pour rétracter l'objet Order, vous devez faire glisser le nœud supérieur dans le volet des faits des schémas XML. Ce nœud se termine par « .xsd » et représente le nœud racine du document (pas le nœud d’élément) ; Il possède un sélecteur « / » qui fait référence à la première **TypedXmlDocument**. Lorsque le parent **TypedXmlDocument** est retiré, toutes les **TypedXmlDocument** instances associées à la **TypedXmlDocument** (tous les  **TypedXmlDocument**créés en appelant le **Assert** fonction en fonction des sélecteurs utilisés dans la stratégie) sont supprimés de la mémoire de travail.  
  
 Pour ne rétracter qu’un seul enfant **TypedXmlDocument** (autrement dit un orderline), vous pouvez faire glisser ce nœud à partir du volet de schémas XML dans le **Retract** (fonction). Il est important de noter que tous les **TypedXmlDocument**sont associés de niveau supérieur **TypedXmlDocument** qui a été déclaré à l’origine et non avec les **TypedXmlDocument**qui apparaît au-dessus de lui dans la hiérarchie d’arborescence XML. Par exemple, le produit est un **TypedXmlDocument** sous l’objet orderline ; par conséquent, il doit donc être associé à la commande **TypedXmlDocument**et non avec l’objet orderline  **TypedXmlDocument**. Dans la plupart des cas, cette distinction n'est pas importante. Cependant, si vous rétractez l'objet Order, les objets Orderline et Product le sont également, et si vous rétractez l'objet Orderline, l'objet Product n'est pas rétracté.  
  
 Le moteur fonctionne uniquement avec et instances d’objet assure le suivi (**TypedXmlDocument**s) qu’il a créées lorsque le **TypedXmlDocument** a été déclaré à l’origine. Si vous créez des nœuds supplémentaires, par exemple, les nœuds frères vers un nœud qui a été sélectionné via un sélecteur dans la stratégie, ces nœuds ne sont pas évaluées dans les règles, sauf si **TypedXmlDocument**sont créés et déclarés pour eux. Déclaration de ces nouvelles, de niveau inférieur **TypedXmlDocuments** provoque leur évaluation dans les règles, mais le niveau supérieur **TypedXmlDocument** n’a pas connaissance. Lorsque le niveau supérieur **TypedXmlDocument** est retiré, la nouvelle indépendamment **TypedXmlDocument**déclarés pas automatiquement. Par conséquent, si de nouveaux nœuds sont créés, il est généralement plus simple de rétracter et redéclarer complet **XmlDocument**.  
  
 Le **TypedXmlDocument** classe prend en charge un nombre de méthodes utiles qui peut être appelée au sein d’un membre .NET personnalisé dans le cadre d’une action. Cela inclut la possibilité pour obtenir le **XmlNode** associé à la **TypedXmlDocument** ou le parent **TypedXmlDocument**.  
  
## <a name="typeddatatable"></a>TypedDataTable  
 Vous pouvez rétracter des **TypedDataRow**ou l’ensemble **TypedDataTable**. Si vous retirez une table, toutes les lignes qu'elle contient sont retirées de la mémoire de travail.  
  
 Pour rétracter tout le **TypedDataTable** vous devez utiliser une fonction d’assistance pour accéder à la **Parent** propriété sur **TypedDataRow**, par exemple :  
  
```  
Retract(MyHelper.GetTypedDataTable(TypedDataRow))  
```  
  
 Dans l’action précédente, faites glisser la table en **TypedDataRow**. Dans **GetTypedDataTable** vous devez retourner la valeur de **TypedDataRow.Parent**.  
  
 Comme avec **TypedXmlDocument**s, si vous déclarez supplémentaires, nouveau **TypedDataRow**s pour le même **DataTable** après la déclaration du **TypedDataTable**, elles sont traitées comme des entités individuelles et le retrait de la **TypedDataTable** n’entraîne pas l’annulation de ces supplémentaire **TypedDataRow**s. Uniquement les **TypedDataRow**contenus dans le **TypedDataTable** lorsqu’il a été déclaré sont retirées.  
  
## <a name="dataconnection"></a>DataConnection  
 Lorsqu’un **DataConnection** est retiré, toutes les **TypedDataRow**extraits de la base de données via la requête créée par le **DataConnection** sont retirés de mémoire de travail. Le **DataConnection** est également rétracté, ce qui signifie que plus aucun **TypedDataRow**s sont récupérées via la **DataConnection** (autrement dit, en utilisant la  **DataConnection** dans d’autres prédicats ou les actions).  
  
 Lorsque vous utilisez un **DataConnection**, toute opération individuelle de rétraction **TypedDataRow** met le moteur dans un état incohérent. Par conséquent, les opérations ne sont pas autorisées sur la personne **TypedDataRow**associées à un **DataConnection**. Si vous faites glisser la table (à l’aide de la **DataConnection** paramètre) dans le **retrait** (fonction), vous retirez le **DataConnection**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de contrôle du moteur](../core/engine-control-functions.md)