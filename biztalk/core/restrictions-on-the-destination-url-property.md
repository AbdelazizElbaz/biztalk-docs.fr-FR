---
title: "Restrictions sur la propriété URL de Destination | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [HTTP adapters], restrictions
- HTTP adapters, restrictions
ms.assetid: 982a5122-e43d-4730-a8b9-ceb1ff88638c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0788b693027fb803b121b1b732cb3ee126897e7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-the-destination-url-property"></a>Restrictions sur la propriété URL de Destination
L'URL de destination est une chaîne qui indique l'adresse du serveur HTTP auquel vous souhaitez envoyer des messages à l'aide du protocole HTTP.  
  
 Les règles et restrictions suivantes s'appliquent à la propriété URL de destination :  
  
-   Vous devez toujours indiquer la propriété URL de destination selon le format suivant :  
  
     http [s]  ://\<hôte > [ :\<port >] [/\<chemin d’accès > [/\<fichier > [ ?\< chaîne de requête >]]]  
  
-   L'intégralité de la chaîne doit ou ne doit pas être un codage URI.  
  
-   La chaîne entière, à l’exception de la chaîne de requête ne peut pas contenir les caractères suivants : \< > : \ &#124; " ? *.  
  
-   Cette propriété ne respecte pas la casse.  
  
-   La longueur de la chaîne ne doit pas dépasser 256 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’un Port d’envoi HTTP](../core/configuring-an-http-send-port.md)