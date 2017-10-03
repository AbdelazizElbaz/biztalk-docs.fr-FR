---
title: "Prise en charge du basculement de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09347fdd-2929-4ed9-b0d8-698508663ecd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3bbc795191eb2c13ca35d55846719cebc20d61a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="database-failover-support"></a>Prise en charge du basculement de base de données
Vous pouvez passer une instance de la **PolicyFetchErrorHandler** délégué en tant que paramètre aux constructeurs surchargés de la **stratégie** classe. Quand une erreur se produit lors de l'extraction des détails de la stratégie depuis la base de données, l'instance de délégué est appelée. Vous pouvez également utiliser un bloc try-catch pour intercepter **RuleStoreConnectionException** et **RuleStoreCompatibilityException** les exceptions qui sont déclenchées lorsque le moteur de règles ne parvient pas à se connecter au moteur de règles base de données.  
  
 Si vous ne passez pas une instance de la **PolicyFetchErrorHandler** délégué en tant que paramètre à la **stratégie** constructeur, ou si vous utilisez la **RèglesAppel** mettre en forme un orchestration, puis si une erreur se produit lors de l’extraction des détails de la stratégie à partir de la base de données, les événements suivants se produisent :  
  
1.  Le moteur de règles utilise les valeurs de la **PolicyFetchErrorHandlerAssembly** et **PolicyFetchErrorHandlerClass** les entrées de Registre sous **HKEY_LOCAL_MACHINE\Software\Microsoft\ BusinessRules\3.0**. Les valeurs par défaut pour le **PolicyFetchErrorHandlerAssembly** et **PolicyFetchErrorHandlerClass** sont des entrées de Registre **Microsoft.BizTalk.RuleEngineExtensions**et **Microsoft.BizTalk.RuleEngineExtension.ExceptionHelper** respectivement.  
  
2.  Le **ExceptionHelper** la classe implémente le **IPolicyFetchErrorMaker** interface.  
  
3.  Le moteur de règles appelle la **get_ErrorHandler** méthode sur le **IPolicyFetchErrorMaker** pour obtenir un pointeur vers la méthode de gestion des erreurs de l’interface et l’appelle.  
  
4.  La méthode de gestion des erreurs par défaut appelle la **SetDBFailure** (méthode), qui est définie dans BTSDBAccessor.dll.  
  
5.  Le **SetDBFailure** méthode provoque le service BizTalk pour l’arrêter. Le service BizTalk redémarre une minute après et se referme si les bases de données ne sont toujours pas disponibles. Ce cycle se répète jusqu'à-ce que les bases de données soient disponibles.