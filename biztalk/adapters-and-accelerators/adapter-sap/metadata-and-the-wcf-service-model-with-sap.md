---
title: "Modèle avec SAP du Service WCF et les métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1900cf66-a0d0-46f4-896b-7f6de3b51875
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f06cd33c0776df70e5ff2554d355915908012abb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-sap"></a><span data-ttu-id="c44d6-102">Métadonnées et le modèle de Service WCF avec SAP</span><span class="sxs-lookup"><span data-stu-id="c44d6-102">Metadata and the WCF Service Model with SAP</span></span>
<span data-ttu-id="c44d6-103">Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]ou le ServiceModel Metadata Utility Tool (svcutile.exe) pour générer des classes proxy via lequel votre code peut :</span><span class="sxs-lookup"><span data-stu-id="c44d6-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].or the ServiceModel Metadata Utility Tool (svcutile.exe) to generate proxy classes through which your code can either:</span></span>  
  
-   <span data-ttu-id="c44d6-104">Appeler des opérations sur la carte (une classe de client WCF)</span><span class="sxs-lookup"><span data-stu-id="c44d6-104">Invoke operations on the adapter (a WCF client class)</span></span>  
  
-   <span data-ttu-id="c44d6-105">Opérations de réception de l’adaptateur (un contrat de service WCF)</span><span class="sxs-lookup"><span data-stu-id="c44d6-105">Receive operations from the adapter (a WCF service contract)</span></span>  
  
 <span data-ttu-id="c44d6-106">Ces outils génèrent des classes .NET qui représentent un contrat de service pour les opérations de la cible (ainsi que la prise en charge des contrats de message, contrats d’opération et des contrats de données) à partir des métadonnées exposées par le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c44d6-106">These tools generate .NET classes that represent a service contract for target operations (as well as the supporting message contracts, operation contracts, and data contracts) from the metadata exposed by the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span> <span data-ttu-id="c44d6-107">Pour mieux comprendre la structure de ce code généré, consultez [compréhension du Code Client généré](https://msdn.microsoft.com/library/ms733881.aspx).</span><span class="sxs-lookup"><span data-stu-id="c44d6-107">For help in understanding the structure of this generated code, see [Understanding Generated Client Code](https://msdn.microsoft.com/library/ms733881.aspx).</span></span> <span data-ttu-id="c44d6-108">Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="c44d6-108">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span> <span data-ttu-id="c44d6-109">Pour plus d’informations sur la façon de générer une classe de client WCF ou un contrat de service WCF (interface) pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un client WCF ou un contrat de service WCF pour SAP artefacts de solution](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="c44d6-109">For information about how to generate a WCF client class or WCF service contract (interface) for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44d6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c44d6-110">See Also</span></span>  
[<span data-ttu-id="c44d6-111">Développer des applications SAP à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="c44d6-111">Develop SAP applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)