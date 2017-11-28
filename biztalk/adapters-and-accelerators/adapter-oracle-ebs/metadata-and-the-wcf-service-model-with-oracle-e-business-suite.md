---
title: "WCF et les métadonnées de modèle avec Oracle E-Business Suite Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d3fcba-c72f-4ae9-82bd-abbfc2a0c2c4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cf87c0a579d1f0c0de590d78e559ead73be0cec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-oracle-e-business-suite"></a><span data-ttu-id="b4c08-102">Métadonnées et le modèle de Service WCF avec Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="b4c08-102">Metadata and the WCF Service Model with Oracle E-Business Suite</span></span>
<span data-ttu-id="b4c08-103">Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutile.exe) pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4c08-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutile.exe) to do the following:</span></span>  
  
-   <span data-ttu-id="b4c08-104">Générer un contrat de service, le contrat de service WCF, via laquelle votre code peut recevoir des opérations à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="b4c08-104">Generate a service contract—the WCF service contract—through which your code can receive operations from the adapter.</span></span> <span data-ttu-id="b4c08-105">Cette interface .NET représente le contrat de service pour les opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="b4c08-105">This .NET interface represents the service contract for target operations.</span></span>  
  
-   <span data-ttu-id="b4c08-106">Générer des classes proxy, la classe de client WCF, via laquelle votre code peut appeler des opérations sur la carte.</span><span class="sxs-lookup"><span data-stu-id="b4c08-106">Generate proxy classes—the WCF client class—through which your code can invoke operations on the adapter.</span></span>  
  
-   <span data-ttu-id="b4c08-107">Classes annotés qui représentent la prise en charge des contrats de message, les contrats d’opération et les contrats de données pour le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="b4c08-107">Annotated classes that represent the supporting message contracts, operation contracts, and data contracts for the service contract.</span></span>  
  
 <span data-ttu-id="b4c08-108">Pour mieux comprendre la structure de ce généré de code, consultez « Description du Code Client généré » à [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365).</span><span class="sxs-lookup"><span data-stu-id="b4c08-108">For help in understanding the structure of this generated code, see "Understanding Generated Client Code" at [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365).</span></span> <span data-ttu-id="b4c08-109">Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="b4c08-109">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
 <span data-ttu-id="b4c08-110">Pour plus d’informations sur la façon de générer une classe de client WCF ou un contrat de service WCF pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un Client WCF ou un contrat de Service WCF pour Oracle E-Business. Artefacts de Solution suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="b4c08-110">For information about how to generate a WCF client class or WCF service contract for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF Client or a WCF Service Contract for Oracle E-Business Suite Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c08-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4c08-111">See Also</span></span>  
 [<span data-ttu-id="b4c08-112">Développer des Applications d’Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="b4c08-112">Develop Oracle E-Business Suite Applications by Using the WCF service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)