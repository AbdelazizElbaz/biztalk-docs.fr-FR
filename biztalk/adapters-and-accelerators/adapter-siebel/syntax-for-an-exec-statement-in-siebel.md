---
title: Syntaxe pour une instruction EXEC dans Siebel | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EXEC statement, syntax for
- Data Provider for Siebel, EXEC statement
ms.assetid: c5534102-bf37-4b39-83ab-e09483744c4d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d18481b206b1be7e0062762c1844305fc36e10f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="syntax-for-an-exec-statement-in-siebel"></a><span data-ttu-id="edb83-102">Syntaxe pour une instruction EXEC dans Siebel</span><span class="sxs-lookup"><span data-stu-id="edb83-102">Syntax for an EXEC Statement in Siebel</span></span>
<span data-ttu-id="edb83-103">À l’aide de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients peuvent également effectuer une opération d’exécution sur le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edb83-103">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients can also perform an EXEC operation on the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="edb83-104">La syntaxe de l’instruction EXEC est :</span><span class="sxs-lookup"><span data-stu-id="edb83-104">The syntax for the EXEC statement is:</span></span>  
  
```  
EXEC  
<Business Service name>.<Business Service method>  
\<value 1..n>,  
@parameter 1..n [OUTPUT],  
@parameter 1..n = <value>  
  
```  
  
 <span data-ttu-id="edb83-105">Dans la syntaxe précédente, `\<value 1..n>` représente un ensemble de paramètres sans nom.</span><span class="sxs-lookup"><span data-stu-id="edb83-105">In the preceding syntax, `\<value 1..n>` represents a set of unnamed parameters.</span></span> <span data-ttu-id="edb83-106">Il s’agit des valeurs codées en dur.</span><span class="sxs-lookup"><span data-stu-id="edb83-106">These are hard-coded values.</span></span> <span data-ttu-id="edb83-107">Ils représentent généralement dans les paramètres.</span><span class="sxs-lookup"><span data-stu-id="edb83-107">They usually represent IN parameters.</span></span>  <span data-ttu-id="edb83-108">Ils peuvent également représenter des paramètres INOUT.</span><span class="sxs-lookup"><span data-stu-id="edb83-108">They can also represent INOUT parameters.</span></span> <span data-ttu-id="edb83-109">Toutefois, si une valeur codée en dur est utilisée pour un paramètre INOUT, la valeur de sortie associée à ce paramètre ne peut pas être récupérée après l’exécution de l’instruction EXEC.</span><span class="sxs-lookup"><span data-stu-id="edb83-109">However, if a hard-coded value is used for an INOUT parameter, the output value associated with that parameter cannot be retrieved after the EXEC statement is executed.</span></span>  
  
 <span data-ttu-id="edb83-110">Le `@parameter 1..n` syntaxe représente un jeu de paramètres nommés, ce qui peuvent être IN, INOUT, ou les paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="edb83-110">The `@parameter 1..n` syntax represents a set of named parameters, which can be IN, INOUT, or OUT parameters.</span></span> <span data-ttu-id="edb83-111">Les paramètres de sortie doivent être suivis par le **sortie** (mot clé).</span><span class="sxs-lookup"><span data-stu-id="edb83-111">The output parameters must be followed by the **OUTPUT** keyword.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edb83-112">Le **sortie** mot clé doit être utilisé qu’avec les paramètres de sortie et non avec les paramètres INOUT.</span><span class="sxs-lookup"><span data-stu-id="edb83-112">The **OUTPUT** keyword must only be used with OUT parameters and not with INOUT parameters.</span></span>  
  
 <span data-ttu-id="edb83-113">Pour spécifier la ligne des valeurs de paramètre, utilisez le `@parameter 1..n = <value>` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="edb83-113">To specify parameter values inline, use the `@parameter 1..n = <value>` syntax.</span></span>  
  
 <span data-ttu-id="edb83-114">Tous les paramètres doivent être séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="edb83-114">All parameters must be comma-separated.</span></span>  
  
 <span data-ttu-id="edb83-115">Voici quelques exemples d’instructions EXEC :</span><span class="sxs-lookup"><span data-stu-id="edb83-115">The following are examples of EXEC statements:</span></span>  
  
```  
EXEC ExtractDataService.Echo @In, @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo 'InputValue', @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo @InOut, @Out OUTPUT, @In='InputValue'  
  
EXEC ExtractDataService.Echo 'InputValue', @Out OUTPUT, @InOut='InputValue'  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="edb83-116">Chaque nom de paramètre (comme `@In` dans l’exemple précédent) doit correspondre au nom de l’argument correspondant dans la méthode de Service d’entreprise Siebel.</span><span class="sxs-lookup"><span data-stu-id="edb83-116">Every parameter name (like `@In` in the preceding example) must match the corresponding argument name in the Siebel Business Service method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb83-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edb83-117">See Also</span></span>  
 [<span data-ttu-id="edb83-118">Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="edb83-118">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)