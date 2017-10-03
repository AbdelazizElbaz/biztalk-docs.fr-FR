---
title: Single Sign-On et adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, Single Sign-On
- Single Sign-On, JD Edwards EnterpriseOne adapters
- adapters [JD Edwards EnterpriseOne adapters], Single Sign-On
ms.assetid: efcc3a2d-18a6-4090-9e95-143fb7a356b2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 182e73ed45a1473286a301cf859e619cc5d21287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="2aa40-102">Authentification unique et adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="2aa40-102">Single Sign-On and BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="2aa40-103">Lorsque vous utilisez l'authentification unique (SSO) avec l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne, ce dernier récupère les informations d'identification dans la base de données des informations d'identification SSO.</span><span class="sxs-lookup"><span data-stu-id="2aa40-103">When you use Single Sign-On (SSO) with Microsoft   Adapter for JD Edwards EnterpriseOne, the adapter obtains the credentials from the SSO Credentials database.</span></span> <span data-ttu-id="2aa40-104">Par conséquent, vous n’avez pas besoin d’entrer les informations d’identification d’ouverture de session pour le système serveur dans le **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2aa40-104">Therefore, you do not need to enter the logon credentials for the server system in the **Transport Properties** dialog box.</span></span>  
  
 <span data-ttu-id="2aa40-105">Au moment de la conception, l'adaptateur BizTalk pour JD Edwards EnterpriseOne obtient les informations d'identification pour le système (application associée spécifiée) sous le contexte de l'utilisateur qui a démarré le projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2aa40-105">At design-time, BizTalk Adapter for JD Edwards EnterpriseOne obtains the credentials for the system (for the specified affiliate application) under the context of the user who started the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="2aa40-106">Cet utilisateur doit être un utilisateur d'applications.</span><span class="sxs-lookup"><span data-stu-id="2aa40-106">That user should be an Application User.</span></span> <span data-ttu-id="2aa40-107">Au moment de l'exécution, utilisez l'adaptateur de réception HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme un emplacement de réception dans les scénarios de transfert durant lesquels vous faites appel à SSO.</span><span class="sxs-lookup"><span data-stu-id="2aa40-107">At run time, use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Receive Adapter as a receive location in the pass-through scenarios when using SSO.</span></span>  
  
## <a name="processing-requests"></a><span data-ttu-id="2aa40-108">Traitement des requêtes</span><span class="sxs-lookup"><span data-stu-id="2aa40-108">Processing Requests</span></span>  
 <span data-ttu-id="2aa40-109">Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2aa40-109">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="2aa40-110">L’extension ISAPI emprunte l’identité de l’utilisateur Windows et appelle le magasin d’informations d’identification SSO pour obtenir un ticket chiffré.</span><span class="sxs-lookup"><span data-stu-id="2aa40-110">The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="2aa40-111">Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="2aa40-111">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="2aa40-112">Le message est ensuite dirigé vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="2aa40-112">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="2aa40-113">Lorsque l'adaptateur BizTalk pour JD Edwards EnterpriseOne reçoit le message de la base de données MessageBox, il appelle `ValidateAndRedeemTicket` à l'aide du ticket chiffré conjointement avec le nom de l'application associée SSO afin de récupérer les informations d'identification dans le magasin SSO.</span><span class="sxs-lookup"><span data-stu-id="2aa40-113">When BizTalk Adapter for JD Edwards EnterpriseOne receives the message from the Message Box database, it calls `ValidateAndRedeemTicket` with the encrypted ticket along with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="2aa40-114">L'adaptateur utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="2aa40-114">The adapter then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2aa40-115">La configuration de l'authentification unique fait partie de l'installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2aa40-115">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="2aa40-116">Si vous obtenez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="2aa40-116">If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="2aa40-117">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="2aa40-117">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa40-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2aa40-118">See Also</span></span>  
 <span data-ttu-id="2aa40-119">[Création d’Applications associées](../core/creating-affiliate-applications4.md) </span><span class="sxs-lookup"><span data-stu-id="2aa40-119">[Creating Affiliate Applications](../core/creating-affiliate-applications4.md) </span></span>  
 [<span data-ttu-id="2aa40-120">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="2aa40-120">Using Single Sign-On</span></span>](../core/using-single-sign-on1.md)