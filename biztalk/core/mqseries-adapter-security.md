---
title: "Sécurité de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, MQSeries adapters
- MQSeries adapters, security
ms.assetid: 0bd82c21-6b77-4a66-a4e9-4a91ba4a56c4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08d5228dab8463c2ad5dc7f9d9347899d4c41a67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-with-the-mqseries-adapter"></a><span data-ttu-id="dd643-102">Sécurité avec l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="dd643-102">Security with the MQSeries adapter</span></span>

<span data-ttu-id="dd643-103">La fonctionnalité de sécurité de l'adaptateur MQSeries commence par sécuriser vos serveurs BizTalk et MQSeries.</span><span class="sxs-lookup"><span data-stu-id="dd643-103">MQSeries adapter security begins with securing your BizTalk and MQSeries servers.</span></span> <span data-ttu-id="dd643-104">Pour plus d’informations sur la sécurisation de BizTalk Server, consultez [sécurisé et protégez vos données](secure-and-protect-your-biztalk-messages.md).</span><span class="sxs-lookup"><span data-stu-id="dd643-104">For information about securing BizTalk Server, see [Secure and protect your data](secure-and-protect-your-biztalk-messages.md).</span></span> <span data-ttu-id="dd643-105">Pour plus d'informations sur la sécurité du serveur MQSeries, consultez la documentation IBM associée.</span><span class="sxs-lookup"><span data-stu-id="dd643-105">For information about MQSeries Server security, see the IBM MQSeries Server documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd643-106">L'adaptateur utilise automatiquement la confidentialité du paquet pour l'envoi et la réception des messages entre le serveur BizTalk et le serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="dd643-106">The adapter automatically uses packet privacy for sending and receiving messages between BizTalk Server and MQSeries Server.</span></span>  

## <a name="adapter-security"></a><span data-ttu-id="dd643-107">Sécurité de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="dd643-107">Adapter security</span></span>  
 <span data-ttu-id="dd643-108">L'utilisation sécurisée de l'adaptateur requiert votre attention sur quatre points importants :</span><span class="sxs-lookup"><span data-stu-id="dd643-108">Using the adapter itself securely requires attention to four areas:</span></span>  
  
-   <span data-ttu-id="dd643-109">la sélection de l'identité et des membres de l'application pour MQSAgent ;</span><span class="sxs-lookup"><span data-stu-id="dd643-109">Choosing the application identity and members for MQSAgent</span></span>  
  
-   <span data-ttu-id="dd643-110">le contrôle des comptes BizTalk Server à l'aide de l'adaptateur ;</span><span class="sxs-lookup"><span data-stu-id="dd643-110">Controlling the BizTalk Server accounts using the adapter</span></span>  
  
-   <span data-ttu-id="dd643-111">la sécurisation des scripts de création de la file d'attente ;</span><span class="sxs-lookup"><span data-stu-id="dd643-111">Securing the queue creation scripts</span></span>  
  
-   <span data-ttu-id="dd643-112">Utilisation appropriée de la **Application associée SSO** propriété</span><span class="sxs-lookup"><span data-stu-id="dd643-112">Making appropriate use of the **SSO Affiliate Application** property</span></span>  
  
 <span data-ttu-id="dd643-113">Le compte affecté à l'identité de l'application lors de la configuration ne doit pas être un compte d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="dd643-113">The account assigned to the application identity during configuration should not be an administrator account.</span></span> <span data-ttu-id="dd643-114">Il ne doit bénéficier que des privilèges requis minimaux, à savoir l'accès en lecture/écriture aux files d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="dd643-114">Rather, the account should have the minimum required privileges—read and write access to the MQSeries queues.</span></span>  
  
 <span data-ttu-id="dd643-115">Vérifiez que vous affectez uniquement des comptes BizTalk Server à l'aide de l'adaptateur au rôle MQSAgent.</span><span class="sxs-lookup"><span data-stu-id="dd643-115">Make sure that you assign only BizTalk Server accounts using the adapter to the MQSAgent role.</span></span>  
  
 <span data-ttu-id="dd643-116">Lors de l'utilisation de scripts exportés créés lors du processus de définition de la file d'attente, conservez ceux-ci dans une zone sécurisée.</span><span class="sxs-lookup"><span data-stu-id="dd643-116">When using exported scripts created during the queue definition process, keep the scripts in a secure area.</span></span> <span data-ttu-id="dd643-117">Seuls les administrateurs utilisant les scripts doivent y avoir accès.</span><span class="sxs-lookup"><span data-stu-id="dd643-117">Only administrators using the scripts should have access.</span></span>  
  
 <span data-ttu-id="dd643-118">Si votre application utilise les propriétés d’en-tête MQCIH et MQIIH pour placer les informations d’identification de l’utilisateur dans les messages sortants, utilisez le **Application associée SSO** propriété sur le **propriétés du Transport** page.</span><span class="sxs-lookup"><span data-stu-id="dd643-118">If your application uses MQCIH and MQIIH header properties to put user credentials in outbound messages, use the **SSO Affiliate Application** property on the **Transport Properties** page.</span></span> <span data-ttu-id="dd643-119">Pour plus d’informations sur cette propriété, consultez [comment configurer les emplacements de réception de la carte de MQSeries et les Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span><span class="sxs-lookup"><span data-stu-id="dd643-119">For more information about this property, see [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd643-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd643-120">See Also</span></span>  
 <span data-ttu-id="dd643-121">[Structure de l’adaptateur MQSeries](../core/structure-of-the-mqseries-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="dd643-121">[Structure of the MQSeries Adapter](../core/structure-of-the-mqseries-adapter.md) </span></span>  
 [<span data-ttu-id="dd643-122">Nouveautés de l’adaptateur MQSeries ?</span><span class="sxs-lookup"><span data-stu-id="dd643-122">What Is the MQSeries Adapter?</span></span>](../core/what-is-the-mqseries-adapter.md)