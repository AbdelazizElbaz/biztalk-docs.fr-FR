---
title: "Implémentation de la sécurité de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 971977a0-b74e-4408-8a07-ad327658f2bc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84c0430b0a8edd0c241706047886f395515c853f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-message-security"></a><span data-ttu-id="2f321-102">Implémentation de la sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="2f321-102">Implementing Message Security</span></span>
<span data-ttu-id="2f321-103">Vous pouvez configurer votre environnement Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour qu'il utilise des certificats permettant de recevoir et d'envoyer des messages signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="2f321-103">You can configure your Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment to use certificates for sending and receiving signed and encrypted messages.</span></span> <span data-ttu-id="2f321-104">L'utilisation de certificats pour le chiffrement et les signatures numériques permet à BizTalk Server d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f321-104">By using certificates for encryption and digital signatures, BizTalk Server can:</span></span>  
  
-   <span data-ttu-id="2f321-105">Envoyer et recevoir des données fiables.</span><span class="sxs-lookup"><span data-stu-id="2f321-105">Send and receive data that can be trusted.</span></span>  
  
-   <span data-ttu-id="2f321-106">S'assurer que les données traitées sont sécurisées.</span><span class="sxs-lookup"><span data-stu-id="2f321-106">Make sure that the data it processes is secure.</span></span>  
  
-   <span data-ttu-id="2f321-107">S'assurer que les tiers autorisés reçoivent ses messages.</span><span class="sxs-lookup"><span data-stu-id="2f321-107">Make sure that authorized parties receive its messages.</span></span>  
  
-   <span data-ttu-id="2f321-108">S'assurer qu'il reçoit les messages envoyés par les tiers autorisés.</span><span class="sxs-lookup"><span data-stu-id="2f321-108">Make sure that it receives messages from authorized parties.</span></span>  
  
 <span data-ttu-id="2f321-109">Cette section fournit des informations sur la configuration des pipelines BizTalk Server, des emplacements de réception, des ports et de l'environnement BizTalk Server afin d'implémenter la sécurité des messages.</span><span class="sxs-lookup"><span data-stu-id="2f321-109">This section provides information about how to configure BizTalk Server pipelines, receive locations, ports, and the BizTalk Server environment to implement message security.</span></span>  
  
 <span data-ttu-id="2f321-110">Pour plus d’informations sur la sécurité de message, consultez [planification de la sécurité de Message](../core/planning-message-security.md).</span><span class="sxs-lookup"><span data-stu-id="2f321-110">For more information about message security, see [Planning Message Security](../core/planning-message-security.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f321-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2f321-111">In This Section</span></span>  
  
-   [<span data-ttu-id="2f321-112">Envoyer et recevoir des Messages chiffrés</span><span class="sxs-lookup"><span data-stu-id="2f321-112">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)  
  
-   [<span data-ttu-id="2f321-113">Envoyer et recevoir des Messages signés</span><span class="sxs-lookup"><span data-stu-id="2f321-113">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)  
  
-   [<span data-ttu-id="2f321-114">L’utilisation de certificats pour la résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="2f321-114">Using Certificates for Party Resolution</span></span>](../core/using-certificates-for-party-resolution.md)