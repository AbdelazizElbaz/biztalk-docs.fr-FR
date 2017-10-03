---
title: Single Sign-On et adaptateur BizTalk pour JD Enterprise OneWorld | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Single Sign-On
ms.assetid: 44fea3a4-8073-4b64-94e5-1eacbae845d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a9d3d102c3ab79ea719587fdb3632612e75faa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-enterprise-oneworld"></a><span data-ttu-id="f81d9-102">Authentification unique et adaptateur BizTalk pour JD Enterprise OneWorld</span><span class="sxs-lookup"><span data-stu-id="f81d9-102">Single Sign-On and BizTalk Adapter for JD Enterprise OneWorld</span></span>
<span data-ttu-id="f81d9-103">Informations d’identification unique de Sign-On (SSO) sont obtenues à partir de la base de données d’informations d’identification de l’authentification unique ; Par conséquent, vous n’avez pas besoin d’entrer des informations d’identification du système du serveur dans le **propriétés du Transport** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="f81d9-103">Single Sign-On (SSO) credentials are obtained from the SSO credentials database; therefore, you do not need to enter the server system's logon credentials in the **Transport Properties** window.</span></span>  
  
 <span data-ttu-id="f81d9-104">Au moment de la conception, l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld obtient les informations d'identification pour le système (application associée spécifiée) sous le contexte de l'utilisateur qui a démarré le projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f81d9-104">At design-time, Microsoft BizTalk Adapter for JD Edwards OneWorld obtains the credentials for the system (for the specified affiliate application) under the context of the user who started BizTalk Server project.</span></span> <span data-ttu-id="f81d9-105">Cet utilisateur doit être un utilisateur d'applications.</span><span class="sxs-lookup"><span data-stu-id="f81d9-105">That user should be an Application User.</span></span>  
  
 <span data-ttu-id="f81d9-106">Au moment de l'exécution, utilisez l'adaptateur BizTalk pour JD Edwards OneWorld comme emplacement de réception dans les scénarios de transfert incluant l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="f81d9-106">At run time, use the BizTalk Adapter for JD Edwards OneWorld as a receive location in the pass-through scenarios when using SSO.</span></span>  
  
 <span data-ttu-id="f81d9-107">Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f81d9-107">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="f81d9-108">L’extension ISAPI emprunte l’identité de l’utilisateur Windows et appelle le magasin d’informations d’identification SSO pour obtenir un ticket chiffré.</span><span class="sxs-lookup"><span data-stu-id="f81d9-108">The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="f81d9-109">Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="f81d9-109">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="f81d9-110">Le message est ensuite dirigé vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="f81d9-110">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="f81d9-111">Lorsque l'adaptateur reçoit le message de la base de données MessageBox, il appelle la méthode IBTSTicket.ValidateAndRedeemTicket avec le ticket chiffré, conjointement avec le nom de l'application associée, pour récupérer les informations d'identification du magasin SSO.</span><span class="sxs-lookup"><span data-stu-id="f81d9-111">When the adapter receives the message from the Message Box database, it calls the IBTSTicket.ValidateAndRedeemTicket method with the encrypted ticket along with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="f81d9-112">L'adaptateur BizTalk pour JD Edwards OneWorld utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="f81d9-112">BizTalk Adapter for JD Edwards OneWorld then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f81d9-113">La configuration de l'authentification unique fait partie de l'installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f81d9-113">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="f81d9-114">Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, car cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f81d9-114">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, because this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="f81d9-115">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="f81d9-115">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81d9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f81d9-116">See Also</span></span>  
 <span data-ttu-id="f81d9-117">[Création d’Applications associées](../core/creating-affiliate-applications3.md) </span><span class="sxs-lookup"><span data-stu-id="f81d9-117">[Creating Affiliate Applications](../core/creating-affiliate-applications3.md) </span></span>  
 [<span data-ttu-id="f81d9-118">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="f81d9-118">Using Single Sign-On</span></span>](../core/using-single-sign-on3.md)