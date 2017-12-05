---
title: "Exemple de bouclage piloté par les table | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Extractor functoids, code sample
- Table Looping functoids
- Table Extractor functoids
- Table Looping functoids, about Table Looping functoids
- Table Extractor functoids, about Table Extractor functoids
- code samples, Table Looping functoids
- Table Looping functoids, code sample
- code samples, Table Extractor functoids
ms.assetid: d890bdb1-12a6-4001-9748-737b1f2bab79
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6989ac7e64cf28784d08f26aaf9e7af3a166a28
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="table-driven-looping-example"></a>Exemple de bouclage piloté par la table
Cette section décrit brièvement un mappage à l’aide de la **bouclage de Table** et **extracteur de Table** fonctoids. Pour plus d’informations sur la sélection, la disposition, liaison et la configuration des fonctoids, voir [comment ajouter le bouclage de Table et de fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md).  
  
 Imaginons que vous avez une liste d'adresses que vous devez utiliser dans un document requérant des adresses de livraison et de facturation différentes. Les adresses vont apparaître comme dans le code suivant.  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.Addresses">  
    <Address>  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address>  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 Une forme que peut recouvrir la sortie serait le code suivant, dupliquant les adresses mais en les marquant avec des attributs.  
  
```  
<ns0:Root xmlns:ns0="http://TableLoopingSample.POAddresses">  
    <Address Type="ShipTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City>  
        <State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Kelly Focht</Name>  
        <Street>456 1st Ave</Street>  
        <City>Miami</City><State>FL</State>  
        <PostalCode>81406</PostalCode>  
    </Address>  
    <Address Type="ShipTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
    <Address Type="BillTo">  
        <Name>Wendy Wheeler</Name>  
        <Street>7890 Broadway</Street>  
        <City>Columbus</City>  
        <State>OH</State>  
        <PostalCode>46290</PostalCode>  
    </Address>  
</ns0:Root>  
```  
  
 `The following figure shows a map using the`  **Table** **bouclage**`functoid and`**Table** **extracteur**   `functoids to generate the desired output instance message.`  
  
 ![Mapper le fonctoid Bouclage de Table et extracteur de Table](../core/media/tableloopingextractorfunctoid.gif "tableloopingextractorfunctoid")  
Fonctoids Bouclage de table et Extracteur de table  
  
 Notez que la **bouclage de Table** des liens du fonctoid à l’élément au niveau des enregistrements dans les schémas d’entrée et de sortie. Ce lien garantit la création de la structure associée et, par conséquent, la création des éléments au sein de l'enregistrement. Notez également qu’il existe un **extracteur de Table** pour chaque champ dans le schéma de sortie.  
  
 Le lien vers l’enregistrement du schéma d’entrée est le premier paramètre de la **configurer \<fonctoid\> fonctoid**boîte de dialogue.  
  
 Le deuxième paramètre est le nombre de colonnes dans la table de grille du fonctoid : une colonne pour le type d’adresse, nom, rue, ville, état et code postal. Outre le second paramètre, une liste de toutes les valeurs peut apparaître dans la table de grille. Il s'agit des constantes de chaîne pour le type d'adresse (« ShipTo », « BillTo »), ainsi que des liens vers les champs de l'adresse. Notez que les liens vers les champs d'adresse portent des noms. Le fait de nommer les liens du mappage facilite la construction de la table. Dans le cas contraire, les chemins complets apparaissent dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue.  
  
 Après avoir configuré le **bouclage de Table** fonctoid, vous pouvez construire la table à l’aide de la **configurer le fonctoid Bouclage de Table** boîte de dialogue. La boîte de dialogue s’affiche lorsque vous cliquez sur le bouton de sélection (**...** ) associés à la **grille Bouclage de Table** propriété dans le **propriétés** fenêtre.  
  
 Notez qu’il y a six colonnes comme spécifié dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue : une colonne pour chaque champ dans le schéma de sortie. La liste déroulante affiche les valeurs possibles pour un champ, comme spécifié par les paramètres suivantes dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue. La table comporte deux lignes, une pour chaque type d'enregistrement dans le schéma de sortie. Dans la mesure où il y a deux lignes, ce mappage produit deux enregistrements pour chaque entrée. S'il y en avait quatre, il y aurait quatre enregistrements de sortie pour chaque enregistrement d'entrée.  
  
 Comme le **bouclage de Table** fonctoid prend chaque enregistrement, il remplit la table avec les valeurs de l’enregistrement, puis envoie une ligne à la fois pour le **extracteur de Table** fonctoids. Le **extracteur de Table** fonctoids extraient une valeur à partir de la ligne de table et la transmettent au champ lié dans le message d’instance de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid Bouclage de table](../core/table-looping-functoid.md)   
 [Fonctoid Extracteur de table](../core/table-extractor-functoid.md)   
 [Configuration de bouclage piloté par table](../core/table-driven-looping-configuration.md)   
 [L’ajout de bouclage de Table et fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoid Index](../core/index-functoid.md)   
 [Fonctoid Itération](../core/iteration-functoid.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)   
 [Fonctoid Nombre d’enregistrements](../core/record-count-functoid.md)