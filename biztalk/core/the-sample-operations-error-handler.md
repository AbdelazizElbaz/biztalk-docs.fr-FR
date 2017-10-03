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
# <a name="the-sample-operations-error-handler"></a><span data-ttu-id="1d1d9-102">Exemple de gestionnaire des erreurs d'opération</span><span class="sxs-lookup"><span data-stu-id="1d1d9-102">The Sample Operations Error Handler</span></span>
<span data-ttu-id="1d1d9-103">Le Gestionnaire d’erreurs operations exemple inclut trois assemblys principaux : **OperationsClient**, **OperationsHandler**, et **OperationsServer**.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-103">The sample operations error handler has three major assemblies: **OperationsClient**, **OperationsHandler**, and **OperationsServer**.</span></span>  
  
 <span data-ttu-id="1d1d9-104">La solution configure l’adaptateur à utiliser le **OpsClient** de l’objet dans le **OperationsClient** assembly.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-104">The solution configures the adapter to use the **OpsClient** object in the **OperationsClient** assembly.</span></span> <span data-ttu-id="1d1d9-105">Évidemment, le **OpsClient** de l’objet implémente le **IOpsAIC** interface.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-105">As you'd expect, the **OpsClient** object implements the **IOpsAIC** interface.</span></span>  
  
 <span data-ttu-id="1d1d9-106">Le **OpsClient** object utilise le **IOperationsSystem** interface pour appeler le **OpsHandler** par le biais de l’objet le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] fonctionnalité de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-106">The **OpsClient** object uses the **IOperationsSystem** interface to call the **OpsHandler** object through the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] remoting feature.</span></span> <span data-ttu-id="1d1d9-107">Le **IOperationsSystem** interface apparaît comme suit :</span><span class="sxs-lookup"><span data-stu-id="1d1d9-107">The **IOperationsSystem** interface appears as follows:</span></span>  
  
```  
public interface IOperationsSystem  
{  
    void Initialize(string initData);  
    void Post(string originMachine, byte[] message);  
}  
  
```  
  
 <span data-ttu-id="1d1d9-108">Le **OperationsServer**, une application console, écoute les demandes de la **OpsHandler** de l’objet et fait Office de serveur pour le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] fonctionnalité de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-108">The **OperationsServer**, a console application, listens for requests for the **OpsHandler** object and acts as the server for the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] remoting feature.</span></span> <span data-ttu-id="1d1d9-109">Appel de la **Execute** méthode de la **OpsClient** objet appelle à son tour le **Post** méthode de la **OpsHandler** objet.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-109">Calling the **Execute** method of the **OpsClient** object in turn invokes the **Post** method of the **OpsHandler** object.</span></span>  
  
 <span data-ttu-id="1d1d9-110">Le **OpsHandler** méthodes répondent en écrivant leurs chaînes d’arguments à l’aide de la **Trace** objet.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-110">The **OpsHandler** methods respond by writing out their argument strings using the **Trace** object.</span></span> <span data-ttu-id="1d1d9-111">Cette opération valide les erreurs dans la console.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-111">This posts the errors to the console.</span></span> <span data-ttu-id="1d1d9-112">Pour plus d’informations sur la **Trace** d’objets, consultez « Classe Trace » dans le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-112">For more information about the **Trace** object, see "Trace Class" in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Class Library.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d1d9-113">Le modèle est identique à celle de la **OrderHandler** dans lequel une interface spécifie les appels de méthode entre un client et un objet distant interprocessus.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-113">The pattern here is the same as that in the **OrderHandler** in which an interface specifies the method calls between a client and a remoted object.</span></span> <span data-ttu-id="1d1d9-114">Il existe, toutefois, une couche supplémentaire de détour entre le **OpsClient** et **OpsHandler**.</span><span class="sxs-lookup"><span data-stu-id="1d1d9-114">There is, however, an additional layer of indirection here between the **OpsClient** and the **OpsHandler**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1d9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d1d9-115">See Also</span></span>  
 [<span data-ttu-id="1d1d9-116">L’adaptateur Ops</span><span class="sxs-lookup"><span data-stu-id="1d1d9-116">The Ops Adapter</span></span>](../core/the-ops-adapter.md)