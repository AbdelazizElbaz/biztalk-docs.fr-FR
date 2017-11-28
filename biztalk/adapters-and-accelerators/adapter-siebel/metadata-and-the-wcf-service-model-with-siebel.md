---
title: "Modèle avec Siebel du Service WCF et les métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, metadata
- metadata, and the WCF service model
ms.assetid: 3aca1835-fb9e-4841-a920-078da0b3fe76
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed348c2ab183960b7af1383768259f67c4ca6270
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-siebel"></a><span data-ttu-id="4f5e4-102">Métadonnées et le modèle de Service WCF avec Siebel</span><span class="sxs-lookup"><span data-stu-id="4f5e4-102">Metadata and the WCF Service Model with Siebel</span></span>
<span data-ttu-id="4f5e4-103">Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutile.exe) pour générer une classe proxy, la classe de client WCF, via laquelle votre code peut appeler des opérations sur le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f5e4-103">In the WCF service model, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutile.exe) to generate a proxy class—the WCF client class—through which your code can invoke operations on the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
 <span data-ttu-id="4f5e4-104">Ces outils permet de générer les métadonnées exposées par l’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="4f5e4-104">These tools use the metadata exposed by the adapter to generate:</span></span>  
  
-   <span data-ttu-id="4f5e4-105">Une interface .NET annotée qui représente le contrat de service pour les opérations de la cible.</span><span class="sxs-lookup"><span data-stu-id="4f5e4-105">An annotated .NET interface that represents the service contract for target operations.</span></span> <span data-ttu-id="4f5e4-106">Cette interface est appelée le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5e4-106">This interface is called the WCF service contract.</span></span>  
  
-   <span data-ttu-id="4f5e4-107">Classes annotés qui représentent la prise en charge des contrats de message, les contrats d’opération et les contrats de données pour le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="4f5e4-107">Annotated classes that represent the supporting message contracts, operation contracts, and data contracts for the service contract.</span></span>  
  
-   <span data-ttu-id="4f5e4-108">Une classe de client WCF dont les méthodes peuvent être utilisées pour appeler les méthodes de service (opérations) exposées par le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="4f5e4-108">A WCF client class whose methods can be used to invoke the service methods (operations) exposed by the WCF service contract.</span></span>  
  
 <span data-ttu-id="4f5e4-109">Pour mieux comprendre la structure de ce généré de code, consultez « Description du Code Client généré » à [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365).</span><span class="sxs-lookup"><span data-stu-id="4f5e4-109">For help in understanding the structure of this generated code, see "Understanding Generated Client Code" at [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365).</span></span> <span data-ttu-id="4f5e4-110">Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.</span><span class="sxs-lookup"><span data-stu-id="4f5e4-110">This topic specifically describes code that svcutil.exe generates, but its content is also applicable to the code that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
 <span data-ttu-id="4f5e4-111">Pour plus d’informations sur la façon de générer une classe de client WCF pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un Client WCF ou un contrat de service WCF pour Siebel solution artefacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)</span><span class="sxs-lookup"><span data-stu-id="4f5e4-111">For information about how to generate a WCF client class for target operations and about the differences between svcutil.exe and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF Client or a WCF service contract for for Siebel solution Artifacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5e4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f5e4-112">See Also</span></span>  
 [<span data-ttu-id="4f5e4-113">Développer des applications Siebel à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="4f5e4-113">Develop Siebel applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)