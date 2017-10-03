---
title: Single Sign-On et adaptateur BizTalk pour PeopleSoft Enterprise | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing HTTP requests
- Single Sign-On, using with the adapter
- HTTP requests, processing
ms.assetid: d8ad75f1-a83f-4722-a43f-50dc95df2f9d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3335d2c41e8c8dad4eabcb9f7a63253bd30e7185
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-peoplesoft-enterprise"></a><span data-ttu-id="841e7-102">Authentification unique et adaptateur BizTalk pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="841e7-102">Single Sign-On and BizTalk Adapter for PeopleSoft Enterprise</span></span>
<span data-ttu-id="841e7-103">Lorsque vous utilisez Single Sign-On (SSO) avec l’adaptateur Microsoft BizTalk pour PeopleSoft Enterprise, l’adaptateur obtient les informations d’identification à partir de la base de données des informations d’identification de l’authentification unique ; Par conséquent, vous n’avez pas à entrer les informations d’identification d’ouverture de session pour le système serveur dans le **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="841e7-103">When you use Single Sign-On (SSO) with Microsoft BizTalk Adapter for PeopleSoft Enterprise, the adapter obtains the credentials from the SSO Credentials database; therefore, you do not have to enter the logon credentials for the server system in the **Transport Properties** dialog box.</span></span>  
  
 <span data-ttu-id="841e7-104">Au moment de la conception, l'adaptateur BizTalk pour PeopleSoft Enterprise obtient les informations d'identification pour le système (application associée spécifiée) sous le contexte de l'utilisateur qui a démarré le projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="841e7-104">At design-time, BizTalk Adapter for PeopleSoft Enterprise obtains the credentials for the system (for the specified affiliate application) under the context of the user who started the BizTalk Server project.</span></span> <span data-ttu-id="841e7-105">Cet utilisateur doit être un utilisateur d'applications.</span><span class="sxs-lookup"><span data-stu-id="841e7-105">That user should be an Application User.</span></span>  
  
## <a name="processing-requests"></a><span data-ttu-id="841e7-106">Traitement des requêtes</span><span class="sxs-lookup"><span data-stu-id="841e7-106">Processing Requests</span></span>  
 <span data-ttu-id="841e7-107">Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="841e7-107">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="841e7-108">L'extension ISAPI se fait passer pour l'utilisateur Windows, puis appelle le magasin d'informations d'identification SSO pour obtenir un ticket chiffré.</span><span class="sxs-lookup"><span data-stu-id="841e7-108">The ISAPI extension impersonates the Windows user and then calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="841e7-109">Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="841e7-109">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="841e7-110">Le message est ensuite dirigé vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="841e7-110">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="841e7-111">Lorsque l'adaptateur BizTalk pour PeopleSoft Enterprise reçoit le message de la base de données MessageBox, il appelle la méthode ValidateAndRedeemTicket avec le ticket chiffré, conjointement avec le nom de l'application associée, pour récupérer les informations d'identification du magasin SSO.</span><span class="sxs-lookup"><span data-stu-id="841e7-111">When BizTalk Adapter for PeopleSoft Enterprises receives the message from the Message Box database, it calls ValidateAndRedeemTicket with the encrypted ticket together with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="841e7-112">L'adaptateur utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="841e7-112">The adapter then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="841e7-113">La configuration de l'authentification unique fait partie de l'installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="841e7-113">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="841e7-114">Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="841e7-114">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="841e7-115">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="841e7-115">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841e7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="841e7-116">See Also</span></span>  
 <span data-ttu-id="841e7-117">[Création d’Applications associées](../core/creating-affiliate-applications2.md) </span><span class="sxs-lookup"><span data-stu-id="841e7-117">[Creating Affiliate Applications](../core/creating-affiliate-applications2.md) </span></span>  
 [<span data-ttu-id="841e7-118">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="841e7-118">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)