---
title: "Instructions de dimensionnement de la base de données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, performance
- Tracking database, size
- Tracking Analysis Server database [BAM]
- performance, Tracking database
ms.assetid: 2188bee5-c0dd-4448-bd4a-4ffb2a0c79f1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c0293ff0a03583e51ee447ec1bd6283f1b02164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-database-sizing-guidelines"></a><span data-ttu-id="234f1-102">Instructions pour le dimensionnement de la base de données des suivis</span><span class="sxs-lookup"><span data-stu-id="234f1-102">Tracking Database Sizing Guidelines</span></span>
<span data-ttu-id="234f1-103">Cette section traite du dimensionnement de la base de données des suivis BizTalk (BizTalkDTADb) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="234f1-103">This section describes sizing considerations for the BizTalk Tracking (BizTalkDTADb) database in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="234f1-104">Elle explique comment utiliser des équations et des variables de message pour déterminer quelle taille la base de données des suivis BizTalk va avoir sur une période donnée et fournit des exemples concrets d'application de ces équations.</span><span class="sxs-lookup"><span data-stu-id="234f1-104">It explains how to use equations and message variables to determine how large the BizTalk Tracking database will become over a given period of time, and provides specific examples of how to apply the equations.</span></span> <span data-ttu-id="234f1-105">Ceci établit la corrélation globale qui existe entre les messages BizTalk, les paramètres de suivi et la taille de la base de données des suivis,</span><span class="sxs-lookup"><span data-stu-id="234f1-105">This provides the rough co-relation between BizTalk messages, tracking settings and the tracking database size.</span></span> <span data-ttu-id="234f1-106">mais ne prend pas en compte d'autres facteurs SQL Server comme la taille des index des tables de suivi. Prévoyez des multiplicateurs raisonnables pour tenir compte de ces facteurs.</span><span class="sxs-lookup"><span data-stu-id="234f1-106">It does not take into account other SQL Server factors such as index size in the tracking tables; you may want to consider reasonable multipliers to account for those factors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="234f1-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="234f1-107">In This Section</span></span>  
  
-   [<span data-ttu-id="234f1-108">À l’aide de Variables de Message à la taille de la base de données de suivi</span><span class="sxs-lookup"><span data-stu-id="234f1-108">Using Message Variables to Size the Tracking Database</span></span>](../core/using-message-variables-to-size-the-tracking-database.md)  
  
-   [<span data-ttu-id="234f1-109">Dimensionnement de la base de données de suivi pour suivre les corps de Message</span><span class="sxs-lookup"><span data-stu-id="234f1-109">Sizing the Tracking Database to Track Message Bodies</span></span>](../core/sizing-the-tracking-database-to-track-message-bodies.md)  
  
-   [<span data-ttu-id="234f1-110">Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples</span><span class="sxs-lookup"><span data-stu-id="234f1-110">Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages</span></span>](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)  
  
-   [<span data-ttu-id="234f1-111">Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="234f1-111">Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations</span></span>](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)  
  
-   [<span data-ttu-id="234f1-112">Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution</span><span class="sxs-lookup"><span data-stu-id="234f1-112">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)  
  
-   [<span data-ttu-id="234f1-113">Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages</span><span class="sxs-lookup"><span data-stu-id="234f1-113">Scenario 4: Sizing the Tracking Database for all Messages</span></span>](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)  
  
## <a name="see-also"></a><span data-ttu-id="234f1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="234f1-114">See Also</span></span>  
 <span data-ttu-id="234f1-115">[Taille de l’enregistrement dans les bases de données de suivi](../core/record-size-in-tracking-databases.md) </span><span class="sxs-lookup"><span data-stu-id="234f1-115">[Record Size in Tracking Databases](../core/record-size-in-tracking-databases.md) </span></span>  
 [<span data-ttu-id="234f1-116">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="234f1-116">Backing Up and Restoring BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-biztalk-server-databases.md)