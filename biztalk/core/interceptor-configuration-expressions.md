---
title: "Expressions de Configuration de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2695f509-fece-40b8-aa00-fa3c0c0f19c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a28af058ac4750426f66dc6e290bc6a02bf2efd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-configuration-expressions"></a>Expressions de configuration d'intercepteur
Le fichier de configuration de l'intercepteur BAM utilise des expressions de filtre pour identifier une activité et des expressions de données pour créer un élément de données pour le stockage, l'utilisation comme ID de corrélation ou jeton de continuation, ou autre. Quelle que soit la finalité, les expressions individuelles sont identifiées dans le fichier de configuration de l'intercepteur par l'élément `expression` et contiennent une ou plusieurs opérations à l'aide de la notation polonaise inverse, également connue sous le nom de notation post-fixée.  
  
## <a name="about-reverse-polish-notation"></a>À propos de la notation polonaise inverse  
 Dans le cadre de la notation polonaise inverse (NPI), les opérandes précèdent l'opérateur, supprimant ainsi le besoin d'utiliser des parenthèses comme opérateurs de priorité. Une pile sert à maintenir des valeurs et toutes les opérations et pousser des valeurs sur la pile, retirer (supprimer) des valeurs de la pile ou réaliser une combinaison de poussées et de retraits pour effectuer une opération.  
  
 Par exemple, si vous souhaitez évaluer l'expression  
  
 `5 + (10 - 2)`  
  
 Conversion en son équivalent NPI résultats dans  
  
 `5 10 2 - +`  
  
 Cela serait évalué comme suit :  
  
|Entrée|Opération|Pile|  
|-----------|---------------|-----------|  
|5|Envoi de données (push)|5|  
|10|Envoi de données (push)|5, 10|  
|2|Envoi de données (push)|5, 10, 2|  
|-|Soustraire|5, 8|  
|+|Ajouter|13|  
  
 En supposant que le système NPI prenne en charge l'opération de concaténation de chaînes, vous pouvez également évaluer l'expression  
  
 `"The quick brown " + "fox " + "jumped over the lazy " + "dog."`  
  
 Sa conversion en son équivalent NPI donne :  
  
 `"The quick brown " "fox " "jumped over the lazy " "dog" + + +`  
  
 Cela serait évalué comme suit :  
  
|Entrée|Opération|Pile|  
|-----------|---------------|-----------|  
|« Le jeune »|Envoi de données (push)|« Le jeune »|  
|« renard »|Envoi de données (push)|« Le jeune »,« renard »|  
|« a sauté par-dessus le vieux »|Envoi de données (push)|« Le jeune »,« renard », « a sauté par-dessus le vieux »|  
|« chien. »|Envoi de données (push)|« Le jeune »,« renard », « a sauté par-dessus le vieux », « chien. »|  
|+|Concaténation|« Le jeune »,« renard », « a sauté par-dessus le vieux chien. »|  
|+|Concaténation|« Le jeune »,« renard a sauté par-dessus le vieux chien. »|  
|+|Concaténation|« Le jeune renard a sauté par-dessus le vieux chien. »|  
  
 Comme vous pouvez le constater, un nombre arbitraire d'opérations peut être pris en charge, notamment la comparaison, les opérations booléennes et les opérations personnalisées qui extraient les valeurs appropriées pour les opérations auxquelles elles participent. Les valeurs s'accumulent sur la pile et sont poussées et retirées en fonction des opérations individuelles.  
  
## <a name="reverse-polish-notation-in-the-interceptor-configuration-file"></a>Notation polonaise inverse dans le fichier de configuration de l'intercepteur  
 Vous allez écrire deux types d’expressions dans l’intercepteur de fichier de configuration : filtrer les expressions et les expressions de données. Les expressions de filtre s'attendent à ce que le résultat d'une expression NPI soit un booléen `true` ou `false` tandis que les expressions de données attendent une valeur unique sur la pile.  
  
