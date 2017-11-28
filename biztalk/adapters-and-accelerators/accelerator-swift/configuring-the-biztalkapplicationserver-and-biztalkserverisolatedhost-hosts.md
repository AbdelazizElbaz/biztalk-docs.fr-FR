---
title: "Configuration du BizTalkApplicationServer et des hôtes de BizTalkServerIsolatedHost | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, hosts
- BizTalkApplicationServer host
- hosts
- BizTalkServerIsolatedHost host
ms.assetid: 17bc9f01-ff87-427d-8411-6a065814ba1e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8459debcd52ce990bc98adf3a2a2372206bae336
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-biztalkapplicationserver-and-biztalkserverisolatedhost-hosts"></a><span data-ttu-id="49820-102">Configuration BizTalkApplicationServer et BizTalkServerIsolatedHost hôtes</span><span class="sxs-lookup"><span data-stu-id="49820-102">Configuring the BizTalkApplicationServer and BizTalkServerIsolatedHost Hosts</span></span>
<span data-ttu-id="49820-103">Pour limiter la messagerie (envoi et réception de messages) sur les serveurs de messagerie BizTalk, vous devez configurer les ordinateurs hôtes par défaut, qui sont en cours d’exécution envoi MSMQT et gestionnaires de réception, pour exécuter uniquement sur les serveurs de messagerie.</span><span class="sxs-lookup"><span data-stu-id="49820-103">To limit the messaging (sending and receiving messages) to the BizTalk Messaging servers, you need to configure the default hosts, which are running the MSMQT send and receive handlers, to run only on the messaging servers.</span></span>  
  
### <a name="to-configure-the-default-hosts"></a><span data-ttu-id="49820-104">Pour configurer les ordinateurs hôtes par défaut</span><span class="sxs-lookup"><span data-stu-id="49820-104">To configure the default hosts</span></span>  
  
1.  <span data-ttu-id="49820-105">À l’aide de la Console Administration de BizTalk, de supprimer les instances d’orchestration serveurs hôte de l’hôte BizTalkApplicationServer :</span><span class="sxs-lookup"><span data-stu-id="49820-105">Using the BizTalk Administration Console, delete the orchestration servers host instances from the BizTalkApplicationServer host:</span></span>  
  
    -   <span data-ttu-id="49820-106">Cliquez sur chaque instance d’hôte, sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="49820-106">Right-click each host instance and click **Stop**.</span></span>  
  
    -   <span data-ttu-id="49820-107">Cliquez sur chaque instance d’hôte, sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="49820-107">Right-click each host instance and click **Delete**.</span></span>  
  
2.  <span data-ttu-id="49820-108">À l’aide de la Console Administration de BizTalk, de supprimer les instances d’orchestration serveurs hôte de l’hôte BizTalkServerIsolatedHost :</span><span class="sxs-lookup"><span data-stu-id="49820-108">Using the BizTalk Administration Console, delete the orchestration servers host instances from the BizTalkServerIsolatedHost host:</span></span>  
  
    -   <span data-ttu-id="49820-109">Cliquez sur chaque instance d’hôte, puis cliquez sur Supprimer.</span><span class="sxs-lookup"><span data-stu-id="49820-109">Right-click each host instance and click Delete.</span></span>  
  
3.  <span data-ttu-id="49820-110">Après avoir configuré les ordinateurs hôtes, redémarrez toutes les instances d’hôte sur tous les serveurs.</span><span class="sxs-lookup"><span data-stu-id="49820-110">After you have configured the hosts, restart all the host instances on all the servers.</span></span>