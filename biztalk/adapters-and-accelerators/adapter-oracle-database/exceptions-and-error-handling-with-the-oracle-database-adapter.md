---
title: "Exceptions et gestion des erreurs avec l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exception, LOB
- exception, inner
- exceptions, error handling
- error handling, exceptions
ms.assetid: df9a1244-63cd-438e-8a06-99383fbeba2c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bd85c53a1e13d127883e463cafec742f2751722
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exceptions-and-error-handling-with-the-oracle-database-adapter"></a>Exceptions et gestion des erreurs avec l’adaptateur de base de données Oracle
Cette section répertorie les exceptions qui le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] lève. Il peuvent contenir :  
  
-   Une exception interne qui est une exception levée système par le .NET Framework.  
  
-   Une exception levée LOB par la bibliothèque cliente LOB.  
  
 Pour plus d’informations sur l’exception interne, consultez la documentation de .NET Framework ou Oracle respectif. Exceptions contiennent également un message d’erreur détaillé qui vous aide à résoudre le problème.  
  
|Exception|Cause possible/Description|  
|---------------|---------------------------------|  
|XmlReaderParsingException|L’adaptateur lève cette exception si elle ne prend pas en charge le type spécifié, ou si une valeur incorrecte est spécifiée pour le type. En outre, le code XML d’entrée peut être incorrect. Une valeur incorrecte inclut les cas où la quantité maximale de texte ou le nombre maximal de chiffres est dépassée. Le code XML d’entrée peut être incorrect si le nom de l’opération ou l’espace de noms est incorrect.|  
|UnsupportedOperationException|L’adaptateur lève cette exception lorsque le client de l’adaptateur spécifie une action non valide.|  
|ArgumentException|L’adaptateur lève cette exception si une valeur incorrecte est spécifiée pour un argument.|  
|NotImplementedException|L’adaptateur lève cette exception si une méthode dans le lecteur XMLReader n’est pas implémentée.|  
|ArgumentNullException|L’adaptateur lève cette exception si un argument requis n’est pas spécifié.|  
|ArgumentOutOfRangeException|L’adaptateur lève cette exception si elle tente d’accéder à une entité d’inexistant ou d’une entité d’out-of-range.|  
|XmlReaderGenerationException|L’adaptateur lève cette exception lorsqu’il est impossible de générer un XmlReader à partir du message de sortie.|  
|MetadataException|L’adaptateur lève cette exception si une erreur se produit pendant la récupération des métadonnées, parcourir ou rechercher.|  
|CredentialsException|L’adaptateur lève cette exception s’il existe un problème la récupération ou l’utilisation de jetons de sécurité ou si les informations d’identification requises ne sont pas spécifiées.|  
|InvalidUriException|L’adaptateur lève cette exception si l’URI de connexion n’a pas les composants requis pour la chaîne de connexion.|  
|ConnectionException|L’adaptateur lève cette exception s’il existe un problème de connexion à la base de données Oracle à l’aide de ODP.NET. L’exception interne contient l’exception d’Oracle.|  
|TimeoutException|L’adaptateur lève cette exception si le délai d’attente spécifié pour une opération est écoulée. L’exception interne contient les caractéristiques de la raison pour laquelle le délai d’attente spécifié n’était pas suffisant.|  
|ListenerException|L’adaptateur lève cette exception s’il existe un problème lors de la réception d’un message à partir du système cible. Ce message indique un problème lié à l’écouteur d’Oracle. L’exception interne a les caractéristiques du problème.|  
|TargetSystemException|L’adaptateur lève cette exception si Oracle retourne une erreur ou une réponse non valide. L’exception interne contient l’exception de runtime Oracle.|  
|InvalidOperationException|L’adaptateur lève cette exception si l’adaptateur tente d’effectuer une opération non valide sur le système cible. L’exception interne contient les détails de l’opération non valide en cours d’exécution.|  
|OverflowException|L’adaptateur lève cette exception si lors de l’opération qui contiennent des types de données numériques Oracle à l’intérieur des jeux de données ou faiblement typée REF CURSOR, une valeur élevée est spécifiée pour ces types de données numériques Oracle qui ne tiennent pas dans le type .NET respectif.|  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)