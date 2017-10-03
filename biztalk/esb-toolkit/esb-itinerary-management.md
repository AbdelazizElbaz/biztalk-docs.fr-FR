---
title: "Gestion d’itinéraire d’ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f78240de-34da-4751-aceb-b69d81403124
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fb7c2566cbd445ea305089033935427b82046bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="esb-itinerary-management"></a>Gestion d’itinéraire d’ESB
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]offre deux options distinctes pour la gestion d’itinéraire ESB : centralisée et décentralisée. Cette section décrit les avantages et les risques pour chacune de ces options.  
  
## <a name="decentralized-esb-policy-management"></a>Gestion des stratégies de ESB décentralisée  
 Dans ce scénario, l’application cliente ESB fournit le contenu de la feuille de route ESB en tant que pièce jointe pour chaque message envoyé à l’architecture ESB. Le message contient un en-tête SOAP avec le contenu d’itinéraire. Lorsqu’un composant de pipeline reçoit le message, il décode le message, puis il promeut l’itinéraire dans le contexte de message pour le routage. Bien que cette conception offre la possibilité d’implémenter facilement un modèle de routage, entièrement permettant au client contrôler le flux d’un message présente les problèmes suivants :  
  
-   En autorisant le client déterminer les processus qui doivent être appliqués à un message, les détails des processus disponibles à partir de laquelle choisir sont transparents pour l’application cliente ESB. Cette pratique peut potentiellement exposer des informations sensibles à partir de la feuille de route ESB au client.  
  
-   Outre les problèmes de sécurité potentiels, permettant au client gérer les itinéraires pour être envoyé avec chaque message n’applique pas la feuille de route ESB en tant que stratégie, sauf si elle est implémentée pour un client spécifique. Par conséquent, les coûts de gestion des modifications pour mettre en œuvre une nouvelle version de la feuille de route sont très élevés et augmentent pour chaque nouveau type spécifique d’une application cliente approuvée.  
  
-   En permettant au client de passer de l’itinéraire entier avec le message envoyé, le client doit toujours se trouver dans le sous-système approuvé ; Sinon, l’itinéraire ESB peut spécifier potentiellement les instructions de traitement malveillant qui ne sont plus valides.  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]prend en charge le traitement des itinéraires soumis par le client ; Toutefois, cette option doit uniquement être utilisée pour la compatibilité descendante et à des fins de tests.  
  
 Pour plus d’informations sur l’activation des itinéraires du côté client, consultez [à l’aide d’un composant de Pipeline pour lire un itinéraire](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md).  
  
## <a name="centralized-esb-policy-management"></a>Gestion des stratégies centralisées ESB  
 Il existe de sécurité et de problèmes de synchronisation inhérente à l’autorisation d’un client envoyer des messages avec les itinéraires attachés, la meilleure pratique consiste à gérer les itinéraires ESB dans un référentiel central implémentés en tant que base de données SQL et inclus dans [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] à cet effet. En déployant les itinéraires vers un emplacement central, les stratégies d’itinéraire ESB peuvent être facilement gérés et modifiées sans avoir besoin de mettre en œuvre en cas de modifications côté client, et l’organisation peut contrôler le traitement des messages sans exposer potentiellement informations sensibles au client.  
  
 Composants de pipeline spécialisés sont fournies afin de déterminer l’itinéraire ESB approprié à joindre à un message entrant. Cette approche fournit deux options distinctes pour l’envoi d’un message pour le routage basé sur l’itinéraire :  
  
-   À l’aide de la première option, l’application cliente peut toujours indiquer un itinéraire ESB distinct à en fournissant des informations de référence d’itinéraire ESB dans l’en-tête SOAP, ainsi que le message de demande, au lieu de soumettre complet. Ces informations comprennent le nom d’itinéraire d’ESB et de version facultatif. Dans ce scénario, les clients peuvent toujours spécifier comment le message peut être routé, mais il n’existe aucun risque d’erreurs de synchronisation de stratégie ou de violations de sécurité de l’exposer le contenu de la feuille de route ESB pour les applications clientes.  
  
-   La deuxième option consiste à configurer l’ESB rampe d’entrée pour déterminer automatiquement l’itinéraire ESB approprié, basé sur le contenu ou le contexte du message, sans nécessiter d’informations d’en-tête à partir du client de soumission. Ce scénario permet aux organisations de contrôler le flux d’un message envoyé et élimine la nécessité pour le client être informé de la façon dont le message est routé.