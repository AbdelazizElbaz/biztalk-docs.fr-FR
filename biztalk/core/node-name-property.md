---
title: "Propriété nom du nœud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d9e5bf-7439-4ef4-ad14-e8d3e8eff911
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1d39c71a425e20c5a9228e418cfa86acb579fa5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="node-name-property"></a>Propriété Nom du nœud
Lorsque vous utilisez l'Éditeur BizTalk pour insérer des nœuds dans l'arborescence de schéma, certains nœuds sont censés être renommés, d'autres non. Fondamentalement, vous pouvez et devez renommer **enregistrement** nœuds, **Fieldelement** nœuds, et **attribut de champ** nœuds. Les noms que vous donnez à ces nœuds deviendront les noms des éléments et des attributs XML du message que le schéma définit.  
  
 Dans l’arborescence du schéma, les nœuds que vous ne pouvez pas renommer sont affichés sous la forme de balises XML ; Autrement dit, avec moins de (\<) et supérieur à (\>) se connecte. Par exemple, le **schéma** nœud, **groupe choix** nœuds, **tout élément** nœuds, et **tout attribut** sont représentés dans le schéma arborescence avec les noms \<schéma\>, \<choix\>, \<tout\>, et \<AnyAttribute\>, respectivement. Le **nom de nœud** propriété pour ces nœuds est en lecture seule.  
  
 Au sein d’une donnée **enregistrement** nœud, vous ne pouvez pas avoir deux **attribut de champ** nœuds portant le même nom. Toutefois, vous pouvez avoir plusieurs **Fieldelement** nœud ou **enregistrement** nœud portant le même nom en tant que nœuds enfants du même **enregistrement** nœud, tant qu’ils ont tous les mêmes données de type (comme spécifié par leur **Type de données** propriété **élément de champ** nœuds ou leurs **Data Structure Type** pour **enregistrement** nœuds).  
  
 Lorsque vous attribuez un nom à **enregistrement** nœuds, **Fieldelement** nœuds, et **attribut de champ** , utilisez des noms descriptifs du rôle de l’élément ou attribut dans le message défini par le schéma. Par exemple, FirstName est probablement un bon choix pour le nom d’un **élément de champ** nœud qui permet de stocker le prénom d’une personne dans une structure d’adresse. Dans un message d'instance XML dans lequel apparaît le prénom James, l'élément correspondant prendrait l'aspect suivant :  
  
```  
    <FirstName>James</FirstName>  
```  
  
 Lorsque vous renommez **enregistrement** nœuds, **Fieldelement** nœuds, et **attribut de champ** nœuds, vous devez être conscient que tous les caractères sont autorisés dans les noms de nœud. Pour plus d’informations sur les caractères non autorisés, consultez [qui nœud nom de codage des caractères](../core/which-node-name-characters-get-encoded.md). Bien que l'Éditeur BizTalk permette d'utiliser les caractères non autorisés en les codant, il est souvent plus simple de ne pas y recourir. Pour plus d’informations sur la façon de caractères non autorisés sont codés, consultez [comment nœud nom de codage des caractères](../core/how-node-name-characters-get-encoded.md).  
  
 Outre les caractères qui ne sont pas autorisées dans les noms de nœud, sauf si elles sont encodées dans la représentation XSD du schéma, vous ne devez pas utiliser de mots réservés c# comme les noms des nœuds racine dans l’arborescence de schéma (sauf si vous fournissez valide **RootNode TypeName** valeur de la propriété) ou en tant que noms de fichiers de schéma.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Caractères de nom de nœud codés](../core/which-node-name-characters-get-encoded.md)  
  
-   [Mode de codage des caractères de nom de nœud](../core/how-node-name-characters-get-encoded.md)