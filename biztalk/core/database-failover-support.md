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
# <a name="database-failover-support"></a><span data-ttu-id="0289d-102">Prise en charge du basculement de base de données</span><span class="sxs-lookup"><span data-stu-id="0289d-102">Database Failover Support</span></span>
<span data-ttu-id="0289d-103">Vous pouvez passer une instance de la **PolicyFetchErrorHandler** délégué en tant que paramètre aux constructeurs surchargés de la **stratégie** classe.</span><span class="sxs-lookup"><span data-stu-id="0289d-103">You can pass an instance of the **PolicyFetchErrorHandler** delegate as a parameter to overloaded constructors of the **Policy** class.</span></span> <span data-ttu-id="0289d-104">Quand une erreur se produit lors de l'extraction des détails de la stratégie depuis la base de données, l'instance de délégué est appelée.</span><span class="sxs-lookup"><span data-stu-id="0289d-104">When an error occurs while fetching the policy details from the database, the delegate instance is invoked.</span></span> <span data-ttu-id="0289d-105">Vous pouvez également utiliser un bloc try-catch pour intercepter **RuleStoreConnectionException** et **RuleStoreCompatibilityException** les exceptions qui sont déclenchées lorsque le moteur de règles ne parvient pas à se connecter au moteur de règles base de données.</span><span class="sxs-lookup"><span data-stu-id="0289d-105">You can also use a try-catch block to trap **RuleStoreConnectionException** and **RuleStoreCompatibilityException** exceptions that are raised when the rule engine fails to connect to the Rule Engine database.</span></span>  
  
 <span data-ttu-id="0289d-106">Si vous ne passez pas une instance de la **PolicyFetchErrorHandler** délégué en tant que paramètre à la **stratégie** constructeur, ou si vous utilisez la **RèglesAppel** mettre en forme un orchestration, puis si une erreur se produit lors de l’extraction des détails de la stratégie à partir de la base de données, les événements suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="0289d-106">If you do not pass an instance of the **PolicyFetchErrorHandler** delegate as a parameter to the **Policy** constructor, or if you use the **CallRules** shape in an orchestration, then if an error occurs while fetching the policy details from the database, the following events happen:</span></span>  
  
1.  <span data-ttu-id="0289d-107">Le moteur de règles utilise les valeurs de la **PolicyFetchErrorHandlerAssembly** et **PolicyFetchErrorHandlerClass** les entrées de Registre sous **HKEY_LOCAL_MACHINE\Software\Microsoft\ BusinessRules\3.0**.</span><span class="sxs-lookup"><span data-stu-id="0289d-107">The rule engine uses the values of the **PolicyFetchErrorHandlerAssembly** and **PolicyFetchErrorHandlerClass** registry entries under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**.</span></span> <span data-ttu-id="0289d-108">Les valeurs par défaut pour le **PolicyFetchErrorHandlerAssembly** et **PolicyFetchErrorHandlerClass** sont des entrées de Registre **Microsoft.BizTalk.RuleEngineExtensions**et **Microsoft.BizTalk.RuleEngineExtension.ExceptionHelper** respectivement.</span><span class="sxs-lookup"><span data-stu-id="0289d-108">The default values for the **PolicyFetchErrorHandlerAssembly** and **PolicyFetchErrorHandlerClass** registry entries are **Microsoft.BizTalk.RuleEngineExtensions** and **Microsoft.BizTalk.RuleEngineExtension.ExceptionHelper** respectively.</span></span>  
  
2.  <span data-ttu-id="0289d-109">Le **ExceptionHelper** la classe implémente le **IPolicyFetchErrorMaker** interface.</span><span class="sxs-lookup"><span data-stu-id="0289d-109">The **ExceptionHelper** class implements the **IPolicyFetchErrorMaker** interface.</span></span>  
  
3.  <span data-ttu-id="0289d-110">Le moteur de règles appelle la **get_ErrorHandler** méthode sur le **IPolicyFetchErrorMaker** pour obtenir un pointeur vers la méthode de gestion des erreurs de l’interface et l’appelle.</span><span class="sxs-lookup"><span data-stu-id="0289d-110">The rule engine invokes the **get_ErrorHandler** method on the **IPolicyFetchErrorMaker** interface to get a pointer to the error-handling method and invokes it.</span></span>  
  
4.  <span data-ttu-id="0289d-111">La méthode de gestion des erreurs par défaut appelle la **SetDBFailure** (méthode), qui est définie dans BTSDBAccessor.dll.</span><span class="sxs-lookup"><span data-stu-id="0289d-111">The default error-handling method invokes the **SetDBFailure** method, which is defined in BTSDBAccessor.dll.</span></span>  
  
5.  <span data-ttu-id="0289d-112">Le **SetDBFailure** méthode provoque le service BizTalk pour l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="0289d-112">The **SetDBFailure** method causes the BizTalk service to shut down.</span></span> <span data-ttu-id="0289d-113">Le service BizTalk redémarre une minute après et se referme si les bases de données ne sont toujours pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="0289d-113">The BizTalk service restarts in one minute and shuts down if the databases are still not available.</span></span> <span data-ttu-id="0289d-114">Ce cycle se répète jusqu'à-ce que les bases de données soient disponibles.</span><span class="sxs-lookup"><span data-stu-id="0289d-114">This cycle repeats until the databases are available.</span></span>