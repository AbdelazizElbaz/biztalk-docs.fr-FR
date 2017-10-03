---
title: "Exceptions et gestion des erreurs avec l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions and error handling
- error handling, troubleshooting
- troubleshooting, exceptions and error handling
ms.assetid: 598a25c5-6905-4c0c-835b-159d827b2269
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 043f76f7fc730430610b7598bbab208ca8b135a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exceptions-and-error-handling-with-the-sap-adapter"></a>Exceptions et gestion des erreurs avec l’adaptateur SAP
Répertorie les exceptions qui le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] lève. Il peuvent contenir :  
  
-   Une exception interne qui est une exception levée système par le .NET Framework  
  
-   Une exception levée LOB par la bibliothèque cliente LOB.  
  
 Pour plus d’informations sur l’exception interne, consultez la documentation de .NET Framework ou SAP. Exceptions contiennent également un message d’erreur détaillé qui peut-être aider à résoudre le problème.  

## <a name="exception-descriptions"></a>Description des exceptions  
|Exception|Cause possible/Description|  
|---------------|---------------------------------|  
|ObjectDisposedException|L’adaptateur lève cette exception lorsque le client de carte tente d’accéder à la réponse XMLReader après que qu’il a été supprimé.|  
|XmlReaderGenerationException|L’adaptateur lève cette exception lorsqu’il est impossible de générer un XmlReader à partir du message de sortie. Cela peut également être dû à des problèmes avec les données reçues à partir du système SAP. Recherchez l’exception interne et le message d’erreur pour plus d’informations.|  
|InvalidUriException|Cette exception est levée lorsque l’URI de connexion n’a pas les composants requis pour la chaîne de connexion.|  
|ConnectionException|Cette exception est levée lorsqu’il existe un problème de connexion au système SAP ou si une connexion sous-jacente devient non valide, soit en raison d’une erreur sur le système SAP, soit en raison d’un problème réseau.|  
|TimeoutException|Cette exception est levée lorsque le délai d’attente spécifié pour une opération est écoulée. L’exception interne contient les caractéristiques de la raison pour laquelle le délai d’attente spécifié n’était pas suffisant.|  
|XmlReaderParsingException|L’adaptateur lève cette exception si elle ne prend pas en charge le type spécifié, ou si une valeur incorrecte est spécifiée pour le type. En outre, le code XML d’entrée peut être incorrect. Une valeur incorrecte inclut les cas où la quantité maximale de texte ou le nombre maximal de chiffres est dépassée. Le code XML d’entrée peut être incorrect si le nom de l’opération ou l’espace de noms est incorrect.|  
|RFCException (dérivée de AdapterException)|L’adaptateur lève cette exception si une erreur s’est reçue du système SAP. L’exception interne est l’exception réelle reçue du système SAP.|  
|UnsupportedOperationException|L’adaptateur lève cette exception lorsque le client de l’adaptateur spécifie une action non valide.|  
|MetadataException|L’adaptateur lève cette exception si une erreur se produit pendant la récupération des métadonnées, parcourir ou rechercher.|  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)