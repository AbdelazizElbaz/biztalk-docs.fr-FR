---
title: "Serveur d’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, tasks
- Master Secret server, SSO
- servers, SSO
- SSO, servers
- SSO, Master Secret server
ms.assetid: 40240d6b-b7d1-48fb-b750-be0e380d52e3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37f2f24911a0336a734125436d97dbce6f9e0b77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-server"></a><span data-ttu-id="58867-102">Serveur de l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="58867-102">SSO Server</span></span>
<span data-ttu-id="58867-103">Le serveur d'authentification unique (SSO) de l'entreprise peut effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="58867-103">The Enterprise Single Sign-On (SSO) server can perform any of the following tasks:</span></span>  
  
-   <span data-ttu-id="58867-104">**Fonctions en tant que serveur de secret principal.**</span><span class="sxs-lookup"><span data-stu-id="58867-104">**Functions as the master secret server.**</span></span> <span data-ttu-id="58867-105">Le server de secret principal contient une copie persistante du secret principal (ou clé) utilisée pour le chiffrement des informations d'identification dans le système SSO.</span><span class="sxs-lookup"><span data-stu-id="58867-105">The master secret server holds a persisted copy of the master secret, or key, used to encrypt all the credentials in the SSO system.</span></span> <span data-ttu-id="58867-106">Bien que le serveur de secret principal puisse servir de serveur pour les recherches et l'administration, il est recommandé de l'utiliser en tant que serveur de secret principal uniquement pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="58867-106">Though the master secret server can act as a server for lookups and administration, it is recommended to use this server to act only as a master secret server for security reasons.</span></span> <span data-ttu-id="58867-107">Pour plus d’informations sur les fonctions que le serveur de secret principal effectue, consultez [serveur de secret principal](../core/master-secret-server.md).</span><span class="sxs-lookup"><span data-stu-id="58867-107">For more information about the functions the master secret server performs, see [Master Secret Server](../core/master-secret-server.md).</span></span>  
  
-   <span data-ttu-id="58867-108">**Effectue des opérations d’administration.**</span><span class="sxs-lookup"><span data-stu-id="58867-108">**Performs administrative operations.**</span></span> <span data-ttu-id="58867-109">Les administrateurs de l'authentification unique peuvent utiliser n'importe quel serveur SSO pour effectuer des tâches administratives telles que la gestion des applications associées, la configuration des informations d'identification des utilisateurs et la gestion des mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="58867-109">SSO administrators can use any of the Single Sign-On Servers to perform administrative tasks such as managing affiliate applications, setting user credentials, and managing user mappings.</span></span>  
  
-   <span data-ttu-id="58867-110">**Effectue des opérations de recherche.**</span><span class="sxs-lookup"><span data-stu-id="58867-110">**Performs lookup operations.**</span></span> <span data-ttu-id="58867-111">Le serveur SSO utilise le composant d'exécution pour rechercher les informations d'identifications des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="58867-111">The SSO server uses the runtime component to look up the user credentials.</span></span>  
  
-   <span data-ttu-id="58867-112">**Émettre et échanger des Tickets.**</span><span class="sxs-lookup"><span data-stu-id="58867-112">**Issues and Redeems Tickets.**</span></span> <span data-ttu-id="58867-113">Le serveur SSO peut également émettre et échanger des tickets SSO.</span><span class="sxs-lookup"><span data-stu-id="58867-113">The SSO server also issues and redeems SSO tickets.</span></span>  
  
-   <span data-ttu-id="58867-114">**Synchronisation de mot de passe.**</span><span class="sxs-lookup"><span data-stu-id="58867-114">**Password Synchronization.**</span></span> <span data-ttu-id="58867-115">Vous pouvez créer et gérer des adaptateurs de synchronisation de mot de passe sur le serveur SSO.</span><span class="sxs-lookup"><span data-stu-id="58867-115">You can create and manage password synchronization adapters on the SSO Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58867-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58867-116">See Also</span></span>  
 <span data-ttu-id="58867-117">[À l’aide de l’authentification unique](../core/using-sso.md) </span><span class="sxs-lookup"><span data-stu-id="58867-117">[Using SSO](../core/using-sso.md) </span></span>  
 [<span data-ttu-id="58867-118">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="58867-118">Installing SSO</span></span>](../core/installing-sso.md)