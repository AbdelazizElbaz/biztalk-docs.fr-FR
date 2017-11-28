---
title: "Métadonnées et le modèle de Service WCF avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4353ce67-f0e8-4f96-b1d9-95deeee7f3e6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c95ed3188c01f0f6d568bd745decd9e601e6ee3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-the-sql-adapter"></a><span data-ttu-id="64488-102">Métadonnées et le modèle de Service WCF avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="64488-102">Metadata and the WCF Service Model with the SQL adapter</span></span>
<span data-ttu-id="64488-103">Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutile.exe) pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="64488-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutile.exe) to do the following:</span></span>  
  
-   <span data-ttu-id="64488-104">Générer un contrat de service, le contrat de service WCF, via laquelle votre code peut recevoir des opérations à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="64488-104">Generate a service contract—the WCF service contract—through which your code can receive operations from the adapter.</span></span> <span data-ttu-id="64488-105">Cette interface .NET représente le contrat de service pour les opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="64488-105">This .NET interface represents the service contract for target operations.</span></span>  
  
-   <span data-ttu-id="64488-106">Générer des classes proxy, la classe de client WCF, via laquelle votre code peut appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="64488-106">Generate proxy classes—the WCF client class—through which your code can invoke operations on the adapter.</span></span>  
  
-   <span data-ttu-id="64488-107">Classes annotés qui représentent la prise en charge des contrats de message, les contrats d’opération et les contrats de données pour le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="64488-107">Annotated classes that represent the supporting message contracts, operation contracts, and data contracts for the service contract.</span></span>  
  
 <span data-ttu-id="64488-108">Pour mieux comprendre la structure de ce code généré, consultez [compréhension du Code Client généré](https://msdn.microsoft.com/library/ms733881.aspx).</span><span class="sxs-lookup"><span data-stu-id="64488-108">For help in understanding the structure of this generated code, see [Understanding Generated Client Code](https://msdn.microsoft.com/library/ms733881.aspx).</span></span> <span data-ttu-id="64488-109">Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="64488-109">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
 <span data-ttu-id="64488-110">Pour plus d’informations sur la façon de générer une classe de client WCF ou un contrat de service WCF pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server ](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="64488-110">For information about how to generate a WCF client class or WCF service contract for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64488-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64488-111">See Also</span></span>  
[<span data-ttu-id="64488-112">Développer des applications SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="64488-112">Develop SQL applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)