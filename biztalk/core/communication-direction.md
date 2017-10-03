---
title: Direction de communication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port types, communication direction
- communication direction [port types]
ms.assetid: b278325e-a1da-49a6-8332-80a5f640cc22
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d6c664643629971366805d08600677d22d7c419
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="communication-direction"></a><span data-ttu-id="ac291-102">Direction de la communication</span><span class="sxs-lookup"><span data-stu-id="ac291-102">Communication Direction</span></span>
<span data-ttu-id="ac291-103">Chaque *port* a sa propre direction de communication.</span><span class="sxs-lookup"><span data-stu-id="ac291-103">Each *port* has its own communication direction.</span></span> <span data-ttu-id="ac291-104">La direction de communication est utilisée en association avec le modèle de communication du type du port pour compléter la définition de la manière dont un port peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="ac291-104">The communication direction is used in combination with the communication pattern of the port's type to complete the definition of how a port can be used.</span></span> <span data-ttu-id="ac291-105">La direction de communication, ou polarité, détermine la direction dans laquelle les messages seront transmis via le port.</span><span class="sxs-lookup"><span data-stu-id="ac291-105">The communication direction, or polarity, determines in which direction messages will be transmitted over that port.</span></span>  
  
 <span data-ttu-id="ac291-106">Si le type du port a un modèle de communication unidirectionnel, sa direction de communication est soit Envoi, soit Réception.</span><span class="sxs-lookup"><span data-stu-id="ac291-106">If the port's type has a one-way communication pattern, its communication direction can be either Send or Receive.</span></span> <span data-ttu-id="ac291-107">Si le type du port a un modèle de communication bidirectionnel (requête-réponse), sa direction de communication est soit Envoi-Réception, par laquelle une requête est envoyée et une réponse est reçue, soit Réception-Envoi, par laquelle une requête est reçue et une réponse est envoyée.</span><span class="sxs-lookup"><span data-stu-id="ac291-107">If the port's type has a two-way (request-response) communication pattern, its communication direction can be Send-Receive, in which a request is sent and a response is received, or Receive-Send, in which a request is received and a response is sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac291-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac291-108">See Also</span></span>  
 [<span data-ttu-id="ac291-109">Modèle de communication</span><span class="sxs-lookup"><span data-stu-id="ac291-109">Communication Pattern</span></span>](../core/communication-pattern.md)  
 <span data-ttu-id="ac291-110">[Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="ac291-110">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="ac291-111">L’utilisation de Ports dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="ac291-111">Using Ports in Orchestrations</span></span>](../core/using-ports-in-orchestrations.md)