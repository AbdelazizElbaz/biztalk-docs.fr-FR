---
title: "Fonctionnalités de sécurité dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, security
- Master Secret server, security
- security, Master Secret server
- security, runtime
- security, data
- deploying, security
- security, configuring
- runtime, security
- security, security features
- security, messages
- security, access control
- security, about security
- access control
- security, deploying
- data, security
- messages, security
ms.assetid: 5ab15023-fa71-439e-b3aa-420fe28806fa
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50371f0b0c5d5a56fc9f7c392e4ee8d69e637b47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-features-in-biztalk-server"></a><span data-ttu-id="872e3-102">Fonctionnalités de sécurité sous BizTalk Server 2010</span><span class="sxs-lookup"><span data-stu-id="872e3-102">Security Features in BizTalk Server</span></span>
<span data-ttu-id="872e3-103">Microsoft® BizTalk® Server fournit une passerelle standard pour envoyer et recevoir des documents via un intranet et via Internet.</span><span class="sxs-lookup"><span data-stu-id="872e3-103">Microsoft® BizTalk® Server provides a standard gateway for sending and receiving documents both within an intranet and through the Internet.</span></span> <span data-ttu-id="872e3-104">La teneur de certains messages envoyés vers et à partir de BizTalk Server peut être stratégique pour l'entreprise. Aussi, il est important d'envisager des mesures permettant de sécuriser ces messages et les informations qu'ils contiennent lorsqu'ils sont en transit et lorsqu'ils sont traités et stockés par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="872e3-104">Due to the possible business-critical nature of the messages sent to and from BizTalk Server, it is important to consider measures to help secure these messages and the information they contain both as they are in transit and while BizTalk Server processes and stores them.</span></span> <span data-ttu-id="872e3-105">Cette section fournit des informations sur les fonctionnalités de sécurité de BizTalk Server, et comment vous pouvez les utiliser pour sécuriser vos données et votre environnement.</span><span class="sxs-lookup"><span data-stu-id="872e3-105">This section provides information about the BizTalk Server security features, and how you can use them to help secure your data and environment.</span></span>  
  
 <span data-ttu-id="872e3-106">BizTalk Server fait appel aux mesures suivantes pour permettre de sécuriser les messages entrants et sortants, le composant d'exécution et les informations de configuration ainsi que pour permettre son intégration à d'autres applications et systèmes en toute sécurité :</span><span class="sxs-lookup"><span data-stu-id="872e3-106">BizTalk Server uses the following measures to help secure inbound and outbound messages, to help secure the runtime and configuration information, and to help integrate securely with other applications and systems:</span></span>  
  
 <span data-ttu-id="872e3-107">**Sécurité des messages**</span><span class="sxs-lookup"><span data-stu-id="872e3-107">**Message security**</span></span>  
  
-   <span data-ttu-id="872e3-108">Authentification de l'expéditeur d'un message.</span><span class="sxs-lookup"><span data-stu-id="872e3-108">Authenticating the sender of a message.</span></span> <span data-ttu-id="872e3-109">BizTalk Server peut authentifier l'expéditeur d'un message (en utilisant soit les informations de certificat soit la sécurité intégrée de Windows) afin de valider l'identité de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="872e3-109">BizTalk Server can authenticate the sender of a message (either by using the certificate information or Windows integrated Security) in order to validate the identity of the sender of the message.</span></span> <span data-ttu-id="872e3-110">Pour plus d’informations, consultez [l’authentification des messages entrants](../core/inbound-message-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="872e3-110">For more information, see [Inbound Message Authentication](../core/inbound-message-authentication.md).</span></span>  
  
