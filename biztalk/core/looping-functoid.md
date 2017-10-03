---
title: Fonctoid Bouclage | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19886ccb-4642-48a4-b93e-563640ea828b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ce2b66fd796708a0e8b24ee05e3a0b043af6808
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="looping-functoid"></a>Fonctoid Bouclage

## <a name="overview--example"></a>Vue d’ensemble et exemple
Le **bouclage** fonctoid combine plusieurs enregistrements ou champs du schéma source en un enregistrement unique dans le schéma de destination.  
  
 L’illustration suivante montre un **bouclage**fonctoid utilisé dans un mappage pour combiner les adresses collectées à partir de deux enquêtes différentes en une liste d’adresses principale unique.  
  
> [!NOTE]
>  Le **bouclage** et **Value Mapping (Flattening)** fonctoids ne doivent pas être utilisés ensemble. Si les deux sont utilisés ensemble, il en résulte un mappage compilé qui suppose il n’y a aucun dépendance pour les nœuds cibles situés au-dessous de bouclage source le **bouclage** fonctoid.  
  
 ![Mappage illustrant l’utilisation du fonctoid Bouclage. ] (../core/media/loopingfunctoid.gif "loopingfunctoid")  
  
 Le **FoodSurvey** et **FlowerSurvey** des enregistrements de boucle du schéma source sont mappés sur le bouclage **adresse** enregistrement du schéma de destination. Si un message d’instance d’entrée possède trois **FoodSurvey** enregistrements et deux **FlowerSurvey** enregistrements, les **bouclage**fonctoid combine pour créer cinq  **Adresse** enregistrements dans le message d’instance de sortie.  
  
 Le code suivant correspond à un exemple de message d’instance d’entrée.  
  
```  
<ns0:Surveys xmlns:ns0="http://LoopingFunctoid.Surveys">  
    <FoodSurvey Name="Karin Zimprich" Address="345 N 63rd St" City="Boston" State="MA" PostalCode="07485" />  
    <FoodSurvey Name="Wendy Wheeler" Address="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" />  
    <FoodSurvey Name="Florian Voss" Address="1234 Main St" City="Denver" State="CO" PostalCode="97402" />  
    <FlowerSurvey Name="Kelly Focht" Address="456 1st Ave" City="Miami" State="FL" PostalCode="81406" />  
    <FlowerSurvey Name="Jim Kim" Address="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" />  
</ns0:Surveys>  
```  
  
 Le message d’instance d’entrée produit le message d’instance de sortie suivant une fois traité par le mappage de l’illustration précédente.  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 Le **FoodSurvey** et **FlowerSurvey** les adresses de message ont été combinés. Le message combiné n'indique pas la source de chaque adresse. Si vous souhaitez effectuer le suivi de la source, ajoutez un **Source** d’attribut pour le **adresse** enregistrement de la **MasterAddress** schéma et du mappage d’une valeur constante. Pour définir cette valeur, connectez le **FoodSurvey** champ au nouveau **Source** champ. Sur la ligne de connecteur, vous devez modifier le **propriétés des liaisons** &#124; **Compilateur** &#124; **Liaisons sources** propriété « Copier le nom ». Répétez ce processus pour le **FlowerSurvey** champ. Le retraitement du message d'entrée à partir des instructions ci-dessus produit la sortie suivante :  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458" Source="FoodSurvey"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" Source="FoodSurvey"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402" Source="FoodSurvey"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406" Source="FlowerSurvey"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" Source="FlowerSurvey"/>  
</ns0:MasterAddresses>  
```  

## <a name="relationships-with-nodes"></a>Relations avec les nœuds

 Relations entre les nœuds affectent le comportement de la **bouclage** fonctoid. Par exemple, liaison d’un nœud enfant et son parent dans le schéma source vers le **bouclage** fonctoid empêche le nœud de destination la création.  
  
 Les fonctoids sont également affectés par les relations entre des nœuds sources. La connexion d’un fonctoid à des champs enfants non frères de nœuds sources du **bouclage** fonctoid peut produire des résultats inattendus. Par exemple, à l’aide de la **concaténation de chaînes** fonctoid pour combiner les **FoodSurvey** champ nom et **FlowerSurvey** champ d’adresse dans le champ nom de l’adresse **MasterAddress** génère le message d’instance de sortie suivant :  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 Notez comment la **nom** champ est manquant pour **FoodSurvey** source des messages mais n’est présente pour **FlowerSurvey** messages source.  
  
> [!IMPORTANT]
>  La connexion d’un fonctoid à des champs enfants des nœuds de source de la **bouclage** fonctoid peut produire des résultats inattendus si les nœuds de la source ne sont pas frères.  
  
 Le **bouclage** fonctoid est une construction puissante que vous pouvez utiliser pour créer des bouclages conditionnels et mapper des schémas à des catalogues. Il existe également des effets de chevauchement **bouclage** chemins d’accès de fonctoid vous devez prendre en compte.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Bouclage conditionnel](../core/conditional-looping.md)  
  
-   [Schéma plat au catalogue](../core/flat-schema-to-catalog.md)  
  
-   [Chemins de bouclage](../core/loop-paths.md)  
  
## <a name="see-also"></a>Voir aussi  
 **Référence du fonctoid de bouclage de table**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]