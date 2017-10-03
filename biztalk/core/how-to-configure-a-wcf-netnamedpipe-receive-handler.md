---
title: "Pour configurer les Gestionnaire de réception WCF-NetNamedPipe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [WCF-NetNamedPipe adapters], global variables
- receive handlers, WCF-NetNamedPipe adapters
- configuring [WCF-NetNamedPipe adapters], receive handlers
- WCF-NetNamedPipe adapters, global variables
ms.assetid: f7ab2228-1049-40f0-87f7-6330a8f40cfe
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9339cca7f8065d3412686cfcc84d84028ef39faf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netnamedpipe-receive-handler"></a><span data-ttu-id="f93c3-102">Configuration d'un gestionnaire de réception WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="f93c3-102">How to Configure a WCF-NetNamedPipe Receive Handler</span></span>
<span data-ttu-id="f93c3-103">La procédure suivante permet de configurer un gestionnaire de réception WCF-NetNamedPipe.</span><span class="sxs-lookup"><span data-stu-id="f93c3-103">Use the following procedure to configure a WCF-NetNamedPipe receive handler.</span></span>  
  
### <a name="to-change-global-variables-for-a-wcf-netnamedpipe-receive-handler"></a><span data-ttu-id="f93c3-104">Pour modifier les variables globales d'un gestionnaire de réception WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="f93c3-104">To change global variables for a WCF-NetNamedPipe receive handler</span></span>  
  
1.  <span data-ttu-id="f93c3-105">Dans la console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.</span><span class="sxs-lookup"><span data-stu-id="f93c3-105">In the BizTalk Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="f93c3-106">Dans la liste développée des adaptateurs, cliquez sur **WCF-NetNamedPipe**, dans le volet de droite, avec le bouton du Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f93c3-106">In the expanded adapter list, click **WCF-NetNamedPipe**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="f93c3-107">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="f93c3-107">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="f93c3-108">Dans le **général** , cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f93c3-108">In the **General** tab, click **Properties**.</span></span> <span data-ttu-id="f93c3-109">Sur le **Gestionnaire de réception** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f93c3-109">On the **Receive handler** tab, do the following:</span></span>  
  
    |<span data-ttu-id="f93c3-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f93c3-110">Use this</span></span>|<span data-ttu-id="f93c3-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f93c3-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f93c3-112">**Nombre maximal de connexions**</span><span class="sxs-lookup"><span data-stu-id="f93c3-112">**Maximum connections**</span></span>|<span data-ttu-id="f93c3-113">Spécifier un nombre maximal de connexions que l’écouteur peut mettre en attente d’acceptation par l’application.</span><span class="sxs-lookup"><span data-stu-id="f93c3-113">Specify the maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="f93c3-114">Lorsque ce quota est dépassé, les nouvelles connexions entrantes sont interrompues plutôt que mises en attente d'acceptation.</span><span class="sxs-lookup"><span data-stu-id="f93c3-114">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span><br /><br /> <span data-ttu-id="f93c3-115">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="f93c3-115">The default is 10.</span></span>|  
  
5.  <span data-ttu-id="f93c3-116">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f93c3-116">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93c3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f93c3-117">See Also</span></span>  
 <span data-ttu-id="f93c3-118">[Publication des Services WCF](../core/publishing-wcf-services.md) </span><span class="sxs-lookup"><span data-stu-id="f93c3-118">[Publishing WCF Services](../core/publishing-wcf-services.md) </span></span>  
 [<span data-ttu-id="f93c3-119">Configuration de l’adaptateur WCF-NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="f93c3-119">Configuring the WCF-NetNamedPipe Adapter</span></span>](../core/configuring-the-wcf-netnamedpipe-adapter.md)