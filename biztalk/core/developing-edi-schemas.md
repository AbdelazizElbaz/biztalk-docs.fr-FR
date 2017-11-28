---
title: "Développement des schémas EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a8fbf3d-ebc7-47f6-87fa-e45722651262
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b241b5d0477d7aa477511c43b642e4e312f2651a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-edi-schemas"></a><span data-ttu-id="a0fc2-102">Développement des schémas EDI</span><span class="sxs-lookup"><span data-stu-id="a0fc2-102">Developing EDI Schemas</span></span>
<span data-ttu-id="a0fc2-103">Les rubriques de cette section décrivent la modification des schémas EDI à des fins d'utilisation dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0fc2-103">The topics in this section describe how to modify EDI Schemas for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a0fc2-104">Pour utiliser un schéma de document dans votre solution, vous devez déployer celui-ci en l'ajoutant à un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis en créant et en déployant le projet.</span><span class="sxs-lookup"><span data-stu-id="a0fc2-104">To use a document schema in your solution, you need to deploy the schema by adding it to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], and then building and deploying the project.</span></span> [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="a0fc2-105"> déploie le projet dans l'Application 1 par défaut de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a0fc2-105"> will deploy the project in the default BizTalk Application 1.</span></span> <span data-ttu-id="a0fc2-106">Vous pouvez voir les schémas qui sont déployés en ouvrant le **schémas** nœud sous **BizTalk Application 1** nœud le **Applications** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration.</span><span class="sxs-lookup"><span data-stu-id="a0fc2-106">You can see the schemas that are deployed by opening the **Schemas** node under **BizTalk Application 1** node the **Applications** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="a0fc2-107">Vous pouvez déployer un assembly dans une autre application à l'aide de l'outil de ligne de commande pour le déploiement `BTSTask`.</span><span class="sxs-lookup"><span data-stu-id="a0fc2-107">You can deploy an assembly into a different application by using the command-line deployment tool `BTSTask`.</span></span>  
  
 <span data-ttu-id="a0fc2-108">Les schémas de service et de contrôle sont automatiquement déployés par l'Assistant Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0fc2-108">The service and control schemas are automatically deployed by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration wizard.</span></span> <span data-ttu-id="a0fc2-109">Pour les afficher, cliquez sur le **schémas** nœud dans le **Application EDI BizTalk** nœud dans la Console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="a0fc2-109">To see them, click the **Schemas** node in the **BizTalk EDI Application** node in the Administration Console.</span></span> <span data-ttu-id="a0fc2-110">Pour plus d’informations sur ces schémas, consultez [Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="a0fc2-110">For more information about these schemas, see [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0fc2-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a0fc2-111">In This Section</span></span>  
  
-   [<span data-ttu-id="a0fc2-112">Modification des schémas EDI</span><span class="sxs-lookup"><span data-stu-id="a0fc2-112">Modifying EDI Schemas</span></span>](../core/modifying-edi-schemas.md)  
  
-   [<span data-ttu-id="a0fc2-113">Personnalisation des énumérations dans le schéma d’enveloppe</span><span class="sxs-lookup"><span data-stu-id="a0fc2-113">Customizing Enumerations in the Envelope Schema</span></span>](../core/customizing-enumerations-in-the-envelope-schema.md)  
  
-   [<span data-ttu-id="a0fc2-114">Configuration de la Validation de champ croisé</span><span class="sxs-lookup"><span data-stu-id="a0fc2-114">Configuring Cross-Field Validation</span></span>](../core/configuring-cross-field-validation.md)  
  
## <a name="see-also"></a><span data-ttu-id="a0fc2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0fc2-115">See Also</span></span>  
 [<span data-ttu-id="a0fc2-116">Développement et la configuration des Solutions EDI BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a0fc2-116">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)