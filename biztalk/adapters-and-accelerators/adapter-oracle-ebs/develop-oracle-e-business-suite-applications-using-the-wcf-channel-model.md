---
title: "Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75bb6de1-e11a-4377-af13-e1cb954aaf3f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e99dfa0c69500b86fe086ce0daa81e3ffb62857d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-e-business-suite-applications-using-the-wcf-channel-model"></a><span data-ttu-id="89835-102">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="89835-102">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>
<span data-ttu-id="89835-103">Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de Oracle eBusiness Suite.</span><span class="sxs-lookup"><span data-stu-id="89835-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] by sending XML messages directly over a channel instance created with the Oracle EBS Binding.</span></span>  
  
 <span data-ttu-id="89835-104">L’un des avantages de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes qui l’expose de modèle de service WCF est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="89835-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the Oracle E-Business Suite.</span></span> <span data-ttu-id="89835-105">Ce contrôle vient du fait que dans le modèle de canal WCF, vous contrôlez directement le contenu des messages que vous envoyez sur le canal.</span><span class="sxs-lookup"><span data-stu-id="89835-105">This control comes from the fact that in the WCF channel model, you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="89835-106">Dans certains scénarios, ce niveau supplémentaire de contrôle peut être utile.</span><span class="sxs-lookup"><span data-stu-id="89835-106">In certain scenarios, this extra level of control can be beneficial.</span></span> <span data-ttu-id="89835-107">Par exemple, lorsque vous utilisez le modèle de canal WCF pour effectuer une opération de mise à jour sur une table, vous pouvez sélectivement mettre à jour colonnes dans les lignes de la cible en omettant les colonnes à partir du modèle de mise à jour que vous passez dans le message.</span><span class="sxs-lookup"><span data-stu-id="89835-107">For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message.</span></span> <span data-ttu-id="89835-108">Seules les colonnes qui sont nécessaires sont celles avec « nillable = false » dans le WSDL.</span><span class="sxs-lookup"><span data-stu-id="89835-108">The only columns that are required are those with “nillable=false” in the WSDL.</span></span> <span data-ttu-id="89835-109">La méthode de mise à jour exposée par un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client utilise un paramètre d’enregistrement de fortement typé pour le modèle qui inclut toutes les colonnes dans le schéma de table.</span><span class="sxs-lookup"><span data-stu-id="89835-109">The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema.</span></span>  
  
 <span data-ttu-id="89835-110">Les rubriques de cette section expliquent comment effectuer des opérations sur les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] en utilisant le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="89835-110">The topics in this section explain how to perform operations on the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89835-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="89835-111">In This Section</span></span>  
  
-   [<span data-ttu-id="89835-112">Vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="89835-112">Overview of the WCF channel model with the Oracle E-Business Suite adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [<span data-ttu-id="89835-113">Créer un canal à l’aide d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="89835-113">Create a channel using Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-channel-using-oracle-e-business-suite.md)
  
-   [<span data-ttu-id="89835-114">Exécuter une opération d’insertion sur une table d’interface dans Oracle E-Business Suite à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="89835-114">Run an insert operation on an interface table in Oracle E-Business Suite using the WCF channel model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/insert-on-an-interface-table-in-oracle-ebs-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="89835-115">Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="89835-115">Poll Oracle E-Business Suite using SELECT statement with the WCF channel model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model.md)
  
## <a name="see-also"></a><span data-ttu-id="89835-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89835-116">See Also</span></span>  
[<span data-ttu-id="89835-117">Développer vos applications Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="89835-117">Develop your Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)