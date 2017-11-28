---
title: "Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf3374a2-2fca-4df4-a1b1-d11cdc05d393
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d201987490d9395b07d043c67fa50a31400fe7cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="254b3-102">Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="254b3-102">Develop BizTalk applications using the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="254b3-103">Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]et à l’aide de la  **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]**  ou  **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]**  pour générer le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="254b3-103">Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and using the **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]** or **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]** to generate XML schema.</span></span> <span data-ttu-id="254b3-104">Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.</span><span class="sxs-lookup"><span data-stu-id="254b3-104">Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to your generated schema.</span></span>  
  
 <span data-ttu-id="254b3-105">CBR peut être utilisé dans les scénarios où les messages envoyés à Oracle E-Business Suite nécessitent un traitement intensif.</span><span class="sxs-lookup"><span data-stu-id="254b3-105">CBR can be used in scenarios where the messages being sent to Oracle E-Business Suite do not require any intensive processing.</span></span> <span data-ttu-id="254b3-106">Par exemple, si vous savez que les messages de réception de port de réception uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour router les messages qui correspondent à l’expression de filtre pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="254b3-106">For example, if you know that the receive port receive messages only of a certain type, you can add a filter to the send port to route messages that match the filter expression to the send port.</span></span>  

## <a name="use-orchestration"></a><span data-ttu-id="254b3-107">Utiliser l’orchestration</span><span class="sxs-lookup"><span data-stu-id="254b3-107">Use orchestration</span></span>  
 <span data-ttu-id="254b3-108">Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="254b3-108">In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> 
 
 <span data-ttu-id="254b3-109">Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer les tâches et les opérations sur Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort_md](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="254b3-109">This section provides information about using BizTalk orchestrations to perform tasks and operations on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort_md](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="254b3-110">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], ce qui peut interagir avec une liaison WCF.</span><span class="sxs-lookup"><span data-stu-id="254b3-110">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which can interact with a WCF binding.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="254b3-111">Pour utiliser le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la **EnableBizTalkCompatibilityMode** liaison de propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="254b3-111">To use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the **EnableBizTalkCompatibilityMode** binding property to **True**.</span></span> <span data-ttu-id="254b3-112">Pour connaître les étapes, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="254b3-112">For the steps, see [Configure the binding properties for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="254b3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="254b3-113">See Also</span></span>  
[<span data-ttu-id="254b3-114">Développer vos applications Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="254b3-114">Develop your Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)