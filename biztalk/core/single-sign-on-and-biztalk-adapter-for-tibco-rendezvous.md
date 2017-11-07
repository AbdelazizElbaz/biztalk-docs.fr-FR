---
title: Single Sign-On et adaptateur BizTalk pour TIBCO Rendezvous | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52e698bb-38ba-4a12-b15a-d1581061d62f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 310a3448acd8bd70e617a9a5af650b55a12c9007
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="f3db0-102">Authentification unique et adaptateur BizTalk pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="f3db0-102">Single Sign-On and BizTalk Adapter for TIBCO Rendezvous</span></span>

## <a name="overview"></a><span data-ttu-id="f3db0-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="f3db0-103">Overview</span></span>
<span data-ttu-id="f3db0-104">Lorsque vous utilisez Single Sign-On (SSO) avec l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous, l’adaptateur obtient les informations d’identification à partir de la base de données des informations d’identification de l’authentification unique ; Par conséquent, vous n’avez pas à entrer les informations d’identification d’ouverture de session pour le système serveur dans le **propriétés du Transport** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="f3db0-104">When you use Single Sign-On (SSO) with Microsoft BizTalk Adapter for TIBCO Rendezvous, the adapter obtains the credentials from the SSO Credentials database; therefore, you do not have to enter the logon credentials for the server system in the **Transport Properties** window.</span></span>  
  
 <span data-ttu-id="f3db0-105">Au moment de la conception, l'adaptateur récupère les informations d'identification pour le système (pour l'application associée SSO spécifiée) dans le contexte de l'utilisateur qui a démarré le projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f3db0-105">At design time, the adapter obtains the credentials for the system (for the specified affiliate application) under the context of the user who started BizTalk Server project.</span></span> <span data-ttu-id="f3db0-106">Cet utilisateur doit être un utilisateur d'applications.</span><span class="sxs-lookup"><span data-stu-id="f3db0-106">That user should be an Application User.</span></span> <span data-ttu-id="f3db0-107">Au moment de l'exécution, utilisez l'adaptateur de réception HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme un emplacement de réception dans les scénarios de transfert pour lesquels vous faites appel à SSO.</span><span class="sxs-lookup"><span data-stu-id="f3db0-107">At run time, use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Receive Adapter as a receive location in the pass-through scenarios when you use SSO.</span></span>  
  
## <a name="processing-requests"></a><span data-ttu-id="f3db0-108">Traitement des requêtes</span><span class="sxs-lookup"><span data-stu-id="f3db0-108">Processing Requests</span></span>  
 <span data-ttu-id="f3db0-109">Lorsqu'il reçoit une requête HTTP d'un client Web, IIS (Internet Information Services) authentifie l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f3db0-109">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="f3db0-110">L’extension ISAPI emprunte l’identité de l’utilisateur Windows et appelle le magasin d’informations d’identification SSO pour obtenir un ticket chiffré.</span><span class="sxs-lookup"><span data-stu-id="f3db0-110">The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="f3db0-111">Ce ticket est stocké en tant que propriété SSOTicket dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="f3db0-111">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="f3db0-112">Le message est ensuite dirigé vers la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="f3db0-112">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="f3db0-113">Lorsque l'adaptateur BizTalk pour TIBCO Rendezvous reçoit les messages dans la base de données MessageBox, il appelle `ValidateAndRedeemTicket` à l'aide du ticket chiffré conjointement avec le nom de l'application associée SSO afin de récupérer les informations d'identification dans le magasin SSO.</span><span class="sxs-lookup"><span data-stu-id="f3db0-113">When BizTalk Adapter for TIBCO Rendezvous receives the message from the Message Box database, it calls `ValidateAndRedeemTicket` with the encrypted ticket together with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="f3db0-114">L'adaptateur utilise alors les informations d'identification externes pour se connecter au système et traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="f3db0-114">The adapter then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3db0-115">La configuration de l'authentification unique fait partie de l'installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f3db0-115">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="f3db0-116">Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f3db0-116">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="f3db0-117">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="f3db0-117">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3db0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3db0-118">See Also</span></span>  
 <span data-ttu-id="f3db0-119">[Création d’Applications associées](../core/creating-affiliate-applications1.md) </span><span class="sxs-lookup"><span data-stu-id="f3db0-119">[Creating Affiliate Applications](../core/creating-affiliate-applications1.md) </span></span>  
[<span data-ttu-id="f3db0-120">Sécurité</span><span class="sxs-lookup"><span data-stu-id="f3db0-120">Security</span></span>](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)