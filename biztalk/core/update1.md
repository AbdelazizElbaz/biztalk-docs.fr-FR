---
title: "Mise à jour 1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Update function [Business Rules Engine]
- Update function [Business Rules Engine], TypedXMLDocument
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], .NET objects
- .NET objects
- Update function [Business Rules Engine], DataConnection
ms.assetid: 939e45dc-6433-42f3-a336-8f3c247417ac
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a4ea10e72be2a39eedaafa0e00c8f8ac630393b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update"></a>Update
Lorsque **mise à jour** fonction est appelée un objet, l’objet est redéclaré dans le moteur pour être réévalué, basées sur les nouvelles données et l’état. L’objet peut être de type **TypedXmlDocument** ou classe .NET ou **DataConnection** ou **TypedDataTable**.  
  
 Vous pouvez également utiliser **mise à jour** fonction pour améliorer les performances du moteur et empêcher les scénarios de boucle sans fin comme décrit dans cette rubrique.  
  
 En général, vous utilisez **Assert** pour placer un nouvel objet dans la mémoire de travail du moteur de règles et utiliser **mettre à jour** pour mettre à jour un objet déjà existant dans la mémoire de travail. Lorsque vous déclarez un nouvel objet, les conditions dans tous les règles sont évaluées. Lorsque vous mettez à jour un objet existant, seules les conditions utilisant le fait mis à jour sont réévaluées, et les actions sont ajoutées à l'agenda si ces conditions ont la valeur True.  
  
## <a name="using-update-function-on-net-facts"></a>Utilisation de la fonction Mettre à jour sur les faits .NET  
 Prenons l'exemple des deux règles suivantes. Supposons que les objets **ItemA** et **ItemB** existent déjà dans la mémoire de travail. Règle 1 évalue la **Id** propriété sur **ItemA**, définit le **Id** propriété sur **ItemB**, puis redéclare **ItemB** après la modification. Lorsque **ItemB** est redéclaré, il est traité comme un nouvel objet et le moteur réévalue toutes les règles qui utilisent l’objet **ItemB** dans les prédicats ou actions. Cela garantit que la règle 2 est réévaluée en fonction de la nouvelle valeur de **ItemB.Id**, comme dans la règle 1. Règle 2 peut avoir échoué la première fois qu’elle a été évaluée, mais prend la valeur de **true** la deuxième fois, elle est évaluée.  
  
### <a name="rule-1"></a>Règle 1  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Assert(ItemB)  
```  
  
### <a name="rule-2"></a>Règle 2  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 Cette possibilité de redéclarer les objets dans la mémoire de travail donne à l'utilisateur un contrôle explicite sur le fonctionnement des scénarios de chaînage avant. Dans cet exemple, l'effet secondaire de la nouvelle déclaration est la réévaluation de la règle 1. Étant donné que **ItemA.Id** n’a pas changé, règle 1 évalue à nouveau à **true** et **Assert (ITEMB)** action est déclenchée à nouveau. Par conséquent, la règle crée une situation de boucle sans fin.  
  
> [!NOTE]
>  Le nombre de boucles maximale par défaut de la réévaluation de règles est 2 ^ 32. Pour certaines règles, l’exécution de la stratégie peut durer longtemps. Vous pouvez réduire le nombre en ajustant la **profondeur maximale de la boucle d’exécution** propriété de la version de stratégie.  
  
 Vous devez pouvoir redéclarer des objets sans créer des boucles sans fin et le **mise à jour** fonction fournit cette fonctionnalité. Comme une fonction de redéclaration, le **mise à jour** fonction effectue **retrait** et **Assert** des instances d’objet associé, qui ont été modifiées à partir d’actions de règle, mais il y a deux principales différences :  
  
-   Les actions sur l'agenda pour les règles dans lesquelles le type d'instance n'est utilisé que dans les actions (pas les prédicats) resteront dans l'agenda.  
  
-   Les règles qui n'utilisent que le type d'instance dans les actions ne seront pas réévaluées.  
  
 Par conséquent, les règles qui utilisent les types d'instances dans les prédicats seulement ou dans les prédicats et les actions seront réévaluées et leurs actions seront ajoutées à l'agenda en conséquence.  
  
 Modification de l’exemple précédent pour utiliser le **mise à jour** fonction garantit que seule la règle 2 est réévaluée car **ItemB** est utilisée dans la condition de règle 2. Règle 1 n’est pas réévaluée car **ItemB** est utilisée uniquement dans les actions de la règle 1, en éliminant le scénario de bouclage.  
  
### <a name="rule-1"></a>Règle 1  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Update(ItemB)  
```  
  
