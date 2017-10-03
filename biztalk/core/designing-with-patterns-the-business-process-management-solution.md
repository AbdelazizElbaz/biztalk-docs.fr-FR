---
title: "Conception de modèles : la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- patterns [process management solutions], examples
- patterns [process management solutions], designing
- examples, programming patterns
- designing, programming patterns
ms.assetid: 0583f4a4-01db-4d5b-a1f5-1694c1ddbd30
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91da8c63fc46ee90696e257bfd6142b5088af305
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designing-with-patterns-the-business-process-management-solution"></a>Conception de modèles : la Solution gestion des processus d’entreprise
La solution gestion des processus d’entreprise montre une façon de construire un gestionnaire de processus dans une application BizTalk. Elle utilise un composant pour sélectionner et contrôler la séquence d'étapes du traitement de commande. La solution prend une commande (par exemple, pour un nouveau service, un changement ou une annulation de service), la consigne et en accuse réception avant de la transmettre pour traitement. Le traitement de la commande consiste en une ou plusieurs étapes. Enfin, la solution renvoie une réponse finale à la demande d'origine.  
  
 Une solution de gestion des processus bien conçue vous permet d'ajouter et de soustraire des étapes du processus sans devoir reconstruire le reste de l'application. C'est précisément ce que permet l'approche adoptée dans cette solution. Le traitement de la commande est réparti en étapes distinctes, indépendantes. Toutes lisent à partir du même port et utilisent un filtre pour déterminer les messages qu'il leur revient de traiter. Ce processus est décrit de façon plus précise dans la section « Modèles ».  
  
 Cette solution accepte des entrées via un service Web, mais vous pouvez également utiliser une interface autre que de service via une connexion FTP. Cette fonctionnalité simule la manière dont l'application pourrait être utilisée dans un système de traitement par lot.  
  
## <a name="patterns"></a>Modèles  
 Le schéma suivant présente une version simplifiée des modèles dans la solution de gestion des processus d'entreprise, comme décrit dans la section précédente.  
  
 ![Modèles de Solution gestion des processus métier](../core/media/bts-cp-business-process-management-patterns.gif "bts_cp_Business_Process_Management_Patterns")  
  
 La solution se compose des éléments suivants : l’interface de service, le canal FTP, divers convertisseurs, le Gestionnaire de processus et les deux étapes de traitement. Les quatre convertisseurs de la section de pré-traitement créent un message d'accusé de réception qui est renvoyé à l'interface du service, génèrent une entrée dans une base de données d'historique ou de suivi, et créent une entrée dans le système du service. Le quatrième convertisseur crée le message dont le gestionnaire de processus a besoin. Ce dernier contrôle, à son tour, les étapes de traitement.  
  
 Dans de nombreuses implémentations du gestionnaire de processus, ce dernier suit l'état du traitement. Comme le montre le schéma, cette implémentation modifie cet aspect. Dans cette solution, le gestionnaire de processus insère un indicateur dans le message, indiquant l'étape de traitement suivante du message. Ensuite, chaque étape utilise un filtre pour déterminer si elle doit ou non traiter un message particulier.  
  
 Grâce à cette approche, le gestionnaire de processus ne doit pas maintenir d'informations de routage. Tous les messages échangés entre le gestionnaire et les diverses étapes utilisent les mêmes ports. Pour ajouter une étape, il suffit d'ajouter un composant qui envoie et reçoit sur les ports appropriés, et filtre pour obtenir le numéro d'étape correct. Aucune modification n'est requise au niveau du gestionnaire de processus proprement dit.  
  
 Notez que le schéma est loin d'être exhaustif. En fait, les étapes de traitement communiquent avec les processus principaux. La solution peut également collecter des informations historiques en plusieurs points du processus. Il se peut surtout que la logique du gestionnaire de processus ne soit pas spécifiée. L'utilisation de connexions synchrones ou asynchrones n'est pas non plus spécifiée. Ces aspects seront abordés dans les sections suivantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles dans la Solution gestion des processus d’entreprise](../core/patterns-in-the-business-process-management-solution.md)   
 [Conversion des modèles de la Solution gestion des processus d’entreprise](../core/translating-the-patterns-of-the-business-process-management-solution.md)