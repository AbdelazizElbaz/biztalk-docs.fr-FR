---
title: "Comment configurer un gestionnaire d’envoi WCF-NetTcp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, WCF-NetTcp adapters
- configuring [WCF-NetTcp adapters], send handlers
- WCF-NetTcp adapters, global variables
- configuring [WCF-NetTcp adapters], global variables
ms.assetid: c60fe03d-7e11-4e08-9a24-8ff443eee9c1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02451dba6755e4db0c10d7cce20141468a67694f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-nettcp-send-handler"></a><span data-ttu-id="81ede-102">Comment configurer un gestionnaire d'envoi WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="81ede-102">How to Configure a WCF-NetTcp Send Handler</span></span>
<span data-ttu-id="81ede-103">La procédure suivante permet de configurer le gestionnaire d'envoi WCF-NetTcp.</span><span class="sxs-lookup"><span data-stu-id="81ede-103">Use the following procedure to configure a WCF-NetTcp send handler.</span></span>  
  
### <a name="to-change-global-variables-for-a-wcf-nettcp-send-handler"></a><span data-ttu-id="81ede-104">Pour modifier les variables globales d'un gestionnaire d'envoi WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="81ede-104">To change global variables for a WCF-NetTcp send handler</span></span>  
  
1.  <span data-ttu-id="81ede-105">Dans la Console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.</span><span class="sxs-lookup"><span data-stu-id="81ede-105">In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="81ede-106">Dans la liste développée des adaptateurs, cliquez sur **WCF-NetTcp**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="81ede-106">In the expanded adapter list, click **WCF-NetTcp**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="81ede-107">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte auquel associer le Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="81ede-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.</span></span>  
  
4.  <span data-ttu-id="81ede-108">Sur le **général** , cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="81ede-108">On the **General** tab, click **Properties**.</span></span> <span data-ttu-id="81ede-109">Sur le **Gestionnaire d’envoi** onglet, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="81ede-109">On the **Send handler** tab, do the following.</span></span>  
  
    |<span data-ttu-id="81ede-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="81ede-110">Use this</span></span>|<span data-ttu-id="81ede-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="81ede-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="81ede-112">**Nombre maximal de connexions**</span><span class="sxs-lookup"><span data-stu-id="81ede-112">**Maximum connections**</span></span>|<span data-ttu-id="81ede-113">Spécifiez le nombre maximal de connexions sortantes pour chaque point de terminaison mis en cache dans le pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="81ede-113">Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool.</span></span> <span data-ttu-id="81ede-114">Cela limite le nombre de connexions sortantes mises en cache pour chaque point de terminaison unique distant.</span><span class="sxs-lookup"><span data-stu-id="81ede-114">This limits the number of connections that are cached for each unique remote endpoint.</span></span> <span data-ttu-id="81ede-115">Vous devez choisir une valeur supérieure au nombre maximal de connexions sortantes que vous voulez mettre en cache pour chaque point de terminaison unique distant.</span><span class="sxs-lookup"><span data-stu-id="81ede-115">You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint.</span></span> <span data-ttu-id="81ede-116">Si le nombre de connexions sortantes actives est supérieur à cette valeur maximale, le service peut sembler inaccessible aux ports d'envoi WCF-NetTcp dont l'exécution est suivie par le gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="81ede-116">If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetTcp send ports running under this send hander.</span></span><br /><br /> <span data-ttu-id="81ede-117">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="81ede-117">The default is 10.</span></span>|  
  
5.  <span data-ttu-id="81ede-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="81ede-118">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ede-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81ede-119">See Also</span></span>  
 <span data-ttu-id="81ede-120">[Utilisation des Services WCF](../core/consuming-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="81ede-120">[Consuming WCF Services](../core/consuming-wcf-services.md) </span></span>  
 [<span data-ttu-id="81ede-121">Configuration de l’adaptateur WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="81ede-121">Configuring the WCF-NetTcp Adapter</span></span>](../core/configuring-the-wcf-nettcp-adapter.md)