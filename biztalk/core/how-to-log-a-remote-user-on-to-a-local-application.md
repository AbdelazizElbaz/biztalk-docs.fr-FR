---
title: "Comment se connecter à un utilisateur distant sur une Application locale | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 886ee7cb-e6ba-476a-bea9-4bb4c22bf94e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f638007c3c4eb1f85a5b5a701dd2b456c2d220d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-log-a-remote-user-on-to-a-local-application"></a><span data-ttu-id="b3c46-102">Procédure : se connecter un utilisateur distant sur une Application locale</span><span class="sxs-lookup"><span data-stu-id="b3c46-102">How to Log a Remote User on to a Local Application</span></span>
<span data-ttu-id="b3c46-103">L’autre principale caractéristique du service d'authentification unique de l'entreprise (ENTSSO) réside dans la prise en charge du processus initié par l’hôte (HIP, Host-Initiated Process).</span><span class="sxs-lookup"><span data-stu-id="b3c46-103">The other main feature of Enterprise Single Sign-On service (ENTSSO) is supporting a host-initiated process (HIP).</span></span> <span data-ttu-id="b3c46-104">ENTSSO interagit avec HIP lorsqu'un utilisateur distant tente d'accéder aux ressources Windows locales.</span><span class="sxs-lookup"><span data-stu-id="b3c46-104">ENTSSO interacts with HIP when a remote user tries to access a local Windows resource.</span></span> <span data-ttu-id="b3c46-105">Il vous permet de recevoir la requête d’un utilisateur d'hôte et de demander l'accès à l'application Windows locale.</span><span class="sxs-lookup"><span data-stu-id="b3c46-105">Using ENTSSO, you can receive the request from the host user and request access to the local Windows application.</span></span>  
  
## <a name="log-a-remote-user-on-to-a-local-windows-application"></a><span data-ttu-id="b3c46-106">Se connecter à un utilisateur distant sur une application Windows locale</span><span class="sxs-lookup"><span data-stu-id="b3c46-106">Log a remote user on to a local Windows application</span></span>  
  
1.  <span data-ttu-id="b3c46-107">Recevez la requête d'un utilisateur distant.</span><span class="sxs-lookup"><span data-stu-id="b3c46-107">Receive the request from the remote user.</span></span>  
  
     <span data-ttu-id="b3c46-108">Il vous incombe de déterminer comment récupérer la requête d'un utilisateur distant.</span><span class="sxs-lookup"><span data-stu-id="b3c46-108">It is your responsibility to determine how to retrieve a request from the remote user.</span></span>  
  
2.  <span data-ttu-id="b3c46-109">Demandez que l'utilisateur distant bénéficie de l'accès à l'application associée spécifiée, à l'aide d'`ISSOLookup2.LogonExternalUser`.</span><span class="sxs-lookup"><span data-stu-id="b3c46-109">Request that the remote user be given access to the specified affiliate application, using `ISSOLookup2.LogonExternalUser`.</span></span>  
  
     <span data-ttu-id="b3c46-110">`LogonExternalUser` transmet le nom de l'application à laquelle l'utilisateur externe souhaite accéder, le nom de l'utilisateur externe, les informations d'identification de l'utilisateur externe ainsi que tous les indicateurs nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b3c46-110">`LogonExternalUser` passes in the name of the application the external user wishes to access, the name of the external user, the associated credentials for the external user, and any relevant flags.</span></span> <span data-ttu-id="b3c46-111">En cas de réussite, `LogonExternalUser` renvoie un handle vers un jeton d'accès Windows.</span><span class="sxs-lookup"><span data-stu-id="b3c46-111">If successful, `LogonExternalUser` returns a handle to a Windows access token.</span></span>  
  
     <span data-ttu-id="b3c46-112">L'utilisateur distant doit déjà être identifié dans la base de données de l'authentification unique, ses informations d'identification doivent figurer dans la base de données, et il doit être associé à une application associée.</span><span class="sxs-lookup"><span data-stu-id="b3c46-112">The remote user must already be identified in the Single Sign-On database, have their credentials in the database, and be associated with an affiliate application.</span></span> <span data-ttu-id="b3c46-113">Si tel n'est pas le cas, `LogonExternalUser` renvoie une erreur.</span><span class="sxs-lookup"><span data-stu-id="b3c46-113">Otherwise, `LogonExternalUser` returns an error.</span></span> <span data-ttu-id="b3c46-114">Vous pouvez conserver les noms d’utilisateur et les informations d’identification à jour à l’aide de la synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b3c46-114">You can keep the user names and credentials up to date using Password Sync.</span></span>  
  
     <span data-ttu-id="b3c46-115">De plus, la transition de protocole doit être activée.</span><span class="sxs-lookup"><span data-stu-id="b3c46-115">In addition, you must have protocol transition enabled.</span></span>  
  
3.  <span data-ttu-id="b3c46-116">Utilisez le handle Windows renvoyé par `LogonExternalUser` pour emprunter l'identité de l'utilisateur que ce jeton représente.</span><span class="sxs-lookup"><span data-stu-id="b3c46-116">Use the Windows handle returned from `LogonExternalUser` to impersonate the user that the token represents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c46-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3c46-117">See Also</span></span>  
 <span data-ttu-id="b3c46-118">[Procédure : se connecter un utilisateur Local à une Application non-Windows](../core/how-to-log-a-local-user-on-to-a-non-windows-application.md) </span><span class="sxs-lookup"><span data-stu-id="b3c46-118">[How to Log a Local User on to a Non-Windows Application](../core/how-to-log-a-local-user-on-to-a-non-windows-application.md) </span></span>  
 <span data-ttu-id="b3c46-119">**Méthode ISSOLookup2.LogonExternalUser**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c46-119">**ISSOLookup2.LogonExternalUser Method** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>