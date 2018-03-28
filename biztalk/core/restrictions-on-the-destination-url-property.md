---
title: Restrictions sur la propriété URL de Destination | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [HTTP adapters], restrictions
- HTTP adapters, restrictions
ms.assetid: 982a5122-e43d-4730-a8b9-ceb1ff88638c
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f7966fccca324a1453f0ea84e79cd7d9d3d55ad
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="restrictions-on-the-destination-url-property"></a>Restrictions sur la propriété URL de Destination
L'URL de destination est une chaîne qui indique l'adresse du serveur HTTP auquel vous souhaitez envoyer des messages à l'aide du protocole HTTP.  
  
 Les règles et restrictions suivantes s'appliquent à la propriété URL de destination :  
  
-   Vous devez toujours indiquer la propriété URL de destination selon le format suivant :  
  
     http[s]://\<host\>[:\<port\>][/\<path\>[/\<file\>[?\<query-string\>]]]  
  
-   L'intégralité de la chaîne doit ou ne doit pas être un codage URI.  
  
-   La chaîne entière, à l’exception de la chaîne de requête ne peut pas contenir les caractères suivants : \< \> : \ &#124; » ? *.  
  
-   Cette propriété ne respecte pas la casse.  
  
-   La longueur de la chaîne ne doit pas dépasser 256 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’un port d’envoi HTTP](../core/configuring-an-http-send-port.md)