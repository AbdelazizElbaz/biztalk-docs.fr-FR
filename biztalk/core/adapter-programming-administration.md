---
title: "Administration de l’adaptateur programmation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38563b3c-6d52-4e4e-ac6e-74f46ce22c6a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b19e3285357bb067614aae9472eb099470fe27f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-programming-administration"></a><span data-ttu-id="57e8c-102">Administration de programmation de carte</span><span class="sxs-lookup"><span data-stu-id="57e8c-102">Adapter Programming Administration</span></span>
<span data-ttu-id="57e8c-103">Un adaptateur est un type spécial de l’application de magasin de configuration : un adaptateur est un composant partageant un espace de noms avec l’authentification unique sur des applications de magasin de configuration.</span><span class="sxs-lookup"><span data-stu-id="57e8c-103">An adapter is a special type of configuration store application: that is, an adapter is a component that shares a namespace with other Single Sign-On and configuration store applications.</span></span> <span data-ttu-id="57e8c-104">Par conséquent, vous pouvez accéder plus d’informations sur une carte à l’aide de ISSOConfigStore.</span><span class="sxs-lookup"><span data-stu-id="57e8c-104">Therefore, you can access information about an adapter using ISSOConfigStore.</span></span> <span data-ttu-id="57e8c-105">Mais contrairement à une application de magasin de configuration, vous n’effectuez pas les fonctions d’administration sur un adaptateur avec l’interface ISSOAdmin.</span><span class="sxs-lookup"><span data-stu-id="57e8c-105">But unlike a configuration store application, you do not perform administrative functions on an adapter with the ISSOAdmin interface.</span></span> <span data-ttu-id="57e8c-106">Au lieu de cela, vous administrez un adaptateur via ISSOPSAdmin.</span><span class="sxs-lookup"><span data-stu-id="57e8c-106">Instead, you administer an adapter through ISSOPSAdmin.</span></span> <span data-ttu-id="57e8c-107">Une interface d’administration d’adaptateur particulière est requise de sorte que le système puisse coordonner d’autres activités avec le magasin de configuration.</span><span class="sxs-lookup"><span data-stu-id="57e8c-107">The reason for a specialized adapter administration interface is so that the system can coordinate other activities with the configuration store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e8c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57e8c-108">See Also</span></span>  
 <span data-ttu-id="57e8c-109">[Configuration de programmation de carte](../core/adapter-programming-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="57e8c-109">[Adapter Programming Configuration](../core/adapter-programming-configuration.md) </span></span>  
 <span data-ttu-id="57e8c-110">[Groupes d’adaptateurs et adaptateurs de groupe](../core/adapter-groups-and-group-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="57e8c-110">[Adapter Groups and Group Adapters](../core/adapter-groups-and-group-adapters.md) </span></span>  
 [<span data-ttu-id="57e8c-111">Adaptateurs de synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="57e8c-111">Password Sync Adapters</span></span>](../core/password-sync-adapters.md)