---
title: "Le Gestionnaire d’erreurs Operations exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Ops adapters, error handler
- process management solution tutorial, Ops adapters
ms.assetid: e6c55f01-c004-4340-beaa-d77764ae34c1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93536733c884b4d5db57ba18619ebabdead17561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-sample-operations-error-handler"></a>Exemple de gestionnaire des erreurs d'opération
Le Gestionnaire d’erreurs operations exemple inclut trois assemblys principaux : **OperationsClient**, **OperationsHandler**, et **OperationsServer**.  
  
 La solution configure l’adaptateur à utiliser le **OpsClient** de l’objet dans le **OperationsClient** assembly. Évidemment, le **OpsClient** de l’objet implémente le **IOpsAIC** interface.  
  
 Le **OpsClient** object utilise le **IOperationsSystem** interface pour appeler le **OpsHandler** par le biais de l’objet le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] fonctionnalité de communication à distance. Le **IOperationsSystem** interface apparaît comme suit :  
  
```  
public interface IOperationsSystem  
{  
    void Initialize(string initData);  
    void Post(string originMachine, byte[] message);  
}  
  
```  
  
 Le **OperationsServer**, une application console, écoute les demandes de la **OpsHandler** de l’objet et fait Office de serveur pour le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] fonctionnalité de la communication à distance. Appel de la **Execute** méthode de la **OpsClient** objet appelle à son tour le **Post** méthode de la **OpsHandler** objet.  
  
 Le **OpsHandler** méthodes répondent en écrivant leurs chaînes d’arguments à l’aide de la **Trace** objet. Cette opération valide les erreurs dans la console. Pour plus d’informations sur la **Trace** d’objets, consultez « Classe Trace » dans le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] bibliothèque de classes.  
  
> [!NOTE]
>  Le modèle est identique à celle de la **OrderHandler** dans lequel une interface spécifie les appels de méthode entre un client et un objet distant interprocessus. Il existe, toutefois, une couche supplémentaire de détour entre le **OpsClient** et **OpsHandler**.  
  
## <a name="see-also"></a>Voir aussi  
 [L’adaptateur Ops](../core/the-ops-adapter.md)