---
title: "Serveurs de traitement pour l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, processing servers
- processing servers [SSO]
ms.assetid: 9e80a456-974a-49b3-bb64-2e4713036cfb
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972e1a3b01394cbf63fb0c8094586d2beda73c3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-servers-for-sso"></a><span data-ttu-id="e49ef-102">Serveurs de traitement pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="e49ef-102">Processing Servers for SSO</span></span>
<span data-ttu-id="e49ef-103">Dans un environnement multiserveur, une fois le serveur de secret principal et la base de données SSO créés, vous pouvez installer l'authentification unique de l'entreprise sur les autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="e49ef-103">In a multi-computer environment, after the master secret server and SSO database have been created, you can install Enterprise Single Sign-On on subsequent computers.</span></span> <span data-ttu-id="e49ef-104">Il s'agit généralement des ordinateurs sur lesquels BizTalk Server ou Host Integration Server est installé.</span><span class="sxs-lookup"><span data-stu-id="e49ef-104">These are typically the computers on which either BizTalk Server or Host Integration Server is installed as well.</span></span>  
  
 <span data-ttu-id="e49ef-105">Bien que le processus d'installation initial soit identique à celui effectué sur le premier ordinateur,</span><span class="sxs-lookup"><span data-stu-id="e49ef-105">The initial installation process is the same as on the first computer.</span></span> <span data-ttu-id="e49ef-106">la configuration varie légèrement.</span><span class="sxs-lookup"><span data-stu-id="e49ef-106">Configuration, however, becomes slightly different.</span></span> <span data-ttu-id="e49ef-107">Étant donné que le serveur de secret principal et de la base de données SSO sont déjà en place, sélectionnez **joindre** lors de la demande de l’Assistant Configuration, **créer un nouveau système SSO** ou **joindre un système existant**.</span><span class="sxs-lookup"><span data-stu-id="e49ef-107">Since the master secret server and the SSO database are already in place, select **Join** when the Configuration Wizard asks, **Create a new SSO system** or **Join an existing system**.</span></span>  
  
 <span data-ttu-id="e49ef-108">Lors de la configuration d'un groupe sur un seul ordinateur, notez qu'il est possible de joindre une base de données SSO située sur un autre ordinateur et qui ne correspond pas à la base de données configurée pour ce groupe.</span><span class="sxs-lookup"><span data-stu-id="e49ef-108">Note that it is possible during configuration for a group on one computer to join an SSO database on a different computer that is not the database configured for that group.</span></span> <span data-ttu-id="e49ef-109">Bien que cette opération soit envisageable, elle est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="e49ef-109">While this is possible, it is not recommended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49ef-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e49ef-110">See Also</span></span>  
 [<span data-ttu-id="e49ef-111">La mise à niveau à partir d’une Version précédente de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="e49ef-111">Upgrading from a Previous Version of SSO</span></span>](../core/upgrading-from-a-previous-version-of-sso.md)