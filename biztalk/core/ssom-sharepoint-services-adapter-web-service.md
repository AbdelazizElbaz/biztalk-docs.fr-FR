---
title: "SSOM : Service Web adaptateur de Services SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 064d97b0-eb4b-4943-af01-5ca11e5f7029
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3362af6cb7d2deca1afe02e7b871d07849ac3671
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ssom-sharepoint-services-adapter-web-service"></a><span data-ttu-id="1500f-102">SSOM : Le Service Web adaptateur SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="1500f-102">SSOM: SharePoint Services Adapter Web Service</span></span>
<span data-ttu-id="1500f-103">À l’aide de l’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], vous pouvez recevoir des messages de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] et envoyer des messages à [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1500f-103">Using the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter, you can receive messages from [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] and send messages to [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1500f-104">Le service Web de l’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], dont l’utilisation est déconseillée, utilise le modèle SSOM (Service-Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1500f-104">The [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web Service Adapter, which is deprecated, uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM).</span></span> <span data-ttu-id="1500f-105">Le service web est installé sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], qui peut se trouver sur le même ordinateur que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sur un ordinateur différent.</span><span class="sxs-lookup"><span data-stu-id="1500f-105">The web service is installed on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, which can be on the same computer as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a separate computer.</span></span> <span data-ttu-id="1500f-106">Il est recommandé d’installer [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur des ordinateurs distincts.</span><span class="sxs-lookup"><span data-stu-id="1500f-106">It is recommended to install [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on separate computers.</span></span>  
  
 <span data-ttu-id="1500f-107">Il est également conseillé d’utiliser le modèle CSOM (Client Side Object Model) de l’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1500f-107">We recommend using the Client Side Object Model (CSOM) of the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter.</span></span> <span data-ttu-id="1500f-108">Consultez [CSOM : adaptateur SharePoint Services](../core/csom-sharepoint-services-adapter.md) et [annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) pour les options d’installation et de configuration.</span><span class="sxs-lookup"><span data-stu-id="1500f-108">See [CSOM: SharePoint Services Adapter](../core/csom-sharepoint-services-adapter.md) and [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) for installation and configuration options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1500f-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1500f-109">In This Section</span></span>  
 [<span data-ttu-id="1500f-110">Nouveautés de l’adaptateur Windows SharePoint Services ?</span><span class="sxs-lookup"><span data-stu-id="1500f-110">What Is the Windows SharePoint Services Adapter?</span></span>](../core/what-is-the-windows-sharepoint-services-adapter.md)  
  
 [<span data-ttu-id="1500f-111">Configuration et déploiement de l’adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="1500f-111">Setting Up and Deploying the Windows SharePoint Services Adapter</span></span>](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)  
  
 [<span data-ttu-id="1500f-112">Configuration de l’adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="1500f-112">Configuring the Windows SharePoint Services Adapter</span></span>](../core/configuring-the-windows-sharepoint-services-adapter.md)  
  
 [<span data-ttu-id="1500f-113">Procédures pas à pas de carte de Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="1500f-113">Windows SharePoint Services Adapter Walkthroughs</span></span>](../core/windows-sharepoint-services-adapter-walkthroughs.md)