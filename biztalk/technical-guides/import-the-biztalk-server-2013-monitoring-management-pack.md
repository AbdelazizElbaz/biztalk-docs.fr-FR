---
title: "Importer le Pack d’administration analyse BizTalk Server 2013 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bee2bfe9-4eb0-46d4-8eee-75182202080c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c6dff55cce17d9b9159a8eca754f91373621929
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-the-biztalk-server-2013-monitoring-management-pack"></a><span data-ttu-id="c8cdc-102">Importer le Pack d’administration analyse BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="c8cdc-102">Import the BizTalk Server 2013 Monitoring Management Pack</span></span>
<span data-ttu-id="c8cdc-103">Pour obtenir des instructions sur l’importation d’un Pack d’administration, consultez Comment importer un Pack d’administration dans [Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=142351) (http://go.microsoft.com/fwlink/?LinkId=142351).</span><span class="sxs-lookup"><span data-stu-id="c8cdc-103">For instructions about how to import a management pack, see How to Import a Management Pack in [Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=142351) (http://go.microsoft.com/fwlink/?LinkId=142351).</span></span> <span data-ttu-id="c8cdc-104">Après le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration est importé, suivez ces procédures pour terminer la configuration initiale :</span><span class="sxs-lookup"><span data-stu-id="c8cdc-104">After the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack is imported, follow these procedures to finish your initial configuration:</span></span>  
  
### <a name="to-configure-the-management-pack"></a><span data-ttu-id="c8cdc-105">Pour configurer le Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="c8cdc-105">To configure the management pack</span></span>  
  
1.  <span data-ttu-id="c8cdc-106">Créer un pack d’administration dans lequel vous stockez les remplacements et autres personnalisations.</span><span class="sxs-lookup"><span data-stu-id="c8cdc-106">Create a new management pack in which you store overrides and other customizations.</span></span>  
  
2.  <span data-ttu-id="c8cdc-107">Pour activer le paramètre Agent Proxy, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c8cdc-107">To enable the Agent Proxy setting, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="c8cdc-108">Ouvrez la console Opérateur, puis sur le bouton Administration.</span><span class="sxs-lookup"><span data-stu-id="c8cdc-108">Open the Operations console and then click the Administration button.</span></span>  
  
    2.  <span data-ttu-id="c8cdc-109">Dans le volet administrateur, cliquez sur **géré par Agent**.</span><span class="sxs-lookup"><span data-stu-id="c8cdc-109">In the Administrator pane, click **Agent Managed**.</span></span>  
  
    3.  <span data-ttu-id="c8cdc-110">Double-cliquez sur un agent dans la liste.</span><span class="sxs-lookup"><span data-stu-id="c8cdc-110">Double-click an agent in the list.</span></span>  
  
    4.  <span data-ttu-id="c8cdc-111">Sous l’onglet sécurité, sélectionnez **autoriser cet agent à agir en tant que proxy et détecter des objets gérés sur d’autres ordinateurs**.</span><span class="sxs-lookup"><span data-stu-id="c8cdc-111">On the Security tab, select **Allow this agent to act as a proxy and discover managed objects on other computers**.</span></span>  
  
    5.  <span data-ttu-id="c8cdc-112">Répétez les étapes 3 et 4 pour chaque agent qui est installé sur un serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c8cdc-112">Repeat steps 3 through 4 for each agent that is installed on a BizTalk Server.</span></span>