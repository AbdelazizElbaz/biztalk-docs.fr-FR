---
title: "À l’aide de BizTalk Server à partir de TIBCO Rendezvous pour envoyer des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, sending
- sending messages
- BizTalk Server, using from TIBCO Rendezvous
ms.assetid: 72057d42-32b5-4748-81e4-5ffb89630f5a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4556ce5ca90b3c62f779d2df55e78c4506458d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-send-messages"></a><span data-ttu-id="8ed9b-102">Utilisation de BizTalk Server à partir de TIBCO Rendezvous pour envoyer des messages</span><span class="sxs-lookup"><span data-stu-id="8ed9b-102">Using BizTalk Server from TIBCO Rendezvous to Send Messages</span></span>
<span data-ttu-id="8ed9b-103">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise l'API asynchrone (Transport.Send).</span><span class="sxs-lookup"><span data-stu-id="8ed9b-103">Microsoft BizTalk Adapter for TIBCO Rendezvous uses the asynchronous API (Transport.Send).</span></span> <span data-ttu-id="8ed9b-104">Vous pouvez spécifier le type de message envoyé par l'adaptateur à l'aide d'une propriété de contexte de message :</span><span class="sxs-lookup"><span data-stu-id="8ed9b-104">You can specify what kind of message the adapter sends using a message context property:</span></span>  
  
-   <span data-ttu-id="8ed9b-105">**Structuré**: l’adaptateur génère un message structuré TIBRVMSG_MSG, basé sur les données XML reçues de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-105">**Structured**: The adapter generates a TIBRVMSG_MSG structured message, based on the XML data received from BizTalk Server.</span></span> <span data-ttu-id="8ed9b-106">(*)</span><span class="sxs-lookup"><span data-stu-id="8ed9b-106">(*)</span></span>  
  
 <span data-ttu-id="8ed9b-107">Si BizTalk Server envoie un message avec des champs dont le nom comporte plus de 127 caractères, l'adaptateur BizTalk pour TIBCO Rendezvous tronque les noms en fonction de la taille de nom de champ maximale pour TIBCO Rendezvous (127).</span><span class="sxs-lookup"><span data-stu-id="8ed9b-107">If BizTalk Server sends a message with fields that have names longer than 127 characters, BizTalk Adapter for TIBCO Rendezvous truncates the names to the maximum field name size for TIBCO Rendezvous, which is 127.</span></span>  
  
 <span data-ttu-id="8ed9b-108">Si une propriété `reply subject name` est fournie, elle est utilisée pour définir l'objet de réponse sur le message TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-108">If a `reply subject name` property is provided, it is used to set the reply subject on the TIBCO Rendezvous message.</span></span> <span data-ttu-id="8ed9b-109">Il est supposé qu'un port de réception est défini pour écouter la réponse et la transmettre à BizTalk Server, ou qu'un autre programme TIBCO Rendezvous traite la réponse.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-109">It is assumed that either a receive port is set to listen for the reply and forward it to BizTalk Server, or some other TIBCO Rendezvous program is taking care of the reply.</span></span>  
  
 <span data-ttu-id="8ed9b-110">Le triplet (service, démon, réseau) constitue la configuration de transport.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-110">The triplet (service, daemon, network) makes up the transport configuration.</span></span> <span data-ttu-id="8ed9b-111">Une configuration de transport vide (par défaut) entraîne l'envoi d'un message via l'objet de transport par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-111">An empty (default) transport configuration results in a message being sent through the default transport object.</span></span>  
  
 <span data-ttu-id="8ed9b-112">Si la page de code n'est pas spécifiée, l'adaptateur utilise le codage UTF-8 (page de code 65001).</span><span class="sxs-lookup"><span data-stu-id="8ed9b-112">If the code page is left unspecified, the adapter uses UTF-8 encoding (code page 65001).</span></span> <span data-ttu-id="8ed9b-113">Les messages certifiés ne sont pas pris en charge du côté transmetteur.</span><span class="sxs-lookup"><span data-stu-id="8ed9b-113">Certified Messages are not supported on the transmitter side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed9b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ed9b-114">See Also</span></span>  
 <span data-ttu-id="8ed9b-115">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="8ed9b-115">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="8ed9b-116">Création gestionnaires d’envoi TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="8ed9b-116">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)