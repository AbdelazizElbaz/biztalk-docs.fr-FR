---
title: Serveur de secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, about Master Secret server
- Master Secret server, SSO
- SSO, encryption key
- Master Secret server, encryption key
- SSO, Master Secret server
ms.assetid: 93685a19-6c27-45db-bfc1-957574362687
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d02d5608546e86801bfc4a2281c42f902594e79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="master-secret-server"></a><span data-ttu-id="3720a-102">Serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="3720a-102">Master Secret Server</span></span>
<span data-ttu-id="3720a-103">Le serveur de secret principal correspond au serveur d'authentification unique de l'entreprise qui contient le secret principal (clé de chiffrement).</span><span class="sxs-lookup"><span data-stu-id="3720a-103">The master secret server is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key).</span></span> <span data-ttu-id="3720a-104">Le serveur de secret principal génère le secret principal quand un administrateur SSO le demande.</span><span class="sxs-lookup"><span data-stu-id="3720a-104">The master secret server generates the master secret when an SSO administrator requests it.</span></span> <span data-ttu-id="3720a-105">Ce serveur enregistre le secret principal chiffré dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="3720a-105">The master secret server stores the encrypted master secret in the registry.</span></span> <span data-ttu-id="3720a-106">Seuls les administrateurs de l'authentification unique peuvent accéder au secret principal.</span><span class="sxs-lookup"><span data-stu-id="3720a-106">Only Single Sign-On administrators can access the master secret.</span></span>  
  
 <span data-ttu-id="3720a-107">Les autres serveurs d'authentification unique vérifient si le secret principal a changé toutes les 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="3720a-107">The other Single Sign-On servers check every 30 seconds to see whether the master secret has changed.</span></span> <span data-ttu-id="3720a-108">Dans l'affirmative, ils le lisent de manière sécurisée. Sinon, ils continuent d'utiliser le secret principal déjà mis en mémoire cache.</span><span class="sxs-lookup"><span data-stu-id="3720a-108">If it has changed, they read it securely; otherwise, they continue to use the master secret they already have cached in memory.</span></span> <span data-ttu-id="3720a-109">Le service d'authentification unique utilise le secret principal pour chiffrer et déchiffrer les informations d'identification des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="3720a-109">The SSO service uses the master secret to encrypt and decrypt the user credentials.</span></span>  
  
 <span data-ttu-id="3720a-110">Vous ne pouvez utiliser le système d'authentification unique qu'une fois le serveur de secret principal configuré et le secret principal généré par un administrateur de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="3720a-110">You cannot use the SSO system until an SSO administrator configures the master secret server and generates the master secret.</span></span> <span data-ttu-id="3720a-111">Le serveur de secret principal génère le secret principal lors de la configuration.</span><span class="sxs-lookup"><span data-stu-id="3720a-111">The master secret server generates the master secret during configuration.</span></span> <span data-ttu-id="3720a-112">Seuls les administrateurs de l'authentification unique sont autorisés à le générer.</span><span class="sxs-lookup"><span data-stu-id="3720a-112">Only SSO administrators can generate the master secret.</span></span> <span data-ttu-id="3720a-113">Un administrateur de l'authentification unique doit configurer le serveur de secret principal et la base de données SSO pour qu'une application puisse utiliser le service d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="3720a-113">An SSO administrator must configure the master secret server and the SSO database before an application can use the SSO service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3720a-114">Une fois le secret principal généré, il est fortement recommandé de le sauvegarder et de le stocker dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="3720a-114">After you generate the master secret, it is strongly recommended that you back it up and store it in a secure location.</span></span>  
  
 <span data-ttu-id="3720a-115">Lorsqu'un administrateur de l'authentification unique doit régénérer le secret principal (par exemple, s'il souhaite modifier le secret principal périodiquement), le serveur de secret principal stocke l'ancien secret principal et le nouveau secret principal.</span><span class="sxs-lookup"><span data-stu-id="3720a-115">When an SSO administrator needs to regenerate the master secret, for example, if the SSO administrator wants to change the master secret periodically, the master secret server stores both the old and new master secret.</span></span> <span data-ttu-id="3720a-116">Le serveur de secret principal passe en revue les mappages, les déchiffre à l'aide de l'ancien secret principal et les chiffre à nouveau à l'aide du nouveau secret principal.</span><span class="sxs-lookup"><span data-stu-id="3720a-116">The master secret server then goes through all the mappings, decrypts them using the old master secret, and encrypts them again using the new master secret.</span></span>  
  
 <span data-ttu-id="3720a-117">Si le serveur de secret principal échoue, les opérations d'exécution déjà en cours continuent d'être exécutées, mais les serveurs d'authentification unique ne peuvent plus chiffrer les nouvelles informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="3720a-117">If the master secret server fails, all runtime operations already running will continue to run, but SSO servers will not be able to encrypt new credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3720a-118">Il ne peut y avoir qu'un serveur de secret principal dans votre système SSO.</span><span class="sxs-lookup"><span data-stu-id="3720a-118">There can be only one master secret server in your SSO system.</span></span> <span data-ttu-id="3720a-119">Par conséquent, il est fortement recommandé de mettre celui-ci en cluster.</span><span class="sxs-lookup"><span data-stu-id="3720a-119">Therefore, it is strongly recommended you cluster the master secret server.</span></span> <span data-ttu-id="3720a-120">Pour plus d’informations, consultez [mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md).</span><span class="sxs-lookup"><span data-stu-id="3720a-120">For more information, see [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3720a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3720a-121">See Also</span></span>  
 [<span data-ttu-id="3720a-122">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3720a-122">Using SSO</span></span>](../core/using-sso.md)