### <a name="rule-2"></a>Règle 2  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 Toutefois, il reste possible de créer des scénarios de bouclage. Observez par exemple la règle suivante :  
  
### <a name="rule-1"></a>Règle 1  
  
```  
IF ItemA.Id == 1  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 Étant donné que **ItemA** est utilisée dans le prédicat, il est réévalué quand **mise à jour** est appelée sur **ItemA**. Si la valeur de **ItemA.Id** n’est pas modifiée nulle part, règle 1 continue à évaluer à **true**, ce qui provoque **mise à jour** à appeler une fois encore sur A. Le Concepteur de la règle doit garantir que les scénarios de bouclage comme celui-ci ne sont pas créés.  
  
 L'approche à adopter dépendra de la nature des règles. Le mécanisme suivant permet de résoudre facilement le problème qui se pose dans l'exemple précédent.  
  
 Le **mise à jour** fonction peut être utilisée dans l’éditeur des règles d’entreprise avec une référence à la classe, comme avec la **Assert**, **retrait**, ou **RetractByType** fonctions.  
  
### <a name="rule-1"></a>Règle 1  
  
```  
IF ItemA.Id == 1 and ItemA.Value != 20  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 Ajouter le contrôle sur **ItemA.Value** empêche de l’évaluation de la règle 1 **true** à nouveau après l’exécution d’actions de règle 1, la première fois.  
  
## <a name="using-update-function-on-xml-facts"></a>Utilisation de la fonction Mettre à jour sur les faits XML  
 Prenons l'exemple des deux règles suivantes. Supposons que la règle 1 évalue le nombre total d'articles dans un message de bon de commande et la règle 2 définit l'état sur « Needs approval » si le nombre total est supérieur ou égal à 10.  
  
### <a name="rule-1"></a>Règle 1  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count)  
```  
  
### <a name="rule-2"></a>Règle 2  
  
```  
IF ProcessPO.Order:/Order/Items/TotalCount >= 10  
THEN ProcessPO.Order:/Order/Status = "Needs approval"  
```  
  
 Si vous passez le message de bon de commande fournisseur suivant comme entrée pour cette stratégie, vous remarquez que l’état n’est pas définie sur « Needs approval » même si le nombre total d’éléments est 14. C’est parce que le règle2 est évaluée uniquement au début lorsque la valeur de la **TotalCount** est de 0, et la règle n’est pas évaluée chaque fois que le nombre total est mis à jour. Pour que les conditions soient réévaluées à chaque le **TotalCount** est mis à jour, vous devez appeler la **mise à jour** fonctionnent sur le nœud parent (**éléments**) du nœud modifié ( **TotalCount**). Si vous modifiez la règle 1 comme illustré ci-dessous et testez cette règle une nouvelle fois, la valeur du champ État doit être définie sur « Needs Approval ».  
  
```  
<ns0:Order xmlns:ns0="http://ProcessPO.Order">  
    <Items>  
        <Item>  
            <Id>ITM1</Id>  
            <Count>2</Count>  
        </Item>  
        <Item>  
            <Id>ITM2</Id>  
            <Count>5</Count>  
        </Item>  
        <Item>  
            <Id>ITM3</Id>  
            <Count>7</Count>  
        </Item>  
        <TotalCount>0</TotalCount>  
    </Items>  
    <Status>No approval needed</Status>  
</ns0:Order>  
```  
  
 Modifié **règle 1** est comme suit :  
  
### <a name="rule-1"></a>Règle 1  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count) AND  
Update(ProcessPO.Order:/Order/Items)  
```  
  
## <a name="using-update-function-on-database-facts"></a>Utilisation de la fonction Mettre à jour sur les faits de base de données  
  
### <a name="typeddatatable"></a>TypedDataTable  
 Si **mise à jour** est appelée sur une **TypedDataTable**, **mise à jour** est appelée par le moteur sur tous associés **TypedDataRows**. **Mise à jour** peut également être appelée sur individuels **TypedDataRows**.  
  
### <a name="dataconnection"></a>DataConnection  
 Mise à jour d’un **DataConnection** n’est pas pris en charge. Utilisez **Assert** à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de contrôle du moteur](../core/engine-control-functions.md)