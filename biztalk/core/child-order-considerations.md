---
title: "Considérations relatives à la commande enfant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4f7aa81-5c08-4932-9e28-31e22e037999
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0909a8d69f5079e493fbc579d6ef4b0ca56f9c61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="child-order-considerations"></a>Considérations relatives à la commande enfant

## <a name="requirements-for-header-in-a-flat-file"></a>Configuration requise pour l’en-tête dans un fichier plat
Il existe deux scénarios liés à des fichiers plats délimités, pour lequel les considérations particulières s’appliquent lors de la définition du **classement enfant** propriété. Le premier scénario concerne les situations où un document de fichier plat comporte un en-tête, un corps et éventuellement un code de fin. Dans ce scénario, vous devez observer les consignes suivantes :  
  
-   Vous devez définir le **classement enfant** propriété de l’enregistrement racine (délimité) de l’en-tête à **suffixés**.  
  
-   Si un code de fin n’est présent, vous devez définir le **classement enfant** propriété de l’enregistrement racine (délimité) du corps **suffixés**.  
  
-   Si un code de fin n’est pas présent, vous pouvez définir le **classement enfant** propriété de l’enregistrement racine (délimité) du corps **préfixe**, **InFix**, ou **Postfix**.  
  
-   Si un code de fin est présent, vous pouvez définir le **classement enfant** propriété de l’enregistrement racine (délimité) de ce code de fin pour **préfixe**, **InFix**, ou **Postfix**.  
  
-   Vous pouvez définir le **classement enfant** propriété d’enregistrements subordonnés délimités de l’en-tête, corps et code de fin **préfixe**, **InFix**, ou **suffixés**.  
  
 Le deuxième scénario associé à des fichiers plats délimités et **classement enfant** propriété est que cette propriété doit être définie en fonction des attendent les composants d’exécution pour les nœuds. Le paramètre correct pour le **classement enfant** propriété ne peut pas être évidente pour les nœuds racine et de groupe, comme illustré dans les scénarios suivants :  
  
-   **Nœud racine.** imaginez un fichier plat typique dont la structure se compose d'enregistrements suivis d'une combinaison retour chariot/saut de ligne. Le délimiteur sépare les enregistrements dans le fichier et la séquence est généralement la suivante : enregistrement, délimiteur, enregistrement, délimiteur, etc. Dans ce cas, le délimiteur suit toujours les données, ce qui correspond à un **classement enfant** de paramètre de la propriété **suffixés**.  
  
-   **Nœuds de groupe.** les nœuds de groupe affichés dans les représentations BizTalk Server et XSD du schéma ne sont pas explicitement présents dans la représentation de fichier plat du message d'instance. Imaginez un bon de commande contenant un ensemble d'enregistrements pour chaque élément de ligne. Imaginez également que ces enregistrements se répètent à maintes reprises pour représenter plusieurs éléments de ligne dans un seul bon de commande. Le schéma d’un tel message comprend généralement un nœud nommé LineItems qui servent de conteneur (parfois conceptuel) pour l’ensemble répété : dans la représentation sous forme de fichier plat du message d’instance, le conteneur LineItems est de nature conceptuel et représenté par la séquence appropriée de données et les délimiteurs ; dans la représentation XML du message d’instance, le conteneur LineItems est explicitement présent sous la forme d’un **LineItems** élément dans XML.  
  
 Imaginez un message contenant un nœud racine et un unique nœud de groupe. Il est facile de voir à quel endroit du flux d'entrée le dernier délimiteur appartiendrait au nœud racine. Par conséquent, la séquence données/délimiteur de la boucle conceptuelle serait simplement composée d'un ou plusieurs enregistrements d'élément de ligne. Il n'y a que dans le cas où il y aurait plus d'un enregistrement d'élément de ligne qu'un délimiteur les séparerait. Dans ce cas, les délimiteurs seraient un de moins que les ensembles des éléments délimités, et les délimiteurs se trouveraient entre les éléments délimités dans une structure appelée Infix.  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations concernant les enregistrements délimités](../core/delimited-record-considerations.md)   
-  **Le classement enfant (propriété de nœud des schémas de fichier plat)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]