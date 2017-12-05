---
title: "Étape 2 : Configuration d’équilibrage de charge réseau sur les serveurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Network Load Balancing
- configuring, NLB
- NLB
ms.assetid: 30b2f645-b495-49a5-852b-cf89d25fd2b7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6d174ba336a94d44aaffdb2605542035304d9ff
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-2-configuring-nlb-on-the-servers"></a><span data-ttu-id="a51ee-102">Étape 2 : Configuration d’équilibrage de charge réseau sur les serveurs</span><span class="sxs-lookup"><span data-stu-id="a51ee-102">Step 2: Configuring NLB on the Servers</span></span>
<span data-ttu-id="a51ee-103">Après avoir installé la plate-forme de base et les serveurs configurés avec les paramètres de réseau approprié (voir [étape 1 : installation de la plate-forme de Base](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)), vous devrez peut-être activer l’équilibrage de charge sur les serveurs frontaux HTTP BizTalk et BizTalk Serveurs de messagerie.</span><span class="sxs-lookup"><span data-stu-id="a51ee-103">After you have installed the base platform and configured the servers with the proper network settings (see [Step 1: Installing the Base Platform](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)), you may need to enable load balancing on BizTalk HTTP front-end servers and the BizTalk Messaging servers.</span></span> <span data-ttu-id="a51ee-104">Cette étape est nécessaire uniquement si vous avez une ou plusieurs BizTalk serveurs frontaux HTTP installés sur un ordinateur distinct à partir d’un ou plusieurs serveurs de messagerie BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a51ee-104">This step is needed only if you have one or more BizTalk HTTP front-end servers installed on a separate computer from one or more BizTalk Messaging servers.</span></span>  
  
 <span data-ttu-id="a51ee-105">L’équilibrage de charge garantit la haute disponibilité des communications entre les ordinateurs clients (utilisateurs accédant au site MRSR pour Internet Explorer) et les serveurs MRSR et entre les serveurs MRSR et les serveurs de messagerie.</span><span class="sxs-lookup"><span data-stu-id="a51ee-105">Load balancing ensures high-availability communication between the client computers (Internet Explorer users browsing to the MRSR site) and the MRSR servers, and between the MRSR servers and the messaging servers.</span></span>  
  
 <span data-ttu-id="a51ee-106">Équilibrage de charge sur le **Public** interfaces des serveurs frontaux HTTP est requis pour activer les utilisateurs Intranet pour se connecter aux serveurs Web IIS sur ces ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a51ee-106">Load balancing on the **Public** interfaces of the HTTP front-end servers is required to enable the Intranet users to connect to the IIS Web servers on these computers.</span></span> <span data-ttu-id="a51ee-107">Équilibrage de charge sur le **privé** interfaces des serveurs frontaux HTTP est requis pour activer les serveurs de messagerie contacter les services web sur ces ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a51ee-107">Load balancing on the **Private** interfaces of the HTTP front-end servers is required to enable the messaging servers to contact the web services on these computers.</span></span>  
  
 <span data-ttu-id="a51ee-108">Sur les serveurs de messagerie, en supposant que les deux serveurs, sont configurer l’équilibrage de charge sur le **privé** cartes réseau.</span><span class="sxs-lookup"><span data-stu-id="a51ee-108">On the messaging servers, assuming there are two servers, configure load balancing on the **Private** network adapters.</span></span>  
  
 <span data-ttu-id="a51ee-109">Pour plus d’informations, consultez le Guide de déploiement de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a51ee-109">For more information, see the BizTalk Server Deployment Guide.</span></span>