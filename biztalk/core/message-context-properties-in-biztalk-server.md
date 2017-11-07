---
title: "Utilisez les propriétés de contexte de message TIBCO EMS | Documents Microsoft"
description: Utilisez les champs de descripteur de message TIBCO Enterprise Message System dans une orchestration BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 163ac2cf-0e2d-4780-b398-baa825f92b00
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef4f0d8c606724cec9c85551251cb003aa8a7e34
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="message-context-properties-in-tibco-ems"></a><span data-ttu-id="6ea8c-103">Propriétés de contexte de message TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="6ea8c-103">Message Context Properties in TIBCO EMS</span></span>

## <a name="tibcoemspropertiesdll"></a><span data-ttu-id="6ea8c-104">TibcoEMSProperties.dll</span><span class="sxs-lookup"><span data-stu-id="6ea8c-104">TibcoEMSProperties.dll</span></span>
<span data-ttu-id="6ea8c-105">Pour accéder aux champs de descripteur de message TIBCO Enterprise Message System à partir d’une orchestration BizTalk Server, vous devez ajouter une référence à **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** à votre projet.</span><span class="sxs-lookup"><span data-stu-id="6ea8c-105">To access TIBCO Enterprise Message System message descriptor fields from a BizTalk Server orchestration, you must add a reference to **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** to your project.</span></span> <span data-ttu-id="6ea8c-106">Cet assembly se trouve dans  **\<TIBCO EMS_Adapter_installation_directory > \bin**.</span><span class="sxs-lookup"><span data-stu-id="6ea8c-106">This assembly is located in **\<TIBCO EMS_Adapter_installation_directory>\bin**.</span></span> <span data-ttu-id="6ea8c-107">Après avoir référencé ce schéma de propriété TIBCO EMS, vous pouvez accéder à des propriétés de contexte supplémentaires à l'aide de différents outils de développement BizTalk Server (par exemple, la forme Assignation de message dans le Concepteur d'orchestration).</span><span class="sxs-lookup"><span data-stu-id="6ea8c-107">After you reference this TIBCO EMS property schema, additional context properties can be accessed by various BizTalk Server development tools (for example, the message assignment shape in the orchestration designer).</span></span>  
  
## <a name="access-context-properties"></a><span data-ttu-id="6ea8c-108">Accéder aux propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="6ea8c-108">Access context Properties</span></span>  
 <span data-ttu-id="6ea8c-109">Pour accéder à une propriété de contexte, spécifiez une des propriétés de contexte disponibles dans l'espace de noms TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="6ea8c-109">To access a context property, you specify one of the available context properties in the TIBCO EMS namespace.</span></span> <span data-ttu-id="6ea8c-110">Pour lire la propriété de contexte d'un message reçu à partir d'un port lié à l'adaptateur BizTalk pour TIBCO EMS, utilisez la syntaxe suivante dans une expression :</span><span class="sxs-lookup"><span data-stu-id="6ea8c-110">To read the context property of a message received from a port bound to BizTalk Adapter for TIBCO EMS, use the following syntax in an expression:</span></span>  
  
```  
Message(TibcoEMS.Property)  
```  
  
 <span data-ttu-id="6ea8c-111">Pour plus d’informations, consultez [propriétés de descripteur de Message TIBCO Enterprise Message Service](../core/tibco-enterprise-message-service-message-descriptor-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6ea8c-111">For more information, see [TIBCO Enterprise Message Service Message Descriptor Properties](../core/tibco-enterprise-message-service-message-descriptor-properties.md).</span></span>  
  
 <span data-ttu-id="6ea8c-112">Dans BizTalk Server, les messages sont immuables.</span><span class="sxs-lookup"><span data-stu-id="6ea8c-112">In BizTalk Server, messages are immutable.</span></span> <span data-ttu-id="6ea8c-113">C'est pourquoi, pour affecter une valeur de propriété de contexte à un message, créez un message, définissez son contenu (par exemple, en lui affectant un message existant) puis les propriétés dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="6ea8c-113">Therefore, to assign a message context property value, you create a new message, set the message content (possibly by assigning an existing message), and then set the properties that you need.</span></span>  
  
 <span data-ttu-id="6ea8c-114">Pour affecter des propriétés de contexte TIBCO EMS à un message destiné à un port d'envoi lié à l'adaptateur BizTalk pour TIBCO EMS, utilisez l'opérateur d'affectation du message et spécifiez l'une des propriétés de contexte disponibles dans l'espace de noms TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="6ea8c-114">To assign TIBCO EMS context properties to a message destined to a send port that is bound to BizTalk Adapter for TIBCO EMS, use the message assignment operator and specify one of the available context properties in the TIBCO EMS namespace.</span></span> <span data-ttu-id="6ea8c-115">La syntaxe de base est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6ea8c-115">The syntax is as follows:</span></span>  
  
```  
Message(TibcoEMS.Property) = value;  
```  
  
## <a name="next-steps"></a><span data-ttu-id="6ea8c-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6ea8c-116">Next steps</span></span>
-   [<span data-ttu-id="6ea8c-117">Les valeurs et les propriétés du descripteur de Message TIBCO EMS</span><span class="sxs-lookup"><span data-stu-id="6ea8c-117">TIBCO EMS Message Descriptor properties & values</span></span>](../core/tibco-enterprise-message-service-message-descriptor-properties.md)  
  
-   [<span data-ttu-id="6ea8c-118">Didacticiel : Utiliser les propriétés du contexte de message</span><span class="sxs-lookup"><span data-stu-id="6ea8c-118">Tutorial: Use Message Context Properties</span></span>](../core/tutorial-using-message-context-properties.md)