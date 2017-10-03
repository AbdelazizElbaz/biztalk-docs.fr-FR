---
title: "Comment régler l’intervalle d’actualisation du Cache Configuration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c6c998-e9c0-48f1-a36a-f1fcb916321b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad9459fadd65af220982ab31ae0e464cb7f1986e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-adjust-the-configuration-cache-refresh-interval"></a><span data-ttu-id="0a2e0-102">Comment régler l’intervalle d’actualisation du Cache Configuration</span><span class="sxs-lookup"><span data-stu-id="0a2e0-102">How to Adjust the Configuration Cache Refresh Interval</span></span>
<span data-ttu-id="0a2e0-103">L’intervalle d’actualisation du cache configuration définit la période de temps dans laquelle BizTalk Server met à jour la configuration des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-103">The configuration cache refresh interval defines the time period in which BizTalk Server updates the configuration of the endpoints.</span></span> <span data-ttu-id="0a2e0-104">Lorsque vous démarrez BizTalk Server, tous les éléments dans l’administration de BizTalk Server, telles que les bases de données MessageBox, les propriétés du serveur, les cartes et les connexions à la base de données de suivi, sont stockés dans le cache de configuration.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-104">When you start BizTalk Server, all items in BizTalk Server administration, such as MessageBox databases, server properties, adapters, and connections to the Tracking database, are stored in the configuration cache.</span></span> <span data-ttu-id="0a2e0-105">Tous les éléments dans le cache sont actualisés à l’intervalle d’actualisation de configuration.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-105">All items in the cache are refreshed by the configuration refresh interval.</span></span> <span data-ttu-id="0a2e0-106">Par défaut, cela est toutes les 60 secondes, à l’exception des connexions du serveur de base de données et propriétés du serveur.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-106">By default this is every 60 seconds, except for the server database connections and server properties.</span></span> <span data-ttu-id="0a2e0-107">Cela signifie que si vous modifiez les propriétés générales d’un groupe BizTalk, telles que l’hôte SMTP, les modifications sont récupérées pendant 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-107">This means that if you change the general properties for a BizTalk group, such as the SMTP host, the changes are picked up within 60 seconds.</span></span> <span data-ttu-id="0a2e0-108">Modifications du système effectuées à l’extérieur de l’instance ouverte de la console Administration de BizTalk Server ne sont pas répercutées jusqu'à ce que vous actualisiez.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-108">System changes made outside the currently open instance of the BizTalk Server Administration console are not reflected until you refresh it.</span></span>  
  
 <span data-ttu-id="0a2e0-109">L’intervalle d’actualisation du cache configuration fait partie des propriétés de groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-109">The configuration cache refresh interval is part of the BizTalk group properties.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a2e0-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0a2e0-110">Prerequisites</span></span>  
 <span data-ttu-id="0a2e0-111">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-111">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-adjust-the-cache-refresh-interval"></a><span data-ttu-id="0a2e0-112">Pour régler l’intervalle d’actualisation du cache</span><span class="sxs-lookup"><span data-stu-id="0a2e0-112">To adjust the cache refresh interval</span></span>  
  
1.  <span data-ttu-id="0a2e0-113">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-113">Click **Start**, click **All Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0a2e0-114">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-114">In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
3.  <span data-ttu-id="0a2e0-115">Dans le **Panneau de configuration BizTalk** boîte de dialogue, sélectionnez le **général** onglet. Pour le **intervalle d’actualisation de Configuration** propriété, tapez ou sélectionnez l’heure (en secondes) que tous les éléments de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cache d’administration doit attendre entre les actualisations du cache de configuration, puis cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="0a2e0-115">In the **BizTalk Settings Dashboard** dialog box, select the **General** tab. For the **Configuration refresh interval** property, type or select the time (in seconds) that all items in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administration cache must wait between configuration cache refreshes, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a2e0-116">Les éléments concernés par cette actualisation sont les bases de données MessageBox, les propriétés du serveur, les adaptateurs et les connexions à la base de données des suivis.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-116">Items involved in the refresh include the MessageBox databases, server properties, adapters, and connections to the Tracking database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a2e0-117">Par défaut, tous les objets dans le cache de configuration sont actualisés toutes les 60 secondes, à l’exception des connexions du serveur de base de données et propriétés du serveur.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-117">By default, all objects in the configuration cache are refreshed every 60 seconds, except for the server database connections and server properties.</span></span>