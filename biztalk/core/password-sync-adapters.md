---
title: Les adaptateurs de synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56f97cfa-59d4-4f0a-bd08-b4857ab42122
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b7ff11e1cc98e953e89705b715db3709b4c4ffb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="password-sync-adapters"></a><span data-ttu-id="45dc1-102">Adaptateurs de synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="45dc1-102">Password Sync Adapters</span></span>
<span data-ttu-id="45dc1-103">A *adaptateur de synchronisation de mot de passe* est un composant qui propage les modifications de mot de passe vers et depuis un système non-Windows.</span><span class="sxs-lookup"><span data-stu-id="45dc1-103">A *password sync adapter* is a component that propagates password changes to and from a non-Windows system.</span></span> <span data-ttu-id="45dc1-104">Un adaptateur de synchronisation de mots de passe est similaire à une application d’authentification unique traditionnelle, à quelques différences près :</span><span class="sxs-lookup"><span data-stu-id="45dc1-104">Although password sync adapters are similar to traditional Single Sign-On applications, they have several differences:</span></span>  
  
-   <span data-ttu-id="45dc1-105">Il est administré par le biais d'interfaces spéciales.</span><span class="sxs-lookup"><span data-stu-id="45dc1-105">They are administered using a specialized interface.</span></span>  
  
-   <span data-ttu-id="45dc1-106">Il est décrit à l'aide d'un format XML spécial dans le magasin de configuration.</span><span class="sxs-lookup"><span data-stu-id="45dc1-106">They are described using a specialized XML format in the configuration store.</span></span>  
  
-   <span data-ttu-id="45dc1-107">Le serveur Host Integration Server utilise un composant spécial pour classer les adaptateurs dans le magasin de configuration.</span><span class="sxs-lookup"><span data-stu-id="45dc1-107">Host Integration Server uses a specialized feature to organize adapters in the configuration store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45dc1-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="45dc1-108">In This Section</span></span>  
 [<span data-ttu-id="45dc1-109">Architecture de programmation de synchronisation de mot de passe</span><span class="sxs-lookup"><span data-stu-id="45dc1-109">Password Sync Programming Architecture</span></span>](../core/password-sync-programming-architecture.md)  
  
 [<span data-ttu-id="45dc1-110">Administration de programmation de carte</span><span class="sxs-lookup"><span data-stu-id="45dc1-110">Adapter Programming Administration</span></span>](../core/adapter-programming-administration.md)  
  
 [<span data-ttu-id="45dc1-111">Configuration de programmation de carte</span><span class="sxs-lookup"><span data-stu-id="45dc1-111">Adapter Programming Configuration</span></span>](../core/adapter-programming-configuration.md)  
  
 [<span data-ttu-id="45dc1-112">Groupes d’adaptateurs et adaptateurs de groupe</span><span class="sxs-lookup"><span data-stu-id="45dc1-112">Adapter Groups and Group Adapters</span></span>](../core/adapter-groups-and-group-adapters.md)