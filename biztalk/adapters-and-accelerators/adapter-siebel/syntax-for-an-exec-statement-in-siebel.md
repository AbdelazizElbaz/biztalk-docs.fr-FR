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
ms.openlocfilehash: 4db9ca810860ea64ffa474725dc485fecfaa5e78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="syntax-for-an-exec-statement-in-siebel"></a>Syntaxe pour une instruction EXEC dans Siebel
À l’aide de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients peuvent également effectuer une opération d’exécution sur le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. La syntaxe de l’instruction EXEC est :  
  
```  
EXEC  
<Business Service name>.<Business Service method>  
<value 1..n>,  
@parameter 1..n [OUTPUT],  
@parameter 1..n = <value>  
  
```  
  
 Dans la syntaxe précédente, `\<value 1..n\>` représente un ensemble de paramètres sans nom. Il s’agit des valeurs codées en dur. Ils représentent généralement dans les paramètres.  Ils peuvent également représenter des paramètres INOUT. Toutefois, si une valeur codée en dur est utilisée pour un paramètre INOUT, la valeur de sortie associée à ce paramètre ne peut pas être récupérée après l’exécution de l’instruction EXEC.  
  
 Le `@parameter 1..n` syntaxe représente un jeu de paramètres nommés, ce qui peuvent être IN, INOUT, ou les paramètres de sortie. Les paramètres de sortie doivent être suivis par le **sortie** (mot clé).  
  
> [!NOTE]
>  Le **sortie** mot clé doit être utilisé qu’avec les paramètres de sortie et non avec les paramètres INOUT.  
  
 Pour spécifier la ligne des valeurs de paramètre, utilisez le `@parameter 1..n = <value>` syntaxe.  
  
 Tous les paramètres doivent être séparées par des virgules.  
  
 Voici quelques exemples d’instructions EXEC :  
  
```  
EXEC ExtractDataService.Echo @In, @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo 'InputValue', @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo @InOut, @Out OUTPUT, @In='InputValue'  
  
EXEC ExtractDataService.Echo 'InputValue', @Out OUTPUT, @InOut='InputValue'  
  
```  
  
> [!NOTE]
>  Chaque nom de paramètre (comme `@In` dans l’exemple précédent) doit correspondre au nom de l’argument correspondant dans la méthode de Service d’entreprise Siebel.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)