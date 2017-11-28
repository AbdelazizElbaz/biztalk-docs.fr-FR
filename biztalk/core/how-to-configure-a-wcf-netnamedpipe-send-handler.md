---
title: "Comment configurer un gestionnaire d’envoi WCF-NetNamedPipe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-NetNamedPipe adapters, global adapters
- configuring [WCF-NetNamedPipe adapters], global adapters
- send handlers, WCF-NetNamedPipe adapters
- configuring [WCF-NetNamedPipe adapters], send handlers
ms.assetid: 1f281649-d09f-44eb-8af5-1f83233fab60
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 079d490ab8af28292c5f6adc6d98c8f64c5b16fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netnamedpipe-send-handler"></a><span data-ttu-id="77603-102">Configuration d'un gestionnaire d'envoi WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="77603-102">How to Configure a WCF-NetNamedPipe Send Handler</span></span>
<span data-ttu-id="77603-103">La procédure suivante permet de configurer un gestionnaire d'envoi WCF-NetNamedPipe.</span><span class="sxs-lookup"><span data-stu-id="77603-103">Use the following procedure to configure a WCF-NetNamedPipe send handler.</span></span>  
  
### <a name="to-change-global-variables-for-a-wcf-netnamedpipe-send-handler"></a><span data-ttu-id="77603-104">Pour modifier les variables globales d'un gestionnaire d'envoi WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="77603-104">To change global variables for a WCF-NetNamedPipe send handler</span></span>  
  
1.  <span data-ttu-id="77603-105">Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="77603-105">In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="77603-106">Dans la liste développée des adaptateurs, cliquez sur **WCF-NetNamedPipe**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="77603-106">In the expanded adapter list, click **WCF-NetNamedPipe**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="77603-107">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte auquel associer le Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="77603-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.</span></span>  
  
4.  <span data-ttu-id="77603-108">Dans le **général** , cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="77603-108">In the **General** tab, click **Properties**.</span></span> <span data-ttu-id="77603-109">Sur le **Gestionnaire d’envoi** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="77603-109">On the **Send handler** tab, do the following:</span></span>  
  
    |<span data-ttu-id="77603-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="77603-110">Use this</span></span>|<span data-ttu-id="77603-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="77603-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="77603-112">**Nombre maximal de connexions**</span><span class="sxs-lookup"><span data-stu-id="77603-112">**Maximum connections**</span></span>|<span data-ttu-id="77603-113">Spécifiez le nombre maximal de connexions sortantes pour chaque point de terminaison mis en cache dans le pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="77603-113">Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool.</span></span> <span data-ttu-id="77603-114">Cela limite le nombre de connexions sortantes mises en cache pour chaque point de terminaison unique distant.</span><span class="sxs-lookup"><span data-stu-id="77603-114">This limits the number of connections that are cached for each unique remote endpoint.</span></span> <span data-ttu-id="77603-115">Vous devez choisir une valeur supérieure au nombre maximal de connexions sortantes que vous voulez mettre en cache pour chaque point de terminaison unique distant.</span><span class="sxs-lookup"><span data-stu-id="77603-115">You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint.</span></span> <span data-ttu-id="77603-116">Si le nombre de connexions sortantes actives est supérieur à cette valeur maximale, le service peut sembler inaccessible aux ports d'envoi WCF-NetNamedPipe dont l'exécution est suivie par le gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="77603-116">If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetNamedPipe send ports running under this send hander.</span></span><br /><br /> <span data-ttu-id="77603-117">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="77603-117">The default is 10.</span></span>|  
  
5.  <span data-ttu-id="77603-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="77603-118">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77603-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77603-119">See Also</span></span>  
 <span data-ttu-id="77603-120">[Utilisation des Services WCF](../core/consuming-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="77603-120">[Consuming WCF Services](../core/consuming-wcf-services.md) </span></span>  
 [<span data-ttu-id="77603-121">Configuration de l’adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="77603-121">Configuring the WCF-NetNamedPipe Adapter</span></span>](../core/configuring-the-wcf-netnamedpipe-adapter.md)