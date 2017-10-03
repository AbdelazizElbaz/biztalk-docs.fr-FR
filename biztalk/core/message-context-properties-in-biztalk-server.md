---
title: "Dans BizTalk Server, les propriétés de contexte de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message context properties, accessing
- message context properties, BizTalk Server
ms.assetid: 163ac2cf-0e2d-4780-b398-baa825f92b00
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75e92e458ec6927ab8e1bc6082cd9a71ee3e4387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-context-properties-in-biztalk-server"></a><span data-ttu-id="99699-102">Propriétés de contexte du message dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="99699-102">Message Context Properties in BizTalk Server</span></span>
<span data-ttu-id="99699-103">Pour accéder aux champs de descripteur de message TIBCO Enterprise Message System à partir d’une orchestration BizTalk Server, vous devez ajouter une référence à **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** à votre projet.</span><span class="sxs-lookup"><span data-stu-id="99699-103">To access TIBCO Enterprise Message System message descriptor fields from a BizTalk Server orchestration, you must add a reference to **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** to your project.</span></span> <span data-ttu-id="99699-104">Cet assembly se trouve dans  **\<TIBCO EMS_Adapter_installation_directory > \bin**.</span><span class="sxs-lookup"><span data-stu-id="99699-104">This assembly is located in **\<TIBCO EMS_Adapter_installation_directory>\bin**.</span></span> <span data-ttu-id="99699-105">Après avoir référencé ce schéma de propriété TIBCO EMS, vous pouvez accéder à des propriétés de contexte supplémentaires à l'aide de différents outils de développement BizTalk Server (par exemple, la forme Assignation de message dans le Concepteur d'orchestration).</span><span class="sxs-lookup"><span data-stu-id="99699-105">After you reference this TIBCO EMS property schema, additional context properties can be accessed by various BizTalk Server development tools (for example, the message assignment shape in the orchestration designer).</span></span>  
  
## <a name="accessing-context-properties"></a><span data-ttu-id="99699-106">Accès aux propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="99699-106">Accessing Context Properties</span></span>  
 <span data-ttu-id="99699-107">Pour accéder à une propriété de contexte, spécifiez une des propriétés de contexte disponibles dans l'espace de noms TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="99699-107">To access a context property, you specify one of the available context properties in the TIBCO EMS namespace.</span></span> <span data-ttu-id="99699-108">Pour lire la propriété de contexte d'un message reçu à partir d'un port lié à l'adaptateur BizTalk pour TIBCO EMS, utilisez la syntaxe suivante dans une expression :</span><span class="sxs-lookup"><span data-stu-id="99699-108">To read the context property of a message received from a port bound to BizTalk Adapter for TIBCO EMS, use the following syntax in an expression:</span></span>  
  
```  
Message(TibcoEMS.Property)  
```  
  
 <span data-ttu-id="99699-109">Pour plus d’informations, consultez [propriétés de descripteur de Message TIBCO Enterprise Message Service](../core/tibco-enterprise-message-service-message-descriptor-properties.md).</span><span class="sxs-lookup"><span data-stu-id="99699-109">For more information, see [TIBCO Enterprise Message Service Message Descriptor Properties](../core/tibco-enterprise-message-service-message-descriptor-properties.md).</span></span>  
  
 <span data-ttu-id="99699-110">Dans BizTalk Server, les messages sont immuables.</span><span class="sxs-lookup"><span data-stu-id="99699-110">In BizTalk Server, messages are immutable.</span></span> <span data-ttu-id="99699-111">C'est pourquoi, pour affecter une valeur de propriété de contexte à un message, créez un message, définissez son contenu (par exemple, en lui affectant un message existant) puis les propriétés dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="99699-111">Therefore, to assign a message context property value, you create a new message, set the message content (possibly by assigning an existing message), and then set the properties that you need.</span></span>  
  
 <span data-ttu-id="99699-112">Pour affecter des propriétés de contexte TIBCO EMS à un message destiné à un port d'envoi lié à l'adaptateur BizTalk pour TIBCO EMS, utilisez l'opérateur d'affectation du message et spécifiez l'une des propriétés de contexte disponibles dans l'espace de noms TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="99699-112">To assign TIBCO EMS context properties to a message destined to a send port that is bound to BizTalk Adapter for TIBCO EMS, use the message assignment operator and specify one of the available context properties in the TIBCO EMS namespace.</span></span> <span data-ttu-id="99699-113">La syntaxe de base est la suivante :</span><span class="sxs-lookup"><span data-stu-id="99699-113">The syntax is as follows:</span></span>  
  
```  
Message(TibcoEMS.Property) = value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="99699-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99699-114">See Also</span></span>  
 [<span data-ttu-id="99699-115">Propriétés de contexte de message</span><span class="sxs-lookup"><span data-stu-id="99699-115">Message Context Properties</span></span>](../core/message-context-properties2.md)