### <a name="filter-expressions"></a>Expressions de filtre  
 Les expressions de filtre donnent le booléen `true` ou `false` et sont utilisées pour identifier un événement spécifique à suivre dans l'application WF ou WFC. Dans les applications WF, il est courant de filtrer en fonction du nom de l'activité et de l'événement. Par exemple, vous souhaitez sélectionner la **FoodAndDrinksPolicy** activité lorsqu’elle est **fermé**. À l'aide d'opérations WF, vous pouvez exprimer le filtre comme suit :  
  
 `(GetActivityName = "FoodAndDrinksPolicy") && (GetActivityEvent = "Closed")`  
  
 Sa conversion en NPI donne :  
  
 `GetActivityName "FoodAndDrinksPolicy" == GetActivityEvent "Closed" == &&`  
  
 La conversion de cette expression en son expression équivalente pour le fichier de configuration de l'intercepteur donne le code XML suivant :  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 Enfin, cette expression est évaluée comme suit en supposant que **GetActivityName** renvoie « DessertPolicy » et **GetActivityEvent** retourné « Closed » :  
  
|Entrée|Opération|Pile|  
|-----------|---------------|-----------|  
||GetActivityName|« DessertPolicy »|  
|« FoodAndDrinksPolicy »|Constante|« DessertPolicy », « FoodAndDrinksPolicy »|  
|Égal à|Comparaison|False|  
||GetActivityEvent|False, « Closed »|  
|« Closed »|Constante|False, « Closed », « Closed »|  
|Égal à|Comparaison|False, True|  
|And|AND logique|False|  
  
 La valeur restante sur la pile est le booléen `False`. Cela entraînera le non-déclenchement de l'événement correspondant. Si le nom de l'activité avait été « FoodAndDrinksPolicy », alors il aurait donné le booléen `True`.  
  
 Vous pouvez créer une expression similaire (avec une évaluation similaire) à l'aide des opérations WCF `GetEndpointName` et `GetOperationName`.  
  
### <a name="data-expressions"></a>Expressions de données  
 Les expressions de données permettent de définir une valeur de données de chaîne unique. Une expression de données est une expression qui n'est pas incluse par un élément `Filter`. Les expressions de données sont utilisées par les éléments `OnEvent`, `CorrelationID`, `ContinuationToken`, `Reference` et `Update`.  
  
 Il est courant de devoir mettre à jour la base de données des activités BAM avec un horodatage étiqueté. Par exemple, vous pourriez capturer l’heure de début d’un événement avec une chaîne sous la forme « Démarrer : \<EventTime > ». Pour ce faire, vous devez utiliser une expression semblable à celle qui suit (où + représente une concaténation) :  
  
 `"Start: " + GetContextProperty(EventTime)`  
  
 Sa conversion en NPI donne :  
  
 `"Start: " GetContextProperty(EventTime) +`  
  
 La conversion de cette expression en son expression équivalente pour un élément `Update` du fichier de configuration de l'intercepteur donne le code XML suivant :  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
 Le tableau suivant montre comment cette expression serait interprétée si l'heure de l'événement était minuit (« 12:00 PM »).  
  
|Entrée|Opération|Pile|  
|-----------|---------------|-----------|  
|« Start:  »|Constante|« Start:  »|  
|GetContextProperty(EventTime)|Envoi de données (push)|« Start:  », « 2006-09-27T12:00:34.000Z »|  
|Concaténation|Concaténation|« Start: 2006-09-27T12:00:34.000Z »|  
  
 La valeur utilisée par la commande de mise à jour serait « Start: 2006-09-27T12:00:34.000Z ».  
  
> [!NOTE]
>  N'utilisez pas les opérations de comparaison « And » ou « Égal à » dans les expressions de données. Sinon, vous obtenez une erreur lors du déploiement de votre fichier de configuration de l'intercepteur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Opérations de l’intercepteur](../core/interceptor-operations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Structure d’un fichier de Configuration de l’intercepteur](../core/structure-of-an-interceptor-configuration-file.md)