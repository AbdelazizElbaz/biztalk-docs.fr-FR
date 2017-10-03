---
title: "Encodage de caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transaction support
- character encoding
- encoding characters
- messages, character encoding
ms.assetid: 0a0c21c8-3318-4533-9734-89302527cb67
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19d3204cae7b82e9d18325b223e5c3b7a2d40808
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding"></a><span data-ttu-id="b9834-102">Codage des caractères</span><span class="sxs-lookup"><span data-stu-id="b9834-102">Character Encoding</span></span>
<span data-ttu-id="b9834-103">TIBCO Enterprise Message Service (EMS) prend en charge plusieurs codages de caractères dans les messages qui lui sont transmis par les adaptateurs BizTalk pour TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b9834-103">TIBCO Enterprise Message Service (EMS) supports different character encoding in the messages transmitted to EMS by BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="b9834-104">Les messages sont codés à l'aide du codage UTF-8 par défaut.</span><span class="sxs-lookup"><span data-stu-id="b9834-104">Messages are encoded using the default UTF-8 encoding.</span></span> <span data-ttu-id="b9834-105">Lorsqu'un adaptateur reçoit un message, il détermine le codage de celui-ci et convertit les chaînes appropriées au format UTF-8 avant de l'envoyer à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9834-105">When receiving messages, the adapter determines the encoding of the message and converts the appropriate strings to UTF-8 before providing the message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="b9834-106">Toutes les opérations de conversion exploitant les classes Microsoft .NET Framework; l'adaptateur prend en charge la conversion des caractères fournie par ce même cadre.</span><span class="sxs-lookup"><span data-stu-id="b9834-106">All character conversions use the Microsoft .NET Framework classes; therefore the adapter supports the character conversions provided by this same framework.</span></span>  
  
## <a name="running-in-a-clustered-environment"></a><span data-ttu-id="b9834-107">Exécution dans un environnement en clusters</span><span class="sxs-lookup"><span data-stu-id="b9834-107">Running in a Clustered Environment</span></span>  
 <span data-ttu-id="b9834-108">Les messages publiés dans les files d'attente sont utilisés par les consommateurs dans un ordre prédéterminé par le serveur EMS (un seul adaptateur reçoit le message dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en clusters).</span><span class="sxs-lookup"><span data-stu-id="b9834-108">Messages published to queues are consumed by the consumers in an order pre-determined by the EMS server—only one adapter in the clustered [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment receives the message.</span></span> <span data-ttu-id="b9834-109">La file d’attente peut être configuré en tant que *exclusif*.</span><span class="sxs-lookup"><span data-stu-id="b9834-109">The queue can be configured as *exclusive*.</span></span> <span data-ttu-id="b9834-110">Cela signifie que seul le premier adaptateur qui s'enregistre pour l'utilisation des messages dans la file d'attente reçoit les messages.</span><span class="sxs-lookup"><span data-stu-id="b9834-110">This means that only the first adapter that registers itself for message consumption on the queue receives the messages.</span></span> <span data-ttu-id="b9834-111">Le serveur EMS envoie des messages aux autres consommateurs seulement si le consommateur exclusif n'accuse pas réception des messages.</span><span class="sxs-lookup"><span data-stu-id="b9834-111">The EMS server only sends messages to the other consumers if the exclusive consumer does not acknowledge message reception.</span></span> <span data-ttu-id="b9834-112">La configuration exclusive de la file d'attente est effectuée dans la configuration EMS et n'est pas réalisable par le client.</span><span class="sxs-lookup"><span data-stu-id="b9834-112">Exclusive queue configuration is performed in the EMS configuration and is not client configurable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9834-113">Concernant les abonnements aux rubriques : étant donné que toutes les cartes dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe sont configurés de façon identique, ils sont tous les abonnés aux messages, et chaque abonnement à une rubrique reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="b9834-113">Regarding subscriptions to topics: because all adapters in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group are configured identically, they are all subscribed for the message, and each topic subscription receives the message.</span></span>  
  
## <a name="transaction-support"></a><span data-ttu-id="b9834-114">Prise en charge des transactions</span><span class="sxs-lookup"><span data-stu-id="b9834-114">Transaction Support</span></span>  
 <span data-ttu-id="b9834-115">L'adaptateur permet de prendre en charge les transactions lorsque cela est demandé par les ports d'envoi de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="b9834-115">The adapter provides support for transactions when required by the orchestration send ports.</span></span> <span data-ttu-id="b9834-116">Il n'existe aucune prise en charge des transactions avec le serveur EMS lorsque l'adaptateur écoute les messages. Toutefois, celui-ci accuse réception de tous les messages provenant d'EMS après la réussite de leur envoi à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9834-116">There is no transaction support with the EMS server when the adapter is listening for messages; however, the adapter acknowledges reception of all messages from EMS after successful message submission to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="b9834-117">EMS renvoie à l'adaptateur les messages non acquittés.</span><span class="sxs-lookup"><span data-stu-id="b9834-117">EMS resends unacknowledged messages to the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9834-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9834-118">See Also</span></span>  
 <span data-ttu-id="b9834-119">[Sécurité de l’adaptateur BizTalk pour TIBCO EMS](../core/security-in-biztalk-adapter-for-tibco-ems.md) </span><span class="sxs-lookup"><span data-stu-id="b9834-119">[Security in BizTalk Adapter for TIBCO EMS](../core/security-in-biztalk-adapter-for-tibco-ems.md) </span></span>  
 [<span data-ttu-id="b9834-120">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="b9834-120">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)