---
title: "Pour configurer les Gestionnaire de réception WCF-NetTcp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF-NetTcp adapters, global variables
- receive handlers, WCF-NetTcp adapters
- configuring [WCF-NetTcp adapters], global variables
- configuring [WCF-NetTcp adapters], receive handlers
ms.assetid: a4a283d1-21de-4d6b-9cb5-f2f9f823903b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69598bc1ce0bda41269fa91a0618fb040e741b28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-nettcp-receive-handler"></a><span data-ttu-id="34f88-102">Configuration d'un gestionnaire de réception WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="34f88-102">How to Configure a WCF-NetTcp Receive Handler</span></span>
<span data-ttu-id="34f88-103">La procédure suivante permet de configurer un gestionnaire de réception WCF-NetTcp.</span><span class="sxs-lookup"><span data-stu-id="34f88-103">Use the following procedure to configure a WCF-NetTcp receive handler.</span></span>  
  
### <a name="to-change-global-variables-for-a-wcf-nettcp-receive-handler"></a><span data-ttu-id="34f88-104">Pour modifier les variables globales d'un gestionnaire de réception WCF-NetTcp</span><span class="sxs-lookup"><span data-stu-id="34f88-104">To change global variables for a WCF-NetTcp receive handler</span></span>  
  
1.  <span data-ttu-id="34f88-105">Dans la Console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.</span><span class="sxs-lookup"><span data-stu-id="34f88-105">In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="34f88-106">Dans la liste développée des adaptateurs, cliquez sur **WCF-NetTcp**, dans le volet de droite, avec le bouton du Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="34f88-106">In the expanded adapter list, click **WCF-NetTcp**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="34f88-107">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="34f88-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="34f88-108">Dans le **général** , cliquez sur **propriétés**, dans le **Gestionnaire de réception** onglet, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="34f88-108">In the **General** tab, click **Properties**, On the **Receive handler** tab, do the following.</span></span>  
  
    |<span data-ttu-id="34f88-109">Utiliser</span><span class="sxs-lookup"><span data-stu-id="34f88-109">Use this</span></span>|<span data-ttu-id="34f88-110">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="34f88-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="34f88-111">**Nombre maximal de connexions**</span><span class="sxs-lookup"><span data-stu-id="34f88-111">**Maximum connections**</span></span>|<span data-ttu-id="34f88-112">Spécifier un nombre maximal de connexions que l’écouteur peut mettre en attente d’acceptation par l’application.</span><span class="sxs-lookup"><span data-stu-id="34f88-112">Specify the maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="34f88-113">Lorsque ce quota est dépassé, les nouvelles connexions entrantes sont interrompues plutôt que mises en attente d'acceptation.</span><span class="sxs-lookup"><span data-stu-id="34f88-113">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span><br /><br /> <span data-ttu-id="34f88-114">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="34f88-114">The default is 10.</span></span>|  
  
5.  <span data-ttu-id="34f88-115">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="34f88-115">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f88-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34f88-116">See Also</span></span>  
 <span data-ttu-id="34f88-117">[Configuration de l’adaptateur WCF-NetTcp](../core/configuring-the-wcf-nettcp-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="34f88-117">[Configuring the WCF-NetTcp Adapter](../core/configuring-the-wcf-nettcp-adapter.md) </span></span>  
 [<span data-ttu-id="34f88-118">Publication des Services WCF</span><span class="sxs-lookup"><span data-stu-id="34f88-118">Publishing WCF Services</span></span>](../core/publishing-wcf-services.md)