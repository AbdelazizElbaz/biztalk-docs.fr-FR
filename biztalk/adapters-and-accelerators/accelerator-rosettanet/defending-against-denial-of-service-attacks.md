---
title: "Protection contre les attaques par déni de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, denial-of-service attacks
- denial-of-service attacks
ms.assetid: 63342d7a-a5df-4e11-9037-93175d8f7ea7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 667b9d321f7703f770297b001ef2a99be2bf4902
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defending-against-denial-of-service-attacks"></a><span data-ttu-id="52116-102">Protection contre les attaques par déni de Service</span><span class="sxs-lookup"><span data-stu-id="52116-102">Defending Against Denial-of-Service Attacks</span></span>
<span data-ttu-id="52116-103">Une personne a pu démarrer une attaque par déni de service par rapport à une installation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] en mettant l’accent sur le fichier RNIFReceive.aspx reçoit la page.</span><span class="sxs-lookup"><span data-stu-id="52116-103">Someone could start a denial-of-service attack against an installation of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] by stressing the RNIFReceive.aspx receive page.</span></span> <span data-ttu-id="52116-104">Il peuvent le faire en envoyant un grand nombre de messages vides à cette page.</span><span class="sxs-lookup"><span data-stu-id="52116-104">They could do so by sending large numbers of empty messages to that page.</span></span> <span data-ttu-id="52116-105">Si la page de gauche est désactivé, qu'une telle attaque peut inonder le journal des événements avec des événements publiés par le ASPX s’affiche.</span><span class="sxs-lookup"><span data-stu-id="52116-105">If left unchecked, such an attack could flood the event log with events published by the ASPX receive page.</span></span>  
  
## <a name="defending-against-an-attack"></a><span data-ttu-id="52116-106">Protection contre une attaque</span><span class="sxs-lookup"><span data-stu-id="52116-106">Defending Against an Attack</span></span>  
 <span data-ttu-id="52116-107">Pour protéger le serveur contre les attaques de déni de service, il est recommandé de mettre à jour le journal des événements à une taille raisonnable et de prendre des mesures pour traiter un nombre excessif d’événements.</span><span class="sxs-lookup"><span data-stu-id="52116-107">To defend your server against denial-of-service attacks, it is recommended that you maintain the event log at a reasonable size and take steps to deal with excessive numbers of events.</span></span> <span data-ttu-id="52116-108">Pour cela en définissant la taille maximale du journal, en sélectionnant un moyen de remplacement des événements, ou à l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]® Management Instrumentation (WMI) pour gérer la taille du journal.</span><span class="sxs-lookup"><span data-stu-id="52116-108">You can accomplish this by setting the maximum log size, selecting a way of overwriting events, or using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]® Management Instrumentation (WMI) to manage the size of the log.</span></span> <span data-ttu-id="52116-109">Pour plus d’informations, consultez l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]™.</span><span class="sxs-lookup"><span data-stu-id="52116-109">For more information, see Help for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]™.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52116-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52116-110">See Also</span></span>  
 [<span data-ttu-id="52116-111">Gérer la configuration, les certificats, les bases de données et la sécurité</span><span class="sxs-lookup"><span data-stu-id="52116-111">Manage configuration, certificates, databases, and security</span></span>](manage-configuration-certificates-databases-security.md)