-   <span data-ttu-id="872e3-111">Approbation du récepteur d'un message.</span><span class="sxs-lookup"><span data-stu-id="872e3-111">Authorizing of the receiver of a message.</span></span> <span data-ttu-id="872e3-112">Après la réception d'un message par BizTalk Server, celui-ci peut déterminer les processus et les utilisateurs disposant des autorisations pour recevoir le message.</span><span class="sxs-lookup"><span data-stu-id="872e3-112">After BizTalk Server receives the message, BizTalk Server can determine what processes and users have permissions to receive the message.</span></span> <span data-ttu-id="872e3-113">Pour plus d’informations, consultez [autorisation du récepteur d’un Message](../core/authorizing-the-receiver-of-a-message.md).</span><span class="sxs-lookup"><span data-stu-id="872e3-113">For more information, see [Authorizing the Receiver of a Message](../core/authorizing-the-receiver-of-a-message.md).</span></span>  
  
 <span data-ttu-id="872e3-114">**Runtime et configuration de sécurité**</span><span class="sxs-lookup"><span data-stu-id="872e3-114">**Runtime and configuration security**</span></span>  
  
-   <span data-ttu-id="872e3-115">**Contrôle d’accès et protection des données.**</span><span class="sxs-lookup"><span data-stu-id="872e3-115">**Access control and securing data.**</span></span> <span data-ttu-id="872e3-116">BizTalk Server fait appel au contrôle d'accès pour garantir que ses processus disposent de limites appropriées et que l'accès aux informations stratégiques est contrôlé.</span><span class="sxs-lookup"><span data-stu-id="872e3-116">BizTalk Server uses access control to ensure that BizTalk Server processes have appropriate limits and that access to business critical information is controlled.</span></span> <span data-ttu-id="872e3-117">En d'autres termes, BizTalk Server vérifie que les utilisateurs et les comptes disposent des droits d'utilisateur minimaux nécessaires à l'exécution de leurs tâches.</span><span class="sxs-lookup"><span data-stu-id="872e3-117">In other words, BizTalk Server ensures that users and accounts have the least user rights possible to enable them to do their tasks.</span></span> <span data-ttu-id="872e3-118">Pour plus d’informations, consultez [contrôle d’accès et sécurité des données](../core/access-control-and-data-security.md).</span><span class="sxs-lookup"><span data-stu-id="872e3-118">For more information, see [Access Control and Data Security](../core/access-control-and-data-security.md).</span></span>  
  
 <span data-ttu-id="872e3-119">**Sécurité intégrée**</span><span class="sxs-lookup"><span data-stu-id="872e3-119">**Integrated security**</span></span>  
  
-   <span data-ttu-id="872e3-120">Authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="872e3-120">Enterprise Single Sign-On.</span></span> <span data-ttu-id="872e3-121">BizTalk Server utilise l'authentification unique de l'entreprise pour garantir qu'il chiffre les informations de configuration stratégiques nécessaires aux adaptateurs et aux emplacements d'envoi et de réception. Cela permet également de garantir que BizTalk Server stocke et transmet ces informations de manière sécurisée.</span><span class="sxs-lookup"><span data-stu-id="872e3-121">BizTalk Server uses Enterprise Single Sign-On (SSO) to ensure that it encrypts the sensitive configuration information that the adapters, send, and receive locations require, thus helping to ensure that BizTalk Server stores and transmit this information in a secure manner.</span></span> <span data-ttu-id="872e3-122">Pour plus d’informations, consultez [à l’aide de l’authentification unique](../core/using-sso.md).</span><span class="sxs-lookup"><span data-stu-id="872e3-122">For more information, see [Using SSO](../core/using-sso.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872e3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="872e3-123">See Also</span></span>  
 <span data-ttu-id="872e3-124">[Conception des Architectures système pour BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="872e3-124">[Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md) </span></span>  
 <span data-ttu-id="872e3-125">[Mise en œuvre Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md) </span><span class="sxs-lookup"><span data-stu-id="872e3-125">[Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md) </span></span>  
 <span data-ttu-id="872e3-126">[Planification de la sécurité de Message](../core/planning-message-security.md) </span><span class="sxs-lookup"><span data-stu-id="872e3-126">[Planning Message Security](../core/planning-message-security.md) </span></span>  
 [<span data-ttu-id="872e3-127">Contrôle d’accès et sécurité des données</span><span class="sxs-lookup"><span data-stu-id="872e3-127">Access Control and Data Security</span></span>](../core/access-control-and-data-security.md)   
