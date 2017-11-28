---
title: "Single Sign-On : Événement 10521 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00d427ff-74d0-45f5-bb55-ab12b564d767
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 827771fe479084719db18152fd86da7d1fc01a2d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10521"></a><span data-ttu-id="eaf44-102">Single Sign-On : Événement 10521</span><span class="sxs-lookup"><span data-stu-id="eaf44-102">Single Sign-On: Event 10521</span></span>
## <a name="details"></a><span data-ttu-id="eaf44-103">Détails</span><span class="sxs-lookup"><span data-stu-id="eaf44-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eaf44-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="eaf44-104">Product Name</span></span>|<span data-ttu-id="eaf44-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="eaf44-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="eaf44-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="eaf44-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="eaf44-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="eaf44-107">Event ID</span></span>|<span data-ttu-id="eaf44-108">10521</span><span class="sxs-lookup"><span data-stu-id="eaf44-108">10521</span></span>|  
|<span data-ttu-id="eaf44-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="eaf44-109">Event Source</span></span>|<span data-ttu-id="eaf44-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="eaf44-110">ENTSSO</span></span>|  
|<span data-ttu-id="eaf44-111">Composant</span><span class="sxs-lookup"><span data-stu-id="eaf44-111">Component</span></span>|<span data-ttu-id="eaf44-112">N\A</span><span class="sxs-lookup"><span data-stu-id="eaf44-112">N\A</span></span>|  
|<span data-ttu-id="eaf44-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="eaf44-113">Symbolic Name</span></span>|<span data-ttu-id="eaf44-114">SSO_ERROR_SECRETS_NOT_LOADED</span><span class="sxs-lookup"><span data-stu-id="eaf44-114">SSO_ERROR_SECRETS_NOT_LOADED</span></span>|  
|<span data-ttu-id="eaf44-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="eaf44-115">Message Text</span></span>|<span data-ttu-id="eaf44-116">Impossible de charger les secrets à partir du Registre du serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="eaf44-116">Could not load secrets from the registry of the master secret server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eaf44-117">Explication</span><span class="sxs-lookup"><span data-stu-id="eaf44-117">Explanation</span></span>  
 <span data-ttu-id="eaf44-118">Cet événement d'erreur survient sur le serveur de secret principal lorsque les secrets principaux ne peuvent pas être obtenus du Registre.</span><span class="sxs-lookup"><span data-stu-id="eaf44-118">This Error event occurs on the master secret server when the master secrets cannot be obtained from the registry.</span></span> <span data-ttu-id="eaf44-119">Le journal des événements peut contenir d'autres messages d'erreur avec davantage d'informations.</span><span class="sxs-lookup"><span data-stu-id="eaf44-119">There may be related errors messages in the event log with further information.</span></span> <span data-ttu-id="eaf44-120">La cause la plus probable de cette erreur est la survenue d'une erreur d'autorisation ou de chiffrement lors de l'accès du compte de service de l'authentification unique au Registre.</span><span class="sxs-lookup"><span data-stu-id="eaf44-120">The most likely cause of this is that there has been a permissions error or an encryption error when the SSO service account attempted to access the registry.</span></span> <span data-ttu-id="eaf44-121">Ceci peut se produire lorsque le compte de service de l'authentification unique a été modifié.</span><span class="sxs-lookup"><span data-stu-id="eaf44-121">This can occur when the SSO service account has been changed.</span></span> <span data-ttu-id="eaf44-122">Le secret principal est chiffré à l'aide d'une clé basée sur l'identité du compte de service de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="eaf44-122">The master secret is encrypted with a key that is based on the identity of the SSO service account.</span></span> <span data-ttu-id="eaf44-123">Si ce compte est modifié, le secret principal existant dans le Registre ne peut plus être déchiffré.</span><span class="sxs-lookup"><span data-stu-id="eaf44-123">If that account is changed, then the existing master secret in the registry can no longer be decrypted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eaf44-124">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="eaf44-124">User Action</span></span>  
 <span data-ttu-id="eaf44-125">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="eaf44-125">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="eaf44-126">Modifiez le compte de service de l'authentification unique en sauvegardant le secret principal, en modifiant le compte, puis en restaurant le secret principal.</span><span class="sxs-lookup"><span data-stu-id="eaf44-126">Change the SSO service account by backing-up the master secret, then changing the SSO service account, and then restoring the master secret.</span></span> <span data-ttu-id="eaf44-127">Cette action permet de restaurer le secret principal et de résoudre cette erreur.</span><span class="sxs-lookup"><span data-stu-id="eaf44-127">This can restore the master secret and should fix this error.</span></span>  
  
 <span data-ttu-id="eaf44-128">Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="eaf44-128">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="eaf44-129">Serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="eaf44-129">Master Secret Server</span></span>](../core/master-secret-server.md)  
  
-   [<span data-ttu-id="eaf44-130">Gestion du Secret</span><span class="sxs-lookup"><span data-stu-id="eaf44-130">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)  
  
-   [<span data-ttu-id="eaf44-131">Configuration de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="eaf44-131">Configuring SSO</span></span>](../core/configuring-sso.md)  
  
-   [<span data-ttu-id="eaf44-132">Recommandations de sécurité pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="eaf44-132">SSO Security Recommendations</span></span>](../core/sso-security-recommendations.md)