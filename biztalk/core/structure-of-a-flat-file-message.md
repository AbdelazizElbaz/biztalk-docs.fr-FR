---
title: "Structure d’un Message de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00f2adf6-a47c-498b-b5ae-c6bd55bafceb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: badb8aacf6f2ed8ce9e38f1ea6bbe432a1d3b89e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="structure-of-a-flat-file-message"></a>Structure d'un message de fichier plat
Dans le contexte de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un message d’instance de fichier plat est un fichier texte qui peut contenir trois parties logiques : un en-tête, un corps et un code de fin, dans cet ordre. L’en-tête et le code de fin sont facultatifs. L’exemple suivant indique un message d’instance de fichier plat constitué des trois parties, le corps affiché en caractères gras.  
  
```  
Microsoft Corporation  
One Microsoft Way  
Redmond, WA 98033  
  
TRANSACTION-1111,1  
  
```  
  
 Pour que le désassembleur de fichier plat puisse distinguer correctement l'en-tête du corps et du code de fin d'un message d'instance de fichier plat, vous devez créer et configurer un schéma séparé pour chaque.  
  
 Au sein d’une partie précise d’un message d’instance de fichier plat, différents éléments de données sont regroupés en enregistrements, qui peuvent à leur tour contenir des sous-enregistrements comprenant des éléments de données individuels, correspondant aux champs. Ces enregistrements et champs sont distingués les uns des autres à l’aide de deux méthodologies de base différentes. La première méthodologie, dite positionnelle, définit une longueur pré-établie pour chaque élément de données,  en utilisant des caractères de remplissage pour agrandir un élément de données plus court de façon qu'il s’adapte à la longueur attendue. La seconde méthodologie, dite délimitée, utilise un ou plusieurs caractères spéciaux pour séparer les éléments de données les uns des autres. Cette méthodologie permet d’éviter d’avoir à ajouter des caractères de remplissage superflus, mais implique de nouvelles considérations lorsque les données elles-mêmes contiennent le caractère ou la séquence de caractères utilisée comme délimiteur.  
  
 Le reste de cette section propose une présentation détaillée de la gestion par BizTalk Server des en-têtes, corps et codes de fin dans les messages d'instance de fichier plat. Vous y apprendrez en particulier comment BizTalk Server décide s'il faut inclure ou non les éléments facultatifs, comment il sépare les parties des messages d’instance de fichier plat entrants et associe les parties des messages d'instance de fichier plat sortants. Cette section propose également des informations supplémentaires sur les différences existant entre les messages d'instance de fichier plat utilisant des champs et enregistrements positionnels et les messages d'instance de fichier plat utilisant des champs et enregistrements délimités.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [En-têtes de Message de fichier plat](../core/flat-file-message-headers.md)  
  
-   [Corps de Message de fichier plat](../core/flat-file-message-bodies.md)  
  
-   [Codes de Message de fichier plat](../core/flat-file-message-trailers.md)  
  
-   [Messages de fichier plat avec des enregistrements positionnels](../core/flat-file-messages-with-positional-records.md)  
  
-   [Messages de fichier plat avec des enregistrements délimités](../core/flat-file-messages-with-delimited-records.md)  
  
-   [Migration des enregistrements de fichier plat](../core/migrating-flat-file-records.md)