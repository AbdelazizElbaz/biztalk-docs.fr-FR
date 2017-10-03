---
title: Objet Recaller | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recaller object
- Invoke method
- process management solution tutorial, Recaller object
- process management solution tutorial, errors
ms.assetid: b30ad1ae-475f-4913-b402-4d3263fcf072
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f7703eb9145b1249872902d0b867fe22622ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-recaller-object"></a>Objet Recaller
La solution de gestion des processus d'entreprise fournit des appels de méthodes d'objet ayant échoué afin de réaliser, de façon générique, de nouvelles tentatives d'appels. La solution procède par l’intermédiaire du **Recaller** de l’objet dans le **ExceptionHandler** orchestration. Le **ExceptionHandler** orchestration utilise l’objet de nouvelles tentatives d’appels de méthode d’objet. Pour plus d’informations, consultez [l’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md).  
  
## <a name="the-invoke-method"></a>La méthode Invoke  
 Le **Recaller** objet possède une méthode unique, statique, **Invoke**. Car elle est statique, vous devez jamais créer une instance de la **Recaller** objet. Vous pouvez utiliser la **Invoke** méthode de trois façons : pour construire un objet, pour appeler une méthode statique pour un objet ou d’appeler une méthode non statique d’un objet.  
  
> [!NOTE]
>  Le **Invoke** méthode sert de wrapper pour le **Type.InvokeMember** méthode dans le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] bibliothèque de classes.  
  
### <a name="arguments-for-the-invoke-method"></a>Arguments pour la méthode Invoke  
 Le tableau suivant décrit les arguments pour le **Invoke** méthode :  
  
|Paramètre|Type| Description|  
|---------------|----------|-----------------|  
|*t*|**Type**|Type de l'objet à partir duquel appeler la méthode.|  
|*obj*|**Objet**|Instance de l'objet à utiliser.|  
|*methodName*|**chaîne**|Le nom de la méthode à appeler.|  
|*args*|**Tableau**|Un tableau de type **objet** contenant les arguments de la méthode.|  
  
 Pour appeler le constructeur pour un objet, utilisez une chaîne vide (« ») ou **null** pour *methodName*.  
  
 Pour appeler une méthode statique, utilisez **null** pour *obj*.  
  
 Pour appeler une méthode non statique, indiquez tous les arguments.  
  
> [!NOTE]
>  À l’aide de **null** comme valeur de l’argument de Type *t*, entraîne **Invoke** pour lever une **ArgumentNullException** exception. L’argument *t* ne doit pas être null, car le **Invoke** utilise le **Type.InvokeMember** [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] (méthode).  
  
## <a name="calling-invoke"></a>Appel de la méthode Invoke  
 Dans la solution, seule la **ExceptionHandler** d’orchestration utilise la **Recaller** objet. Le **ExceptionHandler** est, à son tour, utilisés par d’autres orchestrations. Les valeurs passées à la **Invoke** méthode proviennent de ces autres orchestrations. Par exemple, le code suivant s’affiche dans le **activer** orchestration dans le **InitialException** forme Expression :  
  
```  
Ex = CodeEx;  
ObjectType = orderHandler.GetType();  
CalledObject = orderHandler;  
Reason = "Standard Activate Failed";  
MethodName = "Activate";  
ParameterArray = System.Array.CreateInstance(typeof(System.Object),  
                                              3 );  
ParameterArray.SetValue(ServiceType, 0);  
ParameterArray.SetValue(OrderMsg.CustNum, 1);  
ParameterArray.SetValue(OrderMsg.OrderNum, 2);  
ReturnValue = null; // no return value expected  
  
```  
  
 Notez comment le code crée un tableau à l’aide de **System.Array.CreateInstance** et utilise le **SetValue** méthode pour stocker les valeurs y.  
  
 Après la forme Expression, l’orchestration appelle la **ExceptionHandler** orchestration. Le code suivant illustre la manière dont le Concepteur d'orchestration convertit la forme Appel :  
  
```  
call Microsoft.Samples.  
    BizTalk.SouthridgeVideo.  
        OrderManager.ExceptionHandlerOrch  
            (  
                Reason,  
                Ex,  
                CalledObject,  
                MethodName,   
                ParameterArray,   
                OrderCorrelation,   
                OrderMsg,   
                out ReturnValue,   
                ObjectType  
            );  
  
```  
  
 Dans le **ExceptionHandler** orchestration, le code suivant s’affiche dans le **appeler le Code d’origine** forme Expression :  
  
```  
ReturnValue =   
    Microsoft.Samples.  
        BizTalk.SouthridgeVideo.  
            Utilities.Recaller.  
                Invoke(  
                    ObjectType,  
                    CalledObject,  
                    MethodName,  
                    ParameterArray  
                );  
```  
  
 En dépit du fait que les noms des arguments correspondent à ceux présents dans l'appel de l'orchestration Activate, vous remarquerez que, lors de l'appel d'orchestrations, les arguments sont filtrés par ordre et non pas par nom.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [L’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md)