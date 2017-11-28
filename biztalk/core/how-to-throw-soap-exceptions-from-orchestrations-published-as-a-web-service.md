---
title: "Levée des Exceptions SOAP à partir d’Orchestrations publiées en tant qu’un Service Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, SOAP exceptions
- orchestrations, SOAP errors
- Web services, orchestrations
ms.assetid: e1c7cd74-d1c8-4b9d-a418-4601b1f040d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ef3d975632b6230cf1e3df299d0d9455f39da0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-throw-soap-exceptions-from-orchestrations-published-as-a-web-service"></a><span data-ttu-id="06b2f-102">Levée des Exceptions SOAP à partir d’Orchestrations publiées en tant qu’un Service Web</span><span class="sxs-lookup"><span data-stu-id="06b2f-102">How to Throw SOAP Exceptions from Orchestrations Published as a Web Service</span></span>
<span data-ttu-id="06b2f-103">Vous pouvez renvoyer une exception SOAP à partir d'une orchestration publiée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="06b2f-103">You can return a SOAP exception from an orchestration that you have published as a Web service.</span></span> <span data-ttu-id="06b2f-104">Vous ajoutez un message d'erreur à votre port SOAP et l'envoyez à la place de la réponse.</span><span class="sxs-lookup"><span data-stu-id="06b2f-104">You add a fault message to your SOAP port and send the fault message instead of the response.</span></span>  
  
### <a name="to-throw-a-soap-exception-from-an-orchestration-published-as-a-web-service"></a><span data-ttu-id="06b2f-105">Pour lever une exception SOAP à partir d'une orchestration publiée en tant que service Web</span><span class="sxs-lookup"><span data-stu-id="06b2f-105">To throw a SOAP exception from an orchestration published as a Web service</span></span>  
  
1.  <span data-ttu-id="06b2f-106">Ajoutez un message d'erreur au type de port SOAP.</span><span class="sxs-lookup"><span data-stu-id="06b2f-106">Add a fault message to the SOAP port type.</span></span> <span data-ttu-id="06b2f-107">Le type du message d'erreur peut être tout type simple ou de schéma compatible XDS (XML Schema).</span><span class="sxs-lookup"><span data-stu-id="06b2f-107">The message type for the fault message can be any XML Schema (XSD) compliant schema or simple type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06b2f-108">Pour retourner une chaîne comme un **SoapException** avec les informations d’erreur, vous pouvez utiliser la chaîne de type simple en tant que le type de message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="06b2f-108">To return a string as a **SoapException** with error information, you can use the simple type string as the fault message type.</span></span>  
  
2.  <span data-ttu-id="06b2f-109">Dans votre orchestration, créez le message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="06b2f-109">In your orchestration, create the fault message.</span></span>  
  
3.  <span data-ttu-id="06b2f-110">Utilisez le **envoyer** forme à lier à l’opération d’erreur dans le port SOAP qui correspond au message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="06b2f-110">Use the **Send** shape to link to the fault operation in the SOAP port that corresponds to the fault message.</span></span> <span data-ttu-id="06b2f-111">Une exception SOAP enveloppe le message d'erreur renvoyé.</span><span class="sxs-lookup"><span data-stu-id="06b2f-111">A SOAP exception wraps the returned fault message.</span></span>  
  
 <span data-ttu-id="06b2f-112">Si votre orchestration ne retourne pas d’erreur, utilisez une autre **envoyer** forme pour envoyer le message de réponse SOAP standard à l’aide de l’opération de réponse habituel.</span><span class="sxs-lookup"><span data-stu-id="06b2f-112">If your orchestration does not return an error, use a different **Send** shape to send the standard SOAP response message using the usual response operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b2f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06b2f-113">See Also</span></span>  
 <span data-ttu-id="06b2f-114">[Messages d’erreur](../core/fault-messages.md) </span><span class="sxs-lookup"><span data-stu-id="06b2f-114">[Fault Messages](../core/fault-messages.md) </span></span>  
 [<span data-ttu-id="06b2f-115">Publication d’une Orchestration en tant que Service Web</span><span class="sxs-lookup"><span data-stu-id="06b2f-115">Publishing an Orchestration as a Web Service</span></span>](../core/publishing-an-orchestration-as-a-web-service.md)