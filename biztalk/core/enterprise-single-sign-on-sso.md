---
title: Enterprise Single Sign-On (SSO) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- SSO
ms.assetid: beab96f7-f026-4ae1-8462-a165ad76bbec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6cbc5f514d13cd8457cd9417be5ea5b78408e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enterprise-single-sign-on-sso"></a><span data-ttu-id="8ec05-102">Authentification unique de l'entreprise (SSO)</span><span class="sxs-lookup"><span data-stu-id="8ec05-102">Enterprise Single Sign-On (SSO)</span></span>
<span data-ttu-id="8ec05-103">Enterprise Single Sign-On (SSO) fournit des services pour stocker et transmettre chiffrée des informations d’identification de l’utilisateur entre les locaux et les limites du réseau, y compris les limites de domaine.</span><span class="sxs-lookup"><span data-stu-id="8ec05-103">Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local and network boundaries, including domain boundaries.</span></span> <span data-ttu-id="8ec05-104">Les informations d'identification sont stockées dans la base de données de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8ec05-104">SSO stores the credentials in the SSO database.</span></span> <span data-ttu-id="8ec05-105">Dans la mesure où l'authentification unique fournit une solution générique, les applications intermédiaires et les adaptateurs personnalisés peuvent s'appuyer sur l'authentification unique pour sécuriser le stockage et la transmission des informations d'identification de l'utilisateur dans l'intégralité de l'environnement.</span><span class="sxs-lookup"><span data-stu-id="8ec05-105">Because SSO provides a generic single sign-on solution, middleware applications and custom adapters can leverage SSO to securely store and transmit user credentials across the environment.</span></span> <span data-ttu-id="8ec05-106">Les utilisateurs finaux peuvent accéder aux différentes applications sans avoir à se souvenir de plusieurs informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="8ec05-106">End users do not have to remember different credentials for different applications.</span></span>  
  
 <span data-ttu-id="8ec05-107">Le système d'authentification unique est constitué d'une base de données de l'authentification unique, d'un serveur de secret principal ainsi que d'un ou de plusieurs serveurs de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8ec05-107">The Single Sign-On system consists of an SSO database, a master secret server, and one or more Single Sign-On servers.</span></span>  
  
 <span data-ttu-id="8ec05-108">Le système d’authentification unique contient *applications associées* définies par l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="8ec05-108">The SSO system contains *affiliate applications* that an administrator defines.</span></span> <span data-ttu-id="8ec05-109">Un *application associée* est une entité logique représentant un système ou sous-système tel qu’un hôte, un système principal ou une application métier à laquelle vous êtes connecté à l’aide de Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="8ec05-109">An *affiliate application* is a logical entity that represents a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using Enterprise Single Sign-On.</span></span> <span data-ttu-id="8ec05-110">Chaque application associée est dotée de plusieurs mappages d'utilisateurs. Elle dispose, par exemple, des mappages entre les informations d'identification d'un utilisateur utilisées par Active Directory et par RACF.</span><span class="sxs-lookup"><span data-stu-id="8ec05-110">Each affiliate application has multiple user mappings; for example, it has the mappings between the credentials for a user in Active Directory and their corresponding RACF credentials.</span></span>  
  
 <span data-ttu-id="8ec05-111">La base de données de l'authentification unique correspond à la base de données SQL Server qui stocke les informations relatives aux applications associées, ainsi que les informations d'identification chiffrées de l'utilisateur destinées à toutes les applications associées.</span><span class="sxs-lookup"><span data-stu-id="8ec05-111">The SSO database is the SQL Server database that stores the information about the affiliate applications, as well as all of the encrypted user credentials to all the affiliate applications.</span></span>  
  
 <span data-ttu-id="8ec05-112">Le *serveur de secret principal* est le serveur Enterprise Single Sign-On qui stocke le secret principal.</span><span class="sxs-lookup"><span data-stu-id="8ec05-112">The *master secret server* is the Enterprise Single Sign-On server that stores the master secret.</span></span> <span data-ttu-id="8ec05-113">Tous les autres serveurs d'authentification unique présents dans le système extraient le secret principal à partir de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="8ec05-113">All other Single Sign-On servers in the system get the master secret from the master secret server.</span></span>  
  
 <span data-ttu-id="8ec05-114">Le système d'authentification unique contient également un ou plusieurs serveurs d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8ec05-114">The SSO system also contains one or more SSO Servers.</span></span> <span data-ttu-id="8ec05-115">Ces derniers effectuent le mappage entre les informations d'identification Microsoft Windows et principales, et ils recherchent ces informations d'identification dans la base de données d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8ec05-115">These servers do the mapping between the Microsoft Windows and back-end credentials, and look up the credentials in the SSO database.</span></span> <span data-ttu-id="8ec05-116">Les administrateurs les utilisent pour assurer la gestion du système d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8ec05-116">Administrators use them to maintain the SSO system.</span></span>  
  
 <span data-ttu-id="8ec05-117">Pour plus d’une étude complète à Enterprise Single Sign-On, consultez [présentation SSO](../core/understanding-sso.md).</span><span class="sxs-lookup"><span data-stu-id="8ec05-117">For more a complete look at Enterprise Single Sign-On, see [Understanding SSO](../core/understanding-sso.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec05-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ec05-118">See Also</span></span>  
 [<span data-ttu-id="8ec05-119">Architecture d’exécution</span><span class="sxs-lookup"><span data-stu-id="8ec05-119">Runtime Architecture</span></span>](../core/runtime-architecture.md)